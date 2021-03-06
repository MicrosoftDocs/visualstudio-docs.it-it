---
description: Questa funzione controlla se il plug-in del controllo del codice sorgente consente più estrazioni in un file.
title: Funzione SccIsMultiCheckoutEnabled | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccIsMultiCheckoutEnabled
helpviewer_keywords:
- SccIsMultiCheckoutEnabled function
ms.assetid: 6721639d-e475-4766-81b5-ee40a280fc70
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 648b68f1575e31e81b6f12ca09abcb8e7305a985
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220560"
---
# <a name="sccismulticheckoutenabled-function"></a>Funzione SccIsMultiCheckoutEnabled
Questa funzione controlla se il plug-in del controllo del codice sorgente consente più estrazioni in un file.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccIsMultiCheckoutEnabled(
   LPVOID pContext,
   LPBOOL pbMultiCheckout
);
```

#### <a name="parameters"></a>Parametri
 pContext

in Struttura del contesto del plug-in del controllo del codice sorgente.

 pbMultiCheckout

out Specifica se sono abilitate più estrazioni per questo progetto (valore diverso da zero indica che sono supportate più estrazioni).

## <a name="return-value"></a>Valore restituito
 Si prevede che l'implementazione del plug-in del controllo del codice sorgente di questa funzione restituisca uno dei valori seguenti:

|Valore|Descrizione|
|-----------|-----------------|
|SCC_OK|Il controllo è stato completato correttamente.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Errore non specifico.|

## <a name="remarks"></a>Commenti
 L'IDE esegue due controlli per determinare se i file possono essere estratti simultaneamente da più di un utente. In primo luogo, il sistema di controllo del codice sorgente deve supportare più estrazioni. Il plug-in del controllo del codice sorgente può specificare questa funzionalità durante l'inizializzazione specificando `SCC_CAP_MULTICHECKOUT` . Successivamente, come secondo controllo, l'IDE chiama questa funzione per determinare se il progetto corrente supporta più estrazioni. Se per il progetto selezionato sono supportate più estrazioni, il plug-in restituisce un codice di esito positivo e imposta `pbMultiCheckout` su un valore diverso da zero ( `TRUE` ) o `FALSE` .

## <a name="see-also"></a>Vedi anche
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)
