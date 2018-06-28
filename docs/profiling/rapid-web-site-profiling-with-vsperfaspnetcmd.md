---
title: Profilatura rapida di sito Web con VSPerfASPNETCmd | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- proflilng tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2efa8cf966967b07e1dbbfe5e2e1f6b7f8f6aef7
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572881"
---
# <a name="rapid-web-site-profiling-with-vsperfaspnetcmd"></a>Profilatura rapida di sito Web con VSPerfASPNETCmd

Lo strumento da riga di comando **VSPerfASPNETCmd** consente di eseguire facilmente la profilatura di applicazioni Web di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Rispetto allo strumento da riga di comando [VSPerfCmd](../profiling/vsperfcmd.md), le opzioni sono ridotte, non è necessario impostare variabili di ambiente e non è richiesto il riavvio del computer. **VSPerfASPNETCmd** è il metodo preferito per la profilatura con il profiler autonomo. Per altre informazioni, vedere [Procedura: Installare il profiler autonomo](../profiling/how-to-install-the-stand-alone-profiler.md).

> [!NOTE]
> Le funzionalità di sicurezza avanzate di Windows 8 e Windows Server 2012 hanno richiesto modifiche significative riguardo alla modalità di raccolta dei dati su queste piattaforme da parte del profiler di Visual Studio. Le app UWP richiedono anche nuove tecniche di raccolta. Vedere [Strumenti per le prestazioni nelle applicazioni Windows 8 e Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

 In alcuni scenari, quali la raccolta di dati di concorrenza o la sospensione e la ripresa della profilatura, **VSPerfCmd** costituisce il metodo di profilatura preferito.

> [!NOTE]
> Gli strumenti da riga di comando degli Strumenti di profilatura si trovano nella sottodirectory *\Team Tools\Performance Tools* della directory di installazione di Visual Studio. Nei computer a 64 bit usare lo strumento VSPerfASPNETCmd disponibile nella directory *\Team Tools\Performance Tools* 32 bit. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso. Per altre informazioni, vedere [Specifica del percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

## <a name="profiling-an-aspnet-application"></a>Profilatura di un'applicazione ASP.NET

Per profilare un'applicazione Web di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], digitare uno dei comandi descritti nelle sezioni seguenti. Il sito Web viene avviato e il profiler inizia a raccogliere dati. Verificare la funzionalità dell'applicazione e quindi chiudere il browser. Per interrompere la profilatura, premere **INVIO** nella finestra del prompt dei comandi.

> [!NOTE]
> Per impostazione predefinita, il prompt dei comandi non restituisce il controllo dopo un comando **vsperfaspnetcmd**. È possibile usare l'opzione **/nowait** per imporre il ripristino del prompt dei comandi. Vedere [Uso dell'opzione /NoWait](#UsingNoWait).

## <a name="to-collect-application-statistics-by-using-the-sampling-method"></a>Per raccogliere statistiche sull'applicazione tramite il metodo di campionamento
 Il campionamento è il metodo di profilatura predefinito dello strumento **VSPerfASPNETCmd** e non è necessario specificarlo nella riga di comando. La riga di comando seguente consente di raccogliere statistiche sull'applicazione dall'applicazione Web specificata:

 **vsperfaspnetcmd**  *websiteUrl*

## <a name="to-collect-detailed-timing-data-by-using-the-instrumentation-method"></a>Per raccogliere dati di intervallo dettagliati tramite il metodo di strumentazione

Usare la riga di comando seguente per raccogliere dati di intervallo dettagliati da un'applicazione Web di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilata dinamicamente:

**vsperfaspnetcmd /trace**  *websiteUrl*

Se si vogliono profilare file con estensione *dll* compilati staticamente nell'applicazione Web, è necessario instrumentare i file tramite lo strumento da riga di comando [VSInstr](../profiling/vsinstr.md). Il comando vsperfaspnetcmd /trace includerà i dati dai file instrumentati.

## <a name="to-collect-net-memory-data"></a>Per raccogliere dati di memoria .NET

L'opzione **/Memory** consente di raccogliere dati sull'allocazione di oggetti nella memoria .NET ed è in grado di raccogliere dati sulla durata di tali oggetti. La raccolta di dati di allocazione è la modalità predefinita dell'opzione **/Memory** e non è necessario specificarla nella riga di comando.

 **vsperfaspnetcmd /memory** *websiteUrl*

 Usare il parametro **Lifetime** per raccogliere dati sulla durata degli oggetti oltre ai dati di allocazione:

 **vsperfaspnetcmd /memory:lifetime** *websiteUrl*

 È inoltre possibile usare l'opzione **/Trace** per includere informazioni di intervallo dettagliate con i dati di memoria .NET:

 **vsperfaspnetcmd /memory**[**:lifetime**] **/trace**`websiteUrl`

## <a name="to-collect-tier-interaction-data"></a>Per raccogliere dati di interazione tra livelli

> [!WARNING]
> I dati di profilatura dell'interazione tra livelli possono essere raccolti usando qualsiasi edizione di Visual Studio, ma possono essere visualizzati solo in Visual Studio Enterprise.
>
> Per raccogliere dati TIP in Windows 8 o Windows Server 2012, è necessario usare l'opzione di strumentazione (**/trace**).

Per raccogliere dati di interazione tra livelli con dati di campionamento:

**vsperfaspnetcmd /tip** `websiteUrl`

Per raccogliere dati di interazione tra livelli con dati di strumentazione:

**vsperfaspnetcmd /trace /tip** *websiteUrl*

Per raccogliere dati di interazione tra livelli con dati di memoria .NET:

**vsperfaspnetcmd /memory**[**:lifetime**] **/tip***websiteUrl*

## <a name="UsingNoWait"></a> Uso dell'opzione /NoWait

Per impostazione predefinita, il prompt dei comandi non restituisce il controllo dopo un comando **vsperfaspnetcmd**. È possibile usare l'opzione della sintassi seguente per imporre il ripristino del prompt dei comandi. È quindi possibile eseguire altre operazioni nella finestra del prompt dei comandi. Per terminare la profilatura, usare l'opzione **/shutdown** in un comando **vsperfaspnetcmd** distinto.

Per iniziare la profilatura:

**vsperfaspnetcmd** [*/Opzioni*] **/nowait***websiteUrl*

Per terminare la profilatura:

**vsperfaspnetcmd /shutdown** *websiteUrl*

## <a name="additional-options"></a>Opzioni aggiuntive

È possibile aggiungere una qualsiasi delle opzioni seguenti ai comandi elencati in precedenza in questa sezione, ad eccezione del comando **vsperfaspnetcmd /shutdown**.

|Opzione|Descrizione|
|------------|-----------------|
|**/Output:** `VspFile`|Per impostazione predefinita, il file dei dati di profilatura (con estensione *vsp*) viene creato nella directory corrente con il nome file **PerformanceReport.vsp**. Usare l'opzione /output per specificare un percorso o un nome file diverso o entrambi.|
|**/PackSymbols:Off**|Per impostazione predefinita, VsPerfASPNETCmd incorpora simboli (nomi di funzione e di parametro e così via) nel file con estensione *vsp*. L'incorporamento di simboli può aumentare notevolmente le dimensioni del file di dati di profilatura. Se quando si analizzano i dati si ha accesso ai file con estensione *pdb* contenenti i simboli, usare l'opzione /packsymbols:off per disabilitare l'incorporamento dei simboli.|
