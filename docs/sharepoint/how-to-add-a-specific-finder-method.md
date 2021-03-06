---
title: 'Procedura: aggiungere un metodo Finder specifico | Microsoft Docs'
description: Ottenere un'istanza di entità aggiungendo un metodo Finder. Il servizio BDC chiama il metodo quando un utente seleziona un'entità in una Web part dati business o in un elenco esterno.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], Specific Finder
- BDC [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], get an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], return an entity
- BDC [SharePoint development in Visual Studio], Specific Finder
- Business Data Connectivity service [SharePoint development in Visual Studio], get an entity
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 87f5b0cf86178b88b1611f4b0ce8a4bbacde780e
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216800"
---
# <a name="how-to-add-a-specific-finder-method"></a>Procedura: aggiungere un metodo Finder specifico
  Per restituire una singola istanza di entità, è possibile creare un metodo di *ricerca specifico* . Il servizio di integrazione applicativa dei dati esegue il metodo di ricerca specifico quando un utente sceglie un'entità in una Web part dati business o in un elenco esterno. Per ulteriori informazioni, vedere [progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-specific-finder-method"></a>Per creare un metodo Finder specifico

1. Nella **finestra di progettazione dell'integrazione applicativa** dei dati scegliere un'entità.

    Per informazioni su come aggiungere un'entità alla finestra di **progettazione dell'integrazione applicativa** dei dati in Visual Studio, vedere [procedura: aggiungere un'entità a un modello](../sharepoint/how-to-add-an-entity-to-a-model.md).

2. Sulla barra dei menu scegliere **Visualizza**  >  **altre finestre**, **Dettagli metodo di integrazione applicativa dei dati**.

    Verrà visualizzata la finestra **Dettagli metodo BDC** . Per ulteriori informazioni su tale finestra, vedere [Panoramica degli strumenti di progettazione dei modelli BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. Nell'elenco **Aggiungi metodo** scegliere **Crea metodo di ricerca specifico**.

    Visual Studio aggiunge al modello gli elementi seguenti. Questi elementi vengono visualizzati nella finestra **Dettagli metodo di integrazione applicativa dei dati** .

   - Un metodo.

   - Parametro di input per il metodo.

   - Parametro restituito per il metodo.

   - Descrittore di tipo per ogni parametro.

   - Istanza di metodo per il metodo.

     Per ulteriori informazioni, vedere [progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).

4. Aprire la finestra **Proprietà** di Visual Studio.

5. Configurare il descrittore di tipo del parametro restituito come descrittore del tipo di entità. Per informazioni su come creare un descrittore di tipo di entità, vedere [procedura: definire il descrittore di tipo di un parametro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

   > [!NOTE]
   > Non è necessario eseguire questo passaggio se è stato aggiunto un metodo di ricerca all'entità. Visual Studio usa il descrittore di tipo definito nel metodo Finder.

   > [!NOTE]
   > Se il campo identificatore del tipo di entità rappresenta un campo in una tabella di database generata automaticamente, impostare la proprietà di sola **lettura** del campo identificatore su **true**.

6. Nella finestra **Dettagli metodo** scegliere l'istanza del metodo del metodo.

7. Nella **finestra Proprietà** impostare la proprietà **nome parametro restituito** sul nome del parametro restituito del metodo. Per ulteriori informazioni sulle proprietà dell'istanza del metodo, vedere [oggetto MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)).

8. In **Esplora soluzioni** aprire il menu di scelta rapida del file di codice del servizio generato per l'entità, quindi scegliere **Visualizza codice**.

    Il file di codice di Entity Service verrà aperto nell'editor di codice. Per altre informazioni sul file di codice di Entity Service, vedere [creare un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md).

9. Aggiungere codice al metodo Finder specifico. Il codice esegue queste operazioni:

   - Recupera un record da un'origine dati.

   - Restituisce un'entità al servizio di integrazione applicativa dei dati.

     Nell'esempio seguente viene restituito un contatto dal database di esempio AdventureWorks per SQL Server.

     > [!NOTE]
     > Sostituire il valore del `ServerName` campo con il nome del server.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet3":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet3":::

## <a name="see-also"></a>Vedi anche
- [Progettare un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Procedura: aggiungere un metodo di aggiornamento](../sharepoint/how-to-add-an-updater-method.md)
- [Panoramica degli strumenti di progettazione dei modelli BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Procedura: definire un'istanza di metodo](../sharepoint/how-to-define-a-method-instance.md)
