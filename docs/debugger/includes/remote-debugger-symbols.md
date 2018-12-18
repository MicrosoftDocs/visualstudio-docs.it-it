---
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.openlocfilehash: 95d76781f651b681b81e4dd18848b404d8a85664
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
 Dovrebbe essere possibile eseguire il debug del codice con i simboli generati nel computer di Visual Studio. L'uso di simboli locali consente di migliorare notevolmente le prestazioni del debugger remoto.  Se è necessario usare simboli remoti, indicare a Remote Debugging Monitor di eseguire la ricerca di simboli nel computer remoto.  
  
 A partire da Visual Studio 2013 Update 2, è possibile utilizzare la seguente opzione della riga di comando di msvsmon per usare i simboli remoti per il codice gestito:`Msvsmon /FallbackLoadRemoteManagedPdbs`  
  
 Per ulteriori informazioni, vedere la Guida al debug remoto (premere **F1** nella finestra del debugger remoto oppure fare clic su **Guida > utilizzo**). È possibile trovare ulteriori informazioni in [.NET simbolo modifiche nel caricamento remoto in Visual Studio 2012 e 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)