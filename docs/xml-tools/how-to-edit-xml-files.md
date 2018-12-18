---
title: 'Procedura: modificare i file XML | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 07fa3ecf-6345-4d30-9d85-d5ef5b083319
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b1b078a78d2752c909a9e14b35b7ce6b9e9d4969
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-edit-xml-files"></a>Procedura: modificare i file XML
L'editor XML è il nuovo editor per file XML. Può essere usato per un file XML autonomo o per un file associato a un progetto Visual Studio. L'editor XML è associato alle estensioni di file seguenti: .config, .dtd, .xml, .xsd, .xdr, .xsl, .xslt e .vssettings. L'editor XML è inoltre associato a qualsiasi altro tipo di file per il quale non è stato registrato un editor specifico e che presenta un contenuto XML o DTD.  
  
> [!NOTE]
>  I documenti XHTML sono gestiti dall'editor HTML.  
  
### <a name="to-edit-an-xml-file"></a>Per modificare un file XML  
  
1.  Fare doppio clic sul file che si desidera modificare.  
  
### <a name="to-add-a-new-xml-file-to-a-project"></a>Per aggiungere un nuovo file XML a un progetto  
  
1.  Dal **progetto** dal menu **Aggiungi nuovo elemento**.  
  
2.  Selezionare **File XML** dal **modelli** riquadro.  
  
3.  Immettere il nome del file nel **nome** campo e premere **Aggiungi**.  
  
     Il file XML viene aggiunto al progetto e aperto nell'editor XML. Il file contiene la dichiarazione XML predefinita, `<?xml version="1.0" encoding="utf-8" ?>`.  
  
### <a name="to-add-an-existing-xml-file-to-a-project"></a>Per aggiungere un file XML esistente a un progetto  
  
1.  Dal **progetto** dal menu **Aggiungi elemento esistente**.  
  
     Il **Aggiungi elemento esistente** viene visualizzata la finestra di dialogo.  
  
2.  Selezionare un file XML e premere **Aggiungi**.  
  
### <a name="to-create-a-new-xml-or-xslt-file"></a>Per creare un nuovo file XML o XSLT  
  
1.  Dal **File** dal menu **New**.  
  
     Il **nuovo File** viene visualizzata la finestra di dialogo.  
  
2.  Selezionare **File XML** per creare un nuovo file XML o, selezionare **File XSLT** per creare un nuovo foglio di stile XSLT.  
  
3.  Fare clic su **aprire**.  
  
### <a name="to-create-a-project-for-xml-files"></a>Per creare un progetto per i file XML  
  
1.  Dal **File** dal menu **New**, quindi selezionare **progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
2.  Selezionare il linguaggio del codice di propria scelta, seleziona **progetto vuoto**, fare clic su **OK**.  
  
3.  Aggiunta di file XML al progetto.  
  
     L'editor XML individua gli schemi aggiunti al progetto e li usa per la convalida e IntelliSense in qualsiasi file XML, schema o file XSLT che vengono modificati mentre il progetto è aperto.  
  
## <a name="see-also"></a>Vedere anche  
 [Editor XML](../xml-tools/xml-editor.md)   
 [Proprietà del documento XML, finestra proprietà](../xml-tools/xml-document-properties-properties-window.md)   
 [Procedura: Creare uno schema XML da un documento XML](../xml-tools/how-to-create-an-xml-schema-from-an-xml-document.md)