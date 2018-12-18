---
title: Aggiornamento di SCVMM 2008 R2 a SCVMM 2012 | Microsoft Docs
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Upgrade SCVMM 2008 R2 to SCVMM 2012, test lab
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 51d907dfe25d8f27065b2a4d8bbecaa3e98e42a1
ms.sourcegitcommit: 873c0e1a31def013bcca1b0caa0eb0249de89bec
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2018
---
# <a name="upgrade-scvmm-2008-r2-to-scvmm-2012"></a>Aggiornamento di SCVMM 2008 R2 a SCVMM 2012

Lab Management per Team Foundation Server supporta SCVMM 2008 R2 e SCVMM 2012. Se si aggiorna Team Foundation Server 2013 a Team Foundation Server 2015 e si intende aggiornare SCVMM 2008 R2 a SCVMM 2012, è consigliabile eseguire l'aggiornamento a SCVMM 2012 dopo aver completato l'aggiornamento a Team Foundation Server 2015. Questo argomento descrive come aggiornare SCVMM 2008 R2 a SCVMM 2012 quando si usa Lab Management in Team Foundation Server 2015.
Lab Management **non** supporta SCVMM 2016. 

**Importante:** quando si aggiorna SCVMM, alcuni passaggi possono causare un certo tempo di inattività di Team Foundation Server. Questi passaggi sono indicati di seguito.

## <a name="upgrading-to-scvmm-2012"></a>Aggiornamento a SCVMM 2012

1. Utilizzare il programma di installazione di SCVMM 2012 per aggiornare il server SCVMM 2008 R2 al server SCVMM 2012.

1. Aggiornare gli agenti SCVMM negli host e nelle condivisioni di libreria.

1. Utilizzare la console di amministrazione di SCVMM per verificare che tutti i componenti di SCVMM funzionino.

1. Installare la console di amministrazione di SCVMM 2012 in tutti i computer del livello applicazione di Team Foundation Server.

1. Usare il comando **iisreset** per riavviare il servizio Web di Team Foundation Server. Successivamente, riavviare l'agente processo di Team Foundation Server.

   **Attenzione:** questo passaggio interrompe il funzionamento dei servizi in Team Foundation Server.

1. Aggiornare i dati e i modelli nei database delle raccolte di progetti in modo che siano compatibili con SCVMM 
   2012.

   Aprire un prompt dei comandi con privilegi elevati in Team Foundation Server e immettere il comando seguente:

   **C:\\Programmi\\Microsoft Team Foundation Server 14.0\\Tools\> tfsconfig lab /upgradeSCVMM /collectionName:\***

   Quando si usa il comando **upgradeSCVMM**, tramite Team Foundation Server verrà creato un nuovo oggetto modello nel server SCVMM per ogni progetto team usato dal modello in questione. Ciò garantisce che i modelli vengono aggiornati per essere compatibile con SCVMM 2012 senza perdere i dati. Tuttavia, quando i nuovi modelli vengono creati, il nome del progetto team viene aggiunto al nome del modello.

   **Attenzione:**  
   Se il nuovo nome di modello è maggiore di 64 caratteri, verrà causato un errore di SCVMM. Per risolvere l'errore, è necessario assegnare a questi modelli un nome più breve. Se quando si esegue questo comando vengono generati altri errori o avvisi, vedere la prossima sezione per risolverli. Se non si rilevano errori o avvisi, l'aggiornamento è completo ed è possibile iniziare l'utilizzo di ambienti SCVMM con Lab Management.

## <a name="resolving-errors-and-warnings-when-using-the-upgradescvmm-command"></a>Risoluzione di errori e avvisi quando si utilizza il comando upgradeSCVMM

Dopo l'esecuzione del comando **upgradeSCVMM**, prima di iniziare a usare Lab Management è necessario risolvere tutti gli errori e tutti gli avvisi visualizzati e quindi eseguire nuovamente il comando. Tramite il comando **upgradeSCVMM** viene generato un file di log contenente le informazioni sugli errori e sugli avvisi che si verificano. Il percorso del file di log viene visualizzato quando si esegue il comando**upgradeSCVMM**.

**Errore di SCVMM**: se viene visualizzato un errore correlato a un errore di SCVMM, usare la cronologia dei processi di SCVMM per ottenere altre informazioni sull'errore. Dopo aver risolto l'errore in SCVMM, eseguire nuovamente il comando **upgradeSCVMM**.

## <a name="see-also"></a>Vedere anche

* [Modificare le configurazioni di Lab Management esistenti](https://msdn.microsoft.com/library/ee704508%28v=vs.140%29.aspx)
