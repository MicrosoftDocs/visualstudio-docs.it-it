---
title: Modelli di interazione per Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 094e16fea46e459dd64338ffa5daf3f7b98afb90
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142432"
---
# <a name="interaction-patterns-for-visual-studio"></a>Modelli di interazione per Visual Studio
## <a name="overview"></a>Panoramica  
 Un modello di progettazione, in generale, è alla base di una progettazione che può essere applicata in situazioni specifiche per risolvere i problemi con set simili di vincoli. Finestre di progettazione di funzionalità e di sistema di usare questi modelli di progettazione come punti, che possono essere adattati per le esigenze di partenza.  
  
 Visual Studio è una libreria di modelli di interazione comune da considerare durante la creazione di nuove funzionalità. Esistono due contesti di base per i modelli di progettazione: Client (devenv) di Visual Studio e Visual Studio Online. Per alcuni problemi di progettazione, è disponibile un modello diffuso che funziona bene in tutte le situazioni. In molti casi, tuttavia, la soluzione potrebbe essere diversa per l'interfaccia utente che viene presentata all'interno di un browser e quello di cui è ospitato in un'applicazione client.  
  
### <a name="visual-studio-client-pattern-types"></a>Tipi di modello di Visual Studio Client  
  
|Tipo di modello|Descrizione|Esempi|  
|------------------|-----------------|--------------|  
|**Modelli a livello di applicazione**|Modelli di alto livello comuni all'applicazione, determinazione o la visualizzazione di contesto dell'applicazione e contenente composita e pattern di controllo all'interno di essi|: Le finestre degli strumenti<br />: Finestre di documento|  
|**Modelli compositi**|Modelli comuni che possono estendersi tra modelli di applicazione o un modello riconosciuto costituito da diversi controlli in una configurazione distinto|-Cambio vista<br />-Generatori list<br />-La visualizzazione dei dati<br />-Notifiche<br />-Convalida<br />-Modelli selezione|  
|**Pattern di controllo**|Le specifiche sulle modalità di basso livello controlli si prevede un comportamento|-Visualizzazioni dell'albero<br />-La modifica all'interno di un controllo griglia|  
  
## <a name="application-patterns"></a>Modelli di applicazione  
 In generale, l'interfaccia di Visual Studio è costituito da più finestre, finestre di dialogo, comandi e le barre degli strumenti all'interno di un singolo IDE. Gerarchia di Visual Studio determina i menu di contesto e le unità. I punti di integrazione principali nell'interfaccia utente dell'IDE sono finestre dei documenti, finestre degli strumenti, progetti, la struttura di comando, l'editor di testo, la casella degli strumenti, finestra proprietà e gli strumenti > Opzioni.  
  
 Sono disponibili modelli di utilizzo di base per ognuno dei punti di integrazione principali nell'interfaccia utente dell'IDE:  
  
-   [Menu e comandi per Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)  
  
-   [Modelli delle applicazioni per Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)  
  
    -   [Interazioni di finestra](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)  
  
    -   [Finestre degli strumenti](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)  
  
    -   [Convenzioni di editor](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)  
  
    -   [Dialogs](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) (Finestre di dialogo)  
  
    -   [Progetti](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)  
  
## <a name="common-control-patterns"></a>Pattern di controllo comune  
 Pattern di controllo sono principalmente sul modo in cui singoli controlli sono previsti un comportamento. Si tratta di un'area in cui la coerenza è critica.  
  
 Controlli più comuni in Visual Studio devono seguire le linee guida di Windows Desktop. Linee guida incluse solo le aree in cui è necessario aumentare le convenzioni comuni con le interazioni di specifiche di Visual Studio o posizioni in cui si sostituiscono le linee guida completamente per personalizzare Visual Studio per soddisfare le esigenze dei nostri utenti sofisticati.  
  
-   [Modelli dei controlli comuni per Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)  
  
    -   [Controlli comuni](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)  
  
    -   [Controlli testo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
    -   [I pulsanti e collegamenti ipertestuali](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
## <a name="composite-patterns"></a>Modelli compositi  
 Esistono diversi modi che gli utenti si aspettano per eseguire le attività. Laddove possibile, le funzionalità devono essere progettate per utilizzare tali modelli per l'interazione e di progettazione visiva.  
  
 In presenza di numerosi modelli composti all'interno di Visual Studio, alcuni dei più importanti per quanto riguarda la coerenza sono:  
  
-   [Modelli compositi per Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)  
  
    -   [Per gli oggetti dell'interfaccia utente e la lettura](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
    -   [Modelli di selezione](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
    -   [Persistenza e il salvataggio delle impostazioni](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
    -   [Input tocco](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)