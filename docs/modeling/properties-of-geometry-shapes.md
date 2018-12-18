---
title: Proprietà delle forme geometriche
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.dsltools.dsldesigner.geometryshape
helpviewer_keywords:
- Domain-Specific Language, geometry shape
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2e52e69c3b2a13d02e22c089af7f6ca6dffe28d9
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="properties-of-geometry-shapes"></a>Proprietà delle forme geometriche
Per specificare la modalità di visualizzazione delle istanze di classi di dominio in un linguaggio specifico di dominio, è possibile utilizzare forme geometriche. Per ulteriori informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

 Forme geometriche hanno le proprietà elencate nella tabella seguente.

|Proprietà|Descrizione|Impostazione predefinita|
|--------------|-----------------|-------------|
|Colore riempimento|Il colore di riempimento della forma.|Vuoto|
|Modalità di sfumatura riempimento|La modalità di sfumatura riempimento della forma (orizzontale, verticale, in avanti diagonale, diagonale con le versioni precedenti o None).|Orizzontale|
|Geometry|La geometria della forma (rettangolo, rettangolo arrotondato, ellisse o cerchio).|Rettangolo|
|Dispone di punti di connessione predefinito|Se `True`, la forma utilizzerà superiore, inferiore, sinistro e destro connessione fa riferimento nella finestra di progettazione generato.|False|
|Colore del contorno|Colore del contorno della forma.|Nero|
|Stile di tratteggio di struttura|Stile di tratteggio contorno della forma (solido, trattino, punto, Trattopunto, Trattopuntopunto o personalizzato).|Tinta unita|
|Spessore del contorno|Spessore del contorno della forma.|0.03125|
|Colore del testo|Colore utilizzato per gli elementi Decorator testo associati a questa forma.|Nero|
|Modificatore di accesso|Il modificatore di accesso della classe (interna o pubblica).|Public|
|Attributi personalizzati|Consente di aggiungere attributi alla classe di codice sorgente generato per questa forma.|\<Nessuno >|
|Genera l'errore doppia derivato|Se `True`, verrà generate una classe di base sia una classe parziale (per supportare la personalizzazione tramite le sostituzioni). Per ulteriori informazioni, vedere [si esegue l'override ed estendere le classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Ha un costruttore personalizzato|Se `True`, verrà fornito un costruttore personalizzato nel codice sorgente. Per ulteriori informazioni, vedere [si esegue l'override ed estendere le classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generato dalla forma (`none`, `abstract` o `sealed`).|none|
|Forma di base di geometria|Classe di base di questa forma.|(nessuno)|
|nome|Il nome della forma.|Nome corrente|
|Spazio dei nomi|Lo spazio dei nomi che è associato a questa forma.|Spazio dei nomi corrente|
|ToolTip (tipo)|Come descrizione comando viene definita (fisso, variabile o none). Se viene risolto, quindi il valore della `Fixed Tooltip Text` proprietà viene utilizzata come descrizione comando; se la variabile, la descrizione comandi è definita nel codice personalizzato.|Nessuno|
|Note|Note informale che sono associate a questo elemento.|\<Nessuno >|
|Altezza iniziale|Altezza iniziale di questa forma, espressa in pollici.|1|
|Larghezza iniziale|Larghezza iniziale della forma in pollici.|1,5|
|Colore di riempimento esposto come proprietà<br /><br /> Modalità di sfumatura riempimento esposto<br /><br /> Colore del contorno di esposta come proprietà<br /><br /> Stile di tratteggio di struttura di esposta come proprietà<br /><br /> Esposte come proprietà spessore del contorno<br /><br /> Espone il colore del testo|Se `True`, l'utente può impostare la proprietà di una forma specificata. Per impostare questo, il pulsante destro la definizione della forma e fare clic su **aggiungere esposti**.|False|
|Descrizione|La descrizione che viene utilizzata per la finestra di progettazione generato del documento.|\<Nessuno >|
|Nome visualizzato|Il nome che verrà visualizzato nella finestra di progettazione generato per questa forma.|\<Nessuno >|
|Testo della descrizione comando fisso|Il testo che viene utilizzato per una descrizione di comandi predefinito.|\<Nessuno >|
|Parola chiave della Guida|La parola chiave che viene utilizzata per l'indice della Guida F1 per questa forma.|\<Nessuno >|

## <a name="see-also"></a>Vedere anche

- [Glossario di strumenti di linguaggio specifico di dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)