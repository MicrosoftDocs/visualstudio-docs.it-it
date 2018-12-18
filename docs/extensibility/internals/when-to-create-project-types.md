---
title: Quando creare tipi di progetto | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 732d71e09d00cd5dbaa077b8a62e240fe401540b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="when-to-create-project-types"></a>Quando creare tipi di progetto
Creare un nuovo tipo di progetto fornisce una base per la personalizzazione [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per gli utenti. Tuttavia, creare un nuovo tipo di progetto non è obbligatorio per tutti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] personalizzazioni. Le linee guida seguenti consentono di determinare se un nuovo tipo di progetto è obbligatorio per lo scenario.  
  
## <a name="create-a-new-project-type"></a>Creare un nuovo tipo di progetto  
 È necessario creare un tipo di progetto se si desidera personalizzare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di agire in uno o più dei modi seguenti:  
  
-   Partecipa a compilazione, distribuzione, le configurazioni e controllo del codice sorgente.  
  
-   Offre supporto per il debug.  
  
-   Visualizzare gli elementi di progetto in **Esplora**.  
  
-   Utilizzare il **Apri progetto** o **nuovo progetto** la finestra di dialogo.  
  
-   Supporta l'annidamento di progetto.  
  
## <a name="extend-an-existing-project-type"></a>Estendere un tipo di progetto esistente  
 Si potrebbe voler creare un nuovo tipo di progetto che è possibile utilizzare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nei modi seguenti per modificare o estendere il comportamento di un tipo di progetto esistente, ad esempio, la modifica del processo di compilazione per [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] progetti:  
  
-   Come una singola unità di lavoro con più file.  
  
-   Visualizzare un singolo file come una gerarchia di elementi secondari.  
  
-   Visualizzare un contesto di comando per l'editor.  
  
-   Visualizzare un contesto del servizio per gli editor.  
  
## <a name="use-an-existing-project-type"></a>Utilizzare un tipo di progetto esistente  
 Crea un nuovo progetto in alcuni casi non è necessario. Nella tabella seguente sono elencate le attività che non si dispone di un tipo di progetto per creare.  
  
|Attività|Descrizione|  
|----------|-----------------|  
|Gestione dei comandi|Qualsiasi pacchetto VSPackage può gestire i comandi.|  
|La creazione di un editor|Editor personalizzati possono essere registrati. Per ulteriori informazioni, vedere [editor e finestre di documento](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc).|  
|Proprietario di windows|È possibile creare documenti e degli strumenti di windows senza aggiungere un nuovo tipo di progetto.|  
|Esposizione delle proprietà nella finestra proprietà|Tutti gli oggetti possono esporre le proprietà.|  
  
## <a name="create-a-project-subtype"></a>Creare un sottotipo di progetto  
 È possibile utilizzare i sottotipi di progetto per estendere un tipo di progetto gestito senza la necessità di creare un nuovo tipo di progetto. Sottotipi di progetto usare aggregazione COM per estendere i progetti gestiti, scritti in Microsoft [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Con l'aggregazione COM, è possibile riutilizzare la maggior parte dell'implementazione di sistema di progetto gestito e personalizzare per un determinato scenario tramite l'aggregazione e l'utilizzo di interfacce di supporto. Per ulteriori informazioni su sottotipi di progetto, vedere [sottotipi di progetto](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Editor e finestre di documento](http://msdn.microsoft.com/en-us/603625e1-62b6-413a-bc44-089346e166bc)   
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)