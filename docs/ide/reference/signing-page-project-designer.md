---
title: Pagina Firma, Creazione progetti | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.AddNewStrongNameKey
- ResolveKeySource.KeyFileForSignAssemblyNotImported
- vb.ProjectPropertiesSigning.ChangePasswordDialog
- ResolveKeySource.KeyFileForManifestNotImported
- vb.ProjectPropertiesSigning
- vb.ProjectPropertiesSigning.PasswordNeededDialog
- vb.ProjectPropertiesSigning.PfxPasswordDialog
helpviewer_keywords:
- Project Designer, Signing page
- Signing page in Project Designer
ms.assetid: dab3ba13-2f92-4827-92bd-1be3c35bc48b
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 53fe343002de3f89431927c95f36a0c092b36c2c
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/29/2018
---
# <a name="signing-page-project-designer"></a>Pagina Firma, Progettazione progetti
Usare la pagina **Firma** di **Creazione progetti** per firmare i manifesti dell'applicazione e di distribuzione, nonché l'assembly (firma con nome sicuro).  
  
 La firma dei manifesti dell'applicazione e di distribuzione è un processo distinto dalla firma di un assembly, anche se entrambe le attività vengono eseguite nella pagina **Firma**.  
  
 L'archiviazione delle informazioni relative al file di chiave, poi, è diversa per la firma dei manifesti e per la firma degli assembly. Per la firma dei manifesti, le informazioni sulla chiave vengono archiviate nel database dell'archivio di crittografia del computer e nell'archivio dei certificati di Windows dell'utente corrente. Per la firma degli assembly, le informazioni sulla chiave vengono archiviate esclusivamente nel database dell'archivio di crittografia del computer.  
  
 Per accedere alla pagina **Firma**, selezionare un nodo di progetto in **Esplora soluzioni** e quindi scegliere **Proprietà** dal menu **Progetto**. Quando viene visualizzata la finestra **Creazione progetti**, fare clic sulla scheda **Firma**.  
  
## <a name="application-and-deployment-manifest-signing"></a>Firma del manifesto di applicazione e distribuzione  
 Casella di controllo **Firma i manifesti ClickOnce**  
 Selezionare questa casella di controllo per firmare i manifesti dell'applicazione e di distribuzione con una coppia di chiavi pubblica/privata. Per altre informazioni su questa operazione, vedere [Procedura: firmare manifesti dell'applicazione e di distribuzione](../../ide/how-to-sign-application-and-deployment-manifests.md).  
  
 Pulsante **Seleziona dall'archivio**  
 Consente di selezionare un certificato esistente dall'archivio dei certificati personali dell'utente corrente. È possibile selezionare uno dei certificati disponibili per firmare i manifesti di distribuzione e dell'applicazione.  
  
 Se si fa clic su **Seleziona dall'archivio**, viene aperta la finestra di dialogo **Seleziona un certificato**, che elenca i certificati validi (non scaduti) presenti nell'archivio personale che dispongono di chiavi private. Lo scopo del certificato selezionato deve prevedere la firma di codice.  
  
 Se si fa clic su **view certificate properties** (Fare clic qui per visualizzare le proprietà del certificato), viene visualizzata la finestra di dialogo **Dettagli del certificato**. Questa finestra di dialogo contiene informazioni dettagliate sul certificato e opzioni aggiuntive. È possibile fare clic su **Altre informazioni sui certificati** per visualizzare altre informazioni della Guida.  
  
 Pulsante **Seleziona da un file**  
 Consente di selezionare un certificato da un file di chiave esistente.  
  
 Se si fa clic su **Seleziona da un file**, si apre la finestra di dialogo **Seleziona file**, che consente di selezionare un file della chiave del certificato (con estensione pfx). Il file deve essere protetto da password e non può essere già presente nell'archivio dei certificati personali.  
  
 Nella finestra di dialogo **Immettere la password per aprire il file** immettere la password per aprire il file della chiave del certificato (con estensione pfx). Le informazioni sulla password vengono archiviate nell'elenco dei contenitori di chiavi personali e nell'archivio certificati personale.  
  
 Pulsante **Crea certificato di prova**  
 Consente di creare un certificato per il test. Questo certificato viene usato per firmare l'applicazione ClickOnce e i manifesti di distribuzione.  
  
 Se si fa clic su **Crea certificato di prova**, si apre la finestra di dialogo **Crea certificato di prova**, in cui è possibile digitare una password per il file di chiave con nome sicuro relativo al certificato di prova. Al file viene assegnato il nome *NomeProgetto*_TemporaryKey. pfx. Se si fa clic su **OK** senza digitare alcuna password, il file con estensione pfx non è protetto da password.  
  
 Casella **URL server di timestamp**  
 Specifica l'indirizzo di un server che genera il timestamp della firma. Quando si fornisce un certificato, questo sito esterno verifica l'ora in cui l'applicazione viene firmata.  
  
## <a name="assembly-signing"></a>Firma degli assembly  
 Casella di controllo **Firma assembly**  
 Selezionare questa casella di controllo per firmare l'assembly e creare un file di chiave con nome sicuro. Per altre informazioni sulla firma dell'assembly tramite **Creazione progetti**, vedere [Procedura: firmare un assembly (Visual Studio)](../managing-assembly-and-manifest-signing.md#how-to-sign-an-assembly-in-visual-studio).  
  
 Questa opzione usa lo strumento Al.exe fornito da [!INCLUDE[winsdklong](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name).  
  
 Elenco **Scegliere un file di chiave con nome sicuro**  
 Consente di specificare un file di chiave nuovo o esistente con nome sicuro da usare per firmare l'assembly. Selezionare **\<Sfoglia...>** per selezionare un file di chiave esistente.  
  
 Selezionare **\<Nuovo...>** per creare un nuovo file di chiave con cui firmare l'assembly. Verrà visualizzata la finestra di dialogo **Crea chiave con nome sicuro**, che è possibile usare per specificare il nome di un file di chiave e proteggere il file con una password. La password deve avere una lunghezza di almeno 6 caratteri. Se si specifica una password, viene creato un file di scambio di informazioni personali (con estensione pfx, Personal inFormation eXchange). Se non si specifica una password, viene creato un file di chiave con nome sicuro (con estensione snk).  
  
 Pulsante **Cambia password**  
 Consente di modificare la password del file di chiave con estensione pfx usato per firmare l'assembly.  
  
 Se si fa clic su **Cambia password** si apre la finestra di dialogo **Modifica password chiave**. In questa finestra di dialogo il campo **Vecchia password** contiene la password corrente per il file di chiave. La **Nuova password** deve avere una lunghezza di almeno 6 caratteri. Le informazioni relative alla password vengono archiviate nell'archivio certificati Windows dell'utente corrente.  
  
 Casella di controllo **Solo firma ritardata**  
 Selezionare questa casella di controllo per abilitare la firma ritardata.  
  
 Si tenga presente che un progetto con firma ritardata non può essere eseguito e non può essere sottoposto a debug. È tuttavia possibile evitare la verifica durante lo sviluppo usando [Sn.exe (strumento Nome sicuro)](/dotnet/framework/tools/sn-exe-strong-name-tool) con l'opzione `-Vr`.  
  
> [!NOTE]
>  Quando si firma un assembly, non sempre è possibile accedere a una chiave privata. Ad esempio, un'organizzazione può avere una coppia di chiavi ben protetta a cui gli sviluppatori non hanno accesso su base giornaliera. La chiave pubblica è disponibile ma l'accesso alla chiave privata è limitato a poche persone. In un caso del genere, è possibile usare una firma *ritardata* o *parziale*. Questa funzione consente di fornire la chiave pubblica, rimandando l'aggiunta della chiave privata al momento della consegna dell'assembly.  
  
## <a name="see-also"></a>Vedere anche

[Riferimenti alle proprietà di progetto](../../ide/reference/project-properties-reference.md)  
[Gestione delle firme di assembly e manifesti](../../ide/managing-assembly-and-manifest-signing.md)  
[Procedura: Firmare manifesti dell'applicazione e di distribuzione](../../ide/how-to-sign-application-and-deployment-manifests.md)  
[Procedura: firmare un assembly (Visual Studio)](../managing-assembly-and-manifest-signing.md#how-to-sign-an-assembly-in-visual-studio)  
[Procedura: Firmare un assembly con un nome sicuro](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name)  
[Assembly con nomi sicuri](/dotnet/framework/app-domains/strong-named-assemblies) 