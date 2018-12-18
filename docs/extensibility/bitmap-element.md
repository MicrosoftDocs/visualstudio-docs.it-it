---
title: Bitmap elemento | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: eb265aabdb4feda05512e036cda19abc574e2fd4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="bitmap-element"></a>Elemento bitmap
Definisce una bitmap. La bitmap viene caricata da una risorsa o da un file.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|guid|Obbligatorio. GUID dell'identificatore di comando/ID GUID.<br /><br /> L'attributo guid per una bitmap non è associata a un pacchetto VSPackage o un altro gruppo di comando.  Deve essere univoco nella definizione di bitmap e non deve essere utilizzato per altri scopi.|  
|resID|ID dell'identificatore di comando/ID GUID. È necessario il resID o l'attributo href.<br /><br /> L'attributo resID è un ID di risorsa numero intero che determina la striscia di bitmap che deve essere caricato durante l'unione di tabella di comando.  Durante il caricamento di tabella del comando, la bitmap specificata dall'ID di risorsa verrà caricata dalla risorsa dello stesso modulo.|  
|usedList|Obbligatorio se è presente l'attributo resID. Consente di selezionare le immagini disponibili nella striscia di bitmap.|  
|href|Percorso alla bitmap. È necessario il resID o l'attributo href.<br /><br /> Il percorso di inclusione viene cercato il file di immagine indicato, che è incorporato nel file binario risulta.  Durante l'unione di tabella di comando, l'immagine viene copiata e nessuna ricerca di risorse aggiuntive o il carico è necessario.  Se l'attributo usedList non è presente, sono disponibili tutte le immagini nell'elenco. **Nota:** immagini possono essere fornite in uno dei diversi formati che includono i file con estensione bmp, PNG e GIF.  Le versioni precedenti del compilatore non supportano le immagini bitmap a 32 bit che contiene informazioni alfa per la trasparenza parziale. La soluzione alternativa per queste versioni consiste nell'utilizzare il formato. PNG.|  
|Condizione|Facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Bitmaps](../extensibility/bitmaps-element.md)|Raggruppa gli elementi di Bitmap.|  
  
## <a name="example"></a>Esempio  
  
```  
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
  usedList="1, 2, 3, 4"/>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)