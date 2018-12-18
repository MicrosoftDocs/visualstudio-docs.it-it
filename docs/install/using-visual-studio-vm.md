---
title: Uso di Visual Studio in una macchina virtuale di Azure | Microsoft Docs
description: Informazioni su come usare Visual Studio in una macchina virtuale di Azure
ms.date: 01/30/2018
ms.technology: vs-acquisition
ms.topic: article
helpviewer_keywords:
- azure services
- virtual machine; VM
- installation
- visual studio
author: PhilLee-MSFT
ms.author: phillee
manager: sacalla
ms.workload:
- multiple
ms.openlocfilehash: d8e99965867d5dbc2710d6c56c5b3dc90fc16dc8
ms.sourcegitcommit: 4b4027244b8de25e30b533148804b87321d3e8a6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2018
---
# <a id="top"> </a> Immagini di Visual Studio in Azure
L'uso di Visual Studio in esecuzione in una macchina virtuale di Azure preconfigurata è il modo più semplice e veloce per implementare da zero un ambiente di sviluppo pronto.  In [Azure Marketplace](https://portal.azure.com/) sono disponibili immagini di sistema con configurazioni diverse di Visual Studio ed è sufficiente avviare una macchina virtuale.

Gli utenti che non hanno ancora familiarità con Azure possono [creare un account Azure gratuito](https://azure.microsoft.com/free).

## <a name="what-configurations-and-versions-are-available"></a>Configurazioni e versioni disponibili
In Azure Marketplace sono disponibili immagini per le versioni più recenti principali: Visual Studio 2017 e Visual Studio 2015.  Per ogni versione principale, sono disponibili la versione rilasciata originariamente (anche nota come 'RTW') e le versioni aggiornate "più recenti".  Per ognuna di queste versioni diverse, esistono le edizioni Visual Studio Enterprise e Visual Studio Community.  Queste immagini vengono aggiornate almeno una volta al mese in modo da includere gli aggiornamenti più recenti di Visual Studio e Windows.  Mentre i nomi delle immagini rimangono invariati, la descrizione di ogni immagine include la versione del prodotto installato e la data di validità dell'immagine.

|               Versione di rilascio              |        Edizioni       |     Versione del prodotto     |
|:------------------------------------------:|:---------------------:|:-----------------------:|
| Visual Studio 2017 - Versione più recente (versione 15.5) | Enterprise, Community |      Versione 15.5.3     |
|         Visual Studio 2017 - RTW           | Enterprise, Community |      Versione 15.0.7     |
|   Visual Studio 2015 - Versione più recente (Update 3)   | Enterprise, Community |  Versione 14.0.25431.01  |
|         Visual Studio 2015 - RTW           |         nessuno          | (Scaduto per la manutenzione) |

> [!NOTE]
> In base i criteri per la manutenzione adottati da Microsoft, la versione rilasciata originariamente (nota anche come 'RTW') di Visual Studio 2015 è scaduta per la manutenzione.  Pertanto, Visual Studio 2015 Update 3 è l'unica versione rimanente disponibile per la linea di prodotti Visual Studio 2015.

Per altre informazioni, vedere i [criteri per la manutenzione di Visual Studio](https://www.visualstudio.com/en-us/productinfo/vs-servicing-vs).

## <a name="what-features-are-installed"></a>Funzionalità installate
Ogni immagine contiene il set di funzionalità consigliate per l'edizione specifica di Visual Studio.  In genere, l'installazione include:

* Tutti i carichi di lavoro disponibili inclusi i componenti facoltativi consigliati dei carichi di lavoro
* .NET 4.6.2 e .NET 4.7 SDK, Targeting Pack e Strumenti di sviluppo
* Visual F#
* Estensione GitHub per Visual Studio
* Strumenti di LINQ to SQL

Questa è la riga di comando usata per installare Visual Studio durante la creazione delle immagini:

```
    vs_enterprise.exe --allWorkloads --includeRecommended --passive ^
       add Microsoft.Net.Component.4.7.SDK ^
       add Microsoft.Net.Component.4.7.TargetingPack ^ 
       add Microsoft.Net.Component.4.6.2.SDK ^
       add Microsoft.Net.Component.4.6.2.TargetingPack ^
       add Microsoft.Net.ComponentGroup.4.7.DeveloperTools ^
       add Microsoft.VisualStudio.Component.FSharp ^
       add Component.GitHub.VisualStudio ^
       add Microsoft.VisualStudio.Component.LinqToSql
```

Se le immagini non includono una funzionalità di Visual Studio necessaria, comunicarlo tramite lo strumento per l'invio di commenti e suggerimenti (nell'angolo in alto a destra della pagina).

## <a name="what-size-vm-should-i-choose"></a>Quali dimensioni di macchina virtuale scegliere
Il provisioning di una nuova macchina virtuale è semplice e Azure offre una gamma completa di dimensioni di macchine virtuali.  Come per qualsiasi investimento hardware, occorre bilanciare prestazioni e costi.  Poiché Visual Studio è un'applicazione multithreading potente, è necessaria una macchina virtuale che includa almeno 2 processori e 7 GB di memoria. In Azure ciò corrisponde come minimo a queste dimensioni di macchina virtuale:

   * Standard_D2_v3
   * Standard_D2s_v3
   * Standard_D4_v3
   * Standard_D4s_v3
   * Standard_D2_v2
   * Standard_D2S_v2
   * Standard_D3_v2

Per altre informazioni sulle dimensioni di macchina virtuale più recenti, vedere [Dimensioni per le macchine virtuali Windows in Azure](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/sizes).

Con Azure non si rimane ancorati alla prima scelta ed è infatti possibile ribilanciare la configurazione iniziale ridimensionando la macchina virtuale.  È possibile eseguire il provisioning di una nuova macchina virtuale con dimensioni più appropriate oppure è possibile ridimensionare la macchina virtuale esistente per hardware sottostante diverso.  Per altre informazioni, vedere [Ridimensionare una VM Windows](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/resize-vm).

## <a name="after-i-get-the-vm-running-then-what"></a>Passi successivi all'attivazione della macchina virtuale
Visual Studio segue il modello "Bring Your Own License" in Azure.  In modo analogo all'installazione in hardware proprietario, quindi, uno dei primi passaggi consiste nell'acquisire la licenza per l'installazione di Visual Studio.  Per sbloccare Visual Studio, è possibile accedere con un account Microsoft associato a una sottoscrizione di Visual Studio oppure usare il codice Product Key fornito con l'acquisto iniziale.  Per altre informazioni, vedere [Accesso a Visual Studio](https://docs.microsoft.com/en-us/visualstudio/ide/signing-in-to-visual-studio) e [Come sbloccare Visual Studio](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-unlock-visual-studio).

## <a name="after-i-build-out-the-dev-vm-how-do-i-save-capture-it-for-future-or-team-use"></a>Dopo aver configurato la macchina virtuale per lo sviluppo come si può salvarla (acquisirla) per usi futuri o da parte del team?

La gamma di possibili configurazioni degli ambienti di sviluppo è enorme e i costi sostenuti per la preparazione degli ambienti più complessi sono tutt'altro che irrilevanti.  Tuttavia, indipendentemente dalla configurazione dell'ambiente, Azure consente di proteggere facilmente l'investimento grazie alla possibilità di salvare/acquisire facilmente la macchina virtuale configurata come 'immagine di base' per usi futuri, personali e/o per altri membri del team.  In questo modo, quando si avvia una nuova macchina virtuale è possibile eseguirne il provisioning dall'immagine di base anziché dall'immagine del Marketplace.

In breve, è necessario eseguire sysprep sulla macchina virtuale in esecuzione e arrestarla, quindi *acquisire (figura 1)* la macchina virtuale come immagine tramite l'interfaccia utente del portale di Azure.  Azure salva il file `.vhd` che contiene l'immagine nell'account di archiviazione di propria scelta.  La nuova immagine viene quindi visualizzata come risorsa immagine nell'elenco di risorse della sottoscrizione.

<img src="media/capture-vm.png" alt="Capture an image through the Azure portal’s UI" style="border:3px solid Silver; display: block; margin: auto;"><center>*(Figura 1) Acquisire un'immagine tramite l'interfaccia utente del portale di Azure.*</center>

Per altre informazioni, vedere [Acquisire la macchina virtuale in un'immagine](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/capture-image-resource).

  **Promemoria:** non dimenticare di eseguire sysprep sulla macchina virtuale.  Se si omette questo passaggio, Azure non può eseguire il provisioning di una macchina virtuale dall'immagine.

> [!NOTE]
> Si dovranno sostenere comunque alcuni costi per l'archiviazione delle immagini, ma questi costi aggiuntivi sono probabilmente insignificanti rispetto al costo della manodopera per ricostruire la macchina virtuale da zero per ogni persona del team che necessita di una macchina virtuale.  Ad esempio, costa pochi euro al mese creare e archiviare un'immagine di 127 GB riutilizzabile da tutti i membri del team.  Questi costi sono tuttavia irrisori se confrontati con le ore dedicate da ogni dipendente alla preparazione e alla convalida di una macchina virtuale per lo sviluppo adeguatamente configurata per l'uso individuale.

Inoltre, per le varie attività o tecnologie di sviluppo potrebbe essere necessaria una maggiore scalabilità, ad esempio una gamma di configurazioni per lo sviluppo e più configurazioni di macchina virtuale.  È possibile usare Azure DevTest Labs per creare _recipe_ per automatizzare la costruzione dell'immagine finale e per gestire i criteri per le macchine virtuali in esecuzione del team.  [Using Azure DevTest Labs for developers](https://docs.microsoft.com/en-us/azure/devtest-lab/devtest-lab-developer-lab) (Utilizzo di Azure DevTest Labs per gli sviluppatori) è la migliore fonte di informazioni su DevTest Labs.

## <a name="next-steps"></a>Passaggi successivi
Dopo aver raccolto informazioni sulle immagini di Visual Studio preconfigurate, il passaggio successivo consiste nel creare una nuova macchina virtuale:

* [Creare una macchina virtuale Windows con il portale di Azure](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/quick-create-portal)
* [Panoramica delle macchine virtuali Windows](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/overview)
