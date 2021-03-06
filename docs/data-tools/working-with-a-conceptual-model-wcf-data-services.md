---
title: Uso di un modello concettuale (WCF Data Services)
description: Utilizzare un modello concettuale in WCF Data Services. Eseguire query sui dati tramite oggetti anziché convertirli tra gli schemi di database e i modelli a oggetti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], querying a service
- data [Visual Studio], LINQ to Entities
- data [Visual Studio], querying an EDM
ms.assetid: 2cd873cf-b010-49f2-a278-bb1277aaa934
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: ef5745f974848da75b4dcc0c42b59b38aa61cd0b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866112"
---
# <a name="work-with-a-conceptual-model-wcf-data-services"></a>Utilizzare un modello concettuale (WCF Data Services)

Quando si utilizza un modello concettuale per descrivere i dati in un database, è possibile eseguire query sui dati attraverso gli oggetti anziché dover eseguire la conversione tra uno schema di database e un modello a oggetti.

È possibile utilizzare i modelli concettuali con le applicazioni Data Services WCF. Negli argomenti seguenti viene illustrato come eseguire query sui dati tramite un modello concettuale.

| Argomento | Descrizione |
| - | - |
| [Procedura: eseguire query sul servizio dati](/dotnet/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services) | Viene illustrato come eseguire una query su un servizio dati da un'applicazione .NET. |
| [Procedura: proiettare risultati di query](/dotnet/framework/data/wcf/how-to-project-query-results-wcf-data-services) | Viene illustrato come ridurre la quantità di dati restituiti tramite una query del servizio dati. |

Quando si utilizza un modello concettuale, è possibile definire il tipo di dati valido nella lingua corrispondente al dominio. È possibile definire dati validi nel modello oppure è possibile aggiungere la convalida alle operazioni eseguite su un'entità o un servizio dati.

Negli argomenti riportati di seguito viene illustrato come aggiungere la convalida alle applicazioni WCF Data Services.

|Argomento|Descrizione|
|-----------|-----------------|
|[Procedura: intercettare messaggi del servizio dati](/dotnet/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services)|Viene illustrato come aggiungere la convalida a un'operazione del servizio dati.|

 Negli argomenti seguenti viene illustrato come creare, aggiornare ed eliminare dati eseguendo operazioni sulle entità.

|Argomento|Descrizione|
|-----------|-----------------|
|[Procedura: aggiungere, modificare ed eliminare entità](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)|Viene illustrato come creare, aggiornare ed eliminare dati di entità in un servizio dati.|
|[Procedura: definire le relazioni tra entità](/dotnet/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services)|Viene illustrato come creare o modificare le relazioni in un servizio dati.|

## <a name="see-also"></a>Vedi anche

- [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Esecuzione di query sul servizio dati](/dotnet/framework/data/wcf/querying-the-data-service-wcf-data-services)
