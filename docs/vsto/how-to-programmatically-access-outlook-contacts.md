---
title: 'Procedura: accedere a livello di codice ai contatti di Outlook | Documenti Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c48a58a4215ce73bcc6e9f4593819cbbdbed1693
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Procedura: accedere ai contatti di Outlook a livello di codice
  Questo esempio vengono trovati tutti i contatti il cui cognome contengano una stringa di ricerca specificato.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 L'esempio presenta i requisiti seguenti:  
  
-   Contatti il cui cognome contengono la stringa "**Na"** , ad esempio Tzipi Butnaru, nel **contatti** cartella.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo dei contatti](../vsto/working-with-contact-items.md)   
 [Procedura: aggiungere una voce ai contatti di Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [Procedura: eseguire la ricerca a livello di codice per un contatto specifico](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [Procedura: eseguire la ricerca a livello di codice per un indirizzo di posta elettronica nei contatti](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [Procedura: Eliminare contatti di Outlook a livello di codice](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  