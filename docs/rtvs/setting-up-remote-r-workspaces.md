---
title: Aree di lavoro remote con R Tools per Visual Studio | Microsoft Docs
description: Come configurare aree di lavoro R remote e connettersi a tale aree da Visual Studio.
ms.custom: 
ms.date: 12/04/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
dev_langs:
- R
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- data-science
ms.openlocfilehash: 52122b3b3a92ff7df292764e75175070e0b6b1db
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="setting-up-remote-workspaces"></a>Impostazione di aree di lavoro remote

In questo articolo viene illustrato come configurare un server remoto con SSL e un servizio R appropriato. Ciò consente a R Tools per Visual Studio (RTVS) di connettersi a un'area di lavoro remota su tale server.

- [Requisiti del computer remoto](#remote-computer-requirements)
- [Installare un certificato SSL](#install-an-ssl-certificate)
- [Installare un certificato SSL in Windows](#install-an-ssl-certificate-on-windows)
- [Installare un certificato SSL in Ubuntu](#install-an-ssl-certificate-on-ubuntu)
- [Installare i servizi R in Windows](#install-r-services-on-windows)
- [Installare i servizi R in Linux](#install-r-services-on-Linux)
- [Configurare i servizi R](#configure-r-services)
- [Risoluzione dei problemi](#troubleshooting)

## <a name="remote-computer-requirements"></a>Requisiti del computer remoto

- Windows 10, Windows Server 2016 o Windows Server 2012 R2. RTVS richiede anche
- [.NET framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) o versione successiva

## <a name="install-an-ssl-certificate"></a>Installare un certificato SSL

RTVS richiede che tutte le comunicazioni con un server remoto si svolgano tramite HTTP, che richiede un certificato SSL nel server. È possibile usare un certificato firmato da un'autorità di certificazione attendibile (scelta consigliata) o un certificato autofirmato. Con un certificato autofirmato RTVS genera avvisi al momento della connessione. In entrambi i casi è necessario installare il certificato nel computer e consentire l'accesso alla relativa chiave privata.

### <a name="obtaining-a-trusted-certificate"></a>Acquisizione di un certificato attendibile

Un certificato attendibile viene emesso da un'autorità di certificazione (per altre informazioni vedere [Certificate Authority su Wikipedia](https://en.wikipedia.org/wiki/Certificate_authority)). L'emissione di un certificato attendibile è paragonabile alla richiesta di un documento di identità. Come tale richiede vari passaggi e può comportare dei costi, ma verifica l'autenticità della richiesta e del richiedente.

Il campo chiave che deve essere presente nel certificato è il nome di dominio completo del computer server R. L'autorità di certificazione chiede di dimostrare che l'utente è autorizzato a creare un nuovo server per il dominio a cui appartiene il server.

Per altre informazioni, vedere [public key certificates](https://en.wikipedia.org/wiki/Public_key_certificate) (certificati chiave pubblica) su Wikipedia.

## <a name="install-an-ssl-certificate-on-windows"></a>Installare un certificato SSL in Windows

Il certificato SSL deve essere installato manualmente in Windows. Seguire le istruzioni riportate di seguito per installare un certificato SSL.

### <a name="obtaining-a-self-signed-certificate-windows"></a>Acquisizione di un certificato autofirmato (Windows)

Ignorare questa sezione se è disponibile un certificato attendibile. Rispetto a un certificato emesso da un'autorità attendibile, un certificato autofirmato è paragonabile a un'autocertificazione. Questo processo è sicuramente molto più semplice di quello che richiede l'intervento di un'autorità attendibile, ma l'autenticazione che garantisce è vulnerabile: un utente malintenzionato può sostituire il proprio certificato a quello autofirmato e acquisire tutto il traffico tra il client e il server. *È consigliabile quindi limitare l'uso dei certificati autofirmati a scenari di test su una rete attendibile e non usarli mai in fase di produzione.*

Per questo motivo in RTVS viene sempre visualizzato questo avviso al momento della connessione a un server con un certificato autofirmato:

![Finestra di dialogo di avviso per certificato autofirmato](media/workspaces-remote-self-signed-certificate-warning.png)

Per emettere un certificato autofirmato:

1. Accedere al computer server R con un account Administrator.
1. Aprire un nuovo prompt dei comandi amministratore di PowerShell ed eseguire il seguente comando, sostituendo a `"remote-machine-name"` il nome di dominio completo del computer server.

    ```ps
    New-SelfSignedCertificate -CertStoreLocation Cert:\LocalMachine\My -DnsName "remote-machine-name"
    ```

1. Se PowerShell non è mai stato eseguito nel computer server R, eseguire il comando riportato di seguito per abilitare l'esecuzione di comandi in modo esplicito:

    ```ps
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
    ```

Per informazioni, vedere [self-signed certificates](https://en.wikipedia.org/wiki/Self-signed_certificate) (certificati autofirmati) su Wikipedia.

### <a name="installing-the-certificate"></a>Installazione del certificato

Per installare il certificato nel computer remoto, eseguire `certlm.msc` (lo strumento di gestione certificati) da un prompt dei comandi. Fare clic con il pulsante destro del mouse sulla cartella **Personal** e selezionare il comando **All Tasks > Import** (Tutte le attività > Importa):

![Comando Import (Importa) per il certificato](media/workspaces-remote-certificate-import.png)

### <a name="granting-permissions-to-read-the-ssl-certificates-private-key"></a>Concessione delle autorizzazioni per la lettura della chiave privata del certificato SSL

Dopo aver importato il certificato, concedere all'account `NETWORK SERVICE` le autorizzazioni per la lettura della chiave privata, come indicato nelle istruzioni che seguono. `NETWORK_SERVICE` è l'account usato per l'esecuzione del broker dei servizi R, il servizio che termina le connessioni SSL in ingresso nel computer server.

1. Eseguire `certlm.msc` (lo strumento di gestione certificati) da un prompt dei comandi amministratore.
1. Espandere **Personal > Certificates** (Personale > Certificati), fare clic con il pulsante destro del mouse sul proprio certificato e selezionare **All Tasks > Manage Private Keys** (Tutte le attività > Gestisci chiavi private).
1. Fare clic con il pulsante destro del mouse sul certificato e selezionare il comando Manage Private Keys (Gestisci chiavi private) in All Tasks (Tutte le attività).
1. Nella finestra di dialogo visualizzata selezionare **Add** (Aggiungi) e immettere `NETWORK SERVICE` come nome dell'account:

    ![Finestra di dialogo Manage Private Keys (Aggiungi chiavi private), aggiunta di NETWORK_SERVICE](media/workspaces-remote-manage-private-key-dialog.png)

1. Selezionare **OK** due volte per chiudere le finestre di dialogo e salvare le modifiche.

## <a name="install-an-ssl-certificate-on-ubuntu"></a>Installare un certificato SSL in Ubuntu

Il pacchetto `rtvs-daemon` installerà un certificato autofirmato per impostazione predefinita come parte dell'installazione.

### <a name="obtaining-a-self-signed-certificate-ubuntu"></a>Acquisizione di un certificato autofirmato (Ubuntu)

Per informazioni sui vantaggi e i rischi dell'uso di un certificato autofirmato, vedere la descrizione per Windows. Il pacchetto `rtvs-daemon` genera e configura il certificato autofirmato durante l'installazione. È necessario eseguire questa operazione solo se si vuole sostituire il certificato autofirmato generato automaticamente.

Per emettere un certificato autofirmato:

1. Usare SSH o accedere al computer Linux.
1. Installare il pacchetto `ssl-cert`:
    ```sh
    sudo apt-get install ssl-cert
    ```
1. Eseguire `make-ssl-cert` per generare il certificato SSL autofirmato predefinito:
    ```sh
    sudo make-ssl-cert generate-default-snakeoil --force-overwrite
    ```
1. Convertire la chiave e i file PME generati in PFX. Il file PFX generato deve essere nella home directory:
    ```sh
    openssl pkcs12 -export -out ~/ssl-cert-snakeoil.pfx -inkey /etc/ssl/private/ssl-cert-snakeoil.key -in /etc/ssl/certs/ssl-cert-snakeoil.pem -password pass:SnakeOil
    ```

### <a name="configuring-rtvs-daemon"></a>Configurazione del daemon RTVS

Il percorso del file di certificato SSL (percorso di PFX) deve essere impostato in `/etc/rtvs/rtvsd.config.json`. Aggiornare `X509CertificateFile` e `X509CertificatePassword` rispettivamente con il percorso del file e la password.

```json
{
  "logging": { "logFolder": "/tmp" },
  "security": {
    "allowedGroup": "",
    "X509CertificateFile": "/etc/rtvs/ssl-cert-snakeoil.pfx",
    "X509CertificatePassword": "SnakeOil"
  },
  "startup": { "name": "rtvsd" },
  "urls": "https://0.0.0.0:5444"
}
```

Salvare il file e riavviare il daemon, `sudo systemctl restart rtvsd`.

## <a name="install-r-services-on-windows"></a>Installare i servizi R in Windows

Per eseguire codice R, il computer remoto deve avere un interprete R installato nel modo seguente:

1. Scaricare e installare uno dei seguenti programmi:

    - [Microsoft R Open](https://mran.microsoft.com/open/)
    - [CRAN R per Windows](https://cran.r-project.org/bin/windows/base/)

    Le funzionalità dei programmi sono identiche ma Microsoft R Open dispone di librerie aggiuntive di algebra lineare con accelerazione hardware, per gentile concessione di [Intel Math Kernel Library](https://software.intel.com/intel-mkl).

1. Eseguire il [programma di installazione di R Services](https://aka.ms/rtvs-services) e riavviare quando richiesto. Il programma di installazione esegue le operazioni seguenti:

    - Crea una cartella in `%PROGRAMFILES%\R Tools for Visual Studio\1.0\` e copia tutti i file binari necessari.
    - Installa `RHostBrokerService` e `RUserProfileService` e ne configura l'avvio automatico.
    - Configura l'avvio automatico del servizio `seclogon`.
    - Aggiunge `Microsoft.R.Host.exe` e `Microsoft.R.Host.Broker.exe` alle regole in ingresso del firewall sulla porta predefinita 5444.

I servizi R vengono avviati automaticamente al riavvio del computer:

- Il **servizio R Host Broker** gestisce tutto il traffico HTTPS tra Visual Studio e il processo in cui il codice R viene eseguito nel computer.
- Il **servizio profili utente di R** è un componente con privilegi che gestisce la creazione dei profili utente di Windows. Questo servizio viene chiamato quando un nuovo utente accede per la prima volta al computer server R.

È possibile visualizzare questi servizi nella console di gestione servizi (`compmgmt.msc`).

## <a name="install-r-services-on-linux"></a>Installare i servizi R in Linux

Per eseguire codice R, il computer remoto deve avere un interprete R installato nel modo seguente:

1. Scaricare e installare uno dei seguenti programmi:

    - [Microsoft R Open](https://mran.microsoft.com/open/)
    - [CRAN R per Windows](https://cran.r-project.org/bin/linux/ubuntu/)

    Le funzionalità dei programmi sono identiche ma Microsoft R Open dispone di librerie aggiuntive di algebra lineare con accelerazione hardware, per gentile concessione di [Intel Math Kernel Library](https://software.intel.com/intel-mkl).

1. Seguire le istruzioni in [Remote R Service per Linux](setting-up-remote-r-service-on-linux.md), che tratta argomenti come i computer Ubuntu fisici, le macchine virtuali Ubuntu di Azure, il sottosistema Windows per Linux (WSL) e i contenitori Docker, inclusi quelli in esecuzione in Azure Container Repository.

## <a name="configure-r-services"></a>Configurare i servizi R

Per l'esecuzione dei servizi R nel computer remoto è anche necessario creare account utente, impostare regole firewall, configurare la rete di Azure e configurare il certificato SSL.

1. Account utente: creare account per ogni utente che accede al computer remoto. È possibile creare account locali standard (senza privilegi) oppure è possibile includere il computer server R nel dominio e aggiungere i gruppi di sicurezza appropriati al gruppo di sicurezza `Users`.

1. Regole del firewall: per impostazione predefinita, `R Host Broker` è in ascolto sulla porta TCP 5444. Pertanto verificare che siano attivate regole firewall di Windows per il traffico in ingresso e in uscita (le regole in uscita sono necessarie per l'installazione di pacchetti e operazioni simili).  Il programma di installazione dei servizi R imposta automaticamente queste regole per il firewall incorporato di Windows. Se si usa un firewall di terze parti, è tuttavia necessario aprire manualmente la porta 5444 per `R Host Broker`.

1. Configurazione di Azure: se il computer remoto è una macchina virtuale in Azure, aprire la porta 5444 per il traffico in ingresso anche nella rete di Azure, che è indipendente dal firewall di Windows. Per informazioni dettagliate vedere [Filtrare il traffico di rete con gruppi di sicurezza di rete](https://docs.microsoft.com/azure/virtual-network/virtual-networks-nsg) nella documentazione di Azure.

1. Indicare a R Host Broker il certificato SSL da caricare: se si installa il certificato in un server Intranet, è probabile che il nome di dominio completo del server corrisponda al nome NETBIOS del server. In questo caso non è necessario eseguire alcuna operazione, perché viene caricato il certificato predefinito.

    Se tuttavia si installa il certificato in un server che interagisce con Internet, ad esempio una macchina virtuale di Azure, usare il nome di dominio completo (FQDN) del proprio server, perché il nome di dominio completo di un server che interagisce con Internet non corrisponde mai al proprio nome NETBIOS.

    Per usare l'FQDN, passare alla cartella di installazione di R Services (per impostazione predefinita `%PROGRAM FILES%\R Remote Service for Visual Studio\1.0`), aprire il file `Microsoft.R.Host.Broker.Config.json` in un editor di testo e sostituirne il contenuto con quanto segue, assegnando CN al nome di dominio completo del server, ad esempio `foo.westus.cloudapp.azure.com`:

    ```json
    {
      "server.urls": "https://0.0.0.0:5444",
      "security": {
        "X509CertificateName": "CN=your-server-fully-qualified-domain-name"
      }
    }
    ```

    Salvare il file e riavviare il computer per applicare le modifiche.

## <a name="troubleshooting"></a>Risoluzione dei problemi

**Il computer server R non risponde, come procedere?**

Provare a eseguire il ping del computer remoto dalla riga di comando: `ping remote-machine-name`. Se il ping non riesce verificare che il computer sia in esecuzione.

**D. La finestra interattiva di R indica che il computer remoto è acceso ma il servizio non è in esecuzione. Perché?**

Esistono tre possibili motivi:

- Nel computer non è installato [.NET Framework 4.6.1](https://www.microsoft.com/download/details.aspx?id=49981) o versione successiva.
- Le regole del firewall per `Microsoft.R.Host.Broker` e `Microsoft.R.Host` non sono abilitate per le connessioni sia in ingresso che in uscita sulla porta 5444.
- Non è stato installato un certificato SSL con `CN=<remote-machine-name>`.

Riavviare il computer dopo aver modificato le condizioni precedenti. Quindi verificare che `RHostBrokerService` e `RUserProfileService` siano in esecuzione tramite Gestione attività (scheda Servizi) o tramite `services.msc`.

**D. Perché la finestra interattiva di R visualizza il messaggio "401 Accesso negato" durante la connessione al server R?**

Le ragioni possibili sono due:

- È molto probabile che l'account `NETWORK SERVICE` non disponga dell'accesso alla chiave privata del certificato SSL. Seguire le istruzioni specificate in precedenza per concedere a `NETWORK SERVICE` l'accesso alla chiave privata.
- Verificare che il servizio `seclogon` sia in esecuzione. Usare `services.msc` per configurare l'avvio automatico di `seclogon`.

**D. Perché la finestra interattiva di R visualizza il messaggio "404 Non trovato" durante la connessione al server R?**

Questo errore è probabilmente dovuto al fatto che mancano una o più librerie ridistribuibili di Visual C++. Verificare se nella finestra interattiva di R è presente un messaggio relativo a una libreria (DLL) mancante. Quindi verificare che sia installato il componente ridistribuibile VS 2015 e che sia installato R.

**D. Non è possibile accedere a Internet o a una risorsa dalla finestra interattiva di R. Come procedere?**

Verificare che le regole firewall per `Microsoft.R.Host.Broker` e `Microsoft.R.Host` consentano l'accesso in uscita sulla porta 5444. Riavviare il computer dopo aver applicato le modifiche.

**D. Nessuna delle soluzioni sopra elencate sembra funzionare. Come procedere?**

Verificare i file di log in `C:\Windows\ServiceProfiles\NetworkService\AppData\Local\Temp`. Questa cartella contiene file di log separati per ogni istanza del servizio R Broker che è stata eseguita. Ogni volta che il servizio viene riavviato, viene creato un nuovo file di log. Verificare se il file di log più recente contiene indicazioni sulla possibile causa dell'errore.
