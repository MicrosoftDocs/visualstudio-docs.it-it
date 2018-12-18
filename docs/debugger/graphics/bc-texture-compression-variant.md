---
title: Variante di compressione della trama BC | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d0f5305-585b-4b01-bc9a-7a32d6e991da
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 13b97c4d9e90adf8b621100d6d2a68d11570e71d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="bc-texture-compression-variant"></a>Variante di compressione della trama BC
Abilita la compressione a blocchi in tutte le trame con un formato di pixel che è una variante del formato B8G8R8X8, B8G8R8A8 o R8G8B8A8.  
  
## <a name="interpretation"></a>Interpretazione  
 I formati di compressione basati su blocchi,ad esempio BC1, BC2 e BC3, occupano una quantità di memoria molto inferiore rispetto ai formati di immagine non compressi e, di conseguenza, anche la larghezza di banda della memoria usata risulta molto inferiore. Rispetto a un formato non compresso che usa 32 bit per pixel, il formato BC1 (precedentemente noto come DXT1) raggiunge una compressione di 8:1 e il formato BC3 (precedentemente noto come DXT5) raggiunge una compressione di 4:1. La differenza tra il formato BC1 e BC3 sta nel fatto che BC1 non supporta un canale alfa, mentre BC3 supporta una canale alfa con compressione a blocchi. Nonostante i rapporti di compressione elevati, per le trame tipiche si registra solo una riduzione minima nella qualità dell'immagine. Tuttavia, la compressione a blocchi di determinati tipi di trame, ad esempio di quelle che presentano variazioni di colore significative in un'area di piccole dimensioni, può determinare risultati inaccettabili.  
  
 Se le trame sono adatte per la compressione basata su blocchi e non serve una fedeltà dei colori perfetta, valutare l'uso di un formato con compressione a blocchi per ridurre l'utilizzo della memoria e della larghezza di banda.  
  
## <a name="remarks"></a>Note  
 Per comprimere le trame, usare un formato di compressione basato su blocchi in ogni chiamata a `ID3DDevice::CreateTexture2D` che crea una trama di origine. In particolare, le trame vengono compresse quando:  
  
-   L'oggetto `D3D11_TEXTURE2D_DESC` passato a `pDesc` descrive una risorsa shader che non cambia, ovvero:  
  
    -   Il membro BindFlags presenta solo il flag D3D11_BIND_SHADER_RESOURCE impostato.  
  
    -   Il membro Usage è impostato su D3D11_USAGE_DEFAULT o su D3D11_USAGE_IMMUTABLE.  
  
    -   Il membro CPUAccessFlags è impostato su 0 (nessun accesso alla CPU).  
  
    -   Il membro Count del membro SamplerDesc è impostato su 1 (nessun anti-aliasing multicampione).  
  
-   Vengono forniti i dati iniziali alla chiamata a `CreateTexture2D`.  
  
 Di seguito sono riportati i formati di origine supportati e i relativi formati di compressione a blocchi.  
  
|Formato originale (da)|Formato compresso (a)|  
|------------------------------|------------------------------|  
|`DXGI_FORMAT_B8G8R8X8_UNORM`|BC1 (precedentemente DXT1)|  
|`DXGI_FORMAT_B8G8R8X8_UNORM_SRGB`|BC1|  
|`DXGI_FORMAT_B8G8R8X8_TYPELESS`|BC1|  
|`DXGI_FORMAT_B8G8R8A8_UNORM`|BC3 (precedentemente DXT5)|  
|`DXGI_FORMAT_B8G8R8A8_UNORM_SRGB`|BC3|  
|`DXGI_FORMAT_B8G8R8A8_TYPELESS`|BC3|  
|`DXGI_FORMAT_R8G8B8A8_UNORM`|BC3|  
|`DXGI_FORMAT_R8G8B8A8_UNORM_SRGB`|BC3|  
|`DXGI_FORMAT_R8G8B8A8_TYPELESS`|BC3|  
  
 Se il formato della trama non è presente in questo elenco, la trama non è modificata.  
  
## <a name="restrictions-and-limitations"></a>Limiti e restrizioni  
 In alcuni casi, le trame create con una variante dei formati di immagine B8G8R8A8 o R8G8B8A8 non usano effettivamente il canale alfa, ma la variante non può verificare se sia usato o meno. Per mantenere la correttezza nel caso in cui il canale alfa sia usato, la variante codifica sempre questi formati nel formato BC3 meno efficiente. È possibile consentire all'analisi dei frame di grafica di ottenere informazioni sulle potenziali prestazioni di rendering con questa variante usando una variante del formato di immagine B8G8R8X8 quando non è presente il canale alfa, in modo da poter usare il formato BC1 più efficiente.  
  
## <a name="example"></a>Esempio  
 Questa variante esegue la compressione a blocchi delle trame in fase di esecuzione, prima della chiamata a `CreateTexture2D`. Per il codice di produzione, questo approccio è sconsigliato perché le trame a dimensioni intere occupano più spazio su disco e perché il passaggio aggiuntivo può aumentare in modo significativo i tempi di caricamento nell'app, perché la compressione basata su blocchi richiede risorse di elaborazione notevoli per la codifica. È invece consigliabile comprimere le trame offline usando un editor o programma per l'elaborazione di immagini che faccia parte della pipeline di compilazione. Questi approcci riducono i requisiti di spazio su disco ed eliminano sovraccarichi in fase di esecuzione nell'app, oltre a restituire una quantità di tempo di elaborazione che consente di mantenere la migliore qualità di immagine.  
  
## <a name="see-also"></a>Vedere anche  
 [Variante delle dimensioni della trama a metà o un quarto](half-quarter-texture-dimensions-variant.md)