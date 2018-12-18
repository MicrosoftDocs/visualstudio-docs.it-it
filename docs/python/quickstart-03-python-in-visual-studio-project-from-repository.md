---
title: 'Guida introduttiva: clonazione di un repository di codice Python | Microsoft Docs'
description: In questa guida introduttiva viene creato un progetto Python in Visual Studio tramite la clonazione del repository koans Python con Visual Studio Team Explorer.
ms.custom: mvc
ms.date: 03/21/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: ''
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 9acad900f31d3579156cd266ebc10c244a1de39c
ms.sourcegitcommit: 064f8678f4a918e1dce60285090a9803d37dc34b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2018
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>Guida rapida: Clonazione di un repository del codice Python in Visual Studio

Dopo aver [installato il supporto di Python in Visual Studio 2017](installing-python-support-in-visual-studio.md), è possibile clonare facilmente un repository di codice Python e creare un progetto a partire da questo.

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

2. Avviare Visual Studio.

3. Selezionare **Visualizza > Team Explorer** per aprire la finestra **Team Explorer** in cui è possibile connettersi a GitHub o a Visual Studio Team Services oppure clonare un repository. Se la pagina **Connetti** illustrata di seguito non viene visualizzata, selezionare l'icona della spina sulla barra degli strumenti superiore.

    ![Finestra Team Explorer che mostra Visual Studio Team Services, GitHub e la clonazione di un repository](media/team-explorer.png)

4. In **Repository Git locali** selezionare il comando **Clona** e quindi immettere `https://github.com/gregmalcolm/python_koans` nel campo URL, immettere una cartella per i file clonati e selezionare il pulsante **Clona**.

    > [!Tip]
    > La cartella indicata in Team Explorer corrisponde esattamente alla cartella in cui ricevere i file clonati. A differenza del comando `git clone`, la creazione di un clone in Team Explorer non crea automaticamente una sottocartella con il nome del repository.

5. Al termine della clonazione, viene visualizzato il nome del repository nell'elenco **Repository Git locali**. Fare doppio clic su questo nome per passare al dashboard del repository in **Team Explorer**.

6. In **Soluzioni** selezionare **Nuovo**.

    ![Finestra Team Explorer, creazione di un nuovo progetto da un clone](media/team-explorer-new-project.png)

7. Nella finestra di dialogo **Nuovo progetto** visualizzata passare al linguaggio Python (o cercare "Python"), selezionare "Da codice Python esistente", specificare un nome per il progetto, impostare **Posizione** sulla stessa cartella del repository e selezionare **OK**. Nella procedura guidata visualizzata selezionare **Fine**.

8. Selezionare **Visualizza > Esplora soluzioni** dal menu.

9. In **Esplora soluzioni** espandere il nodo `python3`, fare clic con il pulsante destro del mouse su `contemplate_koans.py` e selezionare **Imposta come file di avvio**. Questo passaggio indica quale file deve essere usato da Visual Studio per l'esecuzione del progetto.

10. Selezionare **Progetto > Proprietà Koans...** dal menu, selezionare la scheda **Generale** e impostare **Directory di lavoro** su "python3". Questo passaggio è necessario perché, per impostazione predefinita, Visual Studio imposta la directory di lavoro sulla radice del progetto anziché sul percorso del file di avvio (`python3\contemplate_koans.py`, che è possibile visualizzare nelle proprietà del progetto). Il codice del programma cerca un file `koans.txt` nella cartella di lavoro, pertanto se non si modifica questo valore viene visualizzato un errore di runtime.

    ![Impostazione della cartella di lavoro per un progetto di Python](media/projects-set-working-directory.png)

11. Premere CTRL+F5 o scegliere **Debug > Avvia senza eseguire debug** per eseguire il programma. Se viene visualizzato un errore `FileNotFoundError` per `koans.txt`, controllare l'impostazione della directory di lavoro come descritto nel passaggio precedente.

12. Quando il programma viene eseguito correttamente, viene visualizzato un errore di asserzione in linea 17 di tipo `python3/koans/about_asserts.py`. È intenzionale: il programma è progettato per fare in modo che gli errori intenzionali siano corretti. (Per altri dettagli, vedere [Ruby Koans](http://rubykoans.com/) da cui è stato ideato Python Koans.)

    ![Primo output del programma di Python koans](media/koans-output.png)

13. Aprire `python3/koans/about_asserts.py` da Esplora soluzioni e fare doppio clic sul file. Si noti che i numeri di riga non vengono visualizzati nell'editor per impostazione predefinita. Per modificare questa impostazione, selezionare **Strumenti > Opzioni**, selezionare **Mostra tutte le impostazioni** nella parte inferiore della finestra di dialogo, quindi passare a **Editor di testo > Python > Generale** e selezionare **Numeri di riga**:

    ![Accensione del numero di riga per i file di Python](media/options-general-line-numbers.png)

14. Correggere l'errore modificando l'argomento `False` nella riga di 17 con `True`. La riga deve essere letta come segue:

    ```python
    self.assertTrue(True) # This should be True
    ```

15. Eseguire di nuovo il programma. Se Visual Studio segnala errori, rispondere con **Sì** per continuare a eseguire il codice. Si può quindi vedere che il primo controllo viene superato e che programma si arresta in corrispondenza del koan successivo. Continuare a correggere gli errori e a eseguire il programma in base alle esigenze.

> [!Important]
> In questa guida introduttiva è stato creato un clone diretto del repository *python_koans* in GitHub. Un repository di questo tipo è protetto dall'autore da modifiche dirette, pertanto il tentativo di eseguire il commit delle modifiche nel repository ha esito negativo. In pratica gli sviluppatori creano invece una copia del repository tramite fork nei propri account GitHub, apportano le modifiche all'interno della copia e quindi creano richieste pull per inviare tali modifiche al repository originale. Quando si ha una copia fork personale, usare l'URL corrispondente anziché l'URL del repository originale usato in precedenza.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Esercitazione: Uso di Python in Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Vedere anche

- [Identificazione manuale di un interprete Python esistente](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment).
- [Installazione del supporto di Python in Visual Studio 2015 e precedenti](installing-python-support-in-visual-studio.md).
- [Percorsi di installazione](installing-python-support-in-visual-studio.md#install-locations).
