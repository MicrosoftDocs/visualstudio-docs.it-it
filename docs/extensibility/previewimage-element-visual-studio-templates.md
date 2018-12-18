---
title: Elemento PreviewImage (modelli di Visual Studio) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <PreviewImage> Element (Visual Studio Templates)
- PreviewImage Element (Visual Studio Templates)
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ee25a764326572531e02eb91985aa6150c310715
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="previewimage-element-visual-studio-templates"></a>Elemento PreviewImage (modelli di Visual Studio)
Specifica l'immagine di anteprima, come un nome di file, per l'immagine di anteprima che verrà visualizzato in entrambi i **nuovo progetto** o **Aggiungi nuovo elemento** la finestra di dialogo.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<PreviewImage >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<PreviewImage>"filename"</PreviewImage>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello e definisce come vengono visualizzati in entrambi i **nuovo progetto** o **Aggiungi nuovo elemento** la finestra di dialogo.|  
  
## <a name="text-value"></a>Valore di testo  
 È necessario specificare un valore di testo.  
  
 Il testo deve essere una stringa che rappresenta un nome di file.  
  
## <a name="remarks"></a>Note  
 `PreviewImage` è un elemento facoltativo.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)