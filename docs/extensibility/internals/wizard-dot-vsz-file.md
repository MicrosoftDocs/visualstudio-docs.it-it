---
title: Procedura guidata (. File vsz) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .vsz files
- vsz files
- wizards, files
ms.assetid: 72e1d0f3-eef1-455e-b803-96827f030f50
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f70d41b353640a3b2b108a55f14b8737a7fe1f8d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="wizard-vsz-file"></a>Procedura guidata (. File vsz)
Ambiente di sviluppo integrato (IDE) Usa file vsz per avviare le procedure guidate. Questi file VSZ contengono informazioni utilizzate per determinare quale procedura guidata per chiamare l'IDE e le informazioni da passare alla procedura guidata.  
  
 Un file VSZ è una versione di un file di testo in formato INI che non dispone di sezioni. Le informazioni note all'IDE viene archiviate all'inizio del file. Fornisce un collegamento tra la procedura guidata che chiama l'IDE e i parametri nel file vsz deve essere passato all'IDE. Il resto del file fornisce parametri che sono specifiche per la procedura guidata e che devono essere raccolti dall'IDE e passato alla procedura guidata specifica.  
  
 Nell'esempio seguente viene illustrato il contenuto di un file vsz.  
  
```  
VSWizard 8.0  
Wizard=VsWizard.CBlankSiteWizard -or- {123-1234556-123334}  
Param="WIZARDNAME = Wizard One"  
Param="WIZARDUI = FALSE"  
```  
  
 Di seguito sono le parti nel file vsz.  
  
|Parte|Descrizione|  
|----------|-----------------|  
|VSWizard|Il primo parametro nel file è il numero di versione del formato di file del modello. Questo numero di versione deve essere 6.0, 7.0, 7.1 o 8.0. Altri numeri non possono essere avviati e causano un errore di formato non valido.|  
|Wizard|Questo campo contiene OLE ProgID della procedura guidata o in alternativa una rappresentazione di stringa GUID del CLSID della procedura guidata che viene cocreata dall'IDE.|  
|Param|Queste parti sono facoltative. È possibile aggiungere un massimo di richieste.|  
  
 I parametri di attivare il file VSZ passare parametri personalizzati aggiuntivi per la procedura guidata. Ogni valore viene passato come un elemento di stringa in una matrice di varianti per la procedura guidata. Per ulteriori informazioni, vedere [parametri personalizzati](../../extensibility/internals/custom-parameters.md). Per informazioni su come utilizzare un file vsz per lo sviluppo di creazioni guidate personalizzate, vedere [. File VSZ (controllo progetto)](/cpp/ide/dot-vsz-file-project-control)  
  
 Per aggiungere un ID impostazioni locali predefinito nel file VSZ, specificare `FALLBACK_LCID`= xxxx, dove xxxx è l'ID delle impostazioni locali, ad esempio 1033 per l'inglese. Quando `FALLBACK_LCID` parametro è definito, la procedura guidata utilizza l'ID impostazioni locali di fallback specificato, se non viene trovato l'ID corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [Parametri personalizzati](../../extensibility/internals/custom-parameters.md)   
 [Procedure guidate](../../extensibility/internals/wizards.md)   
 [File (con estensione vsdir) di descrizione della directory dei modelli](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)