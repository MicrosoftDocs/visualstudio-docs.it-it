---
title: "Proprietà delle corsie | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.swimlane
helpviewer_keywords:
- Domain-Specific Language, swimlane
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 39bb6be4146cf7e9e163b6da5ada6f447a930bc8
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="properties-of-swimlanes"></a>Proprietà delle corsie
È possibile aggiungere le corsie a un diagramma. Le corsie dividono un diagramma in aree verticale o orizzontale. È possibile definire altre forme da visualizzare all'interno delle corsie. Per ulteriori informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Le corsie hanno le proprietà elencate nella tabella seguente.  
  
|Proprietà|Descrizione|Impostazione predefinita|  
|--------------|-----------------|-------------|  
|Colore di riempimento del corpo|Il colore di riempimento per il corpo della corsia.|Vuoto|  
|Colore di riempimento di intestazione|Il colore di riempimento per l'intestazione della corsia.|DarkGray|  
|Colore separatore|Il colore della linea di separazione.|LightGray|  
|Stile di linea di separazione|Lo stile della linea di separazione (`Solid`, `Dash`, `Dot`, `DashDot`, `DashDotDot`, o `Custom`).|`Dash`|  
|Spessore separatore|Lo spessore della linea di separazione in pollici.|0.03125|  
|Colore del testo|Colore utilizzato per gli elementi Decorator testo associati a questa corsia.|Nero|  
|Modificatore di accesso|Il livello di accesso della classe (`public` o `internal`).|Public|  
|Attributi personalizzati|Consente di aggiungere attributi alla classe di codice che viene generata da questa corsia.|\<Nessuno >|  
|Genera l'errore doppia derivato|Se `True`, verrà generate una classe di base sia una classe parziale (per supportare la personalizzazione tramite le sostituzioni). Per ulteriori informazioni, vedere [si esegue l'override ed estendere le classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Ha un costruttore personalizzato|Se `True`, verrà fornito un costruttore personalizzato nel codice sorgente. Per ulteriori informazioni, vedere [si esegue l'override ed estendere le classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di origine di codice che viene generata dalla corsia (`none`, `abstract` o `sealed`).|none|  
|Base corsia|Classe di base di questa corsia.|(nessuno)|  
|nome|Il nome di questa corsia.|Nome corrente|  
|Spazio dei nomi|Lo spazio dei nomi che è associato a questa corsia.|Spazio dei nomi corrente|  
|ToolTip (tipo)|La modalità in cui è definita la descrizione comando (`fixed`, `variable`, o `none`). Se `fixed`, quindi il valore di `Fixed Tooltip Text` proprietà viene utilizzata; se `variable`, quindi la descrizione comandi è definita nel codice personalizzato.|\<Nessuno >|  
|Note|Note informale che sono associate a questa corsia.|\<Nessuno >|  
|Allineamento|Allineamento orizzontale o verticale.|Vertical|  
|Altezza iniziale|L'altezza iniziale di questa corsia, espressa in pollici. Applicabile solo per le corsie orizzontali.|0|  
|Larghezza iniziale|Larghezza iniziale di questa corsia, espressa in pollici. Applicabile solo per le corsie verticale.|0|  
|Espone il colore del testo|Se `True`, l'utente può impostare il colore di una corsia nella finestra di progettazione generato. Per impostare questo, la forma di corsie destro e fare clic su **aggiungere esposti**.|False|  
|Descrizione|Utilizzato per documentare la finestra di progettazione generato.|\<Nessuno >|  
|Nome visualizzato|Il nome che verrà visualizzato nella finestra di progettazione generato per fare riferimento a questa classe corsia.|\<Nessuno >|  
|Testo della descrizione comando fisso|Il testo che viene utilizzato per una descrizione di comandi predefinito.|\<Nessuno >|  
|Parola chiave della Guida|La parola chiave che viene utilizzata per l'indice della Guida F1 per questa corsia.|\<Nessuno >|  
  
## <a name="see-also"></a>Vedere anche  
 [Glossario di strumenti di linguaggio specifico di dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)