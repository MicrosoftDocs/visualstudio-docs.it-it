---
title: Uso dei set di dati nelle applicazioni a più livelli
description: Informazioni su come usare i set di impostazioni in applicazioni a più livelli. Le applicazioni dati a più livelli sono app incentrate sui dati separate in più livelli logici (o livelli).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], n-tier applications
- multi-tier database applications
- DataSet project [VS n-tier applications]
- distributed applications [VS n-tier applications]
- data [Visual Basic], n-tier applications
- TableAdapters, n-tier applications
- n-tier applications
- tiers, n-tier applications
- typed datasets, n-tier applications
- multiple tier applications
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 93a221640ff7383b39bfdec73cbaa9659156e33f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858072"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Uso dei set di dati nelle applicazioni a più livelli

*Le applicazioni dati* a più livelli sono applicazioni incentrate sui dati separate in più livelli logici (o *livelli*). In altre parole, un'applicazione dati a più livelli è un'applicazione separata in più progetti, con il livello di accesso ai dati, il livello di logica di business e il livello di presentazione, ciascuno in un progetto distinto. Per altre informazioni, vedere [Panoramica delle applicazioni dati](../data-tools/n-tier-data-applications-overview.md)a più livelli.

I dataset tipizzati sono stati migliorati in modo da poter generare classi TableAdapter e di dataset in progetti discreti, consentendo di separare rapidamente i livelli dell'applicazione e generare applicazioni dati a più livelli.

Il supporto a più livelli nei dataset tipizzati consente lo sviluppo iterativo dell'architettura dell'applicazione in una progettazione a più livelli. Elimina inoltre la necessità di separare manualmente il codice in più di un progetto. Iniziare a progettare il livello dati usando il **Progettazione DataSet**. Prima di applicare l'architettura dell'applicazione in una progettazione a più livelli, impostare la proprietà **Progetto DataSet** di un set di dati per generare la classe di set di dati in un progetto separato.

## <a name="reference"></a>Riferimento

- <xref:System.Data.DataSet>
- <xref:System.Data.TypedTableBase%601>

## <a name="see-also"></a>Vedi anche

- [Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md)
- [Procedura dettagliata: creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Aggiungere il codice nei TableAdapter di applicazioni a più livelli](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Aggiungere il codice nei set di dati di applicazioni a più livelli](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Aggiungere la convalida a un set di dati a più livelli](../data-tools/add-validation-to-an-n-tier-dataset.md)
- [Separare set di dati e TableAdapter in progetti diversi](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)
- [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)
- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Creare e configurare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md)
- [Applicazioni a più livelli e remote con LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)
