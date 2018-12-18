---
title: Assemblaggio e distribuzione delle soluzioni SharePoint | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: e25d0829305f414712590296b6121d62583736a2
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="packaging-and-deploying-sharepoint-solutions"></a>Creazione del pacchetto e distribuzione delle soluzioni SharePoint
  In genere, una soluzione SharePoint viene distribuita in un server SharePoint utilizzando un file di pacchetto (con estensione wsp) della soluzione. È possibile utilizzare Visual Studio per organizzare gli elementi di progetto SharePoint in funzionalità e per creare un pacchetto per distribuire le funzionalità di SharePoint.  
  
 In questo argomento vengono fornite le seguenti informazioni:  
  
-   [Creazione di funzionalità e pacchetti](#Creating)  
  
-   [Funzionalità e l'assemblaggio di supporto dello strumento](#Tools)  
  
-   [Distribuzione delle soluzioni SharePoint](#Deploying)  
  
-   [Distribuzione dei file di soluzioni SharePoint](#DeployingFiles)  
  
##  <a name="Creating"></a>Creazione di funzionalità e pacchetti  
 È possibile utilizzare Visual Studio per raggruppare gli elementi di SharePoint correlati in un *funzionalità*. Ad esempio, una funzionalità per una definizione di elenco di contatti può includere l'istanza di elenco e la definizione di elenco. È possibile combinare questi due elementi in una singola funzionalità per la distribuzione. Per ulteriori informazioni sulle funzionalità, vedere [blocco predefinito: funzionalità](http://go.microsoft.com/fwlink/?LinkID=169183).  
  
 Successivamente, è possibile creare un pacchetto di soluzione SharePoint (con estensione wsp) per aggregare più funzionalità, definizioni di sito, assembly e altri file in un singolo pacchetto, che archivia i file in un formato richiesto da SharePoint per distribuire i file nel server. Per ulteriori informazioni, vedere [blocco predefinito: soluzioni](http://go.microsoft.com/fwlink/?LinkID=169186).  
  
##  <a name="Tools"></a>Funzionalità e l'assemblaggio di supporto dello strumento  
 È possibile utilizzare gli strumenti di sviluppo per SharePoint in Visual Studio per organizzare rapidamente i file di SharePoint in funzionalità e pacchetti per semplificare la distribuzione della soluzione. È possibile utilizzare gli strumenti seguenti per configurare il pacchetto di funzionalità e soluzioni.  
  
-   Progettazione di funzionalità e pacchetto.  
  
-   Esplora pacchetti, una finestra degli strumenti.  
  
-   Esplora soluzioni.  
  
### <a name="feature-designer-and-package-designer"></a>Progettazione di funzionalità e pacchetto  
 È possibile creare funzionalità, impostare gli ambiti e contrassegnare altre funzionalità come dipendenze utilizzando la finestra di progettazione di funzionalità. La finestra di progettazione visualizza anche il file XML finale che descrive ogni funzionalità. Per ulteriori informazioni, vedere [la creazione di funzionalità SharePoint](../sharepoint/creating-sharepoint-features.md).  
  
 Applicare la funzionalità per un sito Web specifico o un gruppo di siti Web mediante l'impostazione relativa *ambito* in Progettazione funzionalità. Se una funzionalità è attivata per un singolo sito Web, la funzionalità funziona solo in quel particolare sito Web. Se è attivata per una raccolta siti, gli elementi nella funzionalità valide per tutta la raccolta. Per ulteriori informazioni, vedere [ambito elemento](http://go.microsoft.com/fwlink/?LinkID=169189).  
  
 Se la funzionalità si basa su altre funzionalità, è possibile impostare un *dipendenza di attivazione delle funzionalità* per contrassegnare le funzionalità dipendenti prima di rendere disponibile la funzionalità. Dipendenza di attivazione funzionalità controlla se le funzionalità dipendenti già attivate in quell'ambito. Per ulteriori informazioni, vedere [dipendenze di attivazione e l'ambito](http://go.microsoft.com/fwlink/?LinkID=169190).  
  
 Nella finestra di progettazione del pacchetto, è possibile raggruppare gli elementi di SharePoint in un unico pacchetto della soluzione e configurare se si desidera reimpostare il server Web durante la distribuzione. Per impostare il tipo di server di distribuzione, utilizzare il **proprietà** finestra. La finestra di progettazione genera inoltre il file XML che descrive il contenuto del pacchetto. Per ulteriori informazioni, vedere [la creazione di pacchetti della soluzione SharePoint](../sharepoint/creating-sharepoint-solution-packages.md).  
  
 Durante la distribuzione, viene arrestato il servizio Internet Information Services (IIS) per copiare i file della soluzione nel server SharePoint. Utilizzando la finestra di progettazione del pacchetto in Visual Studio, è possibile selezionare se il server Web deve essere riavviato. Per configurare se la soluzione viene distribuita a un server Web front-end o server applicazioni, utilizzare il **proprietà** finestra. Per ulteriori informazioni, vedere [elemento di soluzione (soluzione)](http://go.microsoft.com/fwlink/?LinkID=169191).  
  
### <a name="packaging-explorer"></a>Esplora pacchetti  
 Per completare la progettazione di funzionalità e pacchetto, è possibile utilizzare Esplora pacchetti per raggruppare i file di SharePoint in funzionalità e pacchetti. Inoltre, è possibile visualizzare la visualizzazione gerarchica del progetto SharePoint pacchetto, funzionalità, gli elementi e file. Esplora pacchetti è una finestra degli strumenti che è possibile utilizzare per completare le attività seguenti:  
  
-   Aprire elementi di progetto SharePoint e file.  
  
-   Trascinamento della selezione di elementi di progetto SharePoint da una funzionalità a un'altra.  
  
-   Trascinamento della selezione di elementi di progetto SharePoint e le funzionalità da un pacchetto a un altro.  
  
-   Aggiungere una nuova funzionalità a un pacchetto.  
  
-   Aprire una finestra di progettazione di funzionalità o il pacchetto.  
  
-   Convalidare le funzionalità e pacchetti.  
  
 Gli strumenti di sviluppo per SharePoint in Visual Studio dispongono di regole di convalida per assicurare che il pacchetto della soluzione venga creato correttamente. Inoltre, le regole di verificano che il file della soluzione con estensione wsp può essere distribuito e attivato in un server SharePoint completata. Per ulteriori informazioni sullo schema XML per le funzionalità, vedere [funzionalità schemi](http://go.microsoft.com/fwlink/?LinkID=169192).  
  
 È possibile aggiungere funzionalità personalizzate e regole di convalida del pacchetto per il sistema di progetto SharePoint. Per ulteriori informazioni, vedere [procedura: creare funzionalità personalizzate e regole di convalida del pacchetto per le soluzioni SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
 Per ulteriori informazioni su Esplora pacchetti, vedere [procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto utilizzando Esplora pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
### <a name="solution-explorer"></a>Esplora soluzioni  
 È possibile utilizzare Esplora soluzioni per individuare e aprire i file del progetto SharePoint. Utilizzare il menu di scelta rapida in Esplora soluzioni per aggiungere le funzionalità, i ricevitori di eventi e le risorse di funzionalità. Inoltre, è possibile aprire le finestre di progettazione di funzionalità e del pacchetto per configurare le funzionalità e pacchetti per la distribuzione.  
  
##  <a name="Deploying"></a>Distribuzione delle soluzioni SharePoint  
 Dopo aver personalizzato la funzionalità e pacchetto in Visual Studio, è possibile creare un file con estensione wsp per distribuire SharePoint Server. È possibile utilizzare Visual Studio per eseguire il debug e testare l'estensione wsp solo nel server SharePoint nel computer di sviluppo. Per ulteriori informazioni su come distribuire le soluzioni SharePoint in un server SharePoint remoto, vedere [distribuendo una soluzione](http://go.microsoft.com/fwlink/?LinkID=169194).  
  
 È inoltre possibile personalizzare i passaggi di distribuzione nel computer di sviluppo. Per ulteriori informazioni, vedere [distribuzione, pubblicazione e l'aggiornamento di pacchetti della soluzione SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
##  <a name="DeployingFiles"></a>Distribuzione dei file di soluzioni SharePoint  
 In genere, quando si aggiunge un elemento di progetto SharePoint alla soluzione di SharePoint, tutti i file necessari risultano inclusi. I file che possono essere compilati (codice) vengono compilati in assembly di output della soluzione. Tuttavia, è possibile aggiungere i file non compilabile, ad esempio, con estensione XML,. txt o file di risorse, a un progetto SharePoint. Questi file non sono automaticamente inclusi nella soluzione. Per garantire che vengono inclusi, aggiungere i file in una cartella mappata o a un elemento di progetto SharePoint.  
  
 I file aggiunti alle cartelle mappate vengono copiati automaticamente nell'hive SharePoint quando si distribuisce la soluzione. File aggiunti a un elemento di progetto SharePoint vengono distribuiti nel percorso specificato nella **percorso di distribuzione** proprietà per ogni file, che viene impostato parzialmente in base il **tipo di distribuzione** proprietà. Per impostazione predefinita, il **tipo di distribuzione** valore della proprietà è **NoDeployment**, il che significa che il file non è distribuito con la soluzione. È necessario impostare un altro valore per la proprietà includere il file nel pacchetto.  
  
 Ad esempio, per aggiungere un file XML a un progetto SharePoint, effettuare una delle azioni seguenti:  
  
-   Aggiungere una cartella mappata di SharePoint "Layout" al progetto. Verrà creato in **Esplora** una cartella denominata **layout** che contiene una sottocartella per il progetto. Aggiungere il file XML per la nuova sottocartella. Per impostazione predefinita, viene distribuito il file nel file System di SharePoint in... \Template\Layouts.\\*nome della cartella*\\. Per informazioni su come aggiungere cartelle mappate, vedere [procedura: aggiungere e rimuovere cartelle mappata](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
-   Aggiungere il file XML nella cartella dell'elemento di progetto SharePoint e quindi modificare il **tipo di distribuzione** proprietà del file XML da **NoDeployment** a un altro, ad esempio impostare **RootFile** o **ElementFile**. Appropriata **tipo di distribuzione** impostazione varia a seconda del file e il progetto. Per ulteriori informazioni sul **tipo di distribuzione** le impostazioni delle proprietà, vedere [lo sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md).  
  
 Se un file aggiunto non è applicabile a qualsiasi progetto specifico nella soluzione, è possibile aggiungere un progetto SharePoint vuoto alla soluzione e quindi aggiungere i file aggiuntivi. In alternativa per la distribuzione di file in SharePoint, in particolare per il database del contenuto, è possibile aggiungere un modulo al progetto e quindi aggiungere i file del modulo. Per ulteriori informazioni, vedere [utilizzando moduli da includere file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Sviluppo di soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Compilazione e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  