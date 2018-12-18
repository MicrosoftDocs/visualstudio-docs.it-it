---
title: Creare un progetto unit test | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 71a666a2e52b49f71f5c74419cfda0eb05d78938
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/09/2018
---
# <a name="create-a-unit-test-project"></a>Creare un progetto di unit test
Gli unit test spesso simulano la struttura del codice sottoposto a test. Ad esempio, si crea un progetto unit test per ogni progetto di codice del prodotto. Il progetto test può essere nella stessa soluzione del codice di produzione o in una soluzione separata. È possibile avere più progetti unit test in una soluzione.  
  
> [!NOTE]
>  Il percorso degli unit test per un codice nativo e la struttura del progetto test possono essere diversi da quelli descritti in questo argomento. Per altre informazioni, vedere [Scrittura di unit test per C/C++](writing-unit-tests-for-c-cpp.md).  
  
## <a name="to-create-a-unit-test-project"></a>Per creare un progetto unit test:  
  
1.  Scegliere **Nuovo** dal menu **File** , quindi scegliere **Progetto** oppure premere CTRL+MAIUSC+N.  
  
2.  Nella finestra di dialogo Nuovo progetto espandere il nodo **Installato**, scegliere il linguaggio da usare per il progetto test e quindi scegliere **Test**.  
  
3.  Per usare uno dei framework per unit test Microsoft, scegliere **Progetto unit test** dall'elenco di modelli di progetto. In alternativa, scegliere il modello di progetto del framework per unit test che si vuole usare. Per testare il progetto Accounts dell'esempio, assegnare al progetto il nome AccountsTests.  
  
4.  Nel progetto unit test, aggiungere un riferimento al codice sottoposto a test.  Di seguito viene illustrato come creare il riferimento a un progetto codice nella stessa soluzione:  
  
    1.  Selezionare il progetto in Esplora soluzioni.  
  
    2.  Scegliere **Aggiungi riferimento** dal menu **Progetto**.  
  
    3.  Nella finestra di dialogo Gestione riferimenti aprire il nodo **Soluzione** e scegliere **Progetti**. Selezionare il nome del progetto codice e chiudere la finestra di dialogo.  
  
5.  Se il codice che si vuole testare è in un altro percorso, vedere [Gestione dei riferimenti in un progetto](../ide/managing-references-in-a-project.md) per informazioni sull'aggiunta di riferimenti.  
  
## <a name="next-steps"></a>Passaggi successivi  
 **Scrittura di unit test**  
  
 Vedere una delle sezioni seguenti:  
  
-   [Scrittura di unit test per .NET Framework con il framework unit test di Microsoft per codice gestito](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)  
  
-   [Scrittura di unit test per C/C++](writing-unit-tests-for-c-cpp.md)  
  
 **Esecuzione di unit test**  
  
 [Eseguire unit test con Esplora test](../test/run-unit-tests-with-test-explorer.md)
