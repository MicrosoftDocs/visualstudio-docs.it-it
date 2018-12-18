---
title: 'Procedura: Configurare progetti per piattaforme di destinazione multiple | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], targeting platforms
- platforms, changing target platforms
ms.assetid: affa2392-7aed-45ac-9ffa-1d8e0496d590
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7686e792d804af85bb8f9588f3ae78fd6b6ec3e3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-projects-to-target-multiple-platforms"></a>Procedura: configurare progetti per piattaforme di destinazione multiple
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consente di creare una soluzione per architetture CPU o piattaforme di destinazione diverse. Le proprietà per questa impostazione sono disponibili nella finestra di dialogo **Gestione configurazione**.  
  
## <a name="targeting-a-platform"></a>Impostazione di una piattaforma come destinazione  
 La finestra di dialogo **Gestione configurazione** consente di creare e impostare configurazioni e piattaforme a livello di soluzione e progetto. Ogni combinazione di configurazioni a livello di soluzione e destinazioni può avere un solo set di proprietà associato consentendo di passare facilmente tra una configurazione di versione per una piattaforma [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)], una configurazione di versione per una piattaforma x86 e una configurazione di debug per una piattaforma x86.  
  
#### <a name="to-set-your-configuration-to-target-a-different-platform"></a>Per impostare una piattaforma diversa come destinazione della configurazione  
  
1.  Nel menu **Compila** fare clic su **Gestione configurazione**.  
  
2.  Nella casella **Piattaforma soluzione attiva** selezionare la piattaforma che si vuole impostare come destinazione della soluzione oppure selezionare **\<Nuovo>** per creare una nuova piattaforma. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] compila l'applicazione impostando come destinazione la piattaforma specificata come piattaforma attiva nella finestra di dialogo **Gestione configurazione**.  
  
## <a name="removing-a-platform"></a>Rimozione di una piattaforma  
 Se una piattaforma non è più necessaria, è possibile rimuoverla usando la finestra di dialogo Gestione configurazione. Verranno rimosse tutte le impostazioni di soluzione e progetto configurate per la combinazione di configurazione e destinazione.  
  
#### <a name="to-remove-a-platform"></a>Per rimuovere una piattaforma  
  
1.  Nel menu **Compila** fare clic su **Gestione configurazione**.  
  
2.  Nella casella **Piattaforma soluzione attiva** selezionare **\<Modifica>**. Viene visualizzata la finestra di dialogo **Modifica piattaforme soluzione**.  
  
3.  Fare clic sulla piattaforma da rimuovere e quindi su **Rimuovi**.  
  
## <a name="targeting-multiple-platforms-with-one-solution"></a>Impostazione di più piattaforme come destinazione di un'unica soluzione  
 Poiché è possibile modificare le impostazioni in base alla combinazione di configurazione e piattaforma, è possibile impostare una soluzione con più piattaforme come destinazione .  
  
#### <a name="to-target-multiple-platforms"></a>Per impostare più piattaforme come destinazione  
  
1.  Usare **Gestione configurazione** per aggiungere almeno due piattaforme di destinazione per la soluzione.  
  
2.  Selezionare la piattaforma di destinazione dall'elenco **Piattaforma soluzione attiva**.  
  
3.  Compilare la soluzione.  
  
#### <a name="to-build-multiple-solution-configurations-at-once"></a>Per creare più configurazioni di soluzione contemporaneamente  
  
1.  Usare **Gestione configurazione** per aggiungere almeno due piattaforme di destinazione per la soluzione.  
  
2.  Usare la finestra **Compilazione batch** per compilare più configurazioni di soluzione contemporaneamente.  
  
 È possibile avere una piattaforma a livello di soluzione impostata ad esempio su [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)] e non avere all'interno della soluzione alcun progetto per la stessa piattaforma. È anche possibile avere più progetti nella soluzione ognuno con una piattaforma diversa come destinazione. In questi casi è consigliabile creare una nuova configurazione con un nome descrittivo per evitare confusione.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md)   
 [Understanding Build Configurations](../ide/understanding-build-configurations.md)  (Informazioni sulle configurazioni delle compilazioni)  
 [Building and Cleaning Projects and Solutions in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) (Compilazione e pulizia di progetti e soluzioni in Visual Studio)