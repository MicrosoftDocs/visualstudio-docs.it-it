---
title: 'Procedura dettagliata: Utilizzo di XSLT IntelliSense | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 079d95ac-2eaf-4ae1-9cd3-2c81a961a942
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7a26ca0228a869d36daf427f4ba90fd1b17abeaf
ms.sourcegitcommit: 5f436413bbb1e8aa18231eb5af210e7595401aa6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="walkthrough-using-xslt-intellisense"></a>Procedura dettagliata: utilizzo di XSLT IntelliSense
Questa procedura dettagliata dimostra come usare XSLT IntelliSense per completare automaticamente il valore di alcuni attributi.  
  
### <a name="to-use-intellisense-in-the-name-attribute-of-xslwith-param-and-xslcall-template-elements"></a>Per usare IntelliSense nell'attributo del nome degli elementi xsl:with-param e xsl:call-template  
  
1.  Creare un nuovo file XSLT e copiarvi il seguente codice:  
  
    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
    <!-- These 2 elements effectively assign  
         $messages = resources/en.xml/<messages>,  
         then $messages is used in the "localized-message" template.  -->  
    <xsl:param name="lang">en</xsl:param>  
    <xsl:variable name="messages"  
          select="document(concat('resources/', $lang, '.xml'))/messages"/>   
  
    <xsl:template name="msg23" match="msg23">  
    </xsl:template>  
  
    <xsl:template name="localized-message">  
      <xsl:param name="msgcode"/>  
      <!-- Show message string. -->  
      <xsl:message terminate="yes">  
        <xsl:value-of select="$messages/message[@name=$msgcode]"/>  
      </xsl:message>  
    </xsl:template>  
    </xsl:stylesheet>  
    ```
  
2.  Posizionare il cursore dopo `<xsl:template name="msg23" match="msg23">` e premere INVIO. Quindi iniziare a digitare il seguente elemento `xsl:call-template`:  
  
    ```xml
    <xsl:call-template name="localized-message">  
    </xsl:call-template>  
    ```
  
     L'elenco dei nomi di modello viene visualizzato nell'attributo `name=""` dell'elemento `xsl:call-template` durante la digitazione.  
  
3.  Posizionare il cursore dopo `<xsl:call-template name="localized-message">` e premere INVIO. Quindi iniziare a digitare il seguente elemento `xsl:with-param`:  
  
    ```xml
    <xsl:with-param name="msgcode">msg23</xsl:with-param>  
    ```
  
     L'elenco dei nomi di parametro viene visualizzato nell'attributo `name=""` dell'elemento `xsl:with-param`.  
  
### <a name="to-use-intellisense-in-the-mode-attribute-of-an-xslapply-templates-element"></a>Per usare IntelliSense nell'attributo mode di un elemento xsl:apply-templates  
  
1.  Creare un nuovo file XSLT e copiarvi il seguente codice:  
  
    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
      <xsl:template match="/">  
        <HTML>  
          <BODY>  
            <TABLE>  
              <xsl:apply-templates select="customers/customer">  
                <xsl:sort select="state"/>  
                <xsl:sort select="name"/>  
              </xsl:apply-templates>  
            </TABLE>  
          </BODY>  
        </HTML>  
      </xsl:template>  
      <xsl:template match="customer">  
        <TR>  
          <xsl:apply-templates select="name" />  
          <xsl:apply-templates select="address" />  
          <xsl:apply-templates select="phone" />  
        </TR>  
      </xsl:template>  
      <xsl:template match="name">  
        <TD STYLE="font-size:14pt font-family:serif">  
          <xsl:apply-templates />  
        </TD>  
      </xsl:template>  
      <xsl:template match="address">  
        <TD>  
          <xsl:apply-templates />  
        </TD>  
      </xsl:template>  
      <xsl:template match="phone">  
        <TD>  
          <xsl:apply-templates />  
        </TD>  
      </xsl:template>  
      <xsl:template match="phone" mode="accountNumber">  
        <xsl:param name="Area_Code"/>  
        <TD STYLE="font-style:italic">  
          1-<xsl:value-of select="."/>-001  
        </TD>  
      </xsl:template>  
    </xsl:stylesheet>  
    ```
  
2.  Posizionare il cursore dopo `<xsl:apply-templates select="phone" />` e premere INVIO. Quindi iniziare a digitare il seguente elemento `xsl: apply-templates`:  
  
    ```xml
    <xsl:apply-templates select="phone"  mode="accountNumber">  
    ```
  
     L'elenco delle modalità modello viene visualizzato nell'attributo `mode=""` dell'elemento `xsl:apply-templates`.  
  
### <a name="to-use-intellisense-in-the-stylesheet-prefix-and-result-prefix-attributes-of-an-xslnamespace-alias-element"></a>Per usare IntelliSense negli attributi stylesheet-prefix e result-prefix di un elemento xsl:namespace-alias  
  
1.  Creare un nuovo file XSLT e copiarvi il seguente codice:  
  
    ```xml
    <xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate"  
    version="1.0">  
      <xsl:param name="browser" select="'InternetExplorer'"/>  
      <xsl:template match="/">  
        <alt:stylesheet>  
          <xsl:choose>  
            <xsl:when test="$browser='InternetExplorer'">  
              <alt:import href="IERoutines.xsl"/>  
              <alt:template match="/">  
                <div>  
                  <alt:call-template name="showTable"/>  
                </div>  
              </alt:template>  
            </xsl:when>  
            <xsl:otherwise>  
              <alt:import href="OtherBrowserRoutines.xsl"/>  
              <alt:template match="/">  
                <div>  
                  <alt:call-template name="showTable"/>  
                </div>  
              </alt:template>  
            </xsl:otherwise>  
          </xsl:choose>  
        </alt:stylesheet>  
      </xsl:template>  
    </xsl:stylesheet>  
    ```
  
2.  Posizionare il cursore dopo `<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" xmlns:alt="http://www.w3.org/1999/XSL/Transform-alternate" version="1.0">` e premere INVIO. Quindi iniziare a digitare il seguente elemento `xsl:namespace-alias`:  
  
    ```xml
    <xsl:namespace-alias stylesheet-prefix="alt" result-prefix="xsl"/>  
    ```
  
     Notare come l'elenco dei prefissi viene visualizzato negli attributi `stylesheet-prefix` e `result-prefix` dell'elemento `xsl:namespace-alias`.  
  
## <a name="see-also"></a>Vedere anche

[Funzionalità IntelliSense dell'editor XML](../xml-tools/xml-editor-intellisense-features.md)