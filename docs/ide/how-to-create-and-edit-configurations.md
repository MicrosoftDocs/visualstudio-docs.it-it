---
title: 'Procedura: Creare e modificare le configurazioni | Microsoft Docs'
ms.custom: 
ms.date: 06/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solution build configurations, editing
- build configurations, creating
- solution build configurations, creating
- build configurations, editing
- builds [Visual Studio], setting up
- property pages
- Configuration Manager
- project build configurations, creating
- project build configurations, editing
ms.assetid: 19be121c-148e-4ece-bbfc-d20b08cfc3f7
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7ca6dfe8132603b06b9bd08655eaff3861e4700d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-and-edit-configurations"></a>Procedura: creare e modificare le configurazioni
Per una soluzione è possibile creare diverse configurazioni della build. È possibile, ad esempio, configurare una compilazione di debug che i tester possono usare per trovare e correggere problemi. È anche possibile configurare tipi diversi di compilazioni da distribuire a clienti diversi.  

 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  

## <a name="creating-build-configurations"></a>Creazione di configurazioni della build  
 È possibile usare la finestra di dialogo **Configuration Manager** per selezionare o modificare le configurazioni della build esistenti oppure per crearne di nuove.  

#### <a name="to-open-the-configuration-manager-dialog-box"></a>Per aprire la finestra di dialogo Configuration Manager  

-   In **Esplora soluzioni** aprire il menu di scelta rapida per la soluzione e quindi scegliere **Configuration Manager**.  

    > [!NOTE]
    >  Se il comando **Configuration Manager** non viene visualizzato nel menu di scelta rapida, cercare il menu **Compilazione** nella barra dei menu. Se neanche questo viene visualizzato, sulla barra dei menu scegliere **Strumenti**, **Opzioni**e quindi nel riquadro sinistro della finestra di dialogo **Opzioni** espandere **Progetti e soluzioni**, **Generale**e nel riquadro di destra selezionare la casella di controllo **Mostra configurazioni della build avanzate**.  

     Nella finestra di dialogo **Configuration Manager** è possibile usare l'elenco a discesa **Configurazione soluzione attiva** per selezionare una configurazione della build, modificarne una esistente o crearne una nuova. È possibile usare l'elenco a discesa **Piattaforma soluzione attiva** per selezionare la piattaforma di destinazione della configurazione, modificarne una esistente oppure aggiungerne una nuova. Il riquadro **Contesti progetto** elenca i progetti all'interno della soluzione. Per ogni progetto è possibile selezionare una configurazione e una piattaforma specifiche per il progetto, modificarne alcune esistenti o crearne di nuove. Per ogni progetto è anche disponibile una casella di controllo che è possibile selezionare per includere il progetto quando si usa la configurazione a livello di soluzione per compilare o distribuire la soluzione stessa.  

 Dopo avere definito le configurazioni volute, è possibile impostare le proprietà di progetto appropriate per tali configurazioni.  

#### <a name="to-set-properties-based-on-configurations"></a>Per impostare le proprietà in base alle configurazioni  

-   In **Esplora soluzioni** aprire il menu di scelta rapida per un progetto e quindi scegliere **Proprietà**.  

     Verrà aperta la finestra **Pagine delle proprietà**.  

     È possibile impostare alcune proprietà per le configurazioni. Per una configurazione di rilascio, ad esempio, è possibile specificare che quando si effettua la compilazione della soluzione il codice deve essere ottimizzato. Per una configurazione di debug, poi, è possibile specificare che il simbolo di compilazione condizionale `DEBUG` deve essere incluso. Per altre informazioni sulle impostazioni della pagina delle proprietà, vedere [Gestione delle proprietà di progetti e soluzioni](../ide/managing-project-and-solution-properties.md).  

## <a name="creating-and-modifying-project-configurations"></a>Creazione e modifica di configurazioni di progetto  

#### <a name="to-create-a-project-configuration"></a>Per creare una configurazione di progetto  

1.  Aprire la finestra di dialogo **Gestione configurazione**.  

2.  Selezionare un progetto nella colonna **Progetto**.  

3.  Nell'elenco a discesa **Configurazione** per il progetto scegliere **Nuovo**.  

     Si aprirà la finestra di dialogo **Nuova configurazione progetto**.  

4.  Nella casella **Nome** immettere un nome per la nuova configurazione.  

5.  Per usare le impostazioni delle proprietà di una configurazione di progetto esistente, scegliere una configurazione nell'elenco a discesa **Copia impostazioni da**.  

6.  Per creare contemporaneamente una configurazione a livello di soluzione, selezionare la casella di controllo **Crea nuove configurazioni soluzione**.  

#### <a name="to-rename-a-project-configuration"></a>Per rinominare una configurazione di progetto  

1.  Aprire la finestra di dialogo **Gestione configurazione**.  

2.  Nella colonna **Progetto** selezionare il progetto con la configurazione che si vuole rinominare.  

3.  Nell'elenco a discesa **Configurazione** per il progetto scegliere **Modifica**.  

     Si aprirà la finestra di dialogo **Modifica configurazioni progetto**.  

4.  Selezionare il nome della configurazione di progetto che si vuole modificare.  

5.  Selezionare **Rinomina** e quindi immettere un nuovo nome.  

## <a name="creating-and-modifying-solution-wide-build-configurations"></a>Creare e modificare configurazioni della build a livello di soluzione  

#### <a name="to-create-a-solution-wide-build-configuration"></a>Per creare una configurazione della build a livello di soluzione  

1.  Aprire la finestra di dialogo **Gestione configurazione**.  

2.  Nell'elenco a discesa **Configurazione soluzione attiva** scegliere **Nuovo**.  

     Si aprirà la finestra di dialogo **Nuova configurazione soluzione**.  

3.  Nella casella di testo **Nome** immettere un nome per la nuova configurazione.  

4.  Per usare le impostazioni di una configurazione della soluzione esistente, scegliere una configurazione nell'elenco a discesa **Copia impostazioni da**.  

5.  Se contemporaneamente si vogliono creare configurazioni di progetto, selezionare la casella di controllo **Crea nuove configurazioni progetto**.  

#### <a name="to-rename-a-solution-wide-build-configuration"></a>Per rinominare una configurazione della build a livello di soluzione  

1.  Aprire la finestra di dialogo **Gestione configurazione**.  

2.  Nell'elenco a discesa **Configurazione soluzione attiva** scegliere **Modifica**.  

     Si aprirà la finestra di dialogo **Modifica configurazioni soluzione**.  

3.  Selezionare il nome della configurazione di soluzione che si vuole modificare.  

4.  Selezionare **Rinomina** e quindi immettere un nuovo nome.  

#### <a name="to-modify-a-solution-wide-build-configuration"></a>Per modificare una configurazione della build a livello di soluzione  

1.  Aprire la finestra di dialogo **Gestione configurazione**.  

2.  Nell'elenco a discesa **Configurazione soluzione attiva** selezionare la configurazione voluta.  

3.  Nel riquadro **Contesti progetto** per ogni progetto selezionare la **Configurazione** e la **Piattaforma** volute. Selezionare quindi se eseguire la **compilazione** e la **distribuzione**.  

## <a name="see-also"></a>Vedere anche  
 [Understanding Build Configurations](../ide/understanding-build-configurations.md)  (Informazioni sulle configurazioni delle compilazioni)  
 [Compilazione e pulizia di progetti e soluzioni in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)   
 [Gestione delle proprietà di progetti e soluzioni](managing-project-and-solution-properties.md)

