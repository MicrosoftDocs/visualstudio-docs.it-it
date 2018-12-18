---
title: Proprietà delle relazioni di dominio
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 32943d7e40f7ce1a86ab2236862404686a4d922f
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="properties-of-domain-relationships"></a>Proprietà delle relazioni di dominio
Le proprietà nella tabella seguente sono associate a una relazione di dominio. Per informazioni sulle relazioni di dominio, vedere [informazioni sui modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Proprietà|Descrizione|Impostazione predefinita|
|--------------|-----------------|-------------|
|Modificatore di accesso|Il livello di accesso della relazione di dominio (`public` o `internal`).|`public`|
|Attributi personalizzati|Consente di aggiungere attributi alla classe di codice sorgente generato dalla relazione di dominio.|\<Nessuno >|
|Genera l'errore doppia derivato|Se `True`, viene generata una classe di base sia una classe parziale (per supportare la personalizzazione tramite le sostituzioni). Per ulteriori informazioni, vedere [si esegue l'override ed estendere le classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Ha un costruttore personalizzato|Se `True`, indica che viene fornito un costruttore personalizzato nel codice sorgente. Per ulteriori informazioni, vedere [si esegue l'override ed estendere le classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generato dalla relazione di dominio (`none`, `abstract` o `sealed`).|\<Nessuno >|
|Consente di duplicati|Se `True`, possibile creare tra gli stessi elementi di due collegamenti duplicati della relazione di dominio.|`False`|
|Relazioni di base|Se la relazione di dominio è derivata, la relazione di base della relazione di dominio.|\<Nessuno >|
|È l'incorporamento|Se `True`, la relazione di dominio è una relazione di incorporamento. Se `False`, la relazione è una relazione di riferimento.|\<entrambi >|
|nome|Il nome della relazione di dominio.|Nome corrente|
|Spazio dei nomi|Lo spazio dei nomi che è associato con la relazione di dominio.|Spazio dei nomi corrente|
|Note|Note informale associati con la relazione di dominio.|\<Nessuno >|
|Descrizione|La descrizione che viene utilizzata per documentare il codice e viene utilizzata nell'interfaccia utente della finestra di progettazione generato.|\<Nessuno >|
|Nome visualizzato|Il nome viene visualizzato nella finestra di progettazione generato per la relazione di dominio.|\<Nessuno >|
|Parola chiave della Guida|La parola chiave facoltativa che viene utilizzata per l'indice della Guida F1 per la relazione di dominio.|\<Nessuno >|

## <a name="see-also"></a>Vedere anche

- [Glossario di strumenti di linguaggio specifico di dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)