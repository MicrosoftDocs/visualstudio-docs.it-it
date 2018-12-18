---
title: 'Procedura dettagliata: Creazione di un servizio di linguaggio Legacy | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 660d33dd2d5c46d8020172c1fcf74bfb64b43360
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Procedura dettagliata: Creazione di un servizio di linguaggio Legacy
Utilizzando le classi di pacchetto gestito (MPF) framework language per implementare un servizio di linguaggio in [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] è semplice. È necessario un pacchetto VSPackage per ospitare il servizio di linguaggio, il servizio di linguaggio stesso e un parser per la propria lingua.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Posizioni del modello di progetto di pacchetto di Visual Studio  
 Il modello di progetto di Visual Studio pacchetto sono disponibili in tre posizioni di modelli diversi nel **nuovo progetto** la finestra di dialogo:  
  
1.  Nella sezione relativa all'estendibilità di Visual Basic. Il linguaggio predefinito del progetto è Visual Basic.  
  
2.  Nella sezione relativa all'estendibilità di C#. Il linguaggio predefinito del progetto è C#.  
  
3.  Nella sezione relativa all'estendibilità di altri tipi di progetto. Il linguaggio predefinito del progetto è C++.  
  
### <a name="create-a-vspackage"></a>Creare un pacchetto VSPackage  
  
1.  Creare un nuovo VSPackage con il modello di progetto di pacchetto di Visual Studio.  
  
     Se si aggiunge un servizio di linguaggio a un VSPackage esistente, ignorare i passaggi seguenti e passare direttamente alla procedura "Creare la classe di servizio Language".  
  
2.  Immettere MyLanguagePackage per il nome del progetto e fare clic su **OK**.  
  
     È possibile utilizzare qualsiasi nome desiderato. Descritti in questa sezione presuppongono MyLanguagePackage come nome.  
  
3.  Selezionare [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] come lingua e l'opzione per generare un nuovo file di chiave. Scegliere **Avanti**.  
  
4.  Immettere le informazioni aziendali e di pacchetto appropriate. Scegliere **Avanti**.  
  
5.  Selezionare **comando di Menu**. Scegliere **Avanti**.  
  
     Se non si intende supportare i frammenti di codice, è possibile semplicemente fare clic su Fine e ignorare il passaggio successivo.  
  
6.  Immettere **Inserisci frammento di codice** come il **nome del comando** e `cmdidInsertSnippet` per il **ID di comando**. Scegliere **Fine**.  
  
     Il **nome comando** e **ID di comando** può essere qualsiasi, questi sono soltanto esempi.  
  
### <a name="create-the-language-service-class"></a>Creare la classe di servizio di linguaggio  
  
1.  In **Esplora**, pulsante destro del mouse sul progetto MyLanguagePackage, scegliere **Aggiungi**, **riferimento**, quindi scegliere il **Aggiungi nuovo riferimento** pulsante.  
  
2.  Nel **Aggiungi riferimento** nella finestra di dialogo **Microsoft.VisualStudio.Package.LanguageService** nel **.NET** scheda e fare clic su **OK**.  
  
     Questa operazione deve essere eseguita solo una volta per il progetto di pacchetto di linguaggio.  
  
3.  In **Esplora**del mouse sul progetto VSPackage e scegliere **Aggiungi**, **classe**.  
  
4.  Assicurarsi che **classe** è selezionata nell'elenco di modelli.  
  
5.  Immettere **MyLanguageService.cs** per il nome del file di classe e fare clic su **Aggiungi**.  
  
     È possibile utilizzare qualsiasi nome desiderato. Descritti in questa sezione presuppongono `MyLanguageService` come nome.  
  
6.  Nel file MyLanguageService.cs, aggiungere le seguenti `using` istruzioni.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]  
  
7.  Modificare il `MyLanguageService` classe da cui derivare la <xref:Microsoft.VisualStudio.Package.LanguageService> classe:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]  
  
8.  Posizionare il cursore in "LanguageService" e dal **modifica**, **IntelliSense** dal menu **implementa classe astratta**. Aggiunge i metodi minimi necessari per implementare una classe di servizio di linguaggio.  
  
9. Implementare i metodi astratti, come descritto in [per implementare un servizio di linguaggio Legacy](../../extensibility/internals/implementing-a-legacy-language-service2.md).  
  
### <a name="register-the-language-service"></a>Registrare il servizio di linguaggio  
  
1.  Aprire il file MyLanguagePackagePackage.cs e aggiungere le seguenti `using` istruzioni:  
  
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]  
  
2.  Registrare la classe di servizio di linguaggio, come descritto in [la registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md). Sono inclusi attributi ProvideXX e nelle sezioni "Proffering del servizio di linguaggio". Utilizzare in questo argomento utilizza TestLanguageService MyLanguageService.  
  
### <a name="the-parser-and-scanner"></a>Il Parser e Scanner  
  
1.  Implementare un parser e scanner per la lingua, come descritto in [Parser servizio di linguaggio Legacy e Scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
     Modalità di implementazione il parser e lo scanner è e non rientra nell'ambito di questo argomento.  
  
## <a name="language-service-features"></a>Funzionalità del linguaggio  
 Per implementare ogni funzionalità nel servizio di linguaggio, in genere una classe derivata dalla classe servizio di linguaggio MPF appropriata, implementare i metodi astratti in base alle esigenze e l'override dei metodi appropriati. Le classi creare e/o derivare da è dipende dalle funzionalità di cui si intende supportare. Queste funzionalità sono descritti in dettaglio in [le funzionalità del servizio di linguaggio Legacy](../../extensibility/internals/legacy-language-service-features1.md). La procedura seguente è l'approccio generale per una classe di derivazione dalle classi MPF.  
  
#### <a name="deriving-from-an-mpf-class"></a>Derivazione da una classe MPF  
  
1.  In **Esplora**del mouse sul progetto VSPackage e scegliere **Aggiungi**, **classe**.  
  
2.  Assicurarsi che **classe** è selezionata nell'elenco di modelli.  
  
     Immettere un nome appropriato per il file di classe e fare clic su **Aggiungi**.  
  
3.  Nel nuovo file di classe, aggiungere le seguenti `using` istruzioni.  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]  
  
4.  Modificare la classe da cui derivare la classe MPF desiderata.  
  
5.  Aggiungere un costruttore di classe che accetta almeno gli stessi parametri del costruttore della classe di base e passare i parametri del costruttore al costruttore della classe base.  
  
     Ad esempio, il costruttore per una classe derivata dalla <xref:Microsoft.VisualStudio.Package.Source> classe potrebbe essere simile al seguente:  
  
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]  
  
6.  Dal **modifica**, **IntelliSense** dal menu **implementa classe astratta** se la classe di base dispone di metodi astratti che devono essere implementati.  
  
7.  In caso contrario, posizionare il cursore all'interno della classe e immettere il metodo da sottoporre a override.  
  
     Ad esempio, digitare `public override` per visualizzare un elenco di tutti i metodi che possono essere sostituite in tale classe.  
  
## <a name="see-also"></a>Vedere anche  
 [Implementazione di un servizio di linguaggio Legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)