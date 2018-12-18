---
title: 'Procedura: Creare tipi tramite Progettazione classi | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.Clr.ClrAttributesDialog
helpviewer_keywords:
- custom attributes, applying
- class diagrams, creating types
- classes [Visual Studio], creating with Class Designer
- Class Designer [Visual Studio], creating classes
- types [Visual Studio], class diagrams
- attributes [Visual Studio], applying custom
ms.assetid: 94458c31-28bc-40e2-9737-85868788a0e5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22260ee75a1c64de842da41b292fbeebeb6cf6ef
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-types-by-using-class-designer"></a>Procedura: creare tipi utilizzando Progettazione classi
Per progettare nuovi tipi per progetti C# e Visual Basic, crearli in un diagramma di classi. Per visualizzare i tipi esistenti, vedere [Procedura : Visualizzare i dati esistenti](how-to-view-existing-types.md).  
  
-   [Creare un nuovo tipo](#CreateType)  
  
-   [Applicare un attributo personalizzato a un tipo](#CustAttributeType)  
  
-   [Applicare un attributo personalizzato a un membro di un tipo](#CustAttributeMember)  
  
##  <a name="CreateType"></a>Creare un nuovo tipo  
  
1.  In Progettazione classi di Casella degli strumenti trascinare uno dei seguenti elementi in un diagramma di classi:  
  
    -   **Classe** o **Classe astratta**  
  
    -   **Enum**  
  
    -   **Interface**  
  
    -   **Struttura** (VB) o **Struct** (C#)  
  
    -   **Delegate**  
  
    -   **Modulo** (solo VB)  
  
2.  Assegnare un nome al tipo. Selezionare quindi il relativo livello di accesso.  
  
3.  Selezionare il file in cui si desidera aggiungere il codice iniziale per il tipo:  
  
    -   Per creare un nuovo file e aggiungerlo al progetto corrente, selezionare **Crea nuovo file** e assegnare un nome al file.  
  
    -   Per aggiungere codice a un file esistente, selezionare **Aggiungi a file esistente**.  
  
         Se la soluzione contiene un progetto che condivide il codice tra più app, è possibile aggiungere un nuovo tipo a un diagramma di classi nel progetto di app, ma solo se il file di classe corrispondente si trova nello stesso progetto di app o nel progetto condiviso.  
  
4.  Aggiungere ora altri elementi per definire il tipo:  
  
    |||  
    |-|-|  
    |**Per**|**Aggiungi**|  
    |Classi, classi astratte, strutture o struct|Metodi, proprietà, campi, eventi, costruttori (metodo), distruttori (metodo) e costanti che definiscono il tipo|  
    |Enumerazioni|Valori di campo che costituiscono l'enumerazione|  
    |Interfacce|Metodi, proprietà ed eventi che costituiscono l'interfaccia|  
    |delegato|Parametri che definiscono il delegato|  
    |Modulo|Metodi, proprietà, campi, eventi, costruttori (metodo), distruttori (metodo) e costanti che definiscono il modulo|  
  
     Vedere [Creazione di membri](creating-and-configuring-type-members.md#CreateMembers).  
  
##  <a name="CustAttributeType"></a> Applicare un attributo personalizzato a un tipo  
  
1.  Fare clic sulla forma del tipo in un diagramma classi.  
  
2.  Nella finestra Proprietà fare clic sul pulsante con i puntini di sospensione (...) accanto alla proprietà **Attributi personalizzati** relativa al tipo.  
  
3.  Aggiungere uno o più attributi personalizzati, uno per riga. Non racchiuderli tra parentesi.  
  
     Al termine, gli attributi personalizzati verranno applicati al tipo.  
  
##  <a name="CustAttributeMember"></a> Applicare un attributo personalizzato a un membro di un tipo  
  
1.  Fare clic sul nome del membro nella forma del relativo tipo in un diagramma classi oppure nella relativa riga nella finestra Dettagli classe.  
  
2.  Nella finestra Proprietà individuare la proprietà **Attributi personalizzati** del membro.  
  
3.  Aggiungere uno o più attributi personalizzati, uno per riga. Non racchiuderli tra parentesi.  
  
     Al termine, gli attributi personalizzati verranno applicati al tipo.  
  
## <a name="see-also"></a>Vedere anche
[Procedura: Creare ereditarietà tra tipi](how-to-create-inheritance-between-types.md)  
[Procedura: Creare associazioni tra tipi](how-to-create-associations-between-types.md)
[Creazione e configurazione di membri di tipi](creating-and-configuring-type-members.md)   
[Uso di diagrammi classi](working-with-class-diagrams.md)   
[Progettazione di classi e tipi](designing-classes-and-types.md)