---
title: Frame di grafica Analysis | Documenti Microsoft
ms.custom: ''
ms.date: 02/09/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.frameanalysis
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9fe34c421d06fea1e4eefc064d344727382ca1d8
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="graphics-frame-analysis"></a>Analisi dei frame di grafica
Usare l'analisi dei frame di grafica in Analizzatore grafica di Visual Studio per analizzare e ottimizzare le prestazioni di rendering del gioco o dell'app Direct3D.  

## <a name="frame-analysis"></a>Analisi dei frame  
 L'analisi dei frame usa le stesse informazioni acquisite in un file di registro elementi grafici per finalità diagnostiche, ma le usa per riepilogare invece le prestazioni del rendering. Le informazioni sulle prestazioni non sono registrate nel registro durante l'acquisizione. Queste informazioni sono invece generate in un secondo momento, durante l'analisi dei frame, tramite la misurazione della durata degli eventi e la raccolta di statistiche durante la riproduzione del frame. Questo approccio presenta numerosi vantaggi rispetto alla registrazione delle informazioni sulle prestazioni durante l'acquisizione:  
  
-   L'analisi dei frame può usare i risultati di più riproduzioni dello stesso frame, in modo da assicurare la validità statistica del riepilogo delle prestazioni.  
  
-   L'analisi dei frame può generare informazioni sulle prestazioni per configurazioni hardware e dispositivi diversi da quello in cui sono state acquisite le informazioni.  
  
-   Analisi dei frame può generare nuovi riepiloghi delle prestazioni da informazioni acquisite in precedenza, ad esempio, quando i driver GPU sono ottimizzati o esporre funzionalità di debug aggiuntive.  
  
 Oltre a questi vantaggi, è possibile usare l'analisi dei frame anche per modificare la modalità di esecuzione del rendering durante la riproduzione, in modo che sia possibile presentare informazioni sul possibile impatto delle modifiche sulle prestazioni di rendering di un'app. Queste informazioni permettono di scegliere tra potenziali strategie di ottimizzazione, senza doverle implementare tutte, e quindi di acquisire e confrontare tutti i risultati.  
  
 Anche se l'analisi dei frame è stata progettata principalmente per permettere di ottenere prestazioni di rendering migliori, può anche aiutare a ottenere una qualità visiva superiore per una destinazione di prestazioni specifica o a ridurre il consumo di energia della GPU.  
  
 Per una dimostrazione di ciò che è possibile eseguire l'analisi dei Frame per l'app, è possibile guardare il [Frame analisi grafica di Visual Studio](http://channel9.msdn.com/Shows/C9-GoingNative/GoingNative-25-Offline-Analysis-Graphics-Tool) video su Channel 9.  
  
## <a name="using-frame-analysis"></a>Uso dell'analisi dei frame  
 Prima di potere usare l'analisi dei frame è necessario acquisire informazioni sugli elementi grafici dall'app durante l'esecuzione, esattamente come si farebbe con gli altri strumenti di Analizzatore grafica. Nella finestra del documento (. vsglog) di log di grafica, quindi scegliere il **analisi dei Frame** scheda.  
  
 ![Selezionare la scheda analisi dei Frame](media/pix_frame_analysis_select_tab.png "pix_frame_analysis_select_tab")  
  
 Al termine dell'analisi saranno visualizzati i risultati. Nella parte superiore della scheda Analisi dei frame sono visualizzate la sequenza temporale e la tabella Riepilogo. Nella parte superiore sono disponibili le tabelle di dettaglio. Se durante la riproduzione sono stati generati errori o avvisi, il riepilogo corrispondente sarà disponibile sopra la sequenza temporale. Per ottenere altre informazioni su errori e avvisi, selezionare i collegamenti disponibili nel riepilogo.  
  
### <a name="interpreting-results"></a>Interpretazione dei risultati  
 L'interpretazione dei risultati di ogni variante permette di dedurre informazioni utili sulle prestazioni e sul comportamento di rendering dell'app. Per ulteriori informazioni sulle varianti di rendering, vedere [varianti](#Variants) più avanti in questo articolo.  
  
 Alcuni risultati indicano direttamente il modo in cui la variante influisce sulle prestazioni di rendering:  
  
-   Se la variante Filtraggio bilineare della trama ha mostrato miglioramenti nelle prestazioni, l'uso di questa variante nell'app permetterà di ottenere miglioramenti analoghi nelle prestazioni.  
  
-   Se la variante relativa al riquadro di visualizzazione 1x1 ha mostrato miglioramenti nelle prestazioni, la riduzione delle dimensioni delle destinazioni di rendering nell'app permetterà di migliorarne le prestazioni a livello di rendering.  
  
-   Se la variante Compressione di trama a blocchi ha mostrato miglioramenti nelle prestazioni, l'uso di questa variante nell'app permetterà di ottenere miglioramenti analoghi nelle prestazioni.  
  
-   Se le prestazioni della variante 2xMSAA sono quasi uguali a quelle della variante 0xMSAA, è possibile abilitare la variante 2xMSAA nell'app per migliorare la qualità di rendering senza influire negativamente sulle prestazioni.  
  
 Altri risultati potrebbero suggerire implicazioni più profonde e complesse per le prestazioni dell'app:  
  
-   Se la variante relativa al riquadro di visualizzazione 1x1 mostra miglioramenti notevoli nelle prestazioni, è possibile che l'app usi una quantità di velocità di riempimento superiore a quella disponibile. Se questa variante non mostra alcun miglioramento nelle prestazioni, è possibile che l'app stia elaborando una quantità eccessiva di vertici.  
  
-   Se la variante Formato di destinazione di rendering 16bpp mostra miglioramenti notevoli nelle prestazioni, è possibile che l'app stia usando una larghezza di banda di memoria eccessiva.  
  
-   Se la variante Dimensioni trama - Metà/Quarto mostra miglioramenti significativi delle prestazioni, è possibile che le trame occupino una quantità di memoria eccessiva, usino troppa larghezza di banda o usino in modo non efficace la cache delle trame. Se questa variante non mostra alcun cambiamento nelle prestazioni, è probabilmente possibile usare trame più grandi e più dettagliate senza impatti negativi sulle prestazioni.  
  
 Se sono disponibili contatori hardware, sarà possibile usarli per raccogliere informazioni molto dettagliate sulle possibili cause delle prestazioni di rendering negative dell'app. Tutte le periferiche a livello di funzionalità 9.2 e superiore supportano le query di occlusione di profondità (**pixel bloccati** contatore) e timestamp. È possibile che siano disponibili altri contatori hardware, a seconda se il fornitore di GPU ha implementato o meno i contatori hardware e li ha esposti nel proprio driver. Questi contatori possono essere usati per confermare la causa precisa dei risultati mostrati nella tabella Riepilogo. È ad esempio possibile determinare se il disegno eccessivo costituisce un problema esaminando la percentuale di pixel bloccati dal test di profondità.  
  
### <a name="timeline-and-summary-table"></a>Sequenza temporale e tabella Riepilogo  
 Per impostazione predefinita, la sequenza temporale e la tabella Riepilogo sono visualizzate e le altre sezioni sono compresse.  
  
#### <a name="timeline"></a>Sequenza temporale  
 La sequenza temporale mostra una panoramica dei tempi reciproci di chiamata di disegno. Poiché le barre più larghe corrispondono a tempi di disegno più lunghi, è possibile usarla per individuare rapidamente le chiamate di disegno più dispendiose nel frame. Se il frame acquisito include un numero elevato di chiamate di disegno, più chiamate di disegno saranno combinate in un'unica barra, la cui lunghezza corrisponde alla somma delle chiamate di disegno specifiche.  
  
 ![La sequenza temporale Mostra disegno&#45;chiamare i costi. ] (media/pix_frame_analysis_timeline.png "pix_frame_analysis_timeline")  
  
 È possibile posizionare il puntatore su una barra per verificare l'evento di chiamata di disegno a cui corrisponde la barra. Se si seleziona la barra, l'elenco di eventi sarà sincronizzato in base all'evento specifico.  
  
#### <a name="table"></a>Tabella  
 La tabella numerica sotto la sequenza temporale mostra le prestazioni relative di ogni variante di rendering per ogni chiamata di disegno rispetto al rendering predefinito dell'app. Ogni colonna mostra una diversa variante di rendering e ogni riga rappresenta una chiamata di disegno diversa, identificata nella colonna più a sinistra. È possibile seguire i collegamenti relativi a un evento per visualizzarlo nella finestra Elenco eventi grafici.  
  
 ![La tabella di riepilogo Mostra diverse varianti. ] (media/pix_frame_analysis_summary.png "pix_frame_analysis_summary")  
  
 La seconda colonna da sinistra nella tabella Riepilogo mostra il tempo di rendering iniziale, ovvero il tempo necessario per il completamento della chiamata di disegno da parte del rendering predefinito dell'app. Le colonne rimanenti mostrano le prestazioni relative di ogni variante di rendering sotto forma di percentuale del valore di base, in modo da permettere di individuare con facilità eventuali miglioramenti nelle prestazioni. Le percentuali superiori al 100% hanno richiesto un tempo superiore rispetto al valore di base, ovvero indicano un calo nelle prestazioni, mentre le percentuali inferiori al 100% hanno richiesto meno tempo, ovvero indicano un miglioramento nelle prestazioni.  
  
 I valori della durata assoluta del valore di base e la durata relativa delle varianti di rendering corrispondono in effetti alla media di più esecuzioni, 5 per impostazione predefinita. Il calcolo della media permette di assicurare che i dati relativi alla durata siano affidabili e coerenti. È possibile posizionare il puntatore su ogni cella della tabella per esaminare i valori di durata minima, massima, media e mediana osservati durante la generazione di risultati per la chiamata di disegno e la variante di rendering specifiche. È visualizzata anche la durata di base.  
  
#### <a name="hot-draw-calls"></a>Chiamate di disegno "problematiche"  
 Per evidenziare le chiamate di disegno che consumano una proporzione maggiore del tempo di rendering complessivo o che potrebbero essere insolitamente lente per motivi evitabili, la riga che include queste chiamate di disegno "problematiche" avrà ombreggiatura di colore rosso quando la rispettiva durata iniziale supera di più di una deviazione standard la durata media iniziale di tutte le chiamate di disegno nel frame.  
  
 ![Questa chiamata a DrawIndexed contiene varianti di frequente. ] (media/pix_frame_analysis_hot_calls.png "pix_frame_analysis_hot_calls")  
  
#### <a name="statistical-significance"></a>Rilevanza statistica  
 Per evidenziare le variazioni di rendering con rilevanza maggiore, l'analisi dei frame determina la rilevanza statistica di ogni variante di rendering e mostra in grassetto le varianti più significative. Le varianti che migliorano le prestazioni sono mostrate in verde, mentre quelle che le riducono sono mostrate in rosso. I risultati non significativi a livello statistico sono mostrati in testo normale.  
  
 ![Rilevanza statistica della variante chiamata di disegno](media/pix_frame_analysis_summary_stats.png "pix_frame_analysis_summary_stats")  
  
 Per determinare la rilevanza statistica, l'analisi dei Frame Usa il [test t di Student](http://www.wikipedia.org/wiki/Student%27s_t-test).  
  
### <a name="details-table"></a>Tabella Dettagli  
 Sotto la tabella Riepilogo è disponibile la tabella Dettagli, compressa per impostazione predefinita. Il contenuto della tabella Dettagli dipende dalla piattaforma hardware della macchina di riproduzione. Per informazioni sulle piattaforme hardware supportate, vedere [supporto Hardware](#HardwareSupport).  
  
#### <a name="platforms-that-do-not-support-hardware-counters"></a>Piattaforme che non supportano i contatori hardware  
 La maggior parte delle piattaforme non offre il supporto completo per i contatori GPU hardware, incluse tutte le GPU attualmente fornite da Intel, AMD e nVidia. Se non sono presenti contatori hardware da raccogliere, sarà visualizzata solo una tabella Dettagli, che include la durata media assoluta di tutte le varianti.  
  
 ![La tabella dettagli e alcune varianti di riproduzione. ] (media/pix_frame_analysis_details.png "pix_frame_analysis_details")  
  
#### <a name="platforms-that-support-hardware-counters"></a>Piattaforme che supportano i contatori hardware  
 Per le piattaforme che supportano i contatori GPU hardware, ad esempio nVidia T40 SOC e tutti i SOC Qualcomm, sono visualizzate alcune tabelle Dettagli, una per ogni variante. Ogni contatore hardware disponibile è raccolto per ogni variante di rendering ed è visualizzato nella tabella Dettagli specifica.  
  
 ![I contatori hardware vengono visualizzati se supportati. ] (media/pix_frame.png "pix_frame")  
  
 Le informazioni relative ai contatori hardware offrono una visualizzazione molto dettagliata del comportamento specifico della piattaforma hardware per ogni chiamata di disegno, che possono aiutare a identificare con grande precisione la causa dei colli di bottiglia relativi alle prestazioni.  
  
> [!NOTE]
>  Diverse piattaforme hardware supportano contatori diversi. Questo non è un comportamento standard. I contatori e ciò che rappresentano sono determinati esclusivamente da ogni produttore di GPU.  
  
### <a name="marker-regions-and-events"></a>Aree di marcatori ed eventi  
 L'analisi dei frame supporta i marcatori di eventi definiti dagli utenti e i gruppi di eventi, visualizzati nella tabella Riepilogo e nelle tabelle Dettagli.  
  
 È possibile usare le API ID3DUserDefinedAnnotation o la famiglia legacy D3DPERF_ delle API per creare marcatori e gruppi. Quando si usa la famiglia D3DPERF_ delle API, è possibile assegnare a ogni marcatore e a ogni gruppo un colore, che sarà visualizzato dall'analisi dei frame come banda colorata nelle righe che includono il marcatore di eventi o i marcatori di inizio/fine dei gruppi di eventi e i rispettivi contenuti. Questa funzionalità può aiutare a identificare rapidamente gli eventi di rendering o i gruppi di eventi importanti.  
  
### <a name="warnings-and-errors"></a>Avvisi ed errori  
 Le operazioni di analisi dei frame sono a volte completate con avvisi o errori, che sono riepilogati sopra la sequenza temporale. Le informazioni dettagliate corrispondenti sono disponibili nella parte inferiore della scheda Analisi dei frame.  
  
 In genere, gli avvisi e gli errori sono solo a scopo informativo e non richiedono alcun intervento.  
  
 Gli avvisi indicano solitamente che il supporto hardware è carente ma sono disponibili soluzioni alternative, che non è possibile raccogliere i contatori hardware oppure che determinati dati sulle prestazioni potrebbero non essere attendibili, ad esempio se una soluzione alternativa influisce negativamente sulle prestazioni.  
  
 Gli errori indicano in genere che nell'implementazione dell'analisi dei frame sono presenti bug, che in un driver sono presenti bug, che il supporto hardware è carente e non sono possibili soluzioni alternative oppure che l'app prova a eseguire operazioni non supportate dalla riproduzione.  
  
### <a name="retries"></a>Nuovi tentativi  
 Se la GPU attraversa una transizione di stato di potenza durante l'analisi dei frame, eseguire di nuovo il passaggio di analisi interessato, poiché la velocità di clock della GPU ha subito modifiche e ha quindi reso non validi i risultati di durata relativa.  
  
 L'analisi dei frame limita il numero di nuovi tentativi a 10. Se le impostazioni di risparmio di energia o controllo del clock della piattaforma sono molto rigide, è possibile che l'analisi dei frame abbia esito negativo e che sia segnalato un errore a causa del superamento del limite di nuovi tentativi consentiti. Per ridurre questo problema, è possibile provare a modificare le impostazioni del risparmio energia e della limitazione della velocità del clock della piattaforma in modo che siano meno rigide, se la piattaforma lo permette.  
  
##  <a name="HardwareSupport"></a> Supporto hardware  
  
### <a name="timestamps-and-occlusion-queries"></a>Timestamp e query di occlusione  
 I timestamp sono supportati in tutte le piattaforme che supportano l'analisi dei frame. Le query di occlusione della profondità, necessarie per il contatore relativo ai pixel bloccati, sono supportate sulle piattaforme che supportano funzionalità di livello 9.2 o superiori.  
  
> [!NOTE]
>  Anche se i timestamp sono supportati su tutte le piattaforme che supportano l'analisi dei frame, la precisione e la coerenza dei timestamp variano a seconda della piattaforma usata.  
  
### <a name="gpu-counters"></a>Contatori della GPU  
 Il supporto per i contatori hardware della GPU dipende dall'hardware.  
  
 Poiché nessuna GPU di computer attualmente offerta da Intel, AMD, o nVidia supporta in modo affidabile i contatori hardware della GPU, l'analisi dei frame non raccoglie i contatori corrispondenti. Tuttavia, l'analisi dei Frame raccoglie i contatori hardware GPU seguenti, che li supporta in modo affidabile:  
  
-   nVidia T40 (Tegra4)
  
 Nessun'altra piattaforma che supporta l'analisi dei frame raccoglie i contatori hardware della GPU.  
  
> [!NOTE]
>  Poiché i contatori hardware GPU sono risorse hardware, è possibile che siano necessari più passaggi per raccogliere il set completo di contatori hardware per ogni variante di rendering. Di conseguenza, l'ordine in cui i contatori GPU vengono raccolti non è specificato.  
  
## <a name="unsupported-scenarios"></a>Scenari non supportati  
 Alcuni modi di usare l'analisi dei frame non sono supportati o non sono consigliati.  
  
### <a name="playback-of-high-feature-level-captures-on-down-level-devices"></a>Riproduzione di acquisizioni con livello di funzionalità elevato su dispositivi di livello inferiore  
 Quando si riproduce in Analizzatore grafica un file di log di grafica che usa un livello di funzionalità superiore rispetto a quello supportato dal computer di riproduzione, si verificherà automaticamente il fallback su WARP. In analisi dei frame non si verifica esplicitamente il fallback su WARP ed è generato un errore. WARP è utile per esaminare la correttezza di un'app Direct3D, ma non per esaminarne le prestazioni.  
  
> [!NOTE]
>  Anche se è importante tenere in considerazione le problematiche a livello di funzionalità, è possibile acquisire e riprodurre file di registro elementi grafici in diverse configurazioni e diversi dispositivi hardware. Il log di grafica è possibile riprodurre nuovamente a condizione che il file di log non include API e Usa i livelli di funzionalità non supportate nel computer di riproduzione.  
  
### <a name="direct3d-10-and-lower"></a>Direct3D 10 e versioni precedenti  
 Se l'app chiama l'API Direct3D 10, Analisi dei frame non sarà in grado di riconoscerla o di profilarla, anche se è riconosciuta e usata da altri strumenti di Analizzatore grafica.
  
> [!NOTE]
>  Questa situazione è applicabile solo alle chiamate alle API Direct3D in uso, non ai livelli di funzionalità.

### <a name="warp"></a>WARP  
 L'analisi dei frame deve essere usata per la profilatura e per il miglioramento delle prestazioni di rendering in hardware effettivo. Non è impedito l'esecuzione di analisi dei frame su dispositivi WARP, ma non è in genere un esercizio utile poiché in esecuzione su una CPU di fascia alta WARP è inferiore a anche il minor GPU moderne e le prestazioni di WARP possono variare notevolmente in base alla CPU specifica è in esecuzione.  
  
##  <a name="Variants"></a> Varianti  
 Ogni modifica apportata dall'analisi dei Frame al modo in cui viene eseguito il rendering di un frame durante la riproduzione è noto come un *variante*. Le varianti esaminate dall'analisi dei frame corrispondono a modifiche comuni e relativamente semplici che possono essere apportate per migliorare le prestazioni di rendering o la qualità visiva dell'app, ad esempio riducendo la dimensione delle trame, usando la compressione della trame o abilitando tipi diversi di anti-aliasing. Le varianti eseguono l'override del contesto di rendering normale e dei parametri dell'app. Di seguito è disponibile un riepilogo:  
  
|Variante|Descrizione|  
|-------------|-----------------|  
|**Dimensione del 1x1 Viewport**|Riduce a 1x1 pixel le dimensioni del riquadro di visualizzazione in tutte le destinazioni di rendering.<br /><br /> Per altre informazioni, vedere [variante delle dimensioni del riquadro di visualizzazione 1x1](1x1-viewport-size-variant.md)|  
|**0x MSAA**|Disabilita l'anti-aliasing multicampione (MSAA, Multi-Sample Anti-Aliasing) in tutte le destinazioni di rendering.<br /><br /> Per altre informazioni, vedere [0x / 2 x / 4 varianti di MSAA](0x-2x-4x-msaa-variants.md)|  
|**2x MSAA**|Abilita l'anti-aliasing multicampione (MSAA, Multi-Sample Anti-Aliasing) 2x in tutte le destinazioni di rendering.<br /><br /> Per altre informazioni, vedere [0x / 2 x / 4 varianti di MSAA](0x-2x-4x-msaa-variants.md)|  
|**4x MSAA**|Abilita l'anti-aliasing multicampione (MSAA, Multi-Sample Anti-Aliasing) 4x in tutte le destinazioni di rendering.<br /><br /> Per altre informazioni, vedere [0x / 2 x / 4 varianti di MSAA](0x-2x-4x-msaa-variants.md)|  
|**Filtraggio punti della trama**|Imposta la modalità di filtraggio su `DXD11_FILTER_MIN_MAG_MIP_POINT` (filtraggio punti della trama) per tutti i campioni di trama appropriati.<br /><br /> Per ulteriori informazioni, vedere [punto, bilineare, trilineare e anisotropico varianti del filtro della trama](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Filtraggio bilineare della trama**|Imposta la modalità di filtraggio su `DXD11_FILTER_MIN_MAG_LINEAR_MIP_POINT` (filtraggio bilineare della trama) per tutti i campioni di trama appropriati.<br /><br /> Per ulteriori informazioni, vedere [punto, bilineare, trilineare e anisotropico varianti del filtro della trama](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Filtraggio trilineare della trama**|Imposta la modalità di filtraggio su `DXD11_FILTER_MIN_MAG_MIP_LINEAR` (filtraggio trilineare della trama) per tutti i campioni di trama appropriati.<br /><br /> Per ulteriori informazioni, vedere [punto, bilineare, trilineare e anisotropico varianti del filtro della trama](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Filtraggio anisotropo della trama**|Imposta la modalità di filtraggio `DXD11_FILTER_ANISOTROPIC` e `MaxAnisotropy` a `16` (16 x filtraggio anisotropo della trama) per tutti i campioni di trama appropriati.<br /><br /> Per ulteriori informazioni, vedere [punto, bilineare, trilineare e anisotropico varianti del filtro della trama](point-bilinear-trilinear-and-anisotropic-texture-filtering-variants.md).|  
|**Formato di destinazione di rendering 16bpp**|Imposta il formato di pixel su `DXGI_FORMAT_B5G6R5_UNORM` (16bpp, formato 565) per tutte le destinazioni di rendering e i buffer nascosti.<br /><br /> Per altre informazioni, vedere [16bpp eseguire il rendering di destinazione variante del formato](16bpp-render-target-format-variant.md)|  
|**Generazione di mappe MIP**|Abilita le mappe MIP in tutte le trame che non corrispondono a destinazioni di rendering.<br /><br /> Per ulteriori informazioni, vedere [variante di generazione di mappe Mip](mip-map-generation-variant.md).|  
|**Dimensioni trama-metà**|Riduce le dimensioni di trama di tutte le trame che non corrispondono a destinazioni di rendering alla metà della dimensione originale in ogni dimensione. Ad esempio, una trama con dimensioni 256x128 è ridotta a 128x64 texel.<br /><br /> Per ulteriori informazioni, vedere [variante dimensioni trama](half-quarter-texture-dimensions-variant.md).|  
|**Dimensioni trama-quarto**|Riduce le dimensioni di trama di tutte le trame che non corrispondono a destinazioni di rendering a un quarto della dimensione originale in ogni dimensione. Ad esempio, una trama con dimensioni 256x128 è ridotta a 64x32 texel.<br /><br /> Per ulteriori informazioni, vedere [variante dimensioni trama](half-quarter-texture-dimensions-variant.md).|  
|**Compressione della trama BC**|Abilita la compressione a blocchi in tutte le trame con variante di formato di B8G8R8X8, B8G8R8A8 o R8G8B8A8 pixel. Le varianti di formato B8G8R8X8 sono compresse tramite BC1, mentre per le varianti di formato B8G8R8A8 e R8G8B8A8 si usa BC3.<br /><br /> Per ulteriori informazioni, vedere [variante di compressione della trama BC](bc-texture-compression-variant.md).|  
  
 Il risultato per la maggior parte delle varianti è prescrittivo, ovvero indica ad esempio che la riduzione delle dimensioni della trama a metà offre un incremento del 25 percento nella velocità o che l'abilitazione di 2x MSAA comporta un rallentamento pari solo al 2 percento. Per altre varianti potrebbe essere necessario interpretare i risultati. Se, a esempio la variante che modifica le dimensioni del riquadro di visualizzazioni in 1x1 mostra un miglioramento notevole delle prestazioni, ciò potrebbe indicare la presenza di un collo di bottiglia nel rendering causata da una bassa velocità di riempimento. In alternativa, se non sono rilevate modifiche significative nelle prestazioni, è possibile che il collo di bottiglia del rendering sia dovuto all'elaborazione dei vertici.