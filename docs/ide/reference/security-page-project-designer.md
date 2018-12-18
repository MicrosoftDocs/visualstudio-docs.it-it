---
title: Pagina Sicurezza, Creazione progetti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- vb.ProjectPropertiesSecurity
- vb.XBAPProjectPropertiesSecurity
helpviewer_keywords:
- Project Designer, Security page
- Security page in Project Designer
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 749cf38a70f8d6ab4c53c6c198a42412a4aa3f90
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="security-page-project-designer"></a>Pagina Sicurezza, Progettazione progetti
La pagina **Sicurezza** di **Creazione progetti** viene usata per configurare le impostazioni di sicurezza per l'accesso al codice per le applicazioni distribuite usando la distribuzione [!INCLUDE[ndptecclick](../../deployment/includes/ndptecclick_md.md)]. Per altre informazioni, vedere [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).  
  
 Per accedere alla pagina **Sicurezza**, fare clic su un nodo di progetto in **Esplora soluzioni** e quindi scegliere **Proprietà** dal menu **Progetto**. Quando viene visualizzata la finestra **Creazione progetti** fare clic sulla scheda **Sicurezza**.  
  
## <a name="security-settings"></a>Impostazioni di sicurezza  
 **Abilita impostazioni di sicurezza ClickOnce**  
 Determina se le impostazioni di sicurezza sono abilitate in fase di progettazione. Se questa opzione è deselezionata, tutte le altre opzioni della pagina **Sicurezza** non sono disponibili.  
  
> [!NOTE]
>  Quando si pubblica un'applicazione usando la procedura guidata di **pubblicazione** questa opzione è abilitata automaticamente.  
  
 Quando si seleziona questa opzione, è possibile selezionare uno dei due pulsanti di opzione disponibili: **È un'applicazione con attendibilità totale** o **È un'applicazione con attendibilità parziale**.  
  
 Per impostazione predefinita, l'opzione è selezionata per i progetti Applicazione Web browser WPF.  
  
 Per impostazione predefinita, per tutti gli altri tipi di progetto l'opzione è deselezionata.  
  
 **È un'applicazione con attendibilità totale**  
 Se si seleziona questa opzione, l'applicazione richiede le autorizzazioni Attendibilità totale quando è installata o eseguita in un computer client. Evitare l'uso dell'attendibilità totale, se possibile, perché all'applicazione verrà concesso l'accesso illimitato a risorse come il file system e il registro.  
  
 Per impostazione predefinita, l'opzione è impostata su Attendibilità parziale per i progetti Applicazione Web browser WPF.  
  
 Per impostazione predefinita, per tutti gli altri tipi di progetto l'opzione è impostata su Attendibilità totale.  
  
 **È un'applicazione parzialmente attendibile**  
 Se si seleziona questa opzione, l'applicazione richiede le autorizzazioni Attendibilità parziale quando è installata o eseguita in un computer client. *Attendibilità parziale* significa che verranno eseguite solo le azioni consentite dalle autorizzazioni di sicurezza dall'accesso di codice richieste. Per altre informazioni sulla configurazione delle autorizzazioni di sicurezza, vedere [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).  
  
 È possibile specificare le impostazioni di sicurezza con attendibilità parziale configurando le opzioni dell'area **Autorizzazioni di sicurezza ClickOnce**.  
  
## <a name="clickonce-security-permissions"></a>Autorizzazioni di sicurezza ClickOnce  
 **Zona da cui verrà installata l'applicazione**  
 Specifica un set predefinito di autorizzazioni di sicurezza dall'accesso di codice. Scegliere **Internet** o **Intranet locale** per un set di autorizzazioni oppure **(Personalizzato)** per configurare un set di autorizzazioni personalizzato. Se l'applicazione richiede più autorizzazioni rispetto a quelle concesse in una zona, viene visualizzata una richiesta di attendibilità ClickOnce per l'utente finale per la concessione delle autorizzazioni aggiuntive. Per altre informazioni sulla configurazione delle autorizzazioni di sicurezza, vedere [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).  
  
 Per impostazione predefinita, l'opzione è impostata su **Internet** per i progetti Applicazione Web browser WPF.  
  
 **Modifica XML autorizzazioni**  
 Apre il modello di manifesto dell'applicazione (app.manifest) per configurare le autorizzazioni per il set di autorizzazioni **(Personalizzato)**.  
  
 **Avanzate**  
 Apre la [finestra di dialogo Impostazioni di sicurezza avanzate](../../ide/reference/advanced-security-settings-dialog-box.md), che consente di configurare le impostazioni per il debug dell'applicazione con autorizzazioni con restrizioni. Queste impostazioni vengono controllate durante il debug e le eccezioni delle autorizzazioni indicano che l'applicazione può richiedere più autorizzazioni oltre a quelle definite in una zona.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Security.Permissions.WebBrowserPermission>   
 <xref:System.Security.Permissions.MediaPermission>   
 [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md)   
 [How to: Enable ClickOnce Security Settings](../../deployment/how-to-enable-clickonce-security-settings.md)  (Procedura: Abilitare le impostazioni di sicurezza ClickOnce)  
 [Procedura: impostare un'area di sicurezza per un'applicazione ClickOnce](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Procedura: impostare le autorizzazioni personalizzate per un'applicazione ClickOnce](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Procedura: eseguire il debug di un'applicazione ClickOnce con autorizzazioni limitate](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Sicurezza e distribuzione di ClickOnce](../../deployment/clickonce-security-and-deployment.md)   
 [Riferimenti alle proprietà di progetto](../../ide/reference/project-properties-reference.md)   
 [Finestra di dialogo Impostazioni di sicurezza avanzate](../../ide/reference/advanced-security-settings-dialog-box.md)