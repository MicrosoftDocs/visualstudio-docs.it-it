---
---
# <a name="create-an-ai-project-from-existing-code"></a>Creare un progetto AI da codice esistente

Dopo aver [installato Visual Studio Tools for AI](installation.md) è facile aggiungere codice Python esistente in un progetto di Visual Studio.

> [!Important]
>
> Il processo descritto non sposta o copia i file di origine. Se si vuole usare una copia, per prima cosa duplicare la cartella.

1. Avviare Visual Studio e selezionare **File > Nuovo > Progetto**.

1. Nella finestra di dialogo **Nuovo progetto** cercare "**AI Tools**" (Strumenti AI), selezionare il modello "**Da codice Python esistente**", assegnare al progetto un nome e una posizione e selezionare **OK**.

    ![Nuovo progetto da codice esistente, passaggio 1](media\create-project-existing\new-ai-project.png)

1. Nella procedura guidata visualizzata impostare il percorso del codice esistente, un filtro per i tipi di file ed eventuali percorsi di ricerca richiesti dal progetto, quindi selezionare **OK**. In caso di dubbi sui percorsi di ricerca, lasciare vuoto il campo.

![Nuovo progetto da codice esistente, passaggio 2](media\create-project-existing\azurebatch-newproject.png)

> Se il codice esistente fa parte di un progetto di Azure Machine Learning, selezionare "**Is Azure Machine Learning folder**" (Cartella di Azure Machine Learning) per assicurarsi che vengano convertiti correttamente dettagli importanti della configurazione di Azure Machine Learning, come l'account di sperimentazione, l'area di lavoro, i contesti di calcolo da usare e altro ancora.

1. Per impostare un file di avvio, individuare il file in Esplora soluzioni, fare clic con il pulsante destro del mouse e scegliere **Imposta come file di avvio**.

1. Se necessario, eseguire il programma premendo CTRL+F5 o selezionando **Debug > Avvia senza eseguire debug**.

> [!div class="nextstepaction"]
> [Esercitazione: Uso di Python in Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-00-installation.md)

## <a name="see-also"></a>Vedere anche

- [Creazione di un ambiente per un interprete esistente Python](../python/managing-python-environments-in-visual-studio.md#creating-an-environment-for-an-existing-interpreter)