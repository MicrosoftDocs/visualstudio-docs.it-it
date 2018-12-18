---
title: 'CA1301: Evitare tasti di scelta rapida duplicati | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a61e4c0ab9957772609c20623f0bc6ef7659a9d2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: Evitare tasti di scelta rapida duplicati
|||  
|-|-|  
|TypeName|AvoidDuplicateAccelerators|  
|CheckId|CA1301|  
|Category|Microsoft.Globalization|  
|Modifica importante|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Estende un tipo <xref:System.Windows.Forms.Control?displayProperty=fullName> e contiene due o più controlli di primo livello che presentano tasti di scelta identici vengono archiviati in un file di risorse.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Un tasto di scelta o tasto di scelta rapida consente l'accesso da tastiera a un controllo mediante ALT. Quando più controlli presentano tasti di scelta duplicati, il comportamento del tasto di scelta non è ben definito. L'utente potrebbe non essere in grado di accedere al controllo desiderato utilizzando la chiave di accesso e un controllo diverso da quello che è possibile che sia attivato.  
  
 L'implementazione corrente di questa regola ignora le voci di menu. Tuttavia, le voci di menu nel sottomenu stesso non devono essere identica tasti di scelta.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, definire le chiavi di accesso univoco per tutti i controlli.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un form minimo che contiene due controlli che dispongono di chiavi di accesso identici. Le chiavi vengono archiviate in un file di risorse, non viene visualizzato. Tuttavia, i relativi valori vengono visualizzati in impostati come commento out `checkBox.Text` righe. Il comportamento dei tasti di scelta rapida duplicati può essere esaminato tramite lo scambio di `checkBox.Text` righe con le controparti impostate come commentata. Tuttavia, in questo caso, l'esempio non genererà un avviso dalla regola.  
  
 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [Risorse nelle applicazioni desktop](/dotnet/framework/resources/index)