---
title: 'Creare un ambiente di sviluppo .NET Core con i contenitori usando Kubernetes nel cloud con Visual Studio - Passaggio 3: Creare un ambiente di sviluppo Kubernetes | Microsoft Docs'
author: johnsta
ms.author: johnsta
ms.date: 02/20/2018
ms.topic: get-started-article
ms.technology: vsce-kubernetes
description: Sviluppo rapido Kubernetes con contenitori e microservizi in Azure
keywords: Docker, Kubernetes, Azure, AKS, servizio contenitore di Azure, contenitori
manager: ghogen
ms.openlocfilehash: 01451ca57cbd4bac5c6bf08d040905b9463b15a3
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2018
---
# <a name="get-started-on-connected-environment-with-net-core-and-visual-studio"></a>Introduzione a Connected Environment con .NET Core e Visual Studio

Passaggio precedente: [Creare un'app Web ASP.NET](get-started-netcore-visualstudio-02.md)

## <a name="create-a-dev-environment-in-azure"></a>Creare un ambiente di sviluppo in Azure
Con Connected Environment è possibile creare ambienti di sviluppo basati su Kubernetes gestiti completamente da Azure e ottimizzati per lo sviluppo. Con il progetto appena creato aperto, selezionare **Connected Environment for AKS** (Connected Environment per AKS) nell'elenco a discesa delle impostazioni di avvio, come illustrato di seguito.

![](images/LaunchSettings.png)

Nella finestra di dialogo visualizzata assicurarsi di eseguire l'accesso con l'account appropriato e quindi selezionare un ambiente di sviluppo esistente oppure selezionare **<Create New Connected Environment for AKS…>** (Crea nuovo Connected Environment per AKS) per crearne uno nuovo.

![](images/ConnectedEnvDialog.png)

È possibile usare i valori predefiniti proposti o modificarli nel modo desiderato. Fare clic su **OK** quando i valori sono impostati in modo appropriato.

![](images/NewEnvDialog.png)

Quando si torna alla finestra di dialogo precedente, lasciare l'elenco a discesa **Space** (Spazio) impostato sul valore predefinito `mainline` per il momento. Questa opzione verrà descritta in maggiore dettaglio in seguito. Selezionare la casella di controllo **Publicly Accessible** (Accessibile pubblicamente) in modo che l'app Web sia accessibile tramite un endpoint pubblico. Questo passaggio non è obbligatorio, ma sarà utile per illustrare alcuni concetti più avanti in questa procedura dettagliata. Sarà comunque possibile in ogni caso eseguire il debug del sito Web usando Visual Studio.

![](images/ConnectedEnvDialog2.png)

Fare clic su **OK** per selezionare o creare l'ambiente di sviluppo. Verrà avviata un'attività in background a tale scopo, che richiederà qualche minuto per il completamento. Per controllare se l'operazione di creazione è ancora in corso, passare il puntatore del mouse sull'icona delle **attività in background** nell'angolo in basso a sinistra della barra di stato (vedere di seguito).

![](images/BackgroundTasks.png)

> [!Note]
Non è possibile eseguire il debug dell'applicazione fino al completamento della creazione dell'ambiente di sviluppo.

## <a name="look-at-the-files-added-to-project"></a>Esaminare i file aggiunti al progetto
Quando si è scelto di usare un ambiente di sviluppo, al progetto sono stati aggiunti alcuni file.

In primo luogo, è possibile vedere che è stata aggiunta una cartella denominata `charts` e che al suo interno è stato eseguito lo scaffolding di un [grafico Helm](https://docs.helm.sh) per l'applicazione. Questi file vengono usati per distribuire l'applicazione nell'ambiente di sviluppo.

Come si può vedere, è stato aggiunto anche un file denominato `Dockerfile`. Questo file contiene le informazioni necessarie per creare un pacchetto dell'applicazione nel formato standard di Docker. Viene anche creato un file `HeaderPropagation.cs`, che verrà illustrato più avanti nella procedura dettagliata. 

Infine, è visibile un file denominato `vsce.yaml` che contiene le informazioni di configurazione necessarie per l'ambiente di sviluppo, ad esempio se l'applicazione deve essere accessibile tramite un endpoint pubblico.

![](images/ProjectFiles.png)

> [!div class="nextstepaction"]
> [Eseguire il debug di un contenitore in Kubernetes](get-started-netcore-visualstudio-04.md)