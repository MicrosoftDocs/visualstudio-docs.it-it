---
title: Aggiunta di directory per la finestra di dialogo Nuovo progetto | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 881979b54fb8f8f07a7ffeb2f3648b690fe2bf78
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>Aggiunta di directory per la finestra di dialogo Nuovo progetto
Quando si creano nuovi tipi di progetto, è anche possibile registrare una nuova directory di **nuovo progetto** la finestra di dialogo per la visualizzazione da utilizzare come modelli. Esempio di codice seguente viene illustrato come registrare una nuova directory, noto anche come un nodo. Nell'esempio, modelli esposti dal VSPackage CLSID_Package vengono registrati. Di conseguenza, il lato sinistro del **nuovo progetto** la finestra di dialogo offre il nodo aggiunto, con un nome di base della risorsa Folder_Label_ResID. Questa risorsa verrà caricata dal pacchetto VSPackage DLL satellite.  
  
 Il **cartella** valore rappresenta un GUID di una cartella in cui viene visualizzato il nodo Folder_Label_ResID. Nell'esempio, rappresenta il GUID di **altri progetti** cartella la **tipi di progetto** riquadro del **nuovo progetto** la finestra di dialogo. Se il **altri progetti** valore è assente, l'etichetta viene posizionata nella parte superiore.  
  
 Il valore TemplatesDir specifica il percorso completo della directory che contiene i modelli di progetto. Questi file possono essere file VSZ o file di modello tipico per la clonazione.  
  
 Se si specifica TemplatesLocalizedSubDir, deve essere l'ID di risorsa di una stringa che assegna un nome di sottodirectory di TemplatesDir che contiene modelli localizzati. Poiché [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carica la risorsa stringa da una DLL satellite se si dispone di uno, ogni DLL satellite contenere un nome di sottodirectory di diversi. Il valore SortPriority specifica una priorità di ordinamento.  
  
```  
NoRemove NewProjectTemplates  
{  
    NoRemove TemplateDirs  
  {  
    ForceRemove %CLSID_Package%  
    {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
      {  
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'  
        val TemplatesDir = s '%Template_Path%'  
        val TemplatesLocalizedSubDir = s '#100'  
        val SortPriority = d 1000  
      }  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [La registrazione di progetto e modelli di elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Aggiunta di elementi di Aggiungi nuovo elemento di finestre di dialogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Aggiunta di directory nella finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)