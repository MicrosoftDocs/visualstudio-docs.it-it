---
title: Dimensioni di trama a metà trimestre variante | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 282e9bbb-51aa-4cd0-8e5c-0901268c29e5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b19a7c8444264300bdb819152769f1760d4a4d3e
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="halfquarter-texture-dimensions-variant"></a>Variante delle dimensioni della trama ridotte a metà o un quarto
Riduce le dimensioni della trama per trame che non sono destinazioni di rendering.  
  
## <a name="interpretation"></a>Interpretazione  
 Le trame più piccole occupano meno memoria e consumano quindi meno larghezza di banda di memoria, riducendo il carico sulla cache della trama della GPU. Il minore dettaglio può tuttavia causare una riduzione della qualità dell'immagine, in particolare quando queste vengono visualizzate in modo ravvicinato in una scena 3D o in condizioni di ingrandimento.  
  
 Se questa variante mostra un miglioramento notevole delle prestazioni, ciò potrebbe indicare un consumo eccessivo della larghezza di banda di memoria da parte dell'app, un uso inefficiente della cache della trama o entrambi. Può anche indicare che le trame occupano più memoria GPU di quella disponibile, con conseguente paging delle trame nella memoria di sistema.  
  
 Se l'app consuma troppa larghezza di banda di memoria o fa un uso inefficiente della cache della trama, considerare una riduzione delle dimensioni delle trame, ma solo dopo aver previsto l'abilitazione delle mappe MIP per le trame appropriate. Come accade per le trame più piccole, le trame con mappe MIP usano meno larghezza di banda di memoria (pur occupando più memoria GPU) e aumentano l'uso della cache, ma senza ridurre il dettaglio della trama. Le mappe MIP sono consigliate nei casi in cui l'aumento dell'uso di memoria non causa il paging delle trame nella memoria di sistema.  
  
 Se le trame occupano più memoria di quella disponibile, considerarne la riduzione delle dimensioni, ma solo dopo avere previsto la compressione delle trame appropriate. Come accade per le trame più piccole, le trame compresse occupano meno memoria e riducono la necessità di paging nella memoria di sistema, tuttavia la fedeltà dei colori risulterà ridotta. A seconda del contenuto delle trame, la compressione può non sempre rappresentare la soluzione appropriata, ad esempio nel caso di trame con variazioni di colore significative. Per molte trame, tuttavia, la compressione può permettere di conservare una migliore qualità complessiva dell'immagine rispetto alla loro riduzione.  
  
## <a name="remarks"></a>Note  
 Le dimensioni della trama vengono ridotte a ogni chiamata a `ID3D11Device::CreateTexture2D` che crea una trama di origine. In particolare, le dimensioni della trama vengono ridotte quando l'oggetto D3D11_TEXTURE2D_DESC passato in `pDesc` descrive una trama che viene usata nel rendering, ovvero:  
  
-   Il membro BindFlags presenta solo il flag D3D11_BIND_SHADER_RESOURCE impostato.  
  
-   Il membro MiscFlags non presenta il flag D3D11_RESOURCE_MISC_TILE_POOL o il flag D3D11_RESOURCE_MISC_TILED impostato (le risorse allocate dinamicamente non vengono ridimensionate).  
  
-   Il formato della trama è supportato come destinazione di rendering, come determinato da D3D11_FORMAT_SUPPORT_RENDER_TARGET, il che è necessario per ridurre le dimensioni della trama. I formati BC1, BC2 e BC3 sono anch'essi supportati, sebbene non lo siano come destinazioni di rendering.  
  
 Se i dati iniziali vengono forniti dall'applicazione, questa variante ridimensiona i dati della trama in modo appropriato prima di creare la trama stessa. Se i dati iniziali vengono forniti in un formato a blocchi compressi come BC1, BC2 o BC3, questi vengono decodificati, ridimensionati, quindi ricodificati prima di essere usati per creare la trama di dimensioni minori. A causa della natura della compressione basata su blocchi, il processo di decodifica, ridimensionamento e ricodifica risulta sempre in una qualità dell'immagine inferiore rispetto a quando una trama con compressione a blocchi viene generata da una versione ridimensionata di una trama non precedentemente codificata.  
  
 Se vengono generate mappe MIP per la trama, la variante riduce il numero di livelli MIP di conseguenza, un livello in meno quando si dimezzano le dimensioni o due livelli in meno quando si riducono di tre quarti.  
  
## <a name="example"></a>Esempio  
 Questa variante ridimensiona le trame in fase di esecuzione prima della chiamata a `CreateTexture2D`. Per codice di produzione, questo approccio è sconsigliato perché le trame a dimensioni intere occupano più spazio su disco e perché il passaggio aggiuntivo può aumentare i tempi di caricamento nell'app, in particolare per quanto riguarda le trame compresse, che richiedono risorse di elaborazione notevoli per la codifica. È invece consigliabile ridimensionare le trame offline usando un editor o programma per l'elaborazione di immagini che faccia parte della pipeline di compilazione. Questi approcci riducono i requisiti di spazio su disco ed eliminano sovraccarichi di in fase di esecuzione nell'app, oltre a restituire una quantità di tempo di elaborazione che consente di mantenere la miglior qualità di immagine riducendo o comprimendone le trame.  
  
## <a name="see-also"></a>Vedere anche  
 [Variante di generazione di mappe MIP](mip-map-generation-variant.md)   
 [Variante di compressione della trama BC](bc-texture-compression-variant.md)