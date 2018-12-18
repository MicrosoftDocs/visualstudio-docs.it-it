---
title: "Procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto utilizzando Esplora pacchetti | Documenti Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 25a2514f2d25661de2898be8d2ef9ff051cc5559
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>Procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto utilizzando Esplora pacchetti
  Per configurare un pacchetto per distribuire gli elementi di SharePoint e le funzionalità, è possibile utilizzare Esplora pacchetti. È possibile regolare gli elementi di progetto SharePoint e le funzionalità all'interno del file con estensione wsp.  
  
 In alternativa, è possibile utilizzare la finestra di progettazione di pacchetti per visualizzare e riordinare le funzionalità per modificare l'ordine di attivazione. Per ulteriori informazioni, vedere [procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto utilizzando la finestra di progettazione del pacchetto](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
## <a name="opening-the-packaging-explorer"></a>Apertura di Esplora pacchetti  
 Se la soluzione di Visual Studio contiene almeno un progetto SharePoint, è possibile utilizzare la procedura seguente per aprire Esplora pacchetti. In alternativa, Esplora pacchetti viene aperta automaticamente quando si visualizza una finestra di progettazione di funzionalità o il pacchetto. Dopo aver chiuso tutte le finestre di progettazione di funzionalità e del pacchetto, viene chiusa anche Esplora pacchetti.  
  
#### <a name="to-open-the-packaging-explorer"></a>Per aprire Esplora pacchetti  
  
1.  Nella barra dei menu, scegliere **vista**, **altre finestre**, **Esplora pacchetti**.  
  
     Il **Esplora pacchetti** è presente il **della casella degli strumenti**.  
  
## <a name="adding-a-feature-to-a-package"></a>Aggiunta di una funzionalità a un pacchetto  
 È possibile aggiungere le funzionalità nuove ed esistenti a un pacchetto utilizzando Esplora pacchetti.  
  
#### <a name="to-add-a-sharepoint-feature"></a>Per aggiungere una funzionalità di SharePoint  
  
1.  Aprire il **Esplora pacchetti**, aprire il menu di scelta rapida per il progetto e quindi scegliere **Aggiungi funzionalità**.  
  
#### <a name="to-move-an-existing-sharepoint-feature"></a>Per spostare una funzionalità di SharePoint esistente  
  
1.  Aprire il **Esplora pacchetti**e quindi effettuare una delle operazioni seguenti:  
  
    -   Trascinare un **funzionalità** da un progetto a un altro progetto.  
  
    -   Aprire il menu di scelta rapida per una funzionalità, scegliere **Taglia**, aprire il menu di scelta rapida per il progetto a cui si desidera spostare la funzionalità, quindi scegliere **Incolla**.  
  
    > [!NOTE]  
    >  Utilizzare questa procedura se nella soluzione sono presenti diversi progetti SharePoint.  
  
## <a name="validating-a-feature-or-package"></a>Convalida di una funzione o un pacchetto  
 È possibile identificare potenziali problemi in pacchetti e le funzionalità di SharePoint convalidando i file. Errori e avvisi vengono visualizzati nella finestra Elenco errori e la finestra di Output.  
  
#### <a name="to-validate-a-sharepoint-feature-or-package"></a>Per convalidare un pacchetto o una funzionalità SharePoint  
  
1.  Aprire il **Esplora pacchetti**.  
  
2.  Aprire un menu di scelta rapida per una funzione o un pacchetto e quindi scegliere **convalida**.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  