---
title: Supporto del threading in Office | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3383e3767c97efad9177f0e361524137ea5d66a8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="threading-support-in-office"></a>Supporto del threading in Office
  In questo argomento vengono fornite informazioni sulle modalità di supporto del threading nel modello a oggetti Microsoft Office. Il modello a oggetti Office non è thread-safe, ma è possibile utilizzare più thread in una soluzione Office. Le applicazioni di Office sono server modello COM (Component Object). COM consente ai client di chiamare server COM con thread arbitrari. Per i server COM che non sono thread-safe, COM fornisce un meccanismo per la serializzazione di chiamate simultanee in modo che un solo thread logico viene eseguito nel server in qualsiasi momento. Questo meccanismo è noto come modello di apartment a thread singolo (STA). Poiché le chiamate vengono serializzate, i chiamanti potrebbero essere bloccati per periodi di tempo, mentre il server è occupato o si sta gestendo altre chiamate in un thread in background.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="knowledge-required-when-using-multiple-threads"></a>Conoscenza necessaria per l'utilizzo di più thread  
 Per lavorare con più thread, è richiesta la conoscenza di base dei seguenti aspetti di multithreading:  
  
-   API di Windows  
  
-   COM concetti con multithreading  
  
-   Concorrenza  
  
-   Sincronizzazione  
  
-   marshalling  
  
 Per informazioni generali sul multithreading, vedere [Managed Threading](/dotnet/standard/threading/).  
  
 Office viene eseguita in sta primario. Comprendere le implicazioni di questo oggetto consente di comprendere come utilizzare più thread con Office.  
  
## <a name="basic-multithreading-scenario"></a>Scenario Multithreading di base  
 Codice nelle soluzioni Office viene sempre eseguito nel thread principale dell'interfaccia utente. Si potrebbe voler riducono le prestazioni dell'applicazione mediante l'esecuzione di un'attività distinta su un thread in background. L'obiettivo è completare idealmente due attività in una sola volta anziché una sola attività seguita da altri, consentendo una migliore esecuzione (il principale motivo per l'utilizzo di più thread). Ad esempio, potrebbe essere il codice di eventi nel thread principale dell'interfaccia utente di Excel e in un thread in background è possibile eseguire un'attività che raccoglie i dati da un server e aggiorna le celle nell'interfaccia utente di Excel con i dati dal server.  
  
## <a name="background-threads-that-call-into-the-office-object-model"></a>Thread in background che effettuano chiamate nel modello a oggetti di Office  
 Quando un thread in background effettua una chiamata all'applicazione di Office, viene effettuato automaticamente il marshalling della chiamata attraverso il limite dell'APARTMENT. Tuttavia, non è garantito che l'applicazione di Office può gestire la chiamata al momento che rende il thread in background. Esistono diverse possibilità:  
  
1.  L'applicazione di Office deve pumping dei messaggi per la chiamata abbia la possibilità di immettere. Se viene eseguito con intensa attività di elaborazione senza cede il controllo si potrebbe richiedere del tempo.  
  
2.  Se un altro thread logico è già in apartment, non è possibile immettere il nuovo thread. Questo accade spesso quando un thread logico entra nell'applicazione di Office e quindi effettua una chiamata rientrante all'apartment del chiamante. L'applicazione è bloccato in attesa della chiamata.  
  
3.  Excel potrebbe essere in uno stato in modo che non può gestire immediatamente una chiamata in ingresso. L'applicazione di Office, ad esempio, potrebbe essere visualizzata una finestra di dialogo modale.  
  
 Per le possibilità 2 e 3, COM fornisce il [IMessageFilter](http://msdn.microsoft.com/en-us/e12d48c0-5033-47a8-bdcd-e94c49857248) interfaccia. Se il server implementa, tutte le chiamate immettere tramite il [HandleIncomingCall](http://msdn.microsoft.com/en-us/7e31b518-ef4f-4bdd-b5c7-e1b16383a5be) metodo. Possibilità 2, le chiamate vengono rifiutate automaticamente. Possibilità di 3, il server può rifiutare la chiamata, a seconda delle circostanze. Se la chiamata viene rifiutata, il chiamante deve decidere come procedere. In genere, l'oggetto implementa chiamante [IMessageFilter](http://msdn.microsoft.com/en-us/e12d48c0-5033-47a8-bdcd-e94c49857248), nel qual caso sarebbe stato informato del rifiuto da parte di [RetryRejectedCall](http://msdn.microsoft.com/en-us/3f800819-2a21-4e46-ad15-f9594fac1a3d) metodo.  
  
 Tuttavia, nel caso di soluzioni create mediante gli strumenti di sviluppo per Office in Visual Studio, l'interoperabilità COM converte tutte le chiamate rifiutate per una <xref:System.Runtime.InteropServices.COMException> ("il filtro messaggi ha indicato che l'applicazione è occupata"). Quando si esegue un modello a oggetti chiamata su un thread in background, è necessario per essere pronti a gestire questa eccezione. In genere, che richiede un nuovo tentativo per un determinato periodo di tempo e quindi visualizzando una finestra di dialogo. Tuttavia, è possibile creare il thread in background come STA e quindi registrare un filtro messaggi per il thread gestire questa situazione.  
  
## <a name="starting-the-thread-correctly"></a>È possibile avviare correttamente il Thread  
 Quando si crea un nuovo thread STA, impostare lo stato dell'apartment STA prima di avviare il thread. Nell'esempio di codice seguente viene illustrato come procedere.  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]  
  
 Per ulteriori informazioni, vedere [Managed Threading Best Practices](/dotnet/standard/threading/managed-threading-best-practices).  
  
## <a name="modeless-forms"></a>Form non modali  
 Un form non modale consente un certo tipo di interazione con l'applicazione mentre viene visualizzato il modulo. L'utente interagisce con il modulo e quest ' ultimo interagisce con l'applicazione senza chiudere. Il modello a oggetti Office supporta gestito form modale. Tuttavia, non devono essere usati in un thread in background.  
  
## <a name="see-also"></a>Vedere anche  
 [Threading gestito](/dotnet/standard/threading/)  
 [Threading (c#)](/dotnet/csharp/programming-guide/concepts/threading/index) [Threading (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)   
 [Utilizzo di thread e threading](/dotnet/standard/threading/using-threads-and-threading)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)  
  
  