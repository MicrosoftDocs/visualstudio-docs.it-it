---
title: Errori di runtime JavaScript | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT-32725
- VS.WebClient.Help.SCRIPT7002
- VS.WebClient.Help.SCRIPT1001
- VS.WebClient.Help.SCRIPT16389
- VS.WebClient.HelpSCRIPT50
- VS.WebClient.HelpSCRIPT70
- VS.WebClient.HelpSCRIPT87
- VS.WebClient.HelpSCRIPT65535
- VS.WebClient.HelpSCRIPT445
- VS.WebClient.HelpSCRIPT600
- VS.WebClient.HelpSCRIPT2343
- VS.WebClient.HelpSCRIPT122
- VS.WebClient.HelpSCRIPT28
- VS.WebClient.HelpSCRIPT16386
- VS.WebClient.HelpSCRIPT7015
- VS.WebClient.HelpSCRIPT3
- VS.WebClient.HelpSCRIPT16388
- VS.WebClient.HelpSCRIPT14
- VS.WebClient.HelpSCRIPT12030
- VS.WebClient.HelpSCRIPT12029
- VS.WebClient.HelpSCRIPT1001
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- errors [JavaScript]
- run-time errors, JavaScript
ms.assetid: c111469d-8f31-4bde-9d46-16d58775db7d
caps.latest.revision: "20"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb75c59fae32911c3dd3a7468439a198d7191755
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="javascript-run-time-errors"></a>Errori di runtime JavaScript
Gli errori di run-time[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] si verificano quando lo script tenta di eseguire un'azione che il sistema non supporta. Gli errori di run-time si verificano durante la valutazione delle espressioni variabili o l'allocazione della memoria.  
  
## <a name="windows-runtime-errors"></a>Errori di Windows Runtime  
 Se si usano API di Windows Runtime nell'app [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] , vengono visualizzati errori JavaScript convertiti da HRESULT di Windows Runtime. I valori di HRESULT di Windows Runtime nell'intervallo superiore a 0x80070000 vengono convertiti in errori JavaScript prendendo il valore esadecimale dei bit inferiori e convertendolo in decimale. Ad esempio, HRESULT 0x80070032 viene convertito nel valore decimale 50 e viene prodotto l'errore JavaScript SCRIPT50. HRESULT 0x80074005 viene convertito nel valore decimale 16389 e viene prodotto l'errore JavaScript SCRIPT16389.  
  
## <a name="errors"></a>Errori  
  
|Numero errore|Descrizione|  
|------------------|-----------------|  
|5|[Accesso negato](../../javascript/misc/access-is-denied.md)|  
|438|[L'oggetto non supporta questa proprietà o metodo](../../javascript/misc/object-doesn-t-support-this-property-or-method.md)|  
|1001|Memoria insufficiente|  
|5029|[La lunghezza della matrice deve essere pari a un valore integer positivo finito](../../javascript/misc/array-length-must-be-a-finite-positive-integer.md)|  
|5030|[Alla lunghezza della matrice deve essere assegnato un numero positivo finito](../../javascript/misc/array-length-must-be-assigned-a-finite-positive-number.md)|  
|5028|[Previsto oggetto Array o Arguments](../../javascript/misc/array-or-arguments-object-expected.md)|  
|5010|[Previsto Boolean](../../javascript/misc/boolean-expected.md)|  
|5003|[Assegnazione a un risultato di funzione non consentita](../../javascript/misc/cannot-assign-to-a-function-result.md)|  
|5000|[Assegnazione a 'this' non consentita](../../javascript/misc/cannot-assign-to-this.md)|  
|5034|[Riferimento circolare nell'argomento Value non supportato](../../javascript/misc/circular-reference-in-value-argument-not-supported.md)|  
|5006|[Previsto oggetto date](../../javascript/misc/date-object-expected.md)|  
|5015|[Previsto oggetto Enumerator](../../javascript/misc/enumerator-object-expected.md)|  
|5022|[Eccezione generata e non rilevata](../../javascript/misc/exception-thrown-and-not-caught.md)|  
|5020|[Previsto ')' nell'espressione regolare](../../javascript/misc/expected-right-parenthesis-in-regular-expression-javascript.md)|  
|5019|[Previsto ' &#93;' nell'espressione regolare](../../javascript/misc/expected-right-square-bracket-in-regular-expression-javascript.md)|  
|5023|[La funzione non ha un oggetto Prototype valido](../../javascript/misc/function-does-not-have-a-valid-prototype-object.md)|  
|5002|[Prevista funzione](../../javascript/misc/function-expected.md)|  
|5008|[Assegnazione non valida](../../javascript/misc/illegal-assignment-javascript.md)|  
|5021|[Intervallo non valido nel set di caratteri](../../javascript/misc/invalid-range-in-character-set-javascript.md)|  
|5035|[Argomento Replacer non valido](../../javascript/misc/invalid-replacer-argument.md)|  
|5014|[Previsto oggetto JavaScript](../../javascript/misc/javascript-object-expected.md)|  
|5001|[Previsto numero](../../javascript/misc/number-expected.md)|  
|5007|[Previsto oggetto](../../javascript/misc/object-expected.md)|  
|5012|[Previsto membro dell'oggetto](../../javascript/misc/object-member-expected.md)|  
|5016|[Previsto oggetto Regular Expression](../../javascript/misc/regular-expression-object-expected.md)|  
|5005|[Prevista stringa](../../javascript/misc/string-expected.md)|  
|5017|[Errore di sintassi nell'espressione regolare](../../javascript/misc/syntax-error-in-regular-expression-javascript.md)|  
|5026|[Il numero delle cifre frazionarie non è compreso nell'intervallo](../../javascript/misc/the-number-of-fractional-digits-is-out-of-range.md)|  
|5027|[La precisione non è compresa nell'intervallo](../../javascript/misc/the-precision-is-out-of-range.md)|  
|5025|[La codifica usata per l'URI da decodificare non è valida](../../javascript/misc/the-uri-to-be-decoded-is-not-a-valid-encoding.md)|  
|5024|[L'URI da codificare contiene un carattere non valido](../../javascript/misc/the-uri-to-be-encoded-contains-an-invalid-character.md)|  
|5009|[Identificatore non definito](../../javascript/misc/undefined-identifier.md)|  
|5018|[Quantificatore imprevisto](../../javascript/misc/unexpected-quantifier-javascript.md)|  
|5013|[Previsto VBArray](../../javascript/misc/vbarray-expected.md)|  
  
## <a name="see-also"></a>Vedere anche  
 [Errori di sintassi JavaScript](../../javascript/reference/javascript-syntax-errors.md)