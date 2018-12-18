---
title: Opzioni, Editor di testo, C/C++, Formattazione | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- CPP
helpviewer_keywords:
- Text Editor Options dialog box, formatting
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 61097f910a2dda79852b126a2f17f2af6c62b808
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="options-text-editor-cc-formatting"></a>Opzioni, Editor di testo, C/C++, Formattazione
Consente di modificare il comportamento predefinito dell'editor di codice in fase di programmazione in C o C++.  
  
 Per accedere a questa pagina, nel riquadro sinistro della finestra di dialogo **Opzioni** espandere **Editor di testo** e **C/C++**, quindi fare clic su **Formattazione**.  
  
> [!NOTE]
>  I nomi o i percorsi visualizzati per alcuni elementi dell'interfaccia utente di Visual Studio nelle istruzioni seguenti potrebbero essere diversi nel computer in uso. La versione di Visual Studio in uso e le impostazioni configurate determinano questi elementi. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="cc-options"></a>Opzioni C/C++  
 **Attiva descrizione comandi per informazioni rapide automatiche**  
 Consente di abilitare o disabilitare la funzionalità Informazioni rapide di IntelliSense.  
  
## <a name="inactive-code"></a>Codice inattivo  
 **Mostra blocchi inattivi**  
 Per il codice reso inattivo da dichiarazioni `#ifdef` viene utilizzato un colore diverso in modo da agevolarne l'identificazione.  
  
 **Disabilita opacità del codice inattivo**  
 Codice inattivo che può essere identificato tramite colore, anziché tramite trasparenza.  
  
 **Percentuale di opacità del codice inattivo**  
 È possibile personalizzare il grado di opacità per blocchi di codice inattivo.  
  
## <a name="indentation"></a>Rientro  
 **Rientra parentesi graffe**  
 È possibile configurare la modalità di allineamento delle parentesi graffe quando si preme INVIO dopo aver avviato un blocco di codice, ad esempio una funzione o un ciclo `for`. Le parentesi graffe possono essere allineate al primo carattere del blocco di codice oppure rientrate.  
  
 **Rientra alla pressione del tasto TAB**  
 È possibile configurare le operazioni eseguite nella riga di codice corrente quando si preme TAB. La riga viene rientrata oppure viene inserito un carattere di tabulazione.  
  
## <a name="miscellaneous"></a>Varie  
 **Enumera attività di commento**  
 L'editor può analizzare le parole preimpostate nei commenti all'interno dei file di origine aperti. Crea una voce nella finestra **Elenco attività** per qualsiasi parola chiave trovata.  
  
 **Evidenzia token corrispondenti**  
 Se il cursore si trova accanto a una parentesi graffa, l'editor può evidenziare la parentesi graffa corrispondente in modo che sia possibile visualizzare più agevolmente il codice contenuto.  
  
## <a name="outlining"></a>struttura  
 **Attiva modalità struttura all'apertura del file**  
 Aprendo un file nell'editor di testo, è possibile abilitare la funzionalità di struttura. Per altre informazioni, vedere [Struttura](../../ide/outlining.md). Se questa opzione è selezionata, la funzionalità di struttura verrà abilitata all'apertura di un file.  
  
 **Struttura blocchi pragma region**  
 Se questa opzione è selezionata, la struttura automatica per le [direttive pragma](/cpp/preprocessor/pragma-directives-and-the-pragma-keyword) è abilitata. In questo modo è possibile espandere o comprimere blocchi pragma region in modalità struttura.  
  
 **Struttura blocchi di istruzioni**  
 Se questa opzione è selezionata, la struttura automatica è abilitata per i costrutti delle istruzioni seguenti:  
  
-   [if-else](/dotnet/csharp/language-reference/keywords/if-else)  
  
-   [Istruzione switch (C++)](/cpp/cpp/switch-statement-cpp)  
  
-   [Istruzione while (C++)](/cpp/cpp/while-statement-cpp)  
  
## <a name="see-also"></a>Vedere anche  
 [General, Environment, Options Dialog Box](../../ide/reference/general-environment-options-dialog-box.md)  (Generale, Ambiente, finestra di dialogo Opzioni)  
 [Utilizzo di IntelliSense](../../ide/using-intellisense.md)