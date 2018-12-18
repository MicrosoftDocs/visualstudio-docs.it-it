---
title: Debug di un controllo ActiveX con associazione a dati | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 32cbb7bee21b54c932e0c369c46c3b2c3dacd898
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-a-data-bound-activex-control"></a>Debug di un controllo ActiveX con associazione a dati
Quando si sviluppa un controllo ActiveX che verrà associato a un controllo origine dati, è possibile creare un'applicazione contenitore e utilizzare il contenitore per eseguire il debug del controllo ActiveX.  
  
 È ad esempio possibile creare un'applicazione a finestre MFC e inserire nella finestra di dialogo il controllo con associazione a dati e un controllo origine dati. Questa applicazione MFC può essere utilizzata per effettuare test in fase di esecuzione, nonché come eseguibile del contenitore per il debug del controllo ActiveX con associazione a dati.  
  
## <a name="using-the-test-container"></a>Utilizzo di Test Container  
 Se si desidera un contenitore facilmente modificabile per il supporto di diverse interfacce sul controllo o sul contenitore, utilizzare ActiveX Test Container come eseguibile per la sessione di debug. In ActiveX Test Container, fare clic su **opzioni** dal **contenitore** menu per attivare le diverse interfacce. Per ulteriori informazioni, vedere [test di proprietà ed eventi con Test Container](/cpp/mfc/testing-properties-and-events-with-test-container).  
  
 Per eseguire istruzione per istruzione il codice del contenitore durante il debug, utilizzare la versione di debug del contenitore oppure la versione di debug di ActiveX Control Test Container. Per ulteriori informazioni, vedere [esempio TSTCON: ActiveX Control Test Container](http://msdn.microsoft.com/en-us/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## <a name="see-also"></a>Vedere anche  
 [COM e ActiveX di debug](../debugger/com-and-activex-debugging.md)   
 [Controlli ActiveX](/cpp/mfc/activex-controls)