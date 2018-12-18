---
title: Considerazioni sulla sicurezza quando si lavora con dati XML | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: fce2b708-1aef-454f-be59-52b76f359351
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 80cb0d35e5850361d21df35dfd3f226fc03df9d7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="security-considerations-when-working-with-xml-data"></a>Considerazioni sulla sicurezza durante l'utilizzo di dati XML
In questo argomento vengono illustrati i problemi di sicurezza che è necessario prendere in considerazione quando si usa l'editor XML o il debugger XSLT.  
  
## <a name="xml-editor"></a>Editor XML  
 L'editor XML è basato sull'editor di testo di Visual Studio e si basa sulle classi <xref:System.Xml> e <xref:System.Xml.Xsl> per gestire gran parte dei processi XML.  
  
-   Le trasformazioni XSLT vengono eseguite in un nuovo dominio applicazione. Le trasformazioni XSLT sono *creata mediante sandbox*; ovvero, i criteri di sicurezza di accesso di codice del computer viene utilizzato per determinare le autorizzazioni limitate in base alla quale si trova il foglio di stile XSLT. Ad esempio, per i fogli di stile provenienti da un'area Internet vengono applicate autorizzazioni con la limitazione massima, mentre per i fogli di stile copiati sull'unità disco rigido del computer vengono eseguiti con un livello di Attendibilità totale.  
  
-   La classe <xref:System.Xml.Xsl.XslCompiledTransform> viene usata per compilare il codice XSLT in Microsoft Intermediate Language per ottenere prestazioni più veloci durante l'esecuzione.  
  
-   Gli schemi che fanno riferimento a un percorso esterno nel file del catalogo vengono scaricati automaticamente quando l'editor XML viene caricato. La classe <xref:System.Xml.Schema.XmlSchemaSet> è usata per compilare gli schemi. Il file del catalogo fornito con l'editor XML non dispone di collegamenti a schemi esterni. L'utente deve aggiungere in modo esplicito un riferimento allo schema esterno prima che l'editor XML scarichi il file di schema. Il download HTTP può essere disabilitato tramite il **Miscellaneous Tools Options** pagina per l'Editor XML.  
  
-   L'editor XML usa le classi <xref:System.Net> per scaricare gli schemi  
  
## <a name="xslt-debugger"></a>Debugger XSLT  
 Il debugger XSLT usa il motore di debug gestito di Visual Studio e le classi degli spazi dei nomi <xref:System.Xml> e <xref:System.Xml.Xsl>.  
  
-   Il debugger XSLT esegue ogni trasformazione XSLT in un dominio applicazione sandboxed. I criteri di sicurezza dall'accesso di codice del computer vengono usati per determinare le autorizzazioni limitate basate sulla posizione del foglio di stile XSLT. Ad esempio, per i fogli di stile provenienti da un'area Internet vengono applicate autorizzazioni con la limitazione massima, mentre per i fogli di stile copiati sull'unità disco rigido del computer vengono eseguiti con un livello di Attendibilità totale.  
  
-   Il foglio di stile XSLT viene compilato usando la classe <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
-   L'analizzatore di espressioni XSLT viene caricato dal motore di debug gestito. Il motore di debug gestito presuppone che tutto il codice venga eseguito dal computer locale dell'utente. Di conseguenza, la classe <xref:System.Xml.Xsl.XslCompiledTransform> scarica il file XSLT nel computer locale dell'utente. La possibilità che possa verificarsi un'elevazione dei privilegi di esecuzione è attenuata dall'esecuzione di tutte le trasformazioni XSLT in un nuovo dominio applicazione con autorizzazioni limitate.  
  
## <a name="see-also"></a>Vedere anche  
 [Domini dell'applicazione](/dotnet/framework/app-domains/application-domains)  