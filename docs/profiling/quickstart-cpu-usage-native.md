---
title: Analizzare i dati d'uso della CPU (C++) | Microsoft Docs
ms.custom: ''
ms.date: 12/05/2017
ms.technology: vs-ide-debug
ms.topic: quickstart
f1_keywords:
- ''
helpviewer_keywords:
- Profiling Tools, quick start
- Diagnostics Tools, CPU Usage
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 52483a920d47b5728645ae195bc1837c7ccc565b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="analyze-cpu-usage-data-in-visual-studio-c"></a>Analizzare i dati d'uso della CPU in Visual Studio (C++)

Visual Studio dispone di molte funzionalità avanzate per l'analisi dei problemi di prestazioni nell'applicazione. Questo argomento consente di apprendere in modo rapido come usare alcune funzionalità di base. In questo caso si esamina lo strumento che identifica eventuali colli di bottiglia delle prestazioni dovuti a un uso intensivo della CPU. Gli strumenti di diagnostica sono supportati per lo sviluppo di .NET in Visual Studio, incluso ASP.NET, e per lo sviluppo nativo/C++.

L'hub diagnostica include numerose altre opzioni per eseguire e gestire la sessione di diagnostica. Se lo strumento **Utilizzo CPU** descritto qui non offre i dati necessari, gli [altri strumenti di profilatura](../profiling/profiling-feature-tour.md) mettono a disposizione diversi tipi di informazioni che possono risultare utili. In molti casi il collo di bottiglia delle prestazioni dell'applicazione può dipendere da un fattore diverso dalla CPU, ad esempio la memoria, il rendering dell'interfaccia utente o il tempo di richiesta di rete. L'hub diagnostica offre molte altre opzioni per la registrazione e l'analisi di questo tipo di dati.

## <a name="create-a-project"></a>Creare un progetto

1. In Visual Studio scegliere **File > Nuovo progetto**.

2. In **Visual C++** scegliere **Desktop di Windows** e nel riquadro al centro scegliere **Applicazione console di Windows**.

3. Digitare un nome come **Diagnostics_Get_Started_Native** e fare clic su **OK**.

    Visual Studio crea il progetto.

4. In MyDbgApp.cpp sostituire il codice seguente

    ```c++
    int main()
    {
        return 0;
    }
    ```

    con questo codice (non rimuovere `#include "stdafx.h"`):

    ```c++
    #include <iostream>
    #include <limits>
    #include <mutex>
    #include <random>
    #include <functional>
    
    //.cpp file code:
    
    static constexpr int MIN_ITERATIONS = std::numeric_limits<int>::max() / 1000;
    static constexpr int MAX_ITERATIONS = MIN_ITERATIONS + 10000;
    
    long long m_totalIterations = 0;
    std::mutex m_totalItersLock;
    
    int getNumber()
    {
    
        std::uniform_int_distribution<int> num_distribution(MIN_ITERATIONS, MAX_ITERATIONS);
        std::mt19937 random_number_engine; // pseudorandom number generator
        auto get_num = std::bind(num_distribution, random_number_engine);
        int random_num = get_num();
    
        auto result = 0;
        {
            std::lock_guard<std::mutex> lock(m_totalItersLock);
            m_totalIterations += random_num;
        }
        // we're just spinning here  
        // to increase CPU usage 
        for (int i = 0; i < random_num; i++)
        {
            result = get_num();
        }
        return result;
    }
    
    void doWork()
    {
        std::wcout << L"The doWork function is running on another thread." << std::endl;
    
        auto x = getNumber();    
    }
    
    int main()
    {
        std::vector<std::thread> threads;
    
        for (int i = 0; i < 10; ++i) {
    
            threads.push_back(std::thread(doWork));
            std::cout << "The Main() thread calls this after starting the new thread" << std::endl;
        }
    
        for (auto& thread : threads) {
            thread.join();
        }
    
        return 0;
    }
    ```
  
##  <a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Passaggio 1: Raccogliere i dati di profilatura 
  
1.  In primo luogo impostare un punto di interruzione dell'app su questa riga di codice nella funzione `main`:

    `for (int i = 0; i < 10; ++i) {`

    Per impostare un punto di interruzione fare clic sul margine a sinistra della riga di codice.

2.  Impostare quindi un secondo punto di interruzione sulla parentesi graffa di chiusura alla fine della funzione `main`:

     ![Impostare punti di interruzione per la profilatura](../profiling/media/quickstart-cpu-usage-breakpoints-cplusplus.png "Impostare punti di interruzione per la profilatura")

    > [!TIP]
    > Impostando i due punti di interruzione è possibile limitare la raccolta dei dati per le parti di codice che si vuole analizzare.
  
3.  La finestra **Strumenti di diagnostica** è già visibile, a meno che non sia stata disattivata. Per visualizzare di nuovo la finestra, fare clic su **Debug/Windows/Mostra strumenti di diagnostica**.

4.  Fare clic su **Debug / Avvia debug** (o **Avvia** sulla barra degli strumenti o **F5**).

     Al termine del caricamento dell'applicazione viene visualizzata la vista **Riepilogo** degli strumenti di diagnostica.

5.  Quando il debugger è in pausa, abilitare la raccolta dei dati relativi all'utilizzo della CPU scegliendo **Registra profilo CPU**, quindi aprire la scheda **Utilizzo CPU**.

     ![Abilitazione profilatura CPU in Strumenti di diagnostica](../profiling/media/quickstart-cpu-usage-summary.png "Abilitazione profilatura CPU in Strumenti di diagnostica")

     Quando la raccolta dei dati è abilitata, il pulsante di registrazione visualizza un cerchio rosso.

     Quando si sceglie **Registra profilo CPU** Visual Studio inizia a registrare le funzioni e il tempo necessario per l'esecuzione e crea un grafico della sequenza temporale, utile per concentrarsi su segmenti specifici della sessione di campionamento. È possibile visualizzare i dati raccolti solo quando l'esecuzione dell'applicazione si interrompe in corrispondenza di un punto di interruzione.

6.  Premere F5 per eseguire l'applicazione fino al secondo punto di interruzione.

     Ora si hanno a disposizione i dati relativi alle prestazioni per l'applicazione, precisamente per l'area di codice compresa tra i due punti di interruzione.

     Il profiler inizia a preparare i dati di thread. Attendere il completamento.
  
     Lo strumento Utilizzo CPU consente di visualizzare il report nella scheda **Utilizzo CPU**.

     A questo punto, è possibile iniziare ad analizzare i dati.

## <a name="Step2"></a> Passaggio 2: Analizzare i dati di utilizzo della CPU

È consigliabile iniziare ad analizzare i dati esaminando l'elenco di funzioni in Utilizzo CPU, identificando le funzioni che svolgono la maggior parte del lavoro e quindi concentrandosi su ognuna di esse.

1. Nell'elenco delle funzioni esaminare le funzioni che eseguono il maggior numero di operazioni.

     ![Strumenti di diagnostica - Scheda Utilizzo CPU](../profiling/media/quickstart-cpu-usage-cpu-cplusplus.png "DiagToolsCPUUsageTab")

    > [!TIP]
    > Le funzioni sono elencate in ordine a partire da quelle che svolgono la maggior parte del lavoro (non sono in ordine di chiamata). Ciò consente di identificare rapidamente le funzioni in esecuzione da più tempo.

2. Nell'elenco delle funzioni fare doppio clic sulla funzione `getNumber`.

    Quando si fa doppio clic su una funzione viene aperta la visualizzazione **Chiamante/chiamato** nel riquadro a sinistra. 

    ![Strumenti di diagnostica Visualizzazione Chiamante Chiamato](../profiling/media/quickstart-cpu-usage-caller-callee-cplusplus.png "DiagToolsCallerCallee")

    In questa visualizzazione la funzione selezionata viene visualizzata nell'intestazione e nella casella **Funzione corrente** (in questo esempio `getNumber`). La funzione che ha chiamato la funzione corrente viene visualizzata a sinistra, sotto **Funzioni chiamanti**, e tutte le funzioni chiamate dalla funzione corrente sono riportate nella casella **Funzioni chiamate** sulla destra. Selezionare una delle due caselle per modificare la funzione corrente.

    Questa visualizzazione indica il tempo totale (ms) e la percentuale del tempo complessivo di esecuzione dell'applicazione dedicato al completamento della funzione.

    **Corpo funzione** indica anche la quantità totale di tempo (e la percentuale di tempo) impiegata nel corpo della funzione, escluso il tempo dedicato alle funzioni chiamanti e chiamate. In questo esempio 119 ms su 43602 totali sono stati usati per il corpo della funzione e il tempo rimanente per il codice esterno chiamato dalla funzione. I valori reali saranno molto diversi a seconda dell'ambiente.

    > [!TIP]
    > Valori elevati in **Corpo funzione** possono indicare un collo di bottiglia delle prestazioni all'interno della funzione stessa.

## <a name="next-steps"></a>Passaggi successivi

- [Analizzare l'uso della memoria](../profiling/memory-usage.md) per identificare colli di bottiglia delle prestazioni.
- [Analizzare l'uso della CPU](../profiling/cpu-usage.md) per informazioni dettagliate sullo strumento Utilizzo CPU.
- Analizzare l'uso della CPU senza un debugger collegato o usando un'app in esecuzione. Per altre informazioni, vedere [Raccogliere dati di profilatura senza il debug](../profiling/running-profiling-tools-with-or-without-the-debugger.md#collect-profiling-data-without-debugging) in [Eseguire gli strumenti di profilatura con o senza il debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="see-also"></a>Vedere anche  

 [Profilatura in Visual Studio](../profiling/index.md)  
 [Tour delle funzionalità di profilatura](../profiling/profiling-feature-tour.md)
