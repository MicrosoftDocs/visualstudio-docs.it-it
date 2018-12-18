---
title: Caratteri speciali di escape | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- special characters to escape
- msbuild, special characters to escape
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a155d2d85f0b6208b98587f6907c8dadfd92d737
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="special-characters-to-escape"></a>Caratteri speciali di escape
I caratteri speciali devono essere preceduto da un carattere di escape solo se hanno un significato speciale nel contesto in cui vengono usati. Ad esempio, l'asterisco (*) è un carattere speciale solo negli attributi "Include" ed "Exclude" di una definizione di elemento o in una chiamata a <xref:Microsoft.Build.Tasks.CreateItem>. In tutti gli altri casi, l'asterisco viene considerato come un asterisco letterale. Nonostante non sia necessario usare il carattere di escape davanti agli asterischi in ogni parte dei file di progetto, l'operazione non causa problemi.  
  
 Usare la notazione %*xx* al posto del carattere speciale, dove *xx* rappresenta il valore esadecimale del carattere ASCII. Ad esempio, per usare un asterisco (*) come carattere letterale, usare il valore `%2A`.  
  
 Di seguito è riportato l'elenco completo dei caratteri speciali di escape:  
  
|Carattere|Descrizione|  
|---------------|-----------------|  
|%|Segno di percentuale, usato per fare riferimento a metadati.|  
|$|Segno di dollaro, usato per fare riferimento alle proprietà.|  
|@|Chiocciola, usata per fare riferimento agli elenchi di elementi.|  
|(|Parentesi di apertura, usata negli elenchi.|  
|)|Parentesi di chiusura, usata negli elenchi.|  
|`|Apostrofo o segno di graduazione, usato in condizioni e altre espressioni.|  
|;|Punto e virgola, separatore di elenco.|  
|?|Punto interrogativo, un carattere jolly usato nel descrivere le specifiche di un file nella sezione Include/Exclude di un elemento.|  
|*|Asterisco, un carattere jolly usato nel descrivere le specifiche di un file nella sezione Include/Exclude di un elemento.|  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Usare caratteri di escape speciali in MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)   
 [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)