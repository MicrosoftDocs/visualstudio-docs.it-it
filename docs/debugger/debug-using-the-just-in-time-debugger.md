---
title: Eseguire il debug utilizzando il Debugger JIT | Documenti Microsoft
ms.custom: ''
ms.date: 07/06/17
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: ee4d79a5-a1d2-4418-a93f-dd57a53e1836
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e6abdd96f740d36b4f6806b16e6cdd9ba946cb95
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="debug-using-the-just-in-time-debugger-in-visual-studio"></a>Eseguire il debug utilizzando il Debugger JIT di Visual Studio
Il debug Just-In-Time avvia Visual Studio automaticamente quando si verifica un'eccezione o un arresto anomalo in un'applicazione che è in esecuzione all'esterno di Visual Studio. Ciò consente di testare l'applicazione quando Visual Studio non è in esecuzione e avviare il debug con Visual Studio quando si verifica un problema.

Il debug Just-In-Time funziona per le app desktop di Windows. Non funziona per le app di Windows universale e non funziona per il codice gestito ospitato in un'applicazione nativa, ad esempio visualizzatori.

> [!TIP] 
> Se si desidera sapere come rispondere a Just-in-Time la finestra di dialogo del debugger, vedere [in questo argomento](../debugger/just-in-time-debugging-in-visual-studio.md).

##  <a name="BKMK_Enabling"></a> Abilitare o disabilitare Just-In-Time il debug  
È possibile abilitare o disabilitare il debug di Visual Studio Just-In-Time **strumenti > Opzioni** la finestra di dialogo.
  
#### <a name="to-enable-or-disable-just-in-time-debugging"></a>Per abilitare o disabilitare il debug JIT  
  
1.  Aprire Visual Studio con privilegi di amministratore (pulsante destro del mouse e scegliere **Esegui come amministratore**).

    Abilitazione o disabilitazione Just-In-Time debug imposta una chiave del Registro di sistema e dei privilegi di amministratore potrebbero essere necessario modificare tale chiave.
    
2. Scegliere **Opzioni** dal menu **Strumenti**.
  
2.  Nel **opzioni** finestra di dialogo espandere il **debug** nodo.  
  
3.  Nel **debug** nodo, seleziona **Just-In-Time**.

    ![Abilitare o disabilitare il debug JIT](../debugger/media/dbg-jit-enable-or-disable.png "abilitare o disabilitare il debug JIT") 
  
4.  Nel **Attiva debug JIT per questi tipi di codice** selezionare o deselezionare i tipi di programma relativi: **gestito**, **nativo**, o **Script**.    
  
5.  Fare clic su **OK**.  
  
Il debug JIT può comunque essere abilitato anche se Visual Studio non è più presente nel computer. Quando non è installato Visual Studio, è possibile disabilitare il debug di Visual Studio Just-In-Time **opzioni** la finestra di dialogo. In questo caso, è possibile disabilitare il debug JIT modificando il Registro di sistema di Windows.  
  
#### <a name="to-disable-just-in-time-debugging-by-editing-the-registry"></a>Per disabilitare il debug JIT modificando il Registro di sistema  
  
1.  Nel **avviare** menu, cercare ed eseguire `regedit.exe`  
  
2.  Nel **Editor del Registro di sistema** finestra, individuare ed eliminare le voci del Registro di sistema seguenti:  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\DbgManagedDebugger  

    ![Chiave del Registro di sistema JIT](../debugger/media/dbg-jit-registry.png "chiave del Registro di sistema JIT") 
  
3.  Se il computer è in esecuzione un sistema operativo a 64 bit, eliminare anche le voci del Registro di sistema seguenti:  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows NT\CurrentVersion\AeDebug\Debugger  
  
    -   HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\DbgManagedDebugger  
  
4.  Fare attenzione a non eliminare o modificare altre chiavi del Registro di sistema.  
  
5.  Chiudi il **Editor del Registro di sistema** finestra.   
  
#### <a name="to-enable-just-in-time-debugging-of-a-windows-form"></a>Per attivare il debug JIT di Windows Form  
  
1.  Per impostazione predefinita, le applicazioni Windows Forms dispongono di un gestore eccezioni di livello superiore che consente al programma di proseguire l'esecuzione quando è possibile un ripristino. Ad esempio, se l'applicazione Windows Form genera un'eccezione non gestita, si visualizzerà una finestra di dialogo simile alla seguente:  
  
     ![WindowsFormsUnhandledException](../debugger/media/windowsformsunhandledexception.png "WindowsFormsUnhandledException")  
  
     Per abilitare Just-In-Time il debug di un'applicazione Windows Form, è necessario eseguire i passaggi aggiuntivi seguenti:  
  
2.  Impostare il `jitDebugging` valore `true` nel `system.windows.form` sezione di Machine. config o  *\<nome applicazione >*. exe. config:  
  
    ```  
    <configuration>  
        <system.windows.forms jitDebugging="true" />  
    </configuration>  
    ```  
  
3.  In un'applicazione Windows Form C++ è anche necessario impostare `DebuggableAttribute` in un file con estensione config o nel codice. Se si compila con [/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format) e senza [/Og](/cpp/build/reference/og-global-optimizations), il compilatore imposta automaticamente questo attributo. Se si desidera eseguire il debug di una build di rilascio non ottimizzata, tuttavia, è necessario procedere alla configurazione. A tale scopo, è possibile aggiungere la riga seguente al file AssemblyInfo.cpp dell'applicazione:  
  
    ```  
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];   
    ```  
  
     Per altre informazioni, vedere <xref:System.Diagnostics.DebuggableAttribute>.  
  
## <a name="a-namebkmkusingjituse-just-in-time-debugging"></a><a name="BKMK_Using_JIT">Utilizzare il debug Just-In-Time  
 In questa sezione viene illustrato cosa accade quando un file eseguibile genera un'eccezione.  
  
 È necessario disporre di Visual Studio per eseguire la procedura seguente. Se non si dispone di Visual Studio, è possibile scaricare la versione gratuita [Visual Studio Community Edition](https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15).  
  
 Verificare che tale Just-In-Time debug è [abilitato](#BKMK_Enabling).
  
 Ai fini di questa sezione, verrà effettuata un'applicazione console c# in Visual Studio che genera un [NullReferenceException](http://msdn.microsoft.com/Library/658af786-d893-4114-a3c5-31c7d586056a).  
  
 In Visual Studio, creare un'applicazione console c# (**File > Nuovo > progetto > c# > applicazione Console**) denominato **ThrowsNullException**. Per ulteriori informazioni sulla creazione di progetti in Visual Studio, vedere [procedura dettagliata: creare una semplice applicazione](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md).  
  
 Quando il progetto verrà aperto in Visual Studio, aprire il file Program.cs. Sostituire il metodo Main () con il codice seguente, che stampa una riga nella console e quindi genera un'eccezione NullReferenceException:  
  
```csharp  
static void Main(string[] args)  
{  
    Console.WriteLine("we will now throw a NullReferenceException");  
    throw new NullReferenceException("this is the exception thrown by the console app");  
}  
```  
  
> [!IMPORTANT]
>  Affinché questa procedura per utilizzare un [configurazione release](../debugger/how-to-set-debug-and-release-configurations.md), è necessario disattivare [Just My Code](../debugger/just-my-code.md). In Visual Studio, fare clic su **strumenti > Opzioni**. Nel **opzioni** finestra di dialogo Seleziona **debug**. Rimuovere il segno di spunta da **Abilita Just My Code**.  
  
 Compilare la soluzione (in Visual Studio, scegliere **compilazione > Ricompila soluzione**). È possibile scegliere di Debug o la configurazione di rilascio (scegliere **Debug** per l'esperienza di debug completo). Per altre informazioni sulle configurazioni della build, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).  
  
 Il processo di compilazione crea un file eseguibile ThrowsNullException.exe. È possibile trovarlo sotto la cartella in cui è stato creato il progetto c#: **...\ThrowsNullException\ThrowsNullException\bin\Debug** o **...\ThrowsNullException\ThrowsNullException\bin\Release**.  
  
 Fare doppio clic il ThrowsNullException.exe. Verrà visualizzato una finestra di comando simile al seguente:  
  
 ![ThrowsNullExceptionConsole](../debugger/media/throwsnullexceptionconsole.png "ThrowsNullExceptionConsole")  
  
 Dopo alcuni secondi, viene visualizzata una finestra di errore:  
  
 ![ThrowsNullExceptionError](../debugger/media/throwsnullexceptionerror.png "ThrowsNullExceptionError")  
  
 Non fare clic **Annulla**! Dopo alcuni secondi, verrà visualizzato due pulsanti, **Debug** e **Chiudi programma**. Fare clic su **Debug**.  
  
> [!CAUTION]
>  Se l'applicazione contiene codice non attendibile, viene visualizzata una finestra di dialogo Avviso di protezione. Questa finestra di dialogo consente di decidere se procedere o meno con il debug. Prima di continuare con il debug, decidere se ritenere attendibile o meno il codice. Se il codice è stato scritto da altri, decidere se ritenere attendibile o meno l'autore. Se l'applicazione è in esecuzione in un computer remoto, assicurarsi di riconoscere il nome del processo. Anche se l'applicazione è in esecuzione in un computer locale, non significa che possa essere ritenuta attendibile. Considerare la possibilità di malware in esecuzione nel computer. Se si decide che il codice sta per debug è attendibile, fare clic su **Debug**. In caso contrario, fare clic su **non eseguire il Debug**.  
  
 Il **Debugger JIT di Visual Studio** verrà visualizzata la finestra:  
  
 ![JustInTimeDialog](../debugger/media/justintimedialog.png "JustInTimeDialog")  
  
 In **debugger**, si noterà che il **nuova istanza di Microsoft Visual Studio <available version>**  riga è selezionata. Se si non è già selezionato, selezionarla.  
  
 Nella parte inferiore della finestra, in **si desidera eseguire il debug utilizzando il debugger selezionato?**, fare clic su **Sì**.  
  
 Il progetto ThrowsNullException viene aperto in una nuova istanza di Visual Studio, con esecuzione interrotta alla riga che genera l'eccezione:  
  
 ![NullReferenceSecondInstance](../debugger/media/nullreferencesecondinstance.png "NullReferenceSecondInstance")  
  
 È possibile avviare il debug a questo punto. Se si trattasse di un'applicazione reale, è necessario scoprire perché il codice che genera l'eccezione.  
  
## <a name="just-in-time-debugging-errors"></a>Errori del debug JIT  
 Se non viene visualizzata la finestra di dialogo quando il programma si blocca, questo potrebbe essere dovuto alle impostazioni di segnalazione errori Windows nel computer in uso. Per ulteriori informazioni, vedere [. Le impostazioni di segnalazione errori Windows](/windows-hardware/drivers/dashboard/windows-error-reporting-getting-started).  
  
 I messaggi di errore elencati di seguito sono associati al debug JIT.  
  
-   **Impossibile connettersi al processo bloccato. Il programma specificato non è un programma Windows o MS-DOS.**  
  
     Questo errore si verifica quando si tenta di connettersi a un processo in esecuzione come altro utente.  
  
     Per risolvere il problema, avviare Visual Studio, aprire il **Connetti a processo** dalla finestra di dialogo di **Debug** menu e trovare il processo che si desidera eseguire il debug nel **processi disponibili**elenco. Se non si conosce il nome del processo, esaminare il **Debugger JIT di Visual Studio** finestra di dialogo e annotare l'ID del processo. Selezionare il processo di **processi disponibili** elenco e fare clic su **collegamento**. Nel **Debugger JIT di Visual Studio** finestra di dialogo, fare clic su **n** per chiudere la finestra di dialogo.  
  
-   **Impossibile avviare il debugger perché nessun utente è connesso.**  
  
     Questo errore si verifica quando il debug JIT tenta di avviare Visual Studio in un computer in cui nessun utente è connesso alla console. Poiché nessun utente è connesso, non esiste una sessione utente nella quale visualizzare la finestra di dialogo del debug JIT.  
  
     Per correggere questo problema, connettersi al computer.  
  
-   **Classe non registrata.**  
  
     Questo errore indica che il debugger ha tentato di creare una classe COM non registrata, probabilmente a causa di un problema di installazione.  
  
     Per risolvere questo problema, usare il disco di installazione per reinstallare o riparare l'installazione di Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Nozioni di base sul debugger](../debugger/debugger-basics.md)   
 [Just-In-Time, debug, finestra di dialogo Opzioni](../debugger/just-in-time-debugging-options-dialog-box.md)   
 [Avviso di sicurezza: la connessione a un processo appartenente a un utente non attendibile può essere pericolosa. Se le informazioni seguenti sono sospette o non si è certi della loro provenienza e del loro stato, non connettersi al processo.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)