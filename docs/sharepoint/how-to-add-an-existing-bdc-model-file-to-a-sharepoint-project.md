---
title: 'Procedura: aggiungere un file modello di integrazione applicativa dei dati esistente a un progetto SharePoint | Microsoft Docs'
titleSuffix: ''
description: Aggiungere un file modello di integrazione applicativa dei dati (BDC) esistente a un progetto SharePoint in Visual Studio, in modo da poter personalizzare, creare un pacchetto e ridistribuire un modello di integrazione applicativa dei dati.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: af0768b4834eb1cad3654b6d74ee8f02cf464245
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882674"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Procedura: aggiungere un file modello di integrazione applicativa dei dati esistente a un progetto SharePoint
  È possibile personalizzare, creare un pacchetto e ridistribuire un modello di integrazione applicativa dei dati tramite Visual Studio per aggiungere il file di modello (con *estensione bdcm*) a qualsiasi progetto della farm di SharePoint. Per altre informazioni, vedere [creare un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md).

### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>Per aggiungere un file del modello di integrazione applicativa dei dati a un progetto SharePoint

1. In **Esplora soluzioni** scegliere la cartella per un progetto SharePoint.

2. Sulla barra dei menu scegliere **progetto**  >  **Aggiungi elemento esistente**.

3. Nella finestra di dialogo **Aggiungi elemento esistente** individuare il percorso del file di definizione del modello che si desidera aggiungere al progetto, scegliere il file, quindi fare clic sul pulsante **Aggiungi** .

    Se il modello non definisce un *sistema line-of-business (LOB) di tipo assembly .NET*, viene visualizzata la finestra di dialogo **Aggiungi LobSystem di assembly .NET** .

4. Se la finestra di dialogo viene visualizzata, effettuare una delle seguenti operazioni:

   - Se si desidera scrivere codice personalizzato e utilizzare una finestra di progettazione per definire i metadati per il modello importato, scegliere il pulsante **Sì** , assegnare un nome al sistema, quindi scegliere il pulsante **OK** .

   - In caso contrario, scegliere il pulsante **No** , quindi scegliere il pulsante **OK** .

     L'elemento **modello di integrazione applicativa dei dati** viene aggiunto al progetto.

## <a name="see-also"></a>Vedi anche
- [Creare un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Procedura: creare un modello di integrazione applicativa dei dati](../sharepoint/how-to-create-a-bdc-model.md)
- [Procedura: usare un file di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Procedura: includere un assembly personalizzato in una funzionalità di integrazione applicativa dei dati](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrazione di dati business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
