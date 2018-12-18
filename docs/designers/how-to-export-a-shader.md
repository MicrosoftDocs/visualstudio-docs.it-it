---
title: 'Procedura: Esportare uno shader | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6b4c7cedd267ba02772db16e026803061933cf5d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-export-a-shader"></a>Procedura: Esportare uno shader
Questo documento illustra come usare la finestra di progettazione shader per esportare uno shader DGSL (Directed Graph Shader Language) da usare nell'app.  
  
 Questo documento illustra questa attività:  
  
-   Esportazione di uno shader  
  
## <a name="exporting-a-shader"></a>Esportazione di uno shader  
 Dopo aver creato uno shader tramite la finestra di progettazione shader, prima di poterlo usare nell'app è necessario esportarlo in un formato supportato dall'API di grafica in uso. È possibile esportare uno shader in modi diversi, in base alle proprie esigenze.  
  
#### <a name="to-export-a-shader"></a>Per esportare uno shader  
  
1.  In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aprire un file **Visual Shader Graph (.dgsl)**.  
  
     Se non ha un file **Visual Shader Graph (.dgsl)** da aprire, crearne uno come descritto in [Procedura: Creare uno shader con colore di base](../designers/how-to-create-a-basic-color-shader.md).  
  
2.  Nella barra degli strumenti **Progettazione shader** scegliere **Avanzate**, **Esporta**, **Esporta come**. Viene visualizzata la finestra di dialogo **Esporta shader**.  
  
3.  Nell'elenco a discesa **Salva come** scegliere il formato in cui si vuole esportare il file.  
  
     Di seguito sono illustrati i formati che è possibile scegliere:  
  
     **Pixel shader HLSL (\*.hlsl)**  
     Esporta lo shader come codice sorgente High Level Shader Language (HLSL). Questa opzione consente di modificare lo shader in un secondo momento, anche dopo essere stato distribuito in un'app. Offre quindi l'opportunità di eseguire il debug e correggere il codice in base ai problemi riscontrati dagli utenti finali, ma al tempo stesso rende anche più facile per un utente modificare lo shader in modi indesiderati, ad esempio per ottenere un vantaggio sleale in un gioco competitivo. È inoltre possibile aumentare il tempo di caricamento dello shader.  
  
     **Pixel shader compilato (\*.cso)**  
     Esporta lo shader come bytecode HLSL. Questa opzione consente di modificare lo shader in un secondo momento, anche dopo essere stato distribuito in un'app. Offre quindi l'opportunità di eseguire il debug e correggere il codice in base ai problemi riscontrati dagli utenti finali ma, poiché lo shader è precompilato, non comporta un sovraccarico di runtime aggiuntivo quando lo shader viene caricato dall'app. Utenti sufficientemente esperti possono comunque modificare lo shader in modi indesiderati, ma la compilazione dello shader rende questa operazione molto più difficile.  
  
     **Intestazione C++ (\*.h)**  
     Esporta lo shader come intestazione di tipo C che definisce una matrice di byte contenente il bytecode HLSL. Questa opzione allunga i tempi necessari per eseguire il debug e correggere il codice in base ai problemi riscontrati dagli utenti finali, perché per testare la correzione è necessario ricompilare l'app. Questa opzione rende particolarmente difficile, seppure non impossibile, modificare lo shader dopo essere stato distribuito in un'app. Eventuali utenti che intendano modificare lo shader in modi indesiderati riscontreranno quindi grandi difficoltà.  
  
4.  Nella casella combinata **Nome file** specificare un nome per lo shader esportato e scegliere il pulsante **Salva**.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Creare uno shader con colore di base](../designers/how-to-create-a-basic-color-shader.md)   
 [Finestra di progettazione shader](../designers/shader-designer.md)