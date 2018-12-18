---
title: Supporta l'istruzione per Visual Basic 6.0 | Documenti Microsoft
ms.date: 08/28/2017
ms.technology: devlang-vb
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- VB6 support
- Visual Basic 6.0 support
ms.assetid: ffc5ba4d-44d7-4ef7-a3f6-38a8738bf127
author: paulyuk
ms.author: paulyuk
ms.workload:
- paulyuk
ms.openlocfilehash: cb25f85be6c77dfbef6969435d14f2cae61debf2
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="support-statement-for-visual-basic-60-on-windows"></a>Supporta l'istruzione per Visual Basic 6.0 in Windows


## <a name="executive-summary"></a>Riepilogo

Il team di Visual Basic viene eseguito il commit per la compatibilità "It Just Works" per le applicazioni Visual Basic 6.0 i sistemi operativi Windows supportati seguenti: 

- Windows 10
- Windows 8,1
- Windows 7
- Windows Server 2016
- Windows Server 2012 including R2
- Windows Server 2008 R2 incluso

Obiettivo del team di Visual Basic è che le applicazioni Visual Basic 6.0 continuano a eseguire sulle versioni supportate di Windows. Come descritto in questo documento, il runtime di Visual Basic 6.0 core sarà supportato per la durata completa delle versioni supportate di Windows, ovvero cinque anni di supporto mainstream seguita da cinque anni di supporto esteso (http://support.microsoft.com/gp/lifepolicy). La barra di supporto sarà limitata a gravi regressioni e problemi di sicurezza critico per le applicazioni esistenti.

## <a name="technical-summary"></a>Riepilogo tecnico

Visual Basic 6.0 è costituito da questi risultati finali chiave:
- Visual Basic 6.0 IDE (Integrated Development Environment).
- Runtime di Visual Basic 6.0: le librerie di base e il motore di esecuzione utilizzato per eseguire le applicazioni Visual Basic 6.0.
- File estesi Runtime di Visual Basic 6.0: selezionare i file OCX del controllo ActiveX, librerie e strumenti per la spedizione con il supporto IDE e come una versione online.

## <a name="the-visual-basic-60-ide"></a>6.0 IDE di Visual Basic

L'IDE di Visual Basic 6.0 non è più supportata a partire da 8 aprile 2008. Inoltre, i team di Windows e Visual Basic sono testati IDE di Visual Basic 6.0 in Windows Vista, Windows 7, Windows Server 2008, Windows 8 e Windows 8.1 per comprendere e ridurre (se appropriato), problemi di compatibilità in versioni a 32 bit di Windows (vedere il [Windows a 64 Bit](#62-bit-windows) sezione riportata di seguito per ulteriori informazioni su sistemi a 64 bit). Questo annuncio non modifica i criteri di supporto per l'ambiente IDE.

## <a name="the-visual-basic-60-runtime"></a>Il runtime di Visual Basic 6.0

Il runtime di Visual Basic 6.0 è definito come i file binari compilati originariamente inclusi nell'elenco di ridistribuzione per Visual Basic 6.0. Questi file sono stati contrassegnati come distribuibile nella licenza di Visual Basic 6.0 originale. Esempi di questi file includono la libreria di runtime di Visual Basic 6.0 (`msvbvm60.dll`), controlli (ad esempio, `msflxgrd.ocx`) insieme a runtime file di supporto per le altre aree funzionali principali (ad esempio MDAC).

Il runtime è suddivisa in tre gruppi:

- File di runtime, è supportata nel sistema operativo di spedizione

   File di runtime chiave Visual Basic 6.0, utilizzati nella maggior parte degli scenari di applicazione, vengono forniti con e supportati per la durata delle versioni supportate di Windows. Questa durata è di cinque anni di supporto mainstream e cinque anni di supporto esteso dal momento in cui viene fornita una determinata versione di Windows. Questi file sono stati testati per la compatibilità come parte del testing delle applicazioni di Visual Basic 6.0 in esecuzione sulle versioni supportate di Windows. 

   > [!NOTE]
   > Tutte le versioni supportate di Windows contengono un elenco di file quasi identico, i requisiti di redist per applicazioni che contengono questi file devono essere pressoché identici. Una differenza fondamentale è che `TriEdit.dll` è stato rimosso da Windows Vista e versioni successive.

- I file di runtime: supportati-i file da distribuire con l'applicazione estese

   Questo elenco esteso è costituito da controlli chiavi, librerie e gli strumenti installati dal supporto di IDE o dal sito Web nel computer di sviluppo. In genere, l'IDE VB6 installata questi controlli nel computer di sviluppatori per impostazione predefinita. Lo sviluppatore deve comunque ridistribuire i file con l'applicazione. La versione supportata di file è disponibile online in Microsoft Download Center (http://go.microsoft.com/fwlink/?LinkID=142927).

- File di runtime non supportato

   Alcuni file uno sono scesi fuori mainstream supporta o non sono incluse come parte di redist la fase di esecuzione (ad esempio, sono stati inclusi nel `\Tools` cartella del supporto IDE per supportare le applicazioni legacy VB4/VB5, o sono controlli di terze parti). Questi file non sono supportati in Windows. invece, sono soggette a qualsiasi contratto di supporto si applica ai supporti che siano stati spediti con. Ciò non implica garanzie di supporto e di manutenzione. In alcuni casi, sono supportate nelle versioni successive di queste librerie. Di seguito vengono forniti dettagli su compatibilità con le versioni precedenti o la migrazione a versioni supportate.

Per informazioni specifiche sui file inclusi in ogni gruppo di supporto, vedere il [Runtime definizione](#runtime-definition) sezione riportata di seguito.

## <a name="the-visual-basic-60-support-lifetime"></a>La durata di supporto di Visual Basic 6.0

Supporto e/o file binari di runtime di Visual Basic 6.0 di spedizione nelle versioni supportate di Windows non modifica i criteri di supporto per l'IDE di Visual Basic 6.0 o l'IDE di Visual Studio 6.0 nel suo complesso. Tali prodotti è stato spostato da un supporto esteso 8 aprile 2008.

Dettagli sulla disponibilità del supporto dei prodotti Microsoft sono disponibili in http://support.microsoft.com/gp/lifepolicy. Come parte di questo ciclo di vita del supporto tecnico, Microsoft continuerà a supportare il runtime di Visual Basic 6.0 sulle versioni supportate di Windows per la durata di supporto di tali sistemi operativi. Ciò significa, ad esempio, è possibile che il runtime di Visual Basic 6.0 sarà supportato in Windows Server 2003 fino a giugno 2008 per il supporto Mainstream e giugno 2013 per il supporto esteso.
Per ulteriori informazioni sulla disponibilità del supporto o per informazioni sulle altre opzioni di supporto, visitare la pagina di supporto all'http://www.microsoft.com/support.

## <a name="64-bit-windows"></a>Windows a 64 bit

File di runtime di Visual Basic 6.0 sono a 32 bit. Questi file vengono forniti in 64 bit sistemi operativi Windows a cui fa riferimento nella tabella seguente. componenti e applicazioni a 32 bit VB6 sono supportati nell'ambiente di emulazione di WOW solo. componenti a 32 bit devono anche essere ospitati nei processi di applicazione a 32 bit.

L'IDE di Visual Basic 6.0 non è stato offerto mai in una versione a 64 bit nativa, né l'IDE a 32 bit è stato introdotto in Windows a 64 bit. Lo sviluppo di VB6 in Windows a 64 bit o a qualsiasi architettura nativo diverso da 32 bit non è e non sarà più supportato.

## <a name="windows-7"></a>Windows 7

Dopo la versione iniziale di questa istruzione di supporto, il sistema operativo Windows 7 è stato rilasciato. Questo documento è stato aggiornato per chiarire il supporto Microsoft per VB6 in Windows 7.

Il runtime VB6 spedirà e sarà supportato in Windows 7 per la durata del sistema operativo. File di runtime di Visual Basic 6.0 continuano a essere solo a 32 bit, e tutti i componenti devono essere ospitati in processi di applicazione a 32 bit.

## <a name="windows-81"></a>Windows 8,1

Dopo la versione iniziale di questa istruzione di supporto, il sistema operativo Windows 8.1 è stato rilasciato. Questo documento è stato aggiornato per chiarire il supporto Microsoft per VB6 in Windows 8.1.

Il runtime VB6 spedirà e sarà supportato in Windows 8.1 per la durata del sistema operativo. File di runtime di Visual Basic 6.0 continuano a essere solo a 32 bit, e tutti i componenti devono essere ospitati in processi di applicazione a 32 bit. Gli sviluppatori di essere considerata la storia di supporto per Windows 8.1 non è identico a quello in Windows 7.

## <a name="windows-10"></a>Windows 10

Dopo la versione iniziale di questa istruzione di supporto, è stato rilasciato il sistema operativo Windows 10. Questo documento è stato aggiornato per chiarire il supporto Microsoft per VB6 in Windows 10.

Il runtime VB6 spedirà e sarà supportato in Windows 10 per la durata del sistema operativo. File di runtime di Visual Basic 6.0 continuano a essere solo a 32 bit, e tutti i componenti devono essere ospitati in processi di applicazione a 32 bit. Gli sviluppatori di essere considerata la storia di supporto per Windows 10 non è identico a quello in Windows 8.1.

## <a name="windows-server-2008"></a>Windows Server 2008

Dopo la versione iniziale di questa istruzione di supporto, il sistema operativo Windows Server 2008 è stato rilasciato. Questo documento è stato aggiornato per chiarire il supporto Microsoft per VB6 in Windows Server 2008.

Il runtime VB6 spedirà e sarà supportato in Windows Server 2008 per la durata del sistema operativo. File di runtime di Visual Basic 6.0 continuano a essere solo a 32 bit, e tutti i componenti devono essere ospitati in processi di applicazione a 32 bit.

## <a name="windows-server-2008-r2"></a>Windows Server 2008 R2

Dopo la versione iniziale di questa istruzione di supporto, il sistema operativo Windows Server 2008 R2 è stato rilasciato. Questo documento è stato aggiornato per chiarire il supporto Microsoft per VB6 in Windows Server 2008 R2.

Il runtime VB6 spedirà e sarà supportato in Windows Server 2008 R2 per la durata del sistema operativo. File di runtime di Visual Basic 6.0 continuano a essere solo a 32 bit, e tutti i componenti devono essere ospitati in processi di applicazione a 32 bit. Gli sviluppatori di essere considerata la storia di supporto per Windows Server 2008 R2 non è identico a quello in Windows Server 2008.

## <a name="windows-server-2012"></a>Windows Server 2012

Dopo la versione iniziale di questa istruzione di supporto, il sistema operativo Windows Server 2012 è stato rilasciato. Questo documento è stato aggiornato per chiarire il supporto Microsoft per VB6 in Windows Server 2012.

Il runtime VB6 spedirà e sarà supportato in Windows Server 2012 per la durata del sistema operativo. File di runtime di Visual Basic 6.0 continuano a essere solo a 32 bit, e tutti i componenti devono essere ospitati in processi di applicazione a 32 bit. Gli sviluppatori di essere considerata la storia di supporto per Windows Server 2012 non è identico a quello in Windows Server 2008 R2.

## <a name="windows-server-2012-r2"></a>Windows Server 2012 R2

Dopo la versione iniziale di questa istruzione di supporto, il sistema operativo Windows Server 2012 R2 è stato rilasciato. Questo documento è stato aggiornato per chiarire il supporto Microsoft per VB6 in Windows Server 2012 R2.

Il runtime VB6 spedirà e sarà supportato in Windows Server 2012 R2 per la durata del sistema operativo. File di runtime di Visual Basic 6.0 continuano a essere solo a 32 bit, e tutti i componenti devono essere ospitati in processi di applicazione a 32 bit. Gli sviluppatori di essere considerata la storia di supporto per Windows Server 2012 R2 non è identico a quello in Windows Server 2012.

## <a name="windows-server-2016"></a>Windows Server 2016

Dopo la versione iniziale di questa istruzione di supporto, il sistema operativo Windows Server 2016 è stato rilasciato. Questo documento è stato aggiornato per chiarire il supporto Microsoft per VB6 in Windows Server 2016.

Il runtime VB6 spedirà e sarà supportato in Windows Server 2016 per la durata del sistema operativo. File di runtime di Visual Basic 6.0 continuano a essere solo a 32 bit, e tutti i componenti devono essere ospitati in processi di applicazione a 32 bit. Gli sviluppatori di essere considerata la storia di supporto per Windows Server 2016 non è identico a quello in Windows Server 2012 R2.

## <a name="supported-windows-operating-system-versions"></a>Versioni supportate del sistema operativo Windows

In questa sezione fornisce informazioni aggiuntive per i sistemi operativi che offrono un certo livello di supporto per VB6. 

|Sistema operativo Windows|VB6 Runtime supportate</br>I file di Windows dispongono di supporto?|VB6 Supportato Rutime</br>File estesi</br>Per distribuire l'applicazione è disponibile supporto?| VB6 IDE ha supporto?|
|---|---|---|---|
|Windows 10, tutte le edizioni a 32 bit|Sì *|Sì *|No|
|Windows 10, tutte le edizioni a 64 bit (WOW solo)|Sì * </br> applicazioni in esecuzione solo nella modalità WOW a 32 bit|Sì* </br> applicazioni in esecuzione solo nella modalità WOW a 32 bit|No|
|Windows 8.1, tutte le edizioni a 32 bit|Sì *|Sì *|No|
| Windows 8.1, tutte le edizioni a 64 bit (WOW solo)|Sì * </br> applicazioni in esecuzione solo nella modalità WOW a 32 bit|Sì* </br> applicazioni in esecuzione solo nella modalità WOW a 32 bit|No|
|Windows 7, tutte le edizioni a 32 bit|Sì *|Sì *|No|
|Windows 7, tutte le edizioni a 64 bit (WOW solo)|Sì * </br> applicazioni in esecuzione solo nella modalità WOW a 32 bit|Sì * </br> applicazioni in esecuzione solo nella modalità WOW a 32 bit|No|
|Windows Server 2016, tutte le edizioni a 64 bit (WOW solo)|Sì* </br> applicazioni in esecuzione solo nella modalità WOW a 32 bit|Sì* </br> applicazioni in esecuzione solo nella modalità WOW a 32 bit|No|
|Windows Server 2012 R2, tutte le edizioni a 64 bit (WOW solo)<br>Windows Server 2012, tutte le edizioni a 64 bit (WOW solo)|Sì* </br> applicazioni in esecuzione solo nella modalità WOW a 32 bit|Sì* </br> applicazioni in esecuzione solo nella modalità WOW a 32 bit|No|
|Windows Server 2008 R2 x64 tutte le edizioni (solo WOW)</br>Tutto x64 Windows Server 2008 Edition (solo WOW)|Sì * </br> applicazioni in esecuzione solo nella modalità WOW a 32 bit|Sì * </br> applicazioni in esecuzione solo nella modalità WOW a 32 bit|No|
|Windows Server 2008, tutte le edizioni a 32 bit|Sì *|Sì *|No|


> [!NOTE]
> &#42;  Supporto di runtime VB6 è limitato dal ciclo di vita di supporto di Windows.  Ad esempio, se il sistema operativo di destinazione è il supporto esteso, VB6 non può avere un livello superiore di supporto di supporto esteso.  Il [Windows supporta informativa del ciclo di vita](https://support.microsoft.com/en-us/help/13853/windows-lifecycle-fact-sheet) contiene del ciclo di vita ulteriori informazioni sulle versioni di Windows precedente e corrente.

## <a name="visual-basic-60-runtime-usage-inside-vba-and-office"></a>Utilizzo di runtime di Visual Basic 6.0 in VBA e Office

Visual Basic, Applications Edition o VBA, è una tecnologia distinct comunemente utilizzata per l'automazione di applicazioni e le macro all'interno di altre applicazioni, in genere all'interno delle applicazioni di Microsoft Office. VBA viene fornito come parte di Office e pertanto il supporto per VBA è governato dai criteri di supporto di Office. Tuttavia, esistono situazioni in cui è utilizzato VBA per chiamare o ospitare controlli e i file binari di runtime di Visual Basic 6.0. In questi casi, Visual Basic 6.0 supporta i file di runtime nel sistema operativo e l'elenco di file estesi sono supportati anche se utilizzati in un ambiente supportato da VBA.

Per gli scenari di runtime VB6 devono essere supportati all'interno di VBA, tutti gli elementi seguenti devono essere soddisfatte:

- La versione del sistema operativo host per il runtime di Visual Basic è ancora supportata.
- La versione di host di Office per VBA è ancora supportata.
- I file di runtime in questione sono ancora supportati.

## <a name="visual-basic-script-vbscript"></a>Visual Basic Script (VBScript)

VBScript è correlato a Visual Basic 6.0 e sull'istruzione di supporto. Tuttavia, VBScript è attualmente shipping come parte di Windows 7, Windows 8.1, Windows 10, Windows Server 2008 R2, Windows Server 2012, inclusi R2 e Windows Server 2016 incluso e viene gestito tramite il ciclo di vita del supporto del sistema operativo.

## <a name="third-party-components"></a>Componenti di terze parti

Microsoft è in grado di fornire supporto per i componenti di terze parti, ad esempio OCX/controllo ActiveX. I clienti sono invitati a contattare il fornitore del controllo originale per informazioni dettagliate sul supporto per tali componenti.

## <a name="reporting-issues-with-vb-60-applications-running-on-windows"></a>Segnalare eventuali problemi con le applicazioni Visual Basic 6.0 in esecuzione in Windows

Gli sviluppatori per la pianificazione Visual Basic 6.0 con uno dei sistemi operativi Windows elencati devono installare il sistema operativo e iniziare a testare la compatibilità dell'applicazione utilizzando i test di accettazione dell'applicazione originale.

Se si riscontra un problema con l'applicazione di Visual Basic 6.0 in esecuzione in uno dei sistemi operativi Windows elencati, seguire i canali di supporto per segnalare il problema.

## <a name="supported-and-shipping-in-windows"></a>Windows supportati e di spedizione in

| | | | |
|---|---|---|---|
|atl.dll|         msadcor.dll|     msorcl32.dll|   ole2.dll|
|asycfilt.dll|    msadcs.dll|      msvbvm60.dll|   ole32.dll|
|comcat.dll|      msadds.dll|      msvcirt.dll|    oleaut32.dll|
|compobj.dll|     msaddsr.dll|     msvcrt.dll|     oleaut32.dll|
|dbnmpntw.dll|    msader15.dll|    msvcrt40.dll|   oledb32.dll|
|dcomcnfg.exe|    msado15.dll|     mtxdm.dll|      oledb32r.dll|
|dllhost.exe|     msador15.dll|    mtxoci.dll|     oledlg.dll|
|ds16gt.dll|      msadrh15.dll|    odbc16gt.dll|   olepro32.dll|
|ds32gt.dll|      mscpxl32.dll|    odbc32.dll|     olethk32.dll|
|expsrv.dll|      msdadc.dll|      odbc32gt.dll|   regsvr32.exe|
|hh.exe|          msdaenum.dll|    odbcad32.exe|   rpcns4.dll|
|hhctrl.ocx|      msdaer.dll|      odbccp32.cpl|   rpcrt4.dll|
|imagehlp.dll|    msdaora.dll|     odbccp32.dll|   scrrun.dll|
|iprop.dll|       msdaosp.dll|     odbccr32.dll|   secur32.dll|
|itircl.dll|      msdaprst.dll|    odbccu32.dll|   simpdata.tlb|
|itss.dll|        msdaps.dll|      odbcint.dll|    sqloledb.dll|
|mfc40.dll|       msdasc.dll|      odbcji32.dll|   sqlsrv32.dll|
|mfc42.dll|       msdasql.dll|     odbcjt32.dll|   stdole2.tlb|
|mfc42enu.dll|    msdasqlr.dll|    odbctrac.dll|   stdole32.tlb|
|msadce.dll|      msdatsrc.tlb|    oddbse32.dll|   storage.dll|
|msadcer.dll|     msdatt.dll|      odexl32.dll|    vbajet32.dll|
|msadcf.dll|      msdfmap.dll|     odfox32.dll|    vfpodbc.dll|
|msadcfr.dll|     msdfmap.ini|     odpdx32.dll|                |
|msadco.dll|      msjtes40.dll|    odtext32.dll|               |

## <a name="supported-runtime-files-to-distribute-with-your-application"></a>File di runtime supportate da distribuire con l'applicazione

| | | | |
|---|---|---|---|
|comct232.ocx |msbind.dll   |msdbrptr.dll  |msstdfmt.dll| 
|comct332.ocx |mscdrun.dll  |msflxgrd.ocx  |msstkprp.dll| 
|comctl32.ocx |mschrt20.ocx |mshflxgd.ocx  |mswcrun.dll|  
|comdlg32.ocx |mscomct2.ocx |mshtmpgr.dll  |mswinsck.ocx| 
|dbadapt.dll  |mscomctl.ocx |msinet.ocx    |picclp32.ocx| 
|dbgrid32.ocx |mscomm32.ocx |msmapi32.ocx  |richtx32.ocx| 
|dblist32.ocx |msdatgrd.ocx |msmask32.ocx  |sysinfo.ocx|  
|mci32.ocx    |msdatlst.ocx |msrdc20.ocx   |tabctl32.ocx| 
|msadodc.ocx  |msdatrep.ocx |msrdo20.dll

## <a name="unsupported-but-supported-and-compatible-updates-or-upgrades-are-available"></a>Non è supportato, ma sono disponibili aggiornamenti supportati e compatibili

| | | | |
|---|---|---|---|
|dao350.dll|   msexch35.dll| msjter35.dll| msrepl35.dll|
|mdac_typ.exe| msexcl35.dll| msjtor35.dll| mstext35.dll|
|mschart.ocx|  msjet35.dll|  msltus35.dll| msxbse35.dll|
|msdaerr.dll|  msjint35.dll| mspdox35.dll| odbctl32.dll|
|msdatl2.dll|  msjt4jlt.dll| msrd2x35.dll| oledb32x.dll|

## <a name="unsupported-runtime-files"></a>File di runtime non supportato

| | | | |
|---|---|---|---|
|anibtn32.ocx| spin32.ocx|   rpcltscm.dll|  rdocurs.dll|
|graph32.ocx|  gauge32.ocx|  rpcmqcl.dll|   vbar332.dll|
|keysta32.ocx| gswdll32.dll| rpcmqsvr.dll|  visdata.exe|
|autmgr32.exe| ciscnfg.exe|  rpcss.exe|     vsdbflex.srg|
|autprx32.dll| olecnv32.dll| dbmsshrn.dll|  threed32.ocx|
|racmgr32.exe| rpcltc1.dll|  dbmssocn.dll|  MSWLess.ocx|
|racreg32.dll| rpcltc5.dll|  windbver.exe|  tlbinf32.dll|
|grid32.ocx|   rpcltccm.dll| msderun.dll|   triedit.dll|
|msoutl32.ocx| rpclts5.dll|  odkob32.dll|

## <a name="localization-support-binaries"></a>File binari di supporto di localizzazione

I file binari seguenti sono necessari per supportare le applicazioni Visual Basic 6.0 in esecuzione nelle versioni localizzate del sistema operativo Windows. Sono supportati, ma non sono disponibili in Windows. Questi file devono essere forniti con l'installazione dell'applicazione.

### <a name="supported-runtime-files-to-distribute-with-your-application"></a>File di runtime supportate da distribuire con l'applicazione

|JPN|KOR|CHT|CHS|
|---|---|---|---|
|mfc42jpn.dll|  mfc42kor.dll|  mfc42cht.dll|  mfc42chs.dll|
|scrrnjp.dll|   scrrnko.dll|   scrrncht.dll|  scrrnchs.dll|
|vb6jp.dll|     vb6ko.dll|     vb6cht.dll|    vb6chs.dll|
|cmct2jp.dll|   cmct2ko.dll|   cmct2cht.dll|  cmct2chs.dll|
|cmct3jp.dll|   cmct3ko.dll|   cmct3cht.dll|  mscc2chs.dll|
|mscc2jp.dll|   mscc2ko.dll|   mscc2cht.dll|  cmct3chs.dll|
|cmctljp.dll|   cmctlko.dll|   cmctlcht.dll|  cmctlchs.dll|
|cmdlgjp.dll|   cmdlgko.dll|   mscmccht.dll|  mscmcchs.dll|
|mscmcjp.dll|   mscmcko.dll|   cmdlgcht.dll|  cmdlgchs.dll|
|dbgrdjp.dll|   dbgrdko.dll|   dbgrdcht.dll|  dbgrdchs.dll|
|dblstjp.dll|   dblstko.dll|   dblstcht.dll|  dblstchs.dll|
|mcijp.dll|     mciko.dll|     mcicht.dll|    mcichs.dll|
|msadnjp.dll|   msadnko.dll|   msadncht.dll|  msadnchs.dll|
|adodcjp.dll|   adodcko.dll|   adodccht.dll|  adodcchs.dll|
|mschtjp.dll|   mschtko.dll|   mschtcht.dll|  mschtchs.dll|
|msch2jp.dll|   msch2ko.dll|   msch2cht.dll|  msch2chs.dll|
|mscomjp.dll|   mscomko.dll|   mscomcht.dll|  mscomchs.dll|
|datgdjp.dll|   datgdko.dll|   datgdcht.dll|  datgdchs.dll|
|datlsjp.dll|   datlsko.dll|   datlscht.dll|  datlschs.dll|
|datrpjp.dll|   datrpko.dll|   datrpcht.dll|  datrpchs.dll|
|dbrprjp.dll|   dbrprko.dll|   dbrprcht.dll|  dbrprchs.dll|
|flxgdjp.dll|   flxgdko.dll|   flxgdcht.dll|  flxgdchs.dll|
|mshfgjpn.dll|  mshfgkor.dll|  mshfgcht.dll|  mshfgchs.dll|
|htmprjp.dll|   htmprko.dll|   htmprcht.dll|  htmprchs.dll|
|inetjp.dll|    inetko.dll|    inetcht.dll|   inetchs.dll|
|msmpijp.dll|   msmpiko.dll|   msmpicht.dll|  msmpichs.dll|
|msmskjp.dll|   msmskko.dll|   msmskcht.dll|  msmskchs.dll|
|rdc20jp.dll|   rdc20ko.dll|   rdc20cht.dll|  rdc20chs.dll|
|rdo20jp.dll|   rdo20ko.dll|   rdo20cht.dll|  rdo20chs.dll|
|stdftjp.dll|   stdftko.dll|   stdftcht.dll|  stdftchs.dll|
|mswcrjp.dll|   mswcrko.dll|   mswcrcht.dll|  mswcrchs.dll|
|winskjp.dll|   winskko.dll|   winskcht.dll|  winskchs.dll|
|pcclpjp.dll|   pcclpko.dll|   pcclpcht.dll|  pcclpchs.dll|
|rchtxjp.dll|   rchtxko.dll|   rchtxcht.dll|  rchtxchs.dll|
|sysinjp.dll|   sysinko.dll|   sysincht.dll|  sysinchs.dll|
|tabctjp.dll|   tabctko.dll|   tabctcht.dll|  tabctchs.dll|

|ITA|FRA|ESP|DEU|
|---|---|---|---|
|mfc42ita.dll|  mfc42fra.dll|  mfc42esp.dll|  mfc42deu.dll|
|scrrnit.dll|   scrrnfr.dll|   scrrnes.dll|   scrrnde.dll|
|vb6it.dll|     vb6fr.dll|     vb6es.dll|     vb6de.dll|
|cmct2it.dll|   cmct2fr.dll|   cmct2es.dll|   cmct2de.dll|
|mscc2it.dll|   mscc2fr.dll|   mscc2es.dll|   mscc2de.dll|
|cmct3it.dll|   cmct3fr.dll|   cmct3es.dll|   cmct3de.dll|
|cmctlit.dll|   cmctlfr.dll|   cmctles.dll|   cmctlde.dll|
|mscmcit.dll|   mscmcfr.dll|   mscmces.dll|   mscmcde.dll|
|cmdlgit.dll|   cmdlgfr.dll|   cmdlges.dll|   cmdlgde.dll|
|dbgrdit.dll|   dbgrdfr.dll|   dbgrdes.dll|   dbgrdde.dll|
|dblstit.dll|   dblstfr.dll|   dblstes.dll|   dblstde.dll|
|mciit.dll|     mcifr.dll|     mcies.dll|     mcide.dll|
|msadnit.dll|   msadnfr.dll|   msadnes.dll|   msadnde.dll|
|adodcit.dll|   adodcfr.dll|   adodces.dll|   adodcde.dll|
|mschtit.dll|   mschtfr.dll|   mschtes.dll|   mschtde.dll|
|msch2it.dll|   msch2fr.dll|   msch2es.dll|   msch2de.dll|
|mscomit.dll|   mscomfr.dll|   mscomes.dll|   mscomde.dll|
|atgdit.dll|    datgdfr.dll|   datgdes.dll|   datgdde.dll|
|datlsit.dll|   datlsfr.dll|   datlses.dll|   datlsde.dll|
|datrpit.dll|   datrpfr.dll|   datrpes.dll|   datrpde.dll|
|dbrprit.dll|   dbrprfr.dll|   dbrpres.dll|   dbrprde.dll|
|flxgdit.dll|   flxgdfr.dll|   flxgdes.dll|   flxgdde.dll|
|mshfgit.dll|   mshfgfr.dll|   mshfges.dll|   mshfgde.dll|
|htmprit.dll|   htmprfr.dll|   htmpres.dll|   htmprde.dll|
|inetit.dll|    inetfr.dll|    inetes.dll|    inetde.dll|
|msmpiit.dll|   msmpifr.dll|   msmpies.dll|   msmpide.dll|
|msmskit.dll|   msmskfr.dll|   msmskes.dll|   msmskde.dll|
|rdc20it.dll|   rdc20fr.dll|   rdc20es.dll|   rdc20de.dll|
|rdo20it.dll|   rdo20fr.dll|   rdo20es.dll|   rdo20de.dll|
|stdftit.dll|   stdftfr.dll|   stdftes.dll|   stdftde.dll|
|mswcrit.dll|   mswcrfr.dll|   mswcres.dll|   mswcrde.dll|
|winskit.dll|   winskfr.dll|   winskes.dll|   winskde.dll|
|pcclpit.dll|   pcclpfr.dll|   pcclpes.dll|   pcclpde.dll|
|rchtxit.dll|   rchtxfr.dll|   rchtxes.dll|   rchtxde.dll|
|sysinit.dll|   sysinfr.dll|   sysines.dll|   sysinde.dll|
|tabctit.dll|   tabctfr.dll|   tabctes.dll|   tabctde.dll|

