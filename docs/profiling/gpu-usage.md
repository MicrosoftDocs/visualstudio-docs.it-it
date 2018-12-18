---
title: Utilizzo GPU | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9926846ceaba3591a3e89f2eba0fa2d3888e9302
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="gpu-usage"></a>Utilizzo GPU
Lo strumento Utilizzo GPU disponibile nell'hub Prestazioni e diagnostica consente di comprendere meglio l'utilizzo hardware in generale da parte dell'app Direct3D. Può essere usato per determinare se le prestazioni dell'app sono basate sulla CPU o sulla GPU e per ottenere informazioni su come usare l'hardware della piattaforma in modo più efficiente. Utilizzo GPU supporta le app che usano Direct3D 12, Direct3D 11 e Direct3D 10. Non supporta altre API grafiche, come Direct2D o OpenGL.  
  
 Questa è la finestra **Report Utilizzo GPU**:  
  
 ![Report Utilizzo GPU con sequenze temporali per CPU e GPU](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")  
  
## <a name="requirements"></a>Requisiti  
 Di seguito sono elencati i requisiti aggiuntivi per lo strumento Utilizzo GPU rispetto ai requisiti di Diagnostica grafica.  
  
-   Una GPU e un driver che supportino la strumentazione di temporizzazione necessaria.  
  
    > [!NOTE]
    >  Per altre informazioni sull'hardware e i driver supportati, vedere [Hardware e driver supportati](#hwsupport) alla fine di questo documento.  
  
 Per altre informazioni sui requisiti di Diagnostica della grafica, vedere [Introduzione](../debugger/graphics/getting-started-with-visual-studio-graphics-diagnostics.md).  
  
## <a name="using-the-gpu-usage-tool"></a>Uso dello strumento Utilizzo GPU  
 Quando si esegue l'app nello strumento Utilizzo GPU, Visual Studio crea una sessione di diagnostica che genera un grafico di informazioni generali sulle prestazioni di rendering dell'app e sull'utilizzo della GPU in tempo reale.  
  
#### <a name="to-start-the-gpu-usage-tool"></a>Per avviare lo strumento Utilizzo GPU:  
  
1.  Nel menu principale scegliere **Debug**, quindi **Prestazioni e diagnostica** (tastiera: premere ALT+F2).  
  
2.  Nell'hub Prestazioni e diagnostica selezionare la casella accanto a **Utilizzo GPU**. Facoltativamente, selezionare le caselle accanto agli altri strumenti a cui si è interessati. È possibile eseguire contemporaneamente svariati strumenti per prestazioni e diagnostica per ottenere un quadro più completo delle prestazioni dell'app.  
  
     ![Scegliere gli strumenti di diagnostica da usare.](media/gfx_diag_diagsession_tools.png "gfx_diag_diagsession_tools")  
  
    > [!NOTE]
    >  Non tutti gli strumenti per le prestazioni e la diagnostica possono essere eseguiti contemporaneamente.  
  
3.  Scegliere il pulsante blu **Inizia** nella parte inferiore dell'hub Prestazioni e diagnostica per eseguire l'app negli strumenti selezionati.  
  
 Le informazioni generali visualizzate in tempo reale includono la durata e la frequenza dei fotogrammi e l'utilizzo della GPU. Le diverse informazioni sono rappresentate in grafici distinti, ma usano una scala cronologica comune, in modo che sia possibile correlarle facilmente.  
  
 I grafici **Durata frame (ms)** e **Frame al secondo (FPS)** contengono due linee rosse orizzontali che rappresentano destinazioni di prestazioni di 30 e 60 frame al secondo. Nel grafico **Durata frame** l'app supera la destinazione di prestazioni se il grafico si trova sotto la linea e non la raggiunge se il grafico si trova sopra la linea. Nel grafico Fotogrammi al secondo avviene il contrario: l'app supera l'obiettivo di prestazioni se il grafico si trova sopra la linea e non lo raggiunge se il grafico si trova sotto la linea. In primo luogo, questi grafici consentono di ottenere un'idea generale delle prestazioni dell'app e di identificare i rallentamenti che può essere utile analizzare, ad esempio un calo improvviso della frequenza dei fotogrammi o un picco nell'utilizzo della GPU.  
  
 Quando l'app viene eseguita nello strumento Utilizzo GPU, la sessione di diagnostica raccoglie anche informazioni dettagliate sugli eventi di grafica eseguiti nella GPU. Queste informazioni vengono usate per generare un report più dettagliato sul modo in cui l'app utilizza l'hardware. Poiché la generazione del report a partire dalle informazioni raccolte richiede del tempo, il report è disponibile solo al termine della raccolta delle informazioni nella sessione di diagnostica.  
  
 Quando si vuole esaminare più da vicino un problema di utilizzo o di prestazioni, interrompere la raccolta di informazioni sulle prestazioni in modo che sia possibile generare il report.  
  
#### <a name="to-generate-and-view-the-gpu-usage-report"></a>Per generare e visualizzare il report sull'utilizzo della GPU:  
  
1.  Nella parte inferiore della finestra della sessione di diagnostica scegliere il collegamento **Arresta raccolta** o premere **Arresta** nell'angolo superiore sinistro.  
  
     ![Raccogliere informazioni sugli intervalli per GPU e CPU.](media/gfx_diag_gpu_usage_collect.png "gfx_diag_gpu_usage_collect")  
  
2.  Nella parte superiore del report selezionare in uno dei grafici una sezione che mostra il problema da analizzare. La selezione può essere lunga fino a 3 secondi. Le sezioni più lunghe vengono troncate nella parte iniziale.  
  
     ![Dopo la raccolta, selezionare un intervallo per visualizzare i dettagli](media/gfx_diag_gpu_usage_select1.png "gfx_diag_gpu_usage_select1")  
  
3.  Nella parte inferiore del report scegliere il collegamento **visualizzare i dettagli** nel messaggio **…Fare clic qui per visualizzare i dettagli sull'utilizzo della GPU in tale intervallo** per visualizzare una sequenza temporale dettagliata della selezione.  
  
     ![Dopo la raccolta, con intervallo selezionato](media/gfx_diag_gpu_usage_select2.png "gfx_diag_gpu_usage_select2")  
  
 Viene aperto un nuovo documento a schede che contiene il report. Il report sull'utilizzo della GPU consente di vedere il momento in cui nella CPU viene avviato un evento di grafica, il momento in cui l'evento raggiunge la GPU e il tempo impiegato dalla GPU per eseguirlo. Queste informazioni sono utili per identificare i colli di bottiglia e le opportunità di aumentare il parallelismo nel codice.  

<!-- VERSIONLESS -->
## <a name="export-to-gpuview-or-windows-performance-analyzer"></a>Esportare in GPUView o Windows Performance Analyzer
A partire da Visual Studio 2017, questi dati possono essere aperti con [GPUView](/windows-hardware/drivers/display/using-gpuview) e [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer) facendo clic sui collegamenti **Apri in GpuView** o **Apri in WPA** nella parte inferiore destra della sessione di diagnostica.

![Apri in...](media/gfx_diag_open_in.png)
<!-- /VERSIONLESS -->

## <a name="using-the-gpu-usage-report"></a>Uso del report Utilizzo GPU  
 La parte superiore del report sull'utilizzo della GPU mostra le sequenze temporali delle attività di elaborazione della CPU, le attività di rendering della GPU e le attività di copia della GPU. Queste sequenze temporali sono divise da barre verticali grigio chiaro, che rappresentano il vsync dello schermo; la frequenza delle barre corrisponde alla frequenza di aggiornamento di uno degli schermi (selezionato usando l'elenco a discesa **Schermo**) da cui sono stati raccolti i dati sull'utilizzo della GPU. Poiché lo schermo può avere una frequenza di aggiornamento superiore rispetto alla destinazione di prestazioni dell'app, potrebbe non esserci una relazione 1 a 1 tra vsync e frequenza dei frame che l'app deve ottenere. Per raggiungere la destinazione di prestazioni, un'app deve completare l'elaborazione, eseguire il rendering ed effettuare una chiamata Present() al framerate di destinazione, ma il frame sottoposto a rendering non verrà visualizzato fino al vsync successivo a Present().  
  
 Nella parte inferiore viene visualizzato un elenco degli eventi di grafica che si sono verificati nel periodo di tempo esaminato nel report.  
  
 Di seguito viene illustrata la finestra **Report Utilizzo GPU**:  
  
 ![Report Utilizzo GPU con sequenze temporali per CPU e GPU](media/gfx_diag_gpu_usage_report.png "gfx_diag_gpu_usage_report")  
  
 Selezionando uno degli eventi nella parte inferiore del report, nelle sequenze temporali pertinenti viene inserito un marcatore accanto agli eventi corrispondenti. In genere si tratta di un evento su un thread della CPU, che rappresenta la chiamata API, e di un secondo evento in una delle sequenze temporali della GPU, che rappresenta il punto in cui la GPU ha completato l'attività. Analogamente, se si seleziona uno degli eventi in una sequenza temporale, nella parte inferiore del report viene evidenziato l'evento corrispondente. Quando si riduce il livello di zoom sulle sequenze temporali nella parte superiore del report, sono visibili solo gli eventi che richiedono più tempo. Per visualizzare gli eventi di durata più breve, ingrandire le sequenze temporali premendo CTRL e la rotellina del dispositivo di puntamento oppure usando il controllo di ridimensionamento nell'angolo inferiore sinistro del riquadro superiore. È anche possibile trascinare il contenuto del pannello della sequenza temporale per spostarsi tra gli eventi registrati.  
  
 Per trovare più facilmente ciò che si sta cercando, è possibile filtrare il report Utilizzo GPU in base a nomi di processo, ID dei thread e nome dell'evento. È anche possibile scegliere lo schermo la cui frequenza di aggiornamento determina le linee vysnc e, se l'app usa l'interfaccia ID3DUserDefinedAnnotation per raggruppare i comandi di rendering, ordinare gerarchicamente gli eventi.  
  
 Di seguito sono disponibili maggiori dettagli:  
  
|Controllo filtro|Descrizione|  
|--------------------|-----------------|  
|**Processo**|Nome del processo a cui si è interessati. Questo elenco a discesa contiene tutti i processi che hanno utilizzato la GPU durante la sessione di diagnostica. Il colore associato al processo nell'elenco a discesa è il colore dell'attività del thread nelle sequenze temporali successive.|  
|**Thread**|ID del thread a cui si è interessati. In un'app multithread, questo consente di isolare thread specifici che appartengono al processo a cui si è interessati. Gli eventi associati al thread selezionato sono evidenziati in ogni sequenza temporale.|  
|**Schermo**|Numero dello schermo di cui è visualizzata la frequenza di aggiornamento **Nota:** alcuni driver possono essere configurati in modo da presentare più schermi fisici come un unico schermo virtuale di grandi dimensioni. È possibile che nell'elenco sia presente un solo schermo, anche se al computer sono collegati più schermi.|  
|**Filtro**|Parole chiave a cui si è interessati. Nella parte inferiore del report saranno visualizzati solo gli eventi che corrispondono completamente o parzialmente a una parola chiave. È possibile specificare più parole chiave separandole con un punto e virgola (;).|  
|**Hierarchy Sort** (Ordinamento gerarchia)|Casella di controllo che indica se le gerarchie degli eventi, definite mediante marcatori utente, vengono mantenute o ignorate.|  
  
 L'elenco eventi nella parte inferiore del report di utilizzo della GPU mostra i dettagli relativi a ogni evento.  
  
|Colonna|Descrizione|  
|------------|-----------------|  
|**Nome evento**|Nome dell'evento di grafica. Un evento in genere corrisponde a un evento nella sequenza temporale di un thread della CPU e un evento in una sequenza temporale della GPU.<br /><br /> Se Utilizzo GPU non è riuscito a determinare il nome di un evento, i nomi degli eventi possono risultare non attribuiti. Per altre informazioni, vedere la nota sotto questa tabella.|  
|**Avvio CPU (ns)**|Momento di avvio dell'evento nella CPU a seguito della chiamata a un'API Direct3D. Il tempo viene misurato in nanosecondi in relazione al momento di avvio dell'app.|  
|**Avvio GPU (ns)**|Momento di avvio dell'evento nella GPU. Il tempo viene misurato in nanosecondi in relazione al momento di avvio dell'app.|  
|**Durata GPU (ns)**|Tempo impiegato per il completamento dell'evento nella GPU, espresso in nanosecondi.|  
|**Nome processo**|Nome dell'app da cui proviene l'evento.|  
|**ID thread**|ID del thread da cui proviene l'evento.|  
  
> [!IMPORTANT]
>  Se la GPU o il driver non supporta le funzionalità di strumentazione necessarie, tutti gli eventi vengono visualizzati come non attribuiti. Se si verifica questo problema, aggiornare il driver della GPU e riprovare. Per altre informazioni, vedere [Hardware e driver supportati](#hwsupport) più avanti.  
  
## <a name="gpu-usage-settings"></a>Impostazioni di Utilizzo GPU  
 Si può configurare lo strumento Utilizzo GPU in modo da posticipare la raccolta di informazioni di profilatura, anziché iniziare a raccogliere le informazioni all'avvio dell'app. Poiché le dimensioni delle informazioni di profilatura possono essere notevoli, questo è utile quando si è certi che i rallentamenti nelle prestazioni dell'app compariranno solo in un momento successivo.  
  
#### <a name="to-postpone-profiling-from-the-start-of-the-app"></a>Per posticipare la profilatura rispetto all'avvio dell'app:  
  
1.  Nel menu principale scegliere **Debug**, quindi **Prestazioni e diagnostica** (tastiera: premere ALT+F2).  
  
2.  Nell'hub Prestazioni e diagnostica seguire il collegamento **Impostazioni** accanto a **Utilizzo GPU**.  
  
3.  In **Configurazione Profilatura GPU** nella pagina delle proprietà **Generale** deselezionare la casella di controllo **Begin profiling at app start** (Inizia profilatura all'avvio dell'app) per posticipare la profilatura.  
  
     ![Configurare l'inizio della raccolta Utilizzo GPU](media/gfx_diag_gpu_usage_config.png "gfx_diag_gpu_usage_config")  
  
> [!IMPORTANT]
>  Il posticipo della profilatura non è attualmente supportato per le app Direct3D 12.  
  
 Se si posticipa la raccolta delle informazioni di profilatura con questa impostazione, quando si esegue l'app nello strumento Utilizzo GPU, nella parte inferiore della finestra dello strumento diventa disponibile un collegamento aggiuntivo. Per avviare la raccolta di informazioni di profilatura, scegliere il collegamento **Inizia** nel messaggio **Inizia a raccogliere altri dati dettagliati sull'utilizzo della GPU**.  
  
##  <a name="hwsupport"></a> Hardware e driver supportati  
 Di seguito è riportato un elenco delle GPU e dei driver supportati:  
  
|Vendor|Descrizione GPU|Versione driver richiesta|  
|------------|---------------------|-----------------------------|  
|Intel®|Processori Intel® Core di quarta generazione (Haswell)<br /><br /> -   Intel® HD Graphics (GT1)<br />-   Intel® HD Graphics 4200 (GT2)<br />-   Intel® HD Graphics 4400 (GT2)<br />-   Intel® HD Graphics 4600 (GT2)<br />-   Intel® HD Graphics P4600 (GT2)<br />-   Intel® HD Graphics P4700 (GT2)<br />-   Intel® HD Graphics 5000 (GT3)<br />-   Intel® Iris™ Graphics 5100 (GT3)<br />-   Intel® Iris™ Pro Graphics 5200 (GT3e)|-- (usare i driver più recenti)|  
|AMD®|La maggior parte dalla serie AMD Radeon™ HD 7000 (escluso AMD Radeon™ HD 7350-7670)<br /><br /> GPU AMD Radeon™, GPU AMD FirePro™ e acceleratori grafici AMD FirePro con architettura Graphics Core Next (GCN).<br /><br /> APU (Accelerated Processing Unit) AMD® E-Series e AMD A-series con architettura Graphics Core Next (GCN) (Kaveri, Kabini, Temash, Beema, Mullins)|14.7 RC3 o versione successiva|  
|NVIDIA®|La maggior parte da NVIDIA® GeForce® serie 400.<br /><br /> GPU NVIDIA® GeForce®, GPU NVIDIA Quadro® e acceleratori grafici NVIDIA® Tesla™ con architettura Fermi™, Kepler™ o Maxwell™.|343.37 o versione successiva|  
  
 Al momento le configurazioni multi-GPU, come NVIDIA® SLI™ e AMD Crossfire™, non sono supportate. I sistemi grafici ibridi, come NVIDIA® Optimus™ e AMD Enduro™, sono supportati.  
  
## <a name="see-also"></a>Vedere anche  
  
-   [Solve the Tough Graphics Problems with your Game Using DirectX Tools (video)](http://channel9.msdn.com/Events/GDC/GDC-2015/Solve-the-Tough-Graphics-Problems-with-your-Game-Using-DirectX-Tools) (Risolvere problemi di grafica complessi del gioco usando gli strumenti DirectX)  
-   [GPU Usage Tool in Visual Studio (video)](http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/715) (Strumento Utilizzo GPU in Visual Studio)  
-   [GPU Usage tool in Visual Studio 2013 Update 4 CTP1 (blog)](http://blogs.msdn.com/b/vcblog/archive/2014/09/05/gpu-usage-tool-in-visual-studio-2013-update-4-ctp1.aspx) (Strumento Utilizzo GPU in Visual Studio 2013 Update 4 CTP1)  
-   [GPU Usage for DirectX in Visual Studio (blog)](http://blogs.msdn.com/b/ianhu/archive/2014/12/16/gpu-usage-for-directx-in-visual-studio.aspx) (Utilizzo GPU per DirectX in Visual Studio)
- [GPUView](/windows-hardware/drivers/display/using-gpuview) 
- [Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)