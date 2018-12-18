---
title: SDK di modellazione per Visual Studio (linguaggi specifici di dominio)
ms.date: 11/04/2016
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 922419a1c0b973f704fdd16273b780e6136aebc2
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>SDK di modellazione per Visual Studio (linguaggi specifici di dominio)
Tramite il SDK di modellazione per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], è possibile creare strumenti di sviluppo basato su modello avanzato che consente di integrare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Analogamente, è possibile creare una o più definizioni di modello e integrarle in un set di strumenti.

 MSDK è basato sulla definizione di un modello creato per rappresentare i concetti nella propria area aziendale. È possibile integrare il modello con vari strumenti, ad esempio una visualizzazione basata su diagramma, la possibilità di generare codice e altri elementi, comandi per trasformare il modello e la possibilità di interagire con il codice e altri oggetti in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Quando si sviluppa il modello, è possibile combinarlo con altri modelli e strumenti per formare un potente set di strumenti avanzati incentrati sulla propria attività di sviluppo.

 MSDK consente di compilare rapidamente un modello nel formato di linguaggio specifico di dominio (DSL). Iniziare utilizzando un editor specifico per definire uno schema o una sintassi astratta insieme a una notazione grafica. Utilizzando questa definizione, VMSDK genera:

-   Implementazione di modello con un'API fortemente tipizzata eseguita in un archivio basato sulle transazioni.

-   Finestra di esplorazione ad albero.

-   Editor grafico in cui gli utenti possono visualizzare il modello o parti definite.

-   Metodi di serializzazione che salvano i modelli in XML leggibile.

-   Funzionalità per generare codice di programma e altri elementi utilizzando il modello di testo.

 Tutte queste funzionalità possono essere personalizzate ed estese. Le estensioni sono integrate in modo che sia comunque possibile aggiornare la definizione DSL e rigenerare le funzionalità senza perdere le estensioni.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

 [Post di blog correlati](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)

 Per informazioni aggiuntive sulla tecniche avanzate e risoluzione dei problemi, visitare [forum di Visual Studio DSL & estensibilità degli strumenti di modellazione](http://go.microsoft.com/fwlink/?LinkID=186074).

## <a name="in-this-section"></a>In questa sezione
 [Introduzione ai linguaggi specifici del dominio](../modeling/getting-started-with-domain-specific-languages.md)

 [Informazioni su modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md)

 [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)

 [Personalizzazione ed estensione di un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md)

 [Convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md)

 [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)

 [Generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md)

 [Informazioni sul codice DSL](../modeling/understanding-the-dsl-code.md)

 [Personalizzazione dell'archiviazione dei file e della serializzazione XML](../modeling/customizing-file-storage-and-xml-serialization.md)

 [Distribuzione di soluzioni per un linguaggio specifico di dominio](../modeling/deploying-domain-specific-language-solutions.md)

 [Creazione di un linguaggio specifico di dominio basato su Windows Form](../modeling/creating-a-windows-forms-based-domain-specific-language.md)

 [Creazione di un linguaggio specifico di dominio basato su WPF](../modeling/creating-a-wpf-based-domain-specific-language.md)

 [Procedura: Estendere la finestra di progettazione di linguaggio specifico di dominio](../modeling/how-to-extend-the-domain-specific-language-designer.md)

 [Edizioni di Visual Studio supportate per l'SDK di visualizzazione e modellazione](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md)

 [Procedura: Eseguire la migrazione di un linguaggio specifico di dominio a una nuova versione](../modeling/how-to-migrate-a-domain-specific-language-to-a-new-version.md)

 [Riferimento API per SDK di modellazione per Visual Studio](../modeling/api-reference-for-modeling-sdk-for-visual-studio.md)
