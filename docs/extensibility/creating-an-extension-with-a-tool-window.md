---
title: Creazione di un'estensione con una finestra degli strumenti | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f918a5b8b48a7b9553cf3ca2e6c8fe9d38fbc9b8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="creating-an-extension-with-a-tool-window"></a>Creazione di un'estensione con una finestra degli strumenti
In questa procedura imparare a utilizzare il modello di progetto VSIX e **finestra degli strumenti personalizzata** modello di elemento per creare un'estensione con una finestra degli strumenti.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="creating-a-tool-window"></a>Creazione di una finestra degli strumenti  
  
1.  Creare un progetto VSIX denominato **FirstWindow**. È possibile trovare il modello di progetto VSIX nel **nuovo progetto** nella finestra di dialogo **Visual c# / Extensibility**.  
  
2.  Quando si apre il progetto, aggiungere un modello di elemento della finestra dello strumento denominato **MyWindow**. Nel **Esplora**del mouse sul nodo del progetto e scegliere **Aggiungi / nuovo elemento**. Nel **Aggiungi nuovo elemento** finestra di dialogo, passa a **Visual c# / Extensibility** e selezionare **finestra degli strumenti personalizzata**. Nel **nome** campo nella parte inferiore della finestra, modificare il nome file della finestra dello strumento per **MyWindow.cs**.  
  
3.  Compilare il progetto e avviare il debug.  
  
     Viene visualizzata l'istanza sperimentale di Visual Studio. Per ulteriori informazioni sull'istanza sperimentale, vedere [l'istanza sperimentale](../extensibility/the-experimental-instance.md).  
  
4.  Nell'istanza sperimentale, passare a **vista o altre finestre**.  
  
     Verrà visualizzata una voce di menu per **MyWindow**. Fare clic.  
  
     Si dovrebbe essere una finestra degli strumenti con il titolo **MyWindow** e una massima pulsante **Click Me!.**