---
title: Finestra Comando | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.CommandWindow
helpviewer_keywords:
- IDE, Command window
- Mark mode in Command window
- Command window
- Command mode in Command window
- IDE Command window
ms.assetid: 48711628-1909-4713-a73e-d7b714c77f8a
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b3b1de69c905757c8d28922cd09eadd5abf7d05e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="command-window"></a>Finestra di comando
La finestra **Comando** consente di eseguire i comandi o gli alias direttamente nell'ambiente di sviluppo integrato (IDE) di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. È possibile eseguire sia i comandi di menu che comandi che non vengono visualizzati nei menu. Per visualizzare la finestra **Comando**, scegliere **Altre finestre** dal menu **Visualizza** e selezionare **Finestra di comando**.  
  
## <a name="displaying-the-values-of-variables"></a>Visualizzazione dei valori delle variabili  
 Per controllare il valore di una variabile `varA`, usare il [comando Stampa](../../ide/reference/print-command.md):  
  
```  
>Debug.Print varA  
```  
  
 Il punto interrogativo (?) è un alias di `Debug.Print`. Questo comando può quindi essere scritto anche nel modo seguente:  
  
```  
>? varA  
```  
  
 Entrambe le versioni di questo comando restituiscono il valore della variabile `varA`.  
  
## <a name="entering-commands"></a>Immissione di comandi  
 Il simbolo di maggiore (`>`) viene visualizzato sul lato sinistro della finestra Comando come prompt per nuove righe. Usare FRECCIA SU e FRECCIA GIÙ per scorrere i comandi immessi in precedenza.  
  
|Attività|Soluzione|Esempio|  
|----------|--------------|-------------|  
|Valutare un'espressione.|Inserire l'espressione preceduta da un punto interrogativo (`?`).|`? myvar`|  
|Passare a Finestra di controllo immediato.|Immettere `immed` nella finestra senza il segno di maggiore di (>)|`immed`|  
|Tornare alla finestra Comando da Finestra di controllo immediato.|Immettere `cmd` nella finestra.|`>cmd`|  
  
 I collegamenti seguenti consentono l'esplorazione in modalità di comando.  
  
|Operazione|Posizione del cursore|Tasto di scelta rapida|  
|------------|---------------------|----------------|  
|Scorrere l'elenco dei comandi immessi in precedenza.|Riga di input|FRECCIA GIÙ o FRECCIA SU|  
|Scorrere la finestra verso l'alto.|Contenuto della finestra Comando|CTRL+FRECCIA SU|  
|Scorrere la finestra verso il basso.|Contenuto della finestra Comando|FRECCIA GIÙ o CTRL+FRECCIA GIÙ|  
  
> [!TIP]
>  Per copiare nella riga di input tutto o una parte di un comando precedente, spostarsi su di esso, selezionarlo interamente o in parte e premere INVIO.  
  
## <a name="mark-mode"></a>Modalità Indicatore  
 Facendo clic in una riga precedente nella finestra **Comando**, si passa automaticamente alla modalità Indicatore. Questa modalità consente di selezionare, modificare e copiare il testo dei comandi precedenti in qualsiasi editor di testo e incollarlo nella riga corrente.  
  
## <a name="the-equals--sign"></a>Segno di uguale (=)  
 La finestra usata per immettere il comando `EvaluateStatement` determina se interpretare un segno di uguale (=) come operatore di confronto o come operatore di assegnazione.  
  
 Nella finestra **Comando** il segno di uguale (=) viene interpretato come operatore di confronto. Non è possibile usare operatori di assegnazione nella finestra **Comando**. Pertanto, ad esempio, se i valori delle variabili `varA` e `varB` sono diversi, il comando `>Debug.EvaluateStatement(varA=varB)` restituirà il valore `False`.  
  
 Al contrario, nella finestra **Controllo immediato** il segno di uguale (=) viene interpretato come operatore di assegnazione. Pertanto, ad esempio, il comando `>Debug.EvaluateStatement(varA=varB)` assegnerà la variabile `varA` al valore della variabile `varB`.  
  
## <a name="parameters-switches-and-values"></a>Parametri, opzioni e valori  
 Per alcuni comandi di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] esistono argomenti, opzioni e valori obbligatori e facoltativi. Quando si usano questi comandi, vengono applicate alcune regole. Di seguito è riportato un esempio di un comando complesso con lo scopo di chiarirne la terminologia.  
  
```  
Edit.ReplaceInFiles /case /pattern:regex var[1-3]+ oldpar   
```  
  
 In questo esempio  
  
-   `Edit.ReplaceInFiles` è il comando  
  
-   `/case`e `/pattern:regex` sono opzioni (precedute dal carattere barra [/])  
  
-   `regex` è il valore dell'opzione `/pattern`; all'opzione `/case` non è assegnato alcun valore  
  
-   `var[1-3]+` e `oldpar` sono parametri  
  
    > [!NOTE]
    >  Qualsiasi comando, parametro, opzione o valore contenente spazi deve essere racchiuso tra virgolette doppie.  
  
La posizione di opzioni e parametri nella riga di comando è liberamente intercambiabile, ad eccezione del comando [Shell](../../ide/reference/shell-command.md), nel quale le opzioni e i parametri devono rispettare un ordine specifico.  
  
Esistono due formati per quasi tutte le opzioni supportate da un comando: un formato breve (un carattere) e un formato esteso. Più opzioni in formato breve possono essere raggruppate. Ad esempio, è possibile esprimere `/p /g /m` anche nel formato `/pgm`.  
  
Se alle opzioni in formato breve raggruppate viene assegnato un valore, tale valore viene applicato a ogni opzione. Ad esempio, `/pgm:123` equivale a `/p:123 /g:123 /m:123`. Se una delle opzioni del gruppo non accetta un valore, si verifica un errore.  
  
## <a name="escape-characters"></a>Caratteri di escape  
 Un accento circonflesso (^) in una riga di comando indica che il carattere immediatamente successivo viene interpretato letteralmente e non come carattere di controllo. In questo modo, è possibile incorporare virgolette diritte ("), spazi, barre iniziali, accenti circonflessi o qualsiasi altro carattere letterale nel valore di un parametro o di un'opzione, ad eccezione dei nomi di opzioni. Ad esempio,  
  
```  
>Edit.Find ^^t /regex  
```  

 L'accento circonflesso presenta lo stesso funzionamento sia all'interno sia all'esterno delle virgolette. Se corrisponde all'ultimo carattere sulla riga, viene ignorato. Nell'esempio riportato di seguito viene illustrato come cercare il criterio "^t".  
  
## <a name="use-quotes-for-path-names-with-spaces"></a>Usare le virgolette per nomi di percorso con spazi  
 Se, ad esempio, si vuole aprire un file con un percorso contenente spazi, è necessario racchiudere tra virgolette doppie il percorso o il segmento di tracciato contenente gli spazi: **C:\\"Programmi"** or**"C:\Programmi"**.  
  
## <a name="see-also"></a>Vedere anche  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)   
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)