---
title: Localizzazione di pacchetti VSIX | Documenti Microsoft
ms.custom: ''
ms.date: 10/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d94e390374ca2eb77b4332b3a5c253acce69f051
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="localizing-vsix-packages"></a>Localizzazione di pacchetti VSIX

È possibile localizzare un pacchetto VSIX creando un file vsixlangpack per ogni lingua di destinazione e quindi li inserisce nella cartella corretta. Quando si installa un pacchetto di aggiornamento, viene visualizzato il nome localizzato dell'estensione con una descrizione localizzata. Se si specifica un file di licenza localizzato, o un URL che punta alle informazioni localizzate, vengono anche visualizzate.

Se il contenuto del pacchetto VSIX include un VSPackage che aggiunge i comandi di menu o altra interfaccia utente, vedere [localizzazione i comandi di Menu](../extensibility/localizing-menu-commands.md) per informazioni sulla localizzazione i nuovi elementi dell'interfaccia utente.

## <a name="directory-structure"></a>Struttura di directory

 Quando un utente installa un'estensione, **estensioni e aggiornamenti** controlla il livello principale del pacchetto VSIX per una cartella il cui nome corrisponde alle impostazioni di Visual Studio locali del computer di destinazione. Se **estensioni e aggiornamenti** trova una con estensione vsixlangpack file nella cartella, lo sostituisce con i valori in tale file per i valori corrispondenti, il file con estensione vsixmanifest localizzati. Questi valori vengono visualizzati quando viene installato l'estensione. Nell'esempio seguente mostra la struttura di directory per un pacchetto VSIX che è localizzato in spagnolo (es-ES) e francese (fr-FR).  

```text
.
├── MyExtension.dll
├── Extension.vsixmanifest
├── [Content_Types].xml
├── es-ES
│   └── Extension.vsixlangpack
└── fr-FR
    └── Extension.vsixlangpack
```

> [!NOTE]
> I modelli di progetto supportati VSIX il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] generare un manifesto VSIX e assegnargli il nome vsixmanifest. Quando Visual Studio compila il progetto, copia il contenuto del file in vsixmanifest nel pacchetto VSIX.

## <a name="the-extensionvsixlangpack-file"></a>Il File vsixlangpack

Il file vsixlangpack segue il [VSIX Language Pack Schema 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Questo schema presenta un `PackageLanguagePackManifest`, seguito da un `Metadata` elemento figlio. L'elemento dei metadati può contenere fino a 6 elementi figlio, `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, e `Icon`. Tali elementi figlio corrispondano per il `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, e `Icon` gli elementi figlio del `Metadata` elemento del file Extension. vsixmanifest.

Quando si crea un file vsixlangpack, è necessario impostare il `Include in Vsix` proprietà `true`. In caso contrario, il testo di installazione localizzato verrà ignorato.

### <a name="to-set-the-include-in-vsix-property"></a>Per impostare l'inclusione in proprietà progetto Vsix

1. In **Esplora**vsixlangpack destro e quindi fare clic su **proprietà**.

2.  Nella griglia delle proprietà, fare clic su **Includi in Vsix**e impostarne il valore su `true`.

## <a name="example"></a>Esempio

### <a name="description"></a>Descrizione

L'esempio seguente mostra le parti pertinenti di un file Extension. vsixmanifest, insieme al file vsixlangpack corrispondente per lo spagnolo. Se le impostazioni locali di Visual Studio del computer di destinazione sono impostata sullo spagnolo, i valori del language pack sostituiscono i valori nel manifesto.

### <a name="code"></a>Codice

 [Extension. vsixmanifest]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest ...>
  <Metadata ...>
    <DisplayName>Family Tree</DisplayName>
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>
    <MoreInfo>http://www.contoso.com/products/FamilyTree.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
  <Installation .../>
  <Dependencies .../>
  <Prerequisites .../>
  <Assets .../>
</PackageManifest>
```

 [Vsixlangpack]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</DisplayName>
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
|[Riferimento dello Schema LanguagePack 2.0 VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Un language pack VSIX descrive le informazioni di localizzazione di un file di distribuzione VSIX.|
|[Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Descrive la struttura e contenuto di un pacchetto vsix.|
|[Localizzazione dei comandi di menu](../extensibility/localizing-menu-commands.md)|Viene illustrato come localizzare le risorse di altro testo in un'estensione.|