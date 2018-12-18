---
title: "Procedura: eseguire la migrazione di progetti di estendibilità di Visual Studio 2015 | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ec87a48e61ee69e01032c3b702ae21d6944eee92
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Procedura: eseguire la migrazione di progetti di estendibilità di Visual Studio 2015
Di seguito viene illustrato come aggiornare l'estensione.  
  
> [!IMPORTANT]
>  Se si prevede di gestire una versione della soluzione di estensione per una versione precedente di Visual Studio, assicurarsi di effettuare una copia prima di aggiornarlo. Potrebbe risultare difficile restituire la versione aggiornata allo stato precedente.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>Per eseguire l'aggiornamento di una soluzione di estendibilità  
  
1.  Utilizzando la copia da aggiornare, aprirlo nella nuova versione. Verrà richiesto che l'aggiornamento non è reversibile.  
  
2.  Al termine dell'aggiornamento, è possibile modificare il percorso del programma esterno per la nuova versione di devenv.exe. Pulsante destro del mouse sul nodo del progetto nel **Esplora**, quindi scegliere **proprietà**. Nel **Debug** scheda, la casella di testo da trovare **Avvia programma esterno** e modificare il percorso di devenv.exe al percorso di Visual Studio 2015, dovrebbe essere simile al seguente:  
  
     **%ProgramFiles%\Microsoft visual Studio 14.0\Common7\IDE\devenv.exe**  
  
3.  Aggiungere un riferimento a Microsoft.VisualStudio.Shell.14.0.dll. (Fare doppio clic sul nodo del progetto nel **Esplora soluzioni** e quindi scegliere **aggiungere /Reference**. Selezionare il **estensioni** e quindi controllare **14.0**.)  
  
4.  Compilare la soluzione. Vengono distribuiti i file compilati:  
  
     **%LocalAppData%\Microsoft\VisualStudio.14.0Exp\Extensions\\< nome autore\>\\< nome progetto\>\\< versione progetto\> \\** .  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Per aggiornare un progetto di estendibilità per gli assembly di riferimento NuGet VS SDK  
  
1.  Determinare gli assembly di riferimento di VS SDK per il progetto necessario.  In **Esplora**, espandere il progetto **riferimenti** nodo ed esaminare l'elenco di riferimenti al progetto.  Gli assembly di riferimenti di Visual Studio SDK avrà il prefisso **Microsoft.VisualStudio** nel nome (ad esempio: 14.0).  
  
2.  Rimuovere gli assembly di riferimento di VS SDK dal progetto selezionandoli, fare clic destro e **rimuovere**.  
  
3.  Aggiungere le versioni di NuGet di assembly di riferimento di Visual Studio SDK.  Mentre si trovano ancora nella **i riferimenti di Esplora soluzioni** nodo, aprire il **Gestisci pacchetti NuGet...**  finestra di dialogo.  Se si desidera approfondire la conoscenza di questa finestra di dialogo, vedere [UI Package Manager](/NuGet/Tools/Package-Manager-UI). Gli assembly di riferimento di VS SDK vengono pubblicati su [nuget.org](http://www.nuget.org) da [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4.  Utilizzando **nuget.org** come il **origine pacchetto**, cercare il nome del pacchetto NuGet che corrisponde all'assembly di riferimento desiderato (ad esempio: 14.0) e installarlo nel progetto.  NuGet può aggiungere più assembly di riferimento per soddisfare le dipendenze dell'assembly iniziale.  
  
     Se si preferisce, è possibile aggiungere contemporaneamente tutti gli assembly di riferimento di Visual Studio SDK mediante l'installazione di VS SDK [pacchetto Meta](http://www.nuget.org/packages/VSSDK_Reference_Assemblies).  
  
5.  È inoltre possibile passare alla utilizzando la versione NuGet degli strumenti di compilazione di Visual Studio SDK. Questo pacchetto NuGet è [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) e una volta aggiunti per includere gli strumenti necessari e file consente di compilare il progetto di estendibilità in un computer senza installato il SDK di Visual Studio di destinazione del progetto di.  
  
> [!NOTE]
>  Non è necessario aggiornare i progetti di estendibilità esistenti per l'utilizzo di strumenti e gli assembly di riferimento di NuGet.  Possono continuare a compilare usando gli assembly di riferimento e gli strumenti installati con il SDK di Visual Studio.