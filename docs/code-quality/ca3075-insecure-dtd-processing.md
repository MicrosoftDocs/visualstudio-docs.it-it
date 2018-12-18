---
title: 'CA3075: Elaborazione di DTD non protetta | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65798d66-7a30-4359-b064-61a8660c1eed
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 34f3d518e282650f9369aa3af8fe1600b4f28662
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca3075-insecure-dtd-processing"></a>CA3075: Elaborazione DTD non protetta
|||  
|-|-|  
|TypeName|InsecureDTDProcessing|  
|CheckId|CA3075|  
|Category|Microsoft.Security|  
|Modifica importante|Non importante|  
  
## <a name="cause"></a>Causa  
 Se si usano istanze di <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> non protette o si fa riferimento a origini di entità esterne, il parser può accettare un input non attendibile e divulgare informazioni riservate a utenti malintenzionati.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Oggetto *definizione DTD (Document Type)* è uno dei due modi un parser XML può determinare la validità di un documento, come definito dal [World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Questa regola cerca le proprietà e le istanze in cui vengono accettati i dati non attendibili per avvisare gli sviluppatori delle minacce potenziali di [Information Disclosure](/dotnet/framework/wcf/feature-details/information-disclosure) , che possono causare attacchi [Denial of Service (DoS)](/dotnet/framework/wcf/feature-details/denial-of-service) . Questa regola viene attivata quando:  
  
-   DtdProcessing viene abilitato nell'istanza di <xref:System.Xml.XmlReader> , che risolve le entità XML esterne con <xref:System.Xml.XmlUrlResolver>.  
  
-   La proprietà <xref:System.Xml.XmlNode.InnerXml%2A> nel codice XML è impostata.  
  
-   <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>proprietà è impostata su Parse.  
  
-   Un input non attendibile viene elaborato con <xref:System.Xml.XmlResolver> anziché con <xref:System.Xml.XmlSecureResolver> .  
  
-   Il metodo XmlReader.<xref:System.Xml.XmlReader.Create%2A> viene richiamato con un'istanza non protetta di <xref:System.Xml.XmlReaderSettings> o senza alcuna istanza.  
  
-   <xref:System.Xml.XmlReader>viene creato con le impostazioni predefinite non protette o valori.  
  
 In ognuno di questi casi, il risultato è lo stesso: il contenuto del file system o delle condivisioni di rete nel computer in cui viene elaborato il codice XML sarà esposto alle minacce di utenti malintenzionati e potrà quindi essere usato come vettore di attacchi DoS.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
  
-   Rilevare ed elaborare tutte le eccezioni XmlTextReader correttamente per evitare la divulgazione di informazioni di percorso.  
  
-   Usare l'oggetto <xref:System.Xml.XmlSecureResolver> per limitare le risorse a cui può accedere XmlTextReader.  
  
-   Non consentire all'oggetto <xref:System.Xml.XmlReader> di aprire risorse esterne impostando la proprietà <xref:System.Xml.XmlResolver> su **Null**.  
  
-   Assicurarsi che la proprietà <xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A> di <xref:System.Data.DataViewManager> venga assegnata da un'origine attendibile.  
  
 .NET 3.5 e versioni precedenti  
  
-   Disabilitare l'elaborazione DTD se si usano origini non attendibili impostando la  proprietà <xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A> su **true** .  
  
-   La classe XmlTextReader ha una richiesta di ereditarietà con attendibilità totale.  
  
 .NET 4 e versioni successive  
  
-   Evitare di abilitare DtdProcessing se si gestiscono origini non attendibili impostando la <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A?displayProperty=nameWithType> proprietà **Impedisci** o **ignora**.  
  
-   Assicurarsi che il metodo Load() accetti un'istanza di XmlReader ovunque venga usato InnerXml.  
  
> [!NOTE]
>  Questa regola potrebbe segnalare dei falsi positivi in alcune istanze valide di XmlSecureResolver. Questo problema dovrebbe essere risolto per la metà del 2016.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 A meno che non si abbia la certezza che l'input provenga da un'origine attendibile, non escludere una regola da questo avviso.  
  
## <a name="pseudo-code-examples"></a>Esempi di pseudocodice  
  
### <a name="violation"></a>Violazione  
  
```csharp  
using System.IO;   
using System.Xml.Schema;   
  
class TestClass   
{   
    public XmlSchema Test   
    {   
        get   
        {   
            var src = "";   
            TextReader tr = new StreamReader(src);   
            XmlSchema schema = XmlSchema.Read(tr, null); // warn   
            return schema;   
        }   
    }   
}  
```  
  
### <a name="solution"></a>Soluzione  
  
```csharp  
using System.IO;   
using System.Xml;   
using System.Xml.Schema;   
  
class TestClass   
{   
    public XmlSchema Test   
    {   
        get   
        {   
            var src = "";   
            TextReader tr = new StreamReader(src);   
            XmlTextReader reader = new XmlTextReader(tr) { DtdProcessing = DtdProcessing.Prohibit };   
            XmlSchema schema = XmlSchema.Read(reader , null);   
            return schema;   
        }   
    }   
}  
```  
  
### <a name="violation"></a>Violazione  
  
```csharp  
using System.Xml;   
  
namespace TestNamespace   
{   
    public class TestClass   
    {   
        public XmlReaderSettings settings = new XmlReaderSettings();   
        public void TestMethod(string path)   
        {   
            var reader = XmlReader.Create(path, settings);  // warn   
        }   
    }   
}  
```  
  
### <a name="solution"></a>Soluzione  
  
```csharp  
using System.Xml;   
  
namespace TestNamespace   
{   
    public class TestClass   
    {   
        public XmlReaderSettings settings = new XmlReaderSettings()    
        {   
            DtdProcessing = DtdProcessing.Prohibit    
        };   
  
        public void TestMethod(string path)   
        {   
            var reader = XmlReader.Create(path, settings);    
        }   
    }   
}  
```  
  
### <a name="violations"></a>Violazioni  
  
```csharp  
using System.Xml;   
  
namespace TestNamespace   
{   
    public class DoNotUseSetInnerXml   
    {   
        public void TestMethod(string xml)   
        {   
            XmlDocument doc = new XmlDocument() { XmlResolver = null };   
            doc.InnerXml = xml; // warn   
        }   
    }   
}  
```  
  
```csharp  
using System.Xml;   
  
namespace TestNamespace   
{   
    public class DoNotUseLoadXml   
    {  
        public void TestMethod(string xml)   
        {   
            XmlDocument doc = new XmlDocument(){ XmlResolver = null };   
            doc.LoadXml(xml); // warn   
        }   
    }   
}  
```  
  
### <a name="solution"></a>Soluzione  
  
```csharp  
using System.Xml;   
  
public static void TestMethod(string xml)   
{   
    XmlDocument doc = new XmlDocument() { XmlResolver = null };   
    System.IO.StringReader sreader = new System.IO.StringReader(xml);   
    XmlTextReader reader = new XmlTextReader(sreader) { DtdProcessing = DtdProcessing.Prohibit };   
    doc.Load(reader);   
}  
```  
  
### <a name="violation"></a>Violazione  
  
```csharp  
using System.IO;   
using System.Xml;   
using System.Xml.Serialization;   
  
namespace TestNamespace   
{   
    public class UseXmlReaderForDeserialize   
    {   
        public void TestMethod(Stream stream)   
        {   
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));   
            serializer.Deserialize(stream); // warn   
        }   
    }   
}  
```  
  
### <a name="solution"></a>Soluzione  
  
```csharp  
using System.IO;   
using System.Xml;   
using System.Xml.Serialization;   
  
namespace TestNamespace   
{   
    public class UseXmlReaderForDeserialize   
    {   
        public void TestMethod(Stream stream)   
        {   
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));   
            XmlTextReader reader = new XmlTextReader(stream) { DtdProcessing = DtdProcessing.Prohibit } ;   
            serializer.Deserialize(reader );   
        }   
    }   
}  
```  
  
### <a name="violation"></a>Violazione  
  
```csharp  
using System.Xml;   
using System.Xml.XPath;   
  
namespace TestNamespace   
{   
    public class UseXmlReaderForXPathDocument   
    {   
        public void TestMethod(string path)   
        {   
            XPathDocument doc = new XPathDocument(path); // warn   
        }   
    }   
}  
```  
  
### <a name="solution"></a>Soluzione  
  
```csharp  
using System.Xml;   
using System.Xml.XPath;   
  
namespace TestNamespace   
{   
    public class UseXmlReaderForXPathDocument   
    {   
        public void TestMethod(string path)   
        {   
            XmlTextReader reader = new XmlTextReader(path) { DtdProcessing = DtdProcessing.Prohibit };   
            XPathDocument doc = new XPathDocument(reader);   
        }   
    }   
}  
```  
  
### <a name="violation"></a>Violazione  
  
```csharp  
using System.Xml;   
  
namespace TestNamespace   
{   
    class TestClass   
    {   
        public XmlDocument doc = new XmlDocument() { XmlResolver = new XmlUrlResolver() };   
    }   
}  
```  
  
### <a name="solution"></a>Soluzione  
  
```csharp  
using System.Xml;   
  
namespace TestNamespace   
{   
    class TestClass   
    {   
        public XmlDocument doc = new XmlDocument() { XmlResolver = null }; // or set to a XmlSecureResolver instance   
    }   
}  
```  
  
### <a name="violations"></a>Violazioni  
  
```csharp  
using System.Xml;   
  
namespace TestNamespace   
{   
    public class TestClass   
    {   
        public void TestMethod(string path)   
        {   
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Parse };   
            XmlReader reader = XmlReader.Create(path, settings); // warn   
        }   
    }   
}  
```  
  
```csharp  
using System.Xml;   
  
namespace TestNamespace   
{   
    class TestClass   
    {   
        private static void TestMethod()   
        {   
            var reader = XmlTextReader.Create(""doc.xml""); //warn   
        }   
    }   
}  
```  
  
```csharp  
using System.Xml;   
  
namespace TestNamespace   
{   
    public class TestClass   
    {   
        public void TestMethod(string path)   
        {   
            try {   
                XmlTextReader reader = new XmlTextReader(path); // warn   
            }   
            catch { throw ; }   
            finally {}   
        }   
    }   
}  
```  
  
### <a name="solution"></a>Soluzione  
  
```csharp  
using System.Xml;   
  
namespace TestNamespace   
{   
    public class TestClass   
    {   
        public void TestMethod(string path)   
        {   
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Prohibit };   
            XmlReader reader = XmlReader.Create(path, settings);   
        }   
    }   
}  
```