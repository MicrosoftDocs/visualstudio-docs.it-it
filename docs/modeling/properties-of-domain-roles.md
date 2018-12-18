---
title: Proprietà dei ruoli di dominio
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: ead7128c998b8c4ed97acac0f6da0f08113e7bef
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="properties-of-domain-roles"></a>Proprietà dei ruoli di dominio
Le proprietà nella tabella seguente sono associate a un ruolo di dominio. Per informazioni sui ruoli di dominio, vedere [informazioni sui modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Proprietà|Descrizione|Impostazione predefinita|
|--------------|-----------------|-------------|
|Tipo di raccolta|Se questo ruolo dispone di molteplicità 0... * o 1... \*, questa proprietà consente di personalizzare il tipo generico che viene utilizzato per memorizzare la raccolta dei collegamenti.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> viene utilizzato|
|Attributi personalizzati|Verranno aggiunti attributi che è possibile specificare come attributi alla classe il codice generato.|< none\>|
|È possibile esplorare proprietà|Se `True`, e se la molteplicità della relazione è 0..1 1 o 1, la proprietà del ruolo può essere visualizzata dall'utente nel **proprietà** finestra. La proprietà consente di visualizzare il nome dell'elemento a altra estremità del collegamento della relazione.|`True`|
|Generatore di proprietà|Se `True`, viene generata una proprietà di ruolo per questo ruolo, che consente di attraversare la relazione nel codice programma. Se si imposta questo false, è possibile attraversare la relazione in modo meno efficiente utilizzando metodi statici della relazione di dominio.|`True`|
|Modificatore di accesso get di proprietà|Il modificatore di accesso per il metodo Get della proprietà generato (`public`, `internal`, `private`, `protected`, o `protected internal`).|`public`|
|Modificatore di accesso Setter di proprietà|Il modificatore di accesso per il metodo di impostazione per la proprietà generata (`public`, `internal`, `private`, `protected`, o `protected internal`).|`public`|
|Multiplicity|Il numero di elementi del modello che svolge il ruolo opposto (`0..1`, `1..1`, `0..*`, o `1..*`). Se la molteplicità è `0..*` o `1..*`, quindi la proprietà generata rappresenta una raccolta; in caso contrario, la proprietà generata rappresenta un elemento singolo modello.|Dipende dal tipo di relazione e se questo è il ruolo di origine o di destinazione nella relazione.|
|nome|Il nome del ruolo del dominio. Questa proprietà non può contenere spazi vuoti.|Il nome della classe di dominio dell'assegnatario di ruolo per questo ruolo.|
|Propaga copia|`DoNotPropagateCopy` -L'assegnatario di ruolo copiato non avrà alcuna copia di questo collegamento.<br /><br /> `PropagateCopyToLinkOnly` -I punti di collegamento copiato opposto assegnatario di ruolo esistente.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` -Il collegamento copiato punta a una copia dell'assegnatario di ruolo opposto.|`PropagateCopyToLinkAndOppositeRolePlayer` per i ruoli di origine degli incorporamenti.<br /><br /> `DoNotPropagateCopy` per altri ruoli.<br /><br /> Per ulteriori informazioni, vedere [personalizzare il comportamento di copia](../modeling/customizing-copy-behavior.md)|
|Propaga l'eliminazione|`True` Per eliminare l'elemento che svolge il ruolo quando viene eliminato il collegamento associato.|`True` per la destinazione di un ruolo di incorporamento.<br /><br /> `False` per altri ruoli.<br /><br /> Per ulteriori informazioni, vedere [personalizzare comportamento di eliminazione](../modeling/customizing-deletion-behavior.md).|
|Nome proprietà|Il nome della proprietà generate nel codice dell'assegnatario di ruolo. Questo nome non può contenere spazi vuoti.|Il nome del ruolo opposto se questo ruolo dispone di un zero-a-uno o una molteplicità uno a uno; in caso contrario, il nome del ruolo opposto pluralized.|
|Assegnatario di ruolo|La classe dell'elemento in grado di riprodurre questo ruolo nella relazione di dominio. Questa proprietà è di sola lettura.|La classe di dominio dell'assegnatario di ruolo per questo ruolo.|
|Note|Note informale che sono associate al ruolo di dominio.|< none\>|
|Category|La categoria in cui la proprietà generata viene visualizzata nel **proprietà** finestra di progettazione generata. Se questa proprietà è vuota, quindi la proprietà generata viene visualizzato sotto il **varie** categoria|< none\>|
|Descrizione|La descrizione che viene utilizzata per documentare il codice e viene utilizzata nell'interfaccia utente della finestra di progettazione generato.<br /><br /> La descrizione viene visualizzata nella descrizione comando IntelliSense per la proprietà generata nella classe assegnatario di ruolo.|`Description for` *il nome completo del ruolo*|
|Nome visualizzato|Il nome viene visualizzato nella finestra di progettazione generato per il ruolo di dominio.|Valore della proprietà nome modificato.|
|Parola chiave della Guida|La parola chiave facoltativa che viene utilizzata per indicizzare F1 Guida in linea per il ruolo di dominio.|\<Nessuno >|
|Nome visualizzazione proprietà|Il nome viene visualizzato nella finestra di progettazione generato per la proprietà del ruolo generato.|Valore della proprietà nome della proprietà modificato.|

> [!NOTE]
> Il valore predefinito di un nome visualizzato è basato sul valore della proprietà associata tramite l'inserimento di spazi prima di ogni carattere maiuscolo, che è preceduto da un carattere minuscolo e che non è seguito da un altro carattere maiuscolo.

## <a name="see-also"></a>Vedere anche

- [Proprietà delle relazioni di dominio](../modeling/properties-of-domain-relationships.md)