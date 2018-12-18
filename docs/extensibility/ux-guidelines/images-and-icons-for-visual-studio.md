---
title: Immagini e icone per Visual Studio | Documenti Microsoft
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f410325e-9cf2-4f39-b6d7-b672121c2691
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 164a450ca346fe2bd7b267d951ce522d27f14160
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="images-and-icons-for-visual-studio"></a>Immagini e icone per Visual Studio
##  <a name="BKMK_ImageUseInVisualStudio"></a>Utilizzo di immagini in Visual Studio  
 Prima di creare l'oggetto grafico, si consiglia di rendere l'utilizzo delle immagini in più di 1.000 il [libreria di immagini di Visual Studio](http://www.microsoft.com/en-my/download/details.aspx?id=35825).  
  
### <a name="types-of-images"></a>Tipi di immagini  
  
-   **Icone**. Immagini di piccole dimensioni che vengono visualizzati nei comandi, gerarchie, modelli e così via. La dimensione di icona predefinita utilizzata in Visual Studio è un file PNG 16 x 16. Icone generate automaticamente dal servizio immagini generano il formato XAML per il supporto HDPI.  
  
     **Nota:** immagini vengono usati nel sistema di menu, non è necessario creare un'icona per ogni comando. Consultare [menu e comandi di Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md) per vedere se il comando deve ottenere un'icona.  
  
-   **Anteprime.** Immagini utilizzate nell'area di anteprima di una finestra di dialogo, ad esempio la finestra di dialogo Nuovo progetto.  
  
-   **Immagini di finestra di dialogo.** Immagini visualizzate nelle finestre di dialogo o le procedure guidate, come grafica descrittivo o indicatori di messaggio. Utilizzare raramente e solo quando è necessario per illustrare un concetto difficile o per ottenere l'attenzione dell'utente (avviso, avviso).  
  
-   **Immagini animate.** Utilizzare gli indicatori di stato, le barre di stato e le finestre di dialogo di operazione.  
  
-   **Cursori.** Utilizzato per indicare se un'operazione è consentita l'uso del mouse, in cui un oggetto può essere eliminato e così via.  
  
##  <a name="BKMK_IconDesign"></a>Progettazione di icona  
  
### <a name="overview"></a>Panoramica  
 Visual Studio Usa icone in stile moderno, geometry pulita e 50/50 giusto equilibrio tra positivo o negativo (chiaro o scuro), e utilizzano metafore dirette e comprensibile. Icona fondamentale il centro di punti di progettazione per maggiore chiarezza, semplificare le operazioni e il contesto.  
  
-   **Chiarezza:** concentrarsi sulla metafora di base che fornisce un'icona, il relativo significato e la tua personalità.  
  
-   **Semplificazione:** ridurre l'icona per il significato di base - ottenere il tema con solo gli elementi necessari e non increspature.  
  
-   **Contesto:** considerare tutti gli aspetti del ruolo di un'icona durante lo sviluppo, concetto che è fondamentale per decidere quali elementi costituiscono metafora core dell'icona.  
  
 Le icone, non vi sono un numero di punti di progettazione per evitare di:  
  
-   Non usare le icone che indicano gli elementi dell'interfaccia utente tranne nei casi appropriati. Scegliere un approccio più astratto o simbolico quando l'elemento dell'interfaccia utente comune, evidenti, né univoco.  
  
-   Non utilizzo eccessivo di elementi comuni, ad esempio documenti, cartelle, le frecce e sulla lente di ingrandimento. Utilizzare questi elementi solo quando è essenziale per il significato dell'icona. Ad esempio, la lente di ingrandimento rivolta verso destra deve indicare solo la ricerca, esplorare e trovare.  
  
-   Anche se alcuni elementi icona legacy mantengono l'utilizzo della prospettiva, non creare nuove icone con la prospettiva, a meno che l'elemento non dispone di maggiore chiarezza senza di esso.  
  
-   Non cram troppe informazioni in un'icona. Un'immagine semplice che può essere facilmente riconosciuta o appreso come simbolo riconoscibile è molto più utile rispetto a un'immagine eccessivamente complessa. Un'icona non è possibile per capire.  
  
### <a name="icon-creation"></a>Creazione di icone  
  
#### <a name="concept-development"></a>Sviluppo di concetto  
 Visual Studio è all'interno dell'interfaccia utente di un'ampia gamma di tipi di icona. Valutare attentamente il tipo di icona durante lo sviluppo. Non utilizzare gli oggetti dell'interfaccia utente comune o poco chiari per gli elementi di icona. Scegliere il collegamento simbolico in questi casi, ad esempio con l'icona dello Smart Tag. Si noti che il significato della classe astratta tag a sinistra è più evidenti rispetto alla versione dell'interfaccia utente basata su vagamente a destra:  
  
|||  
|-|-|  
|**Utilizzo corretto delle immagini simbolico**|**Utilizzo non corretto di immagini simbolico**|  
|![Icona Smart Tag corretta](../../extensibility/ux-guidelines/media/0404-01_smarttagcorrect.png "0404 01_SmartTagCorrect")|![Icona Smart Tag non corretta](../../extensibility/ux-guidelines/media/0404-02_smarttagincorrect.png "0404 02_SmartTagIncorrect")|  
  
 Esistono casi in cui gli elementi dell'interfaccia utente standard, facilmente riconoscibili funzionano anche per le icone. Aggiungi che finestra è un esempio:  
  
|||  
|-|-|  
|**Elemento dell'interfaccia utente corretto in un'icona**|**Elemento dell'interfaccia utente non corretto in un'icona**|  
|![Icona Aggiungi finestra corretta](../../extensibility/ux-guidelines/media/0404-03_addwindowcorrect.png "0404 03_AddWindowCorrect")|![Icona Aggiungi finestra corretta](../../extensibility/ux-guidelines/media/0404-04_addwindowincorrect.png "0404 04_AddWindowIncorrect")|  
  
 Non usare un documento come elemento di base, a meno che non è essenziale per il significato dell'icona. Senza il documento elemento nel documento aggiungere (il significato sotto) verrà perso, mentre con l'aggiornamento è necessario comunicare il significato di elemento del documento.  
  
|||  
|-|-|  
|**Uso corretto di icona documento**|**Utilizzo non corretto dell'icona di documento**|  
|![Icona documento corretta](../../extensibility/ux-guidelines/media/0404-05_documenticoncorrect.png "0404 05_DocumentIconCorrect")|![Icona documento corretta](../../extensibility/ux-guidelines/media/0404-06_documenticonincorrect.png "0404 06_DocumentIconIncorrect")|  
  
 Il concetto di "show" deve essere rappresentato dall'icona che meglio illustra ciò che viene visualizzato, ad esempio come con l'esempio mostra tutti i file. Una metafora obiettivo può essere utilizzata per indicare il concetto di "view", se necessario, ad esempio con l'esempio di visualizzazione delle risorse.  
  
|||  
|-|-|  
|**"Mostra"**|**"View"**|  
|![Mostra icona](../../extensibility/ux-guidelines/media/0404-07_show.png "0404 07_Show")|![Icona visualizzazione](../../extensibility/ux-guidelines/media/0404-08_view.png "0404 08_View")|  
  
 Il rivolta verso destra ingrandimento sull'icona a forma di deve rappresentare solo cercare, trovare e Sfoglia. La variante rivolta verso sinistra con il segno più o meno deve rappresentare solo zoom avanti / zoom indietro.  
  
|||  
|-|-|  
|**"Cerca"**|**"Zoom"**|  
|![Icona di ricerca](../../extensibility/ux-guidelines/media/0404-09_search.png "0404 09_Search")|![Icona Zoom](../../extensibility/ux-guidelines/media/0404-10_zoom.png "0404 10_Zoom")|  
  
 Nelle visualizzazioni albero, non utilizzare l'icona della cartella sia un modificatore. Quando è disponibile, è possibile utilizzare solo il modificatore.  
  
|||  
|-|-|  
|**Icone di visualizzazione albero corretto**|**Icone di visualizzazione albero non corretta**|  
|![Icona visualizzazione albero corretta &#40; 1 &#41; ] (../../extensibility/ux-guidelines/media/0404-11_treeviewcorrect1.png "0404 11_TreeViewCorrect1") ![correggere 2 icona visualizzazione albero &#40; &#41;] (../../extensibility/ux-guidelines/media/0404-12_treeviewcorrect2.png "0404 12_TreeViewCorrect2")|![Icona visualizzazione albero non corretta &#40; 1 &#41; ] (../../extensibility/ux-guidelines/media/0404-13_treeviewincorrect1.png "0404 13_TreeViewIncorrect1") ![corretto icona visualizzazione albero &#40; 2 &#41;] (../../extensibility/ux-guidelines/media/0404-14_treeviewincorrect2.png "0404 14_TreeViewIncorrect2")|  
  
### <a name="style-details"></a>Dettagli di stile  
  
#### <a name="layout"></a>Layout  
 Elementi dello stack, come illustrato per 16x16 icone standard:  
  
 ![Stack di layout per 16x16 icone](../../extensibility/ux-guidelines/media/0404-15_layoutstack.png "0404 15_LayoutStack")<br />Stack di layout per icone 16x16
  
 Elementi delle notifiche di stato sono più utilizzati come icone autonomo. Vi sono contesti, tuttavia, in cui una notifica deve essere in pila nell'elemento di base, ad esempio con un'icona attività completata:  
  
 ![Notifiche autonome in Visual Studio](../../extensibility/ux-guidelines/media/0404-16_standalonenotificationicons.png "0404 16_StandaloneNotificationIcons")<br />Icone di notifica autonomo
  
 ![Icona attività completata](../../extensibility/ux-guidelines/media/0404-17_taskcomplete.png "0404 17_TaskComplete")<br />Icona attività completata
  
 Icone di progetto sono in genere i file con estensione ico che contengono più dimensioni. La maggior parte delle 16x16 icone contengono gli stessi elementi. Le versioni a 32 x 32 include informazioni dettagliate, tra cui il tipo di progetto quando applicabile.  
  
 ![Progetto icone in Visual Studio](../../extensibility/ux-guidelines/media/0404-18_iconprojectthreesizes.png "0404 18_IconProjectThreeSizes")<br />Icone di progetto libreria di controlli Windows VB, 16 x 16 e 32 x 32 
  
 Centro di un'icona all'interno della cornice di pixel. Se ciò non è possibile, allineare l'icona nella parte superiore e/o a destra del frame.  
  
 ![Icona centrata nel frame di pixel](../../extensibility/ux-guidelines/media/0404-19_iconcentered.png "0404 19_IconCentered")<br />Icona centrata nel frame di pixel
  
 ![Icona allineata al lato superiore destro del frame di pixel](../../extensibility/ux-guidelines/media/0404-20_icontopright.png "0404 20_IconTopRight")<br />Icona allineata in alto a destra del frame
  
 ![Icona centrata e allineata al lato superiore del frame di pixel](../../extensibility/ux-guidelines/media/0404-21_icontopalign.png "0404 21_IconTopAlign")<br />Icona centrata e allineata nella parte superiore del frame
  
 Per raggiungere un equilibrio e allineamento ideale, evitare impediscono all'elemento di base dell'icona con glifi di azione. Posizione dell'icona nella parte superiore sinistra dell'elemento di base. Quando si aggiunge un ulteriore elemento, prendere in considerazione l'allineamento e il saldo dell'icona.  
  
|||  
|-|-|  
|**Equilibrio e allineamento corretto**|**Equilibrio e allineamento non corretto**|  
|![Correggere icona equilibrio e allineamento](../../extensibility/ux-guidelines/media/0404-22_alignbalancecorrect.png "0404 22_AlignBalanceCorrect")|![Icona non corretta equilibrio e allineamento](../../extensibility/ux-guidelines/media/0404-23_alignbalanceincorrect.png "0404 23_AlignBalanceIncorrect")|  
  
 Verificare la parità di dimensioni per le icone che condividono gli elementi e vengono utilizzati nel set. Si noti che nell'associazione corretto, il cerchio e freccia sono di grandi dimensioni e non corrispondono.  
  
|||  
|-|-|  
|**Parità di dimensioni corrette**|**Parità di dimensione non corretta**|  
|![Correggere icona dimensioni e parità](../../extensibility/ux-guidelines/media/0404-24_sizeparitycorrect.png "0404 24_SizeParityCorrect")|![Dimensioni dell'icona non corretto e parità](../../extensibility/ux-guidelines/media/0404-25_sizeparityincorrect.png "0404 25_SizeParityIncorrect")|  
  
 Utilizzare linee coerente e pesi visual. Valutare come l'icona che si sta compilando confrontata con altre icone utilizzando un confronto side-by-side. Utilizzare il frame di 16 x 16 intero, non utilizzare mai 15 x 15 o più piccolo. Il rapporto di un numero negativo per positivo (dark-chiaro) deve essere 50/50.  
  
|||  
|-|-|  
|**Rapporto di un numero negativo per positivo corretto**|**Rapporto di un numero negativo per positivo non corretto**|  
|![Correggere l'impatto visivo per le icone &#40; 1 &#41; ] (../../extensibility/ux-guidelines/media/0404-26_visualweightcorrect1.png "0404 26_VisualWeightCorrect1")<br /><br /> ![Correggere l'impatto visivo per le icone &#40; 2 &#41; ] (../../extensibility/ux-guidelines/media/0404-27_visualweightcorrect2.png "0404 27_VisualWeightCorrect2")<br /><br /> ![Correggere l'impatto visivo per le icone &#40; 3 &#41; ] (../../extensibility/ux-guidelines/media/0404-28_visualweightcorrect3.png "0404 28_VisualWeightCorrect3")|![Impatto visivo non corretto per le icone](../../extensibility/ux-guidelines/media/0404-29_visualweightincorrect.png "0404 29_VisualWeightIncorrect")|  
  
 Utilizzare forme confrontabili, semplice e degli angoli complementare per compilare elementi senza compromettere l'integrità di elemento. Dove possibile, utilizzare gli angoli di 45° o 90°.  
  
 ![Correggere gli angoli di icona](../../extensibility/ux-guidelines/media/0404-30_iconanglescorrect.png "0404 30_IconAnglesCorrect")  
  
#### <a name="perspective"></a>Prospettiva  
 Mantenere l'icona chiaro e comprensibile. Utilizzare prospettiva e una sorgente di luce solo quando necessario. Sebbene l'utilizzo della prospettiva per gli elementi di icona, è consigliabile evitare alcuni elementi sono non riconoscibile senza di esso. In questi casi, una prospettiva con stili comunica chiarezza dell'elemento.  
  
 ![prospettiva di 3 punto](../../extensibility/ux-guidelines/media/0404-31_3pointperspective.png "0404 31_3PointPerspective")<br />Prospettiva a tre punti
  
 ![1 punto prospettiva](../../extensibility/ux-guidelines/media/0404-32_1pointperspective.png "0404 32_1PointPerspective")<br />Prospettiva a un punto
  
 La maggior parte degli elementi devono essere affiancate o con angolazione verso destra:  
  
 ![Icone con angolazione corretta](../../extensibility/ux-guidelines/media/0404-33_angledright.png "0404 33_AngledRight")  
  
 Utilizzare sorgenti di luce solo durante l'aggiunta di chiarezza necessaria a un oggetto.  
  
|||  
|-|-|  
|**Sorgente di luce corrette**|**Sorgente di luce non corretto**|  
|![Sorgenti di luce per le icone di correggere](../../extensibility/ux-guidelines/media/0404-34_lightsourcescorrect.png "0404 34_LightSourcesCorrect")|![Sorgenti di luce non corretti per le icone](../../extensibility/ux-guidelines/media/0404-35_lightsourcesincorrect.png "0404 35_LightSourcesIncorrect")|  
  
 Utilizzare strutture solo per migliorare la leggibilità o per comunicare meglio la metafora. Il saldo (chiaro-scuro) positivo a negativo deve essere 50/50.  
  
|||  
|-|-|  
|**Utilizzo corretto delle strutture**|**Utilizzo non corretto di strutture**|  
|![Correggere i contorni](../../extensibility/ux-guidelines/media/0404-36_outlinescorrect.png "0404 36_OutlinesCorrect")|![Strutture non corrette](../../extensibility/ux-guidelines/media/0404-37_outlinesincorrect.png "0404 37_OutlinesIncorrect")|  
  
#### <a name="icon-types"></a>Tipi di icona  
 **Barra dei comandi e shell** icone sono costituiti da non più di tre dei seguenti elementi: una base, un modificatore, un'azione o uno stato.  
  
 ![Esempi di comando della barra delle icone e shell](../../extensibility/ux-guidelines/media/0404-38_shellicons.png "0404 38_ShellIcons")<br />Esempi di shell e barra delle icone dei comandi
  
 **Barra di comando degli strumenti finestra** icone sono costituiti da non più di tre dei seguenti elementi: una base, un modificatore, un'azione o uno stato.  
  
 ![Esempi di finestra dello strumento di comando della barra delle icone](../../extensibility/ux-guidelines/media/0404-39_toolwindowcommandbaricons.png "0404 39_ToolWindowCommandBarIcons")<br />Esempi di icone della barra di comando finestra dello strumento
  
 **Disambiguatore visualizzazione struttura ad albero** icone sono costituiti da non più di tre dei seguenti elementi: una base, un modificatore, un'azione o uno stato.  
  
 ![Esempi di struttura ad albero visualizzare icone del disambiguatore](../../extensibility/ux-guidelines/media/0404-40_treeviewicons.png "0404 40_TreeViewIcons")<br />Esempi di struttura ad albero visualizzare icone del disambiguatore
  
 **Tassonomia basati sullo stato valore** icone esistono nei seguenti stati: attivo, disabilitato attivo e inattivo disabilitato.  
  
 ![Esempi di icone di tassonomia basati sullo stato valore](../../extensibility/ux-guidelines/media/0404-41_statebasedtaxonomy.png "0404 41_StateBasedTaxonomy")<br />Esempi di icone di tassonomia basati sullo stato di valore
  
 **IntelliSense** icone sono costituiti da non più di tre dei seguenti elementi: una base, il uno modificatore e uno stato.  
  
 ![Esempi di icone per IntelliSense](../../extensibility/ux-guidelines/media/0404-42_intellisenseicons.png "0404 42_IntelliSenseIcons")<br />Esempi di icone per IntelliSense
  
 **Progetto di piccole dimensioni (16 x 16)** icone devono avere non più di due elementi: una base e un modificatore.  
  
 ![Icone di progetto di esempi di piccoli (16 x 16)](../../extensibility/ux-guidelines/media/0404-43_16x16project1.png "0404 43_16x16Project1") ![2 icona di 16x16 progetto &#40; &#41;] (../../extensibility/ux-guidelines/media/0404-44_16x16project2.png "0404 44_16x16Project2") ![3 icona di 16x16 progetto &#40; &#41;] (../../extensibility/ux-guidelines/media/0404-45_16x16project3.png "0404 45_16x16Project3")<br />Esempi di icone piccole di progetto (16 x 16)
  
 **Progetto di grandi dimensioni (32x32)** icone sono costituiti da non più di quattro elementi seguenti: una base, i modificatori di uno o due e un linguaggio di sovrapposizione.  
  
 ![Icone di progetto di esempi di grande (32x32)](../../extensibility/ux-guidelines/media/0404-46_32x32project.png "0404 46_32x32Project")<br />Esempi di grande (32x32) di icone di progetto
  
### <a name="production-details"></a>Dettagli di produzione  
 Tutti i nuovi elementi dell'interfaccia utente devono essere creati usando Windows Presentation Foundation (WPF) e tutte le icone di nuovo per WPF devono essere in formato PNG a 32 bit. Il file PNG 24 bit è un formato legacy che non supportano la trasparenza e pertanto non è consigliato per le icone.  
  
 Salvare la risoluzione di 96 DPI.  
  
#### <a name="file-types"></a>Tipi di file  
  
-   **PNG a 32 bit:** nel formato preferito per le icone. Formato del file la compressione dei dati senza perdita di dati che può archiviare un'immagine raster singola (pixel). file PNG a 32 bit supportano la trasparenza canale alfa, la correzione gamma e interlacciamento.  
  
-   **32 bit BMP:** per i controlli non WPF. Noto anche come XP o colore elevata, BMP a 32 bit è un formato di immagine RGB/A, un'immagine del true-color con la trasparenza di una canale alfa. Il canale alfa è un livello di trasparenza designato in Adobe Photoshop che viene quindi salvato all'interno di bitmap come un aggiuntiva (quarto) canale di colore. Sfondo nero viene aggiunto durante la produzione di disegno a tutti i file BMP 32 bit per fornire un'indicazione visiva rapida sull'intensità del colore. Lo sfondo bianco rappresenta l'area da mascherare nell'interfaccia utente.  
  
-   **32 bit ICO:** per le icone di progetto e aggiungere elemento. Tutti i file ICO sono true colori a 32 bit con trasparenza canale alfa (RGB/A). Poiché il file ICO possono archiviare più dimensioni e intensità di colore, le icone di Vista sono spesso in formato ICO contenente 16 x 16, 32 x 32, 48 x 48 e dimensioni delle immagini di 256 x 256. Per visualizzare correttamente in Windows Explorer, il file ICO devono essere salvato a discesa per intensità di colore a 24 bit e a 8 bit per ogni dimensione dell'immagine.  
  
-   **XAML:** per aree di progettazione e strumenti decorativi di Windows. Icone XAML sono file di immagine basata su vettore che supportano la scala, rotazione, archiviazione e la trasparenza. Non sono comuni in Visual Studio oggi, ma sono sempre più di frequente a causa delle loro flessibilità.  
  
-   **SVG**  
  
-   **24 bit BMP:** per la barra dei comandi di Visual Studio. Un formato di immagine true colore RGB, BMP 24 bit è una convenzione di icona che crea un livello di trasparenza come una chiave di colore per un livello di trasparenza di ritaglio in uscita tramite magenta (R = 255, G = 0, B = 255). In un'immagine BMP 24 bit, tutte le superfici magenta vengono visualizzate utilizzando il colore di sfondo.  
  
-   **24 bit GIF:** per la barra dei comandi di Visual Studio. Un formato di immagine RGB true-color che supporta la trasparenza. GIF (file) vengono spesso utilizzati nel disegno di procedura guidata e le animazioni GIF.  
  
### <a name="icon-construction"></a>Costruzione di icona  
 Le dimensioni dell'icona più piccolo in Visual Studio sono 16 x 16. Il più grande in comune utilizzo è 32 x 32. Tenere presente, non per riempire l'intera cornice 16 x 16, 24 x 24 o 32 x 32 quando si progetta un'icona. Costruzione di icona leggibili, uniform è essenziale per il riconoscimento di utente. Rispettare i seguenti punti durante la creazione di icone.  
  
-   Icone devono essere chiaro comprensibile e coerente.  
  
-   È preferibile utilizzare gli elementi di notifica di stato sotto forma di icone singole e non sovrapposti l'elemento di base di un'icona. In determinati contesti, l'interfaccia utente potrebbe richiedere l'elemento di stato per poter essere associati con un elemento di base.  
  
-   Icone di progetto sono in genere i file con estensione ico che contengono diverse dimensioni. Aggiornare solo le icone 16x16, 24x24 e 32x32. La maggior parte delle icone di 16 x 16 e 24 x 24 conterrà gli stessi elementi. Le icone di 32 x 32 contengono ulteriori dettagli, incluso il tipo di linguaggio progetto quando applicabile.  
  
-   Per le icone di 32 x 32, elementi di base in genere hanno uno spessore di linea 2 pixel. Per gli elementi di dettaglio, è possibile utilizzare uno spessore di linea 1 o 2 pixel. Utilizzare giudizio per stabilire che è più adatto.  
  
-   Disporre di almeno un 1 pixel la spaziatura tra gli elementi per 16 x 16 e icone 24 x 24. Per le icone di 32 x 32, utilizzare 2 pixel spaziatura tra gli elementi e tra il modificatore e un elemento di base.  
  
 ![Elemento spaziatura per dimensioni di icone 16x16, 24x24 e 32x32](../../extensibility/ux-guidelines/media/0404-47_elementspacing.png "0404 47_ElementSpacing")<br />Dimensioni di spaziatura elementi per icone 16x16, 24x24 e 32x32
  
#### <a name="color-and-accessibility"></a>Colore e l'accessibilità  
 Linee guida di conformità di Visual Studio richiedono che tutte le icone nel prodotto soddisfa i requisiti di accessibilità per colore e contrasto. Questo risultato viene ottenuto tramite inversione icona e quando si progetta, è necessario essere consapevoli che verrà invertiti a livello di codice all'interno del prodotto.  
  
 Per ulteriori informazioni sull'utilizzo dei colori, icone di Visual Studio, vedere [utilizzando colore nelle immagini](../../extensibility/ux-guidelines/images-and-icons-for-visual-studio.md#BKMK_UsingColorInImages).  
  
##  <a name="BKMK_UsingColorInImages"></a>Utilizzo di colore in immagini  
  
### <a name="overview"></a>Panoramica  
 Icone in Visual Studio sono principalmente monocromatica. Colore è riservato per trasmettere informazioni specifiche e mai per effetto. Colore verrà utilizzato:  
  
-   per indicare un'azione  
  
-   per avvisare l'utente a una notifica sullo stato  
  
-   Per definire l'associazione del linguaggio  
  
-   per distinguere gli elementi all'interno di IntelliSense  
  
### <a name="accessibility"></a>Accessibilità  
 Linee guida di conformità di Visual Studio richiedono che tutte le icone archiviati nel passaggio di prodotto i requisiti di accessibilità per colore e contrasto. Colori della tavolozza del linguaggio visual sono stati testati e soddisfano tali requisiti.  
  
#### <a name="color-inversion-for-dark-themes"></a>Inversione di colore per i temi scuri  
 Per visualizzare le icone con il contrasto corretto nel tema scuro di Visual Studio, un'inversione viene applicata a livello di codice. I colori in questa guida sono state scelte in parte in modo che essi Inverti correttamente. Limitare l'uso del colore per la tavolozza o si otterranno risultati imprevisti quando viene applicato l'inversione.  
  
 ![Esempi di icone che hanno i colori invertiti](../../extensibility/ux-guidelines/media/0405-01_darkthemeinversion.png "0405 01_DarkThemeInversion")<br />Esempi di icone che hanno i colori invertiti
  
### <a name="base-palette"></a>Tavolozza di base  
 Tutte le icone standard contengono tre colori di base. Icone non contengono alcun sfumature o ombreggiature, con uno o due eccezioni per le icone degli strumenti 3D.  
  
|Utilizzo|nome|Valore (tema chiaro)|Campione|Esempio|  
|-----------|----------|---------------------------|------------|-------------|  
|Sfondo/scuro|BG VS|424242 / 66,66,66|![Campione 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|![Esempio di tavolozza di base](../../extensibility/ux-guidelines/media/0405-02_basepaletteexample.png "0405 02_BasePaletteExample")|  
|In primo piano/leggero|FG VS|F0EFF1 / 240,239,241|![Campione F0EFF1](../../extensibility/ux-guidelines/media/0405_f0eff1.png "0405_F0EFF1")||  
|Struttura|VS Out|F6F6F6 / 246,246,246|![Campione F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")||  
  
 Oltre ai colori di base, ogni icona può contenere un aggiuntivo colore dalla tavolozza estesa.  
  
### <a name="extended-palette"></a>Tavolozza estesa  
  
#### <a name="action-modifiers"></a>Modificatori di azione  
 I quattro colori riportato di seguito indicano i tipi di azioni richieste dal modificatori di azione:  
  
|Utilizzo|nome|Valore (tutti i temi)|Campione|  
|-----------|----------|--------------------------|------------|  
|Positivo|VS azione verde|388A34 / 56,138,52|![Campione 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|Negativo|VS azione rosso|A1260D / 161,38,13|![Campione A1260D](../../extensibility/ux-guidelines/media/0405_a1260d.png "0405_A1260D")|  
|Lingua di sistema|VS azione blu|C 00539 / 0,83,156|![Campione 00539c](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|Creare/nuovo|VS azione arancione|C27D1A / 194,156,26|![Campione C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
  
##### <a name="examples"></a>Esempi  
 Verde viene utilizzato per i modificatori di azione positiva come "Add", "Esegui", "Play" e "Convalida".  
  
|||||  
|-|-|-|-|  
|![Icona dell'esecuzione di](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405 03_ActionModifierRun")<br />Esegui|![Icona Esegui query](../../extensibility/ux-guidelines/media/0405-04_executequery.png "0405 04_ExecuteQuery")<br />Esecuzione di Query|![Icona Riproduci tutti i passaggi](../../extensibility/ux-guidelines/media/0405-05_playallsteps.png "0405 05_PlayAllSteps")<br />Tutti i passaggi di riproduzione|![Icona Aggiungi controllo](../../extensibility/ux-guidelines/media/0405-06_addcontrol.png "0405 06_AddControl")<br />Aggiungi controllo|  
  
 Rosso viene usato per i modificatori di azione negativo come "Delete", "Stop", "Annulla" e "Chiudi".  
  
|||||  
|-|-|-|-|  
|![Icona Elimina relazioni](../../extensibility/ux-guidelines/media/0405-07_deleterelationship.png "0405 07_DeleteRelationship")<br />Elimina relazione|![Icona Elimina colonna](../../extensibility/ux-guidelines/media/0405-08_deletecolumn.png "0405 08_DeleteColumn")<br />Elimina colonna|![Icona query Arresta](../../extensibility/ux-guidelines/media/0405-09_stopquery.png "0405 09_StopQuery")<br />Interrompi Query|![Icona connessione offline](../../extensibility/ux-guidelines/media/0405-10_connectionoffline.png "0405 10_ConnectionOffline")<br />Connessione non in linea|  
  
 Blu viene applicata all'azione neutro modificatori in genere rappresentate come frecce, ad esempio "Aperta", "Avanti", "Precedente", "Importa" e "Esportazione".  
  
|||||  
|-|-|-|-|  
|![Passare a icona campo](../../extensibility/ux-guidelines/media/0405-11_gotofield.png "0405 11_GoToField")<br />Passare al campo|![In blocco di controllo &#45; icona](../../extensibility/ux-guidelines/media/0405-12_batchedcheckin.png "0405 12_BatchedCheckIn")<br />Archiviazione in batch|![Icona editor di indirizzo](../../extensibility/ux-guidelines/media/0405-13_addresseditor.png "0405 13_AddressEditor")<br />Editor di indirizzo|![Icona editor di associazione](../../extensibility/ux-guidelines/media/0405-14_associationeditor.png "0405 14_AssociationEditor")<br />Editor di associazione|  
  
 Oro scuro viene principalmente utilizzato per il modificatore "Nuovo".  
  
|||||  
|-|-|-|-|  
|![Icona Nuovo progetto](../../extensibility/ux-guidelines/media/0405-15_newproject.png "0405 15_NewProject")<br />Nuovo progetto|![Icona Crea nuovo grafico](../../extensibility/ux-guidelines/media/0405-16_createnewgraph.png "0405 16_CreateNewGraph")<br />Crea un nuovo grafico|![Icona nuovo unit test](../../extensibility/ux-guidelines/media/0405-17_newunittest.png "0405 17_NewUnitTest")<br />Nuovo Unit Test|![Icona Nuovo elemento di elenco](../../extensibility/ux-guidelines/media/0405-18_newlistitem.png "0405 18_NewListItem")<br />Nuovo elemento elenco|  
  
#### <a name="special-cases"></a>Casi speciali  
 In casi particolari, un modificatore di colorata azione può essere utilizzato in modo indipendente come icona autonomo. Colore utilizzato per l'icona riflette le azioni che è associata l'icona. Questo utilizzo è limitato a un piccolo subset delle icone, tra cui:  
  
||||||  
|-|-|-|-|-|  
|![Icona dell'esecuzione di](../../extensibility/ux-guidelines/media/0405-03_actionmodifierrun.png "0405 03_ActionModifierRun")<br />Esegui|![Icona Arresta](../../extensibility/ux-guidelines/media/0405-19_stop.png "0405 19_Stop")<br />Arresta|![Icona Elimina](../../extensibility/ux-guidelines/media/0405-20_delete.png "0405 20_Delete")<br />Eliminare|![Icona Salva](../../extensibility/ux-guidelines/media/0405-21_save.png "0405 21_Save")<br />Salva|![Icona Esplora Indietro](../../extensibility/ux-guidelines/media/0405-22_navigateback.png "0405 22_NavigateBack")<br />Esplora indietro|  
  
### <a name="code-hierarchy-palette"></a>Tavolozza gerarchia codice  
  
#### <a name="folder"></a>Cartella  
  
|Utilizzo|nome|Valore (tutti i temi)|Campione|Esempio|  
|-----------|----------|--------------------------|------------|-------------|  
|Cartelle|Cartella|DCB67A / 220,182,122|![Campione DCB67A](../../extensibility/ux-guidelines/media/0405_dcb67a.png "0405_DCB67A")|![Icona cartella](../../extensibility/ux-guidelines/media/0405-23_foldercolor.png "0405 23_FolderColor")|  
  
#### <a name="visual-studio-languages"></a>Linguaggi di Visual Studio  
 Ciascuno dei linguaggi o piattaforme disponibili in Visual Studio comuni associate a un colore. Questi colori vengono utilizzati l'icona di base, o sui modificatori di linguaggio che vengono visualizzati nell'angolo superiore destro delle icone composte.  
  
|Utilizzo|nome|Valore (tutti i temi)|Campione|  
|-----------|----------|--------------------------|------------|  
|ASP, HTML, WPF|ASP HTML WPF blu|7 0095D / 0,149,215|![Campione 0095d7](../../extensibility/ux-guidelines/media/0405_0096d7.png "0405_0096D7")|  
|C++|CPP viola|9B4F96 / 155,79,150|![Campione 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|C#|CS verde (VS azione verde)|388A34 / 56,138,52|![Campione 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|CSS|Rosso CSS|BD1E2D / 189,30,45|![Campione BD1E2D](../../extensibility/ux-guidelines/media/0405_bd1e2d.png "0405_BD1E2D")|  
|F#|ADFS viola|672878 / 103,40,120|![Campione 672878](../../extensibility/ux-guidelines/media/0405_672878.png "0405_672878")|  
|JavaScript|JS arancione|F16421 / 241,100,33|![Campione F16421](../../extensibility/ux-guidelines/media/0405_f16421.png "0405_F16421")|  
|VB|VB blu (VS azione blu)|C 00539 / 0,83,156|![Campione 00539c](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|TypeScript|Servizi terminal arancione|E04C06 / 224,76,6|![Campione E04C06](../../extensibility/ux-guidelines/media/0405_e04c06.png "0405_E04C06")|  
|Python|Verde rispetto all'anno precedente|879636 / 135,150,54|![Campione 879636](../../extensibility/ux-guidelines/media/0405_879636.png "0405_879636")|  
  
##### <a name="examples-of-icons-with-language-modifiers"></a>Esempi di icone con i modificatori di linguaggio  
  
|||||||  
|-|-|-|-|-|-|  
|![Icona di Visual Basic](../../extensibility/ux-guidelines/media/0405-25_vb.png "0405 25_VB")<br />VB|![C &#35; icona](../../extensibility/ux-guidelines/media/0405-26_csharp.png "0405 26_CSharp")<br />C#|![C &#43; &#43; icona](../../extensibility/ux-guidelines/media/0405-27_cplusplus.png "0405 27_CPlusPlus")<br />C++|![F &#35; icona](../../extensibility/ux-guidelines/media/0405-28_fsharp.png "0405 28_FSharp")<br />F#|![Icona di JavaScript](../../extensibility/ux-guidelines/media/0405-29_javascript.png "0405 29_JavaScript")<br />JavaScript|![Icona di Python](../../extensibility/ux-guidelines/media/0405-30_python.png "0405 30_Python")<br />Python|  
|![Icona HTML](../../extensibility/ux-guidelines/media/0405-31_html.png "0405 31_HTML")<br />HTML|![Icona di WPF](../../extensibility/ux-guidelines/media/0405-32_wpf.png "0405 32_WPF")<br />WPF|![Icona di ASP](../../extensibility/ux-guidelines/media/0405-33_asp.png "0405 33_ASP")<br />ASP|![Icona di CSS](../../extensibility/ux-guidelines/media/0405-34_css.png "0405 34_CSS")<br />CSS|![Icona di typeScript](../../extensibility/ux-guidelines/media/0405-35_typescript.png "0405 35_TypeScript")<br />TypeScript||  
  
#### <a name="intellisense"></a>IntelliSense  
 Icone per IntelliSense utilizzano una tavolozza di colori esclusivo. Questi colori vengono utilizzati per consentire agli utenti di distinguere rapidamente tra i diversi elementi nell'elenco popup di IntelliSense.  
  
|Utilizzo|nome|Valore (tutti i temi)|Campione|  
|-----------|----------|--------------------------|------------|  
|Classe di evento,|VS azione arancione|C27D1A / 194,125,26|![Campione C27D1A](../../extensibility/ux-guidelines/media/0405_c27d1a.png "0405_C27D1A")|  
|Metodo di estensione, metodo, modulo, delegato|VS azione viola|652 LA 90 D / 101,45,144|![Campione 652d90](../../extensibility/ux-guidelines/media/0405_652d90.png "0405_652D90")|  
|Campo, elemento Enum, Macro, struttura, tipo di valore di unione, operatore, interfaccia|VS azione blu|C 00539 / 0,83,156|![Campione 00539c](../../extensibility/ux-guidelines/media/0405_00539c.png "0405_00539C")|  
|Object|VS azione verde|388A34 / 56,138,52|![Campione 388A34](../../extensibility/ux-guidelines/media/0405_388a34.png "0405_388A34")|  
|Costante, eccezione, elemento Enum, mappa, l'elemento della mappa, Namespace, modello, definizione di tipo|Sfondo (VS BG)|424242 / 66,66,66|![Campione 424242](../../extensibility/ux-guidelines/media/0405_424242.png "0405_424242")|  
  
##### <a name="examples-of-intellisense-icons"></a>Esempi di icone per IntelliSense  
  
||||||  
|-|-|-|-|-|  
|![Icona della classe IntelliSense](../../extensibility/ux-guidelines/media/0405-36_intellisenseclass.png "0405 36_IntelliSenseClass")<br />Classe|![Icona dell'evento privato IntelliSense](../../extensibility/ux-guidelines/media/0405-37_intellisenseprivateevent.png "0405 37_IntelliSensePrivateEvent")<br />Evento privato|![Icona del delegato IntelliSense](../../extensibility/ux-guidelines/media/0405-38_intellisensedelegate.png "0405 38_IntelliSenseDelegate")<br />delegato|![Icona descrittiva del metodo IntelliSense](../../extensibility/ux-guidelines/media/0405-39_intellisensemethodfriend.png "0405 39_IntelliSenseMethodFriend")<br />Friend (metodo)|![Icona campo](../../extensibility/ux-guidelines/media/0405-40_field.png "0405 40_Field")<br />Campo|  
|![Icona dell'elemento enum di protetto IntelliSense](../../extensibility/ux-guidelines/media/0405-41_intellisenseprotectedenumitem.png "0405 41_IntelliSenseProtectedEnumItem")<br />Elemento Enum protetto|![Icona dell'oggetto IntelliSense](../../extensibility/ux-guidelines/media/0405-42_intellisenseobject.png "0405 42_IntelliSenseObject")<br />Object|![Icona del modello IntelliSense](../../extensibility/ux-guidelines/media/0405-43_intellisensetemplate.png "0405 43_IntelliSenseTemplate")<br />Modello|![Icona di collegamento eccezione IntelliSense](../../extensibility/ux-guidelines/media/0405-44_intellisenseexceptionshortcut.png "0405 44_IntelliSenseExceptionShortcut")<br />Scelta rapida di eccezione||  
  
### <a name="notifications"></a>Notifiche  
 Le notifiche in Visual Studio vengono usate per indicare lo stato. La tavolozza notifica utilizza quattro colori seguenti, nonché le opzioni di riempimento di primo piano bianchi o neri, per definire le notifiche con i seguenti livelli di stato.  
  
|Utilizzo|nome|Valore (tutti i temi)|Campione|  
|-----------|----------|--------------------------|------------|  
|Stato: neutra|Notifica blu (VS blu)|1BA1E2 / 27,161,226|![Campione 1BA1E2](../../extensibility/ux-guidelines/media/0405_1ba1e2.png "0405_1BA1E2")|  
|Stato: positivo|Notifica verde (VS verde)|339933 / 51,153,51|![Campione 339933](../../extensibility/ux-guidelines/media/0405_339933.png "0405_339933")|  
|Stato: negativo|Notifica rosso (VS rosso)|E51400 / 229,20,0|![Campione E51400](../../extensibility/ux-guidelines/media/0405_e51400.png "0405_E51400")|  
|Stato: avviso|Notifica giallo (VS arancione)|FFCC00 / 255,204,0|![Campione FFCC00](../../extensibility/ux-guidelines/media/0405_ffcc00.png "0405_FFCC00")|  
|Riempimento di primo piano|Notifica nero (nero)|000000 / 0,0,0|![Campione &#35; 000000](../../extensibility/ux-guidelines/media/0405_000000.png "0405_000000")|  
|Riempimento di primo piano|Notifica vuoto (bianco)|FFFFFF / 255,255,255|![Campione FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
  
#### <a name="examples-of-notification-icons"></a>Esempi di icone di notifica  
  
|||||  
|-|-|-|-|  
|![Icona di avviso](../../extensibility/ux-guidelines/media/0405-45_alert.png "0405 45_Alert")<br />Avviso|![Icona di avviso](../../extensibility/ux-guidelines/media/0405-48_warning.png "0405 48_Warning")<br />Avviso|![Icona completata](../../extensibility/ux-guidelines/media/0405-46_complete.png "0405 46_Complete")<br />Completa|![Icona Arresta](../../extensibility/ux-guidelines/media/0405-47_stop.png "0405 47_Stop")<br />Arresta|  
  
### <a name="visual-studio-online"></a>Visual Studio Online  
 In generale, Visual Studio Online include funzionalità ospitate in un browser. Varia il colore in ambienti diversi, ma lo stile rimane invariato.  
  
|Gruppo|Utilizzo|nome|Valore (tutti i temi)|Campione|  
|-----------|-----------|----------|--------------------------|------------|  
|TFS|Sfondo|BG TFSO|656565/ 101, 101, 101|![Campione 656565](../../extensibility/ux-guidelines/media/0405_656565.png "0405_656565")|  
|TFS|Struttura|TFSO OUT|FFFFFF / 255, 255, 255|![Campione FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Napa|Sfondo|Vuoto|FFFFFF / 255, 255, 255|![Campione FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|Monaco|Sfondo|Vuoto|FFFFFF / 255, 255, 255|![Campione FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|Sfondo|Vuoto|FFFFFF / 255, 255, 255|![Campione FFFFFF](../../extensibility/ux-guidelines/media/0405_ffffff.png "0405_FFFFFF")|  
|F12|Normale|Grey_Primary F12|555555 / 85, 85, 85|![Campione 555555](../../extensibility/ux-guidelines/media/0405_555555.png "0405_555555")|  
|F12|Passaggio del mouse|Blue_Hover F12|2279BF / 34,121,191|![Campione 2279BF](../../extensibility/ux-guidelines/media/0405_2279bf.png "0405_2279BF")|  
|F12|Disabilitato|LtGrey_Disabled F12|ABABAC / 171,171,172|![Campione ABABAC](../../extensibility/ux-guidelines/media/0405_ababac.png "0405_ABABAC")|  
|F12|Sfondo al passaggio del mouse|Passare il mouse bg|D9EBF7 / 217,235,247|![Campione D9EBF7](../../extensibility/ux-guidelines/media/0405_d9ebf7.png "0405_D9EBF7")|  
|F12|Sfondo premuto|Bg premuto|B2D7F0 / 178,215,240|![Campione B2D7F0](../../extensibility/ux-guidelines/media/0405_b2d7f0.png "0405_B2D7F0")|  
|F12|Struttura|VS OUT|F6F6F6 / 246,246,246|![Campione F6F6F6](../../extensibility/ux-guidelines/media/0405_f6f6f6.png "0405_F6F6F6")|  
|F12|Informazioni|Informazioni|00BCF2 / 0,188,242|![Campione 00BCF2](../../extensibility/ux-guidelines/media/0405_00bcf2.png "0405_00BCF2")|  
|F12|Avviso|Avviso|F28300 / 242,131,0|![Campione F28300](../../extensibility/ux-guidelines/media/0405_f28300.png "0405_F28300")|  
|F12|Errore / negativo|Error_Negative|E81123 / 232,17,35|![Campione E81123](../../extensibility/ux-guidelines/media/0405_e81123.png "0405_E81123")|  
|F12|Avviare / positivo|Start_Positive|009E49 / 0,158,73|![Campione 009E49](../../extensibility/ux-guidelines/media/0405_009e49.png "0405_009E49")|  
|F12|Tipo di interruzione|Tipo di interruzione|9B4F96 / 155,79,150|![Campione 9B4F96](../../extensibility/ux-guidelines/media/0405_9b4f96.png "0405_9B4F96")|  
|F12|Contrassegno di eventi|Contrassegno di eventi|A51F00 / 165,31,0|![Campione A51F00](../../extensibility/ux-guidelines/media/0405_a51f00.png "0405_A51F00")|  
|F12|Contrassegno utente|Contrassegno utente|F16220 / 241,98,32|![Campione F16220](../../extensibility/ux-guidelines/media/0405_f16220.png "0405_F16220")|  
  
#### <a name="examples-of-visual-studio-online-icons"></a>Esempi di icone di Visual Studio Online  
  
|TFS Online||||  
|----------------|-|-|-|  
|![Icona team di TFS Online](../../extensibility/ux-guidelines/media/0405-49_tfsonlineteam.png "0405 49_TFSOnlineTeam")<br />Team online|![Icona di informazioni TFS](../../extensibility/ux-guidelines/media/0405-50_tfsinformation.png "0405 50_TFSInformation")<br />Informazioni|![Icona cronologia TFS](../../extensibility/ux-guidelines/media/0405-51_tfshistory.png "0405 51_TFSHistory")<br />Cronologia|![Icona del branch TFS](../../extensibility/ux-guidelines/media/0405-52_tfsbranch.png "0405 52_TFSBranch")<br />Branch|  
  
|Napa||||  
|----------|-|-|-|  
|![Icona del contenuto Napa](../../extensibility/ux-guidelines/media/0405-53_napacontent.png "0405 53_NapaContent")<br />Content|![Icona posta elettronica di office Napa](../../extensibility/ux-guidelines/media/0405-54_napaofficemail.png "0405 54_NapaOfficeMail")<br />Posta elettronica di Office|![Icona di SharePoint Napa](../../extensibility/ux-guidelines/media/0405-55_napasharepoint.png "0405 55_NapaSharePoint")<br />SharePoint|![Icona del riquadro attività Napa](../../extensibility/ux-guidelines/media/0405-56_napataskpane.png "0405 56_NapaTaskPane")<br />Riquadro attività|  
  
|Monaco||||  
|------------|-|-|-|  
|![Icona dei file Monaco](../../extensibility/ux-guidelines/media/0405-57_monacofiles.png "0405 57_MonacoFiles")<br />File|![Icona Git Monaco](../../extensibility/ux-guidelines/media/0405-58_monacogit.png "0405 58_MonacoGit")<br />Git|![Icona di ricerca Monaco](../../extensibility/ux-guidelines/media/0405-59_monacosearch.png "0405 59_MonacoSearch")<br />Cerca|![Icona di testo Monaco](../../extensibility/ux-guidelines/media/0405-60_monacotext.png "0405 60_MonacoText")<br />Testo|  
  
|F12|||  
|---------|-|-|  
|![Icona codice pretty F12](../../extensibility/ux-guidelines/media/0405-61_f12prettycode.png "0405 61_F12PrettyCode")<br />Codice Pretty|![Icona di avviso F12](../../extensibility/ux-guidelines/media/0405-62_f12warning.png "0405 62_F12Warning")<br />Avviso|![Icona di emulazione F12](../../extensibility/ux-guidelines/media/0405-63_f12emulate.png "0405 63_F12Emulate")<br />Emulare|