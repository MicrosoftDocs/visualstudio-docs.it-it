---
title: Estendere i diagrammi di dipendenza | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-modeling
ms.topic: article
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 3d3358d5e74b121bcf670a0092f3064882d6960b
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="extend-dependency-diagrams"></a>Estendere i diagrammi di dipendenza
È possibile scrivere codice per creare e aggiornare i diagrammi di dipendenza e per convalidare la struttura del codice programma in base ai diagrammi di dipendenza in Visual Studio. È possibile aggiungere comandi da visualizzare nel menu di scelta rapida (contestuale) dei diagrammi, personalizzare i movimenti di trascinamento della selezione e accedere al modello di livello dai modelli di testo. È possibile creare un pacchetto di queste estensioni in un progetto VSIX (Visual Studio Integration Extension) e distribuirle ad altri utenti di Visual Studio.  
  
 Per ulteriori informazioni sui diagrammi di dipendenza, vedere:  
  
-   [Diagrammi delle dipendenze: riferimenti](../modeling/layer-diagrams-reference.md)  
  
-   [Diagrammi delle dipendenze: linee guida](../modeling/layer-diagrams-guidelines.md)  
  
-   [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Convalidare il codice con i diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)  
  
##  <a name="prereqs"></a> Requisiti  
 È necessario verificare che nel computer in cui si vogliono sviluppare le estensioni del livello sia installato quanto segue:  
  
-   Visual Studio  
  
-   [Visual Studio SDK](../extensibility/visual-studio-sdk.md)  
  
-   SDK di modellazione per Visual Studio  


[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

  
 È necessario avere installato una versione appropriata di Visual Studio nel computer in cui si vogliono eseguire le estensioni del livello. Per ulteriori informazioni, vedere [distribuire un'estensione del modello di livello](../modeling/deploy-a-layer-model-extension.md).  
  
 Per le versioni di Visual Studio che supportano i diagrammi di dipendenza, vedere [supporto della versione per l'architettura e strumenti di modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="in-this-section"></a>In questa sezione  
 [Aggiungere comandi e movimenti ai diagrammi delle dipendenze](../modeling/add-commands-and-gestures-to-layer-diagrams.md)  
  
 [Aggiungere strumenti di convalida dell'architettura personalizzati ai diagrammi delle dipendenze](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)  
  
 [Aggiungere proprietà personalizzate ai diagrammi delle dipendenze](../modeling/add-custom-properties-to-layer-diagrams.md)  
  
 [Esplorare e aggiornare i modelli di livello nel codice del programma](../modeling/navigate-and-update-layer-models-in-program-code.md)  
  
 [Distribuire un'estensione del modello di livello](../modeling/deploy-a-layer-model-extension.md)  
  
 [Risolvere i problemi relativi alle estensioni per i diagrammi delle dipendenze](../modeling/troubleshoot-extensions-for-layer-diagrams.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Diagrammi di dipendenza: riferimento](../modeling/layer-diagrams-reference.md)   
 [Diagrammi di dipendenza: linee guida](../modeling/layer-diagrams-guidelines.md)   
 [Creare diagrammi dipendenza dal codice](../modeling/create-layer-diagrams-from-your-code.md)   
 [Convalidare il codice con i diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)   
