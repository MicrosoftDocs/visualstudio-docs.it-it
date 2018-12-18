---
title: Panoramica del linguaggio specifico di dominio di strumenti di interfaccia utente | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 24aad9d934b044ea42a3ad5319c2a10234ca94ef
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Informazioni sull'interfaccia utente degli strumenti di linguaggio specifico di dominio
Quando si apre una soluzione di strumenti del linguaggio specifico di dominio (strumenti DSL) in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], l'interfaccia utente sarà simili a quello nell'immagine seguente.  
  
 ![Progettazione DSL](../modeling/media/dsl_designer.png "dsl_designer")  
  
 Nella tabella seguente viene illustrato l'utilizzo delle parti dell'interfaccia utente.  
  
|**Elemento**|**Definizione**|  
|-----------------|--------------------|  
|Diagramma|Il diagramma consente di visualizzare il modello di dominio.<br /><br /> Il diagramma ha due lati. Lato "uno" definisce i tipi degli elementi dei modelli. L'altro lato definisce come i modelli verranno visualizzati sullo schermo.|  
|Casella degli strumenti|Trascinare gli strumenti dalla casella degli strumenti per aggiungere le classi di dominio e definire i tipi al diagramma. Per aggiungere le relazioni, i connettori e mappe delle forme, fare clic sullo strumento, quindi fare clic sul nodo di origine nel diagramma, quindi scegliere il nodo di destinazione.|  
|Esplora DSL|**Esplora DSL** viene visualizzato quando una definizione DSL è la finestra attiva. Mostra come una struttura ad albero del linguaggio DSL. Esplora DSL consente di modificare le funzionalità del modello che non vengono visualizzate nel diagramma. Ad esempio, è possibile aggiungere elementi della casella degli strumenti e sul processo di convalida utilizzando il **Esplora DSL**.|  
|Finestra Dettagli DSL|Il **dettagli DSL** finestra Visualizza proprietà del dominio per gli elementi del modello che consentono di controllare la modalità di visualizzazione degli elementi e come gli elementi vengono copiati ed eliminati.<br /><br /> -Per impostazione predefinita, il **dettagli DSL** accanto a verrà visualizzata la finestra di **elenco errori** e **Output** windows.|  
  
## <a name="the-domain-model-diagram"></a>Il diagramma del modello di dominio  
 Il diagramma del modello di dominio è suddivisa in due parti. Un lato del diagramma mostra gli elementi e relazioni nel modello. L'altro lato viene illustrato il modello da visualizzare e include le forme che consentono di visualizzare gli elementi e le proprietà del diagramma del modello. La figura seguente illustra gli elementi del diagramma.  
  
 ![Progettazione DSL con corsia](../modeling/media/dsl_desinger.png "dsl_desinger")  
  
 Nella tabella seguente illustra alcuni degli elementi del diagramma del modello di dominio.  
  
|**Termine**|**Definizione**|  
|--------------|--------------------|  
|Classe di dominio|Classi di dominio sono i tipi di elementi nei modelli.<br /><br /> Una classe di dominio può essere presente più di una volta in un diagramma, se si tratta della destinazione di più di una relazione.<br /><br /> Per aggiungere una classe di dominio, trascinare lo strumento di classe di dominio dal **della casella degli strumenti** per il **classi e relazioni** lato del diagramma.|  
|Relazione di dominio|Le relazioni di dominio sono i tipi di collegamenti tra gli elementi dei modelli.<br /><br /> Un *relazione di incorporamento* indica che l'elemento di destinazione è di proprietà o contenuto nell'elemento di origine e viene visualizzato come una linea continua. Ogni elemento in un modello deve essere la destinazione di una relazione di incorporamento, in modo che il modello di form di una struttura ad albero. Oggetto *relazione di riferimento* indica un collegamento tra gli elementi del modello generale e viene visualizzato come una linea tratteggiata. Qualsiasi elemento può avere qualsiasi numero di collegamenti di riferimento.<br /><br /> Creare una relazione facendo clic sullo strumento di **della casella degli strumenti**, la classe di dominio di origine, scegliere la classe di destinazione.|  
|Forme e connettori|Forme specificano come gli elementi del modello devono essere visualizzati in un diagramma DSL., i connettori di specificare le righe in un diagramma DSL che può essere usato per visualizzare le relazioni.<br /><br /> Per creare un connettore o una forma, trascinare lo strumento per la **elementi del diagramma** lato del diagramma.|  
|Mappe delle forme|Una mappa di forme viene visualizzato come una riga nel diagramma del modello di dominio, collegamento di una forma per la classe di dominio che vengono visualizzati, o di un connettore per la relazione di dominio che vengono visualizzati.|  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica degli strumenti di linguaggio specifico di dominio](../modeling/overview-of-domain-specific-language-tools.md)   
 [Glossario di strumenti di linguaggio specifico di dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)   
 [Personalizzazione ed estensione di un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md)