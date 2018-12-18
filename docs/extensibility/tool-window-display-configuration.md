---
title: Strumento di configurazione di finestra | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 585ea78e0591ad979d09a3e5b208635c3f75f903
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="tool-window-display-configuration"></a>Lo strumento Configurazione di finestra
Quando un pacchetto VSPackage registra una finestra degli strumenti, la posizione predefinita, le dimensioni, lo stile di ancoraggio e altre informazioni di visibilità è specificato in valori facoltativi. Per ulteriori informazioni sulla registrazione di finestra dello strumento, vedere [finestre degli strumenti nel Registro di sistema](../extensibility/tool-windows-in-the-registry.md)  
  
## <a name="window-display-information"></a>Informazioni della finestra di visualizzazione  
 Configurazione di visualizzazione di base di una finestra degli strumenti viene archiviata in un massimo di sei valori facoltativi:  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              (Default)       = reg_sz: <Package GUID>Name            = reg_sz: <name of tool window>Float           = reg_sz: <position>Style           = reg_sz: <dock style>Window          = reg_sz: <window GUID>Orientation     = reg_sz: <orientation>DontForceCreate = reg_dword: 0x00000000  
```  
  
|nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|nome|REG_SZ|"Nome breve qui"|Nome breve che descrive la finestra degli strumenti. Utilizzato solo per riferimento nel Registro di sistema.|  
|Float|REG_SZ|"X1, Y1, X2, Y2"|Quattro valori separati da virgole. X1, Y1 è coordinate dell'angolo superiore sinistro della finestra degli strumenti. X2, Y2 è coordinate dell'angolo inferiore destro. Tutti i valori sono nelle coordinate dello schermo.|  
|Stile|REG_SZ|"MDI"<br /><br /> "Float"<br /><br /> "Collegate"<br /><br /> "Schede"<br /><br /> "AlwaysFloat"|Una parola chiave specifica iniziale visualizzare lo stato della finestra degli strumenti.<br /><br /> "MDI" = ancorate con finestra MDI.<br /><br /> "Float" = mobile.<br /><br /> "Collegate" = collegata a un'altra finestra (specificata nella voce della finestra).<br /><br /> "Schede" = combinati con un'altra finestra degli strumenti.<br /><br /> "AlwaysFloat" = non può essere ancorato.<br /><br /> Per ulteriori informazioni, vedere la sezione commenti riportato di seguito.|  
|Window|REG_SZ|*\<GUID >*|Il GUID di una finestra a cui la finestra degli strumenti può essere collegata o a schede. Il GUID può appartenere a una delle finestre personalizzate o una delle finestre di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE.|  
|Orientamento|REG_SZ|"Left"<br /><br /> "Right"<br /><br /> "Top"<br /><br /> "Basso"|Vedere la sezione commenti.|  
|DontForceCreate|REG_DWORD|0 o 1|Quando questa voce è presente e il relativo valore è diverso da zero, la finestra viene caricata, ma non immediatamente visualizzata.|  
  
### <a name="comments"></a>Commenti  
 La voce orientamento definisce la posizione in cui la finestra degli strumenti ancorata quando si fa doppio clic sulla barra del titolo. La posizione è relativo alla finestra specificata nella voce della finestra. Se la voce di stile è impostata su "Collegate", la voce di orientamento può essere "Left", "Right", "Top" o "Bottom". Se la voce di stile è "Schede", l'orientamento della voce può essere "Left" o "Right" e specifica in cui la scheda viene aggiunta. Se la voce di stile è "Float", viene spostata prima la finestra degli strumenti. Facendo doppio clic sulla barra del titolo, applicano le voci di finestra e l'orientamento e la finestra utilizza lo stile "Schede". Se la voce di stile è "AlwaysFloat", la finestra degli strumenti non può essere ancorata. Se la voce di stile è "MDI", la finestra degli strumenti è collegata all'area di MDI, e viene ignorata la voce della finestra.  
  
### <a name="example"></a>Esempio  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {A0C5197D-0AC7-4B63-97CD-8872A789D233}\  
              (Default)       = reg_sz: {DA9FB551-C724-11D0-AE1F-00A0C90FFFC3}  
              DontForceCreate = reg_dword: 0x00000000  
              Float           = reg_sz: 100,100,450,300  
              Name            = reg_sz: Bookmarks  
              Orientation     = reg_sz: Left  
              Style           = reg_sz: Tabbed  
              Window          = reg_sz: {34E76E81-EE4A-11D0-00A0C90FFFC3}  
```  
  
## <a name="tool-window-visibility"></a>Visibilità della finestra dello strumento  
 I valori nella sottochiave visibilità facoltativo determinano le impostazioni di visibilità di una finestra degli strumenti. I nomi dei valori vengono utilizzati per archiviare i GUID di comandi che richiedono la visibilità della finestra. Se il comando viene eseguito, l'IDE garantisce che la finestra degli strumenti viene creata e reso visibile.  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              Visibility\  
                (Default) = reg_sz:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_sz:  
```  
  
|nome|Tipo|Dati|Descrizione|  
|----------|----------|----------|-----------------|  
|(Predefinito)|REG_SZ|nessuno|Lasciare vuoto.|  
|*\<GUID >*|REG_DWORD o REG_SZ.|0 o una stringa descrittiva.|Facoltativo. Nome della voce deve essere il GUID di un comando che richiede la visibilità. Il valore contiene solo una stringa informativa. In genere, il valore è un `reg_dword` impostato su 0.|  
  
### <a name="example"></a>Esempio  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {EEFA5220-E298-11D0-8F78-00A0C9110057}\  
              Visibility\  
                (Default) = reg_sz:  
                {93694fa0-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
                {9DA22B82-6211-11d2-9561-00600818403B} = reg_dword: 0x00000000  
                {adfc4e66-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Pacchetti VSPackage](../extensibility/internals/vspackages.md)