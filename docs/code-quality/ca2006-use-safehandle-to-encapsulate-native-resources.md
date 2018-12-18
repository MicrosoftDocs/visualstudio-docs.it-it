---
title: 'CA2006: Utilizzare SafeHandle per incapsulare le risorse native'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: dc059f606da3229351e749a4e27ad87f2055fa8c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: Utilizzare SafeHandle per incapsulare le risorse native
|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Category|Microsoft.Reliability|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Il codice gestito utilizza <xref:System.IntPtr> per accedere alle risorse native.

## <a name="rule-description"></a>Descrizione della regola
 Utilizzo di `IntPtr` in codice gestito potrebbe indicare un potenziale problema di sicurezza e affidabilità. Tutte le occorrenze di `IntPtr` devono essere esaminate per determinare se l'utilizzo di un <xref:System.Runtime.InteropServices.SafeHandle> , o una tecnologia simile, è necessario al suo posto. Se si verificheranno problemi di `IntPtr` rappresenta una risorsa nativa, ad esempio memoria, un handle di file o un socket, che il codice gestito si considera. Se il codice gestito proprietario della risorsa, è necessario rilasciare anche le risorse native a esso associate, perché un errore a tale scopo potrebbe causare la perdita della risorsa.

 In questi scenari, i problemi di sicurezza o di affidabilità saranno disponibile anche se è consentito l'accesso multithreading di `IntPtr` e modalità di rilascio della risorsa che è rappresentata dal `IntPtr` viene fornito. Questi problemi riguardano il riciclo del `IntPtr` valore sul rilascio di risorse durante l'utilizzo simultaneo della risorsa è stata effettuata in un altro thread. Ciò può causare una race condition in cui un thread può leggere o scrivere i dati associati con la risorsa errata. Ad esempio, se il tipo è archiviato un handle del sistema operativo come un `IntPtr` e consente agli utenti di chiamare entrambe **Chiudi** e qualsiasi altro metodo che utilizza tale handle simultaneamente e senza alcun tipo di sincronizzazione, il codice include un riciclo esiste un problema.

 Questo problema di riciclo può causare il danneggiamento dei dati e, spesso una vulnerabilità di sicurezza. `SafeHandle` e la relativa classe di elemento di pari livello <xref:System.Runtime.InteropServices.CriticalHandle> forniscono un meccanismo per incapsulare un handle nativo di una risorsa in modo che è possibile evitare tali problemi di threading. Inoltre, è possibile utilizzare `SafeHandle` e la relativa classe di elemento di pari livello `CriticalHandle` per altri problemi di threading, ad esempio, per controllare con attenzione la durata degli oggetti gestiti che contengono una copia dell'handle nativo nelle chiamate ai metodi nativi. In questo caso, è spesso possibile evitare le chiamate a `GC.KeepAlive`. Il sovraccarico delle prestazioni che si verifica quando si utilizza `SafeHandle` e, a un livello inferiore, `CriticalHandle`, possono spesso essere ridotti attraverso un'attenta progettazione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Convertire `IntPtr` l'utilizzo di `SafeHandle` per gestire in modo sicuro l'accesso alle risorse native. Vedere il <xref:System.Runtime.InteropServices.SafeHandle> argomento di riferimento per gli esempi.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non è necessario eliminare l'avviso.

## <a name="see-also"></a>Vedere anche
 <xref:System.IDisposable>