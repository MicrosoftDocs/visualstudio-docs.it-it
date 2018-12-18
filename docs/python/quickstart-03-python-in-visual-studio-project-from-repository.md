---
title: 'Guida introduttiva: Clonazione di un repository di codice Python in Visual Studio | Microsoft Docs'
description: Iniziare a usare rapidamente Python tramite la clonazione del repository koans Python con Visual Studio Team Explorer.
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: ca32058d9207221c1752e522bbba82d0033626f2
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="quickstart-clone-a-repository-of-python-code-in-visual-studio"></a>Guida rapida: Clonazione di un repository del codice Python in Visual Studio

Dopo aver [installato il supporto di Python in Visual Studio 2017](installing-python-support-in-visual-studio.md), è possibile clonare facilmente un repository di codice Python e creare un progetto a partire da questo.

[!INCLUDE[install-github-extension](includes/install-github-extension.md)]

2. Avviare Visual Studio.

3. Selezionare **Visualizza > Team Explorer** per aprire la finestra **Team Explorer** in cui è possibile connettersi a GitHub o a Visual Studio Team Services oppure clonare un repository.

    ![Finestra Team Explorer che mostra Visual Studio Team Services, GitHub e la clonazione di un repository](media/team-explorer.png)

4. Nel campo URL in **Repository Git locali** immettere `https://github.com/gregmalcolm/python_koans`, immettere una cartella per i file clonati e selezionare **Clona**.

    > [!Tip]
    > La cartella immessa in Team Explorer è specifica per ricevere i file clonati. A differenza del comando `git clone`, la creazione di un clone in Team Explorer non crea automaticamente una sottocartella con il nome del repository.

5. Al termine della clonazione, fare doppio clic sulla cartella del repository nella parte inferiore di Team Explorer per passare al dashboard del repository. In **Soluzioni** selezionare **Nuovo**.

    ![Finestra Team explorer, creazione di un nuovo progetto da un clone](media/team-explorer-new-project.png)

6. Nella finestra di dialogo **Nuovo progetto** visualizzata, selezionare "Da codice Python esistente", specificare un nome per il progetto, impostare **Percorso** nella stessa cartella del repository, selezionare **OK**. Nella procedura guidata visualizzata, selezionare **Fine**.

7. Selezionare **Visualizza > Esplora soluzioni** dal menu.

8. In Esplora soluzioni espandere il nodo `python3`, fare clic con il pulsante destro del mouse su `contemplate_koans.py` e scegliere **Imposta come file di avvio**. Questo passaggio indica quale file deve essere usato da Visual Studio per l'esecuzione del progetto.

9. Dal menu selezionare **Progetto > Proprietà**, selezionare la scheda **Generale** e impostare come **directory di lavoro** "python3". Questo è necessario perché, per impostazione predefinita, Visual Studio imposta la directory di lavoro per la radice del progetto anziché per il percorso del file di avvio (`python3\contemplate_koans.py`, che è possibile visualizzare nelle proprietà del progetto). Il codice del programma cerca un file `koans.txt` nella cartella di lavoro, pertanto se non si modifica questo valore viene visualizzato un errore di runtime.

    ![Impostazione della cartella di lavoro per un progetto di Python](media/projects-set-working-directory.png)

10. Premere Ctrl+F5 o scegliere **Debug > Avvia senza eseguire debug** per eseguire il programma. Se viene visualizzato un errore `FileNotFoundError` per `koans.txt`, ricontrollare le impostazioni della directory di lavoro nel passaggio precedente.

11. Quando il programma viene eseguito correttamente, viene visualizzato un errore di asserzione in linea 17 di tipo `python3/koans/about_asserts.py`. È intenzionale: il programma è progettato per fare in modo che gli errori intenzionali siano corretti. (Per altri dettagli, vedere [Ruby Koans](http://rubykoans.com/) da cui è stato ideato Python Koans.)

    ![Primo output del programma di Python koans](media/koans-output.png)

12. Aprire `python3/koans/about_asserts.py` da Esplora soluzioni e fare doppio clic sul file. Si noti che i numeri di riga non vengono visualizzati nell'editor per impostazione predefinita. Per modificare questa impostazione, selezionare **Strumenti > Opzioni**, selezionare **Mostra tutte le impostazioni** nella parte inferiore della finestra di dialogo, quindi passare a **Editor di testo > Python > Generale** e selezionare **Numeri di riga**:

    ![Accensione del numero di riga per i file di Python](media/options-general-line-numbers.png)

13. Correggere l'errore modificando l'argomento `False` nella riga di 17 con `True`. La riga deve essere letta come segue:

    ```python
    self.assertTrue(True) # This should be True
    ```

14. Eseguire nuovamente il programma per verificare se il primo controllo è superato. Il programma si arresterà nel koan successivo. Proseguire con la correzione degli errori ed eseguire nuovamente il programma desiderato.

> [!Important]
> In questa Guida rapida, è stato creato un clone diretto del repository *python_koans* in GitHub. Un repository di questo tipo è protetto dall'autore da modifiche dirette, pertanto il tentativo di eseguire il commit delle modifiche nel repository ha esito negativo. In pratica gli sviluppatori non creano una copia del repository tramite fork per i propri account GitHub ma apportano delle modifiche e quindi creano richieste pull per inviare tali modifiche nel repository originale. Questi passaggi sono descritti nell'[Esercitazione sull'uso di Git: passaggio 6](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md).

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Esercitazione: Uso di Python in Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Vedere anche

- [Creazione di un ambiente per un interprete esistente Python](managing-python-environments-in-visual-studio.md#creating-an-environment-for-an-existing-interpreter).
- [Installazione del supporto di Python in Visual Studio 2015 e precedenti](installing-python-support-in-visual-studio.md).
- [Percorsi di installazione](installing-python-support-in-visual-studio.md#install-locations).
