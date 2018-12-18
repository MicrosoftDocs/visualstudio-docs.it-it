---
title: Installazione degli strumenti di intelligenza artificiale per Visual Studio
description: Installazione degli strumenti di intelligenza artificiale per Visual Studio
keywords: ia, visual studio
author: lisawong19
ms.author: liwong
manager: routlaw
ms.date: 11/13/2017
ms.topic: article
ms.devlang: multiple
ms.service: multiple
ms.technology: vs-ai-tools
ms.workload:
- multiple
ms.openlocfilehash: 7e182a000dc9c8aaeb721b81036f878430260618
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/28/2018
---
# <a name="installation"></a>Installazione

È possibile installare gli strumenti di Visual Studio per IA nei sistemi operativi Windows a 64 bit.

## <a name="installing-visual-studio-tools-for-ai"></a>Installazione degli strumenti di Visual Studio per IA

L'estensione può essere usata con [Visual Studio](https://docs.microsoft.com/visualstudio/) 2015, 2017, con l'edizione Community o versioni successive.

Per eseguire l'installazione, scaricare il download da [Visual Studio Marketplace](http://aka.ms/vstoolsforai) o da Visual Studio

1. **Strumenti**> **Estensioni e aggiornamenti**

![Installare CUDA in Windows](media\installation\extensions.png)

1. Scegliere **Ricerca** nell'angolo superiore destro per "Tools for AI" (Strumenti per IA)
2. Selezionare **Visual Studio Tools for AI** (Strumenti di Visual Studio per IA)
3. Fare clic su **Download**


## <a name="preparing-your-local-machine"></a>Preparazione del computer locale

Prima di eseguire modelli di apprendimento profondo nel computer locale, assicurarsi di aver installato la versione più recente dei prerequisiti appropriati. Ciò include la versione più recente dei driver e delle raccolte per la GPU NVIDIA, se presente. È necessario anche assicurarsi di aver installato Python e le raccolte Python, ad esempio NumPy, SciPy e i framework dell'apprendimento profondo, ad esempio Microsoft Cognitive Toolkit (CNTK), TensorFlow, Caffe2, MXNet, Keras, Theano, PyTorch e/o Chainer, che si prevede di usare nel progetto.

> [!NOTE]
>
> Le introduzioni ai software nelle sottosezioni riportate di seguito sono state estratte dalle relative home page.

### <a name="nvidia-gpu-driver"></a>Driver della GPU NVIDIA

I framework dell'apprendimento profondo sfruttano la GPU NVIDIA per consentire alle macchine di apprendere con una velocità, precisione e scalabilità tipiche della vera e propria intelligenza artificiale. Se il computer ha schede GPU NVIDIA, visitare [questo sito](http://www.nvidia.com/Download/index.aspx) o aggiornare il sistema operativo per installare il driver più recente.

### <a name="cuda"></a>CUDA

[CUDA](https://developer.nvidia.com/cuda-zone) è una piattaforma di elaborazione parallela e un modello di programmazione ideato da NVIDIA.
Consente un aumento considerevole delle prestazioni di elaborazione sfruttando la potenza della GPU.
Attualmente, i framework di apprendimento profondo richiedono il toolkit CUDA 8.0.

Per installare CUDA

- Visitare questo [sito](https://developer.nvidia.com/cuda-80-ga2-download-archive), scaricare CUDA e installarlo.
- Assicurarsi di installare le librerie di runtime CUDA e aggiungere il percorso del file binario CUDA alla variabile di ambiente %$Path% o $Path.
- Per impostazione predefinita, in Windows il percorso è "C:\Programmi\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin".

![Installare CUDA in Windows](media\installation\install_cuda_win.png)

### <a name="cudnn"></a>cuDNN

[cuDNN](https://developer.nvidia.com/cudnn) (CUDA Deep Neural Network library, libreria di reti neurali profonde CUDA) è una libreria con accelerazione GPU di primitive per reti neurali profonde ideata da NVIDIA. Per i framework di apprendimento profondo più recenti è necessaria la versione 6 di cuDNN.

Per installare cuDNN
- Visitare [questo sito](https://developer.nvidia.com/rdp/cudnn-download) per scaricare e installare il pacchetto più recente.
- Assicurarsi di aggiungere la directory contenente il file binario cuDNN alla variabile di ambiente %$Path% o $Path.
- In Windows è possibile copiare cudnn64_6.dll in "C:\Programmi\NVIDIA GPU Computing Toolkit\CUDA\v8.0\bin".

> [!NOTE]
>
> Per i framework di apprendimento profondo più recenti, come ad esempio CNTK 2.0 e TensorFlow 1.2.1, è richiesta la versione 5.1 di cuDNN.
> Tuttavia, è possibile installare più versioni di cuDNN insieme.


### <a name="python"></a>Python

Python è il linguaggio di programmazione principale per le applicazioni di apprendimento profondo.
È richiesta la distribuzione di Python a **64 bit** ed è consigliabile installare [Python 3.5.4](https://www.python.org/downloads/release/python-354/) per una compatibilità ottimale.

### <a name="to-install-python-on-windows"></a>Per installare Python in Windows
- È consigliabile installare solo l'utilità di avvio e di aggiungere Python alla variabile di ambiente %PATH%.
- Assicurarsi di installare pip, ovvero il sistema di gestione pacchetti per installare e gestire i pacchetti software scritti in Python.

L'installazione dei framework di apprendimento profondo si basa su pip.

![installare Python in Windows](media\installation\install_python_win.png)

In seguito, è necessario verificare se Python 3.5 sia installato correttamente e aggiornare pip alla versione più recente eseguendo i comandi seguenti in un terminale:

- **Windows**
    ```cmd
    C:\Users\test>python -V
    Python 3.5.4

    C:\Users\test>pip3.5 -V
    pip 9.0.1 from c:\users\test\appdata\local\programs\python\python35\lib\site-packages (python 3.5)

    C:\Users\test>python -m pip install -U pip
    ```

- **macOS**
    ```bash
    MyMac:~ test$ python3.5 -V
    Python 3.5.4

    MyMac:~ test$ pip3.5 -V
    pip 9.0.1 from /Library/Frameworks/Python.framework/Versions/3.5/lib/python3.5/site-packages (python 3.5)

    MyMac:~ test$ python3.5 -m pip install -U pip
    ```

### <a name="python-on-visual-studio"></a>Python in Visual Studio

Il supporto completo di Python in Visual Studio è garantito dalle estensioni.
Per altre informazioni sull'installazione, vedere [Installazione del supporto di Python in Visual Studio in Windows](../python/installing-python-support-in-visual-studio.md).

### <a name="numpy-and-scipy"></a>NumPy e SciPy

- **NumPy** è un pacchetto di elaborazione di matrici generico progettato per modificare in modo efficiente matrici multidimensionali di record arbitrari di dimensioni elevate senza compromettere la velocità per le matrici multidimensionali di piccole dimensioni.

- **SciPy** (pronunciato come l'inglese "Sigh Pie") è un software open source destinato all'ambito matematico, scientifico e tecnico, che dipende da NumPy.
A partire dalla versione 1.0.0, SciPy ha un pacchetto precompilato per Windows.

Per installare NumPy e SciPy, eseguire il comando seguente in un terminale:
```bash
pip3.5 install -U numpy scipy
```

> [!NOTE]
>
> Il comando precedente aggiorna le installazioni di NumPy e SciPy obsolete o non ufficiali, ad esempio, pacchetti di terze parti da http://www.lfd.uci.edu/~gohlke/pythonlibs/ for Windows.

### <a name="microsoft-cognitive-toolkit-cntk"></a>Microsoft Cognitive Toolkit (CNTK)

[Microsoft Cognitive Toolkit](https://cntk.ai) è un toolkit di apprendimento profondo unificato che descrive le reti neurali come una serie di passaggi di elaborazione tramite un digrafo. CNTK supporta sia il linguaggio di programmazione Python che BrainScript.

> [!NOTE]
>
> Al momento CNTK non supporta macOS.

Per installare il pacchetto di Python CNTK, vedere [How to install CNTK](https://docs.microsoft.com/cognitive-toolkit/Setup-CNTK-on-your-machine) (Come installare CNTK)

### <a name="tensorflow"></a>TensorFlow

[TensorFlow](https://www.tensorflow.org/) è una libreria di software open source per calcoli numerici che usa rappresentazioni dei flussi di dati.
Per la procedura dettagliata di installazione, fare clic [qui](https://www.tensorflow.org/install/).

> [!NOTE]
>
> A partire dalla versione 1.2, TensorFlow non supporta più la GPU per macOS.

### <a name="caffe2"></a>Caffe2

[Caffe2](https://caffe2.ai/) è un framework di apprendimento profondo leggero, modulare e scalabile.
Compilato sulla base di Caffe, Caffe2 è progettato per espressione, velocità e modularità.

Attualmente, non vi sono pacchetti di Caffe2 precompilati per Python.

Visitare [questo sito](https://caffe2.ai/docs/getting-started.html) per eseguire la compilazione dal codice sorgente.

### <a name="mxnet"></a>MXNet

[Apache MXNet (incubating)](https://mxnet.incubator.apache.org/) è un framework di apprendimento profondo progettato per efficienza e flessibilità.
Consente di **combinare** [programmazione simbolica e imperativa](http://mxnet.io/architecture/index.html#deep-learning-system-design-concepts) per ottimizzare efficienza e produttività.

Per installare MXNet, eseguire il comando seguente in un terminale:
- Con GPU
    ```bash
    pip3.5 install mxnet-cu80==0.12.0
    ```
- Senza GPU
    ```bash
    pip3.5 install mxnet==0.12.0
    ```

### <a name="keras"></a>Keras

[Keras](https://keras.io/) è un'API di alto livello per reti neurali, scritta in Python e che può essere eseguita con CNTK, TensorFlow o Theano. È stata sviluppata allo scopo di consentire la sperimentazione veloce. La possibilità di passare dall'idea al risultato senza perdere tempo è fondamentale per una ricerca di buon livello.

Per installare Keras, eseguire il comando seguente in un terminale:
```bash
pip3.5 install Keras==2.0.9
```

### <a name="theano"></a>Theano

[Theano](http://deeplearning.net/software/theano/) è una libreria Python che consente di definire, ottimizzare e valutare in modo efficiente espressioni matematiche che coinvolgono matrici multidimensionali.

Per installare Theano, eseguire il comando seguente in un terminale:
```bash
pip3.5 install Theano==0.9.0
```

### <a name="pytorch"></a>PyTorch

[PyTorch](http://pytorch.org/) è un pacchetto Python che offre due funzionalità di alto livello:
- Calcolo del tensore, come NumPy, con un'accelerazione della GPU notevole
- Reti neurali profonde generate a partire da un sistema di differenziazione automatica basato su nastro

Per installare PyTorch, eseguire il comando seguente in un terminale:

- **Windows**
    - Non è ancora disponibile un pacchetto ufficiale. È possibile scaricare un [pacchetto Anaconda PyTorch](https://anaconda.org/peterjc123/pytorch/0.2.1/download/win-64/pytorch-0.2.1-py35h24644ff_0.2.1cu80.tar.bz2) di terze parti.
    - Decomprimerlo nella directory principale, ad esempio "C:\Utenti\test\pytorch".
    - Aggiungere "C:\Utenti\test\pytorch\Lib\site-packages" alla variabile di ambiente % PYTHONPATH%.

- **macOS**
    ```bash
    pip3.5 install http://download.pytorch.org/whl/torch-0.2.0.post3-cp35-cp35m-macosx_10_7_x86_64.whl
    ```
    > [!NOTE]
    >
    > I file binari macOS non supportano CUDA. Se necessario, eseguire l'installazione dai file di origine

- **Linux**
    ```bash
    pip3.5 install http://download.pytorch.org/whl/cu80/torch-0.2.0.post3-cp35-cp35m-manylinux1_x86_64.whl
    ```
    > [!NOTE]
    >
    > Il pacchetto singolo supporta sia GPU che CPU.

Infine, installare il pacchetto torchvision per sistemi non-Windows:
```bash
pip3.5 install torchvision
```

### <a name="chainer"></a>Chainer

[Chainer](https://chainer.org/) è un framework di apprendimento profondo basato su Python che ottimizza la flessibilità.
Offre API di differenziazione automatica basate sull'**approccio define-by-run**, ovvero sui grafici di calcolo dinamico, nonché su API di alto livello orientate agli oggetti per sfruttare e addestrare le reti neurali.

Per abilitare il supporto CUDA, installare [CuPy](https://github.com/cupy/cupy):
```bash
pip3.5 install cupy
```

> [!NOTE]
>
> In Windows è necessaria la versione **2015** di [Microsoft Visual Studio](https://www.visualstudio.com/) o [Microsoft Visual C++ Build Tools](http://landinghub.visualstudio.com/visual-cpp-build-tools) per compilare CuPy con CUDA 8.0.

Per installare Chainer, eseguire il comando seguente in un terminale:
```bash
pip3.5 install chainer==3.0.0
```


