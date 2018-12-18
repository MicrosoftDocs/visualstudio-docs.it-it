---
title: 'Procedura: Configurare progetti per le piattaforme di destinazione | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project settings [Visual Studio], targeting platforms
- platforms, targeting specific CPUs
- project properties [Visual Studio], targeting platforms
- projects [Visual Studio], targeting platforms
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- CPUs, targeting specific
- 64-bit applications [Visual Studio]
ms.assetid: 845302fc-273d-4f81-820a-7296ce91bd76
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0ccca87721c39daa7e613d7426c9d5fed6a144cf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-projects-to-target-platforms"></a>Procedura: configurare progetti per le piattaforme di destinazione
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consente di configurare le applicazioni per diverse piattaforme di destinazione, tra cui le piattaforme a 64 bit. Per altre informazioni sul supporto delle piattaforme a 64 bit in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vedere [Applicazioni a 64 bit](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181).  
  
## <a name="targeting-platforms-with-the-configuration-manager"></a>Individuazione delle piattaforme di destinazione con Gestione configurazione  
 La **Gestione configurazione** consente di aggiungere rapidamente una nuova piattaforma di destinazione al progetto. Se si seleziona una delle piattaforme incluse con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], le proprietà del progetto vengono modificate per compilare il progetto per la piattaforma selezionata.   
  
#### <a name="to-configure-a-project-to-target-a-64-bit-platform"></a>Per configurare un progetto per una piattaforma a 64 bit  
  
1.  Nella barra dei menu scegliere **Compilazione**, **Gestione configurazione**.  
  
2.  Nell'elenco **Piattaforma soluzione attiva** scegliere una piattaforma a 64 bit di destinazione per la soluzione e quindi scegliere il pulsante **Chiudi**.  
  
    1.  Se la piattaforma non compare nell'elenco **Piattaforma soluzione attiva**, scegliere **Nuovo**.  
  
         Viene visualizzata la finestra di dialogo **Nuova piattaforma soluzione**.  
  
    2.  Nell'elenco **Digitare o selezionare la nuova piattaforma** scegliere **x64**.  
  
        > [!NOTE]
        >  Se si specifica un nuovo nome per la configurazione, potrebbe essere necessario modificare le impostazioni in **Creazione progetti** per la piattaforma corretta.  
  
    3.  Se si vuole copiare le impostazioni da una configurazione di piattaforma corrente, selezionarla e quindi fare clic sul pulsante **OK**.  
  
 Le proprietà per tutti i progetti destinati alla piattaforma a 64 bit vengono aggiornate e la compilazione successiva del progetto verrà ottimizzata per le piattaforme a 64 bit.   
  
## <a name="targeting-platforms-in-the-project-designer"></a>Individuazione delle piattaforme di destinazione in Progettazione progetti  
 Anche Progettazione progetti consente di creare diverse piattaforme di destinazione per il progetto. Se la selezione di una delle piattaforme incluse nell'elenco della finestra di dialogo **Nuova piattaforma soluzione** non è applicabile alla soluzione, è possibile creare un nome di configurazione personalizzato e modificare le impostazioni in **Creazione progetti** per la piattaforma di destinazione corretta.  
  
 L'esecuzione di questa attività varia in base al linguaggio di programmazione usato. Per altre informazioni, vedere i collegamenti che seguono:  
  
-   Per i progetti [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], vedere [/platform (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/platform).  
  
-   Per i progetti [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)], vedere [Pagina Compilazione, Creazione progetti (C#)](../ide/reference/build-page-project-designer-csharp.md).  
  
-   Per i progetti [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], vedere [/clr (Compilazione Common Language Runtime)](/cpp/build/reference/clr-common-language-runtime-compilation).  
  
## <a name="see-also"></a>Vedere anche  
 [Understanding Build Platforms](../ide/understanding-build-platforms.md)  (Informazioni sulle piattaforme di compilazione)  
 [/platform (opzioni del compilatore C#)](/dotnet/csharp/language-reference/compiler-options/platform-compiler-option)   
 [Applicazioni a 64 bit](http://msdn.microsoft.com/Library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Supporto a 64 bit per l'IDE di Visual Studio](../ide/visual-studio-ide-64-bit-support.md)