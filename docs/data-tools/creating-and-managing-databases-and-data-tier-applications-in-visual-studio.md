---
title: Progetti di database, i progetti server e progetti di applicazione livello dati in Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: e456d436145d859a24a224511dc69c1383bbcaeb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="database-projects-and-data-tier-applications-in-visual-studio"></a>Progetti di database e applicazioni livello dati in Visual Studio
È possibile utilizzare i progetti di database per creare nuovi database, le nuove applicazioni livello dati (DAC) e per aggiornare i database esistenti e le applicazioni livello dati. I progetti di database e progetti di applicazione livello dati consentono di applicare tecniche di gestione del progetto e del controllo di versione per le attività di sviluppo di database in modo che tali tecniche vengono applicate al codice gestito o nativo. Per aiutare il team di sviluppo gestire le modifiche al database e server di database creando un *progetto DAC*, *progetto di database*, o un *progetto server* e applicarlo nel controllo della versione. I membri del team possono quindi estrarre i file per apportare, compilare e testare le modifiche in un *ambiente di sviluppo isolato*, o sandbox, prima di condividerli con il team. Per garantire la qualità del codice, il team possa completare e verificare tutte le modifiche per una particolare versione del database in un ambiente di gestione temporanea prima di distribuire le modifiche nell'ambiente di produzione.

Per un elenco delle funzionalità di database che sono supportati dalle applicazioni livello dati, vedere [funzionalità supportate nelle applicazioni livello dati](http://go.microsoft.com/fwlink/?LinkId=164239) sul sito web Microsoft. Se si utilizza una funzionalità di database che non sono supportate dalle applicazioni livello dati, è invece necessario utilizzare un progetto di database per gestire le modifiche al database.

## <a name="common-high-level-tasks"></a>Attività comuni di alto livello

|Attività di livello superiore|Contenuto di supporto|
|----------------------|------------------------|
|**Avviare lo sviluppo di un'applicazione livello dati:** un'applicazione livello dati è un nuovo concetto introdotto con [!INCLUDE[sskatmai_r2](../data-tools/includes/sskatmai_r2_md.md)] che contiene la definizione per un [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] database e il supporto di oggetti utilizzati da un client-server o a 3 livelli delle istanze applicazione. Un'applicazione livello dati include oggetti di database quali tabelle e viste, insieme alle entità di istanza, ad esempio gli account di accesso. È possibile utilizzare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per creare un progetto di applicazione livello dati, compilare un file di pacchetto DAC e inviare tale file di pacchetto di applicazione livello dati a un amministratore del database per la distribuzione in un'istanza di [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] motore di database.|-   [La creazione e gestione di applicazioni livello dati](http://go.microsoft.com/fwlink/?LinkId=160741) (sito web Microsoft)<br />-   [SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=227328)|
|**L'esecuzione di sviluppo iterativo di database:** se si è uno sviluppatore o un tester, estrarre le parti del progetto e quindi aggiornarle in un ambiente di sviluppo isolato. Tramite questo tipo di ambiente, è possibile testare le modifiche senza influire su altri membri del team. Dopo aver completate le modifiche, estrarre i file nel controllo della versione, in cui altri membri del team possono ottenere le modifiche di compilazione e distribuirle in un server di prova.|-   [Editor di query e Text (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (sito web Microsoft)<br />-   [Debugger Transact-SQL](http://go.microsoft.com/fwlink/?LinkId=227324) (sito web Microsoft)|
|**La creazione di prototipi, verifica risultati del test e la modifica degli script del database e oggetti:** è possibile utilizzare il [!INCLUDE[tsql](../data-tools/includes/tsql_md.md)] editor per eseguire una di queste attività comuni.|-   [Editor di query e Text (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=227327) (sito web Microsoft)|

## <a name="see-also"></a>Vedere anche

- [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
