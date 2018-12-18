---
title: Panoramica degli strumenti di linguaggio specifico di dominio | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 89ff0565bf33936f15c18c0964fc9fb2f64ab9b8
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="overview-of-domain-specific-language-tools"></a>Informazioni generali sugli strumenti di linguaggio specifico di dominio
Strumenti di linguaggio specifico di dominio (strumenti DSL), che sono ospitati in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], consentono progettare un linguaggio specifico di dominio e quindi generare tutto ciò che gli utenti devono disporre per creare i modelli basati sulla lingua.  
  
 Gli strumenti seguenti sono inclusi in strumenti DSL:  
  
-   Creazione guidata progetto che utilizza modelli diversi di soluzioni che consentono di iniziare a sviluppare il linguaggio specifico di dominio.  
  
-   Finestra di progettazione grafica per la creazione e modifica la definizione di linguaggio specifico di dominio.  
  
-   Motore di convalida che consente di verifica che la definizione del linguaggio specifico di dominio sia ben formata e consente di visualizzare errori e avvisi se sono presenti problemi.  
  
-   Generatore di codice che accetta una definizione di linguaggio specifico di dominio come input e genera codice sorgente come output.  
  
## <a name="the-dsl-tools-solution"></a>La soluzione di strumenti DSL  
 La procedura guidata progettazione specifico di dominio fornisce i modelli di soluzioni seguenti:  
  
-   Flusso di attività  
  
-   Diagrammi classi  
  
-   Linguaggio minima  
  
-   Modelli di componente  
  
-   WPF minima  
  
-   Windows. Forms minima  
  
-   Libreria DSL  
  
 Per ulteriori informazioni, vedere [scelta di un modello di soluzione di linguaggio specifico di dominio](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
 La procedura guidata crea un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] soluzione che include i progetti seguenti:  
  
-   Dsl  
  
     Il progetto Dsl definisce il linguaggio specifico di dominio e dei relativi strumenti di modificare e di elaborazione.  
  
-   **DslPackage**  
  
     Il progetto DslPackage determina la modalità di integrare gli strumenti di linguaggio con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="the-dsl-tools-graphical-interface"></a>L'interfaccia grafica di strumenti DSL  
 Per aggiungere elementi e relazioni per il linguaggio specifico di dominio, è possibile utilizzare l'interfaccia grafica di strumenti DSL. Dopo aver aggiunto gli elementi, è possibile definire l'aspetto eseguendone il mapping alle forme, personalizzazione dei colori e aggiungendo gli elementi Decorator. È anche possibile aggiungere elementi alla casella degli strumenti.  
  
## <a name="validation-in-dsl-tools"></a>Convalida in strumenti DSL  
 DSL fornisce un livello di convalida per assicurarsi che il modello di dominio soddisfi i requisiti di base per la generazione di codice. In genere, quando si crea la propria linguaggio specifico di dominio, è possibile aggiungere convalida personalizzata per esprimere le regole di logica di business. Per ulteriori informazioni sulla convalida personalizzata, vedere [convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md).  
  
 È consigliabile convalidare il linguaggio specifico di dominio spesso quando si progettano. Se il linguaggio specifico di dominio è presenti errori di convalida, è possibile generare codice sorgente. Viene eseguito il processo di generazione di codice sorgente dai modelli facendo **Trasforma tutti i modelli** nella barra degli strumenti di Esplora soluzioni. Quando si modifica la definizione del linguaggio, assicurarsi anche di **Trasforma tutti i modelli**. Per ulteriori informazioni, vedere [procedura: creare una soluzione di linguaggio specifico di dominio](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="customization-of-dsl-tools"></a>Personalizzazione di strumenti DSL  
 È possibile fornire codice aggiuntivo per perfezionare il comportamento del modello e per definire i vincoli per la lingua. Se necessario, è possibile apportare modifiche significative modificando i modelli di testo.  
  
## <a name="distributing-your-dsl-solution"></a>Distribuzione della soluzione DSL  
 Strumenti DSL genera un pacchetto che è ospitato in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Il pacchetto consente di visualizzare una casella degli strumenti, una finestra di esplorazione DSL e altri elementi dell'interfaccia utente che consentono agli utenti di creare modelli utilizzando il linguaggio specifico di dominio.  
  
 Quando si compila e si esegue la soluzione di strumenti DSL in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], una seconda istanza di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene illustrato l'aspetto del linguaggio specifico di dominio per l'utente del linguaggio. Dopo aver verificato che tutto funzioni correttamente, è possibile distribuire il `.vsix` file che si trovano nella cartella di compilazione del progetto DslPackage. Questo file può essere utilizzato per installare del linguaggio DSL come un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estensione in altri computer.  Per ulteriori informazioni, vedere [soluzioni per la distribuzione di un linguaggio specifico di dominio](../modeling/deploying-domain-specific-language-solutions.md).  
  
## <a name="see-also"></a>Vedere anche  
 [L'istanza sperimentale](../extensibility/the-experimental-instance.md)   
 [Glossario di strumenti di linguaggio specifico di dominio](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)