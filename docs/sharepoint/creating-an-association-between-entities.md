---
title: "Creazione di un'associazione tra entità | Documenti Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.BDC.Association_Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: ec68543f50e3cde527792cdaaca0fb32a93a3dd7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="creating-an-association-between-entities"></a>Creazione di un'associazione tra entità
  È possibile definire relazioni tra entità nel modello (Applicativa dei dati) tramite la creazione di associazioni. Visual Studio genera metodi che forniscono i consumer del modello con informazioni su ogni associazione. Questi metodi possono essere utilizzati da elenchi, applicazioni personalizzate o web part di SharePoint per visualizzare le relazioni tra i dati in un'interfaccia utente.  
  
## <a name="creating-an-association"></a>Creazione di un'associazione  
 Creare un'associazione scegliendo il **associazione** controllo in Visual Studio **della casella degli strumenti**, scegliendo la prima entità (entità di origine denominata) e quindi la seconda entità (chiamato il entità di destinazione). È possibile definire i dettagli dell'associazione nel **Editor di associazione**. Per ulteriori informazioni, vedere [procedura: creare un'associazione tra entità](../sharepoint/how-to-create-an-association-between-entities.md).  
  
## <a name="association-methods"></a>Metodi di associazione  
 Le applicazioni, ad esempio web part dei dati aziendali di SharePoint utilizzano associazioni chiamando i metodi nella classe di servizio di un'entità. È possibile aggiungere metodi alla classe di servizio di un'entità selezionandoli nel **Editor di associazione**.  
  
 Per impostazione predefinita, il **Editor di associazione** aggiunge un metodo AssociationNavigator alle entità di origine e destinazione. Un metodo AssociationNavigator nell'entità di origine consente agli utenti di recuperare un elenco di entità di destinazione. Un metodo AssociationNavigator nell'entità di destinazione consente agli utenti di recuperare l'entità di origine che si riferisce a un'entità di destinazione.  
  
 È necessario aggiungere il codice per ognuno di questi metodi per restituire le informazioni appropriate. È anche possibile aggiungere altri tipi di metodi per supportare scenari più avanzati. Per ulteriori informazioni su ciascuno di questi metodi, vedere [operazioni supportate](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
## <a name="types-of-associations"></a>Tipi di associazioni  
 È possibile creare due tipi di associazioni nella finestra di progettazione di integrazione applicativa dei dati: associazioni basato su chiave esterne e associazioni senza chiave esterna.  
  
### <a name="foreign-key-based-association"></a>Associazione basata su chiavi esterne  
 È possibile creare un'associazione basata su chiavi esterne in relazione con un identificatore dell'entità di origine al tipo descrittori definiti nell'entità di destinazione. Questa relazione consente agli utenti del modello fornire un'interfaccia utente avanzata per i propri utenti. Ad esempio, un modulo in Outlook che consente all'utente di creare un ordine di vendita che è possibile visualizzare i clienti in un elenco a discesa; o un elenco di ordini di vendita in SharePoint che consente agli utenti di aprire una pagina del profilo per un cliente.  
  
 Per creare un'associazione basata su chiavi esterne, correlare gli identificatori e descrittori di tipo che condividono lo stesso nome e tipo. Ad esempio, è possibile creare un'associazione basata su chiavi esterne tra un `Contact` entità e un `SalesOrder` entità. Il `SalesOrder` entità restituisce una `ContactID` descrittore di tipo come parte del parametro restituito dal metodo Finder o Finder specifico. Entrambi i descrittori di tipo vengono visualizzati di **Editor di associazione**. Per creare una relazione basata su chiave esterna tra le `Contact` entità e `SalesOrder` entità, scegliere il `ContactID` identificatore accanto a ciascuno di questi campi.  
  
 Aggiungere codice al metodo AssociationNavigator dell'entità di origine che restituisce una raccolta di entità di destinazione. L'esempio seguente restituisce gli ordini di vendita per un contatto.  
  
 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]  
  
 Aggiungere codice al metodo AssociationNavigator dell'entità di destinazione che restituisce un'entità di origine. Nell'esempio seguente viene restituito il contatto è correlato all'ordine di vendita.  
  
 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]  
  
### <a name="foreign-keyless-association"></a>Associazione senza chiave esterna  
 È possibile creare un'associazione senza mapping tra gli identificatori e descrittori del tipo di campo. Creare questo tipo di associazione quando l'entità di origine non dispone di una relazione diretta con l'entità di destinazione. Ad esempio, un `SalesOrderDetail` tabella non dispone di una chiave esterna che esegue il mapping a una chiave primaria in un `Contact` tabella.  
  
 Se si desidera visualizzare le informazioni nel `SalesOrderDetail` tabella che si riferisce a un `Contact`, è possibile creare un'associazione senza chiave esterna tra le `Contact` entità e `SalesOrderDetail` entità.  
  
 Nel metodo AssociationNavigator il `Contact` entità, restituito il `SalesOrderDetail` entità unendo in join tabelle o chiamando una stored procedure.  
  
 Nell'esempio seguente vengono restituiti i dettagli di tutti gli ordini di vendita unendo in join le tabelle.  
  
 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]  
  
 Nel metodo AssociationNavigator il `SalesOrderDetail` entità, restituire correlata `Contact`. Nell'esempio che segue viene illustrato quanto descritto.  
  
 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]  
  
## <a name="see-also"></a>Vedere anche  
 [Progettazione di un modello di integrazione applicativa dei dati Business](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Procedura: creare un'associazione tra entità](../sharepoint/how-to-create-an-association-between-entities.md)  
  
  