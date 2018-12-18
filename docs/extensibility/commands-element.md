---
title: I comandi elemento | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2d905914c9819671cf8c77d81ec8d51302467a9d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="commands-element"></a>Elemento Commands
Rappresenta la raccolta di comandi sulla barra degli strumenti di VSPackage. La raccolta può avere fino a cinque sezioni, come indicato di seguito: menu, gruppi, i pulsanti, casella combinata e bitmap.  
  
 Ogni elemento figlio sottosezione, ad esempio, \<Menu >, è identificato da un ID univoco del comando che è un GUID e la coppia identificatore numerico. Il GUID identifica il set di comandi"" e viene utilizzato per raggruppare i comandi correlati logicamente. Il pacchetto VSPackage deve definire un proprio set per evitare conflitti con gli ID di comando che sono definiti da altri pacchetti VSPackage di comandi.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Commands package="GuidMyPackage" >  
  <Menus>... </Menus>  
  <Groups>... </Groups>  
  <Buttons>... </Buttons>  
  <Combos>... </Combos>  
  <Bitmaps>... </Bitmaps>  
</Commands>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|pacchetto|GUID che identifica il pacchetto VSPackage che fornisce i comandi.<br /><br /> Ad esempio, creare un pacchetto = "guidVsPackage1Pkg".|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Menus](../extensibility/menus-element.md)|Definisce tutti i menu che implementa un pacchetto VSPackage.|  
|[Elemento Groups](../extensibility/groups-element.md)|Contiene le voci che definiscono i gruppi di comandi in un pacchetto VSPackage.|  
|[Elemento Buttons](../extensibility/buttons-element.md)|Raggruppa gli elementi di pulsante.|  
|[Elemento Bitmaps](../extensibility/bitmaps-element.md)|Raggruppa gli elementi di Bitmap.|  
|[Elemento Combos](../extensibility/combos-element.md)|Raggruppa elementi combinata.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi che un pacchetto VSPackage fornisce all'IDE. Gli elementi possibili sono voci di menu, menu, barre degli strumenti e caselle combinate.|  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come utilizzare un [elemento Commands](../extensibility/commands-element.md).  
  
```  
<Commands package="guidMyPackage">  
    <Menus>  
      <Menu Condition="'%(DEBUG)' != 'true'"   
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"   
        priority="0x0000" type="Menu">  
        <Annotation>  
          <Documentation>this is an annotation</Documentation>  
          <AppInfo>  
            <CustomData>  
              <CustomSubElement>Some data</CustomSubElement>  
            </CustomData>  
          </AppInfo>  
        </Annotation>  
        <CommandFlag>AlwaysCreate</CommandFlag>  
        <Strings>  
          <ButtonText>MainMenu</ButtonText>  
        </Strings>  
      </Menu>  
  </Menus>  
<Commands>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Come VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)