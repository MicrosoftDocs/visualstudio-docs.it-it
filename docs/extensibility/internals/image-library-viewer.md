---
title: Visualizzatore della libreria di immagini | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d9c7fbb-ebae-4b20-9dd8-3c9070c0d0d1
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b699233d0b0ddf14079240da3bd831a172641fba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="image-library-viewer"></a>Visualizzatore della libreria di immagini
Lo strumento Visualizzatore di Visual Studio Image Library è possibile caricare e la ricerca di manifesti dell'immagine, consentendo all'utente di modificarli in modo identico a Visual Studio. L'utente può modificare in background, le dimensioni, DPI, contrasto elevato e altre impostazioni. Inoltre, lo strumento visualizza le informazioni di caricamento per ogni manifesto immagine e visualizza le informazioni di origine per ogni immagine nel manifesto dell'immagine. Questo strumento è utile per:  
  
1.  Diagnostica degli errori  
  
2.  Verifica gli attributi sono impostati correttamente nei manifesti immagine personalizzata  
  
3.  Ricerca per le immagini in Visual Studio immagine catalogo in modo che un'estensione di Visual Studio è possibile utilizzare le immagini di adattare lo stile di Visual Studio  
  
 ![Immagine principale del Visualizzatore della libreria](../../extensibility/internals/media/image-library-viewer-hero.png "principale del Visualizzatore della libreria di immagini")  
  
 **Moniker dell'immagine**  
  
 Un moniker immagine (o un moniker per breve) è una coppia GUID: ID che identifica in modo univoco un asset di immagine o risorsa di elenco di immagine nella raccolta immagini.  
  
 **File manifesto immagine**  
  
 File di immagine manifesto (.imagemanifest) sono file XML che definiscono un set di risorse di immagini, il moniker che rappresentano tali risorse e l'immagine reale o le immagini per rappresentare ogni asset. Manifesti dell'immagine è possibile definire immagini autonome o elenchi di immagini per il supporto dell'interfaccia utente legacy. Inoltre, esistono attributi che è possibile impostare nell'asset o delle singole immagini dietro ogni asset cambiare la data e la modalità di visualizzazione di tali risorse.  
  
 **Schema del manifesto di immagini**  
  
 Un manifesto di completare l'immagine è simile al seguente:  
  
```xml  
<ImageManifest>  
      <!-- zero or one Symbols elements -->  
      <Symbols>  
        <!-- zero or more Guid, ID, or String elements -->  
      </Symbols>  
      <!-- zero or one Images elements -->  
      <Images>  
        <!-- zero or more Image elements -->  
      </Images>  
      <!-- zero or one ImageLists elements -->  
      <ImageLists>  
        <!-- zero or more ImageList elements -->  
      </ImageLists>  
</ImageManifest>  
```  
  
 **Simboli**  
  
 Come favorire un leggibilità e la manutenzione, il manifesto di immagini è possibile usare i simboli per i valori di attributo. I simboli sono definiti come segue:  
  
```xml  
<Symbols>  
      <Import Manifest="manifest" />  
      <Guid Name="ShellCommandGuid" Value="8ee4f65d-bab4-4cde-b8e7-ac412abbda8a" />  
      <ID Name="cmdidSaveAll" Value="1000" />  
      <String Name="AssemblyName" Value="Microsoft.VisualStudio.Shell.UI.Internal" />  
</Symbols>  
```  
  
|||  
|-|-|  
|**Sottoelemento**|**Definizione**|  
|Import|Importa i simboli del file manifesto specificato per l'utilizzo nel manifesto corrente.|  
|GUID|Il simbolo rappresenta un GUID e deve corrispondere la formattazione di GUID.|  
|Id|Il simbolo rappresenta un ID e deve essere un numero intero non negativo.|  
|Stringa|Il simbolo rappresenta un valore stringa arbitraria.|  
  
 I simboli sono maiuscole / minuscole e di cui viene fatto riferimento utilizzando la sintassi $(symbol-name):  
  
```xml  
<Image Guid="$(ShellCommandGuid)" ID="$(cmdidSaveAll)" >  
      <Source Uri="/$(AssemblyName);Component/Resources/image.xaml" />  
</Image>  
```  
  
 Alcuni simboli sono predefiniti per tutti i manifesti. Possono essere usati nell'attributo dell'Uri di \<origine > o \<importazione > elemento ai percorsi di riferimento sul computer locale.  
  
|||  
|-|-|  
|**Simbolo**|**Descrizione**|  
|CommonProgramFiles|Il valore della variabile di ambiente % CommonProgramFiles %|  
|LocalAppData|Il valore della variabile di ambiente % LocalAppData %|  
|ManifestFolder|La cartella contenente il file manifesto|  
|Documenti|Il percorso completo della cartella documenti dell'utente corrente|  
|ProgramFiles|Il valore della variabile di ambiente % ProgramFiles %|  
|System|Nella cartella Windows\System32|  
|WinDir|Il valore della variabile di ambiente % WinDir %|  
  
 **Immagine**  
  
 Il \<immagine > elemento definisce un'immagine che è possibile fare riferimento da un moniker. Il GUID e l'ID nel loro insieme costituiscono il moniker dell'immagine. Il moniker per l'immagine deve essere univoco tra la libreria di immagini intero. Se più di un'immagine è un moniker specificato, il primo durante la compilazione della libreria è quello che viene mantenuto.  
  
 Deve contenere almeno un'origine. La dimensione neutral origini fornirà i migliori risultati in una vasta gamma di dimensioni, non sono necessarie. Se il servizio è richiesto per un'immagine di dimensioni non è stata definita il \<immagine > elemento ed è presente alcuna origine indipendente dalla dimensione, il servizio scegliere la migliore fonte di dimensioni specifiche e applicarvi la scalabilità per la dimensione richiesta.  
  
```xml  
<Image Guid="guid" ID="int" AllowColorInversion="true/false">  
      <Source ... />  
      <!-- optional additional Source elements -->  
</Image>  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|GUID|[Obbligatorio] La parte GUID del moniker di immagini|  
|Id|[Obbligatorio] La porzione dell'ID del moniker immagine|  
|AllowColorInversion|[Facoltativo, valore predefinito true] Indica se l'immagine può avere i colori invertiti a livello di codice quando viene utilizzata su uno sfondo scuro.|  
  
 **Origine**  
  
 Il \<origine > elemento definisce una risorsa di origine immagine singola (XAML e PNG).  
  
```xml  
<Source Uri="uri" Background="background">  
      <!-- optional NativeResource element -->  
 </Source>  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|URI|[Obbligatorio] URI che definisce dove è possibile caricare l'immagine da. Può essere uno dei valori seguenti:<br /><br /> -A [URI di tipo Pack](http://msdn.microsoft.com/en-US/library/aa970069\(v=vs.100\).aspx) utilizzando l'applicazione: / / / autorità<br /><br /> -Un riferimento a una risorsa componente assoluto<br /><br /> -Un percorso di un file contenente una risorsa nativa|  
|Sfondo|[Facoltativo] Indica l'oggetto tipo di sfondo che dell'origine deve essere utilizzata.<br /><br /> Può essere uno dei valori seguenti:<br /><br /> - *Luce*: l'origine può essere utilizzata su uno sfondo.<br /><br /> - *Scuro*: l'origine può essere utilizzata su uno sfondo scuro.<br /><br /> - *Contrasto elevato*: l'origine può essere utilizzata su qualsiasi sfondo in modalità a contrasto elevato.<br /><br /> - *HighContrastLight*: l'origine può essere utilizzata su uno sfondo di colore in modalità a contrasto elevato.<br /><br /> -*HighContrastDark*: l'origine può essere utilizzata su uno sfondo scuro in modalità a contrasto elevato.<br /><br /> Se il **Background** attributo viene omesso, l'origine può essere utilizzato in qualsiasi dello sfondo.<br /><br /> Se **Background** è *luce*, *scuro*, *HighContrastLight*, o *HighContrastDark*, i colori dell'origine non vengono mai invertiti. Se **Background** viene omesso o impostato su *contrasto elevato*, l'inversione dei colori dell'origine viene controllata l'immagine **AllowColorInversion** attributo.|  
  
 Oggetto \<origine > elemento può avere uno e uno solo dei sottoelementi facoltativi seguenti:  
  
||||  
|-|-|-|  
|**Elemento**|**Attributi (tutti necessari)**|**Definizione**|  
|\<Dimensioni >|Valore|L'origine verrà utilizzata per le immagini della dimensione specificata (in unità dispositivo). L'immagine sarà quadrato.|  
|\<SizeRange >|MinSize, MaxSize|L'origine verrà utilizzata per le immagini da MinSize MaxSize (in unità dispositivo), inclusi. L'immagine sarà quadrato.|  
|\<Dimensioni >|Larghezza, altezza|L'origine verrà utilizzata per le immagini di una determinata larghezza e altezza (in unità dispositivo).|  
|\<DimensionRange >|MinWidth, MinHeight,<br /><br /> MaxWidth, MaxHeight|L'origine verrà utilizzata per le immagini dalla larghezza/altezza minima di larghezza/altezza massima (in unità dispositivo), inclusi.|  
  
 Oggetto \<origine > elemento può avere anche un parametro facoltativo \<NativeResource > sottoelemento che definisce un \<origine > che viene caricato da un assembly nativo piuttosto che da un assembly gestito.  
  
```xml  
<NativeResource Type="type" ID="int" />  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|Tipo|[Obbligatorio] Il tipo di risorsa nativa, XAML o PNG|  
|Id|[Obbligatorio] Il quoziente di ID di risorsa nativa|  
  
 **ImageList**  
  
 Il \<ImageList > elemento definisce una raccolta di immagini che possono essere restituite in un singolo elenco. L'elenco viene compilato su richiesta, in base alle esigenze.  
  
```xml  
<ImageList>  
      <ContainedImage Guid="guid" ID="int" External="true/false" />  
      <!-- optional additional ContainedImage elements -->  
 </ImageList>  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|GUID|[Obbligatorio] La parte GUID del moniker di immagini|  
|Id|[Obbligatorio] La porzione dell'ID del moniker immagine|  
|Altre informazioni|[Impostazione predefinita è false, facoltativo] Indica se il moniker dell'immagine fa riferimento a un'immagine nel manifesto corrente.|  
  
 Il moniker per l'immagine contenuta non è necessario fare riferimento a un'immagine definita nel manifesto corrente. Se l'immagine del contenuto non viene trovato nella raccolta immagini, un'immagine segnaposto vuoto verrà utilizzata al suo posto.  
  
## <a name="how-to-use-the-tool"></a>Come utilizzare lo strumento  
 **Convalida di un manifesto immagine personalizzata**  
  
 Per creare un manifesto personalizzato, è consigliabile utilizzare lo strumento ManifestFromResources per generare automaticamente il manifesto. Per convalidare il manifesto personalizzato, avviare il Visualizzatore della libreria di immagini e selezionare File > imposta percorsi... per aprire la finestra di dialogo Directory di ricerca. Directory di ricerca verrà utilizzato per caricare i manifesti dell'immagine, ma è necessario utilizzarlo anche per trovare i file DLL che contengono le immagini in un manifesto, pertanto assicurarsi di includere il manifesto e directory DLL in questa finestra di dialogo.  
  
 ![Ricerca del Visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-search.png "ricerca del Visualizzatore della libreria di immagini")  
  
 Fare clic su **Aggiungi...**  per selezionare una nuova directory di ricerca per cercare i manifesti e le relative DLL corrispondente. Lo strumento verrà memorizzate le directory di ricerca e può essere attivate o disattivata selezionando o deselezionando una directory.  
  
 Per impostazione predefinita, lo strumento tenterà di trovare la directory di installazione di Visual Studio e aggiungere tali directory all'elenco di directory di ricerca. È possibile aggiungere manualmente le directory che non viene trovato lo strumento.  
  
 Una volta che vengono caricati tutti i manifesti, lo strumento consente di attivare o disattivare **background** colori, **DPI**, **contrasto elevato**, o **grigio** per le immagini in modo che un utente può controllare visivamente gli asset delle immagini per verificare che viene eseguito il rendering correttamente per diverse impostazioni.  
  
 ![Immagine di sfondo del Visualizzatore della libreria](../../extensibility/internals/media/image-library-viewer-background.png "immagine di sfondo del Visualizzatore della libreria")  
  
 Il colore di sfondo può essere impostato chiaro, scuro o un valore personalizzato. Selezionando "Colore personalizzato" aprire una finestra di dialogo di selezione colore e aggiunge tale colore personalizzato nella parte inferiore della casella combinata in background per semplice richiamo in un secondo momento.  
  
 ![Colore personalizzato del Visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-custom-color.png "colore personalizzato del Visualizzatore della libreria di immagini")  
  
 Selezionando un moniker di immagini consente di visualizzare le informazioni per ogni immagine reale dietro il moniker nel riquadro dei dettagli di immagine a destra. Il riquadro consente anche agli utenti di copiare un moniker in base al nome o valore non elaborato coppia GUID: ID.  
  
 ![I dettagli dell'immagine del Visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-image-details.png "immagine i dettagli del Visualizzatore della libreria di immagini")  
  
 Le informazioni visualizzate per ogni origine dell'immagine includono il tipo di sfondo per visualizzarlo, se è possibile applicare un tema o supporta contrasto elevato, le dimensioni è valido per o se è indipendente dalla dimensione e indica se l'immagine viene recuperato da un assembly nativo.  
  
 ![Visualizzatore della libreria di immagini può tema](../../extensibility/internals/media/image-library-viewer-can-theme.png "Visualizzatore della libreria di immagini può tema")  
  
 Quando si convalida un manifesto di immagini, è consigliabile distribuire il manifesto e l'immagine DLL nei rispettivi percorsi reali. Ciò consente di verificare che tutti i percorsi relativi sono funzioni correttamente e che la libreria di immagini è possibile individuare e caricare il manifesto e l'immagine DLL.  
  
 **Cercare il catalogo di immagini KnownMonikers**  
  
 Per una migliore corrispondenza lo stile di Visual Studio, un'estensione di Visual Studio possa usare le immagini nel catalogo di immagini Visual Studio anziché creando e con i propri. Questo ha il vantaggio di non dover gestire tali immagini e garantisce che l'immagine avrà un'immagine a DPI elevato in modo dovrebbe essere corretto in tutte le impostazioni DPI che supporta Visual Studio.  
  
 Il Visualizzatore della libreria di immagini consente di eseguire la ricerca in modo che un utente può trovare il moniker che rappresenta una risorsa immagine, usare il moniker nel codice un manifesto. Per cercare le immagini, immettere il termine di ricerca desiderato nella casella di ricerca e premere INVIO. La barra di stato nella parte inferiore verrà visualizzato il numero di corrispondenze trovato fuori le immagini totale in tutti i manifesti.  
  
 ![Filtro del Visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-filter.png "filtro del Visualizzatore della libreria di immagini")  
  
 Quando si cerca il moniker di immagini nei manifesti esistenti, è consigliabile cercare di utilizzare solo i moniker di Visual Studio immagine del catalogo, altri moniker intenzionalmente pubblicamente accessibile o il propria moniker personalizzati. Se si utilizza il moniker non pubblico, interfaccia utente personalizzata potrebbe essere interrotta o le relative immagini cambiano in modo imprevisto se o quando tali moniker non pubblici e le immagini vengono modificate o aggiornate.  
  
 Inoltre, è possibile ricerca in base al GUID. Questo tipo di ricerca è utile per il filtro in basso nell'elenco a un unico manifesto o sottosezione singola di un manifesto manifesto se contiene più GUID.  
  
 ![GUID filtro del Visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-filter-guid.png "GUID filtro del Visualizzatore della libreria di immagini")  
  
 Infine, la ricerca per ID è possibile anche.  
  
 ![ID filtro del Visualizzatore della libreria di immagini](../../extensibility/internals/media/image-library-viewer-filter-id.png "ID filtro del Visualizzatore della libreria di immagini")  
  
## <a name="notes"></a>Note  
  
-   Per impostazione predefinita, lo strumento effettuerà il pull nei manifesti di immagine più presenti nella directory di installazione di Visual Studio. È l'unico moniker pubblicamente utilizzabile con il **Microsoft.VisualStudio.ImageCatalog** manifesto. GUID: ae27a6b0-e345-4288-96df-5eaf394ee369 (eseguire **non** eseguire l'override di questo GUID in un manifesto personalizzato) tipo: KnownMonikers  
  
-   Lo strumento tenta di caricare tutti i manifesti dell'immagine, che ne viene trovato, pertanto potrebbe richiedere alcuni secondi per l'applicazione venga effettivamente visualizzato viene avviata. Potrebbe inoltre essere lento o che non risponde durante il caricamento dei manifesti.  
  
## <a name="sample-output"></a>Esempio di output  
 Questo strumento non genera alcun output.