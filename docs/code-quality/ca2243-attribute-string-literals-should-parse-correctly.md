---
title: 'CA2243: Valori letterali di stringa di attributo devono essere analizzate correttamente | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2243
- AttributeStringLiteralsShouldParseCorrectly
helpviewer_keywords:
- AttributeStringLiteralsShouldParseCorrectly
- CA2243
ms.assetid: bfadb366-379d-4ee4-b17b-c4a09bf1106b
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 79ffda960d85c05648a0f1ea7d6c759fc9e76f78
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2243-attribute-string-literals-should-parse-correctly"></a>CA2243: Valori letterali stringa di attributo devono essere analizzate correttamente
|||  
|-|-|  
|TypeName|AttributeStringLiteralsShouldParseCorrectly|  
|CheckId|CA2243|  
|Category|Microsoft. Usage|  
|Modifica importante|Non importante|  
  
## <a name="cause"></a>Causa  
 Parametro del valore letterale stringa dell'attributo non analizza correttamente un URL, un GUID o una versione.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Poiché gli attributi sono derivati da <xref:System.Attribute?displayProperty=fullName>e gli attributi vengono utilizzati in fase di compilazione, solo i valori costanti possono essere passati ai relativi costruttori. I parametri dell'attributo che devono rappresentare gli URL, GUID e versioni non possono essere tipizzati come <xref:System.Uri?displayProperty=fullName>, <xref:System.Guid?displayProperty=fullName>, e <xref:System.Version?displayProperty=fullName>, perché questi tipi non possono essere rappresentati come costanti. Al contrario, devono essere rappresentati da stringhe.  
  
 Poiché il parametro è tipizzato come una stringa, è possibile che è stato passato un parametro di formato non corretto in fase di compilazione.  
  
 Questa regola utilizza un approccio euristico di denominazione per trovare i parametri che rappresentano un uniform resource identifier (URI), un identificatore univoco globale (GUID, Globally Unique Identifier) o una versione e verifica che il valore passato sia corretto.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Modificare la stringa di parametri per un URL in formato corretto, GUID o versione.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare un avviso da questa regola se il parametro non rappresenta un URL, un GUID o una versione.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra codice per AssemblyFileVersionAttribute che viola questa regola.  
  
 [!code-csharp[FxCop.Usage.AttributeStringLiteralsShouldParseCorrectly#1](../code-quality/codesnippet/CSharp/ca2243-attribute-string-literals-should-parse-correctly_1.cs)]  
  
 La regola viene attivata dagli elementi seguenti:  
  
-   Parametri che contengono 'version' e non possono essere analizzati in System. Version.  
  
-   Parametri che contengono "guid" e non possono essere analizzati in System. GUID.  
  
-   Parametri che contengono 'uri', 'urn' o 'url' e non possono essere analizzati in System. Uri.  
  
## <a name="see-also"></a>Vedere anche  
 [CA1054: I parametri URI non devono essere stringhe](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)