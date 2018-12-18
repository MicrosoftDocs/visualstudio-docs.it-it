---
title: Panoramica delle parti XML personalizzate | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom XML parts [Office development in Visual Studio], about
- Office Open XML Formats [Office development in Visual Studio]
- custom XML parts [Office development in Visual Studio]
- embedding XML data in documents [Office development in Visual Studio]
- XML parts [Office development in Visual Studio]
- XML file formats [Office development in Visual Studio]
- data [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- XML [Office development in Visual Studio], custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- documents [Office development in Visual Studio], custom XML parts
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8dc3e4b1abc5f60f9ca63e374ab8870df6bb0d41
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="custom-xml-parts-overview"></a>Custom XML Parts Overview
  È possibile incorporare i dati XML nei documenti per alcune applicazioni di Microsoft Office. Quando si incorporano dati XML in un documento, i dati vengono denominati un *parte XML personalizzata*.  
  
 È possibile creare e modificare le parti XML personalizzate in un documento usando un componente aggiuntivo VSTO o una soluzione a livello di documento in Visual Studio. Non è necessario avviare l'applicazione di Microsoft Office per creare e modificare le parti XML personalizzate.  
  
 **Si applica a:** le informazioni contenute in questo argomento si applicano ai progetti a livello di documento e il componente aggiuntivo VSTO per Excel, PowerPoint e Word. Per altre informazioni, vedere [Features Available by Office Application and Project Type](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Visual Studio consente anche di memorizzare nella cache gli oggetti dati nelle personalizzazioni a livello di documento. Questa funzionalità è diversa dalle parti XML personalizzate, sebbene siano presenti alcune somiglianze. Per ulteriori informazioni, vedere [dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md).  
  
## <a name="understanding-custom-xml-parts"></a>Informazioni sulle parti XML personalizzate  
 Le parti XML personalizzate sono state introdotte nel sistema Microsoft Office 2007, insieme ai formati Open XML. I formati includono i nuovi formati di file basati su XML per Excel, PowerPoint e Word (ad esempio con estensione xlsx, pptx e docx). I documenti in questi formati includono file XML (anche denominato *parti XML*) che sono organizzati in cartelle in un archivio ZIP. Per la maggior parte, si tratta di parti XML predefinite che consentono di definire la struttura e lo stato del documento. Tuttavia, i documenti possono contenere anche parti XML personalizzate, che è possibile usare per archiviare i dati XML arbitrari nei documenti.  
  
 I formati di file XML consentono alle applicazioni di usare nei documenti funzionalità non consentite con i vecchi formati di file binari (ad esempio, xls, ppt e doc). Tutte le applicazioni in grado di leggere gli archivi ZIP possono esaminare e modificare i contenuti dei documenti, anche se Microsoft Office non è installato.  
  
 Per altre informazioni sulla struttura di Open XML e delle parti XML personalizzate, vedere i seguenti articoli:  
  
-   [Introduzione ai formati file Office (2007) Open XML](http://msdn.microsoft.com/en-us/96018532-f62c-4da7-bbff-16b96a483fbf)  
  
-   [Procedura: modifica dei documenti nei formati Open XML](http://msdn.microsoft.com/en-us/c989d4e2-053d-4e1f-83be-257c608b343f)  
  
-   [Procedura dettagliata: Formato XML di Word 2007](http://msdn.microsoft.com/en-us/fc1afcb2-27fb-4608-9f29-11b7bd23ea4a)  
  
-   [Formati di compilazione di documenti di Word 2007 con Open XML](http://msdn.microsoft.com/en-us/59a46f4e-5a5a-4dac-86e5-7dfd43330766)  
  
> [!NOTE]  
>  Excel, Word e PowerPoint consentono anche di usare parti XML personalizzate nei documenti salvati in formati di file binari. Tuttavia, se un documento viene salvato in un formato binario, non è possibile aggiungere o modificare le parti XML personalizzate senza avviare l'applicazione di Microsoft Office.  
  
## <a name="creating-and-modifying-custom-xml-parts"></a>Creazione e modifica delle parti XML personalizzate  
 È possibile creare o modificare le parti XML personalizzate quando il documento è aperto nell'applicazione di Office oppure quando il documento è chiuso, anche se Microsoft Office non è installato.  
  
### <a name="modifying-xml-parts-while-the-office-application-is-running"></a>Modifica delle parti XML durante l'esecuzione dell'applicazione di Office  
 È possibile usare le parti XML personalizzate usando una personalizzazione a livello di documento o un componente aggiuntivo VSTO. Se si una personalizzazione a livello di documento, vengono usate in genere le parti XML personalizzate nel documento personalizzato. Se si usa un componente aggiuntivo VSTO, è possibile creare o modificare le parti XML personalizzate in qualsiasi documento aperto nell'applicazione.  
  
 Per creare una parte XML personalizzata usando Visual Studio, aggiungere un nuovo <xref:Microsoft.Office.Core.CustomXMLPart> alla raccolta <xref:Microsoft.Office.Core.CustomXMLParts> nel documento. Per altre informazioni, vedere i seguenti argomenti:  
  
-   [Procedura: Aggiungere Web part XML personalizzate a personalizzazioni a livello di documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
-   [Procedura: Aggiungere Web part XML personalizzate a documenti usando componenti aggiuntivi VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
### <a name="modifying-xml-parts-without-starting-the-office-application"></a>Modifica delle parti XML senza avviare l'applicazione di Office  
 È possibile aggiungere o modificare una parte XML personalizzata senza avviare Excel, PowerPoint o Word. Questa funzione è utile per usare i dati XML di un documento in un computer in cui sono installate le applicazioni di Microsoft Office, ad esempio un server.  
  
 Per aggiungere una parte XML personalizzata senza avviare Microsoft Office, usare le classi in Open XML SDK. Queste classi sono progettate per fornire l'accesso ai contenuti Open XML specifici dei documenti di Office. Ad esempio, per aggiungere una parte XML personalizzata a una cartella di lavoro di Excel, utilizzare il [AddNewPart\<T >](http://msdn.microsoft.com/en-us/47c348c0-77ab-a504-5097-bcd6a213921a) metodo di un [WorkbookPart](http://msdn.microsoft.com/en-us/d011e6f4-77dd-d02d-66ef-dc4a9e7b26f2) oggetto. Per ulteriori informazioni, vedere [Open XML SDK 2.0](http://msdn.microsoft.com/en-us/f6a9ae68-7989-4208-97f5-3c945137a0ab).  
  
## <a name="binding-custom-xml-parts-to-word-content-controls"></a>Associazione di parti XML personalizzate a controlli contenuto Word  
 È possibile associare i controlli contenuto in una soluzione Word agli elementi in una parte XML personalizzata. Quando un controllo contenuto è associato a una parte XML personalizzata, i dati nella parte XML personalizzata vengono visualizzati nell'interfaccia utente del controllo contenuto. Se un utente modifica testo nel controllo, l'elemento XML corrispondente viene automaticamente aggiornato. Analogamente, se si modificano i valori degli elementi nelle parti XML personalizzate, i controlli contenuto associati agli elementi XML visualizzeranno i nuovi dati. Per altre informazioni, vedere [Content Controls](../vsto/content-controls.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Schemi e dati nelle personalizzazioni a livello di documento XML](../vsto/xml-schemas-and-data-in-document-level-customizations.md)   
 [Procedura: aggiungere parti XML personalizzate a personalizzazioni a livello di documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)   
 [Procedura: aggiungere parti XML personalizzate a documenti usando componenti aggiuntivi VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)   
 [Controlli contenuto](../vsto/content-controls.md)   
 [Procedura dettagliata: associazione dei controlli del contenuto a Web part XML personalizzate](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)  
  
  