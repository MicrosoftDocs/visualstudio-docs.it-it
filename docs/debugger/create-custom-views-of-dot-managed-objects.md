---
title: Creare viste personalizzate di oggetti gestiti | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data types [C#], custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6be491a5c7a0ceb0ed536416cdd3b273f96b4bb1
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="create-custom-views-of-managed-objects"></a>Creare viste personalizzate di oggetti gestiti
È possibile personalizzare la modalità di visualizzazione dei tipi di dati nelle finestre delle variabili del debugger in Visual Studio.  
  
## <a name="attributes"></a>Attributi  
 In C# e Visual Basic, è possibile aggiungere espansioni per dati personalizzati tramite <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, <xref:System.Diagnostics.DebuggerDisplayAttribute> e <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  
  
 Nel codice [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] Visual Basic non supporta l'attributo DebuggerBrowsable. Questa limitazione è stata rimossa nelle versioni più recenti di .NET Framework.  
  
## <a name="visualizers"></a>Visualizzatori  
 È possibile scrivere un visualizzatore per visualizzare qualsiasi tipo di dati gestito. Per ulteriori informazioni, vedere [procedura: scrivere un visualizzatore](../debugger/how-to-write-a-visualizer.md).  
  
## <a name="native-code"></a>Codice nativo  
 Per il codice nativo, è possibile aggiungere espansioni per tipi di dati personalizzati al file autoexp.dat, che si trova nella directory Programmi\Microsoft Visual Studio 11.0\Common7\Packages\Debugger. Le istruzioni relative alla sintassi delle regole `autoexp` sono contenute nel file stesso.  
  
> [!CAUTION]
>  La struttura di questo file e la sintassi delle regole autoexp possono variare in base alle diverse versioni di Visual Studio.  
  
 Le visualizzazioni del tipo nativo possono anche essere personalizzate scrivendo un componente aggiuntivo dell'analizzatore di espressioni. Per ulteriori informazioni, vedere [esempio EEAddIn: debug di espressione dell'analizzatore di espressioni componenti](http://msdn.microsoft.com/en-us/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e).  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo dell'attributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)   
 [Utilizzo dell'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)   
 [Espressioni di controllo e finestre di controllo immediato](../debugger/watch-and-quickwatch-windows.md)   
 [Miglioramento del debug tramite gli attributi di visualizzazione del debugger](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)