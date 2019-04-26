---
title: Publish-WebApplicationVM | Documentazione Microsoft
description: Informazioni su come distribuire un'applicazione Web in una macchina virtuale. Se non sono presenti, lo script crea le risorse necessarie nella sottoscrizione di Azure.
services: visual-studio-online
author: ghogen
manager: douge
assetId: de4cec95-f73f-44d9-babd-9f47f2633cdb
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
origin.date: 11/11/2016
ms.date: 09/10/2018
ms.author: v-junlch
ms.openlocfilehash: 8b4b7a05de87ab8b70046b51fe9f256f05d3aee5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62572285"
---
# <a name="publish-webapplicationvm-windows-powershell-script"></a>Publish-WebApplicationVM (Windows PowerShell script)
Consente di distribuire un'applicazione Web in una macchina virtuale. Se non sono presenti, lo script crea le risorse necessarie nella sottoscrizione di Azure.

```
Publish-WebApplicationVM
-Configuration <configuration>
-SubscriptionName <subscriptionName>
-WebDeployPackage <packageName>
-VMPassword @{Name = "name"; Password = "password")
-DatabaseServerPassword @{Name = "name"; Password = "password"}
-SendHostMessagesToOutput
-Verbose
```

### <a name="configuration"></a>Configurazione
Percorso del file di configurazione JSON che descrive i dettagli della distribuzione.

| Alias | none |
| --- | --- |
| Obbligatorio? |true |
| Posizione |denominata |
| Valore predefinito |none |
| Input pipeline accettato? |False |
| Caratteri jolly accettati? |False |

### <a name="subscriptionname"></a>SubscriptionName
Nome della sottoscrizione di Azure in cui creare la macchina virtuale.

| Alias | none |
| --- | --- |
| Obbligatorio? |False |
| Posizione |denominata |
| Valore predefinito |Usa la prima sottoscrizione nel file di sottoscrizione |
| Input pipeline accettato? |False |
| Caratteri jolly accettati? |False |

### <a name="webdeploypackage"></a>WebDeployPackage
Percorso al pacchetto di distribuzione Web da pubblicare nella macchina virtuale. È possibile creare questo pacchetto usando la pubblicazione Web guidata di Visual Studio. Vedere [How to: Create a Web Deployment Package in Visual Studio](https://msdn.microsoft.com/library/dd465323.aspx) (Procedura: Creare un pacchetto di distribuzione Web in Visual Studio).

| Alias | none |
| --- | --- |
| Obbligatorio? |False |
| Posizione |denominata |
| Valore predefinito |none |
| Input pipeline accettato? |False |
| Caratteri jolly accettati? |False |

### <a name="allowuntrusted"></a>AllowUntrusted
Se true, consente l'utilizzo di certificati che non sono firmati da un'autorità radice attendibile.

| Alias | none |
| --- | --- |
| Obbligatorio? |False |
| Posizione |denominata |
| Valore predefinito |False |
| Input pipeline accettato? |False |
| Caratteri jolly accettati? |False |

### <a name="vmpassword"></a>VMPassword
Le credenziali per l'account della macchina virtuale. Esempio: -VMPassword @{Name = "admin"; Password = "password"}

| Alias | none |
| --- | --- |
| Obbligatorio? |False |
| Posizione |denominata |
| Valore predefinito |none |
| Input pipeline accettato? |False |
| Caratteri jolly accettati? |False |

### <a name="databaseserverpassword"></a>DatabaseServerPassword
Le credenziali del database SQL in Azure. Esempio: -DatabaseServerPassword @{Name = "admin"; Password = "password"}

| Alias | none |
| --- | --- |
| Obbligatorio? |False |
| Posizione |denominata |
| Valore predefinito |none |
| Input pipeline accettato? |False |
| Caratteri jolly accettati? |False |

### <a name="sendhostmessagestooutput"></a>SendHostMessagesToOutput
Se impostato su true, stampa i messaggi dallo script al flusso di output.

| Alias | none |
| --- | --- |
| Obbligatorio? |False |
| Posizione |denominata |
| Valore predefinito |False |
| Input pipeline accettato? |False |
| Caratteri jolly accettati? |False |

## <a name="remarks"></a>Osservazioni
Per una spiegazione completa sull'uso dello script per creare ambienti di sviluppo e test, vedere [Uso degli script di Windows PowerShell per la pubblicazione in ambienti di sviluppo e test](vs-azure-tools-publishing-using-powershell-scripts.md).

Il file di configurazione JSON specifica i dettagli degli elementi da distribuire. Include le informazioni specificate al momento della creazione del progetto, ad esempio il nome, il set di affinità, l’immagine VHD e la dimensione della macchina virtuale. Inoltre include gli endpoint nella macchina virtuale, i database per eseguire il provisioning, se presente, e i parametri di distribuzione Web. Il codice seguente mostra un esempio di file di configurazione JSON:

```
{
    "environmentSettings": {
        "cloudService": {
            "name": "myvmname",
            "affinityGroup": "",
            "location": "China North",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myvmname",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Windows-Server-2012-R2-201404.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [
                    {
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [
            {
                "connectionStringName": "",
                "databaseName": "",
                "serverName": "",
                "user": "",
                "password": ""
            }
        ],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

È possibile modificare il file di configurazione JSON per cambiare gli elementi del provisioning. Una macchina virtuale e un servizio cloud sono necessari, ma la sezione del database è facoltativa.


<!-- Update_Description: update metedata properties -->