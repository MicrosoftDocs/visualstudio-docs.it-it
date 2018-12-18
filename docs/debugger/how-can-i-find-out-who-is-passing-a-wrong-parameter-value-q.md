---
title: "Come è possibile individuare chi passa un valore di parametro errato? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.parameters
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], parameters
- parameters [debugger]
- passing parameters, troubleshooting wrong values
- functions [debugger], detecting wrong parameter values
- parameter values, troubleshooting
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 77c4953840c879a14406003f0bafffe98908cd95
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Come è possibile individuare chi passa un valore di parametro errato?
## <a name="problem-description"></a>Descrizione del problema  
 Il valore di parametro errato è stato passato a una delle funzioni utilizzate. Questa funzione viene chiamata da numerosissime posizioni. Come è possibile capire quale elemento passa il valore errato?  
  
## <a name="solution"></a>Soluzione  
  
#### <a name="to-resolve-this-problem"></a>Per risolvere questo problema  
  
1.  Impostare un punto di interruzione del percorso all'inizio della funzione.  
  
2.  Il punto di interruzione e scegliere **condizione**.  
  
3.  Nel **condizione punto di interruzione** la finestra di dialogo, fare clic su di **condizione** casella di controllo. Vedere [punti di interruzione avanzati](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).  
  
4.  Nella casella di testo immettere un'espressione, ad esempio `Var==3`, in cui `Var` è il nome del parametro che contiene il valore errato e `3` il valore errato passato.  
  
5.  Selezionare il **è True** pulsante di opzione e fare clic su di **OK** pulsante.  
  
6.  Eseguire nuovamente il programma. Il punto di interruzione causa l'arresto del programma all'inizio della funzione, quando il parametro `Var` ha valore `3`.  
  
7.  Utilizzare la finestra Stack di chiamate per individuare la funzione chiamante e passare al relativo codice sorgente. Per ulteriori informazioni, vedere [procedura: utilizzare la finestra Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Domande frequenti sul codice nativo debug](../debugger/debugging-native-code-faqs.md)   
 [Punti di interruzione](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)