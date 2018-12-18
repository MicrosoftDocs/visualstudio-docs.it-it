---
title: Definizione di forme e connettori | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: a1a1043515afb8d7567459e1adae23f1d4fcfde9
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="defining-shapes-and-connectors"></a>Definizione di forme e connettori
Per visualizzare le informazioni su un diagramma in un linguaggio specifico di dominio (DSL), sono disponibili numerosi tipi base di forme.  
  
##  <a name="shapeTypes"></a>Tipi di forme e connettori di base  
 Un diagramma DSL Mostra una raccolta di *forme* concatenati da linee o *connettori*.  In genere, ma non sempre:  
  
-   Le forme sono la rappresentazione visibile di elementi modello.  
  
-   I connettori rappresentano le relazioni di riferimento.  
  
-   Il diagramma rappresenta l'istanza radice del modello.  
  
-   Le relazioni di incorporamento tra elementi modello sono mostrate tramite il contenimento. Ad esempio, gli elementi che rappresentano le porte dei componenti sono incorporati nel componente.  
  
 Questi modelli non sono imposti ma sono fortemente supportati. Quando si progetta un DSL, tenere presente che la progettazione delle relazioni di incorporamento deve essere influenzata dal modo in cui si vuole presentare il modello sullo schermo. Al contrario, le relazioni di riferimento devono riflettere i concetti del dominio aziendale.  
  
 Sono disponibili i tipi di forme seguenti:  
  
|Tipo di forma|Descrizione|  
|----------------|-----------------|  
|Forma geometrica|Forma rettangolare o ellittica di utilizzo generale. È possibile visualizzare elementi Decorator testo e icona in posizioni specifiche relative ai contorni della forma.<br /><br /> Per nidificare le forme all'interno delle forme di geometria, vedere [nidificazione forme](../modeling/nesting-shapes.md).|  
|Forma Raggruppamento|Rettangolo contenente un'intestazione e raggruppamenti, come una classe UML. Ogni raggruppamento può contenere un elenco di righe di testo.<br /><br /> Le righe in genere rappresentano gli elementi incorporati nell'elemento rappresentato dalla forma. Per un esempio, creare un DSL dal modello di soluzione Diagramma classi.|  
|Forma immagine|Forma che visualizza un'immagine.|  
|Forma della porta|Un piccolo rettangolo progettato per essere collegato al contorno di un'altra forma. Usato in genere nei modelli di componenti.<br /><br /> L'elemento del modello rappresentato da una porta è in genere incorporato nell'elemento rappresentato dalla forma padre. Per un esempio, creare un DSL dal modello di soluzione Componenti.<br /><br /> Per impostazione predefinita, una forma della porta può scorrere lungo i lati del relativo elemento padre. È possibile definire una regola con dei limiti per vincolarla in una posizione specifica.<br /><br /> Se si crea una forma della porta molto piccola e trasparente, è possibile usarla per fornire un punto di connessione fisso sulla superficie della forma padre.|  
|Corsie|Le corsie sono una partizione orizzontale o verticale di un diagramma. Le corsia rimane sempre sotto le altre forme nel diagramma.<br /><br /> In genere, gli elementi modello della corsia sono associati a un elemento padre nel modello radice e gli altri elementi sono associati agli elementi padre dei primi. Per un esempio, creare un DSL dal modello di soluzione Flusso attività.|  
|Connettori|Le linee tracciate tra le forme rappresentano in genere relazioni di riferimento. Sono disponibili opzioni per impostare un connettore come diritto o rettilineo e con diversi tipi di punta della freccia.|  
  
##  <a name="shapeInheritance"></a>Ereditarietà di forma  
 Una forma può ereditare da un'altra forma. Tuttavia, è necessario che le forme siano dello stesso tipo. Ad esempio, solo una forma geometrica può ereditare da una forma geometrica. Le forme ereditate mantengono i raggruppamenti e gli elementi Decorator della relativa forma di base. I connettori possono invece ereditare dai connettori.