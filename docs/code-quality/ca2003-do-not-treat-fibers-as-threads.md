---
title: 'CA2003: Non considerare i fiber come i thread'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf33bf27036400bd75b3c61960f35448df3abead
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: Non considerare i fiber come i thread
|||
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|Category|Microsoft.Reliability|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un thread gestito viene considerato come un thread Win32.

## <a name="rule-description"></a>Descrizione della regola
 Si presuppone che un thread gestito è un thread Win32. È un fiber. Common language runtime (CLR) eseguirà i thread gestiti come fiber nel contesto del thread reali che appartengono a SQL. Questi thread possono essere condivisi tra AppDomains e database nel processo di SQL Server. Utilizzando gestito funzionerà archiviazione locale di thread, ma è possibile non utilizzare l'archiviazione locale di thread non gestito o si presuppone che il codice verrà eseguito nuovamente sul thread del sistema operativo corrente. Non modificare le impostazioni, ad esempio le impostazioni locali del thread. Non chiamare CreateCriticalSection o CreateMutex tramite P/Invoke perché richiedono che il thread che accede a un blocco deve anche uscirne. Poiché non sarà il caso quando si utilizzano i fiber, i mutex e le sezioni critiche Win32 dovrà essere inutili, in SQL. Potrebbe essere possibile utilizzare la maggior parte dello stato su un oggetto System. thread gestito. Ciò include l'archiviazione locale di thread gestiti e le impostazioni cultura dell'interfaccia utente correnti del thread. Tuttavia, per motivi legati al modello di programmazione, non sarà in grado di modificare le impostazioni cultura correnti di un thread quando si utilizza SQL. verrà applicata una nuova autorizzazione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Esaminare l'utilizzo di thread e modificare di conseguenza il codice.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non è necessario eliminare questa regola.