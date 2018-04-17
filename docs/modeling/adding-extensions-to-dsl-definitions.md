---
title: Aggiunta di estensioni a definizioni DSL | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: a689d902a58eb747cbaec0bf7cebd740ade3e9bf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="adding-extensions-to-dsl-definitions"></a>Aggiunta di estensioni alle definizioni DSL
Definizione DSL estensione consente di creare un pacchetto di estensioni da un linguaggio specifico di dominio (DSL). L'estensione del linguaggio DSL, incluso in Visual Studio Integration Extension (VSIX), può essere installato nel computer dell'utente nello stesso modo come un linguaggio DSL. Le funzionalità aggiuntive possono essere abilitate e disabilitate in fase di esecuzione in modo dinamico. DSL non deve essere progettato in modo esplicito per l'estensione e le estensioni possono essere progettate in un secondo momento o da terzi senza alterare il DSL estesa.  
  
 Le funzionalità aggiuntive possono includere quanto segue:  
  
-   Proprietà degli elementi di modello e la presentazione  
  
-   Elementi Decorator di forme e connettori  
  
-   Classi, le relazioni, forme e connettori  
  
-   Vincoli di convalida  
  
-   Schede e gli elementi della casella degli strumenti  
  
 Un utente di un'estesa DSL può creare e salvare un modello che contiene le istanze di funzionalità aggiuntive, e questi possono essere letti da altri utenti che hanno installato l'estensione appropriata. Gli utenti che non hanno installato l'estensione non è possibile utilizzare le funzionalità aggiuntive, ma possono aggiornare e salvare un modello senza perdere le funzionalità aggiuntive.  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Vedere anche  
 [Post di blog correlati](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
