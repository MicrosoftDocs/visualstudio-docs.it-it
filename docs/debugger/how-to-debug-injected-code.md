---
title: 'Procedura: eseguire il Debug di codice inserito | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.injected
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- assembly language, viewing
- debugging [C++], viewing assembly code
- debugging [C++], injected code
- debugging [C++], enabling source annotation
- injected code
- Show Source Code command [debugger]
- debugging [C++], using attributes
- disassembly code, debugging
ms.assetid: a1b4104d-d49e-451f-a91e-e39ceaf35875
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2c06209d2c2774eb12c0e04d8f448b8ceb2de771
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-injected-code"></a>Procedura: eseguire il debug di codice inserito
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere Importa/esporta impostazioni dal menu Strumenti. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Il ricorso agli attributi può semplificare notevolmente la programmazione in C++. Per ulteriori informazioni, vedere [concetti](/cpp/windows/attributed-programming-concepts). Alcuni attributi sono interpretati direttamente dal compilatore. Con altri attributi è invece possibile inserire codice nell'origine del programma, il quale verrà quindi compilato dal compilatore. Questo codice inserito rende più semplice la programmazione perché riduce la quantità di codice che è necessario scrivere. A volte, tuttavia, può accadere che un bug arresti l'applicazione mentre è in esecuzione il codice inserito. Quando ciò accade, può essere utile esaminare tale codice e Visual Studio prevede due metodi per farlo:  
  
-   È possibile visualizzare il codice inserito nel **Disassembly** finestra.  
  
-   Utilizzando [/Fx](/cpp/build/reference/fx-merge-injected-code), è possibile creare un file di origine unito contenente il codice originale e inserito.  
  
 Il **Disassembly** finestra vengono visualizzate le istruzioni in linguaggio assembly che corrispondono al codice sorgente e il codice inserito da attributi. Inoltre, il **Disassembly** finestra consente di visualizzare l'annotazione del codice sorgente.  
  
### <a name="to-turn-on-source-annotation"></a>Per attivare l'annotazione del codice sorgente  
  
-   Fare doppio clic su di **Disassembly** finestra e scegliere **Mostra codice sorgente** dal menu di scelta rapida.  
  
     Se si conosce il percorso di un attributo in una finestra di origine, è possibile utilizzare il menu di scelta rapida per trovare il codice inserito nel **Disassembly** finestra.  
  
### <a name="to-view-injected-code"></a>Per visualizzare il codice inserito  
  
1.  Il debugger deve essere in modalità di interruzione.  
  
2.  In una finestra di codice sorgente, portare il cursore davanti all'attributo di cui si desidera visualizzare il codice inserito.  
  
3.  Mouse e scegliere **Vai a Disassembly** dal menu di scelta rapida.  
  
     Se l'attributo si trova vicino al punto di esecuzione corrente, è possibile selezionare il **Disassembly** finestra il **Debug** menu.  
  
### <a name="to-view-the-disassembly-code-at-the-current-execution-point"></a>Per visualizzare il codice disassembly al punto di esecuzione corrente  
  
1.  Il debugger deve essere in modalità di interruzione.  
  
2.  Dal **Debug** menu, scegliere **Windows**, fare clic su **Disassembly**.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)