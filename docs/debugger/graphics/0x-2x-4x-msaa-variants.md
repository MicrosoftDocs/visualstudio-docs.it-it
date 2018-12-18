---
title: Varianti di MSAA x-4 x-2 0 | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 77e4d199fe0c0ae1d876eae62014e6aaabd6f643
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="0x2x4x-msaa-variants"></a>Varianti di MSAA 0x/2x/4x
Eseguono l'override dell'anti-aliasing multicampione (MSAA, Multi-Sample Anti-Aliasing) in tutte le destinazioni di rendering e catene di scambio.  
  
## <a name="interpretation"></a>Interpretazione  
 L'anti-aliasing multicampione aumenta la qualità visiva ottenendo campioni da più aree in ogni pixel. Livelli più elevati di MSAA consentono l'acquisizione di un numero maggiore di campioni, mentre senza MSAA viene acquisito un solo campione dal centro del pixel. L'abilitazione di MSAA in una singola app comporta in genere un impatto contenuto ma percepibile sulle prestazioni di rendering, tuttavia in determinate condizioni di carico di lavoro o su certe GPU tale impatto può risultare quasi azzerato.  
  
 Se la propria app ha già MSAA abilitato, varianti minori del livello di MSAA indicheranno l'impatto relativo sulle prestazioni determinato dal livello esistente, più elevato, di MSAA. La variante 0x MSAA in particolare, indica le prestazioni relative dell'app in assenza di MSAA.  
  
 Se l'app non ha ancora MSAA abilitato, le varianti 2x MSAA e 4x MSAA indicano l'impatto relativo sulle prestazioni qualora venissero abilitate nell'app. Quando il livello di impatto è accettabile, considerare l'abilitazione di MSAA per migliorare la qualità di immagine dell'app.  
  
> [!NOTE]
>  L'hardware potrebbe non supportare completamente MSAA per tutti i formati. Se una di queste varianti dovesse incorrere in un limite hardware che non è possibile aggirare, la relativa colonna nella tabella di riepilogo delle prestazioni resterà vuota e verrà visualizzato un messaggio di errore.  
  
## <a name="remarks"></a>Note  
 Queste varianti eseguono l'override degli argomenti relativi conteggio e alla qualità dei campioni nelle chiamate a `ID3DDevice::CreateTexture2D` che creano destinazioni di rendering. In particolare, tali parametri vengono sottoposti a override nei casi seguenti:  
  
-   L'oggetto `D3D11_TEXTURE2D_DESC` passato in `pDesc` descrive una destinazione di rendering, ossia:  
  
    -   Il membro BindFlags presenta il flag D3D11_BIND_TARGET o il flag D3D11_BIND_DEPTH_STENCIL impostato.  
  
    -   Il membro Usage è impostato su D3D11_USAGE_DEFAULT.  
  
    -   Il membro CPUAccessFlags è impostato su 0.  
  
    -   Il membro MipLevels è impostato su 1.  
  
-   Il dispositivo supporta il conteggio dei campioni (0, 2 o 4) e la qualità degli stessi (0) necessari per il formato della destinazione di rendering richiesta (membro D3D11_TEXTURE2D_DESC::Format), così come determinato da `ID3D11Device::CheckMultisampleQualityLevels`.  
  
 Se il membro D3D11_TEXTURE2D_DESC::BindFlags ha il flag D3D_BIND_SHADER_RESOUCE o D3D11_BIND_UNORDERED_ACCESS impostato, vengono create due versioni della trama: la prima con tre flag deselezionati per l'uso come destinazione di rendering, mentre l'altra è una trama non MSAA che presenta i flag intatti in modo da agire come buffer di risoluzione per la prima versione. Ciò è necessario perché l'uso di una trama MSAA come risorsa shader o per l'accesso non ordinato difficilmente sarà valido. Uno shader che agisce su di essa genererebbe ad esempio risultati non corretti perché si prevederebbe una trama non MSAA. Se la variante ha creato la trama secondaria non MSAA, quando la destinazione di rendering MSAA viene annullata dal contesto del dispositivo, il relativo contenuto viene risolto nella trama non MSAA. Analogamente, quando la destinazione di rendering MSAA si trova impegnata come risorsa condivisa o viene usata in una visualizzazione con accesso non ordinato, verrà associata la trama non MSAA risolta.  
  
 Queste varianti eseguono anche l'override delle impostazioni MSAA su tutte le catene di scambio create tramite `IDXGIFactory::CreateSwapChain`, `IDXGIFactory2::CreateSwapChainForHwnd`, `IDXGIFactory2::CreateSwapChainForCoreWindow`, `IDXGIFactory2::CreateSwapChainForComposition` e `ID3D11CreateDeviceAndSwapChain`.  
  
 L'effetto finale di queste modifiche è che tutto il rendering viene eseguito in una destinazione di rendering MSAA, ma, se l'applicazione usa una di tali destinazioni di rendering, o buffer della catena di scambio, come visualizzazione di risorse shader o visualizzazione con accesso non ordinato, i dati verranno campionati dalla copia risolta, non MSAA, della destinazione di rendering.  
  
## <a name="restrictions-and-limitations"></a>Limiti e restrizioni  
 In Direct3D11, le trame MSAA sono soggette a maggiori restrizioni rispetto alle trame non MSAA. Non è ad esempio possibile chiamare `ID3D11DeviceContext::UpdateSubresource` su una trama MSAA e la chiamata a `ID3D11DeviceContext::CopySubresourceRegion` non riuscirà se il conteggio e la qualità dei campioni delle risorse di origine e di destinazione non coincidono, situazione che può prodursi quando questa variante esegue l'override delle impostazioni MSAA di una risorsa ma non dell'altra.  
  
 Quando la riproduzione rileva questi tipi di conflitti, viene fatto il possibile per replicare il comportamento atteso, ma potrebbe non essere possibile raggiungere una corrispondenza esatta dei risultati. Sebbene raramente ciò influisca sulle prestazioni di queste varianti in modo tale da rappresentarne l'impatto in modo erroneo, ciò può verificarsi, ad esempio, quando il controllo di flusso in un pixel shader viene determinato dal contenuto preciso di una trama, perché la trama replicata potrebbe non avere un contenuto identico.  
  
## <a name="example"></a>Esempio  
 Queste varianti possono essere riprodotte per destinazioni di rendering create tramite `ID3D11Device::CreateTexture2D` usando codice simile al seguente:  
  
```  
D3D11_TEXTURE2D_DESC target_description;  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead  
target_description.SampleDesc.Quality = 0;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```  
  
## <a name="example"></a>Esempio  
 Per catene di scambio create tramite IDXGISwapChain::CreateSwapChain or D3D11CreateDeviceAndSwapChain il codice sarebbe simile al seguente:  
  
```  
DXGI_SWAP_CHAIN_DESC chain_description;  
chain_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead  
chain_description.SampleDesc.Quality = 0;  
  
// Call IDXGISwapChain::CreateSwapChain or D3D11CreateDeviceAndSwapChain, etc.  
```