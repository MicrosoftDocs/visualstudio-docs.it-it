---
title: Condivisione di classi tra DSL utilizzando una libreria DSL | Documenti Microsoft
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
ms.openlocfilehash: a58726bdc4e6e139963ae8cca2d12f26e0696246
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="sharing-classes-between-dsls-by-using-a-dsl-library"></a>Condivisione di classi tra DSL utilizzando una libreria DSL
Nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK, è possibile creare una definizione DSL incompleta che è possibile importare in un altro linguaggio DSL. Ciò consente di suddividere le parti comuni di modelli simili.  
  
## <a name="creating-and-using-dsl-libraries"></a>Creazione e utilizzo di librerie di DSL  
  
#### <a name="to-create-a-dsl-library"></a>Per creare una libreria di DSL  
  
1.  Creare un nuovo progetto DSL e scegliere il modello di soluzione DSL libreria.  
  
     Verrà creato un singolo progetto DSL con un modello vuoto.  
  
2.  È possibile aggiungere classi di dominio, relazioni, forme e così via.  
  
     Gli elementi nella raccolta non sono in modo da formare una singola struttura di incorporamento.  
  
     Per definire una relazione che è possibile utilizzare l'utilità di importazione, creare due classi di dominio e creare la relazione tra di essi.  
  
     Impostare il **modificatore di ereditarietà** delle classi di dominio per `Abstract`.  
  
3.  È possibile aggiungere gli elementi definiti in Esplora DSL, ad esempio i generatori di connessione.  
  
4.  È possibile aggiungere personalizzazioni che richiedono codice aggiuntivo, ad esempio i vincoli di convalida.  
  
5.  Fare clic su **Trasforma tutti i modelli**.  
  
6.  Compilare il progetto.  
  
7.  Quando si distribuisce il DSL per altri utenti possano utilizzare, è necessario specificare sia l'assembly compilato (DLL) e il file `DslDefinition.dsl`. È possibile trovare l'assembly compilato in una cartella`Dsl\bin\*`  
  
#### <a name="to-import-a-dsl-library"></a>Per importare una libreria di DSL  
  
1.  In un'altra definizione DSL, in **Esplora DSL**, la classe radice della DSL destro e quindi fare clic su **Aggiungi nuova importazione DslLibrary**.  
  
2.  Nella finestra Proprietà impostare il **percorso del File** della libreria. È possibile utilizzare un percorso assoluto o relativo.  
  
     La libreria importata viene visualizzato in Esplora DSL, in modalità di sola lettura.  
  
3.  È possibile utilizzare le classi importate come classi di base. Creare una classe di dominio nella DSL l'importazione e nella proprietà finestra, impostare **di una classe Base** a una classe importata.  
  
4.  Fare clic su Trasforma tutti i modelli.  
  
5.  Aggiungere al progetto DSL un riferimento all'assembly (DLL) che è stato compilato il progetto di libreria DSL.  
  
6.  Compilare la soluzione.  
  
 Una libreria DSL è possibile importare altre librerie. Quando si importa una libreria, in Esplora DSL vengono visualizzati automaticamente anche le importazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
