---
title: Formattazione, XML, Editor di testo, finestra di dialogo Opzioni | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9a4d6de24a75b5a08820878bc74633c02ab4118f
ms.sourcegitcommit: 5f436413bbb1e8aa18231eb5af210e7595401aa6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2018
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>Formattazione, XML, Editor di testo, finestra di dialogo Opzioni
Questa finestra di dialogo consente di specificare le impostazioni di formattazione dell'editor XML. È possibile accedere il **opzioni** dalla finestra di dialogo di **strumenti** menu.  
  
> [!NOTE]
>  Queste impostazioni sono disponibili quando si seleziona il **Editor di testo** cartella, il **XML** cartella, quindi il **formattazione** opzione il **opzioni** la finestra di dialogo.  
  
## <a name="attributes"></a>Attributi  
 **Mantieni la formattazione manuale degli attributi**  
 Gli attributi non vengono riformattati. Questa è l'impostazione predefinita.  
  
> [!NOTE]
>  Se gli attributi si trovano su più righe, l'editor fa rientrare ogni riga degli attributi in base al rientro dell'elemento padre.  
  
 **Allinea ogni attributo su una riga separata**  
 Allinea verticalmente il secondo attributo e i successivi in base al rientro del primo attributo. Il testo XML seguente è un esempio di come vengono allineati gli attributi.  
  
```xml
<item id = "123-A"  
      name = "hammer"  
      price = "9.95">  
</item>  
```
  
## <a name="auto-reformat"></a>Riformatta automaticamente  
 **Quando si incolla dagli Appunti**  
 Riformatta il testo XML incollato dagli Appunti.  
  
 **Al completamento del tag di fine**  
 Riformatta l'elemento quando il tag di fine è completato.  
  
## <a name="mixed-content"></a>Contenuto misto  
 **Mantieni contenuto misto per impostazione predefinita**  
 Determina se l'editor riformatta o meno il contenuto misto. Per impostazione predefinita l'editor tenta di riformattare il contenuto misto, a meno che il contenuto non venga rilevato in un ambito `xml:space="preserve"`.  
  
 Se un elemento contiene una combinazione di testo e markup, il contenuto viene considerato misto. Di seguito viene riportato un esempio di elemento con contenuto misto.  
  
```xml
<dir>c:\data\AlphaProject\  
  <file readOnly="false">test1.txt</file>  
  <file readOnly="false">test2.txt</file>  
</dir>  
```
  
## <a name="see-also"></a>Vedere anche  
 [Proprietà del documento XML, finestra proprietà](../xml-tools/xml-document-properties-properties-window.md)   
 [Componenti dell'editor XML](../xml-tools/xml-editor-components.md)