---
title: 'Procedura dettagliata: Creazione di un Editor personalizzato | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ecc70112dc89a1866a4688fd39d8a2aae129387b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-creating-a-custom-editor"></a>Procedura dettagliata: Creazione di un Editor personalizzato
Il modello di progetto VSPackage è possibile creare un editor personalizzato semplice in C++.  Il modello di progetto VSPackage non supporta più progetti in c# o Visual Basic. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="the-visual-studio-package-project-template"></a>Il modello di progetto di pacchetto di Visual Studio  
 Il modello di progetto di pacchetto di Visual Studio, vedere il **nuovo progetto** finestra di dialogo nella cartella Extensibility C++  
  
### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Per creare un pacchetto VSPackage usando il modello di pacchetto di Visual Studio  
  
1.  Creare un progetto con il modello di pacchetto di Visual Studio.  
  
2.  Selezionare il **Editor personalizzato** opzione e fare clic su **Avanti**. Il **opzioni dell'Editor** viene visualizzata la pagina.  
  
3.  Digitare il nome dell'editor nel **nome Editor** casella. Digitare l'estensione di file che si desidera essere associata con l'editor nel **estensione** casella. L'editor è disponibile per i file con questa estensione. L'estensione di file è registrata per Visual Studio solo, non per Windows. Digitare il nome di file predefinito per nuovi documenti creati con l'editor nel **nome File predefinito** casella.  
  
4.  Fare clic su **Fine** per creare il pacchetto VSPackage nella cartella specificata.  
  
### <a name="to-test-your-custom-editor"></a>Per testare l'editor personalizzato  
  
1.  Nel **File** dal menu **New** e quindi fare clic su **File**.  
  
2.  Nel **modelli installati** riquadro del **nuovo File** la finestra di dialogo, seleziona il modello di file, quindi il file di tipo appena registrato.  
  
3.  Fare clic su **aprire** per visualizzare e modificare il documento.  
  
     L'editor supporta operazioni di taglia e Incolla, ricerca e sostituzione e open-carico.  
  
## <a name="see-also"></a>Vedere anche  
 [Pacchetti VSPackage](../extensibility/internals/vspackages.md)