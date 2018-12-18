---
title: Manifesto dalle risorse | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0234109b-5dcb-4d9d-acb9-a63f8bd5699c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 514135e5c6ba932d7b3b4319dd39c1df4e8cb212
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="manifest-from-resources"></a>Manifesto da risorse
Il manifesto dallo strumento di risorse è un'applicazione console che accetta un elenco di risorse immagine (file con estensione PNG o XAML) e genera un file .imagemanifest che consente le immagini da utilizzare con il servizio di immagini di Visual Studio. Inoltre, questo strumento può essere utilizzato per aggiungere immagini a un .imagemanifest esistente. Questo strumento è utile per aggiungere supporto per immagini a un'estensione di Visual Studio ad alta risoluzione e temi. Il file generato .imagemanifest deve essere incluso in e distribuito come parte di un'estensione di Visual Studio (VSIX).  
  
## <a name="how-to-use-the-tool"></a>Come utilizzare lo strumento  
 **Sintassi**  
  
 ManifestFromResources /Resources.:\<Dir1 >;\< Img1 > /assembly:\<AssemblyName > \<Args facoltativo >  
  
 **Argomenti**  
  
||||  
|-|-|-|  
|**Nome del commutatore**|**Note**|**Obbligatorio o facoltativo**|  
|/risorse|Un elenco delimitato da punto e virgola di immagini o directory. Questo elenco deve contenere sempre l'elenco completo delle immagini presenti nel manifesto. Se viene fornito un elenco parziale, solo le voci incluse non andranno perse.<br /><br /> Se un file di risorse specificato è un elenco di immagini, lo strumento verrà dividerlo in diverse immagini prima di aggiungere ogni immagine secondaria per il manifesto.<br /><br /> Se l'immagine è un file con estensione png, è consigliabile formattare il nome simile al seguente in modo che sia possibile compilare lo strumento gli attributi per l'immagine di destra: \<nome >.\< Larghezza >. \<Altezza > PNG.|Obbligatorio|  
|/assembly|Il nome di assembly gestiti (senza includere l'estensione) o il percorso di runtime dell'assembly nativo che ospita le risorse (relativo al percorso di runtime del manifesto).|Obbligatorio|  
|/manifest|Nome da assegnare al file .imagemanifest generato. Possono anche includere un percorso assoluto o relativo per creare il file in un percorso diverso. Il nome predefinito corrisponde al nome di assembly.<br /><br /> Impostazione predefinita: \<Directory corrente >\\< Assembly\>.imagemanifest|Facoltativo|  
|/guidName|Il nome da assegnare al simbolo GUID per tutte le immagini nel manifesto generato.<br /><br /> Predefinito: AssetsGuid|Facoltativo|  
|/rootPath|Il percorso radice che devono essere rimosse prima di creare gli URI di risorsa gestita. (Questo flag è per consentire ai casi in cui lo strumento Ottiene errato, a causa di risorse a non riuscire a caricare il percorso URI relativo).<br /><br /> Impostazione predefinita: \<Directory corrente >|Facoltativo|  
|/Recursive|L'impostazione di questo flag indica che lo strumento in modo ricorsivo tutte le directory di ricerca nell'argomento /Resources. L'omissione di questo flag comporterà una ricerca di top-livello solo delle directory.|Facoltativo|  
|/isNative|Impostare questo flag quando l'argomento di assembly è un percorso per un assembly nativo. Quando l'argomento di assembly è il nome di un assembly gestito, omettere questo flag. (Vedere la sezione Note per ulteriori informazioni su questo flag).|Facoltativo|  
|/newGuids|Impostare questo flag indica allo strumento per creare un nuovo valore per il simbolo GUID delle immagini anziché nel manifesto esistente con quello di unione.|Facoltativo|  
|/newIds|Impostare questo flag indica allo strumento per creare nuovi valori di ID simbolo per ogni immagine anziché l'unione di valori del manifesto esistente.|Facoltativo|  
|/noLogo|Impostare questo flag arresta prodotto e il copyright di stampare le informazioni.|Facoltativo|  
|/?|Stampare le informazioni della Guida.|Facoltativo|  
|/help|Stampare le informazioni della Guida.|Facoltativo|  
  
 **Esempi**  
  
-   ManifestFromResources /resources:D:\Images /assembly:My.Assembly.Name /isNative  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /manifest:MyImageManifest.imagemanifest  
  
-   ManifestFromResources /resources:D:\Images\Image1.png;D:\Images\Image1.xaml /assembly:My.Assembly.Name /guidName:MyImages /newGuids /newIds  
  
## <a name="notes"></a>Note  
  
-   Lo strumento supporta solo file con estensione png e XAML. Qualsiasi altro tipo di immagine o un file verrà ignorato. Viene generato un avviso per tutti i tipi non supportati durante l'analisi delle risorse. Se non supportata immagini vengono rilevate quando è terminato lo strumento di analisi delle risorse, verrà generato un errore  
  
-   Seguendo il formato consigliato per le immagini PNG, lo strumento imposterà il valore di dimensioni e delle dimensioni per il formato PNG per le dimensioni di formato specificato, anche se differisce dalla dimensione effettiva dell'immagine.  
  
-   Il formato di larghezza/altezza può essere omesso per le immagini PNG, ma lo strumento leggerà larghezza/altezza effettiva dell'immagine e utilizzarli per il valore di dimensioni e delle dimensioni dell'immagine.  
  
-   Eseguire questo strumento nell'elenco di immagine stessa più volte per la stessa .imagemanifest comporterà voci duplicate di manifesto, perché lo strumento tenta di suddividere l'elenco di immagini in immagini autonome e aggiungerle al manifesto esistente.  
  
-   L'unione (omettendo /newGuids o /newIds) deve essere eseguita solo per i manifesti generati da strumenti. Manifesti che sono stati personalizzati o generati tramite altri mezzi potrebbero non essere uniti correttamente.  
  
-   Manifesti generati per assembly nativi potrebbero dover essere modificato manualmente dopo la generazione per rendere i simboli di ID corrisponde alla risorsa, ID file RC dell'assembly nativo.  
  
## <a name="sample-output"></a>Esempio di output  
 **Manifesto immagine semplice**  
  
 Un manifesto dell'immagine sarà simile a questo file XML:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!-- This file was generated by the ManifestFromResources tool.-->  
<!-- Version: 14.0.15197 -->  
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  
  <Symbols>  
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/Images" />  
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />  
    <ID Name="MyImage" Value="0" />  
  </Symbols>  
  <Images>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImage)">  
      <Source Uri="$(Resources)/Xaml/MyImage.xaml" />  
      <Source Uri="$(Resources)/Png/MyImage.16.16.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
  </Images>  
  <ImageLists />  
</ImageManifest>  
```  
  
 **Manifesto immagine per un elenco di immagini**  
  
 Un manifesto di immagini per un elenco immagini sarà simile a questo file XML:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!-- This file was generated by the ManifestFromResources tool.-->  
<!-- Version: 14.0.15197 -->  
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  
  <Symbols>  
    <String Name="Resources" Value="/My.Assembly.Name;Component/Resources/ImageStrip" />  
    <Guid Name="AssetsGuid" Value="{fb41b7ef-6587-480c-aa27-5b559d42cfc9}" />  
    <ID Name="MyImageStrip_0" Value="1" />  
    <ID Name="MyImageStrip_1" Value="2" />  
    <ID Name="MyImageStrip" Value="3" />  
  </Symbols>  
  <Images>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)">  
      <Source Uri="$(Resources)/MyImageStrip_0.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)">  
      <Source Uri="$(Resources)/MyImageStrip_1.png">  
        <Size Value="16" />  
      </Source>  
    </Image>  
  </Images>  
  <ImageLists>  
    <ImageList Guid="$(AssetsGuid)" ID="$(MyImageStrip)">  
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_0)" />  
      <ContainedImage Guid="$(AssetsGuid)" ID="$(MyImageStrip_1)" />  
    </ImageList>  
  </ImageLists>  
</ImageManifest>  
```  
  
 **Manifesto di immagini per le risorse di immagine nativa**  
  
 Un manifesto di immagini per le immagini native sarà simile a questo file XML:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!-- This file was generated by the ManifestFromResources tool.-->  
<!-- Version: 14.0.15198 -->  
<ImageManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns="http://schemas.microsoft.com/VisualStudio/ImageManifestSchema/2014">  
  <Symbols>  
    <String Name="Resources" Value="..\Assembly\Folder\My.Assembly.Name" />  
    <Guid Name="AssetsGuid" Value="{442d8739-efde-46a4-8f29-e3a1e5e7f8b4}" />  
    <ID Name="MyImage1" Value="0" />  
    <ID Name="MyImage2" Value="1" />  
  </Symbols>  
  <Images>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImage1)">  
      <Source Uri="$(Resources)">  
        <Size Value="16" />  
        <NativeResource ID="$(MyImage1)" Type="PNG" />  
      </Source>  
    </Image>  
    <Image Guid="$(AssetsGuid)" ID="$(MyImage2)">  
      <Source Uri="$(Resources)">  
        <Size Value="16" />  
        <NativeResource ID="$(MyImage2)" Type="PNG" />  
      </Source>  
    </Image>  
  </Images>  
  <ImageLists />  
</ImageManifest>  
```