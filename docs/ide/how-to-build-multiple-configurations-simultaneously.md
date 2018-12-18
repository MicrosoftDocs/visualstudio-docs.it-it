---
title: "Procedura: Compilare più configurazioni contemporaneamente | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba830937-3317-4674-8cc2-c0cd565603c5
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 86c0a9fbbfe7e4b0b38b0286cf10f06dd7eec89c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-multiple-configurations-simultaneously"></a>Procedura: compilare più configurazioni contemporaneamente
È possibile compilare la maggior parte dei tipi di progetti con più configurazioni della build o con tutte le configurazioni contemporaneamente usando la finestra di dialogo **Compilazione batch**. Tuttavia, non è possibile compilare i seguenti tipi di progetti in più configurazioni della build contemporaneamente:  
  
1.  App di [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] compilata per Windows usando JavaScript.  
  
2.  Tutti i progetti di Visual Basic  
  
 Per altre informazioni sulle configurazioni della build, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).  
  
### <a name="to-build-a-project-in-multiple-build-configurations"></a>Per compilare un progetto in più configurazioni della build  
  
1.  Nella barra dei menu scegliere **Compilazione**, **Compilazione batch**.  
  
2.  Nella colonna **Compila** selezionare le caselle di controllo per le configurazioni in cui si vuole compilare un progetto.  
  
    > [!TIP]
    >  Per modificare o creare una configurazione della build per una soluzione, scegliere **Compilazione**, **Gestione configurazione** nella barra dei menu per aprire la finestra di dialogo **Gestione configurazione**. Dopo aver modificato una configurazione della build per una soluzione, scegliere il pulsante **Ricompila** nella finestra di dialogo **Compilazione batch** per aggiornare tutte le configurazioni della build per i progetti nella soluzione.  
  
3.  Scegliere i pulsanti **Compila** o **Ricompila** per compilare il progetto con le configurazioni specificate.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md)   
 [Understanding Build Configurations](../ide/understanding-build-configurations.md)  (Informazioni sulle configurazioni delle compilazioni)  
 [Compilazione di più progetti in parallelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)