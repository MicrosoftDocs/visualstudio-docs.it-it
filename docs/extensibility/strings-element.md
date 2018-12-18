---
title: Stringhe elemento | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Strings element (VSCT XML schema)
- VSCT XML schema elements, Strings
ms.assetid: 23a42074-a689-481d-824f-b43aa448f266
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c5994144f07b8af84f61d7833737f45593c551b2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="strings-element"></a>Elemento di stringhe
L'elemento di stringhe deve contenere almeno un **ButtonText** elemento figlio. Tutti gli altri elementi figlio sono facoltativi. I caratteri XML non valido, ad esempio '&' e ' <' devono essere codificati come entità ('&amp;'e'&lt;' e così via).  
  
 Una e commerciale nella stringa di testo specifica il tasto di scelta rapida per il comando.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Strings>  
  <ButtonText>... </ButtonText>  
  <CommandName>... </CommandName>  
</Strings>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|language|Facoltativo. Language = ".".|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|ButtonText|Questo campo e i cinque campi di testo seguente in una definizione di comando consentono di specificare il testo visualizzato in diversi menu. Per impostazione predefinita, il `ButtonText` campo viene visualizzato nel controller di menu. Il `ButtonText` campo viene inoltre impostato il valore predefinito se gli altri campi di testo sono vuoti. Il `ButtonText` campo non può essere vuoto, anche se sono specificati gli altri campi di testo.|  
|ToolTipText|Il `ToolTipText` campo specifica il testo visualizzato nella descrizione comando per una voce di menu.<br /><br /> Se il `ToolTipText` campo è vuoto, il `ButtonText` campo viene usato.|  
|MenuText|Il `MenuText` campo specifica il testo visualizzato per un comando se è presente nel menu principale, una barra degli strumenti in un menu di scelta rapida o in un sottomenu. Se il `MenuText` campo è vuoto, utilizza l'ambiente di sviluppo integrato (IDE) di `ButtonText` campo. Il `MenuText` campo può essere usato anche per la localizzazione.<br /><br /> Per i menu di scelta rapida, il `MenuText` campo è il nome visualizzato nella barra degli strumenti di menu di scelta rapida, che consente la personalizzazione di menu di scelta rapida nell'IDE. Pertanto, essere specifico in ciò che si assegna il nome del menu di scelta rapida. ad esempio, utilizzare "Menu di scelta rapida pacchetto Widget" anziché "Collegamento".<br /><br /> Se il `MenuText` campo non è specificato, il `ButtonText` campo viene usato.|  
|CommandName|Il `CommandName` campo specifica il testo visualizzato nella categoria tastiera di **comandi** nella scheda il **Personalizza** la finestra di dialogo (disponibile facendo clic **Personalizza**sul **strumenti** menu).|  
|canonicalName|La lingua inglese `CanonicalName` campo specifica il nome del comando nel testo in lingua inglese che può essere immesse nel **comando** finestra per eseguire la voce di menu. L'IDE consente di rimuovere i caratteri che non sono lettere, numeri, caratteri di sottolineatura o punti. Questo testo viene quindi concatenato per il `ButtonText` campo per definire il comando. Ad esempio, **nuovo progetto** sul **File** menu diventa il comando, il file. NewProject.<br /><br /> Se la lingua inglese `CanonicalName` campo non è specificato, l'IDE Usa il `ButtonText` campo e strisce tutte tranne lettere, cifre, caratteri di sottolineatura e punti. Ad esempio, il testo del pulsante "& definire comandi …" diventa DefineCommands, in cui vengono rimossi i puntini di sospensione, lo spazio e la e commerciale.<br /><br /> Se il `TextChanges` flag specificato e il testo del comando viene modificato, il comando corrispondente riconosciuto dal **comando** finestra non viene modificata; la forma canonica dell'originale rimane `ButtonText` o inglese `CanonicalName` campi.|  
|LocCanonicalName|Il `LocCanonicalName` campo si comporta come la lingua inglese `CanonicalName` campo ma consente di testo del comando localizzata specificare. È possibile specificare entrambi i campi canonici. Poiché l'IDE analizza solo il testo immesso nella **comando** finestra e lo associa con un comando, in inglese e il testo in lingua inglese non può essere associato lo stesso comando.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Button](../extensibility/button-element.md)|Definisce un elemento che l'utente può interagire con.|  
|[Elemento Menu](../extensibility/menu-element.md)|Definisce una singola voce di menu.|  
|[Elemento Combo](../extensibility/combo-element.md)|Definisce i comandi che vengono visualizzati in una casella combinata.|  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)