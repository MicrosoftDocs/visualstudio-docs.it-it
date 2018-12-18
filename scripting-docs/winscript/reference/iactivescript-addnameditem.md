---
title: IActiveScript::AddNamedItem | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.AddNamedItem
apilocation: scrobj.dll
helpviewer_keywords: AddNamedItem method, IActiveScript interface
ms.assetid: a7c6317d-948f-4bb3-b169-1bbe5b7c7cc5
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db65361e4bde14e803d9085a4530a505ccaf9fcb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
Aggiunge il nome di un elemento di livello radice per lo spazio dei nomi del motore di script. Un elemento di livello radice è un oggetto con proprietà e metodi, un'origine evento o tutti e tre.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrName`  
 [in] Indirizzo di un buffer che contiene il nome dell'elemento visualizzato dallo script. Il nome deve essere univoco e persistente.  
  
 `dwFlags`  
 [in] Flag associato a un elemento. Può essere una combinazione dei valori seguenti:  
  
|Valore|Significato|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|Indica che l'elemento denominato rappresenta un oggetto solo codice e che l'host non ha alcun `IUnknown` da associare a questo oggetto solo codice. L'host ha solo un nome per questo oggetto. In linguaggi orientati ad esempio C++, questo flag creerà una classe. Non tutti i linguaggi supportano questo flag.|  
|SCRIPTITEM_GLOBALMEMBERS|Indica che l'elemento è una raccolta di proprietà globali e metodi associati lo script. In genere, un motore di script potrebbe ignorare il nome dell'oggetto (diverso da quello allo scopo di utilizzarlo come un cookie per il [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) metodo, o per la risoluzione dell'ambito esplicita) ed esporre i relativi membri come globale le variabili e metodi. Questo consente all'host ampliare la libreria (le funzioni di runtime e così via) disponibile per lo script. Viene rimosso al motore di script per gestire con il nome è in conflitto (ad esempio, quando due elementi SCRIPTITEM_GLOBALMEMBERS dispongono di metodi con lo stesso nome), anche se non deve essere restituito un errore a causa di questa situazione.|  
|SCRIPTITEM_ISPERSISTENT|Indica che l'elemento deve essere salvato se il motore di script viene salvato. Analogamente, l'impostazione di questo flag indica che una transizione allo stato inizializzato deve mantenere le informazioni di nome e il tipo dell'elemento (il motore di script deve, tuttavia, rilasciare tutti i puntatori alle interfacce per l'oggetto effettivo).|  
|SCRIPTITEM_ISSOURCE|Indica che l'elemento genera eventi che possa includere lo script. Gli oggetti figlio (proprietà dell'oggetto di per sé oggetti) possono anche origine eventi per lo script. Questo non è ricorsiva, ma fornisce un meccanismo efficace per il caso comune, ad esempio, di creazione di un contenitore e tutti i relativi membri controlli.|  
|SCRIPTITEM_ISVISIBLE|Indica che il nome dell'elemento è disponibile nello spazio dei nomi dello script, consentendo l'accesso alle proprietà, metodi ed eventi dell'elemento. Per convenzione le proprietà dell'elemento includono elementi figlio dell'elemento; Pertanto, tutte le proprietà di oggetto figlio e i metodi (e i relativi elementi figlio, in modo ricorsivo) saranno accessibili.|  
|SCRIPTITEM_NOCODE|Indica che l'elemento è semplicemente un nome da aggiungere allo spazio dei nomi dello script e non deve essere considerato un elemento per il quale codice deve essere associato. Ad esempio, se questo flag viene impostato, VBScript creerà un modulo separato per l'elemento denominato e C++ potrebbe creare una classe wrapper separato per l'elemento denominato.|  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_INVALIDARG`|Un argomento non valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di script non è ancora caricato o inizializzato).|  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)