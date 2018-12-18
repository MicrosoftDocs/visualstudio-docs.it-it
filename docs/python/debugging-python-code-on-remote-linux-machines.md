---
title: Debug di codice Python in esecuzione in computer Linux remoti con Visual Studio | Microsoft Docs
description: Come usare Visual Studio per il debug del codice Python in esecuzione in computer Linux remoti, inclusi i passaggi di configurazione necessari, la sicurezza e la risoluzione dei problemi.
ms.custom: 
ms.date: 07/12/2017
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
ms.openlocfilehash: 765d42de00c5fa716cd1445301136d8f7a39c2ec
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2018
---
# <a name="remotely-debugging-python-code-on-linux"></a>Debug remoto di codice Python in Linux

Visual Studio consente di avviare le applicazioni Python e di eseguirne il debug in locale e in remoto in un computer Windows. Vedere [Remote Debugging](../debugger/remote-debugging.md) (Debug remoto). È anche possibile eseguire il debug in remoto su un altro sistema operativo o dispositivo oppure su un'implementazione di Python diversa da CPython usando la [libreria ptvsd](https://pypi.python.org/pypi/ptvsd).

Quando si usa ptvsd, il codice Python di cui si esegue il debug ospita il server di debug a cui può collegarsi Visual Studio. L'hosting richiede una piccola modifica del codice per importare e abilitare il server e potrebbe richiedere configurazioni della rete o del firewall nel computer remoto per consentire le connessioni TCP.

|   |   |
|---|---|
| ![icona della telecamera](../install/media/video-icon.png "Guardare un video") | Per un'introduzione al debug remoto, vedere [Deep Dive: Cross-Platform Remote Debugging](https://youtu.be/y1Qq7BrV6Cc) (Approfondimento: il debug multipiattaforma) (youtube.com, 6m22s), applicabile sia a Visual Studio 2015 che a Visual Studio 2017. |

## <a name="setting-up-a-linux-computer"></a>Impostazione di un computer Linux

Per eseguire questa procedura dettagliata sono necessari gli elementi seguenti:

- Un computer remoto che esegue Python in un sistema operativo come Mac OSX o Linux.
- La porta 5678 (in ingresso) deve essere aperta nel firewall di tale computer, in base all'impostazione predefinita per il debug remoto.

È possibile creare facilmente [macchine virtuali Linux in Azure](/azure/virtual-machines/linux/creation-choices) e [accedervi usando Desktop remoto](/azure/virtual-machines/linux/use-remote-desktop) da Windows. L'uso di Ubuntu per la macchina virtuale è comodo perché Python è installato per impostazione predefinita. Se si preferisce scegliere un altro percorso di download per Python, vedere l'elenco di opzioni in [Selezione e installazione di interpreti Python](managing-python-environments-in-visual-studio.md#selecting-and-installing-python-interpreters).

Per informazioni dettagliate sulla creazione di una regola del firewall per una macchina virtuale di Azure, vedere [Apertura di porte su una VM tramite il portale di Azure](/azure/virtual-machines/windows/nsg-quickstart-portal).

## <a name="preparing-the-script-for-debugging"></a>Preparazione dello script per il debug

1. Nel computer remoto creare un file Python denominato `guessing-game.py` con il codice seguente:

  ```python
  import random

  guesses_made = 0
  name = input('Hello! What is your name?\n')
  number = random.randint(1, 20)
  print('Well, {0}, I am thinking of a number between 1 and 20.'.format(name))

  while guesses_made < 6:
      guess = int(input('Take a guess: '))
      guesses_made += 1
      if guess < number:
          print('Your guess is too low.')
      if guess > number:
          print('Your guess is too high.')
      if guess == number:
          break
  if guess == number:
      print('Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made))
  else:
      print('Nope. The number I was thinking of was {0}'.format(number))
  ```
 
1. Installare il pacchetto `ptvsd` nell'ambiente usando `pip3 install ptvsd`. Nota: si consiglia di registrare la versione di ptvsd installata nel caso in cui fosse necessaria per la risoluzione dei problemi. Nell'[elenco ptvsd](https://pypi.python.org/pypi/ptvsd) sono indicate anche le versioni disponibili.

1. Abilitare il debug remoto aggiungendo il codice seguente nel primo punto possibile in `guessing-game.py`, prima di altro codice. Anche se non è un requisito vincolante, non è possibile eseguire il debug di qualsiasi thread in background generato prima della chiamata della funzione `enable_attach`.

   ```python
   import ptvsd
   ptvsd.enable_attach('my_secret')
   ```

   Il primo argomento passato a `enable_attach`, detto "segreto", limita l'accesso allo script in esecuzione e deve essere immesso quando si collega il debugger remoto. Non è consigliabile, ma è possibile consentire a chiunque di connettersi usando `enable_attach(secret=None)`.

1. Salvare il file ed eseguire `python3 guessing-game.py`. La chiamata a `enable_attach` viene eseguita in background e attende connessioni in ingresso quando si interagisce in altro modo con il programma. Se richiesto, è possibile chiamare la funzione `wait_for_attach` dopo `enable_attach` per bloccare il programma fino al collegamento del debugger.

> [!Tip]
> Oltre a `enable_attach` e `wait_for_attach`, ptvsd offre anche una funzione helper `break_into_debugger`, che funge da punto di interruzione programmatico se il debugger è collegato. È anche disponibile una funzione `is_attached` che restituisce `True` se il debugger è collegato (si noti che non è necessario verificare questo risultato prima di chiamare qualsiasi altra funzione `ptvsd`).

## <a name="attaching-remotely-from-python-tools"></a>Collegamento remoto da Python Tools

In questa procedura viene impostato un semplice punto di interruzione per arrestare il processo remoto.

1. Creare una copia del file remoto nel computer locale e aprirlo in Visual Studio. La posizione del file non è importante, ma il relativo nome deve corrispondere al nome dello script nel computer remoto.

1. (Facoltativo) Per usare IntelliSense per ptvsd nel computer locale, installare il pacchetto ptvsd nell'ambiente Python.

1. Selezionare **Debug > Connetti a processo**.

1. Nella finestra di dialogo **Connetti a processo** visualizzata impostare **Tipo di connessione** su **Python remote (ptvsd)** (Python remoto). Nelle versioni precedenti di Visual Studio questi comandi sono denominati rispettivamente **Trasporto** e **Debug remoto Python**.

1. Nel campo **Destinazione della connessione**, **Qualificatore** nelle versioni precedenti, immettere `tcp://<secret>@<ip_address>:5678`, dove `<secret>` è la stringa passata a `enable_attach` nel codice Python, `<ip_address>` è l'indirizzo IP del computer remoto, che può essere un indirizzo esplicito o un nome simile a myvm.cloudapp.net, e `:5678` è il numero di porta del debug remoto.

    > [!Warning]
    > Se si sta effettuando una connessione sulla rete Internet pubblica, è preferibile usare invece `tcps` e seguire l'istruzione seguente per [proteggere la connessione del debugger con SSL](#securing-the-debugger-connection-with-ssl).

1. Premere Invio per compilare l'elenco dei processi ptvsd disponibili in quel computer:

    ![Immissione della destinazione di connessione e indicazione dei processi](media/remote-debugging-qualifier.png)

    Se si avvia un altro programma nel computer remoto dopo la compilazione di questo elenco, selezionare il pulsante **Aggiorna**.

1. Selezionare il processo per cui eseguire il debug e quindi **Allega** oppure fare doppio clic sul processo.

1. Visual Studio passa quindi in modalità di debug mentre lo script continua l'esecuzione nel computer remoto, rendendo disponibili tutte le consuete funzionalità di [debug](debugging-python-in-visual-studio.md). Ad esempio, impostare un punto di interruzione sulla riga `if guess < number:`, quindi passare al computer remoto e immettere un'altra proposta. Al termine dell'operazione, Visual Studio si arresta nel computer locale in corrispondenza di tale punto di interruzione, indica le variabili locali e così via:

    ![Punto di interruzione raggiunto](media/remote-debugging-breakpoint-hit.png)

1. Quando si arresta il debug, Visual Studio si disconnette dal programma, che rimane in esecuzione nel computer remoto. Ptvsd rimane in ascolto del collegamento di debugger, quindi è possibile eseguire di nuovo la connessione al processo in qualsiasi momento.

### <a name="connection-troubleshooting"></a>Risoluzione dei problemi di connessione

1. Verificare che sia selezionata l'opzione **Python remote (ptvsd)** (Python remoto) per **Tipo di connessione** (**Debug remoto Python** per **Trasporto** nelle versioni precedenti).
1. Verificare che il segreto in **Destinazione della connessione** (o **Qualificatore**) corrisponda esattamente al segreto nel codice remoto.
1. Verificare che l'indirizzo IP in **Destinazione della connessione** (o **Qualificatore**) corrisponda esattamente a quello del computer remoto.
1. Verificare che la porta di debug remoto sia aperta nel computer remoto e che il suffisso di porta sia incluso nella destinazione di connessione, ad esempio `:5678`.
    - Se è necessario usare un'altra porta, è possibile specificarla nella chiamata a `enable_attach` usando l'argomento `address`, come in `ptvsd.enable_attach(secret = 'my_secret', address = ('0.0.0.0', 8080))`. In questo caso, aprire quella porta specifica nel firewall.
1. Verificare nella tabella seguente che la versione di ptvsd installata nel computer remoto e restituita da `pip3 list` corrisponda a quella usata dalla versione degli strumenti Python in uso in Visual Studio. Se necessario, aggiornare ptvsd nel computer remoto.

    | Versione di Visual Studio | Versione di strumenti Python/ptvsd |
    | --- | --- |
    | 2017 15.3 | 3.2.0 |
    | 2017 15.2 | 3.1.0 |
    | 2017 15.0, 15.1 | 3.0.0 |
    | 2015 | 2.2.6 |
    | 2013 | 2.2.2 |
    | 2012, 2010 | 2.1 |

## <a name="securing-the-debugger-connection-with-ssl"></a>Protezione della connessione del debugger con SSL

Per impostazione predefinita, la connessione al server di debug remoto di ptvsd è protetta solo dal segreto e tutti i dati vengono passati come testo normale. Per proteggere maggiormente la connessione, ptvsd supporta SSL, che deve essere impostato come indicato di seguito:

1. Nel computer remoto generare un certificato autofirmato separato e i file di chiave usando il comando openssl:

    ```command
    openssl req -new -x509 -days 365 -nodes -out cert.cer -keyout cert.key
    ```

    Quando openssl richiede il **nome comune** usare il nome host o l'indirizzo IP, a seconda dell'opzione scelta per la connessione.

    Per maggiori dettagli, vedere la sezione relativa ai [certificati autofirmati](http://docs.python.org/3/library/ssl.html#self-signed-certificates) nei documenti del modulo `ssl` di Python. Si noti che il comando in tali documenti genera solo un singolo file combinato.

1. Nel codice modificare la chiamata a `enable_attach` per includere gli argomenti `certfile` e `keyfile` usando i nomi di file come valori. Questi argomenti hanno lo stesso significato per la funzione `ssl.wrap_socket` standard di Python:

    ```python
    ptvsd.enable_attach(secret='my_secret', certfile='cert.cer', keyfile='cert.key')
    ```

    È anche possibile apportare la stessa modifica nel file di codice nel computer locale, ma poiché il codice non viene effettivamente eseguito, non è strettamente necessario.

1. Riavviare il programma Python nel computer remoto, in modo che sia pronto per il debug.

1. Proteggere il canale aggiungendo il certificato alla CA radice attendibile nel computer Windows con Visual Studio:

    1. Copiare il file del certificato dal computer remoto al computer locale.
    1. Aprire il Pannello di controllo e passare a **Strumenti di amministrazione > Gestisci i certificati computer**.
    1. Nella finestra visualizzata espandere **Autorità di certificazione radice attendibili** sul lato sinistro, fare clic con il pulsante destro del mouse su **Certificati** e selezionare **Tutte le attività > Importa...**.
    1. Individuare e selezionare il file `.cer` copiato dal computer remoto, quindi fare clic nelle finestre di dialogo per completare l'importazione.

1. Ripetere il processo di associazione in Visual Studio come descritto in precedenza, usando ora `tcps://` come protocollo per **Destinazione della connessione** (o **Qualificatore**).

    ![Scelta del trasporto di debug remoto con SSL](media/remote-debugging-qualifier-ssl.png)

### <a name="warnings"></a>Avvisi

Visual Studio chiede informazioni sui potenziali problemi di certificato durante la connessione con SSL, come descritto di seguito. È possibile ignorare gli avvisi e continuare, ma anche se il canale rimane crittografato per evitare intercettazioni, può comunque essere vulnerabile agli attacchi di tipo man-in-the-middle.

1. Se appare l'avviso "il certificato remoto non è attendibile", significa che il certificato non è stato aggiunto correttamente alla CA radice attendibile. Verificare questi passaggi e riprovare.

    ![Avviso su attendibilità del certificato SSL](media/remote-debugging-ssl-warning.png)

1. Se appare l'avviso "il nome del certificato remoto non corrisponde al nome host", significa che non è stato usato il nome host o l'indirizzo IP corretto come **nome comune** durante la creazione del certificato.

    ![Avviso sul nome host del certificato SSL](media/remote-debugging-ssl-warning2.png)

> [!Warning]
> Al momento Visual Studio 2017 si blocca se si ignorano questi avvisi. Assicurarsi di correggere tutti i problemi prima di tentare la connessione.
