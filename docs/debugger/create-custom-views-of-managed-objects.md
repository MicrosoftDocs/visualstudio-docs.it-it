---
title: Creare visualizzazioni personalizzate di oggetti gestiti | Microsoft Docs
description: Il debugger di Visual Studio Visualizza i dati nelle finestre delle variabili. Informazioni su come personalizzare il modo in cui vengono visualizzati i tipi di dati, inclusi i tipi personalizzati.
ms.custom: SEO-VS-2020
ms.date: 01/08/2019
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data types, custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: c054d3bcfbb06d0093f04190ab8b4825b5cbf20f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865800"
---
# <a name="create-custom-views-of-managed-objects-c-visual-basic-f-ccli"></a>Creazione di visualizzazioni personalizzate di oggetti gestiti (C#, Visual Basic, F #, C++/CLI)
È possibile personalizzare la modalità di visualizzazione dei tipi di dati nelle finestre delle variabili del debugger in Visual Studio.

## <a name="attributes"></a>Attributi

In C#, Visual Basic, F # e C++ (solo codice C++/CLI), è possibile aggiungere espansioni per i dati personalizzati usando <xref:System.Diagnostics.DebuggerTypeProxyAttribute> , <xref:System.Diagnostics.DebuggerDisplayAttribute> e <xref:System.Diagnostics.DebuggerBrowsableAttribute> .

Nel codice .NET Framework 2,0 Visual Basic non supporta l'attributo l'DebuggerBrowsable. Questa limitazione è stata rimossa nelle versioni più recenti di .NET.

## <a name="visualizers"></a>Visualizzatori

È possibile scrivere un visualizzatore per visualizzare qualsiasi tipo di dati gestito. Per altre informazioni, vedere [procedura: scrivere un visualizzatore](create-custom-visualizers-of-data.md).

> [!NOTE]
> Per il codice C++, è possibile aggiungere espansioni di tipi di dati personalizzati usando natvis Framework, come descritto in [creare visualizzazioni personalizzate di oggetti C++ nel debugger](create-custom-views-of-native-objects.md).

## <a name="see-also"></a>Vedi anche

- [Indicare al debugger cosa visualizzare usando l'attributo DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md)
- [Indicare al debugger quale tipo visualizzare usando l'attributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)
- [Finestre Espressioni di controllo e Controllo immediato](../debugger/watch-and-quickwatch-windows.md)
- [Miglioramento del debug tramite gli attributi di visualizzazione del debugger](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
