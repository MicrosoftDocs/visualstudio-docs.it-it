---
title: "Proprietà dei connettori | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, connectors
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 858ce6fd3d53cd580a2aaac1b6b5c160dffac517
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="properties-of-connectors"></a>Proprietà dei connettori
Connettori rappresentano le relazioni di dominio in una finestra di progettazione generato.  
  
 Per ulteriori informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 I connettori sono le proprietà elencate nella tabella seguente.  
  
|Proprietà|Descrizione|Impostazione predefinita|  
|--------------|-----------------|-------------|  
|Colore|Il colore di questo connettore.|Nero|  
|Stile tratteggio|Lo stile di tratteggio per la riga per il connettore (solido, trattino, punto, Trattopunto, Trattopuntopunto o personalizzato).|Tinta unita|  
|Stile estremità di origine|Lo stile di fine di origine per questo connettore (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond o None).|nessuno|  
|Stile estremità di destinazione|Lo stile di fine della destinazione per questo connettore (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond o None).|nessuno|  
|Colore del testo|Colore utilizzato per gli elementi Decorator testo associati a questo connettore.|Nero|  
|Thickness|Lo spessore della linea per questo connettore, misurata in pollici.|0.03125|  
|Modificatore di accesso|Il livello di accesso della classe (`public` o `internal`).|Public|  
|Attributi personalizzati|Consente di aggiungere attributi alla classe di codice sorgente generato da questo connettore.|\<Nessuno >|  
|Genera l'errore doppia derivato|Se `True`, verrà generate una classe di base sia una classe parziale (per supportare la personalizzazione tramite le sostituzioni). Per ulteriori informazioni, vedere [si esegue l'override ed estendere le classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Ha un costruttore personalizzato|Se `True`, verrà fornito un costruttore personalizzato nel codice sorgente. Per ulteriori informazioni, vedere [si esegue l'override ed estendere le classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generato dal connettore (`none`, `abstract` o `sealed`).|none|  
|Connettore di base|Classe di base di questo connettore.|(nessuno)|  
|nome|Il nome di questo connettore.|Nome corrente|  
|Spazio dei nomi|Lo spazio dei nomi che è associato a questo connettore.|Spazio dei nomi corrente|  
|ToolTip (tipo)|Come descrizione comando viene definita (fisso, variabile o none). Se viene risolto, quindi il valore della `Fixed Tooltip Text` proprietà viene utilizzata come descrizione comando; se la variabile, la descrizione comandi è definita nel codice personalizzato.|\<Nessuno >|  
|Note|Note informale che sono associate a questo connettore.|\<Nessuno >|  
|Stile di routing|Stile utilizzato per il connettore di routing. Oggetto `Rectilinear` connettore rende attiva ad angolo retto come richiesto; un `Straight` non connettore.|Rettilineo|  
|Colore esposto come proprietà<br /><br /> Stile di tratteggio esposto come proprietà<br /><br /> Spessore esposto come proprietà<br /><br /> Espone il colore del testo|Se `True`, l'utente può impostare la proprietà di una forma specificata. Per impostare questo, il pulsante destro la definizione della forma e fare clic su **aggiungere esposti**.|False|  
|Descrizione|Utilizzato per documentare la finestra di progettazione generato.|\<Nessuno >|  
|Nome visualizzato|Il nome che verrà visualizzato nella finestra di progettazione generato per questo connettore.|\<Nessuno >|  
|Testo della descrizione comando fisso|Il testo che viene utilizzato per una descrizione di comandi predefinito.|\<Nessuno >|  
|Parola chiave della Guida|La parola chiave che viene utilizzata per l'indice della Guida F1 per questo elemento.|\<Nessuno >|  
  
## <a name="see-also"></a>Vedere anche  
 [Glossario di strumenti di linguaggio specifico di dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)