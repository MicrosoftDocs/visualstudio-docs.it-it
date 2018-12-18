---
title: 'Procedura: invio di posta elettronica a livello di codice | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c3ee656a8a4965f01969bad19d66d0ea6215bcbe
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-send-e-mail"></a>Procedura: invio di posta elettronica a livello di codice  
  Questo esempio viene inviato un messaggio di posta elettronica per i contatti con il nome di dominio **example.com** indirizzi di posta elettronica.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 L'esempio presenta i requisiti seguenti:  
  
-   I contatti con il nome di dominio **example.com** indirizzi di posta elettronica.  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Non rimuovere il codice di filtro che cerca il nome di dominio **example.com**. Se si rimuove il filtro, la soluzione invierà messaggi di posta elettronica a tutti i contatti.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di elementi di posta elettronica](../vsto/working-with-mail-items.md)   
 [Procedura: creare a livello di programmazione un elemento di posta elettronica](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [Procedura: accedere a livello di codice ai contatti di Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Procedura: Eseguire azioni a livello di codice quando viene ricevuto un messaggio di posta elettronica](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  