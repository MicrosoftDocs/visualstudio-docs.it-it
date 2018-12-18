---
title: Riferimento allo Schema 2.0 di VSIX Language Pack | Documenti Microsoft
ms.custom: ''
ms.date: 10/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
ms.author: dagriffe
author: dgriffen
manager: douge
ms.workload:
- dagriffe
ms.openlocfilehash: 571f90f31014dcc4d5686483bfc037e458f4a31e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="vsix-language-pack-schema-20-reference"></a>Riferimento allo Schema 2.0 di VSIX Language Pack

Lo schema di Language Pack VSIX fornisce informazioni sull'installazione localizzata per i pacchetti VSIX. La versione 2.0 di questo schema supporta gli elementi di localizzazione aggiuntive.

## <a name="language-pack-schema"></a>Schema di Language Pack

L'elemento radice del file language pack è `<PackageLanguagePackManifest>`, con un attributo di `Version`, che è la versione del formato language pack. In questo argomento descrive versione 2.0 del formato language pack, che viene specificato nel manifesto impostando il `Version` al valore dell'attributo `Version="2.0.0"`. L'elemento radice contiene esattamente un elemento figlio `<Metadata>` elemento.

### <a name="packagelangaugepackmanifest-element"></a>Elemento PackageLangaugePackManifest

All'interno di `<PackageLanguagePackManifest>` elemento deve essere presente l'elemento seguente:
|Titolo|Descrizione|
|-----------|-----------------|
|`<Metadata>`| Elemento contenitore per tutti i metadati di un pacchetto localizzato

### <a name="metadata-element"></a>Elemento dei metadati

All'interno di `<Metadata>` elemento si può presentare gli elementi seguenti:
|Titolo|Descrizione|
|-----------|-----------------|
|`<DisplayName>`|Il nome localizzato dell'estensione da installare|
|`<Description>`|La descrizione localizzata dell'estensione da installare|
|`<License>`| Il percorso di una versione localizzata di licenza dell'estensione|
|`<MoreInfo>`| Un collegamento a informazioni localizzate sull'estensione|
|`<ReleaseNotes>`| Un percorso o un collegamento a una versione localizzata di note sulla versione|
|`<Icon>`| Il percorso di una versione localizzata dell'icona di estensioni|

### <a name="sample-manifest"></a>Manifesto di esempio

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</LocalizedName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>Vedere anche

|Titolo|Descrizione|
|-----------|-----------------|
|[Localizzazione di pacchetti VSIX](../extensibility/localizing-vsix-packages.md)|Viene illustrato come fornire supporto di installazione localizzato per un pacchetto VSIX.|
|[Riferimenti su VSIX Extension Schema 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)|Un manifesto VSIX descrive il contenuto di un file di distribuzione VSIX, che consente di essere installato con un'estensione di Visual Studio il **estensioni e aggiornamenti** la finestra di dialogo.|
|[Ricerca e uso delle estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)|Viene illustrato come utilizzare il **estensioni e aggiornamenti** la finestra di dialogo per installare, rimuovere, attivare e disabilitare le estensioni.|