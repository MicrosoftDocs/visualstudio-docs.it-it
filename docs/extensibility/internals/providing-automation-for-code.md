---
title: Fornisce l'automazione per il codice | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9f9dbb7a8ddad39f01f5b29443168eebe12a2da8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="providing-automation-for-code"></a>Fornisce l'automazione per il codice
Creazione di un modello di automazione per il codice non è necessaria. il SDK di ambiente non fornisce un esempio per questa operazione. Per informazioni su modelli di codice, vedere il <xref:EnvDTE.CodeModel> oggetto.  
  
 Per implementare un modello di codice, è necessario implementare le interfacce che sono determinate dalla struttura di dati interno. Gli oggetti devono essere derivati dalla `IDispatch` classe.  
  
 Gli oggetti che si estendono, <xref:EnvDTE.CodeModel> e <xref:EnvDTE.FileCodeModel>, sono disponibili le <xref:EnvDTE.Project> dell'oggetto e simile al seguente:  
  
 <xref:EnvDTE.Project.CodeModel%2A>  
  
 <xref:EnvDTE.ProjectItem.FileCodeModel%2A>  
  
 È possibile scegliere di implementare solo il `CodeModel` o `FileCodeModel` interfaccia l'oggetto restituito dal `Project` e <xref:EnvDTE.ProjectItem> oggetti. Fornisce funzionalità da questa interfaccia appropriata per il sistema di progetto.  
  
 Se si desidera aggiungere le funzionalità, ad esempio metodi o proprietà, che non sono disponibili dallo standard `CodeModel` e `FileCodeModel` interfacce, creare un'interfaccia che eredita da standard. Assicurarsi di documentare con il sistema di progetto in modo che gli utenti finali verrà per cercare l'elemento. Restituire l'interfaccia standard, ma l'utente può chiamare il `QueryInterface` metodo o eseguire il cast all'interfaccia se è noto al esiste.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica del modello di automazione](../../extensibility/internals/automation-model-overview.md)