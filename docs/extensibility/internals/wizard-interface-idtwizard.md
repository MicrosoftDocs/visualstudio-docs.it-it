---
title: Creazione guidata interfaccia (IDTWizard) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 57e3ceda07abadbf00e67e740bd276430157eabe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="wizard-interface-idtwizard"></a>Creazione guidata interfaccia (IDTWizard)
Ambiente di sviluppo integrato (IDE) usa il <xref:EnvDTE.IDTWizard> interfaccia per comunicare con le procedure guidate. Procedure guidate devono implementare questa interfaccia per essere installato nell'IDE.  
  
 Il <xref:EnvDTE.IDTWizard.Execute%2A> è il solo metodo associato il <xref:EnvDTE.IDTWizard> interfaccia. Procedure guidate implementano questo metodo e l'IDE chiama il metodo sull'interfaccia. Nell'esempio seguente viene illustrata la firma del metodo.  
  
```  
/* IDTWizard Method */  
STDMETHOD(Execute)(THIS_  
   /* [in] */ IDispatch *Application,  
   /* [in] */ long hwndOwner,  
   /* [in] */ SAFEARRAY * *ContextParams,  
   /* [in] */ SAFEARRAY * *CustomParams,  
   /* [out] [in] */ wizardResult *RetVal  
   );  
```  
  
 Il meccanismo di avvio è simile per entrambi i **nuovo progetto** e **Aggiungi nuovo elemento**procedure guidate. Per avviare uno, si chiama il <xref:EnvDTE.IDTWizard> interfaccia definita in Dteinternal.h. L'unica differenza è il set di contesto e i parametri personalizzati che vengono passati all'interfaccia quando viene chiamato l'interfaccia.  
  
 Le informazioni seguenti illustrano il <xref:EnvDTE.IDTWizard> interfaccia che devono implementare le procedure guidate per utilizzare il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Le chiamate a IDE il <xref:EnvDTE.IDTWizard.Execute%2A> metodo della procedura guidata, passando le operazioni seguenti:  
  
-   L'oggetto DTE  
  
     L'oggetto DTE è la radice del modello di automazione.  
  
-   L'handle di finestra di dialogo come illustrato nel segmento di codice, `hwndOwner ([in] long)`.  
  
     La procedura guidata utilizza questo `hwndOwner` come elemento padre per la creazione guidata finestra di dialogo.  
  
-   Parametri di contesto passato all'interfaccia di tipo variant per SAFEARRAY come illustrato nel segmento di codice, `[in] SAFEARRAY (VARIANT)* ContextParams`.  
  
     Parametri di contesto contengono una matrice di valori che sono specifiche per il tipo di procedura guidata in corso l'avvio e lo stato corrente del progetto. L'IDE passa i parametri di contesto per la procedura guidata. Per ulteriori informazioni, vedere [parametri di contesto](../../extensibility/internals/context-parameters.md).  
  
-   Parametri personalizzati passato all'interfaccia di un tipo variant per SAFEARRAY come illustrato nel segmento di codice, `[in] SAFEARRAY (VARIANT)* CustomParams`.  
  
     I parametri personalizzati contengono una matrice di parametri definiti dall'utente. Un file VSZ passa i parametri personalizzati all'IDE. I valori vengono determinati dalle `Param=` istruzioni. Per ulteriori informazioni, vedere [parametri personalizzati](../../extensibility/internals/custom-parameters.md).  
  
-   I valori restituiti per l'interfaccia da  
  
    ```  
    wizardResultSuccess = -1,  
    wizardResultFailure = 0  
    wizardResultCancel = 1  
    wizardResultBackout = 2  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Parametri di contesto](../../extensibility/internals/context-parameters.md)   
 [Parametri personalizzati](../../extensibility/internals/custom-parameters.md)   
 [Procedure guidate](../../extensibility/internals/wizards.md)   
 [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)