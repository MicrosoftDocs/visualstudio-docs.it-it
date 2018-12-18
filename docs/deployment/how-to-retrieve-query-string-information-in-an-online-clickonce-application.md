---
title: "Procedura: recuperare informazioni sulle stringhe di Query in un'applicazione ClickOnce Online | Documenti Microsoft"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, query strings
- query strings, retrieving information
ms.assetid: 48ce098a-a075-481b-a5f5-c8ba11f63120
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47d20cf156cfdb6aaa18e37160dbf027bb3fb519
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-retrieve-query-string-information-in-an-online-clickonce-application"></a>Procedura: recuperare informazioni sulle stringhe di query in un'applicazione ClickOnce online
La *stringa di query* è la parte di un URL che inizia con un punto interrogativo (?) e contiene informazioni arbitrarie nel formato *nome = valore*. Si supponga di avere un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] denominata `WindowsApp1` che è ospitare in `servername`e di voler passare un valore per la variabile `username` quando l'applicazione viene avviata. L'aspetto dell'URL potrebbe essere simile al seguente:  
  
 `http://servername/WindowsApp1.application?username=joeuser`  
  
 Le due procedure seguenti illustrano come usare un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] per ottenere informazioni sulla stringa di query.  
  
> [!NOTE]
>  È possibile passare informazioni in una stringa di query solo quando l'applicazione viene avviata usando HTTP anziché una condivisione file o il file system locale.  
  
 La prima procedura mostra come l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] può usare una piccola parte di codice per leggere questi valori quando l'applicazione viene avviata.  
  
 La procedura seguente illustra come configurare l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] usando MageUI.exe in modo che possa accettare parametri della stringa di query. È necessario eseguire questa operazione ogni volta che si pubblica l'applicazione.  
  
> [!NOTE]
>  Prima di decidere se attivare questa funzionalità, vedere la sezione "Sicurezza" più avanti in questo argomento.  
  
 Per informazioni su come creare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione tramite Mage.exe o MageUI.exe, vedere [procedura dettagliata: distribuzione manuale di un'applicazione ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
> [!NOTE]
>  A partire da .NET Framework 3.5 SP1, è possibile passare argomenti della riga di comando in un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] offline. Se si desidera fornire argomenti all'applicazione, è possibile passare parametri al file di collegamento con l'estensione .APPREF-MS.  
  
### <a name="to-obtain-query-string-information-from-a-clickonce-application"></a>Per ottenere informazioni sulla stringa di query da un'applicazione ClickOnce  
  
1.  Includere il codice seguente nel progetto. Affinché questo codice funzioni, è necessario avere un riferimento a System.Web e aggiungere le istruzioni `using` o `Imports` per System.Web, System.Collections.Specialized e System.Deployment.Application.  
  
     [!code-csharp[ClickOnceQueryString#1](../deployment/codesnippet/CSharp/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.cs)]
     [!code-vb[ClickOnceQueryString#1](../deployment/codesnippet/VisualBasic/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.vb)]  
  
2.  Chiamare la funzione definita in precedenza per recuperare un <xref:System.Collections.DictionaryBase.Dictionary%2A> dei parametri della stringa di query, indicizzati per nome.  
  
### <a name="to-enable-query-string-passing-in-a-clickonce-application-with-mageuiexe"></a>Per abilitare la stringa di query passando un'applicazione ClickOnce con MageUI.exe  
  
1.  Aprire il prompt dei comandi .NET e digitare:  
  
    ```  
    MageUI  
    ```  
  
2.  Nel menu **File** selezionare **Apri**e aprire il manifesto di distribuzione per l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , che è il file con l'estensione `.application` .  
  
3.  Selezionare il riquadro **Opzioni di distribuzione** nella finestra di navigazione a sinistra e selezionare la casella di controllo **Consenti passaggio di parametri URL all'applicazione** .  
  
4.  Nel menu **File** selezionare **Salva**.  
  
> [!NOTE]
>  In alternativa è possibile abilitare la stringa di query passando [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Selezionare la casella di controllo **Consenti passaggio di parametri URL all'applicazione** , a cui si accede aprendo **Proprietà progetto**selezionando la scheda **Pubblica** e facendo clic sul pulsante **Opzioni** e quindi selezionando **Manifesti**.  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Quando si usano parametri di stringa di query, è necessario valutare attentamente come l'applicazione è installata e attivata. Se l'applicazione è configurata per essere installata nel computer dell'utente dal Web o da una condivisione di rete, è probabile che l'utente attiverà l'applicazione solo una volta tramite l'URL. Successivamente, l'utente attiverà l'applicazione usando il collegamento nel menu **Start** . Di conseguenza, è garantito che l'applicazione riceverà gli argomenti della stringa di query una sola volta durante tutta la sua vita. Se si sceglie di archiviare questi argomenti sul computer dell'utente per uso futuro, è necessario archiviarli in modo sicuro e protetto.  
  
 Se l'applicazione è solo online, verrà sempre attivata tramite un URL. Anche in questo caso, tuttavia, l'applicazione deve essere scritta in modo da funzionare correttamente se i parametri della stringa di query mancano o sono danneggiati.  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 Consentire il passaggio di parametri URL all'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] solo se si prevede di ripulire l'input da eventuali caratteri dannosi prima di usarlo. Una stringa incorporata con virgolette, barre o punto e virgola, ad esempio, potrebbe eseguire le operazioni di dati arbitrarie se viene impiegata senza essere filtrata in una query SQL su un database. Per altre informazioni sulla sicurezza delle stringhe di query, vedere [Script Exploits Overview](http://msdn.microsoft.com/Library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07).  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)