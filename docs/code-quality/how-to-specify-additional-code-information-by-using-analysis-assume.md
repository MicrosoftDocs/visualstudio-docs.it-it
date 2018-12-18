---
title: 'Procedura: specificare informazioni aggiuntive sul codice utilizzando analysis_assume | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: __analysis_assume
helpviewer_keywords: __analysis_assume
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 72b72ce474a24d77b3b40513c2e69fb5ab4aea59
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-additional-code-information-by-using-analysisassume"></a>Procedura: specificare informazioni aggiuntive sul codice utilizzando __analysis_assume
È possibile fornire suggerimenti per lo strumento di analisi codice per il codice C/C++ che guida il processo di analisi e ridurre gli avvisi. Per fornire informazioni aggiuntive, utilizzare la funzione seguente:  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr`-qualsiasi espressione che deve per restituire true.  
  
 Lo strumento di analisi del codice si presuppone che la condizione rappresentata dall'espressione sia true nel punto in cui la funzione viene visualizzata e rimanga true finché l'espressione viene modificata, ad esempio, tramite l'assegnazione alla variabile.  
  
> [!NOTE]
>  `__analysis_assume`non influisce sull'ottimizzazione del codice. Lo strumento di analisi del codice, di fuori `__analysis_assume` è definito come alcuna operazione.  
  
## <a name="example"></a>Esempio  
 Il codice seguente usa `__analysis_assume` per correggere l'avviso di analisi del codice [C6388](../code-quality/c6388.md):  
  
```  
#include<windows.h>  
#include<codeanalysis\sourceannotations.h>  
  
using namespace vc_attributes;  
  
// calls free and sets ch to null  
void FreeAndNull(char* ch);  
  
//requires pc to be null  
void f([Pre(Null=Yes)] char* pc);  
  
void test( )  
{  
  char *pc = (char*)malloc(5);  
  FreeAndNull(pc);  
  __analysis_assume(pc == NULL);   
  f(pc);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [__assume](/cpp/intrinsics/assume)