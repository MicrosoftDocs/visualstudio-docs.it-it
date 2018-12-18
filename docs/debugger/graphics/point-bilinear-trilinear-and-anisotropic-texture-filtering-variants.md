---
title: Punti, bilineare, trilineare e anisotropico della trama varianti del filtro | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57d14fc9-b5f7-45ee-9717-48086886742d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ed1306d8bca70cd80f50c2980f76c5efc3588279
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="point-bilinear-trilinear-and-anisotropic-texture-filtering-variants"></a>Varianti del filtro della trama a punti, bilineare, trilineare e anisotropico
Esegue l'override della modalità di filtraggio sui campionatori di trame appropriati.  
  
## <a name="interpretation"></a>Interpretazione  
 Diversi metodi di campionamento delle trame presentano diversi livelli di impatto sulle prestazioni e sulla qualità dell'immagine. Le modalità di filtraggio, in ordine crescente di impatto e di qualità dell'immagine, sono le seguenti:  
  
1.  Filtraggio punti (impatto minimo, livello minimo di qualità visiva)  
  
2.  Filtraggio bilineare  
  
3.  Filtraggio trilineare  
  
4.  Filtraggio anisotropo (massimo impatto, massima qualità visiva)  
  
 Se l'impatto sulle prestazioni di ogni variante è significativo o aumenta con l'applicazione di filtraggi più complessi, è possibile valutare un compromesso in base al miglioramento della qualità dell'immagine. In base alla valutazione, si potrebbe accettare un impatto aggiuntivo sulle prestazioni in cambio di un aumento della qualità visiva oppure si potrebbe decidere per una riduzione della qualità visiva in favore di un aumento di frequenza dei fotogrammi o del recupero di prestazioni, utilizzabili per altri scopi.  
  
 Se l'impatto sulle prestazioni è trascurabile o invariato a prescindere dalla modalità di filtraggio, ad esempio quando la GPU di destinazione presenta un'abbondanza di velocità di shader e di larghezza di banda di memoria, considerare l'uso del filtraggio anisotropo per ottenere la migliore qualità di immagine per l'applicazione.  
  
## <a name="remarks"></a>Note  
 Queste varianti eseguono l'override degli stati del campionatore nelle chiamate a `ID3D11DeviceContext::PSSetSamplers` in cui la modalità di filtraggio del campionatore fornita dall'applicazione è una delle seguenti:  
  
-   `D3D11_FILTER_MIN_MAG_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_MAG_POINT_MIP_LINEAR`  
  
-   `D3D11_FILTER_MIN_POINT_MAG_LINEAR_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_POINT_MAG_MIP_LINEAR`  
  
-   `D3D11_FILTER_MIN_LINEAR_MAG_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_LINEAR_MAG_POINT_MIP_LINEAR`  
  
-   `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`  
  
-   `D3D11_FILTER_MIN_MAG_MIP_LINEAR`  
  
-   `D3D11_FILTER_ANISOTROPIC`  
  
 Nel **filtraggio punti della trama** variant, la modalità di filtro forniti dall'applicazione viene sostituita con `D3D11_FILTER_MIN_MAG_MIP_POINT`, nel **bilineare della trama** variant, viene sostituito con `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`; e il **trilineare della trama** variant, viene sostituito con `D3D11_FILTER_MIN_MAG_MIP_LINEAR`.  
  
 Nel **anisotropo della trama** variant, la modalità di filtro forniti dall'applicazione viene sostituita con `D3D11_FILTER_ANISOTROPIC`, e il Max Anisotropy viene impostato su 16.  
  
## <a name="restrictions-and-limitations"></a>Limiti e restrizioni  
 In Direct3D la funzionalità di livello 9.1 specifica un'anisotropia massima di 2x. Poiché il **anisotropo della trama** variante tenta di usare l'anisotropia 16x in modo esclusivo, la riproduzione non riesce quando l'analisi dei frame viene eseguito in un dispositivo con funzionalità di livello 9.1. Tra i dispositivi contemporanei che sono interessati da questo limite ci sono i tablet Windows basati su ARM Surface RT e Surface 2. GPU più datate che potrebbero essere ancora presenti in alcuni computer possono anch'esse risultare interessate, ma si tratta di hardware generalmente considerato obsoleto e in rapida via di estinzione.  
  
## <a name="example"></a>Esempio  
 Il **filtraggio punti della trama** variante può essere riprodotta usando codice simile al seguente:  
  
```  
D3D11_SAMPLER_DESC sampler_description;  
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Esempio  
 Il **bilineare della trama** variante può essere riprodotta usando codice simile al seguente:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Esempio  
 Il **trilineare della trama** variante può essere riprodotta usando codice simile al seguente:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>Esempio  
 Il **anisotropo della trama** variante può essere riprodotta usando codice simile al seguente:  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_ANISOTROPIC;  
sampler_description.MaxAnisotropy = 16;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```