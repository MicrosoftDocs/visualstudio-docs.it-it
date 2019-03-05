---
title: Creare un'installazione di rete
description: Informazioni sulla creazione di un punto di installazione di rete per la distribuzione di Visual Studio in un'organizzazione.
ms.date: 02/12/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e25bdc20393c0d3faff5faa72c89bd531972e5d4
ms.sourcegitcommit: 1c8e07b98fc0a44b5ab90bcef77d9fac7b3eb452
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/25/2019
ms.locfileid: "56796400"
---
# <a name="create-a-network-installation-of-visual-studio-2017"></a>Creare un'installazione di rete di Visual Studio 2017

In genere un amministratore aziendale crea un punto di installazione di rete per la distribuzione nelle workstation client. Visual Studio 2017 è stato progettato in modo da consentire di memorizzare nella cache i file per l'installazione iniziale insieme a tutti gli aggiornamenti di prodotto in una singola cartella. Questo processo è anche definito _creazione di un layout_. 

Tale operazione è stata effettuata per consentire alle workstation client di poter utilizzare il medesimo percorso di rete per gestire l'installazione anche se non è stato ancora eseguito l’aggiornamento alla versione più recente per la manutenzione.

 > [!NOTE]
 > Se nell'azienda sono in uso più versioni di Visual Studio (ad esempio, Visual Studio Professional e Visual Studio Enterprise), è necessario creare una condivisione di installazione di rete separata per ogni edizione.

## <a name="download-the-visual-studio-bootstrapper"></a>Scaricare il programma di bootstrap di Visual Studio

Scaricare l'edizione di Visual Studio desiderata. Assicurarsi di fare clic su **Salva** e quindi su **Apri cartella**.

Il file eseguibile di installazione&mdash;o, per essere più specifici, il file di un programma di bootstrap&mdash;, deve corrispondere a uno dei seguenti.

|Edizione | Download|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=enterprise&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |
|Visual Studio Professional | [**vs_professional.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=professional&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |
|Community di Visual Studio | [**vs_community.exe**](https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=community&rel=15&utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=network+install&utm_content=download+vs2017) |

Altri programmi di bootstrap supportati includono [vs_buildtools.exe](https://aka.ms/vs/15/release/vs_buildtools.exe), [vs_feedbackclient.exe](https://aka.ms/vs/15/release/vs_feedbackclient.exe), [vs_teamexplorer.exe](https://aka.ms/vs/15/release/vs_teamexplorer.exe), [vs_testagent.exe](https://aka.ms/vs/15/release/vs_testagent.exe), [vs_testcontroller.exe](https://aka.ms/vs/15/release/vs_testcontroller.exe) e [vs_testprofessional.exe](https://aka.ms/vs/15/release/vs_testprofessional.exe).

## <a name="create-an-offline-installation-folder"></a>Creare una cartella di installazione offline

Per completare questo passaggio è necessario avere una connessione Internet. Per creare un'installazione offline con tutte le lingue e tutte le funzionalità, usare uno dei comandi degli esempi seguenti.

   > [!IMPORTANT]
   > Un layout di Visual Studio 2017 completo richiede almeno 35 GB di spazio su disco e, pertanto, può essere necessario molto tempo per scaricarlo.  Vedere la sezione [Personalizzazione del layout di rete](#customizing-the-network-layout) per informazioni su come creare un layout contenente solo i componenti che si vuole installare.
   >
   > [!TIP]
   > Assicurarsi di eseguire il comando dalla directory Download. In genere il percorso di questa cartella è `C:\Users\<username>\Downloads` in un computer con Windows 10.

- Per Visual Studio Enterprise, eseguire:

  ```vs_enterprise.exe --layout c:\vs2017offline```

- Per For Visual Studio Professional, eseguire:

  ```vs_professional.exe --layout c:\vs2017offline```

- Per Visual Studio Community, eseguire:

  ```vs_community.exe --layout c:\vs2017offline```

## <a name="modify-the-responsejson-file"></a>Modificare il file response.json

È possibile modificare il file response.json per impostare i valori predefiniti da usare quando viene eseguito il programma di installazione.  È possibile ,ad esempio, configurare il file `response.json` per selezionare un set specifico di carichi di lavoro selezionato in modo automatico.
Per informazioni dettagliate, vedere [Automatizzare l'installazione di Visual Studio con un file di risposta](automated-installation-with-response-file.md).

## <a name="copy-the-layout-to-a-network-share"></a>Copiare il layout in una condivisione di rete

Inserire il layout in una condivisione di rete affinché possa essere eseguito anche da altri computer.

Esempio:

```cmd
xcopy /e c:\vs2017offline \\server\products\VS2017
```

## <a name="customize-the-network-layout"></a>Personalizzare il layout di rete

Sono disponibili varie opzioni per personalizzare il layout di rete. È possibile, ad esempio, creare un layout parziale che contenga solo un set specifico di [impostazioni locali delle lingue](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales), [carichi di lavoro, componenti e relative dipendenze consigliate o facoltative](workload-and-component-ids.md). Questa soluzione potrebbe essere utile se si prevede di distribuire nelle workstation client solo un subset di carichi di lavoro. I parametri della riga di comando tipici per la personalizzazione del layout includono:

* `--add` per specificare ID di [carico di lavoro o di componente](workload-and-component-ids.md). <br>Se si usa `--add`, verranno scaricati solo i carichi di lavoro e i componenti specificati con `--add`.  Se non si usa `--add`, verranno scaricati tutti i carichi di lavoro e i componenti.
* `--includeRecommended` per includere tutti i componenti consigliati per gli ID di carico di lavoro specificati.
* `--includeOptional` per includere tutti i componenti consigliati e facoltativi per gli ID di carico di lavoro specificati.
* `--lang` per specificare le [impostazioni locali delle lingue](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

Gli esempi seguenti illustrano come creare un layout parziale personalizzato.

* Per scaricare tutti i carichi di lavoro e tutti i componenti per una sola lingua, eseguire:

    ```cmd
    vs_enterprise.exe --layout C:\vs2017offline --lang en-US
    ```

* Per scaricare tutti i carichi di lavoro e tutti i componenti per più lingue, eseguire:

    ```cmd
    vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP
    ```

* Per scaricare un solo carico di lavoro per tutte le lingue, eseguire:

    ```cmd
    vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --includeRecommended
    ```

* Per scaricare due carichi di lavoro e un solo componente facoltativo per tre lingue, eseguire:

    ```cmd
    vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP
    ```

* Per scaricare due carichi di lavoro e tutti i relativi componenti consigliati:

    ```cmd
    vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended 
    ```

* Per scaricare due carichi di lavoro e tutti i relativi componenti consigliati e facoltativi, eseguire:

    ```cmd
    vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional 
    ```

### <a name="new-in-153"></a>Novità nella versione 15.3

Quando si esegue un comando relativo al layout, le opzioni specificate vengono salvate (ad esempio le lingue e i carichi di lavoro). I comandi successivi relativi al layout includeranno tutte le opzioni precedenti.  Ecco un esempio di un layout con un carico di lavoro solo per la lingua inglese:

```cmd
vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --lang en-US
```

Quando si intende aggiornare il layout in questione a una versione più recente, non è necessario specificare i parametri della riga di comando aggiuntivi. Le impostazioni precedenti sono salvate e utilizzate da tutti i successivi comandi di layout in questa cartella di layout.  Il comando seguente aggiornerà il layout parziale esistente.

```cmd
vs_enterprise.exe --layout c:\VS2017Layout
```

Ecco un esempio di come eseguire questa operazione quando si desidera aggiungere un carico di lavoro aggiuntivo. In questo caso, verrà aggiunto il carico di lavoro di Azure e una lingua localizzata.  Il Desktop gestito e Azure sono ora inclusi in questo layout.  Sono incluse per tutti questi carichi di lavoro anche le risorse di lingua per inglese e tedesco. E il layout viene aggiornato all'ultima versione disponibile.

```cmd
vs_enterprise.exe --layout c:\VS2017Layout --add Microsoft.VisualStudio.Workload.Azure --lang de-DE
```

Se si desidera aggiornare un layout esistente a un layout completo, utilizzare l’opzione --all, come illustrato nell'esempio seguente.

```cmd
vs_enterprise.exe --layout c:\VS2017Layout --all
```

## <a name="deploy-from-a-network-installation"></a>Eseguire la distribuzione da un'installazione di rete

Gli amministratori possono distribuire Visual Studio nelle workstation client nell'ambito di uno script di installazione. In alternativa, gli utenti che hanno i diritti di amministratore possono installare Visual Studio nel proprio computer direttamente dalla condivisione.

* Gli utenti possono effettuare l'installazione eseguendo il comando seguente: <br>
    ```cmd
    \\server\products\VS2017\vs_enterprise.exe
    ```

* Gli amministratori possono effettuare l'installazione in modalità automatica eseguendo il comando seguente:
    ```cmd
    \server\products\VS2017\vs_enterprise.exe --quiet --wait --norestart
    ```

> [!IMPORTANT]
> Per evitare un errore, assicurarsi che il percorso di installazione completo sia composto da meno di 80 caratteri.
>
> [!TIP]
> Se Visual Studio viene eseguito nell'ambito di un file batch, l'opzione `--wait` garantisce che il processo `vs_enterprise.exe` attenda il completamento dell'installazione prima di restituire un codice di uscita.<br><br>Questa opzione è particolarmente utile se l'amministratore aziendale vuole eseguire altre azioni sull'installazione completa (ad esempio, [applicare un codice Product Key a un'installazione eseguita correttamente](automatically-apply-product-keys-when-deploying-visual-studio.md)) tuttavia occorre attendere il termine dell’installazione per gestire il corice di ritorno da tale installazione.<br><br>Se non si usa `--wait`, il processo `vs_enterprise.exe` verrà terminato prima del completamento dell'installazione e non verrà restituito un codice di uscita esatto che rappresenti lo stato dell'operazione di installazione.

Quando si installa da un layout, viene acquisito il contenuto che viene installato dal layout. Se tuttavia si seleziona un componente non presente nel layout, il componente viene acquisito da internet.  Se si desidera impedire che l’installazione di Visual Studio scarichi i contenuti mancanti nel layout, utilizzare l’opzione `--noWeb`. Se viene usato `--noWeb` ma nel layout non è presente almeno uno dei contenuti selezionati per l'installazione, il programma di installazione ha esito negativo.

> [!IMPORTANT]
> L'opzione `--noWeb` non impedisce al programma di installazione di Visual Studio di controllare la disponibilità di aggiornamenti. Per altre informazioni, vedere la pagina [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](controlling-updates-to-visual-studio-deployments.md).

### <a name="error-codes"></a>Codici di errore

Se è stato usato il parametro `--wait`, a seconda del risultato dell'operazione, la variabile di ambiente `%ERRORLEVEL%` viene impostata su uno dei valori seguenti:

  | **Valore** | **Risultato** |
  | --------- | ---------- |
  | 0 | L'operazione è riuscita |
  | 3010 | L'operazione è riuscita, ma è necessario riavviare per poter usare l'installazione |
  | Altro | Si è verificata una condizione di errore. Per altre informazioni, vedere i log |

## <a name="update-a-network-install-layout"></a>Aggiornare un layout di installazione di rete

Man mano che diventano disponibili nuovi aggiornamenti di prodotto, è possibile scegliere di [aggiornare il layout di installazione di rete](update-a-network-installation-of-visual-studio.md) in modo da integrare i pacchetti aggiornati.

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-2017-release"></a>Come creare un layout per una versione precedente di Visual Studio 2017

> [!NOTE]
> I programmi di bootstrap di Visual Studio 2017 disponibili in [visualstudio.microsoft.com](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) scaricano e installano la versione più recente di Visual Studio 2017 disponibile ogni volta che vengono eseguiti.<br><br>Pertanto se si scarica un *programma di bootstrap* di Visual Studio oggi e lo si esegue tra sei mesi, viene installata la versione di Visual Studio 2017 disponibile al momento dell'esecuzione del programma di bootstrap.<br><br>Se invece si crea un *layout* e si esegue l'installazione dal layout, viene installata la versione specifica di Visual Studio presente nel layout. Anche nel caso in cui sia disponibile online una versione più recente.

Se è necessario creare un layout per una versione precedente di Visual Studio 2017, accedere all'indirizzo [https://my.visualstudio.com](https://my.visualstudio.com) e scaricare le versioni "corrette" dei programmi di bootstrap di Visual Studio 2017.

### <a name="how-to-get-support-for-your-offline-installer"></a>Come ottenere supporto per il programma di installazione offline

Se si verifica un problema con l'installazione offline, è importante segnalarlo a Microsoft. Il modo migliore per farlo è tramite lo strumento [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md). Con questo strumento è possibile inviare a Microsoft i dati di telemetria e i log necessari per diagnosticare e risolvere il problema.

Per i problemi correlati all'installazione è disponibile anche un'opzione di supporto che offre una [**chat attiva**](https://visualstudio.microsoft.com/vs/support/#talktous) (solo in lingua inglese).

Sono disponibili anche altre opzioni per il supporto. Per un elenco, vedere la pagina [Comunicazioni con Microsoft](../ide/talk-to-us.md).

## <a name="see-also"></a>Vedere anche

* [Aggiornare un'installazione di rete di Visual Studio 2017](update-a-network-installation-of-visual-studio.md)
* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [ID dei carichi di lavoro e dei componenti di Visual Studio](workload-and-component-ids.md)
