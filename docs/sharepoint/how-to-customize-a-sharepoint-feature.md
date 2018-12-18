---
title: "Procedura: personalizzare una funzionalità SharePoint | Documenti Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner.SwitchView
- VS.SharePointTools.RAD.featureDesigner.Manifest
- VS.SharePointTools.RAD.FeatureDesignerProperties
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, features
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: adb4283a56715da704df8991543ea89c6cbc79a4
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-customize-a-sharepoint-feature"></a>Procedura: personalizzare una funzionalità SharePoint
  È possibile creare e personalizzare le funzionalità di SharePoint utilizzando la finestra di progettazione di funzionalità in Visual Studio. Ad esempio, è possibile impostare l'ambito della funzionalità e aggiungere altre funzionalità come dipendenze. Per impostazione predefinita, la funzionalità di progettazione viene aperto quando si aggiunge una nuova funzionalità in Esplora soluzioni o Esplora pacchetti di SharePoint.  
  
## <a name="opening-the-feature-designer"></a>La finestra di progettazione di funzionalità  
 È possibile aggiungere o rimuovere elementi di progetto SharePoint a una funzionalità tramite la finestra di progettazione di funzionalità.  
  
#### <a name="to-open-the-feature-designer"></a>Per aprire la finestra di progettazione di funzionalità  
  
1.  In **Esplora**, espandere **funzionalità**.  
  
2.  Fare doppio clic su di *Feature1* , o di elemento di aprire il menu di scelta rapida per il *Feature1* elemento e quindi scegliere **Visualizza finestra di progettazione**.  
  
## <a name="viewing-the-packaged-manifest-file"></a>Visualizzazione del File manifesto nel pacchetto  
 È possibile utilizzare la finestra di progettazione di funzionalità per modificare e generare il file manifesto nel pacchetto per la funzionalità (feature). Quindi, è possibile visualizzare il codice XML per questo file in Visual Studio.  
  
#### <a name="to-view-the-packaged-manifest-file"></a>Per visualizzare il file manifesto nel pacchetto  
  
1.  Nel **Progettazione funzionalità**, scegliere il **manifesto** scheda.  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Per visualizzare il file manifesto nel pacchetto utilizzando Esplora soluzioni  
  
1.  In **Esplora**, scegliere il **Mostra tutti i file** icona.  
  
2.  Espandere le funzionalità, espandere NomeFunzionalità, espandere FeatureName.feature e quindi aprire il *FeatureName*. File template. Xml.  
  
    > [!NOTE]  
    >  Quando si apre il file XML manifesto modello funzionalità, i file vengono convalidati automaticamente ed è possono ignorare gli avvisi visualizzati nella finestra Elenco errori.  
  
## <a name="changing-the-manifest-template"></a>La modifica del modello di manifesto  
 È possibile modificare il codice XML per il file manifesto di funzionalità nell'Editor XML di Visual Studio o nel riquadro modello di manifesto. Tutte le modifiche al codice XML viene unito al file manifesto nel pacchetto per la funzionalità. Potrebbe ad esempio, si desidera modificare il modello di manifesto per personalizzare una proprietà della funzionalità.  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Per modificare il modello di manifesto tramite l'Editor XML  
  
1.  Nel **Progettazione funzionalità**, scegliere il **manifesto** scheda, espandere il **opzioni di modifica** nodo e quindi scegliere il **aperto nell'Editor XML** collegamento.  
  
     Le modifiche al codice XML vengono unite nel file manifesto nel pacchetto.  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Per modificare il modello di manifesto tramite il riquadro modello di manifesto  
  
1.  Nel **Progettazione funzionalità**, scegliere il **manifesto** scheda, espandere il **opzioni di modifica** nodo e quindi modificare il codice XML che viene visualizzata nel riquadro modello di manifesto.  
  
     Le modifiche al codice XML visualizzato nel **anteprima del manifesto nel pacchetto** riquadro.  
  
## <a name="overwriting-the-packaged-manifest-file"></a>Sovrascrivere il File manifesto nel pacchetto  
 È possibile disabilitare la funzionalità di progettazione e creare manualmente il file feature. La prima volta che si esegue questa procedura, le impostazioni correnti nella finestra di progettazione delle funzionalità vengono salvate in file XML del modello di funzione. Quindi, è possibile modificare o sovrascrivere il codice XML.  
  
> [!NOTE]  
>  Se si aggiungono o rimuovono elementi di progetto SharePoint nel file XML, mentre la finestra di progettazione di funzionalità è disabilitata, questi elementi di progetto non vengono inclusi nel pacchetto.  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Per sovrascrivere il file manifesto disabilitando la finestra di progettazione  
  
1.  Nel **Progettazione funzionalità**, scegliere il **manifesto** scheda.  
  
2.  Espandere il **opzioni di modifica** nodo, scegliere il **Sovrascrivi XML e modifica manifesto generato nell'editor XML** collegamento e quindi scegliere il **Sì** pulsante.  
  
     Il modello viene aggiornato con il file manifesto nel pacchetto corrente.  
  
## <a name="enabling-the-feature-designer"></a>La finestra di progettazione di funzionalità di attivazione  
 È possibile abilitare nuovamente la finestra di progettazione di funzionalità per personalizzare il file feature.  
  
#### <a name="to-re-enable-the-designer"></a>Per abilitare nuovamente la finestra di progettazione  
  
1.  Nel **Progettazione funzionalità**, scegliere il **Ignora modifiche al manifesto e riabilita la finestra di progettazione** collegamento e quindi scegliere il **Sì** pulsante.  
  
2.  Il modello viene aggiornato con il testo originale e le modifiche al codice XML vengono perse.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  