---
title: La struttura del File [Content_types] XML | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 38e65f484411abcfb2acd78b124b77ff3f2c49cd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="the-structure-of-the-contenttypesxml-file"></a>La struttura del File [Content_types] XML
Contiene informazioni sui tipi di contenuto in un pacchetto VSIX. Per installare il pacchetto di Visual Studio viene utilizzato il file [Content_Types] XML, ma non installa il file stesso.  
  
> [!NOTE]
>  Anche se questo argomento si applica solo ai file con estensione XML [Content_Types] utilizzati nei pacchetti VSIX, il tipo di file [Content_Types] XML fa parte di *Open Packaging Conventions (OPC)* standard. Per ulteriori informazioni, vedere [OPC: un nuovo Standard per la creazione di pacchetti di dati](http://go.microsoft.com/fwlink/?LinkID=148207) nel sito Web MSDN.  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Le sezioni seguenti descrivono l'elemento radice e i relativi attributi ed elementi figlio.  
  
### <a name="root-element"></a>Elemento radice  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|`Types`|Contiene gli elementi figlio che enumera i tipi di file nel pacchetto VSIX.|  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Xmlns`|Obbligatorio. Il percorso dello schema utilizzato per il file [Content_Types] XML.|  
  
### <a name="attribute-name-attribute"></a>Attributo {nome} Attributo  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|http://schemas.openformats.org/package/2006/content-types|Il percorso dello schema di tipi di contenuto.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Il `Types` elemento può contenere un numero qualsiasi di `Default` elementi.  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|`Default`|Descrive un tipo di contenuto nel pacchetto VSIX. Ogni tipo di file del pacchetto deve avere un proprio `Default` elemento.|  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Extension`|L'estensione di un file di pacchetto VSIX.|  
|`ContentType`|Descrive il tipo di contenuto che è associato con l'estensione del nome file.|  
  
### <a name="attribute-name-attribute"></a>Attributo {nome} Attributo  
 Visual Studio vengono riconosciuti i seguenti `ContentType` valori per la proprietà associata `Extension` tipi.  
  
|Estensione|ContentType|  
|---------------|-----------------|  
|txt|Testo|  
|pkgdef|Testo|  
|xml|text/xml|  
|vsixmanifest|text/xml|  
|htm o html|testo/html|  
|formato RTF|applicazione/rtf|  
|PDF|Application/pdf|  
|GIF|image/gif|  
|jpg o jpeg|immagine/jpg|  
|TIFF|immagine/tiff|  
|vsix|Application/zip.|  
|Codice postale|Application/zip.|  
|dll|application/octet-stream|  
|tutti gli altri tipi di file|application/octet-stream|  
  
## <a name="example"></a>Esempio  
  
### <a name="description"></a>Descrizione  
 Il file [Content_Types] XML seguente viene descritto un pacchetto VSIX tipico.  
  
### <a name="code"></a>Codice  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">  
    <Default Extension="vsixmanifest" ContentType="text/xml" />   
    <Default Extension="dll" ContentType="application/octet-stream" />   
    <Default Extension="png" ContentType="application/octet-stream" />   
    <Default Extension="txt" ContentType="text/plain" />   
    <Default Extension="pkgdef" ContentType="text/plain" />   
</Types>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Riferimento dello Schema 1.0 estensione VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: Un nuovo Standard per l'assemblaggio dei dati](http://go.microsoft.com/fwlink/?LinkID=148207)