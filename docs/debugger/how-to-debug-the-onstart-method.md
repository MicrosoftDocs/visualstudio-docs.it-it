---
title: 'Procedura: eseguire il Debug del metodo OnStart | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- OnStart method
- debugging [Visual Studio], Windows services
- debugging managed code, OnStart method
- debugging Windows Services applications, OnStart method
- Windows Service applications, debugging
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d438a8d6dcd80ec8d9dcce2fb4943e8b5614442c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-debug-the-onstart-method"></a>Procedura: eseguire il debug del metodo OnStart
È possibile eseguire il debug di un servizio Windows stesso avviando il servizio e connettendo il debugger al processo del servizio. Per altre informazioni, vedere [How to: Debug Windows Service Applications](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). Per eseguire il debug del metodo <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> di un servizio Windows, è tuttavia necessario avviare il debugger all'interno del metodo.  
  
1.  Aggiungere una chiamata a <xref:System.Diagnostics.Debugger.Launch%2A> all'inizio del metodo `OnStart()`.  
  
    ```csharp  
    protected override void OnStart(string[] args)  
    {  
        System.Diagnostics.Debugger.Launch();  
     }  
    ```  
  
2.  Avviare il servizio. È possibile usare `net start`o avviarlo nella finestra **Servizi** .  
  
     Verrà visualizzata una finestra di dialogo analoga alla seguente:  
  
     ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")  
  
3.  Selezionare **Sì, eseguire il debug \<nome servizio >.**  
  
4.  Nella finestra Debugger JIT di Visual Studio selezionare la versione di Visual Studio da usare per il debug.  
  
     ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")  
  
5.  Viene avviata una nuova istanza di Visual Studio e l'esecuzione viene arrestata in corrispondenza del metodo `Debugger.Launch()` .  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug di codice gestito](../debugger/debugging-managed-code.md)