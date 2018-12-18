---
title: La creazione di gruppi riutilizzabili pulsanti | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- button groups, creating in VSPackages
- VSPackages, creating reusable button groups
- buttons, creating reusable groups
ms.assetid: 0c561617-fb86-476d-8bd1-c6e5e7464c65
caps.latest.revision: "44"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c2ac175d2fd267500f19e9f22cd46d88dcc9f314
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="creating-reusable-groups-of-buttons"></a>Creazione di gruppi riutilizzabili di pulsanti
Un gruppo di comandi è una raccolta di comandi che vengono sempre visualizzati insieme in un menu o una barra degli strumenti. Qualsiasi gruppo di comando nuovo utilizzabile tramite l'assegnazione ai menu padre diverso nella sezione CommandPlacements del file con estensione vsct.  
  
 Gruppi di comandi in genere contengono pulsanti, ma possono essere contenuti anche altri menu o caselle combinate.  
  
### <a name="to-create-a-reusable-group-of-buttons"></a>Per creare un gruppo di pulsanti riutilizzabile  
  
1.  Creare un progetto VSIX denominato `ReusableButtons`. Per ulteriori informazioni, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Quando si apre il progetto, aggiungere un modello di elemento di comando personalizzato denominato **ReusableCommand**. Nel **Esplora**del mouse sul nodo del progetto e scegliere **Aggiungi / nuovo elemento**. Nel **Aggiungi nuovo elemento** finestra di dialogo, passa a **Visual c# / Extensibility** e selezionare **comando personalizzato**. Nel **nome** campo nella parte inferiore della finestra, modificare il nome del file di comando in **ReusableCommand.cs**.  
  
3.  Nel file vsct, vedere la sezione di simboli e trovare l'elemento GuidSymbol che contiene i gruppi e i comandi per il progetto. Devono essere denominato guidReusableCommandPackageCmdSet.  
  
4.  Aggiungere un IDSymbol per ogni pulsante che verrà aggiunto al gruppo, come nell'esempio seguente.  
  
    ```xml  
    <GuidSymbol name="guidReusableCommandPackageCmdSet" value="{7f383b2a-c6b9-4c1d-b4b8-a26dc5b60ca1}">  
        <IDSymbol name="MyMenuGroup" value="0x1020" />  
        <IDSymbol name="ReusableCommandId" value="0x0100" />  
        <IDSymbol name="SecondReusableCommandId" value="0x0200" />  
    </GuidSymbol>  
    ```  
  
     Per impostazione predefinita, il modello di elemento di comando crea un gruppo denominato **MyGroup** e un pulsante con il nome fornito dall'utente, insieme a una voce IDSymbol per ognuno.  
  
5.  Nella sezione gruppi, creare un elemento di gruppo che ha gli stessi attributi GUID e ID di quelli specificati nella sezione simboli. È anche possibile utilizzare un gruppo esistente o utilizzare la voce che viene fornita dal modello di comando, come nell'esempio seguente. Questo gruppo viene visualizzata sul **strumenti** menu  
  
    ```xml  
    <Groups>  
        <Group guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0x0600">  
              <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS"/>  
        </Group>  
    </Groups>  
    ```  
  
### <a name="to-create-a-group-of-buttons-for-reuse"></a>Per creare un gruppo di pulsanti per il riutilizzo  
  
1.  È possibile inserire un comando o un menu in un gruppo tramite il gruppo come elemento padre nella definizione del comando o menu o inserendo il comando o il menu del gruppo utilizzando la sezione CommandPlacements.  
  
     Nella sezione pulsanti definire un pulsante con il gruppo come elemento padre oppure utilizzare il pulsante che viene fornito dal modello di pacchetto, come illustrato nell'esempio seguente.  
  
    ```xml  
    <Button guid="guidReusableCommandPackageCmdSet" id="ReusableCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke ReusableCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
2.  Se un pulsante deve comparire in più di un gruppo, creare una voce per tale nella sezione CommandPlacements, che deve essere inserita dopo la sezione di comandi. Impostare gli attributi GUID e ID dell'elemento CommandPlacement affinché corrispondano a quelle del pulsante che si desidera posizionare e quindi impostare il GUID e l'ID dell'elemento padre a quelli del gruppo di destinazione, come illustrato nell'esempio seguente.  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="SecondReusableCommandId" priority="0x105">  
          <Parent guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" />  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    > [!NOTE]
    >  Il valore del campo priorità determina la posizione del comando nel nuovo gruppo di comando. Le priorità di impostare il CommandPlacement elemento sostituiscono quelli impostati nella definizione di elemento. I comandi che hanno valori di priorità inferiore vengono visualizzati prima i comandi che hanno valori di priorità superiore. Sono consentiti valori di priorità identici, ma la posizione relativa dei comandi con lo stesso valore di priorità non può essere garantita poiché l'ordine in cui il **devenv /setup** comando crea l'interfaccia finale dal Registro di sistema potrebbe non essere coerente.  
  
### <a name="to-put-a-reusable-group-of-buttons-on-a-menu"></a>Per inserire un gruppo di pulsanti riutilizzabile in un menu  
  
1.  Creare una voce di `CommandPlacements` sezione. Impostare il GUID e ID del `CommandPlacement` elemento a quelli del gruppo e impostare l'elemento padre GUID e ID a quelle del percorso di destinazione.  
  
     La sezione CommandPlacements deve essere posizionata immediatamente dopo la sezione di comandi:  
  
    ```xml  
    <CommandTable>  
    ...  
      <Commands>... </Commands>  
      <CommandPlacements>... </CommandPlacements>  
    ...   
    </CommandTable>  
    ```  
  
     Un gruppo di comandi può essere inclusi più di un menu. Menu del padre può essere creato, che viene fornito da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (come descritto in ShellCmdDef.vsct o SharedCmdDef.vsct), o che viene definito in un altro VSPackage. Il numero di livelli padre è illimitato, purché menu del padre è connesso alla fine di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o a un menu di scelta rapida che viene visualizzato da un pacchetto VSPackage.  
  
     Nell'esempio seguente inserisce il gruppo **Esplora** barra degli strumenti, a destra degli altri pulsanti.  
  
    ```xml  
    <CommandPlacements>  
        <CommandPlacement guid="guidReusableCommandPackageCmdSet" id="MyMenuGroup" priority="0xF00">  
          <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_PROJWIN"/>  
        </CommandPlacement>  
    </CommandPlacements>  
    ```  
  
    ```xml  
    <CommandPlacements>  
      <CommandPlacement guid="guidButtonGroupCmdSet" id="MyMenuGroup"   
          priority="0x605">  
        <Parent guid="guidSHLMainMenu" id="IDM_VS_MENU_TOOLS" />  
      </CommandPlacement>  
    </CommandPlacements>  
  
    ```