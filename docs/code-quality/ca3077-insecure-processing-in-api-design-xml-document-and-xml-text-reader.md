---
title: 'CA3077: Elaborazione non sicura in progettazione API, documenti XML e lettori di testo XML'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4974187a877cf27961d269141c78e18facb2c84d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077: Elaborazione non sicura in progettazione API, documenti XML e lettori di testo XML
|||
|-|-|
|TypeName|InsecureDTDProcessingInAPIDesign|
|CheckId|CA3077|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Quando si progetta un'API derivata da XMLDocument e XMLTextReader, tenere presente <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>.  Se si usano istanze di DTDProcessing non protette per fare riferimento o risolvere origini di entità esterne oppure per impostare valori non protetti nel codice XML, si può causare la divulgazione di informazioni.

## <a name="rule-description"></a>Descrizione della regola
 Oggetto *definizione DTD (Document Type)* è uno dei due modi un parser XML può determinare la validità di un documento, come definito dal [World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Questa regola cerca le proprietà e le istanze in cui vengono accettati i dati non attendibili per avvisare gli sviluppatori delle minacce potenziali di [Information Disclosure](/dotnet/framework/wcf/feature-details/information-disclosure) , che possono causare attacchi [Denial of Service (DoS)](/dotnet/framework/wcf/feature-details/denial-of-service) . Questa regola viene attivata quando:

-   <xref:System.Xml.XmlDocument> o <xref:System.Xml.XmlTextReader> classi usano valori resolver predefiniti per l'elaborazione della DTD.

-   Non è definito alcun costruttore per le classi derivate XmlDocument o XmlTextReader oppure non sono usati valori sicuri per <xref:System.Xml.XmlResolver>.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

-   Rilevare ed elaborare tutte le eccezioni XmlTextReader correttamente per evitare la divulgazione di informazioni di percorso.

-   Utilizzare <xref:System.Xml.XmlSecureResolver>posto di XmlResolver per limitare le risorse a cui può accedere XmlTextReader.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 A meno che non si abbia la certezza che l'input provenga da un'origine attendibile, non escludere una regola da questo avviso.

## <a name="pseudo-code-examples"></a>Esempi di pseudocodice

### <a name="violation"></a>Violazione

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass () {} // warn
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2() // warn
        {
        }
    }
}
```

### <a name="solution"></a>Soluzione

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass ()
        {
            XmlResolver = null;
        }
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2()
        {
               XmlResolver = null;
        }
    }
}
```