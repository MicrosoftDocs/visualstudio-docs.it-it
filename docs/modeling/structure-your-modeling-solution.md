---
title: Strutturare la soluzione di modellazione
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 3de677d23f11f56bde101e1e0e7748824e0d30c9
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="structure-your-modeling-solution"></a>Strutturare la soluzione di modellazione
Per usare efficacemente i modelli in un progetto di sviluppo, è necessario che i membri del team siano in grado di usare contemporaneamente modelli di parti diverse del progetto. Questo argomento suggerisce uno schema per suddividere l'applicazione in più parti, che corrispondono ai livelli di un diagramma su livelli generale.

 Per iniziare rapidamente un progetto o un sottoprogetto, è utile avere un modello di progetto basato sulla struttura del progetto scelta. Questo argomento descrive come creare e usare tale modello.

 Questo argomento presuppone che si lavori su un progetto abbastanza grande per richiedere la collaborazione di più membri del team ed eventualmente di più team. Il codice e i modelli del progetto sono archiviati in un sistema di controllo del codice sorgente quale [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]. Almeno alcuni membri del team usano Visual Studio per sviluppare i modelli, mentre altri membri possono visualizzarli con altre versioni di Visual Studio.

 Per le versioni di Visual Studio che supportano ogni strumento e modellazione di funzionalità, vedere [supporto della versione per l'architettura e strumenti di modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="solution-structure"></a>Struttura della soluzione
 In un progetto di medie o grandi dimensioni, la struttura del team riflette la struttura dell'applicazione. Ogni team usa una soluzione di Visual Studio.

#### <a name="to-divide-an-application-into-layers"></a>Per suddividere un'applicazione in livelli

1.  Basare la struttura delle soluzioni sulla struttura dell'applicazione, ad esempio applicazione Web, applicazione di servizio o applicazione desktop. Viene illustrata un'ampia gamma di architetture comuni in [archetipi applicazione nella Guida all'architettura di applicazione di Microsoft](http://go.microsoft.com/fwlink/?LinkId=196681).

2.  Creare una soluzione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], che verrà denominata soluzione Architecture. Questa soluzione verrà usata per creare la progettazione complessiva del sistema. Conterrà modelli ma non il codice.

     Aggiungere un diagramma di dipendenze per questa soluzione. Nel diagramma di dipendenza, disegnare l'architettura in cui che si è scelto per l'applicazione. Ad esempio, il diagramma potrebbe mostrare i seguenti livelli con le reciproche dipendenze: presentazione, logica di business e dati.

4.  Creare una soluzione di Visual Studio separata per ogni livello nel diagramma architettura dipendenza.

     Queste soluzioni verranno usate per sviluppare il codice dei livelli.

5.  Creare modelli che rappresentano le strutture dei livelli e i concetti che sono comuni a tutti i livelli. Disporre i modelli in modo che si possano visualizzare tutti dalla soluzione Architecture e che da ogni livello sia possibile visualizzare i relativi modelli.

     È possibile ottenere questo risultato con una delle procedure seguenti. La prima consente di creare un progetto di modello separato per ogni livello, mentre la seconda permette di creare un unico progetto di modello condiviso tra i livelli.

    ###### <a name="to-use-a-separate-modeling-project-for-each-layer"></a>Per usare un progetto di modello separato per ogni livello

    1.  Creare un progetto di modello nella soluzione di ogni livello.

         Questo modello conterrà i diagrammi che descrivono i requisiti e progettazione di tale livello. Contiene anche i diagrammi di dipendenza che mostrano i livelli annidati.

         A questo punto è disponibile un modello per ogni livello, oltre a un modello per l'architettura dell'applicazione. Ogni modello è contenuto in una soluzione separata. In questo modo, i membri del team possono lavorare contemporaneamente sugli stessi livelli.

    2.  Aggiungere alla soluzione Architecture il progetto di modellazione della soluzione di ogni livello. A questo scopo, aprire la soluzione Architecture. In Esplora soluzioni, fare clic sul nodo della soluzione, scegliere Aggiungi e quindi fare clic su **progetto esistente**. Passare al progetto di modellazione (con estensione modelproj) in una soluzione del livello.

         Ogni modello è ora visibile in due soluzioni: la relativa soluzione principale e la soluzione Architecture.

    3.  Per il progetto di modellazione di ogni livello, aggiungere un diagramma di dipendenza. Iniziare con una copia del diagramma architettura dipendenza. È possibile eliminare le parti che non sono le dipendenze del diagramma di dipendenza.

         È anche possibile aggiungere i diagrammi di dipendenza che rappresentano la struttura dettagliata di questo livello.

         Questi diagrammi vengono usati per convalidare il codice sviluppato nel livello.

    4.  Nella soluzione Architecture modificare i requisiti e i modelli di progettazione di tutti i livelli tramite Visual Studio.

         Nella soluzione di ogni livello sviluppare il codice relativo al livello specifico, facendo riferimento al modello. Se si ritiene sufficiente eseguire lo sviluppo senza usare lo stesso computer per aggiornare il modello, è possibile leggere il modello e sviluppare codice usando versioni di Visual Studio che non consentono di creare modelli. È anche possibile generare codice dal modello in queste versioni.

     Questo metodo assicura che non ci saranno interferenze da parte degli sviluppatori che modificano contemporaneamente i modelli di livello.

     Tuttavia, poiché i modelli sono separati, è difficile fare riferimento a concetti comuni. Ogni modello deve disporre di una copia distinta degli elementi degli altri livelli e dell'architettura dai quali dipende. Il diagramma di dipendenze in ogni livello deve essere mantenuto sincronizzato con il diagramma dell'architettura dipendenza. È difficile mantenere la sincronizzazione quando questi elementi sono soggetti a modifica, anche se è possibile sviluppare appositi strumenti a questo scopo.

    ###### <a name="to-use-a-separate-package-for-each-layer"></a>Per usare un pacchetto separato per ogni livello

    1.  Aggiungere il progetto di modello Architecture alla soluzione di ogni livello. In Esplora soluzioni, fare clic sul nodo della soluzione, scegliere **Aggiungi**, quindi fare clic su **progetto esistente**. A questo punto, è possibile accedere da qualsiasi soluzione al singolo progetto di modello, ossia al progetto Architecture e al progetto di sviluppo per ogni livello.

    2.  Nel modello condiviso, creare un pacchetto per ogni livello: In Esplora soluzioni selezionare il progetto di modellazione. In Esplora modelli UML, fare clic sul nodo radice del modello, scegliere **Aggiungi**, quindi fare clic su **pacchetto**.

         Ogni pacchetto conterrà i diagrammi che descrivono i requisiti e progettazione del livello corrispondente.

    3.  Se necessario, aggiungere diagrammi dipendenza locale per la struttura interna di ogni livello.

     Questo metodo consente agli elementi di progettazione di ogni livello di fare riferimento direttamente agli elementi degli altri livelli e dell'architettura comune da cui dipendono.

     Anche se è possibile che operazioni simultanee su pacchetti diversi causino alcuni conflitti, questi risulteranno abbastanza facili da gestire, in quanto i pacchetti vengono archiviati in file separati.

## <a name="creating-architecture-templates"></a>Creazione di modelli dell'architettura
 Nella pratica, non si creeranno tutte le soluzioni di Visual Studio contemporaneamente, ma se ne aggiungeranno di nuove man mano che il progetto procede. Probabilmente si userà anche la stessa struttura della soluzione nei progetti successivi.  Per velocizzare la creazione di nuove soluzioni, è possibile creare un modello di soluzione o di progetto. È possibile acquisire il modello in un'estensione VSIX ( Visual Studio Integration Extension) per facilitarne la distribuzione e l'installazione in altri computer.

 Ad esempio, se si usano spesso soluzioni con livelli presentazione, aziendale e dati, è possibile configurare un modello per creare nuove soluzioni con la medesima struttura.

#### <a name="to-create-a-solution-template"></a>Per creare un modello di soluzione

1.  [Scaricare e installare l'esportazione guidata modelli](http://go.microsoft.com/fwlink/?LinkId=196686), se non si è già presente.

2.  Creare la struttura della soluzione da usare come punto di partenza per i progetti futuri.

3.  Scegliere **Esporta modello come VSIX** dal menu **File**. Il **Esporta modello come VSIX guidata** apre.

4.  Seguendo le istruzioni della procedura guidata, selezionare i progetti da includere nel modello, fornire un nome e una descrizione per il modello e specificare un percorso di output.

> [!NOTE]
>  Il materiale contenuto in questo argomento è tratto e adattato dalla documentazione Visual Studio Architecture Tooling Guidance, redatta dai membri del gruppo Visual Studio ALM Rangers, una collaborazione tra Most Valued Professional (MVP), Microsoft Services e i team e i writer del prodotto Visual Studio. [Fare clic qui per scaricare il pacchetto completo di indicazioni.](http://go.microsoft.com/fwlink/?LinkID=191984)

## <a name="related-materials"></a>Materiali correlati
 [Organizzare e gestire i modelli](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-9-Organizing-and-Managing-Your-Models/) - video di Clint Edmondson.

 [Visual Studio Architecture Tooling Guidance](../modeling/visual-studio-architecture-tooling-guidance.md) -ulteriori informazioni sulla gestione dei modelli in un team

## <a name="see-also"></a>Vedere anche

- [Usare modelli nel processo di sviluppo](../modeling/use-models-in-your-development-process.md)
