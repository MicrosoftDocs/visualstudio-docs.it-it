---
title: Proprietà file, JavaScript | Microsoft Docs
ms.custom: ''
ms.date: 06/21/2017
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- javascript.project.property.expandedsdknode.fileversion
- javascript.project.property.expandedsdknode.uri
- javascript.project.property.expandedsdknode.filename
- javascript.project.property.reference.description
- javascript.project.property.reference.specificversion
- javascript.project.property.reference.identity
- javascript.project.property.fullpath
- javascript.project.property.packageaction
- javascript.project.property.reference.package
- javascript.project.property.copytooutputdirectory
- javascript.project.property.expandedsdknode.sdkpath
- javascript.project.property.reference.filetype
- javascript.project.property.reference.culture
- javascript.project.property.filename
- javascript.project.property.reference.resolvedpath
- javascript.project.property.reference.version
ms.assetid: 085913b8-a97b-45f7-85fa-bbb0902f3ee9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 06fd31fc8d87dc40df023cbf494fde16c944ae03
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="file-properties-javascript"></a>Proprietà file, JavaScript
È possibile usare le proprietà file per indicare le operazioni che il sistema di progetto dovrà eseguire sui file. Ad esempio, è possibile impostare le proprietà file per indicare se un file deve essere aggiunto al pacchetto come file di risorse.  

 È possibile selezionare qualunque file in Esplora soluzioni ed esaminare, quindi, le relative proprietà nella finestra Proprietà. I file JavaScript hanno quattro proprietà: **Copia nella directory di output**, **Azione pacchetto**, **Nome file** e **Percorso file**.  

## <a name="file-properties"></a>Proprietà file  
 In questa sezione vengono descritte le proprietà comuni ai file JavaScript.  

### <a name="copy-to-output-directory-property"></a>Proprietà Copia nella directory di output  
 Questa proprietà specifica le condizioni in cui il file di origine selezionato verrà copiato nella directory di output. Selezionare **Non copiare** se il file non deve mai essere copiato nella directory di output. Selezionare **Copia sempre** se il file deve essere copiato sempre nella directory di output. Selezionare **Copia se più recente** se il file deve essere copiato solo quando è più recente di un file esistente con lo stesso nome nella directory di output.  

### <a name="package-action"></a>Azione pacchetto  
 La proprietà **Azione pacchetto** indica ciò che realizza Visual Studio con un file quando viene eseguita una compilazione. **Azione pacchetto** può avere diversi valori:  

-   **Nessuno** - Il file non è incluso nel manifesto del pacchetto. Un esempio è un file di testo che contiene la documentazione, ad esempio un file Leggimi.  

-   **Contenuto** - Il file è incluso nel manifesto di pacchetto. Ad esempio, questa impostazione è il valore predefinito di un file .htm, .js, .css, immagine, audio o video.  

-   **Manifesto** - Il file non è incluso nel manifesto di pacchetto. Il file viene usato invece per l'input durante la generazione del manifesto di pacchetto. Questo è il valore predefinito del file package.appxmanifest.  

-   **Risorsa** - Il file non è incluso nel manifesto di pacchetto. Il contenuto del file viene invece indicizzato nel file di indice risorse (PRI) che va inserito nel manifesto di pacchetto. Viene usato generalmente per i file di risorse.  

Il valore predefinito per **Azione pacchetto** dipende dall'estensione del file aggiunta alla soluzione.  

### <a name="file-name-property"></a>Proprietà nome file  
 Visualizza il nome del file come un valore di sola lettura. Per rinominarlo, fare clic con il pulsante destro del mouse sul file in Esplora soluzioni e scegliere **Rinomina**.  

### <a name="full-path-property"></a>Proprietà Percorso completo  
 Visualizza il percorso completo del file come valore di sola lettura. Per modificare il percorso del file, è possibile trascinare il file in Esplora soluzioni.  

## <a name="reference-file-properties"></a>Proprietà File di riferimento  
 In questa sezione vengono descritte le proprietà comuni ai file cui fa riferimento un'app UWP sviluppata con JavaScript. Quando si seleziona un riferimento come un file con estensione .winmd, un riferimento SDK, un riferimento da progetto a progetto o un riferimento ad assembly in Esplora soluzioni, le altre proprietà possono essere visualizzate nella finestra Proprietà, in base al tipo di file.  

### <a name="culture"></a>Impostazioni cultura  
 Visualizza la lingua associata al riferimento.  

### <a name="file-type"></a>Tipo di file  
 Visualizza il tipo di file del riferimento.  

### <a name="file-version"></a>Versione file  
 Visualizza la versione file del riferimento.  

### <a name="identity"></a>identità  
 Visualizza l'identità del riferimento utilizzato nel progetto, archiviato nel file di progetto.  

### <a name="package"></a>Pacchetto  
 Visualizza il nome del manifesto di pacchetto associato al riferimento.  

### <a name="resolved-path"></a>Percorso risolto  
 Visualizza il percorso del riferimento utilizzato nel progetto.  

### <a name="sdk-path"></a>Percorso SDK  
 Visualizza il percorso al file SDK cui viene fatto riferimento.  

### <a name="uri"></a>URI  
 Visualizza l'URI che deve essere incluso nel file HTML o JavaScript del progetto per includere il file come file di origine.  

### <a name="version"></a>Versione  
 Visualizza la versione del riferimento.  

## <a name="see-also"></a>Vedere anche  
 [Gestione delle proprietà di progetti e soluzioni](../../ide/managing-project-and-solution-properties.md)
