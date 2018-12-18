---
title: 'Procedura: personalizzare un pacchetto di soluzione SharePoint | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerAdvanced
- VS.SharePointTools.RAD.PackageDesigner.Manifest
- VS.SharePointTools.RAD.PackageDesignerProperties
- VS.SharePointTools.RAD.PackageDesigner.SwitchView
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9ffe532653abf58e4af6297e69c1049a916144cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>Procedura: personalizzare un pacchetto della soluzione SharePoint
  È possibile utilizzare la finestra di progettazione del pacchetto per creare e personalizzare un pacchetto (con estensione wsp). Ad esempio, è possibile aggiungere elementi di progetto SharePoint e le funzionalità, specificare se il server Web viene reimpostato quando viene distribuita la soluzione e impostare il tipo di server di distribuzione.  
  
## <a name="opening-the-package-designer"></a>La finestra di progettazione del pacchetto  
  
#### <a name="to-open-the-package-designer"></a>Per aprire la finestra di progettazione del pacchetto  
  
-   In **Esplora**, fare doppio clic su **pacchetto**, oppure scegliere **Visualizza finestra di progettazione** nel menu di scelta rapida per **pacchetto**.  
  
## <a name="viewing-the-packaged-manifest-file"></a>Visualizzazione del File manifesto nel pacchetto  
 È possibile utilizzare la finestra di progettazione del pacchetto per modificare e generare il file manifesto nel pacchetto. Quindi, è possibile visualizzare il codice XML per questo file in Visual Studio.  
  
#### <a name="to-view-the-xml-source-file"></a>Per visualizzare il file di origine XML  
  
1.  Nel **Progettazione pacchetti**, scegliere **manifesto**.  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Per visualizzare il file manifesto nel pacchetto utilizzando Esplora soluzioni  
  
1.  In **Esplora**, scegliere **Mostra tutti i file**.  
  
2.  Espandere pacchetto package. package espandere e quindi aprire il file Package.Template.xml.  
  
    > [!NOTE]  
    >  Quando si apre il file manifesto XML per il modello di pacchetto, i file vengono convalidati automaticamente, ed è possibile ignorare gli avvisi visualizzati nella finestra Elenco errori.  
  
## <a name="changing-the-manifest-template"></a>La modifica del modello di manifesto  
 È possibile modificare il codice XML per il file manifesto nel pacchetto nell'Editor XML di Visual Studio o nel riquadro modello di manifesto. Tutte le modifiche al codice XML vengono unite nel file manifesto nel pacchetto per il pacchetto.  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Per modificare il modello di manifesto tramite l'Editor XML  
  
1.  Nel **Progettazione pacchetti**, scegliere il **manifesto** scheda, espandere il **opzioni di modifica** nodo e quindi scegliere il **aperto nell'Editor XML** collegamento.  
  
     Le modifiche al codice XML vengono unite nel file manifesto nel pacchetto.  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Per modificare il modello di manifesto tramite il riquadro modello di manifesto  
  
1.  Nel **Progettazione pacchetti**, scegliere il **manifesto** scheda, espandere il **opzioni di modifica** nodo e quindi modificare il codice XML che viene visualizzata nel riquadro modello di manifesto.  
  
     Le modifiche al codice XML visualizzato nel **anteprima del manifesto nel pacchetto** riquadro.  
  
## <a name="overwriting-the-packaged-manifest-file"></a>Sovrascrivere il File manifesto nel pacchetto  
 È possibile disattivare la finestra di progettazione del pacchetto e creare manualmente il file manifest. La prima volta che si esegue questa procedura, le impostazioni correnti nella finestra di progettazione del pacchetto vengono salvate in file XML del modello di pacchetto. Quindi, è possibile modificare o sovrascrivere il codice XML.  
  
> [!NOTE]  
>  Se si aggiunge o rimuovere elementi di progetto SharePoint e funzionalità nel file XML, mentre la finestra di progettazione del pacchetto è disabilitato, questi elementi di progetto e la funzionalità non sono inclusi nel pacchetto.  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Per sovrascrivere il file manifesto disabilitando la finestra di progettazione  
  
1.  Nel **Progettazione pacchetti**, scegliere il **manifesto** scheda.  
  
2.  .  
  
3.  Espandere il **opzioni di modifica** nodo, scegliere il **Sovrascrivi XML e modifica manifesto generato nell'editor XML** collegamento e quindi scegliere il **Sì** pulsante.  
  
     Il modello viene aggiornato con il file manifesto nel pacchetto corrente.  
  
## <a name="enabling-the-package-designer"></a>Abilitare la finestra di progettazione del pacchetto  
 È possibile abilitare nuovamente la finestra di progettazione del pacchetto per personalizzare il file manifest.  
  
#### <a name="to-re-enable-the-designer"></a>Per abilitare nuovamente la finestra di progettazione  
  
1.  Nel **Progettazione pacchetti**, scegliere il **Ignora modifiche al manifesto e riabilita la finestra di progettazione** collegamento e quindi scegliere il **Sì** pulsante.  
  
     Il modello viene aggiornato con il testo originale e le modifiche al codice XML vengono perse.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  