---
title: 'Procedura: accedere a livello di codice ai contatti di Outlook | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: contacts [Office development in Visual Studio], searching
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4d4d88416507f7e63cd112df350dc93b2e13605f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
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
  
  