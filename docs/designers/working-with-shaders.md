---
title: Utilizzo degli shader | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b2ea1ed-b995-4e75-af19-c68fd37a3bc5
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: bf96f1cdbdf8e3f995d8a1020a655b73d369cf7d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="working-with-shaders"></a>Utilizzo degli shader
È possibile usare la finestra di progettazione shader basata su grafico in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per progettare effetti shader personalizzati. È possibile usare gli shader nelle app o nei giochi basati su DirectX.  
  
## <a name="shaders"></a>Shader  
 Uno *shader* è un programma per computer che esegue calcoli grafici, ad esempio le trasformazioni di vertice o la colorazione dei pixel. In genere viene eseguito su un'unità di elaborazione grafica (GPU) anziché su una CPU. Poiché le fasi della tradizionale pipeline grafica a funzioni fisse vengono ora eseguite per la maggior parte dai programmi shader, è possibile usare questi ultimi per creare una pipeline specifica per le esigenze dell'applicazione.  
  
 I tipi più comuni di shader sono i *vertex shader*, che eseguono calcoli per vertice e sostituiscono i circuiti di trasformazione e di illuminazione a funzioni fisse in hardware per grafica non programmabile, e i *pixel shader*, che eseguono calcoli per pixel in grado di determinare il colore dei singoli pixel e sostituire i circuiti di combinazione dei colori a funzioni fisse in hardware per grafica non programmabile. Nell'hardware per grafica moderno sono inclusi anche altri tipi di shader: *hull shader*, *domain shader* e *geometry shader* per i calcoli di grafica e *compute shader* per i calcoli non di grafica. Nessuna di queste fasi è disponibile nell'hardware per grafica non programmabile. Gli shader sono stati originariamente creati tramite un linguaggio di tipo di assembly che ha fornito istruzioni dati in parallelo (SIMD) e incentrate su grafici (prodotto scalare). Ora gli shader vengono in genere creati usando linguaggi di alto livello simili al C, ad esempio HLSL (High Level Shader Language).  
  
 È possibile usare la finestra di progettazione shader per creare i pixel shader in modo interattivo anziché mediante l'immissione e la compilazione di codice. Nella finestra di progettazione shader, uno shader è definito da una serie di nodi che rappresentano i dati e le operazioni, oltre che da connessioni tra i nodi che rappresentano il flusso dei valori di dati e risultati intermedi attraverso lo shader stesso. Usando questo approccio e l'anteprima in tempo reale nella finestra di progettazione shader, è possibile visualizzare l'esecuzione dello shader in modo più facile e "scoprire" variazioni interessanti mediante sperimentazioni.  
  
## <a name="dgsl-documents"></a>Documenti DGSL  
 Nella finestra di progettazione shader, gli shader vengono salvati in formato DGSL (Directed Graph Shader Language), un formato XML basato sul linguaggio DGML (Directed Graph Markup Language). È possibile applicare shader DGSL direttamente ai modelli 3D nell'editor modello. Prima di poter usare uno shader DGSL nell'applicazione, è tuttavia necessario esportarlo in un formato noto a DirectX, ad esempio HLSL.  
  
 Poiché DGSL è compatibile con DGML, è possibile usare gli strumenti progettati per analizzare i documenti DGML anche per analizzare gli shader DGSL. Per altre informazioni su DGML, vedere [Informazioni su DGML (Directed Graph Markup Language)](http://msdn.microsoft.com/library/ee842619.aspx).  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Finestra di progettazione shader](../designers/shader-designer.md)|Descrive come utilizzare la finestra di progettazione shader di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per utilizzare gli shader.|  
|[Nodi della finestra di progettazione shader](../designers/shader-designer-nodes.md)|Vengono descritti i tipi di nodi della finestra di progettazione shader che è possibile usare per realizzare effetti grafici.|  
|[Esempi della finestra di progettazione shader](../designers/shader-designer-examples.md)|Vengono forniti collegamenti ad argomenti che illustrano come usare la finestra di progettazione shader per realizzare comuni effetti di grafica.|