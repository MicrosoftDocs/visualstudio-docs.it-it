---
title: Analisi del code coverage nei test di verifica della compilazione | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 3f02166c89837dfd122ab8a8c71913c659ab1dd2
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2018
---
# <a name="analyzing-code-coverage-in-build-verification-tests"></a>Analisi del code coverage nei test di verifica della compilazione
L'analisi del code coverage in Microsoft Visual Studio mostra la quantità di codice usato dai test automatizzati. Per altre informazioni, vedere [Uso di code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
 Quando si controlla il codice, i test vengono eseguiti sul server di compilazione insieme a tutti gli altri test degli altri membri del team. Se questo aspetto non è già stato configurato, vedere [Eseguire test nel processo di compilazione](http://msdn.microsoft.com/Library/d05743a1-c5cf-447e-bed9-bed3cb595e38). È utile analizzare il code coverage nel servizio di compilazione perché viene offerta un'immagine aggiornata e completa del code coverage dell'intero progetto. Vengono inclusi i test di sistema automatizzati e altri test codificati che normalmente non vengono eseguiti nei computer di sviluppo.  
  
1.  In Team Explorer aprire **Compilazioni** e aggiungere o modificare una definizione di compilazione.  
  
2.  Nella pagina **Processo** espandere **Test automatizzati**, **Origine test**, **Impostazioni esecuzione test**. Impostare **Tipo di file di impostazioni esecuzione test** su **Code coverage abilitato**.  
  
     Se si dispone di più di una definizione di origine del test, ripetere questo passaggio per ciascuna di esse.  
  
    -   *Non è presente alcun campo denominato **Tipo di file di impostazioni esecuzione test**.*  
  
         In **Test automatizzati** selezionare **Assembly di test** e premere il pulsante con i puntini di sospensione **[...]** alla fine della riga. Nella finestra di dialogo **Aggiungi/Modifica esecuzione dei test** in **Test Runner** scegliere **Visual Studio Test Runner**.  
  
 ![Impostazione della definizione di compilazione per il code coverage](../test/media/codecoverage-plaincc.png "CodeCoverage-plainCC")  
  
 Dopo la compilazione, i risultati di code coverage vengono visualizzati nel riepilogo della compilazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di code coverage per determinare la quantità di codice testato](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)
