---
title: "Procedura: aggiungere la convalida alle classi di entità | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 1ff8eb04ae9b5009aff13dc8588633b34d4d72dd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-validation-to-entity-classes"></a>Procedura: aggiungere la convalida alle classi di entità
*Convalida* classi di entità è il processo di conferma che i valori immessi negli oggetti dati sono conformi con i vincoli nello schema di un oggetto e alle regole stabilite per l'applicazione. Per ridurre gli errori, è opportuno convalidare i dati prima di inviare aggiornamenti al database sottostante. La convalida consente anche di ridurre il numero potenziale di round trip tra un'applicazione e il database.  
  
 Il [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fornisce i metodi parziali che consentano agli utenti di estendere il codice generato da progettazione che viene eseguito durante l'inserimento, aggiornamento ed eliminazione di entità complete nonché durante e dopo una singola colonna modifiche.  
  
> [!NOTE]
>  In questo argomento vengono forniti i passaggi di base per aggiungere la convalida a classi di entità usando [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Perché potrebbe essere difficile seguire questi passaggi generici senza fare riferimento a una classe di entità specifico, è stata fornita una procedura dettagliata vengono usati dati effettivi.  
  
## <a name="adding-validation-for-changes-to-the-value-in-a-specific-column"></a>Aggiunta della convalida per le modifiche al valore di una specifica colonna  
 In questa procedura viene mostrato come convalidare i dati quando viene modificato il valore in una colonna. Poiché la convalida viene eseguita nella definizione di classe anziché nell'interfaccia utente, se il valore causa l'esito negativo della convalida, viene generata un'eccezione. Implementare la gestione degli errori per il codice nell'applicazione che tenta di modificare i valori della colonna.  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-validate-data-during-a-columns-value-change"></a>Per convalidare i dati durante la modifica del valore di una colonna  
  
1.  Aprire o creare un nuovo file LINQ to SQL Classes (**dbml** file) nei [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. (Fare doppio clic su di **. dbml** file **Esplora**.)  
  
2.  In Progettazione relazionale oggetti, fare clic sulla classe per cui si desidera aggiungere la convalida, quindi fare clic su **Visualizza codice**.  
  
     Viene aperto l'editor del codice con una classe parziale per la classe di entità selezionata.  
  
3.  Posizionare il cursore nella classe parziale.  
  
4.  Per i progetti di Visual Basic:  
  
    1.  Espandere il **nome del metodo** elenco.  
  
    2.  Individuare il **OnCOLUMNNAMEChanging** metodo per la colonna che si desidera aggiungere la convalida.  
  
    3.  Un `OnCOLUMNNAMEChanging` metodo viene aggiunto alla classe parziale.  
  
    4.  Aggiungere il codice riportato di seguito per verificare innanzitutto che sia stato immesso un valore e quindi per assicurarsi che il valore immesso per la colonna sia accettabile per l'applicazione. Poiché l'argomento `value` contiene il valore proposto, aggiungere logica per confermare che si tratta di un valore valido:  
  
        ```vb  
        If value.HasValue Then  
            ' Add code to ensure that the value is acceptable.  
            ' If value < 1 Then  
            '    Throw New Exception("Invalid data!")  
            ' End If  
        End If  
        ```  
  
    Per i progetti C#:  
  
    Poiché i progetti c# non generano automaticamente i gestori eventi, è possibile utilizzare IntelliSense per creare i metodi parziali di modifica delle colonne. Digitare `partial` e uno spazio per accedere all'elenco dei metodi parziali disponibili. Fare clic sul metodo di modifica delle colonne relativo alla colonna per cui si desidera aggiungere la convalida. Il codice seguente è simile al codice che viene generato quando si seleziona un metodo parziale di modifica delle colonne:  
  
    ```csharp  
    partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)  
        {  
           throw new System.NotImplementedException();  
        }  
    ```  
  
## <a name="adding-validation-for-updates-to-an-entity-class"></a>Aggiunta della convalida per gli aggiornamenti a una classe di entità  
 Oltre a controllare i valori durante le modifiche, è anche possibile convalidare i dati quando si tenta di aggiornare una classe di entità completa. La convalida durante un tentativo di aggiornamento consente di confrontare i valori di più colonne, se richiesto dalle regole business. Nella procedura riportata di seguito viene mostrato come eseguire la convalida quando si tenta di aggiornare una classe di entità completa.  
  
> [!NOTE]
>  Il codice di convalida per gli aggiornamenti alle classi di entità complete viene eseguito nella classe <xref:System.Data.Linq.DataContext> parziale, anziché nella classe parziale di una classe di entità specifica.  
  
#### <a name="to-validate-data-during-an-update-to-an-entity-class"></a>Per convalidare i dati durante un aggiornamento a una classe di entità  
  
1.  Aprire o creare un nuovo file LINQ to SQL Classes (**dbml** file) nei [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. (Fare doppio clic su di **. dbml** file **Esplora**.)  
  
2.  Fare doppio clic su un'area vuota in Progettazione relazionale oggetti e fare clic su **Visualizza codice**.  
  
     Viene aperto l'editor del codice con una classe parziale per `DataContext`.  
  
3.  Posizionare il cursore nella classe parziale per `DataContext`.  
  
4.  Per i progetti di Visual Basic:  
  
    1.  Espandere il **nome del metodo** elenco.  
  
    2.  Fare clic su **UpdateENTITYCLASSNAME**.  
  
    3.  Un `UpdateENTITYCLASSNAME` metodo viene aggiunto alla classe parziale.  
  
    4.  Accedere ai valori delle singole colonne usando l'argomento `instance`, come mostrato nel codice seguente:  
  
        ```vb  
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then  
            Dim ErrorMessage As String = "Invalid data!"  
            Throw New Exception(ErrorMessage)  
        End If  
        ```  
  
    Per i progetti C#:  
  
    Poiché i progetti c# non generano automaticamente i gestori eventi, è possibile utilizzare IntelliSense per creare parziale `UpdateCLASSNAME` metodo. Digitare `partial` e uno spazio per accedere all'elenco dei metodi parziali disponibili. Fare clic sul metodo di aggiornamento relativo alla classe per cui si desidera aggiungere la convalida. Il codice seguente è simile al codice che viene generato quando si seleziona un `UpdateCLASSNAME` metodo parziale:  
  
    ```csharp  
    partial void UpdateCLASSNAME(CLASSNAME instance)  
    {  
        if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))  
        {  
            string ErrorMessage = "Invalid data!";  
            throw new System.Exception(ErrorMessage);  
        }  
    }  
    ```  
  
## <a name="see-also"></a>Vedere anche
[LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
[Convalida dei dati](../data-tools/validate-data-in-datasets.md)  
[LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)  