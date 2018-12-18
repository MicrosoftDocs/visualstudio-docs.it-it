---
title: Necessarie modifiche per l'esecuzione di progetti di Office migrati a .NET Framework 4 o .NET Framework 4.5 | Documenti Microsoft
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
helpviewer_keywords: Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: ee90d5c205f58736f7ccb6536e29b2fd6d16b152
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2018
---
# <a name="required-changes-to-run-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Modifiche necessarie per l'esecuzione di progetti di Office migrati a .NET Framework 4 o a .NET Framework 4.5
  Se il framework di destinazione di un progetto di Office viene modificato per il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o in un secondo momento da una versione precedente di .NET Framework, è necessario eseguire le attività seguenti per assicurarsi che la soluzione possa essere eseguita nel computer di sviluppo e nei computer degli utenti finali:  
  
-   Rimuovere l'oggetto <xref:System.Security.SecurityTransparentAttribute> dal progetto se è stato aggiornato da Visual Studio 2008.  
  
-   Eseguire un **Pulisci** comando in Visual Studio per essere in grado di eseguire il debug del progetto nel computer di sviluppo.  
  
-   Aggiornare il prerequisito di .NET Framework per il progetto.  
  
-   Gli utenti finali devono anche reinstallare la soluzione se in precedenza è stata distribuita con ClickOnce prima dell'impostazione di un framework di destinazione diverso.  
  
 Per altre informazioni su queste attività, vedere le sezioni corrispondenti riportate di seguito.  
  
## <a name="removing-the-securitytransparent-attribute-from-projects-that-you-upgrade-from-visual-studio-2008"></a>Rimozione dell'attributo SecurityTransparent da progetti aggiornati da Visual Studio 2008  
 Se si aggiorna un progetto di Office da Visual Studio 2008 e il framework di destinazione del progetto viene successivamente modificato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario rimuovere <xref:System.Security.SecurityTransparentAttribute> dal progetto. Visual Studio non rimuove automaticamente questo attributo. Se non si rimuove questo attributo, viene visualizzato un messaggio di errore quando si compila il progetto.  
  
 Per ulteriori informazioni sulle condizioni in cui Visual Studio è possibile modificare il framework di destinazione di un progetto aggiornato per il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], vedere [l'aggiornamento e migrazione di soluzioni Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
#### <a name="to-remove-the-securitytransparentattribute"></a>Per rimuovere SecurityTransparentAttribute  
  
1.  Con il progetto aperto in Visual Studio, aprire **Esplora soluzioni**.  
  
2.  Nel nodo **Proprietà** (per C#) o **Progetto personale** (per Visual Basic) fare doppio clic sul file di codice AssemblyInfo per aprirlo nell'editor di codice.  
  
    > [!NOTE]  
    >  Per visualizzare il file di codice AssemblyInfo nei progetti di Visual Basic, è necessario fare clic sul pulsante **Mostra tutti i file** in **Esplora soluzioni** .  
  
3.  Individuare <xref:System.Security.SecurityTransparentAttribute> e rimuoverlo dal file o impostarlo come commento.  
  
    ```vb  
    <Assembly: SecurityTransparent()>  
    ```  
  
    ```csharp  
    [assembly: SecurityTransparent()]  
    ```  
  
## <a name="performing-the-clean-command-to-debug-or-run-a-project-on-the-development-computer"></a>Esecuzione del comando Pulisci per eseguire il debug o eseguire un progetto nel computer di sviluppo  
 Se un progetto di Office è stato creato prima di modificata il framework di destinazione del progetto per il [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario eseguire un **Pulisci** comandi e quindi ricompilare il progetto dopo la modifica del framework di destinazione. Se non si esegue un **Pulisci** comando, si riceverà un <xref:System.Runtime.InteropServices.COMException> quando si tenta di eseguire il debug o eseguire il progetto con.  
  
 Per ulteriori informazioni sul **Pulisci** command, vedere [compilazione di soluzioni Office](../vsto/building-office-solutions.md).  
  
## <a name="updating-the-prerequisites-for-deployment"></a>Aggiornamento dei prerequisiti per la distribuzione  
 Quando si destina un progetto di Office per [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario aggiornare anche il prerequisito di .NET Framework corrispondente nel **prerequisiti** la finestra di dialogo. In caso contrario, i controlli di progetto limited di InstallShield la distribuzione ClickOnce o per e installa una versione precedente di .NET Framework.  
  
 Per ulteriori informazioni sull'aggiornamento dei prerequisiti per la distribuzione ai computer degli utenti finali, vedere [procedura: installare i prerequisiti nei computer degli utenti finali per eseguire soluzioni Office](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
## <a name="reinstalling-solutions-on-end-user-computers"></a>Reinstallazione di soluzioni nei computer degli utenti finali  
 Se si usa ClickOnce per distribuire una soluzione Office destinata a .NET Framework 3.5 e quindi si modifica la destinazione del progetto a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, gli utenti finali devono disinstallare la soluzione e reinstallarla dopo averla ripubblicata. Se si ripubblica la soluzione di cui è stata reimpostata la destinazione e la soluzione viene aggiornata nei computer degli utenti finali, questi ultimi riceveranno un'eccezione <xref:System.Runtime.InteropServices.COMException> all'esecuzione della soluzione aggiornata.  
  
## <a name="see-also"></a>Vedere anche  
 [Migrazione di soluzioni Office a .NET Framework 4 o versioni successive](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
  
  