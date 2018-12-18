---
title: Fare riferimento a elemento (modelli di Visual Studio) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#Reference
helpviewer_keywords:
- Reference element [Visual Studio templates]
- <Reference> element [Visual Studio templates]
ms.assetid: 852772ea-c324-42e9-8c8a-6d565414a109
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1006e85611044805c0f3bd1e0035595288a5b32d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="reference-element-visual-studio-templates"></a>Elemento Reference (modelli di Visual Studio)
Specifica il riferimento all'assembly da aggiungere quando l'elemento viene aggiunto a un progetto.  
  
 \<VSTemplate >  
 \<TemplateContent >  
 \<Riferimenti >  
 \<Riferimento >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Reference>  
    <Assembly> ... </Assembly>  
</Reference>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Assembly](../extensibility/assembly-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Specifica le informazioni relative a un assembly, che utilizza il modello per aggiungere un riferimento dell'assembly per i progetti. Deve essere presente un `Assembly` elemento in ogni `Reference` elemento.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Riferimenti](../extensibility/references-element-visual-studio-templates.md)|Raggruppa i riferimenti all'assembly che il modello consente di aggiungere ai progetti.|  
  
## <a name="remarks"></a>Note  
 `Reference` è un elemento figlio obbligatorio di `References`.  
  
 Il `Reference` e `References` elementi possono essere utilizzati solo nei file con estensione vstemplate che hanno un `Type` valore dell'attributo `Item`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato il `TemplateContent` elemento di un modello di elemento. Questo codice XML vengono aggiunti riferimenti agli assembly dll e System.Data.dll.  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)