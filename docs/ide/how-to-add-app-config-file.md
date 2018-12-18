---
title: Come aggiungere un file app.config in un progetto in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords: app.config files, adding to C# projects
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: d77e86599670ef04b813381da84a03ab1f238af3
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2018
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Procedura: aggiungere un file di configurazione dell'applicazione a un progetto C#

Aggiungendo un file di configurazione dell'applicazione (file app.config) a un progetto C#, è possibile personalizzare il modo in cui CLR individua e carica i file di assembly. Per altre informazioni sui file di configurazione dell'applicazione, vedere [Come il runtime individua gli assembly (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Le app UWP non contengono un file app.config.

Quando si compila il progetto, l'ambiente di sviluppo copia automaticamente il file app.config, modifica il nome di file della copia in modo che corrisponda all'eseguibile, quindi sposta la copia nella directory **bin**.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Per aggiungere un file di configurazione dell'applicazione a un progetto C#

1. Nella barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento**.

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento**.

1. Espandere **Installati** > **Elementi di Visual C#** e quindi scegliere il modello **File di configurazione dell'applicazione**.

Nella casella di testo **Nome** immettere un nome e quindi scegliere il pulsante **Aggiungi**.

     A file named app.config is added to your project.

## <a name="see-also"></a>Vedere anche

[Gestione delle impostazioni di un'applicazione (.NET)](../ide/managing-application-settings-dotnet.md)  
[Schema del file di configurazione (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)  
[Configurazione di app (.NET Framework)](/dotnet/framework/configure-apps/index)