---
title: "Gestione delle proprietà di progetti e soluzioni | Microsoft Docs"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 75247EB8-323A-4AFD-A451-6703A03D5D1F
ms.openlocfilehash: 8871ab002a94a9c0bbc0063a25b4dea9cb271142
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="managing-project-and-solution-properties"></a>Gestione delle proprietà di progetti e soluzioni

## <a name="project-options"></a>Opzioni del progetto

Le opzioni del progetto sono specifiche di ogni progetto e influiscono sul modo in cui il progetto viene scritto, compilato ed eseguito. Ciò è in contrasto con le preferenze di Visual Studio per Mac, che rappresentano opzioni specifiche dell'utente, e con le opzioni della soluzione, che rappresentano le opzioni per l'intera soluzione. Le opzioni del progetto vengono archiviate nel file di progetto (con estensione csproj), in modo che altri sviluppatori possano compilare ed eseguire correttamente il progetto. In questo modo, molti sviluppatori possono lavorare allo stesso documento senza compromettere la formattazione del file.

Le opzioni del progetto in Visual Studio per Mac possono essere avviate facendo doppio clic sul nome del progetto oppure facendo clic con il pulsante destro del mouse per aprire il menu di scelta rapida e scegliendo **Opzioni**:

 ![Opzioni nel menu di scelta rapida](media/projects-and-solutions-image2.png)

Le opzioni modificabili includono quelle per compilare, eseguire e impostare opzioni del codice sorgente e di controllo della versione.

Le opzioni del progetto sono organizzate in cinque categorie diverse che hanno le funzionalità seguenti:

* **Generale** - In questa sezione è possibile impostare informazioni sul progetto, come nome, descrizione e spazio dei nomi predefinito, oltre al percorso del progetto.
* **Compila** - Consente agli sviluppatori di impostare o modificare i profili PCL per le librerie di classi portabili. Consente anche di impostare opzioni del compilatore, configurazioni e comandi personalizzati. Qui è possibile impostare anche il percorso di output e il nome dell'assembly.
* **Esegui** - Consente di creare configurazioni di esecuzione personalizzate per i singoli progetti.
* **Codice sorgente** - Consente di controllare la formattazione di molti diversi tipi di file e convenzioni di denominazione. In questa posizione è possibile anche impostare criteri di denominazione e stili di intestazione predefiniti.
* **Controllo della versione** - Consente di modificare lo stile del messaggio di commit quando si usa il controllo della versione con il progetto.

Ogni progetto può contenere anche opzioni specifiche, a seconda della piattaforma. Un progetto Xamarin.Android come quello illustrato di seguito, ad esempio, avrà opzioni relative alla compilazione Android, come le opzioni del linker, e all'applicazione, come le autorizzazioni:

 ![Opzioni di progetto Android](media/projects-and-solutions-image5.png)

Xamarin.iOS conterrà le opzioni relative alla firma del bundle, ad esempio il profilo di provisioning da usare, oltre che quelle relative alla creazione del pacchetto IPA:

 ![Opzioni di progetto iOS](media/projects-and-solutions-image6.png)

## <a name="solution-options"></a>Opzioni della soluzione 

Le opzioni della soluzione sono come le opzioni del progetto, ma riguardano l'intera soluzione. Consentono di impostare le informazioni sull'autore, le impostazioni di compilazione, gli stili di formattazione del codice e il controllo della versione e permettono di assegnare il progetto di avvio nella soluzione.  È possibile accedere alla finestra di dialogo Opzioni soluzione dalla voce di menu **Progetto > Opzioni soluzione**, dalla voce del menu di scelta rapida **Opzioni** della soluzione nel riquadro della soluzione oppure facendo doppio clic sulla soluzione nel riquadro della soluzione:

 ![Opzioni della soluzione](media/projects-and-solutions-image7.png)
