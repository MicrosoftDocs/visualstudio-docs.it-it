---
title: "Proprietà delle forme di raggruppamento | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.compartmentshape
helpviewer_keywords:
- Domain-Specific Language, compartment shape
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: e87af6c7b95fc05ab7e018f4b9adeb0ea9708868
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="properties-of-compartment-shapes"></a>Proprietà delle forme di raggruppamento
Le forme di raggruppamento sono una delle forme che è possibile utilizzare per visualizzare una classe di dominio in un linguaggio specifico di dominio. È possibile espandere e comprimere i raggruppamenti.  
  
 Per ulteriori informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Forme di raggruppamento sono le proprietà elencate nella tabella seguente.  
  
|Proprietà|Descrizione|Impostazione predefinita|  
|--------------|-----------------|-------------|  
|Predefinito espandere lo stato di compressione|Se `Expanded`, vengono visualizzati i raggruppamenti al momento della creazione. Se `Collapsed`, non lo siano.|Espanso|  
|Colore riempimento|Il colore di riempimento della forma.|Vuoto|  
|Modalità di sfumatura riempimento|La modalità di sfumatura riempimento della forma.|Orizzontale|  
|Geometry|La geometria della forma (rettangolo o rettangolo con angoli arrotondati).|Rettangolo|  
|Dispone di punti di connessione predefinito|Se `True`, la forma utilizzerà superiore, inferiore, sinistro e destro connessione fa riferimento nella finestra di progettazione generato.|False|  
|È visibile solo compartimento intestazione|Se `False`e la forma presenta un singolo raggruppamento, l'intestazione di raggruppamento non è visibile.|True|  
|Colore del contorno|Colore del contorno della forma.|Nero|  
|Stile di tratteggio di struttura|Stile di tratteggio contorno della forma (solido, trattino, punto, Trattopunto, Trattopuntopunto, personalizzato).|Tinta unita|  
|Spessore del contorno|Spessore del contorno della forma.|0.03125|  
|Colore del testo|Colore utilizzato per gli elementi Decorator testo associati a questa forma.|Nero|  
|Modificatore di accesso|Il livello di accesso della forma raggruppamento (`public` o `internal`).|Public|  
|Attributi personalizzati|Consente di aggiungere attributi alla classe di codice sorgente generato da questa forma raggruppamento|\<Nessuno >|  
|Genera l'errore doppia derivato|Se `True`, verrà generate una classe di base sia una classe parziale (per supportare la personalizzazione tramite le sostituzioni). Per ulteriori informazioni, vedere [si esegue l'override ed estendere le classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Ha un costruttore personalizzato|Se `True`, verrà fornito un costruttore personalizzato nel codice sorgente. Per ulteriori informazioni, vedere [si esegue l'override ed estendere le classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generato dalla forma raggruppamento (`none`, `abstract` o `sealed`).|nessuno|  
|Forma raggruppamento di base|Classe di base di questa forma.|(nessuno)|  
|nome|Il nome della forma.|Nome corrente|  
|Spazio dei nomi|Lo spazio dei nomi che è associato a questa forma.|Spazio dei nomi corrente|  
|ToolTip (tipo)|Come descrizione comando viene definita (fisso, variabile o none). Se viene risolto, quindi il valore della `Fixed Tooltip Text` proprietà viene utilizzata come descrizione comando; se la variabile, la descrizione comandi è definita nel codice personalizzato.|none|  
|Note|Note informale che sono associate a questa forma.|\<Nessuno >|  
|Altezza iniziale|L'altezza iniziale di questa forma, espressa in pollici. Per le forme di raggruppamento, l'altezza della sezione dell'intestazione solo e non può essere ridimensionato.|1|  
|Larghezza iniziale|Larghezza iniziale della forma in pollici.|1,5|  
|Colore di riempimento esposto come proprietà<br /><br /> Modalità di sfumatura riempimento esposto<br /><br /> Colore del contorno di esposta come proprietà<br /><br /> Stile di tratteggio di struttura di esposta come proprietà<br /><br /> Esposte come proprietà spessore del contorno<br /><br /> Espone il colore del testo|Se `True`, l'utente può impostare la proprietà di una forma specificata. Per impostare questo, il pulsante destro la definizione della forma e fare clic su **aggiungere esposti**.|False|  
|Descrizione|Utilizzato per documentare la finestra di progettazione generato.|\<Nessuno >|  
|Nome visualizzato|Il nome che verrà visualizzato nella finestra di progettazione generato per questa forma.|\<Nessuno >|  
|Testo della descrizione comando fisso|Il testo che viene utilizzato per una descrizione di comandi predefinito.|\<Nessuno >|  
|Parola chiave della Guida|La parola chiave che viene utilizzata per l'indice della Guida F1 per questa forma.|\<Nessuno >|  
  
## <a name="see-also"></a>Vedere anche  
 [Glossario di strumenti di linguaggio specifico di dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)