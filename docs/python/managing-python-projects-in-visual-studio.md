---
title: Gestione di progetti per applicazioni Python in Visual Studio | Microsoft Docs
description: Viene illustrato lo scopo dei progetti in Visual Studio, come creare e gestire i progetti per il codice Python e vengono presentati diversi modelli di progetto disponibili per Python.
ms.custom: 
ms.date: 02/15/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: aafb2259ec4f16341abf514e9496dbb66f3cb95c
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2018
---
# <a name="python-projects"></a>Progetti Python

Per definire le applicazioni Python, si usano in genere solo file e cartelle, ma questa struttura può diventare complessa se le dimensioni delle applicazioni aumentano e interessano magari anche file generati automaticamente, JavaScript per le applicazioni Web e così via. Un progetto di Visual Studio aiuta a gestire questa complessità. Il progetto (un file `.pyproj`) identifica tutti i file di origine e di contenuto associati al progetto, contiene le informazioni di compilazione relative a ogni file, gestisce le informazioni per l'integrazione con sistemi di controllo del codice sorgente e consente di organizzare l'applicazione in componenti logici.

![Progetto Python in Esplora soluzioni](media/projects-solution-explorer.png)

I progetti vengono inoltre sempre gestiti all'interno di una *soluzione* Visual Studio, che può contenere un numero qualsiasi di progetti che fanno riferimento l'uno all'altro. Ad esempio, un progetto di Python può fare riferimento a un progetto C++ che implementa un modulo di estensione. Con questa relazione, Visual Studio genera automaticamente il progetto C++ (se necessario) quando si avvia il debug del progetto di Python. Per informazioni di carattere generale, vedere [Soluzioni e progetti in Visual Studio](../ide/solutions-and-projects-in-visual-studio.md).

In Visual Studio è disponibile un'ampia gamma di modelli di progetto Python per configurare rapidamente numerose strutture di applicazione, incluso un modello per creare un progetto da un albero delle cartelle esistente e un modello per creare un progetto pulito e vuoto. Per un indice, vedere [Modelli di progetto](#project-templates).

<a name="lightweight-usage-project-free"></a>

> [!Tip]
> Visual Studio viene eseguito correttamente con il codice Python anche senza un progetto. Ad esempio, è possibile aprire un file Python e usare le funzionalità IntelliSense, di completamento automatico e di debug facendo clic con il pulsante destro del mouse nell'editor e scegliendo **Avvia eseguendo debug/Avvia senza eseguire debug**. Dal momento che tale codice usa sempre l'ambiente globale predefinito, è però possibile notare completamenti non corretti o completamenti errati se il codice è destinato a un ambiente diverso. Visual Studio inoltre analizza tutti i file e tutti i pacchetti presenti nella cartella da cui viene aperto il singolo file e questo potrebbe causare un notevole consumo del tempo della CPU.
>
> Creare un progetto di Visual Studio da codice esistente è davvero semplicissimo, come descritto in [Creazione di un progetto da file esistenti](#creating-a-project-from-existing-files).

|   |   |
|---|---|
| ![icona della telecamera](../install/media/video-icon.png "Guardare un video") | [Guardare un video (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Getting-Python-Code-iLAv23LWE_3905918567) per un'introduzione ai progetti Python (2m 17s). |
| ![icona della telecamera](../install/media/video-icon.png "Guardare un video") | Vedere anche [Deep Dive: Using source control with Python projects](https://youtu.be/Aq8eqApnugM) (Approfondimenti: uso del controllo del codice sorgente con i progetti Python) su youtube.com (8m e 55s). |

## <a name="adding-files-assigning-a-startup-file-and-setting-environments"></a>Aggiunta di file, assegnazione di un file di avvio e impostazione degli ambienti

Durante lo sviluppo dell'applicazione è in genere necessario aggiungere al progetto nuovi file di tipi diversi. Per aggiungere tali file, è possibile fare clic con il pulsante destro del mouse sul progetto e scegliere **Aggiungi > Elemento esistente**, che consente di individuare e selezionare un file da aggiungere. È anche possibile scegliere **Aggiungi > Nuovo elemento**, che consente di visualizzare una finestra di dialogo con numerosi modelli di elemento, tra cui file Python vuoti, una classe Python, uno unit test e diversi file correlati alle applicazioni Web. È possibile esaminare queste opzioni usando un progetto di test per scoprire quali elementi sono inclusi nella propria versione di Visual Studio.

A ogni progetto Python è assegnato un file di avvio, evidenziato in grassetto in Esplora soluzioni. Si tratta del file che viene eseguito all'avvio del debug (con F5 o **Debug > Avvia debug**) oppure quando si esegue il progetto nella finestra interattiva (con MAIUSC+ALT+F5 o **Debug > Esegui progetto in Python interattivo**). Per cambiarlo, fare clic con il pulsante destro del mouse sul nuovo file e scegliere **Imposta come file di avvio**.

> [!Tip]
> Se si rimuove il file di avvio selezionato da un progetto e non si seleziona un altro file, l'esecuzione del progetto comporta la visualizzazione di una finestra di output Python che verrà nascosta quasi immediatamente. Se si verifica questo comportamento, verificare che sia stato assegnato un file di avvio. Inoltre, per mantenere aperta la finestra di output, fare clic con il pulsante destro del mouse sul progetto, selezionare **Proprietà**, selezionare la scheda **Debug**, quindi aggiungere `-i` al campo **Argomenti dell'interprete**. Questo argomento fa sì che l'interprete passi in modalità interattiva dopo il completamento di un programma, mantenendo la finestra aperta fino a quando non viene premuto CTRL+Z, INVIO per chiuderla.

Un nuovo progetto è sempre associato all'ambiente Python globale predefinito. Per associare il progetto a un altro ambiente (inclusi gli ambienti virtuali), fare clic con il pulsante destro del mouse sul nodo **Ambienti Python** nel progetto, selezionare **Aggiungi/Rimuovi ambienti Python** e selezionare quelli desiderati. Per cambiare l'ambiente attivo, fare clic con il pulsante destro del mouse sull'ambiente desiderato e scegliere **Attiva ambiente**, come illustrato di seguito. Per altre informazioni, vedere [Ambienti Python](managing-python-environments-in-visual-studio.md#selecting-an-environment-for-a-project).

![Attivazione di un ambiente per un progetto Python](media/projects-activate-environment.png)

<a name="project-types"</a>

## <a name="project-templates"></a>Modelli di progetto

In Visual Studio sono disponibili diverse opzioni per configurare un progetto Python, sia partendo da zero che da codice esistente. Per usare un modello, selezionare il comando di menu **File > Nuovo > Progetto** oppure fare clic con il pulsante destro del mouse sulla soluzione in Esplora soluzioni e scegliere **Aggiungi > Nuovo progetto**. In entrambi i casi verrà visualizzata la finestra di dialogo **Nuovo progetto** illustrata di seguito. Per visualizzare modelli specifici di Python, cercare "Python" o selezionare il nodo **Installati > Python**:

![Finestra di dialogo Nuovo progetto con modelli Python](media/projects-new-project-dialog.png)

La tabella seguente riepiloga i modelli disponibili in Visual Studio 2017 (non tutti i modelli sono disponibili nelle versioni precedenti):

| Modello | Descrizione |
| --- | --- |
| [Da codice Python esistente](#creating-a-project-from-existing-files) | Crea un progetto di Visual Studio da codice Python esistente in una struttura di cartelle.  |
| Applicazione Python | Struttura di progetto di base per una nuova applicazione Python che contiene un solo file di origine vuoto. Per impostazione predefinita, il progetto viene eseguito nell'interprete della console dell'ambiente globale predefinito, che è possibile modificare [assegnando un altro ambiente](managing-python-environments-in-visual-studio.md#selecting-an-environment-for-a-project). |
| [Servizio cloud di Azure](python-azure-cloud-service-project-template.md) | Progetto per un servizio cloud di Azure scritto in Python. |
| [Progetti Web](python-web-application-project-templates.md) | Progetti per i server Web basati su diversi framework, tra cui Bottle, Django, Flask e Flask/Jade. |
| Applicazione IronPython | È simile al modello Applicazione Python, ma usa IronPython per impostazione predefinita e abilita l'interoperabilità .NET e il debug in modalità mista con i linguaggi .NET. |
| Applicazione WPF IronPython | Struttura di progetto che usa IronPython con file XAML di Windows Presentation Foundation per l'interfaccia utente dell'applicazione. Visual Studio offre una finestra di progettazione dell'interfaccia utente XAML, il code-behind può essere scritto in Python e l'applicazione viene eseguita senza visualizzare alcuna console. |
| Pagina Web IronPython Silverlight | Progetto IronPython che viene eseguito in un browser con Silverlight. Il codice Python dell'applicazione è incluso nella pagina Web come script. Un tag di script boilerplate estrae parte del codice JavaScript che inizializza l'esecuzione di IronPython all'interno di Silverlight, da cui il codice Python può interagire con il DOM. |
| Windows Forms Application IronPython | Struttura di progetto che usa IronPython con l'interfaccia utente creata tramite il codice con Windows Forms. L'applicazione viene eseguita senza visualizzare alcuna console. |
| Applicazione in background (IoT) | Supporta la distribuzione di progetti Python per l'esecuzione nei dispositivi come servizi in background. Per altre informazioni, vedere la pagina di [Windows Dev Center dedicata a IoT](https://dev.windows.com/en-us/iot). |
| Modulo di estensione Python | Questo modello viene visualizzato in Visual C++ se sono stati installati gli **Strumenti di sviluppo nativi Python** con il carico di lavoro Python in Visual Studio 2017 (vedere [Installazione](installing-python-support-in-visual-studio.md)). Offre la struttura di base per una DLL di estensione C++, simile a quella descritta in [Creating a C++ Extension for Python](working-with-c-cpp-python-in-visual-studio.md) (Creazione di un'estensione C++ per Python). |

> [!Note]
> Poiché Python è un linguaggio interpretato, i progetti Python in Visual Studio non producono un file eseguibile autonomo come altri progetti di linguaggi compilati (ad esempio, C#). Per altre informazioni, vedere le [domande e risposte](overview-of-python-tools-for-visual-studio.md#questions-and-answers).

<a name="create-project-from-existing-files"</a>

### <a name="creating-a-project-from-existing-files"></a>Creazione di un progetto da file esistenti

> [!Important]
> Il processo descritto non sposta o copia i file di origine. Se si vuole usare una copia, per prima cosa duplicare la cartella.

[!INCLUDE[project-from-existing](includes/project-from-existing.md)]

## <a name="linked-files"></a>File collegati

Per file collegati si intendono i file importati in un progetto, ma che in genere si trovano all'esterno delle cartelle di progetto dell'applicazione. Tali file vengono visualizzati in Esplora soluzioni come file normali contraddistinti da un'icona di collegamento sovrapposta: ![Icona di file collegato](media/projects-linked-file-icon.png)

Questi file collegati vengono specificati nel file `.pyproj` usando l'elemento `<Compile Include="...">`. I file collegati sono impliciti se usano un percorso relativo al di fuori della struttura di directory o espliciti se usano i percorsi all'interno di Esplora soluzioni:

```xml
<Compile Include="..\test2.py">
    <Link>MyProject\test2.py</Link>
</Compile>
```

In presenza delle condizioni seguenti i file collegati vengono ignorati:

- Il file collegato contiene metadati Link e il percorso specificato nell'attributo Include è presente all'interno della directory di progetto.
- Il file collegato duplica un file esistente nella gerarchia del progetto
- Il file collegato contiene metadati Link e il percorso di Link è un percorso relativo esterno alla gerarchia del progetto.
- Il percorso del collegamento è completo.

### <a name="working-with-linked-files"></a>Uso dei file collegati

Per aggiungere un elemento esistente come collegamento, fare clic con il pulsante destro del mouse sulla cartella del progetto in cui aggiungere il file e quindi scegliere **Aggiungi > Elemento esistente**. Nella finestra di dialogo visualizzata, selezionare un file e scegliere **Aggiungi come collegamento** nell'elenco a discesa del pulsante **Aggiungi**. Questo comando crea un collegamento nella cartella selezionata, purché non siano presenti file in conflitto. Il collegamento non verrà aggiunto se però è già presente un file con lo stesso nome o nel progetto esiste già un collegamento a tale file.

Se si prova a collegare un file già esistente nelle cartelle di progetto, questo viene aggiunto come un file normale e non come collegamento. Per convertire un file in un collegamento, selezionare **File > Salva con nome** per salvare il file in un percorso esterno alla gerarchia del progetto. Visual Studio lo converte automaticamente in un collegamento. Analogamente, è possibile usare **File > Salva con nome** anche per riconvertire un collegamento in un file e salvarlo in un punto qualsiasi all'interno della gerarchia del progetto. 

Se si sposta un file collegato in Esplora soluzioni, viene spostato solo il collegamento, mentre il file effettivo rimane nella posizione originale. Analogamente, l'eliminazione di un collegamento implica solo la rimozione del collegamento e non del file.

I file collegati non possono essere rinominati.

## <a name="references"></a>Riferimenti

Nei progetti Visual Studio è possibile aggiungere riferimenti a progetti ed estensioni che figureranno nel nodo **Riferimenti** in Esplora soluzioni:

![Riferimenti alle estensioni in progetti Python](media/projects-extension-references.png)

I riferimenti alle estensioni indicano in genere le dipendenze tra progetti e vengono usati per fornire funzionalità IntelliSense in fase di progettazione o di collegamento in fase di compilazione. I riferimenti vengono usati in modo analogo nei progetti Python, ma a causa della natura dinamica di Python vengono usati principalmente in fase di progettazione per fornire funzionalità IntelliSense migliorate. Possono inoltre essere usati per la distribuzione in Microsoft Azure per installare le dipendenze aggiuntive.

### <a name="extension-modules"></a>Moduli di estensione

Un riferimento a un file `.pyd` consente di abilitare la funzionalità IntelliSense per il modulo generato. Visual Studio carica il file `.pyd` caricato nell'interprete Python e ne esamina tipi e funzioni. Prova inoltre ad analizzare le stringhe di documento relative alle funzioni per offrire il supporto per la firma.

Se in qualsiasi momento il modulo di estensione viene aggiornato sul disco, Visual Studio analizza nuovamente il modulo in background. Questa azione non influisce sul comportamento del runtime, anche se alcuni completamenti saranno disponibili solo al termine dell'analisi.

Potrebbe anche essere necessario aggiungere un [percorso di ricerca](managing-python-environments-in-visual-studio.md#search-paths) per la cartella che contiene il modulo.

### <a name="net-projects"></a>Progetti .NET

Quando si usa IronPython, è possibile aggiungere riferimenti ad assembly .NET per abilitare la funzionalità IntelliSense. Per i progetti .NET presenti nella soluzione fare clic con il pulsante destro del mouse sul nodo **Riferimenti** del progetto Python, scegliere **Aggiungi riferimento**, selezionare la scheda **Progetti** e quindi individuare e selezionare il progetto desiderato. Per le DLL scaricate separatamente, selezionare la scheda **Sfoglia** e quindi individuare e selezionare la DLL desiderata.

Dal momento che i riferimenti in IronPython non sono disponibili fino a quando non si effettua una chiamata a `clr.AddReference('AssemblyName')`, è inoltre necessario aggiungere una chiamata `clr.AddReference` all'assembly.

### <a name="webpi-projects"></a>Progetti WebPI

È possibile aggiungere riferimenti alle voci di prodotto WebPI per la distribuzione nei servizi cloud di Microsoft Azure in cui è possibile installare componenti aggiuntivi tramite il feed WebPI. Per impostazione predefinita, il feed visualizzato è specifico di Python e include Django, CPython e altri componenti di base. È inoltre possibile selezionare un feed personalizzato, come illustrato di seguito. Durante la pubblicazione in Microsoft Azure, un'attività di installazione installerà tutti i prodotti di riferimento.

![Riferimenti WebPI](media/projects-webPI-components.png)