---
title: Scelta di un modello di soluzione per un linguaggio specifico di dominio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 6ec2d2210912011e09e439f25ecaa0e21ab6e918
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Scelta di un modello di soluzione per un linguaggio specifico di dominio
Per creare una soluzione di linguaggio specifico di dominio, scegliere uno dei modelli di soluzioni che sono disponibili nella finestra di progettazione guidata linguaggio specifico di dominio. Scegliendo il modello che rispecchia maggiormente la lingua che si desidera creare, è possibile ridurre al minimo le modifiche che è necessario apportare alla soluzione inizia.

 I seguenti modelli di soluzione sono disponibili nella finestra di progettazione guidata linguaggio specifico di dominio.

|Modello|Funzionalità|Descrizione|
|--------------|--------------|-----------------|
|Diagrammi classi|-Forme raggruppamento<br />: Ereditarietà della classe<br />-Ereditarietà della relazione<br />-Ereditarietà forma<br />-Proprietà relazione|Se il linguaggio specifico di dominio include entità e relazioni che dispongono di proprietà, utilizzare questo modello di soluzione. Questo modello consente di creare un linguaggio specifico di dominio che è simile a diagrammi classi UML. Le entità principali sono le classi e interfacce, insieme alle relazioni di generalizzazione, associazione e l'implementazione. Una classe o interfaccia viene visualizzato come una casella che contiene un elenco di attributi.|
|Diagrammi componente|-Le porte|Utilizzare questo modello di soluzione se il linguaggio specifico di dominio include i componenti, ovvero parti di un sistema software. Questo modello consente di creare un linguaggio specifico di dominio che è simile a diagrammi dei componenti UML. Le entità principali sono i componenti e le porte, che vengono visualizzate come forme di piccole dimensioni all'esterno dei componenti.|
|Diagrammi di flusso attività|-Immagini e forme di geometria<br />-   *Corsie*|Se il linguaggio specifico di dominio include i flussi di lavoro, stati o le sequenze, utilizzare questo modello di soluzione. Questo modello consente di creare un linguaggio specifico di dominio che è simile a diagrammi di attività UML. L'entità principale è un'attività e la relazione principale è una transizione tra le attività. Il modello include diversi altri elementi, ad esempio allo stato di avvio, lo stato finale e una barra di sincronizzazione.|
|Linguaggio minima|-Una classe e la forma<br />-Una relazione e connettore|Utilizzare questo modello di soluzione se il linguaggio specifico di dominio non sono simili agli altri modelli. Questo modello consente di creare un linguaggio specifico di dominio che dispone di due classi e una relazione, che sono rappresentati nel **della casella degli strumenti** come **casella** e **riga**. La classe e la relazione di disporre di una proprietà di stringa di esempio.|
|Minimo Progettazione Windows Form|-Un modello di piccole dimensioni.<br />-Un Windows Form che consente di visualizzare il modello.|Utilizzare questo modello se si desidera compilare un'applicazione in cui un linguaggio DSL è associato a un Windows Form, anziché una finestra di progettazione grafica.<br /><br /> Il modulo che funge da interfaccia utente per la lingua sia nella cartella Dsl\UI.<br /><br /> Compilare il progetto prima di aprire la finestra di progettazione del form.<br /><br /> Per ulteriori informazioni, vedere [la creazione di un linguaggio specifico di dominio Windows Forms-Based](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|Minimo di WPF Designer|-Un modello di piccole dimensioni<br />-Un'interfaccia utente di Windows Presentation Foundation che consente di visualizzare il modello|Utilizzare questo modello se si desidera compilare un'applicazione in cui un linguaggio DSL è associato a un'interfaccia utente WPF, anziché una finestra di progettazione grafica.<br /><br /> La finestra di progettazione per l'interfaccia utente si trova nella cartella Dsl\UI.<br /><br /> Compilare il progetto prima di aprire la finestra di progettazione dell'interfaccia utente.<br /><br /> Per ulteriori informazioni, vedere [la creazione di un linguaggio specifico di dominio WPF-Based](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|Libreria DSL|-Una libreria minima|Utilizzare questo modello se si desidera creare una definizione parziale di DSL che può essere importata in altre definizioni DSL.|

## <a name="see-also"></a>Vedere anche

- [Panoramica degli strumenti di linguaggio specifico di dominio](../modeling/overview-of-domain-specific-language-tools.md)
