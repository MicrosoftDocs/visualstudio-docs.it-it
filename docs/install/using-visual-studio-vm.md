---
title: Uso di Visual Studio in una macchina virtuale di Azure | Microsoft Docs
description: Informazioni su come usare Visual Studio in una macchina virtuale di Azure
ms.date: 03/03/2018
ms.technology: vs-acquisition
ms.topic: conceptual
helpviewer_keywords:
- azure services
- virtual machine; VM
- installation
- visual studio
author: PhilLee-MSFT
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a7e1a3646e2e30302548f2445b0ab657f8e3ec4
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2018
---
# <a id="top"> </a> Immagini di Visual Studio in Azure
L'uso di Visual Studio in una macchina virtuale di Azure preconfigurata è un modo semplice e veloce per implementare da zero un ambiente di sviluppo pronto. In [Azure Marketplace](https://azuremarketplace.microsoft.com/marketplace/apps?search=%22visual%20studio%202017%22&page=1) sono disponibili immagini di sistema con configurazioni diverse di Visual Studio

Gli utenti che non hanno ancora familiarità con Azure possono [creare un account Azure gratuito](https://azure.microsoft.com/free).

## <a name="what-configurations-and-versions-are-available"></a>Configurazioni e versioni disponibili
In Azure Marketplace sono disponibili immagini per le versioni più recenti principali: Visual Studio 2017 e Visual Studio 2015. Per ogni versione principale vengono visualizzate la versione definitiva (RTW) rilasciata in origine e le versioni aggiornate più recenti. Per ognuna di queste versioni sono disponibili le edizioni Visual Studio Enterprise e Visual Studio Community. Queste immagini vengono aggiornate almeno una volta al mese in modo da includere gli aggiornamenti più recenti di Visual Studio e Windows. Anche se i nomi delle immagini rimangono invariati, la descrizione di ogni immagine include la versione del prodotto installato e la data di validità dell'immagine.

| Versione di rilascio                                              | Edizioni                     |     Versione del prodotto     |
|:------------------------------------------------------------:|:----------------------------:|:-----------------------:|
| Visual Studio 2017: versione più recente (versione 15.6)                    |    Enterprise, Community     |      Versione 15.6.4     |
| Visual Studio 2017: ultima versione di anteprima (versione 15.7, anteprima 3) |    Enterprise, Community     |      Versione 15.7.0     |
|         Visual Studio 2017: RTW                              |    Enterprise, Community     |      Versione 15.0.10    |
|   Visual Studio 2015: versione più recente (Update 3)                      |    Enterprise, Community     |  Versione 14.0.25431.01  |
|         Visual Studio 2015: RTW                              |             nessuno             | (Scaduto per la manutenzione) |

> [!NOTE]
> In base i criteri per la manutenzione adottati da Microsoft, la versione rilasciata originariamente (RTW) di Visual Studio 2015 è scaduta per la manutenzione. Visual Studio 2015 Update 3 è l'unica versione rimanente disponibile per la linea di prodotti Visual Studio 2015.

Per altre informazioni, vedere i [criteri per la manutenzione di Visual Studio](/visualstudio/productinfo/vs-servicing-vs).

## <a name="what-features-are-installed"></a>Funzionalità installate
Ogni immagine contiene il set di funzionalità consigliate per l'edizione specifica di Visual Studio. In genere, l'installazione include:

* Tutti i carichi di lavoro disponibili, inclusi i componenti facoltativi consigliati per ogni carico di lavoro
* .NET 4.6.2 e .NET 4.7 SDK, Targeting Pack e Strumenti di sviluppo
* Visual F#
* Estensione GitHub per Visual Studio
* Strumenti di LINQ to SQL

Per installare Visual Studio durante la creazione delle immagini viene usata la riga di comando seguente:

```shell
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

Se le immagini non includono una funzionalità di Visual Studio necessaria, comunicarlo tramite lo strumento per l'invio di commenti e suggerimenti nell'angolo in alto a destra della pagina.

## <a name="what-size-vm-should-i-choose"></a>Quali dimensioni di macchina virtuale scegliere
Azure offre una gamma completa di dimensioni di macchine virtuali. Poiché Visual Studio è un'applicazione multithreading potente, è necessaria una macchina virtuale che includa almeno due processori e 7 GB di memoria. Si consigliano le dimensioni di macchine virtuali seguenti per le immagini di Visual Studio:

   * Standard_D2_v3
   * Standard_D2s_v3
   * Standard_D4_v3
   * Standard_D4s_v3
   * Standard_D2_v2
   * Standard_D2S_v2
   * Standard_D3_v2

Per altre informazioni sulle dimensioni di macchina virtuale più recenti, vedere [Dimensioni per le macchine virtuali Windows in Azure](/azure/virtual-machines/windows/sizes).

Con Azure è possibile ribilanciare la configurazione iniziale ridimensionando la macchina virtuale. È possibile eseguire il provisioning di una nuova macchina virtuale con dimensioni più appropriate oppure ridimensionare la macchina virtuale esistente per hardware sottostante diverso. Per altre informazioni, vedere [Ridimensionare una VM Windows](/azure/virtual-machines/windows/resize-vm).

## <a name="after-the-vm-is-running-whats-next"></a>Operazioni successive all'installazione della macchina virtuale
Visual Studio segue il modello "Bring Your Own License" in Azure. Come per un'installazione in hardware proprietario, quindi, uno dei primi passaggi consiste nell'acquisire la licenza per l'installazione di Visual Studio. Per sbloccare Visual Studio:
- Eseguire l'accesso con un account Microsoft associato a una sottoscrizione di Visual Studio
- Sbloccare Visual Studio con il codice Product Key fornito al momento dell'acquisto iniziale

Per altre informazioni, vedere [Accedere a Visual Studio](../ide/signing-in-to-visual-studio.md) e [Come sbloccare Visual Studio](../ide/how-to-unlock-visual-studio.md).

## <a name="how-do-i-save-the-development-vm-for-future-or-team-use"></a>Come salvare la macchina virtuale per lo sviluppo per usi futuri

La gamma di possibili configurazioni degli ambienti di sviluppo è enorme e i costi sostenuti per la preparazione degli ambienti più complessi sono tutt'altro che irrilevanti. Indipendentemente dalla configurazione dell'ambiente, è possibile salvare, o acquisire, la macchina virtuale configurata come "immagine di base" per usi futuri o per altri membri del team. In questo modo, quando si avvia una nuova macchina virtuale è possibile eseguirne il provisioning dall'immagine di base anziché dall'immagine di Azure Marketplace.

Riepilogo rapido: usare l'utilità preparazione sistema (Sysprep) e arrestare la macchina virtuale in esecuzione, quindi acquisire *(figura 1)* la macchina virtuale come immagine tramite l'interfaccia utente nel portale di Azure. Azure salva il file `.vhd` che contiene l'immagine nell'account di archiviazione di propria scelta. La nuova immagine viene quindi visualizzata come risorsa Immagine nell'elenco di risorse della sottoscrizione.

<img src="media/capture-vm.png" alt="Capture an image through the Azure portal’s UI" style="border:3px solid Silver; display: block; margin: auto;"><center>*(Figura 1) Acquisire un'immagine tramite l'interfaccia utente del portale di Azure.*</center>

Per altre informazioni, vedere [Creare un'immagine gestita di una macchina virtuale generalizzata in Azure](/azure/virtual-machines/windows/capture-image-resource).

> [!IMPORTANT]
> Non dimenticare di usare Sysprep per preparare la macchina virtuale. Se si omette questo passaggio, Azure non può eseguire il provisioning di una macchina virtuale dall'immagine.

> [!NOTE]
> Si dovranno sostenere comunque alcuni costi per l'archiviazione delle immagini, ma questi costi aggiuntivi sono probabilmente insignificanti rispetto ai costi generali per ricostruire la macchina virtuale da zero per ogni membro del team che necessita di una macchina virtuale. Ad esempio, costa pochi euro al mese creare e archiviare un'immagine di 127 GB, riutilizzabile dall'intero team. Questi costi sono tuttavia irrisori se confrontati con le ore dedicate da ogni dipendente alla preparazione e alla convalida di una macchina virtuale per lo sviluppo adeguatamente configurata per l'uso individuale.

Inoltre, per le varie attività o tecnologie di sviluppo potrebbe essere necessaria una maggiore scalabilità, ad esempio una gamma di configurazioni per lo sviluppo e più configurazioni di macchina virtuale. È possibile usare Azure DevTest Labs per creare _recipe_ per automatizzare la costruzione dell'immagine finale. DevTest Labs consente anche di gestire i criteri per le macchine virtuali in esecuzione del team. [Using Azure DevTest Labs for developers](/azure/devtest-lab/devtest-lab-developer-lab) (Utilizzo di Azure DevTest Labs per gli sviluppatori) è la migliore fonte di informazioni su DevTest Labs.

## <a name="next-steps"></a>Passaggi successivi
Dopo aver raccolto informazioni sulle immagini di Visual Studio preconfigurate, il passaggio successivo consiste nel creare una nuova macchina virtuale:

* [Creare una macchina virtuale Windows con il portale di Azure](/azure/virtual-machines/windows/quick-create-portal)
* [Panoramica delle macchine virtuali Windows](/azure/virtual-machines/windows/overview)
