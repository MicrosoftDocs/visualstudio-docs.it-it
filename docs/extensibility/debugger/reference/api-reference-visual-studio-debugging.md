---
title: Riferimento all'API (debug di Visual Studio) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9f6e3110ca4988fcc12e547f3bcd82c1026f3aeb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="api-reference-visual-studio-debugging"></a>Riferimento all'API (debug di Visual Studio)
La sezione di riferimento include una panoramica concettuale dell'API, una Guida che illustra la sintassi e utilizzo per tutti gli elementi API e un'ampia gamma di esempi di codice. Tutti i riferimenti sono elencati in ordine alfabetico in base alla categoria.  
  
 La tabella seguente illustra il comune `HRESULT` valori restituiti dai metodi.  
  
|nome|Descrizione|Valore|  
|----------|-----------------|-----------|  
|S_OK|Operazione completata.|0x00000000|  
|E_UNEXPECTED|Errore imprevisto.|0x8000ffff|  
|E_NOTIMPL|Non implementato.|0x80004001|  
|E_OUTOFMEMORY|Memoria insufficiente per completare l'operazione.|0x8007000E|  
|E_INVALIDARG|Uno o più argomenti non sono validi.|0x80070057|  
|E_NOINTERFACE|Interfaccia non supportata.|0x80004002|  
|E_POINTER|Puntatore non valido.|0x80004003|  
|E_HANDLE|Handle non valido.|0x80070006|  
|E_ABORT|Operazione interrotta.|0x80004004|  
|E_FAIL|Errore imprevisto.|0x80004005|  
|E_ACCESSDENIED|Errore di accesso generale negato.|0x80070005|  
  
> [!NOTE]
>  Quando un [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] debug metodo restituisce `S_OK`, si presuppone che tutte le risorse sono validi i puntatori di parametro, vale a dire alcuna convalida non viene effettuata su out puntatori parametro quando `S_OK` viene restituito.  
  
> [!NOTE]
>  Non valido o `NULL` [parametri out] può causare l'IDE di arresto anomalo del sistema.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Estendibilità del debugger di Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)