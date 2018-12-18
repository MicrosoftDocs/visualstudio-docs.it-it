---
title: 'CA2001: Evitare le chiamate a metodi problematici | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2001
- AvoidCallingProblematicMethods
helpviewer_keywords:
- CA2001
- AvoidCallingProblematicMethods
ms.assetid: 19db8edb-31ce-441c-b0de-a0f2746155b7
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: da5da213d400f846f634a98dbdbe919cedf03bcd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca2001-avoid-calling-problematic-methods"></a>CA2001: Evitare le chiamate a metodi problematici
|||  
|-|-|  
|TypeName|AvoidCallingProblematicMethods|  
|CheckId|CA2001|  
|Category|Microsoft.Reliability|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Un membro chiama un metodo potenzialmente pericoloso o problematico.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Evitare di effettuare chiamate a metodi potenzialmente pericolosi e superflui.  
  
 Una violazione di questa regola si verifica quando un membro chiama uno dei metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|<xref:System.GC.Collect%2A?displayProperty=fullName>|La chiamata a GC. Raccogli possono influire in modo significativo le prestazioni dell'applicazione ed sono raramente necessaria. Per ulteriori informazioni, vedere il [Performance Tidbits Rico](http://go.microsoft.com/fwlink/?LinkId=169256) post di blog su MSDN.|  
|<xref:System.Threading.Thread.Resume%2A?displayProperty=fullName><br /><br /> <xref:System.Threading.Thread.Suspend%2A?displayProperty=fullName>|Thread. Suspend e Resume sono state deprecate a causa di un comportamento imprevedibile.  Usare le altre classi nel <xref:System.Threading> dello spazio dei nomi, ad esempio <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>, <xref:System.Threading.Mutex>, e <xref:System.Threading.Semaphore> per sincronizzare i thread o proteggere le risorse.|  
|<xref:System.Runtime.InteropServices.SafeHandle.DangerousGetHandle%2A?displayProperty=fullName>|Il metodo DangerousGetHandle pone un rischio per la sicurezza in quanto può restituire un handle che non è valido. Vedere il <xref:System.Runtime.InteropServices.SafeHandle.DangerousAddRef%2A> e <xref:System.Runtime.InteropServices.SafeHandle.DangerousRelease%2A> metodi per ulteriori informazioni su come usare il metodo DangerousGetHandle in modo sicuro.|  
|<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName><br /><br /> <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName>|Questi metodi possono caricare l'assembly da posizioni non previste. Ad esempio, vedere i post di blog di .NET CLR Notes Suzanne Cook [LoadFile vs. LoadFrom](http://go.microsoft.com/fwlink/?LinkId=164450) e [scelta di un contesto di associazione](http://go.microsoft.com/fwlink/?LinkId=164451) nel sito Web MSDN per informazioni sui metodi che caricano gli assembly.|  
|[CoSetProxyBlanket](http://go.microsoft.com/fwlink/?LinkID=169250) (Ole32)<br /><br /> [CoInitializeSecurity](http://go.microsoft.com/fwlink/?LinkId=169255) (Ole32)|Una volta il codice utente avvia l'esecuzione in un processo gestito, è troppo tardi per chiamare in modo affidabile CoSetProxyBlanket. Common language runtime (CLR) esegue operazioni di inizializzazione che possono impedire agli utenti di P/Invoke di.<br /><br /> Se è necessario chiamare CoSetProxyBlanket per un'applicazione gestita, è consigliabile avviare il processo utilizzando un file eseguibile di codice nativo (C++), chiamare CoSetProxyBlanket nel codice nativo e quindi avviare l'applicazione di codice gestito nel processo. (Assicurarsi di specificare un numero di versione del runtime.)|  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, rimuovere o sostituire la chiamata al metodo pericoloso o problematico.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È necessario eliminare i messaggi da questa regola solo quando nessun alternative al metodo problematico sono disponibili.  
  
## <a name="see-also"></a>Vedere anche  
 [Avvisi di affidabilità](../code-quality/reliability-warnings.md)