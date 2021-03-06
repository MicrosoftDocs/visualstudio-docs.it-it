---
title: Creazione di un'associazione tra entità | Microsoft Docs
description: Creare un'associazione tra entità nel modello di integrazione applicativa dei dati (Business Data Connectivity). Informazioni sui metodi e sui tipi di associazioni di associazione.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Association_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d40c4e5c5d61b9da3cdbdd3fe96f45c4a0cff929
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106213966"
---
# <a name="create-an-association-between-entities"></a>Creare un'associazione tra entità
  È possibile definire le relazioni tra entità nel modello di integrazione applicativa dei dati (Business Data Connectivity) creando associazioni. Visual Studio genera metodi che forniscono agli utenti del modello informazioni sulle singole associazioni. Questi metodi possono essere utilizzati da elenchi, applicazioni personalizzate o web part di SharePoint per visualizzare le relazioni tra i dati in un'interfaccia utente.

## <a name="create-an-association"></a>Creare un'associazione
 Creare un'associazione scegliendo il controllo **associazione** nella **casella degli strumenti** di Visual Studio, scegliendo la prima entità (denominata entità di origine) e scegliendo la seconda entità (denominata entità di destinazione). È possibile definire i dettagli dell'associazione nell'editor di **associazione**. Per altre informazioni, vedere [procedura: creare un'associazione tra entità](../sharepoint/how-to-create-an-association-between-entities.md).

## <a name="association-methods"></a>Metodi di associazione
 Applicazioni come le web part di dati aziendali di SharePoint utilizzano le associazioni chiamando i metodi nella classe del servizio di un'entità. È possibile aggiungere metodi alla classe di servizio di un'entità selezionandola nell' **editor di associazione**.

 Per impostazione predefinita, l' **editor di associazioni** aggiunge un metodo di navigazione di associazione alle entità di origine e di destinazione. Un metodo di navigazione di associazione nell'entità di origine consente ai consumer di recuperare un elenco di entità di destinazione. Un metodo di navigazione di associazione nell'entità di destinazione consente ai consumer di recuperare l'entità di origine che si riferisce a un'entità di destinazione.

 È necessario aggiungere il codice a ognuno di questi metodi per restituire le informazioni appropriate. È anche possibile aggiungere altri tipi di metodi per supportare scenari più avanzati. Per ulteriori informazioni su ognuno di questi metodi, vedere [operazioni supportate](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14)).

## <a name="types-of-associations"></a>Tipi di associazioni
 È possibile creare due tipi di associazioni nella finestra di progettazione dell'integrazione applicativa dei dati: associazioni basate su chiavi esterne e associazioni di chiavi esterne.

### <a name="foreign-key-based-association"></a>Associazione basata su chiavi esterne
 È possibile creare un'associazione basata su chiavi esterne correlando un identificatore nell'entità di origine ai descrittori di tipo definiti nell'entità di destinazione. Questa relazione consente ai consumer del modello di fornire un'interfaccia utente avanzata per gli utenti. Ad esempio, un modulo in Outlook che consente a un utente di creare un ordine di vendita in grado di visualizzare i clienti in un elenco a discesa; o un elenco di ordini di vendita in SharePoint che consente agli utenti di aprire una pagina del profilo per un cliente.

 Per creare un'associazione basata su chiave esterna, correlare gli identificatori e i descrittori di tipo che condividono lo stesso nome e tipo. Ad esempio, è possibile creare un'associazione basata su chiave esterna tra un' `Contact` entità e un' `SalesOrder` entità. L' `SalesOrder` entità restituisce un `ContactID` descrittore di tipo come parte del parametro restituito di Finder o di metodi di ricerca specifici. Entrambi i descrittori di tipo vengono visualizzati nell' **editor di associazione**. Per creare una relazione basata su chiave esterna tra `Contact` entità ed `SalesOrder` entità, scegliere l' `ContactID` identificatore accanto a ognuno di questi campi.

 Aggiungere codice al metodo dello strumento di spostamento dell'associazione dell'entità di origine che restituisce una raccolta di entità di destinazione. Nell'esempio seguente vengono restituiti gli ordini di vendita per un contatto.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet7":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet7":::

 Aggiungere il codice al metodo dello strumento di spostamento dell'associazione dell'entità di destinazione che restituisce un'entità di origine. Nell'esempio seguente viene restituito il contatto correlato all'ordine di vendita.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs" id="Snippet8":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb" id="Snippet8":::

### <a name="foreign-keyless-association"></a>Associazione di chiave esterna
 È possibile creare un'associazione senza eseguire il mapping degli identificatori ai descrittori di tipo di campo. Creare questo tipo di associazione quando l'entità di origine non dispone di una relazione diretta con l'entità di destinazione. Ad esempio, una `SalesOrderDetail` tabella non dispone di una chiave esterna che esegue il mapping a una chiave primaria in una `Contact` tabella.

 Se si desidera visualizzare le informazioni nella `SalesOrderDetail` tabella che è correlata a un `Contact` , è possibile creare un'associazione di chiave esterna non consentita tra `Contact` entità ed `SalesOrderDetail` entità.

 Nel metodo di navigazione di associazione dell' `Contact` entità, restituire le `SalesOrderDetail` entità mediante l'Unione di tabelle o chiamando un stored procedure.

 Nell'esempio seguente vengono restituiti i dettagli di tutti gli ordini di vendita mediante l'Unione di tabelle.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs" id="Snippet9":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb" id="Snippet9":::

 Nel metodo di navigazione dell'associazione dell' `SalesOrderDetail` entità, restituire l'oggetto correlato `Contact` . L'esempio seguente illustra questa operazione.
                                                                            
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs" id="Snippet10":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb" id="Snippet10":::

## <a name="see-also"></a>Vedi anche
- [Progettare un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Procedura: creare un'associazione tra entità](../sharepoint/how-to-create-an-association-between-entities.md)
