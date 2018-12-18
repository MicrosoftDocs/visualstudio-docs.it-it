---
title: Trovare le modifiche apportate al codice e altri elementi della cronologia con CodeLens | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a1123d1c557f6e7f01eb98e668b4f13785ee6893
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="find-code-changes-and-other-history-with-codelens"></a>Trovare le modifiche apportate al codice e altri elementi della cronologia con CodeLens

CodeLens consente di rimanere concentrati sulle proprie attività mentre si cercano informazioni sul codice senza uscire dall'editor. È infatti possibile trovare i riferimenti e le modifiche apportate al codice, i bug collegati, gli elementi di lavoro, le revisioni del codice e gli unit test.

> [!NOTE]
> CodeLens è disponibile solo nelle edizioni Visual Studio Enterprise e Visual Studio Professional. Non è disponibile nell'edizione Community di Visual Studio.  

Vedere dove e come vengono usate le singole parti di codice nella soluzione:  

![Indicatori CodeLens nell'editor del codice](../ide/media/codelensoverview.png "CodeLensOverview")  

È anche possibile contattare il team in merito alle modifiche al codice senza uscire dall'editor:  

![CodeLens &#45; Contattare il proprio team](../ide/media/codelensovervew2.png "CodeLensOvervew2")  

Per scegliere gli indicatori da visualizzare o per abilitare o disabilitare CodeLens, passare a **Strumenti**, **Opzioni**, **Editor di testo**, **Tutti i linguaggi**, **CodeLens**.  

## <a name="FindReferences"></a> Individuare i riferimenti del codice

Sono necessari:

-  Visual Studio Enterprise e Visual Studio Professional

-  Codice C# o Visual Basic

Scegliere l'indicatore dei **riferimenti** (**Alt + 2**). Se i **riferimenti sono pari a 0**, non sono disponibili riferimenti da codice C# o Visual Basic. Questo non include riferimenti da altri elementi, ad esempio file XAML e ASPX.

![CodeLens &#45; Scegliere l'indicatore dei riferimenti](../ide/media/codelensviewreferenceslist.png "CodeLensViewReferencesList")  

Per visualizzare il codice con riferimenti, posizionare il mouse sul riferimento.  

![CodeLens &#45; Posizionare il puntatore su un riferimento](../ide/media/codelensviewreferencespeekreference.png "CodeLensViewReferencesPeekReference")  

Per aprire il file con il riferimento, fare doppio clic sul riferimento.  

Per vedere le relazioni tra il codice e i riferimenti relativi, [creare una mappa dei codici](../modeling/map-dependencies-across-your-solutions.md) e scegliere **Mostra tutti i riferimenti** nel menu di scelta rapida della mappa del codice.

![CodeLens &#45; Riferimenti nella mappa del codice](../ide/media/codelensmappedreferences.png "CodeLensMappedReferences")  

## <a name="FindCodeHistory"></a> Individuare la cronologia e gli elementi collegati del codice

È possibile esaminare la cronologia del codice per scoprire cosa è successo oppure esaminare le modifiche prima che vengano unite nel codice per ottenere altre informazioni sull'eventuale impatto di modifiche in altri rami sul codice.

Sono necessari:

- Visual Studio Enterprise e Visual Studio Professional

- Team Foundation Server 2013 o versioni successive, Visual Studio Team Services o Git

- [Lync 2010 o versioni successive oppure Skype for Business](https://technet.microsoft.com/office/dn788773)per contattare il team dall'editor di codice.

Per il codice C# o Visual Basic archiviato con il controllo della versione di Team Foundation (TFVC) o Git, si ricevono dettagli CodeLens a livello di classe e metodo (indicatori *a livello di elemento codice*). Se il repository Git è ospitato in TfGit, è anche possibile ottenere collegamenti negli elementi di lavoro TFS.  

![Indicatori a livello di elemento di codice](../ide/media/codelenselementlevelindicators.png "CodeLensElementLevelIndicators")  

Per tutti gli altri tipi di file che si possono aprire nell'editor di Visual Studio, si ricevono dettagli CodeLens per l'intero file in un'unica posizione nella parte inferiore della finestra (indicatori*a livello di file* ).

![Indicatori CodeLens a livello di file](../ide/media/almcodelensfilelevelindicators.png "ALMCodeLensFileLevelIndicators")  

Per usare la tastiera per la selezione degli indicatori, tenere premuto il testo **ALT** per visualizzare i tasti numerici correlati.  

![Premere ALT per visualizzare i numeri di accesso della tastiera](../ide/media/codelensaltkeyindicators.png "CodeLensAltKeyIndicators")  

### <a name="find-changes-in-your-code"></a>Individuare le modifiche nel codice

Trovare l'utente che ha modificato il codice C# o Visual Basic e le modifiche apportate, negli indicatori a livello di codice elemento. Questo è ciò che viene visualizzato quando si usa il controllo della versione di Team Foundation (TFVC) in Team Foundation Server o Visual Studio Team Services.  

![CodeLens: ottenere la cronologia delle modifiche per il codice nel controllo della versione di Team Foundation](../ide/media/codelenscodechanges.png "CodeLensCodeChanges")  

Il periodo di tempo predefinito è 12 secondi. Se il codice è archiviato in Team Foundation Server, è possibile modificarlo eseguendo il [comando TFSConfig](/vsts/tfs-server/command-line/tfsconfig-cmd) con il [comando CodeIndex](../ide/codeindex-command.md) e il flag **/indexHistoryPeriod** .

Per visualizzare una cronologia dettagliata di tutte le modifiche, comprese quelle di più di un anno fa, scegliere **Mostra tutte le modifiche apportate ai file**.  

![Visualizzare tutte le modifiche apportate al codice](../ide/media/codelensshowsallchanges.png "CodeLensShowsAllChanges")  

Verrà visualizzata la finestra Cronologia per i set di modifiche.  

![Finestra Cronologia per tutte le modifiche al codice](../ide/media/codelenscodechangeshistory.png "CodeLensCodeChangesHistory")  

Quando i file si trovano in un repository Git e si sceglie l'indicatore di modifiche a livello di elemento di codice, questo è ciò che viene visualizzato.  

![CodeLens: ottenere la cronologia delle modifiche per il codice nel repository Git](../ide/media/codelenscodechangesgit.png "CodeLensCodeChangesGit")  

Individuare le modifiche di un intero file (esclusi i file C# e Visual Basic) negli indicatori a livello di file nella parte inferiore della finestra.  

![CodeLens: ottenere i dettagli sul file di codice](../ide/media/codelensfilelevel.png "CodeLensFileLevel")  

Per ottenere altre informazioni su una modifica, fare clic con il pulsante destro del mouse su tale elemento. A seconda se si utilizza TFVC o Git si otterrà una serie di opzioni per confrontare le versioni del file, visualizzare i dettagli e tenere traccia delle modifiche, ottenere la versione selezionata del file e inviare un messaggio di posta elettronica all'autore della modifica. Alcuni di dettagli vengono visualizzati in Team Explorer.  

È possibile anche visualizzare l'utente che ha modificato il codice nel tempo, consentendo di individuare i criteri delle modifiche del team e di valutarne l'impatto.  

![CodeLens: visualizzare la cronologia delle modifiche del codice sotto forma di grafico](../ide/media/codelens.png "CodeLens")  

#### <a name="find-changes-in-your-current-branch"></a>Individuare le modifiche nel branch corrente

Si supponga che il team sia costituito da più branch, ovvero un branch principale e un branch di sviluppo figlio, per ridurre il rischio di danneggiare la stabilità del codice:  

![CodeLens: individuare quando il codice è stato sottoposto a branching](../ide/media/codelensfirstbranchconceptual.png "CodeLensFirstBranchConceptual")  

Individuare il numero di persone che hanno modificato il codice e il numero di modifiche apportate (**ALT + 6**) nel branch principale:  

![CodeLens: individuare il numero di modifiche nel branch](../ide/media/codelensbranchchanges.png "CodeLensBranchChanges")  

#### <a name="find-when-your-code-was-branched"></a>Individuare il punto in cui il codice è stato sottoposto a branching

Passare al codice nel branch figlio, ad esempio, in questo caso il branch relativo allo sviluppo. Scegliere l'indicatore delle modifiche (**ALT + 6**):  

![CodeLens: individuare quando il codice è stato sottoposto a branching](../ide/media/codelensfirstbranchscreenshot.png "CodeLensFirstBranchScreenshot")  

#### <a name="find-incoming-changes-from-other-branches"></a>Individuare le modifiche in arrivo da altri branch

![CodeLens: individuare le modifiche al codice in altri branch](../ide/media/codelensbranchchangecheckinconceptual.png "CodeLensBranchChangeCheckinConceptual")  

… ad esempio questa correzione di bug nel branch relativo allo sviluppo:

![CodeLens: modifica verificata in un altro branch](../ide/media/codelensbranchchangedevscreenshot.png "CodeLensBranchChangeDevScreenshot")  

È possibile esaminare questa modifica senza uscire dal branch corrente (principale):  

![CodeLens: visualizzare la modifica proveniente da un altro branch](../ide/media/codelensbranchchangemainscreenshot.png "CodeLensBranchChangeMainScreenshot")  

#### <a name="find-when-changes-got-merged"></a>Scoprire quando sono state unite le modifiche

Sarà quindi possibile verificare le modifiche incluse nel branch:  

![CodeLens &#45; Unione delle modifiche tra branch](../ide/media/codelensbranchmergedconceptual.png "CodeLensBranchMergedConceptual")  

Ad esempio, il codice nel branch principale include ora la correzione di bug dal branch relativo allo sviluppo:  

![CodeLens &#45; Unione delle modifiche tra branch](../ide/media/codelensbranchmergedscreenshot.png "CodeLensBranchMergedScreenshot")  

#### <a name="compare-an-incoming-change-with-your-local-version-shift--f10"></a>Confrontare una modifica in arrivo con la versione locale (MAIUSC + F10)

![CodeLens: confronto della modifica in arrivo con quella locale](../ide/media/codelensbranchincomingchangemenu.png "CodeLensBranchIncomingChangeMenu")  

È anche possibile fare doppio clic sull'insieme di modifiche.

#### <a name="what-do-the-icons-mean"></a>Significato delle icone

|**Icona**|**Origine della modifica**|  
|--------------|-----------------------------------------|  
|![CodeLens: icona di modifica da branch corrente](../ide/media/codelensbranchcurrenticon.png "CodeLensBranchCurrentIcon")|Branch corrente|  
|![CodeLens &#45; Icona di modifica da branch padre](../ide/media/codelensbranchparenticon.png "CodeLensBranchParentIcon")|Branch padre|  
|![CodeLens: icona di modifica da branch figlio](../ide/media/codelensbranchchildicon.png "CodeLensBranchChildIcon")|Branch figlio|  
|![CodeLens &#45; Icona di modifica da branch peer](../ide/media/codelensbranchpeericon.png "CodeLensBranchPeerIcon")|Branch peer|  
|![CodeLens &#45; Icona di modifica da branch più lontano ](../ide/media/codelensbranchfurtherawayicon.png "CodeLensBranchFurtherAwayIcon")|Branch più lontano rispetto a un branch padre, figlio o peer|  
|![CodeLens: icona di unione da branch padre](../ide/media/codelensbranchmergefromparenticon.png "CodeLensBranchMergeFromParentIcon")|Unione dal branch padre in un branch figlio|
|![CodeLens: icona di unione da branch figlio](../ide/media/codelensbranchmergefromchildicon.png "CodeLensBranchMergeFromChildIcon")|Unione da un branch figlio nel branch padre|  
|![CodeLens: icona di unione da branch non correlato](../ide/media/codelensbranchmergefromunrelatedicon.png "CodeLensBranchMergeFromUnrelatedIcon")|Unione da un branch non correlato (unione senza base)|  

### <a name="find-linked-work-items"></a>Individuare elementi di lavoro collegati

![CodeLens &#45; Trovare elementi di lavoro per un codice specifico](../ide/media/codelensworkitems.png "CodeLensWorkItems")  

### <a name="find-linked-code-reviews"></a>Individuare revisioni del codice collegate

![CodeLens &#45; Visualizzare richieste di revisione del codice](../ide/media/codelenscodereviews.png "CodeLensCodeReviews")  

### <a name="find-linked-bugs"></a>Individuare bug collegati

![CodeLens &#45; Trovare bug collegati agli insiemi di modifiche](../ide/media/codelensbugschangesets.png "CodeLensBugsChangesets")  

### <a name="contact-the-owner-of-an-item"></a>Contattare il proprietario di un elemento

![Contattare il proprietario di un elemento](../ide/media/codelenscontactitemowner.png "CodeLensContactItemOwner")  

Aprire il menu di scelta rapida di un elemento per visualizzare le opzioni di contatto. Se è installato Lync o Skype per Business, è possibile visualizzare queste opzioni:  

![Opzioni di contatto per un elemento](../ide/media/codelensitemcontactmenu.png "CodeLensItemContactMenu")  

##  <a name="FindRunUnitTests"></a> Trovare unit test per il codice

Informazioni sugli unit test disponibili per il proprio codice senza la necessità di aprire Test Explorer. Sono necessari:  

-   Visual Studio Enterprise e Visual Studio Professional  
  
-   Codice C# o Visual Basic  
  
-   Un [progetto unit test](../test/unit-test-your-code.md) che includa unit test per il codice dell'applicazione  
  
1.  Visualizzare il codice dell'applicazione contenente unit test.  
  
2.  Visualizzare i test per tale codice (**ALT + 3**).  
  
     ![CodeLens &#45; Scegliere lo stato del test nell'editor di codice](../ide/media/codelenschoosetestindicator.png "CodeLensChooseTestIndicator")  
  
3.  Se viene visualizzata un'icona di avviso ![CodeLens &#45; Avviso di unit test non ancora in esecuzione](../ide/media/codelenstestwarningicon.png "CodeLensTestWarningIcon"), eseguire i test.  
  
     ![CodeLens &#45; Visualizzare gli unit test non ancora in esecuzione](../ide/media/codelenstestsnotyetrun.png "CodeLensTestsNotYetRun")  
  
4.  Per esaminare la definizione di un test, fare doppio clic sull'elemento di test nella finestra dell’indicatore CodeLens per aprire il file di codice nell'editor.  
  
     ![CodeLens &#45; Passare alla definizione di unit test](../ide/media/codelensunittestdefinition.png "CodeLensUnitTestDefinition")  
  
5.  Esaminare i risultati del test. Scegliere l'indicatore di stato dei test (![CodeLens &#45; Icona test non riuscito](../ide/media/codelenstestfailedicon.png "CodeLensTestFailedIcon") o ![CodeLens &#45; Icona unit test riuscito](../ide/media/codelenstestpassedicon.png "CodeLensTestPassedIcon")), oppure premere **ALT + 1**.  
  
     ![CodeLens &#45; Visualizzare il risultato dello unit test](../ide/media/codelensunittestresult.png "CodeLensUnitTestResult")  
  
6.  Per vedere quante persone hanno modificato il test, gli autori delle modifiche o il numero di modifiche apportate al test, [Individuare la cronologia e gli elementi collegati del codice](#FindCodeHistory).

##  <a name="QA"></a> Domande e risposte

###  <a name="ChangeOrTurnOff"></a> D: Come si attiva o disattiva CodeLens o si scelgono gli indicatori da visualizzare?

**R:**  È possibile attivare o disattivare tutti gli indicatori, ad eccezione di Riferimenti. Passare a **Strumenti**, **Opzioni**, **Editor di testo**, **Tutti i linguaggi**, **CodeLens**.  
  
 Quando gli indicatori sono attivati, è possibile anche aprire le opzioni CodeLens dagli indicatori.  
  
 ![CodeLens &#45; Attivare o disattivare gli indicatori](../ide/media/codelensturnoffonindicatorsfromcode.png "CodeLensTurnOffOnIndicatorsFromCode")  
  
 Attivare gli indicatori CodeLens a livello di file e disattivare l’utilizzo delle icone con la freccia di espansione nella parte inferiore della finestra dell'editor.  
  
 ![Attivare e disattivare gli indicatori a livello di file](../ide/media/codelensfilelevelonandoff.png "CodeLensFileLevelOnAndOff")  
  
###  <a name="NoIndicators"></a> D: Dove si trova CodeLens?

**R:** CodeLens viene visualizzato nel codice C# e Visual Basic a livello di metodo, classe, indicizzatore e proprietà. CodeLens viene visualizzato a livello di file per tutti gli altri tipi di file.

- Assicurarsi che CodeLens sia attivato. Passare a **Strumenti**, **Opzioni**, **Editor di testo**, **Tutti i linguaggi**, **CodeLens**.  

- Se il codice è archiviato in TFS, assicurarsi che l'indicizzazione del codice sia attivata usando il [comando CodeIndex](../ide/codeindex-command.md) con il [comando Config di TFS](/vsts/tfs-server/command-line/tfsconfig-cmd).

- Gli indicatori TFS vengono visualizzati solo quando gli elementi di lavoro sono collegati al codice e quando si dispone delle autorizzazioni per aprire gli elementi di lavoro collegati. [Confermare di disporre delle autorizzazioni dei membri del team](/vsts/work/scale/multiple-teams).

- Gli indicatori di unit test non vengono visualizzati quando il codice dell'applicazione non contiene unit test. Gli indicatori di stato del test vengono visualizzati automaticamente nei progetti di test. Se si è certi che il codice dell'applicazione include di unit test, ma gli indicatori del test non vengono visualizzati, provare a compilare la soluzione (**CTRL+MAIUSC+B**).

### <a name="q-why-dont-i-see-the-work-item-details-for-a-commit"></a>D: Perché non vengono visualizzati i dettagli degli elementi di lavoro per un commit?

**R:** Questo problema potrebbe verificarsi perché CodeLens non riesce a trovare gli elementi di lavoro in TFS. Verificare di essere connessi al progetto team con quelli elementi di lavoro e di avere le autorizzazioni necessarie per visualizzare gli elementi di lavoro. Questa situazione potrebbe anche verificarsi se la descrizione di commit presenta informazioni non corrette sugli ID elemento di lavoro in TFS.  

###  <a name="NoLync"></a> D: Perché gli indicatori Lync o Skype non sono visualizzati?

**R:** Gli indicatori non vengono visualizzati quando non si è connessi a Lync oppure a Skype for Business, quando non uno di questi programmi non è installato o la configurazione non è supportata. È comunque possibile inviare messaggi di posta elettronica:  

![CodeLens &#45; Contattare il proprietario dell'insieme di modifiche tramite posta elettronica](../ide/media/codelenscodesendmailchangesetnolync1.png "CodeLensCodeSendMailChangesetNoLync1")  

 **Quali configurazioni di Lync e Skype sono supportate?**

-   Skype per Business (32 bit o 64 bit)  

-   Lync 2010 o nelle versioni successive da solo (32 bit o 64 bit), ma non Lync Basic 2013 con Windows 8.1  

CodeLens non supporta l'installazione di versioni di Lync o Skype diverse. Potrebbero non essere stati localizzati per tutte le versioni localizzate di Visual Studio.  

### <a name="q-how-do-i-change-the-font-and-color-for-codelens"></a>D: Come si modifica il tipo di carattere e il colore per CodeLens?

**R:** accedere a **Strumenti**, **Opzioni**, **Ambiente**, **Tipi di carattere e colori**.  

![CodeLens &#45; Modificare le impostazioni di carattere e colore](../ide/media/codelensoptionsfontscolorssettings.png "CodeLensOptionsFontsColorsSettings")  

Per usare la tastiera:

1.  Premere **ALT+T+O** per aprire la finestra di dialogo **Opzioni** .  

2.  Premere **Freccia SU** o **Freccia GIÙ** per passare al nodo **Ambiente** , quindi premere **Freccia SINISTRA** per espandere il nodo.  

3.  Premere **Freccia GIÙ** da passare a **Tipi di carattere e colori**.  

4.  Premere **TAB** per passare all'elenco **Mostra impostazioni per** , quindi premere **Freccia GIÙ** per selezionare **CodeLens**.  

### <a name="q-can-i-move-the-codelens-heads-up-display"></a>D: È possibile spostare l'heads-up display CodeLens?

**R:** Sì, è possibile scegliere ![CodeLens &#45; Ancora come finestra](../ide/media/codelensdockwindow.png "CodeLensDockWindow") per ancorare CodeLens come una finestra.  

![Finestra Ancorare gli indicatori CodeLens](../ide/media/codelensselectdockwindow.png "CodeLensSelectDockWindow")  

![Finestra riferimenti CodeLens ancorata](../ide/media/codelensreferencesdockedwindow.png "CodeLensReferencesDockedWindow")  

### <a name="q-how-do-i-refresh-the-indicators"></a>D: come si aggiornano gli indicatori?

**R:** Dipende dall'indicatore:  

-   **Riferimenti**: questo indicatore viene aggiornato automaticamente in caso di modifica del codice. Se questo indicatore è ancorato come finestra separata, è possibile aggiornarlo manualmente qui:  

     ![CodeLens &#45; Ancorare come finestra](../ide/media/codelensviewreferencesdocked.png "CodeLensViewReferencesDocked")  

-   **Team**: aggiornare questi indicatori manualmente qui:  

     ![CodeLens &#45; Aggiornare gli indicatori](../ide/media/codelensrefreshindicatorsfromcode.png "CodeLensRefreshIndicatorsFromCode")  

-   **Test**: [Trovare unit test per il codice](#FindRunUnitTests) per aggiornare questo indicatore.  

###  <a name="LocalVersion"></a> D: Qual è la "versione locale"?

**R:** La freccia **Versione locale** punta al set di modifiche più recente nella versione locale di questo file. Quando il server ha insiemi di modifiche più recenti, vengono visualizzati sopra o sotto la freccia **Versione locale** , a seconda dell'ordine usato per ordinare gli insiemi di modifiche.

### <a name="q-can-i-manage-how-codelens-processes-code-to-show-history-and-linked-items"></a>D: È possibile gestire la modalità di elaborazione del codice in CodeLens per visualizzare la cronologia e gli elementi collegati?

**R:** Sì, se il codice è disponibile in TFS, usare il [comando CodeIndex](../ide/codeindex-command.md) con il [comando Config di TFS](/vsts/tfs-server/command-line/tfsconfig-cmd).

## <a name="see-also"></a>Vedere anche

[Scrivere codice nell'editor del codice](../ide/writing-code-in-the-code-and-text-editor.md)