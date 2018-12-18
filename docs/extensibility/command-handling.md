---
title: Comandi (gestione) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 3ecbff62570067b25aae9ad525138687eb281c9f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="command-handling"></a>Gestione dei comandi
L'editor è possibile definire nuovi comandi. I comandi vengono in genere visualizzati in un menu, in una barra degli strumenti oppure in un menu di scelta rapida.  
  
 Per ulteriori informazioni sulla definizione di menu e comandi, vedere [comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Un servizio di linguaggio è possibile controllare il menu di scelta rapida vengono visualizzati nell'editor, mediante l'intercettazione di <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> enumerazione. In alternativa, è possibile controllare il menu di scelta rapida in una base per ogni marcatore. Per ulteriori informazioni vedere [comandi importanti per i filtri di servizio di linguaggio](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Aggiunta di comandi al menu di scelta rapida Editor  
 Per aggiungere un comando di menu di scelta rapida, è innanzitutto necessario definire un set di comandi di menu che appartengono a un gruppo specifico. L'esempio seguente è tratto dal file con estensione vsct generato come parte della procedura dettagliata [procedura dettagliata: aggiunta di funzionalità a un Editor personalizzato](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Menu guid = "guidCustomEditorCmdSet" id = "IDMX_RTF" priorità = "0x0000" type = "Contesto" >  
  
 \<Guid padre = "guidCustomEditorCmdSet" id = "0" / >  
  
 \<Stringhe >  
  
 \<ButtonText > Menu di scelta rapida CustomEditor\</ButtonText >  
  
 \<CommandName > CustomEditorContextMenu\</CommandName >  
  
 \</ Stringhe di >  
  
 \</ Menu >  
  
 \</ Menu >  
  
 Il testo precedente aggiunge un comando di menu di contesto con il testo **il menu di scelta rapida CustomEditor**. Il GUID di Menu è che del set di comandi che viene creato con questo editor e il tipo è "Context".  
  
 È inoltre possibile utilizzare comandi predefiniti che non devono essere definiti nel file vsct. Ad esempio, se si esamina il file EditorPane.cs generato dal modello di pacchetto di Visual Studio, è disponibile che un set di comandi predefiniti, ad esempio <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> definito da <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>, vengono gestite nei gestori di comando, ad esempio il metodo onSelectAll.  
  
## <a name="see-also"></a>Vedere anche  
 [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)