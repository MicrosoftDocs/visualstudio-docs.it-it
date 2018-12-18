---
title: Variante delle dimensioni del Viewport 1x1 | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0c2f97793c838316d252aa56dcadd9fbb045decf
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="1x1-viewport-size-variant"></a>Variante delle dimensioni del viewport 1x1
Riduce a 1x1 pixel le dimensioni del riquadro di visualizzazione in tutte le destinazioni di rendering.  
  
## <a name="interpretation"></a>Interpretazione  
 In un riquadro di visualizzazione più piccolo il numero di pixel che devono essere ombreggiati è ridotto, ma non viene ridotto il numero di vertici che devono essere elaborati. L'impostazione delle dimensioni del riquadro di visualizzazione su 1x1 pixel consente di eliminare l'ombreggiatura dei pixel dall'app.  
  
 Se questa variante mostra un miglioramento notevole delle prestazioni, questo potrebbe indicare un utilizzo eccessivo della velocità di riempimento, a significare che la risoluzione scelta è troppo elevata per la piattaforma di destinazione o che l'app impiega troppo tempo per l'ombreggiatura di pixel che in seguito vengono sovrascritti (caricamento). Il risultato suggerisce che la riduzione delle dimensioni del buffer frame o della quantità di caricamento determina un miglioramento delle prestazioni dell'app.  
  
## <a name="remarks"></a>Note  
 Le dimensioni del riquadro di visualizzazione vengono reimpostate su 1x1 pixel dopo ogni chiamata a `ID3D11DeviceContext::OMSetRenderTargets` o `ID3D11DeviceContext::RSSetViewports`.  
  
## <a name="example"></a>Esempio  
 Questa variante può essere riprodotta usando codice simile al seguente:  
  
```  
D3D11_VIEWPORT viewport;  
viewport.TopLeftX = 0;  
viewport.TopLeftY = 0;  
viewport.Width = 1;  
viewport.Height = 1;  
d3d_context->RSSetViewports(1, &viewport);  
```