---
title: Applicare automaticamente i codici Product Key durante la distribuzione di Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 08/14/2017
ms.reviewer: tims
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3fbea34afa4e82ea360a0dfefe4f18dc74d11f19
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Applicare automaticamente i codici Product Key durante la distribuzione di Visual Studio
È possibile applicare il codice Product Key a livello di programmazione come parte dello script utilizzato per automatizzare la distribuzione di Visual Studio. È possibile impostare i codici Product Key su un dispositivo a livello di programmazione durante l'installazione di Visual Studio o al termine dell'installazione.

## <a name="apply-the-license-after-installation"></a>Applicare la licenza dopo l'installazione
 È possibile attivare una versione installata di Visual Studio con un codice Product Key tramite l'utilità `StorePID.exe` nei computer di destinazione in modalità invisibile all'utente. `StorePID.exe` è un programma di utilità che viene installato con Visual Studio 2017 nel percorso predefinito seguente: <br> `C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE`

 Eseguire `StorePID.exe` con privilegi elevati, usando un agente System Center o un prompt dei comandi con privilegi elevati. Continuare quindi con il codice Product Key (con i trattini) e il codice Microsoft Product Code (MPC).

>[!IMPORTANT]
> Assicurarsi di includere i trattini nel codice Product Key.

 ```
 StorePID.exe [product key including the dashes] [MPC]
 ```

 In questo esempio è riportata una riga di comando per l'applicazione della licenza di Visual Studio 2017 Enterprise, con codice MPC 08860 e codice Product Key `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`, presupponendone l'installazione in un percorso predefinito:

 ```cmd
 "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
 ```

 La tabella seguente riporta i codici MPC per ogni edizione di Visual Studio:

| Edizione di Visual Studio                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

Se `StorePID.exe` applica correttamente il codice Product Key, restituisce un `%ERRORLEVEL%` pari a 0. Se si verificano errori, verrà restituito uno dei codici seguenti, a seconda della condizione di errore:

| Error                     | Codice |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

## <a name="get-support"></a>Supporto
Non sempre tutto funziona correttamente. Se l'installazione di Visual Studio non riesce, vedere la pagina [Risoluzione degli errori di installazione e aggiornamento di Visual Studio 2017](troubleshooting-installation-issues.md). Se nessuna delle procedure di risoluzione dei problemi risulta utile, contattare Microsoft tramite chat in tempo reale per richiedere assistenza per l'installazione (solo in lingua inglese). Per informazioni dettagliate, vedere la [pagina del supporto di Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Ecco alcune altre opzioni di supporto:
* È possibile segnalare i problemi del prodotto a Microsoft tramite lo strumento [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) che viene visualizzato sia nel programma di installazione di Visual Studio che nell'IDE di Visual Studio.
* È possibile condividere un suggerimento per il prodotto con Microsoft in [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* È possibile visualizzare lo stato dei problemi del prodotto nella [community degli sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/), dove è possibile creare domande e trovare risposte.
* È anche possibile comunicare con gli sviluppatori Microsoft e altri sviluppatori di Visual Studio partecipando alla [conversazione dedicata a Visual Studio nella community di Gitter](https://gitter.im/Microsoft/VisualStudio).  Per questa opzione è necessario un account [GitHub](https://github.com/).

## <a name="see-also"></a>Vedere anche
 * [Installare Visual Studio](../install/install-visual-studio.md)
 * [Creare un'installazione offline di Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)
