---
title: 'Procedura: Firmare manifesti dell''applicazione e di distribuzione | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- manifests [Visual Studio]
- code signing [Visual Studio], Authenticode
- deployment manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- ClickOnce deployment [Visual Studio], signing assemblies
- key files [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 64173505-8bfb-41cf-a0de-b9075173f3a2
caps.latest.revision: "58"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0ca5caa822108d5a6417e69f827e1ba754b0d105
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-sign-application-and-deployment-manifests"></a>Procedura: firmare manifesti dell'applicazione e di distribuzione
Se si vuole pubblicare un'applicazione tramite la distribuzione ClickOnce, i manifesti dell'applicazione e di distribuzione devono essere firmati con una coppia di chiavi pubblica/privata e tramite la tecnologia Authenticode. È possibile firmare i manifesti con un certificato dall'archivio certificati di Windows o un file di chiave.  
  
 Per altre informazioni sulla distribuzione ClickOnce, vedere [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md) (Sicurezza e distribuzione ClickOnce).  
  
 La firma dei manifesti ClickOnce è facoltativa per le applicazioni basate su file con estensione EXE. Per altre informazioni, vedere la sezione "Creazione di manifesti non firmati" di questo documento.  
  
 Per altre informazioni sulla creazione di file di chiave, vedere [Procedura: Creare una coppia di chiavi pubblica/privata](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair).  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] supporta solo file di chiave Scambio informazioni personali con estensione PFX. È possibile tuttavia selezionare altri tipi di certificati dall'archivio certificati di Windows dell'utente corrente, facendo clic su **Seleziona da archivio** nella pagina **Firma** delle proprietà del progetto.  
  
### <a name="to-sign-application-and-deployment-manifests-using-a-certificate"></a>Per firmare manifesti dell'applicazione e di distribuzione usando un certificato  
  
1.  Aprire la finestra delle proprietà del progetto (fare clic con il pulsante destro del mouse sul nodo del progetto in **Esplora soluzioni** e scegliere **Proprietà** o digitare **proprietà del progetto** nella finestra **Avvio veloce** oppure premere ALT+INVIO nella finestra **Esplora soluzioni**). Nella scheda **Firma**, selezionare la casella di controllo **Firma i manifesti ClickOnce**.  
  
2.  Fare clic sul pulsante **Seleziona da archivio**.  
  
     Viene visualizzata la finestra di dialogo **Seleziona un certificato** con il contenuto dell'archivio certificati di Windows.  
  
    > [!TIP]
    >  Se si fa clic su **Fare clic qui per le proprietà del certificato**, viene visualizzata la finestra di dialogo **Dettagli del certificato**. Questa finestra di dialogo contiene informazioni dettagliate sul certificato e opzioni aggiuntive. È possibile fare clic su **Certificati** per visualizzare altre informazioni della Guida.  
  
3.  Selezionare il certificato che si vuole usare per firmare i manifesti.  
  
4.  È possibile anche specificare l'indirizzo di un server di timestamp nella casella di testo **URL del server di timestamp**. Questo server indica quando è stato firmato il manifesto.  
  
### <a name="to-sign-application-and-deployment-manifests-using-an-existing-key-file"></a>Per firmare manifesti dell'applicazione e di distribuzione tramite un file di chiave esistente  
  
1.  Nella pagina **Firma** selezionare la casella di controllo **Firma i manifesti ClickOnce**.  
  
2.  Fare clic sul pulsante **Seleziona da file**.  
  
     Verrà visualizzata la finestra di dialogo **Seleziona file**.  
  
3.  Nella finestra di dialogo **Seleziona file** individuare la posizione del file di chiave (PFX) che si vuole usare e scegliere **Apri**.  
  
    > [!NOTE]
    >  Questa opzione supporta solo file con estensione PFX. Se il file di chiave o il certificato sono in un altro formato, archiviarlo nell'archivio certificati di Windows e selezionare il certificato come illustrato nella procedura precedente. Nei requisiti del certificato selezionato deve essere inclusa la firma del codice.  
  
     Viene visualizzata la finestra di dialogo **Immettere la password per aprire il file**. Se il file PFX è già archiviato nell'archivio dei certificati di Windows oppure non è protetto da password, non verrà richiesto di digitare una password.  
  
4.  Immettere la password per accedere al file di chiave e premere INVIO.  
  
### <a name="to-sign-application-and-deployment-manifests-using-a-test-certificate"></a>Per firmare manifesti dell'applicazione e di distribuzione tramite un certificato di test  
  
1.  Nella pagina **Firma** selezionare la casella di controllo **Firma i manifesti ClickOnce**.  
  
2.  Per creare un nuovo certificato per il test, fare clic sul pulsante **Crea certificato di prova**.  
  
3.  Nella finestra di dialogo **Crea certificato di prova** immettere una password per proteggere il certificato.  
  
## <a name="generating-unsigned-manifests"></a>Creazione di manifesti non firmati  
 La firma dei manifesti ClickOnce è facoltativa per le applicazioni basate su file con estensione EXE. Le procedure seguenti illustrano come creare manifesti ClickOnce non firmati.  
  
> [!IMPORTANT]
>  I manifesti non firmati possono semplificare lo sviluppo e test dell'applicazione. I manifesti non firmati tuttavia comportano notevoli rischi di sicurezza in un ambiente di produzione. È consigliabile usare i manifesti non firmati solo se l'applicazione ClickOnce viene eseguita nei computer all'interno di una rete intranet che è completamente isolata da internet o da altre origini di codice dannoso.  
  
 Per impostazione predefinita, ClickOnce genera automaticamente manifesti firmati, a meno che uno o più file sono esplicitamente esclusi dall'hash creato. In altre parole, la pubblicazione dell'applicazione crea manifesti firmati se tutti i file sono inclusi nell'hash, anche quando la casella di controllo **Firma i manifesti ClickOnce** non è selezionata.  
  
#### <a name="to-generate-unsigned-manifests-and-include-all-files-in-the-generated-hash"></a>Per generare manifesti non firmati e includere tutti i file nell'hash creato  
  
1.  Per generare manifesti non firmati che includono tutti i file nell'hash, è necessario prima pubblicare l'applicazione insieme ai manifesti firmati. Pertanto, firmare prima i manifesti ClickOnce seguendo una delle procedure precedenti e quindi pubblicare l'applicazione.  
  
2.  Nella pagina **Firma** deselezionare la casella di controllo **Firma i manifesti ClickOnce**.  
  
3.  Reimpostare la versione di pubblicazione in modo che solo una versione dell'applicazione sia disponibile. Per impostazione predefinita, Visual Studio incrementa automaticamente il numero di revisione della versione di pubblicazione ogni volta che si pubblica un'applicazione. Per altre informazioni vedere [How to: Set the ClickOnce Publish Version](../deployment/how-to-set-the-clickonce-publish-version.md) (Procedura: Reimpostare la versione di pubblicazione ClickOnce).  
  
4.  Pubblicare l'applicazione.  
  
#### <a name="to-generate-unsigned-manifests-and-exclude-one-or-more-files-from-the-generated-hash"></a>Per generare manifesti non firmati ed escludere uno o più file dall'hash creato  
  
1.  Nella pagina **Firma** deselezionare la casella di controllo **Firma i manifesti ClickOnce**.  
  
2.  Aprire la finestra di dialogo **File dell'applicazione** e impostare **Hash** a **Escludi** per i file che si vuole escludere dall'hash creato.  
  
    > [!NOTE]
    >  L'esclusione di un file dall'hash configura ClickOnce per disattivare la firma automatica dei manifesti, pertanto non è necessario pubblicare prima l'applicazione con manifesti firmati, come illustrato nella procedura precedente.  
  
3.  Pubblicare l'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Assembly con nomi sicuri](/dotnet/framework/app-domains/strong-named-assemblies)   
 [Procedura: Creare una coppia di chiavi pubblica/privata](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair)   
 [Pagina Firma, Creazione progetti](../ide/reference/signing-page-project-designer.md)   
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)