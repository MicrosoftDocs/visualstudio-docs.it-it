---
title: Distribuzione MSI e VSIX di un linguaggio DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 0c17ac476e0edbec73c407090cd84e6a44d9219c
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="msi-and-vsix-deployment-of-a-dsl"></a>Distribuzione MSI e VSIX di un linguaggio DSL
È possibile installare un linguaggio specifico di dominio nel proprio computer o in altri computer. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] deve essere già installato nel computer di destinazione.

##  <a name="which"></a> Scelta tra VSIX e MSI distribuzione
 Esistono due metodi di distribuzione di un linguaggio specifico di dominio:

|Metodo|Vantaggi|
|------------|--------------|
|VSX ([!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estensione)|Molto facile da distribuire: copia ed eseguire il **VSIX** file dal progetto DslPackage.<br /><br /> Per ulteriori informazioni vedere [installazione e disinstallazione di un linguaggio DSL utilizzando il VSX](#Installing).|
|MSI (file di programma di installazione)|-Consente all'utente di aprire [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] facendo doppio clic su un file DSL.<br />-Consente di associare un'icona con il tipo di file DSL nel computer di destinazione.<br />-Associa uno schema XSD (XML schema) con il tipo di file DSL. Ciò consente di evitare gli avvisi quando viene caricato il file [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].<br /><br /> È necessario aggiungere un progetto di installazione alla soluzione per creare un file MSI.<br /><br /> Per ulteriori informazioni, vedere [la distribuzione di un linguaggio DSL utilizzando un file con estensione MSI](#msi).|

##  <a name="Installing"></a> Installazione e disinstallazione di un linguaggio DSL utilizzando il VSX
 Quando il modello DSL viene installato da questo metodo, l'utente può aprire un file DSL dall'interno [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ma non è possibile aprire il file da Esplora risorse.

#### <a name="to-install-a-dsl-by-using-the-vsx"></a>Per installare un linguaggio DSL utilizzando il VSX

1.  Nel computer, trovare il **VSIX** file compilato dal progetto di pacchetto DSL.

    1.  In **Esplora**, fare doppio clic su di **DslPackage** del progetto e quindi fare clic su **Apri cartella in Esplora risorse**.

    2.  Individuare il file **bin\\\*\\***YourProject***. DslPackage.vsix**

2.  Copia il **VSIX** file nel computer di destinazione in cui si desidera installare del linguaggio DSL. Può trattarsi del computer in uso o di un altro computer.

    -   Nel computer di destinazione deve essere una delle edizioni di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] DSL che supporta in fase di esecuzione. Per ulteriori informazioni, vedere [supportati edizioni di Visual Studio per Visualization and Modeling SDK](../modeling/supported-visual-studio-editions-for-visualization-amp-modeling-sdk.md).

    -   Nel computer di destinazione deve essere una delle edizioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] specificato in **DslPackage\source.extensions.manifest**.

3.  Nel computer di destinazione, fare doppio clic su di **VSIX** file.

     **Visual Studio Extension Installer** si apre e installa l'estensione.

4.  Avviare o riavviare [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].

5.  Per eseguire il test del linguaggio DSL, utilizzare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per creare un nuovo file con estensione definito per il modello DSL.

#### <a name="to-uninstall-a-dsl-that-was-installed-by-using-vsx"></a>Per disinstallare un linguaggio DSL che è stato installato tramite VSX

1.  Nel **strumenti** menu, fare clic su **Extension Manager**.

2.  Espandere **Estensioni installate**.

3.  Selezionare l'estensione in cui è definito il DSL e quindi fare clic su **Disinstalla**.

 Raramente, un'estensione errata non viene caricata e crea un report nella finestra degli errori, ma non viene visualizzata in Gestione estensioni. In tal caso, è possibile rimuovere l'estensione eliminando il file da:

 *LocalAppData* **\Microsoft\VisualStudio\10.0\Extensions**

##  <a name="msi"></a> Distribuzione di un linguaggio DSL in un file MSI
 Mediante la definizione di un file MSI (programma di installazione di Windows) per il modello DSL, è possibile consentire agli utenti di aprire file DSL da Esplora risorse. Con l'estensione del nome file, è anche possibile associare un'icona e una breve descrizione. Inoltre, il file MSI è possibile installare uno schema XSD che può essere utilizzato per convalidare i file DSL. Se si desidera, è possibile aggiungere altri componenti in MSI che verranno installato nello stesso momento.

 Per ulteriori informazioni sulle altre opzioni di distribuzione e i file MSI, vedere [distribuzione di applicazioni, servizi e componenti](../deployment/deploying-applications-services-and-components.md).

 Per compilare un file MSI, si aggiunge un progetto di installazione per il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] soluzione. Il metodo di creazione di un progetto di installazione più semplice consiste nell'utilizzare il modello CreateMsiSetupProject.tt, che è possibile scaricare dal [sito VMSDK](http://go.microsoft.com/fwlink/?LinkID=186128).

#### <a name="to-deploy-a-dsl-in-an-msi"></a>Per distribuire un linguaggio DSL in un file MSI

1.  Impostare `InstalledByMsi` nel manifesto dell'estensione. Ciò impedisce il VSX viene installato e disinstallato tranne per il file MSI. Questo è importante se si include altri componenti in MSI.

    1.  Open DslPackage\source.extension.tt

    2.  Inserire la riga seguente prima di `<SupportedProducts>`:

        ```
        <InstalledByMsi>true</InstalledByMsi>
        ```

2.  Creare o modificare un'icona che rappresenta il modello DSL in Esplora risorse. Ad esempio, modificare **DslPackage\Resources\File.ico**

3.  Assicurarsi che i seguenti attributi di tale linguaggio DSL siano corretti:

    -   In Esplora DSL fare clic sul nodo radice e nella finestra Proprietà controllare:

        -   Descrizione

        -   Versione

    -   Fare clic su di **Editor** nodo e nella finestra Proprietà fare clic su **icona**. Impostare il valore per fare riferimento a un file dell'icona nel **DslPackage\Resources**, ad esempio **File.ico**

    -   Nel **compilare** menu aprirlo **Configuration Manager**e selezionare la configurazione che si desidera compilare, ad esempio **versione** o **Debug** .

4.  Passare a [home page di Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)e dal **Scarica** scheda, scaricare **CreateMsiSetupProject.tt**.

5.  Aggiungere **CreateMsiSetupProject.tt** al progetto Dsl.

     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verrà creato un file denominato **CreateMsiSetupProject.vdproj**.

6.  In Esplora risorse, la copia Dsl\\\*.vdproj in una nuova cartella denominata il programma di installazione.

     (Se si desidera, è possibile ora escludere CreateMsiSetupProject.tt dal progetto Dsl.)

7.  In **Esplora**, aggiungere **installazione\\\*con estensione vdproj** di un progetto esistente.

8.  Nel **progetto** menu, fare clic su **dipendenze progetto**.

     Nel **dipendenze progetto** finestra di dialogo, selezionare il progetto di installazione.

     Selezionare la casella accanto a **DslPackage**.

9. Ricompilare la soluzione.

10. In Esplora risorse, individuare il file MSI generato nel progetto di installazione.

     Copiare il file con estensione MSI in un computer in cui si desidera installare il modello DSL. Fare doppio clic sul file con estensione MSI. Viene eseguito il programma di installazione.

11. Nel computer di destinazione, creare un nuovo file con l'estensione del file di tale linguaggio DSL. Verificare che:

    -   Nella visualizzazione elenco in Esplora risorse, il file viene visualizzato con un'icona e la descrizione è definito.

    -   Quando si fa doppio clic su file, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] avvia e apre il file DSL nell'editor di linguaggio DSL.

 Se si preferisce, è possibile creare il progetto di installazione manualmente, anziché utilizzare il modello di testo. Per una procedura dettagliata che include la procedura vedere il capitolo 5 del [di visualizzazione e modellazione Lab SDK](http://go.microsoft.com/fwlink/?LinkId=208878).

#### <a name="to-uninstall-a-dsl-that-was-installed-from-an-msi"></a>Per disinstallare un linguaggio DSL che è stato installato da un file MSI

1.  In Windows, aprire il **programmi e funzionalità** Pannello di controllo.

2.  La disinstallazione del linguaggio DSL.

3.  Riavviare Visual Studio.