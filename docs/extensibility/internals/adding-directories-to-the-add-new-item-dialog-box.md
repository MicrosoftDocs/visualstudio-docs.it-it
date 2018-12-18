---
title: Aggiunta di directory per il dialogo Aggiungi nuovo elemento | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b8d9989e8cf4ec8f0eb714a26e73d89fba339b71
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>Aggiunta di directory per il dialogo Aggiungi nuovo elemento
Esempio di codice riportato di seguito viene illustrato come registrare un nuovo set di directory per il **Aggiungi nuovo elemento** la finestra di dialogo. Directory per il **Aggiungi nuovo elemento** la finestra di dialogo sono diverse per ogni progetto. Pertanto, le directory vengono registrate nella sottochiave progetti, vedere \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects >:  
  
## <a name="the-registry-script"></a>Lo Script del Registro di sistema  
  
```  
NoRemove Projects  
{  
  NoRemove %GUID_Project%  
  {  
    NoRemove AddItemTemplates  
    {  
      NoRemove TemplateDirs  
      {  
        ForceRemove %CLSID_Package%  
        {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
          {  
            val TemplatesDir = s '%Template_Path%'     
            val SortPriority = d 2000  
          }  
        }  
      }  
    }  
  }  
}  
```  
  
 Il valore Template_Path specifica il percorso completo della directory che contiene i modelli di progetto. Questi modelli possono essere VSZ (file) o file di modello prototipo da clonare.  
  
 Il valore SortPriority specifica una priorità di ordinamento.  
  
## <a name="adding-items-to-an-existing-project"></a>Aggiunta di elementi a un progetto esistente  
 È anche possibile aggiungere elementi a un progetto esistente. Ad esempio, per un [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] progetto, è possibile aggiungere elementi per il \<radice > cartella \VC#\CSharpProjectItems\LocalProjectItems \Programmi\Microsoft Visual Studio. In questo caso il `%GUID_Project%` è il GUID per un progetto c# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 È anche possibile estendere un progetto esistente da un sottotipo di progetto di programmazione. Con un sottotipo di progetto, è possibile estendere un progetto senza scrivere un nuovo tipo di progetto. Per ulteriori informazioni su sottotipi di progetto, vedere [sottotipi di progetto](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Vedere anche  
 [La registrazione di progetto e modelli di elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Aggiunta di elementi di Aggiungi nuovo elemento di finestre di dialogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Aggiunta di directory nella finestra di dialogo Nuovo progetto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)