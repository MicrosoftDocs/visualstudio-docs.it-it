---
title: Gestione delle risorse delle applicazioni (.NET) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- Resource Designer
- resources [Visual Studio]
- Resources page in Project Designer
- application resources [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2006f565edbca8a859cd2c155645e47e083b5528
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/12/2018
---
# <a name="managing-application-resources-net"></a>Gestione delle risorse delle applicazioni (.NET)

I file di risorse sono file che fanno parte di un'applicazione ma non vengono compilati, ad esempio file di icone o file audio. Poiché questi file non fanno parte del processo di compilazione, è possibile modificarli senza dover ricompilare i file binari. Se si prevede di localizzare l'applicazione, è consigliabile usare file di risorse per tutte le stringhe e le altre risorse che devono essere modificate quando si localizza l'applicazione.

Per altre informazioni sulle risorse nelle app desktop .NET, vedere [Resources in Desktop Apps](/dotnet/framework/resources/index).

## <a name="working-with-resources"></a>Uso delle risorse

In un progetto di codice gestito aprire la finestra delle proprietà del progetto. È possibile aprire la finestra delle proprietà in uno dei modi seguenti:

- fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e selezionare **Proprietà**
- digitare "proprietà progetto" nella finestra **Avvio veloce**
- scegliere **ALT**+**INVIO** nella finestra **Esplora soluzioni**

Selezionare la scheda **Risorse** . È possibile aggiungere un file RESX, se non è ancora presente nel progetto, aggiungere ed eliminare diversi tipi di risorse e modificare le risorse esistenti.

## <a name="resources-in-other-project-types"></a>Risorse in altri tipi di progetto

Le risorse vengono gestite in modo diverso nei progetti .NET rispetto ad altri tipi di progetto. Per altre informazioni sulle risorse in:

- app della piattaforma UWP (Universal Windows Platform), vedere [Risorse dell'app e sistema di gestione delle risorse](/windows/uwp/app-resources/)
- progetti C++, vedere [Utilizzo di file di risorse](/cpp/windows/working-with-resource-files) e [Procedura: creare una risorsa](/cpp/windows/how-to-create-a-resource)

## <a name="see-also"></a>Vedere anche

[Risorse nelle applicazioni desktop (.NET Framework)](/dotnet/framework/resources/index)