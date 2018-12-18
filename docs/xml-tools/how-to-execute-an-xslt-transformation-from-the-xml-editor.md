---
title: "Procedura: eseguire una trasformazione XSLT dall'Editor XML | Documenti Microsoft"
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: 56a0fe82-5231-487d-8b6e-a08a9b04e0fc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2ce56195d0bc9750af3b869cb3e8bb0a780fdcde
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-execute-an-xslt-transformation-from-the-xml-editor"></a>Procedura: eseguire una trasformazione XSLT dall'editor XML
L'editor XML consente di associare un foglio di stile XSLT a un documento XML, eseguire la trasformazione e visualizzare l'output. L'output risultante dalla trasformazione XSLT viene visualizzato in una nuova finestra del documento.  
  
 Il **Output** proprietà specifica il nome del file per l'output. Se il **Output** proprietà è vuota, viene generato un nome di file nella directory temporanea. L'estensione del file è basata sull'elemento `xsl:output` del foglio di stile e può essere .xml, .txt o .htm.  
  
 Se il **Output** proprietà specifica un nome di file con un file. htm o HTML estensione, l'output XSLT viene visualizzato in anteprima utilizzando [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Internet Explorer. Tutte le altre estensioni di file vengono aperte usando l'editor predefinito scelto da [!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)] Visual Studio. Ad esempio, se l'estensione del file è .xml, Visual Studio utilizzerà l'editor XML.  
  
### <a name="to-execute-an-xslt-transformation-from-an-xml-document"></a>Per eseguire una trasformazione XSLT da un documento XML  
  
1.  Aprire un documento XML nell'editor XML.  
  
2.  Associare un foglio di stile XSLT al documento XML.  
  
    -   Aggiungere un'istruzione di elaborazione `xml-stylesheet` al documento XML. Ad esempio, aggiungere la seguente riga `<?xml-stylesheet type='text/xsl' href='filename.xsl'?>` al prologo del documento.  
  
         oppure  
  
    -   Aggiungere il foglio di stile XSLT utilizzando il **proprietà** finestra. Nel documento **finestra proprietà**, fare clic su di **Sfoglia** pulsante per la **Stylesheet** campo, selezionare il foglio di stile XSLT e fare clic su **aprire**.  
  
3.  Fare clic su di **ShowXSL Output** pulsante il **Editor XML** barra degli strumenti.  
  
    > [!NOTE]
    >  Se al documento XML non è associato alcun foglio di stile, viene visualizzata una finestra di dialogo con la richiesta di specificare il foglio di stile da usare.  
    >   
    >  L'output risultante dalla trasformazione XSLT viene visualizzato in una nuova finestra del documento.  
  
### <a name="to-execute-an-xslt-transformation-from-an-xslt-style-sheet"></a>Per eseguire una trasformazione XSLT da un foglio di stile XSLT  
  
1.  Aprire il foglio di stile XSLT nell'editor XML.  
  
2.  Specificare un documento XML nel **Input** campo del documento **proprietà** finestra.  
  
    > [!NOTE]
    >  Il documento XML è il documento di input usato per la trasformazione. Se non è specificato alcun documento quando la trasformazione XSLT viene avviata, il **Apri File** viene visualizzata la finestra di dialogo e specificare un documento in quel momento.  
  
3.  Fare clic su di **ShowXSLT Output** pulsante il **Editor XML** barra degli strumenti.  
  
     L'output risultante dalla trasformazione XSLT viene visualizzato in una nuova finestra del documento.  
  
### <a name="to-provide-a-different-output-file-name"></a>Per fornire un nome di file di output diverso  
  
1.  Specificare un nome di file nel **Output** campo del documento **proprietà** finestra.  
  
2.  Fare clic su di **ShowXSLT Output** pulsante il **Editor XML** barra degli strumenti.  
  
     L'output risultante dalla trasformazione XSLT viene visualizzato in una nuova finestra del documento e l'editor usato nella finestra di output dipende dall'estensione del file del **Output** proprietà di documento.  
  
## <a name="see-also"></a>Vedere anche  
 [Editor XML](../xml-tools/xml-editor.md)