---
ms.technology: vs-ai-tools
ms.openlocfilehash: 73292b9e0c7df23db839a7a13f70dbc2432d564f
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/28/2018
---
# <a name="clone-a-repository-of-python-code-in-visual-studio"></a>Clonare un repository del codice Python in Visual Studio

Dopo aver [installato Visual Studio Tools for AI](installation.md), è possibile clonare facilmente un repository di codice Python e creare un progetto a partire da questo.

1. Per connettersi ai repository di GitHub, eseguire il programma di installazione di Visual Studio, selezionare **Cambia** e quindi la scheda **Singoli componenti**. Scorrere verso il basso fino alla sezione **Strumenti per il codice**, selezionare **Estensione GitHub per Visual Studio** e quindi **Modifica**.

    ![Selezione dell'estensione GitHub nel programma di installazione di Visual Studio](media\create-project-repo\installation-github-extension.png)

2. Avviare Visual Studio.

3. Selezionare **Visualizza > Team Explorer** per aprire la finestra **Team Explorer** in cui è possibile connettersi a GitHub o a Visual Studio Team Services oppure clonare un repository.

    ![Finestra Team Explorer che mostra Visual Studio Team Services, GitHub e la clonazione di un repository](media\create-project-repo\team-explorer.png)

4. Nel campo URL in **Repository Git locali** immettere `https://github.com/Microsoft/samples-for-ai`, immettere una cartella per i file clonati e selezionare **Clona**.

    > [!Tip]
    > La cartella immessa in Team Explorer è specifica per ricevere i file clonati. A differenza del comando `git clone`, la creazione di un clone in Team Explorer non crea automaticamente una sottocartella con il nome del repository.

5. Al termine della clonazione, fare doppio clic sulla cartella del repository nella parte inferiore di Team Explorer per passare al dashboard del repository. In **Soluzioni** selezionare **Nuovo**.

    ![Finestra Team Explorer, creazione di un nuovo progetto da un clone](media\create-project-repo\team-explorer-new-project.png)

6. Nella finestra di dialogo **Nuovo progetto** visualizzata selezionare "**Da codice Python esistente**", specificare un nome per il progetto, impostare **Percorso** nella stessa cartella del repository e quindi selezionare **OK**. Nella procedura guidata visualizzata selezionare **Fine**.

7. Selezionare **Visualizza > Esplora soluzioni** dal menu.

8. In Esplora soluzioni espandere il nodo `TensorFlow Examples> MNIST`, fare clic con il pulsante destro del mouse su `convolutional.py` e scegliere **Imposta come file di avvio**. Questo passaggio indica quale file deve essere usato da Visual Studio per l'esecuzione del progetto.

10. Premere CTRL+F5 o scegliere **Debug > Avvia senza eseguire debug** per eseguire il programma. Se viene visualizzato un `, ricontrollare le impostazioni della directory di lavoro nel passaggio precedente.


11. Quando il programma viene eseguito correttamente, si noterà che viene avviato il download del set di dati per training e test, quindi viene eseguito il training del modello e viene infine restituita la frequenza degli errori. Si vuole ridurre la frequenza degli errori nel tempo

    ![Primo output del programma MNIST Python](media\create-project-repo\tensorflow-mnist-running.png)

> Se si usa Anaconda e si riceve un errore di numpy mancante, potrebbe essere necessario [modificare l'ambiente Python per usare Anaconda](../python/selecting-a-python-environment-for-a-project.md).

11. È possibile visualizzare lo stato con TensorBoard. Fare clic con il pulsante destro de mouse sul progetto e scegliere **Run TensorBoard** (Esegui TensorBoard) quindi selezionare la directory dei log di output di TensorBoard.

    ![eseguire tensorboard](media\create-project-repo\run-tensorboard.png)

11. Si noti che gli errori diminuiscono nel tempo e ciò indica un miglioramento della qualità

    ![eseguire tensorboard](media\create-project-repo\tensorboard.png)