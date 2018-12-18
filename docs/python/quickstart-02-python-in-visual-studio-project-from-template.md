---
title: 'Guida introduttiva: Creare un progetto Python in Visual Studio da un modello | Microsoft Docs'
description: Iniziare velocemente a usare Python creando un progetto di Visual Studio da uno dei modelli predefiniti.
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
ms.openlocfilehash: 2af5a7412b6d4a6554d4bc11f5877541a3384115
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Guida rapida: creare un progetto Python da un modello in Visual Studio

Dopo aver [installato il supporto di Python in Visual Studio 2017](installing-python-support-in-visual-studio.md), è facile creare un nuovo progetto Python con una varietà di modelli.

1. Avviare Visual Studio.

1. Selezionare **File > Nuovo > progetto** (Ctrl+Shift+N). Nel finestra di dialogo **Nuovo progetto**, cercare "Python" e selezionare il modello desiderato. Si noti che la selezione di un modello visualizza una breve descrizione di ciò che offre tale modello. Vedere anche [Progetti Python](managing-python-projects-in-visual-studio.md#project-templates).

    ![Finestra di dialogo VS2017 Nuovo progetto con modelli Python](media/projects-new-project-dialog2.png)

1. Per questa Guida rapida, selezionare il modello "Applicazione Python", assegnare al progetto un nome (ad esempio "MakePI") e un percorso e selezionare **OK**.

1. Visual Studio crea il file di progetto (un file `.pyproj` su disco) insieme a qualsiasi altro file, come descritto nel modello. Con il modello "Applicazione Python", il progetto contiene un solo file vuoto con lo stesso nome del progetto. Il file è aperto nell'editor di Visual Studio per impostazione predefinita.

    ![Progetto risultante quando si usa il modello di applicazione Python](media/projects-new-structure.png)

1. Aggiungere codice al file aperto, ad esempio il codice seguente che calcola e visualizza le cifre 1000 di PI:

    ```python
    """ Print digits of PI; code adapted from the second, shorter solution
    at http://www.codecodex.com/wiki/Calculate_digits_of_pi#Python
    """

    from time import perf_counter

    def pi_digits_Python(digits):
        scale = 10000
        maxarr = int((digits / 4) * 14)
        arrinit = 2000
        carry = 0
        arr = [arrinit] * (maxarr + 1)
        output = ""

        for i in range(maxarr, 1, -14):
            total = 0
            for j in range(i, 0, -1):
                total = (total * j) + (scale * arr[j])
                arr[j] = total % ((j * 2) - 1)
                total = total / ((j * 2) - 1)

            output += "%04d" % (carry + (total / scale))
            carry = total % scale

        return output;

    def test_py():
        digits = 1000;

        start = perf_counter()
        output = pi_digits_Python(digits);
        elapsed = perf_counter() - start;

        print("PI to " + str(digits) + " digits in " + str(int(elapsed * 10000)/10000) + " seconds:")

        ## replace inserts the decimal point
        print(output.replace("3", "3.", 1))

    if __name__ == "__main__":
        test_py();
    ```

1. Eseguire il programma premendo Ctrl+F5 o selezionando **Debug > Avvia senza eseguire debug** del menu. I risultati vengono visualizzati nella finestra della console.

## <a name="next-steps"></a>Passaggi successivi

> [!div class="nextstepaction"]
> [Esercitazione: Uso di Python in Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Vedere anche

- [Creazione di un ambiente per un interprete esistente Python](managing-python-environments-in-visual-studio.md#creating-an-environment-for-an-existing-interpreter).
- [Installazione del supporto di Python in Visual Studio 2015 e precedenti](installing-python-support-in-visual-studio.md).
- [Percorsi di installazione](installing-python-support-in-visual-studio.md#install-locations).
