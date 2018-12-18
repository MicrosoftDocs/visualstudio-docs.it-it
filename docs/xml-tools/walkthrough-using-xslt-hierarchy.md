---
title: 'Procedura dettagliata: Utilizzo di gerarchia XSLT | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1e36ebaec08d09cbf006f4c20e743b5c2a909169
ms.sourcegitcommit: 5f436413bbb1e8aa18231eb5af210e7595401aa6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="walkthrough-using-xslt-hierarchy"></a>Procedura dettagliata: utilizzo della gerarchia XSLT

Lo strumento di gerarchia XSLT semplifica molte attività di sviluppo XML. Un foglio di stile XSLT spesso usa istruzioni `includes` e `imports`. La compilazione viene avviata dal foglio di stile principale, ma quando viene visualizzato un errore come risultato della compilazione di un foglio di stile XSLT, è possibile che l'errore provenga da un'origine diversa dal foglio di stile principale. È possibile che la correzione dell'errore o la modifica del foglio di stile richieda accesso ai fogli di stile inclusi o importati. Scorrendo il foglio di stile nel debugger è possibile che vengano visualizzati i fogli di stile inclusi e importati ed è necessario aggiungere un punto di interruzione in una determinata posizione di uno o più fogli di stile inclusi.

Un altro scenario in cui può essere utile lo strumento di gerarchia XSLT è l'inserimento di punti di interruzione sulle regole del modello incorporato. Le regole del modello sono modelli speciali generati per ogni modalità del foglio di stile e sono chiamate da `xsl:apply-templates` quando nessun altro modello corrisponde al nodo. Per implementare il debug nelle regole dei modelli incorporati, il debugger XSLT genera il file con le regole nella cartella temporanea e le compila insieme al foglio di stile principale. Senza eseguire istruzioni di codice da alcuni `xsl:apply-template`, può essere difficile individuare i fogli di stile inclusi nel foglio di stile principale o trovare e aprire il foglio di stile con le regole del modello incorporate.

Nell'esempio riportato in questo argomento viene dimostrata l'esecuzione del debug in un foglio di stile a cui si fa riferimento.

## <a name="to-debug-in-a-referenced-style-sheet"></a>Per eseguire il debug in un foglio di stile di riferimento

1. Aprire un documento XML in Visual Studio. Nel presente esempio viene usato il seguente documento `collection.xml`.  
  
    ```xml
    <?xml version="1.0" encoding="utf-8"?>  
    <?xml-stylesheet type="text/xsl" href="xslinclude.xsl"?>  
    <COLLECTION>  
      <BOOK>  
        <TITLE>Lover Birds</TITLE>  
        <AUTHOR>Cynthia Randall</AUTHOR>  
        <PUBLISHER>Lucerne Publishing</PUBLISHER>  
      </BOOK>  
      <BOOK>  
        <TITLE>The Sundered Grail</TITLE>  
        <AUTHOR>Eva Corets</AUTHOR>  
        <PUBLISHER>Lucerne Publishing</PUBLISHER>  
      </BOOK>  
      <BOOK>  
        <TITLE>Splish Splash</TITLE>  
        <AUTHOR>Paula Thurman</AUTHOR>  
        <PUBLISHER>Scootney</PUBLISHER>  
      </BOOK>  
    </COLLECTION>  
    ```

1. Aggiungere il seguente `xslincludefile.xsl`:

    ```xml
    <?xml version='1.0'?>  
    <xsl:stylesheet version="1.0"  
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
          xml:space="preserve">  
  
    <xsl:template match="TITLE">  
       Title - <xsl:value-of select="."/><BR/>  
    </xsl:template>  
  
    <xsl:template match="AUTHOR">  
       Author - <xsl:value-of select="."/><BR/>  
    </xsl:template>  
  
    <xsl:template match="PUBLISHER">  
       Publisher - <xsl:value-of select="."/><BR/><!-- removed second <BR/> -->  
    </xsl:template>  
  
    </xsl:stylesheet>  
    ```
  
3.  Aggiungere il seguente file `xslinclude.xsl`:  
  
    ```xml
    <?xml version='1.0'?>  
    <xsl:stylesheet version="1.0"  
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform">  
  
      <xsl:output method="xml" omit-xml-declaration="yes"/>  
  
      <xsl:template match="/">  
        <xsl:for-each select="COLLECTION/BOOK">  
          <xsl:apply-templates select="TITLE"/>  
          <xsl:apply-templates select="AUTHOR"/>  
          <xsl:apply-templates select="PUBLISHER"/>  
          <BR/>  
          <!-- add this -->  
        </xsl:for-each>  
      </xsl:template>  
  
      <!-- The following template rule will not be called,  
      because the related template in the including stylesheet  
      is called. If we move this template so that  
      it follows the xsl:include instruction, this one  
      will be called instead.-->  
      <xsl:template match="TITLE">  
        <DIV STYLE="color:blue">  
          Title: <xsl:value-of select="."/>  
        </DIV>  
      </xsl:template>  
  
      <xsl:include href="xslincludefile.xsl" />  
    </xsl:stylesheet>  
    ```
  
4.  Aggiungere un punto di interruzione in corrispondenza dell'istruzione `<xsl:include href="xslincludefile.xsl" />`.
  
5.  Avviare il debug.  
  
6.  Quando il debugger si arresta in corrispondenza dell'istruzione `<xsl:include href="xslincludefile.xsl" />`, premere il **Esegui istruzione** pulsante. Notare che l'esecuzione del debug può proseguire nel foglio di stile a cui si fa riferimento. La gerarchia è visibile e nella finestra di progettazione viene visualizzato il percorso corretto.  
  
## <a name="see-also"></a>Vedere anche

[Procedura dettagliata: Profiler XSLT](../xml-tools/walkthrough-xslt-profiler.md)