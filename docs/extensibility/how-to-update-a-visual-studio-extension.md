---
title: 'Procedura: aggiornare un''estensione di Visual Studio | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 46b540f1c5ba5b345464948170287d2b354b7a0e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-update-a-visual-studio-extension"></a>Procedura: aggiornare un'estensione di Visual Studio
È possibile aggiornare un'estensione di Visual Studio nel sistema tramite **estensioni e aggiornamenti** per installare la versione aggiornata. Se si crea una versione aggiornata di un'estensione, è possibile indicare come aggiornamento incrementando il numero di versione nel manifesto VSIX.  
  
 Gli aggiornamenti vengono installati quando il manifesto VSIX dell'estensione in ingresso ha lo stesso `ID` come quello installato e un valore più alto `Version` numero. Se il `Version` numero è uguale o inferiore, il pacchetto non può essere installato. Se il `ID` valori non corrispondono, il pacchetto che non è ancora stato installato è riconosciuto come un'estensione diversa.  
  
 Per evitare conflitti durante lo sviluppo, è consigliabile disinstallare le versioni precedenti delle estensioni in corso e anche disinstallare o disabilitare tutte le altre estensioni potenzialmente in conflitto.  
  
### <a name="to-update-an-extension-on-your-system"></a>Per aggiornare un'estensione del sistema  
  
1.  Nel menu **Strumenti** fare clic su **Estensioni e aggiornamenti**.  
  
2.  Nel riquadro a sinistra, fare clic su **aggiornamenti**.  
  
3.  Nel riquadro centrale fare clic sull'aggiornamento che si desidera installare.  
  
     Il numero di versione dell'estensione aggiornata viene visualizzato nel riquadro di destra, insieme ad altre informazioni.  
  
4.  Nella parte inferiore del riquadro di destra, fare clic su **aggiornamento**.  
  
### <a name="to-publish-an-update-of-an-extension"></a>Per pubblicare un aggiornamento di un'estensione  
  
1.  In Visual Studio, aprire la soluzione per l'estensione che si desidera aggiornare. Apportare le modifiche.  
  
    > [!IMPORTANT]
    >  Senza segno che tutte le estensioni di utente non vengono aggiornate automaticamente. È consigliabile firmare sempre le estensioni.  
  
2.  In **Esplora**, aprire source.extension.manifest.  
  
3.  Nella finestra di progettazione manifesto, aumentare il valore del numero nel **versione** campo.  
  
4.  Salvare la soluzione e compilarla.  
  
5.  Caricare il nuovo file con estensione VSIX (nella cartella \bin\Debug\ del progetto) per il [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) sito Web.  
  
     Quando si apre un utente che dispone di una versione precedente dell'estensione **estensioni e aggiornamenti**, verrà visualizzata la nuova versione nel **aggiornamenti** elenco, a condizione che lo strumento è impostato per la ricerca di aggiornamenti.  
  
     È possibile abilitare o disabilitare il controllo automatico per gli aggiornamenti nella parte inferiore del **aggiornamenti** riquadro (**abilitare o disabilitare il rilevamento automatico degli aggiornamenti disponibili**), le modifiche di **cercare aggiornamenti** impostazione **Strumenti / opzioni / ambiente / estensioni e aggiornamenti**.  
  
    > [!NOTE]
    >  A partire da Visual Studio 2015 Update 2, è possibile specificare in **Strumenti / Opzioni / Ambiente / Estensioni e aggiornamenti** se gli aggiornamenti automatici devono essere installati per le estensioni per utente, per tutte le estensioni utente o entrambe le opzioni (impostazione predefinita).  
  
## <a name="see-also"></a>Vedere anche  
 [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Ricerca e uso delle estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
