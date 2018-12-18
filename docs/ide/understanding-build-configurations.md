---
title: Informazioni sulle configurazioni della build | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SolutionProperties.ActiveConfig
- vs.build.newprojectconfiguration
- vc.proj.configurationsctrl.multipleconfigs
- vs.build.editsolutionconfigurations
- vs.build.editprojectconfigurations
- vs.multipleconfigurations
- vs.build.newsolutionconfiguration
- VS.ConfigurationManager
- VS.MultipleConfig
helpviewer_keywords:
- solution build configurations, about build configurations
- build configurations
- project build configurations
- build configurations, advanced
- projects [Visual Studio], build configuration
- solutions [Visual Studio], build configuration
ms.assetid: 934c727d-3a22-429c-bd13-3552cecf2e24
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 6cf3f299f2b5ec2e38b5fe0315b6d0abc0411b12
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="understanding-build-configurations"></a>Informazioni sulle configurazioni della build
È possibile memorizzare diverse configurazioni di proprietà per soluzioni e progetti da usare in tipi di compilazioni differenti. Per creare, selezionare, modificare o eliminare una configurazione, è possibile usare **Gestione configurazione**. Per aprirlo, sulla barra dei menu scegliere **Compilazione**, **Gestione configurazione** oppure digitare **configurazione** nella casella **Avvio veloce**. È inoltre possibile usare l'elenco **Configurazioni soluzione** sulla barra degli strumenti **Standard** per selezionare una configurazione o aprire **Gestione configurazione**.  
  
> [!NOTE]
>  Se le impostazioni di configurazione della soluzione non vengono trovate sulla barra degli strumenti oppure se non è possibile accedere a **Gestione configurazione**, è possibile che siano applicate le impostazioni di sviluppo di [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Per altre informazioni, vedere [Procedura: Gestire configurazioni di compilazione applicando le impostazioni di Visual Basic Developer](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).  
  
 Per impostazione predefinita, le configurazioni per il debug e il rilascio sono incluse nei progetti creati mediante i modelli [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Una configurazione per il debug supporta il debug di un'applicazione, mentre una configurazione per il rilascio consente di compilare una versione dll'applicazione che può essere distribuita. Per altre informazioni, vedere [Procedura: Impostare le configurazioni di debug e rilascio](../debugger/how-to-set-debug-and-release-configurations.md). È inoltre possibile creare configurazioni personalizzate per progetti e soluzioni. Per altre informazioni, vedere [How to: Create and Edit Configurations](../ide/how-to-create-and-edit-configurations.md) (Procedura: Creare e modificare le configurazioni).  
  
## <a name="solution-configurations"></a>Configurazioni soluzione  
 In una configurazione per la soluzione viene specificato il modo in cui i progetti di una soluzione devono essere compilati e distribuiti. Per modificare una configurazione per la soluzione o per definirne una nuova, in **Gestione configurazione**, sotto la voce **Configurazione soluzione attiva** scegliere **Modifica** o **Nuovo**.  
  
 Ogni voce nella casella **Contesti progetto** di una configurazione per la soluzione rappresenta un progetto nella soluzione. Per ogni combinazione di **Configurazione soluzione attiva** e **Piattaforma soluzione attiva**, è possibile definire il modo in cui ogni progetto viene usato. Per altre informazioni sulle piattaforme per la soluzione, vedere [Informazioni sulle piattaforme di compilazione](../ide/understanding-build-platforms.md).  
  
> [!NOTE]
>  Quando si definisce una nuova configurazione per la soluzione e si seleziona la casella di controllo **Crea nuove configurazioni progetto**, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene assegnata automaticamente la nuova configurazione a tutti i progetti. In modo analogo, quando si definisce una nuova configurazione per la soluzione e si seleziona la casella di controllo **Crea nuove piattaforme progetto**, in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene assegnata automaticamente la nuova configurazione a tutti i progetti. Inoltre, se si aggiunge un progetto destinato a una nuova piattaforma, in Visual Studio tale piattaforma viene aggiunta all'elenco delle piattaforme per la soluzione e assegnata a tutti i progetti.  
>   
>  È ancora possibile modificare le impostazioni per ogni progetto.  
  
 La configurazione per la soluzione attiva fornisce anche il contesto all'IDE. Se, ad esempio, si sta lavorando a un progetto e nella configurazione per la soluzione attiva viene specificata la compilazione per un dispositivo mobile, nella **Casella degli strumenti** verranno visualizzati solo gli elementi del progetto che possono essere usati in un progetto per un dispositivo mobile.  
  
## <a name="project-configurations"></a>Configurazioni di progetto  
 La piattaforma e la configurazione correlate a un progetto vengono usate congiuntamente per specificare le proprietà da usare durante le compilazione. A un progetto può essere associato un set di definizioni di proprietà diverso per ogni combinazione di configurazione e piattaforma. Per modificare le proprietà di un progetto, è possibile usare le pagine delle proprietà. In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto e scegliere **Proprietà**.  
  
 Per ogni configurazione di progetto, possono essere definite le proprietà dipendenti dalla configurazione in base alle esigenze. Per una determinata compilazione, ad esempio, è possibile impostare gli elementi del progetto che verranno inclusi, i file di output che verranno creati, la posizione in cui saranno collocati e il modo in cui verranno ottimizzati.  
  
 Le configurazioni di progetto possono variare notevolmente. Nelle proprietà di una configurazione di progetto può ad esempio essere specificata l'ottimizzazione del file di output, in modo che il file binario che ne risulta occupi uno spazio minimo, mentre un altro progetto può essere ottimizzato in modo che l'esecuzione avvenga alla velocità massima possibile.  
  
 Le configurazioni di progetto non vengono archiviate per utente bensì per soluzione, in modo che possano essere condivise.  
  
 Nonostante le dipendenze dei progetti siano indipendenti dalla configurazione, verranno compilati solo i progetti specificati nella configurazione di soluzione attiva.  
  
## <a name="how-visual-studio-assigns-project-configurations"></a>Modalità di assegnazione delle configurazioni di progetto in Visual Studio  
 Quando si definisce una nuova configurazione di soluzione e non la si copia da una già esistente, in Visual Studio vengono usati i criteri seguenti per assegnare configurazioni di progetto predefinite. I criteri vengono valutati nell'ordine indicato.  
  
1.  Se il nome di configurazione (*\<nome configurazione> \<nome piattaforma>*) di un progetto corrisponde esattamente al nome della nuova configurazione per la soluzione, viene assegnata la configurazione specifica. I nomi delle configurazioni non rispettano la distinzione tra maiuscole e minuscole.  
  
2.  Se il progetto include un nome di configurazione in cui la parte del nome corrisponde alla nuova configurazione per la soluzione, tale configurazione viene assegnata, anche se le piattaforme non coincidono.  
  
3.  Se non esiste alcuna corrispondenza, viene assegnata la prima configurazione elencata nel progetto.  
  
## <a name="how-visual-studio-assigns-solution-configurations"></a>Modalità di assegnazione delle configurazioni per le soluzioni in Visual Studio  
 Quando si crea una configurazione per il progetto (in **Gestione configurazione** scegliere **Nuovo** nel menu a discesa nella colonna **Configurazione** del progetto) e si seleziona la casella di controllo **Crea nuove configurazioni soluzione**, in Visual Studio viene cercata una configurazione con lo stesso nome per compilare il progetto per ogni piattaforma supportata. In alcuni casi, le configurazioni di soluzione esistenti vengono rinominate o ne vengono definite di nuove.  
  
 In Visual Studio vengono usati i criteri seguenti per assegnare configurazioni di soluzione.  
  
-   Se in una configurazione di progetto non è specificata una piattaforma oppure ne è specificata una sola, viene trovata o aggiunta una configurazione per la soluzione il cui nome corrisponde a quello della nuova configurazione di progetto. Il nome predefinito di tale configurazione di soluzione non include un nome di piattaforma e pertanto assume il formato *\<nome configurazione di progetto>*.  
  
-   Se un progetto supporta più piattaforme, verrà trovata o aggiunta una configurazione per la soluzione per ogni piattaforma supportata. Il nome di ogni configurazione di soluzione include sia il nome della configurazione di progetto sia il nome della piattaforma e assume il formato *\<nome configurazione di progetto> \<nome piattaforma>*.  
  
## <a name="see-also"></a>Vedere anche  
 [Walkthrough: Building an Application](../ide/walkthrough-building-an-application.md)  (Procedura dettagliata: Compilazione di un'applicazione)  
 [Compiling and Building](../ide/compiling-and-building-in-visual-studio.md)  (Compilazione e creazione)  
 [Solutions and Projects](../ide/solutions-and-projects-in-visual-studio.md)  (Soluzioni e progetti)  
 [Riferimenti alla compilazione in C/C++](/cpp/build/reference/c-cpp-building-reference)   
 [Opzioni della riga di comando devenv](../ide/reference/devenv-command-line-switches.md)