---
title: "Estensione delle proprietà | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 26cf161259736dbd2b2e26279842571d62f69352
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/22/2018
---
# <a name="extending-properties"></a>Estensione delle proprietà
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **proprietà** finestra è un visualizzatore di proprietà universale per i componenti COM e COM+ e supporta tutte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prodotti. Il **proprietà** finestra funziona con `ITypeInfo` digitare le informazioni e i metadati di COM+ per elencare le proprietà in fase di progettazione per l'oggetto attualmente selezionato in un'altra finestra nell'ambiente di sviluppo integrato (IDE).  
  
 Il **proprietà** finestra, che può essere aperta, premere F4 sulla tastiera, oppure selezionando **finestra proprietà** sul **vista** menu, viene utilizzato per visualizzare e modificare proprietà in fase di progettazione indipendenti dalla configurazione e gli eventi degli oggetti selezionati. Proprietà dipendenti dalla configurazione, associata a soluzioni e progetti, vengono visualizzate in [pagine delle proprietà](../../extensibility/internals/property-pages.md). Per ulteriori informazioni, [la gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md).  
  
 ![Panoramica della finestra proprietà](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Finestra Proprietà  
  
 In questa sezione vengono fornite informazioni dettagliate relative alle singole aree del **proprietà** finestra e le interfacce che è necessario implementare e chiamare per popolare la finestra.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Panoramica della finestra Proprietà](../../extensibility/internals/properties-window-overview.md)  
 Viene illustrato lo scopo del **proprietà** finestra rispetto alla finestra degli strumenti e finestra del documento.  
  
 [Criteri dei modelli e finestra Proprietà](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Viene illustrato come un progetto è contenuto in un progetto di modello dell'organizzazione e come tale progetto di modello dell'organizzazione possa applicare i criteri.  
  
 [Campi e interfacce della finestra Proprietà](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Illustra la base per la selezione che determina quali informazioni vengono visualizzate nel **proprietà** finestra.  
  
 [Elenco di oggetti della finestra Proprietà](../../extensibility/internals/properties-window-object-list.md)  
 Viene descritto lo scopo del **proprietà** elenco di oggetti finestra, che descrive la modalità, quando un oggetto diverso da questo elenco è attiva una chiamata, l'ambiente viene informato che è stato selezionato un nuovo oggetto.  
  
 [Pulsanti della finestra Proprietà](../../extensibility/internals/properties-window-buttons.md)  
 Viene illustrato lo scopo dei pulsanti quattro predefinito visualizzati nella **proprietà** degli strumenti della finestra.  
  
 [Griglia di visualizzazione delle proprietà](../../extensibility/internals/properties-display-grid.md)  
 Viene illustrato dove i campi di valori di proprietà e i nomi delle proprietà presenti nella griglia.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Vengono illustrati i progetti come i blocchi predefiniti del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Compiling and Building](../../ide/compiling-and-building-in-visual-studio.md) (Compilazione e creazione)  
 Descrive come è possibile utilizzare il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] piattaforma per il test e debug di applicazioni durante la compilazione.  
  
 [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)  
 Viene descritto il `IDispatch` interfaccia, che è stato progettato inizialmente per supportare l'automazione, fornendo un meccanismo di associazione tardiva per recuperare le informazioni sui metodi e proprietà di un oggetto.  
  
 [Gestione delle impostazioni dell'applicazione (.NET)](../../ide/managing-application-settings-dotnet.md)  
 Viene fornita una panoramica delle impostazioni dell'applicazione che consentono di configurare l'applicazione in modo che i valori delle proprietà vengono archiviati in un file di configurazione esterno anziché il codice dell'applicazione compilata.  
  
 [Solutions and Projects](../../ide/solutions-and-projects-in-visual-studio.md) (Soluzioni e progetti)  
 Viene illustrato come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestisce in modo efficiente gli elementi, ad esempio i riferimenti, le connessioni dati, cartelle e file necessari allo sviluppo tramite soluzioni e progetti.  
  
 [Estensione di altre parti di Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Viene illustrato come utilizzare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] services per creare elementi dell'interfaccia utente che corrispondano al resto del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].