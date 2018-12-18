---
title: "Procedura: aggiungere e rimuovere dipendenze di funzionalità | Documenti Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW
- VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY
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
ms.openlocfilehash: 6e74ac8cef88319a54df0c08cd91fb2654d390cb
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-and-remove-feature-dependencies"></a>Procedura: aggiungere e rimuovere dipendenze di funzionalità
  La funzionalità di SharePoint può dipendere da altre funzionalità per la funzionalità o dati. In questi casi, è possibile contrassegnare queste altre funzionalità come dipendenze per le funzionalità. In questo modo, il server SharePoint garantisce che le funzionalità dipendenti vengono attivate prima che venga attivata la funzionalità.  
  
## <a name="adding-dependencies"></a>Aggiunta di dipendenze  
 È possibile aggiungere altre funzionalità nella soluzione come dipendenze. In questo modo, è possibile assicurarsi che le funzionalità necessarie vengono installate e attivate prima di installata la funzionalità.  
  
#### <a name="to-add-a-dependency-on-a-feature-in-the-solution"></a>Per aggiungere una dipendenza su una funzionalità nella soluzione  
  
1.  Aprire la finestra di progettazione di funzionalità, espandere il **dipendenze di attivazione funzionalità** nodo, quindi scegliere il **Aggiungi** pulsante.  
  
2.  Nel **aggiungere dipendenze di attivazione funzionalità** finestra di dialogo scegliere la **aggiungere una dipendenza a funzionalità nella soluzione** pulsante di opzione, scegliere il titolo della funzionalità che si desidera aggiungere come una dipendenza, quindi Scegliere il **Aggiungi** pulsante.  
  
     È possibile aggiungere più funzionalità scegliendo più titoli e premendo il tasto Ctrl.  
  
## <a name="adding-custom-dependencies"></a>Aggiunta di dipendenze personalizzate  
 È possibile aggiungere le funzionalità che sono già state distribuite in un server SharePoint come dipendenza. In questo modo, il processo di attivazione di SharePoint consente di assicurarsi che tutte le funzionalità dipendenti vengono attivate prima di installata la funzionalità.  
  
#### <a name="to-add-a-dependency-by-the-feature-id"></a>Per aggiungere una dipendenza dall'ID di funzionalità  
  
1.  Aprire la finestra di progettazione di funzionalità, espandere il **dipendenze di attivazione funzionalità** nodo, quindi scegliere il **Aggiungi** pulsante.  
  
2.  Nel **aggiungere dipendenze di attivazione funzionalità** finestra di dialogo scegliere la **aggiungere una dipendenza personalizzata** pulsante di opzione.  
  
3.  Nel **ID funzionalità** testo immettere il GUID per la funzionalità che si desidera contrassegnare come una dipendenza di attivazione e quindi scegliere il **Aggiungi** pulsante.  
  
## <a name="editing-custom-dependencies"></a>Modifica di dipendenze personalizzate  
 È possibile modificare le dipendenze personalizzate aggiunto in precedenza. Tuttavia, le funzionalità dipendenti che sono nella soluzione possono solo essere rimosso, non modificato.  
  
#### <a name="to-change-a-dependency-on-a-feature-in-the-solution"></a>Per modificare una dipendenza da una funzionalità nella soluzione  
  
1.  Aprire la finestra di progettazione di funzionalità e quindi espandere il **dipendenze di attivazione funzionalità** nodo.  
  
2.  Scegliere il nome della funzionalità che si desidera modificare e quindi scegliere il **modifica** pulsante.  
  
3.  Nel **Modifica dipendenza di attivazione funzionalità personalizzata** la finestra di dialogo, modificare il titolo, un ID di funzionalità o una descrizione, quindi scegliere il **Invia** pulsante.  
  
## <a name="removing-dependencies"></a>Rimozione di dipendenze  
  
#### <a name="to-remove-a-dependency-on-a-feature-in-the-solution"></a>Per rimuovere una dipendenza da una funzionalità nella soluzione  
  
1.  Nella finestra di progettazione di funzionalità, espandere il **dipendenze di attivazione funzionalità** nodo, scegliere il nome della funzionalità che si desidera rimuovere e quindi scegliere il **rimuovere** pulsante.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di funzionalità SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Procedura: personalizzare una funzionalità SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Procedura: Aggiungere e rimuovere elementi alle funzionalità SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  