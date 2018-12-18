---
title: Comando implementazione | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5ed14a65e2839039a9f5c3075dd68498c948a4fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="command-implementation"></a>Implementazione di comando
Per implementare un comando in un pacchetto VSPackage, è necessario eseguire le attività seguenti:  
  
1.  Nel file vsct, configurare un gruppo di comandi e quindi aggiungere il comando. Per ulteriori informazioni, vedere [Visual Studio Command Table (. File Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)'  
  
2.  Registrare il comando con Visual Studio.  
  
3.  Implementare il comando.  
  
 Le sezioni seguenti illustrano come registrare e implementare i comandi.  
  
## <a name="registering-commands-with-visual-studio"></a>Registrazione di comandi con Visual Studio  
 Se il comando viene visualizzato un menu, è necessario aggiungere il <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> al pacchetto VSPackage e utilizzare come valore il nome del menu di scelta o ID della risorsa.  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 Inoltre, è necessario registrare il comando con il <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>. È possibile ottenere questo servizio utilizzando il <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metodo se il pacchetto VSPackage è derivato da <xref:Microsoft.VisualStudio.Shell.Package>.  
  
```  
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
if ( null != mcs )  
{  
    // Create the command for the menu item.  
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);  
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );  
    mcs.AddCommand( menuItem );  
}  
  
```  
  
## <a name="implementing-commands"></a>Implementazione di comandi  
 Esistono diversi modi per implementare i comandi. Se si desidera che un comando di menu statico, che è un comando che viene sempre visualizzata la stessa modalità e dello stesso menu, creare il comando utilizzando <xref:System.ComponentModel.Design.MenuCommand> come illustrato negli esempi nella sezione precedente. Per creare un comando statico, è necessario fornire un gestore eventi che è responsabile per l'esecuzione del comando. Poiché il comando è sempre visibile e abilitato, non è necessario fornire il relativo stato di Visual Studio. Se si desidera modificare lo stato di un comando in base a determinate condizioni, è possibile creare il comando come un'istanza di <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> classe e, nel relativo costruttore, fornire un gestore eventi per eseguire il comando e un gestore dello stato di query per notificare Visual Studio quando viene modificato lo stato del comando. È anche possibile implementare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> come parte di una classe di comando o, è possibile implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> se si specifica un comando come parte di un progetto. Le due interfacce e <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> tutti classe dispone di metodi che la notifica di Visual Studio di una modifica dello stato di un comando e altri metodi che forniscono l'esecuzione del comando.  
  
 Quando un comando viene aggiunto al servizio di comando, diventa uno di una catena di comandi. Quando si implementano i metodi di notifica e l'esecuzione di stato per il comando, prestare attenzione per fornire solo per quel comando specifico e per passare tutti gli altri casi al altri comandi nella catena. Se non è possibile passare il comando (in genere restituendo <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>), Visual Studio potrebbero non funzionare correttamente.  
  
## <a name="query-status-methods"></a>Metodi di query dello stato  
 Se si implementa il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> (metodo), cercare il GUID del comando set a cui appartiene il comando e l'ID del comando. Attenersi alle seguenti indicazioni:  
  
-   Se il GUID non viene riconosciuto, l'implementazione di uno di questi metodi debba restituire <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>.  
  
-   Se l'implementazione dei metodi riconosce il GUID, ma non ha implementato il comando, quindi il metodo dovrebbe restituire <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
-   Se l'implementazione dei metodi riconosce il GUID e il comando, quindi il metodo deve impostare il campo flag dei comandi di ogni comando (nelle `prgCmds` parametro) con i seguenti <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> flag:  
  
    -   OLECMDF_SUPPORTED - se il comando è supportato.  
  
    -   OLECMDF_INVISIBLE - se il comando non deve essere visibile.  
  
    -   OLECMDF_LATCHED - se il comando è attivato e viene visualizzato per sono state controllate.  
  
    -   OLECMDF_ENABLED - se il comando è abilitato.  
  
    -   OLECMDF_DEFHIDEONCTXTMENU - se il comando deve essere nascosto quando viene visualizzato un menu di scelta rapida.  
  
    -   OLECMDF_NINCHED - se il comando è un controller di menu e non è abilitato, ma l'elenco di menu a discesa non è vuoto ed è ancora disponibile. (Questo flag viene raramente utilizzato).  
  
-   Se il comando è stato definito nel file vsct con il `TextChanges` flag, impostare i parametri seguenti:  
  
    -   Impostare il `rgwz` elemento il `pCmdText` parametro per il nuovo testo del comando.  
  
    -   Impostare il `cwActual` elemento del `pCmdText` parametro per le dimensioni della stringa di comando.  
  
 Assicurarsi che il contesto corrente non è una funzione di automazione, a meno che il comando è concepito appositamente per gestire le funzioni di automazione.  
  
 Per indicare che si supporta un comando specifico, restituire <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Per tutti gli altri comandi, restituire <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
 Nell'esempio seguente, il metodo di query-status prima assicura che il contesto non è una funzione di automazione, quindi consente di trovare il GUID di set di comandi corretto e ID di comando. Il comando è impostato per essere attivato e supportato. Altri comandi non sono supportati.  
  
```  
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)  
        {  
            // make the Right command visible   
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;  
                return VSConstants.S_OK;  
            }  
        }  
        return Constants.OLECMDERR_E_NOTSUPPORTED;  
    }  
}  
  
```  
  
## <a name="execution-methods"></a>Metodi di esecuzione  
 Implementazione del metodo query-status è simile a implementazione del metodo execute. Innanzitutto, assicurarsi che il contesto non è una funzione di automazione. Verificare quindi il GUID e ID di comando. Se il GUID o ID di comando non riconosciuto, restituire <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>.  
  
 Per gestire il comando, eseguirlo e restituire <xref:Microsoft.VisualStudio.VSConstants.S_OK> se l'esecuzione ha esito positivo. Il comando è responsabile per il rilevamento errori e la notifica. Pertanto, restituire un codice di errore se l'esecuzione ha esito negativo. Nell'esempio seguente viene illustrato come il metodo di esecuzione deve essere implementato.  
  
```  
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)  
        {  
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                //execute the command  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    return Constants.OLECMDERR_E_NOTSUPPORTED;  
}  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)