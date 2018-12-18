---
title: Azure SDK per Python | Microsoft Docs
description: Azure SDK per Python semplifica l'utilizzo dei servizi di Microsoft Azure dalle applicazioni Python eseguite su qualsiasi piattaforma.
ms.custom: 
ms.date: 01/22/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: baa206dfbb9caf58ce872d0c9dee22e183403adb
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="azure-sdk-for-python"></a>Azure SDK per Python

Azure SDK per Python semplifica l'uso e la gestione dei servizi di Microsoft Azure dalle applicazioni eseguite in Windows, Mac, OSX e Linux.

## <a name="installation"></a>Installazione

Azure SDK può essere installato da [Python Package Index](https://pypi.python.org/pypi/azure) (Indice dei pacchetti Python).

Installare la **versione stabile più recente** che supporta Python 2.7 e 3.x, come indicato di seguito:

```command
pip install azure
```

È anche possibile seguire le indicazioni in [Installazione di Python e dell'SDK](https://docs.microsoft.com/azure/python-how-to-install/) nella documentazione di Azure.

## <a name="documentation"></a>Documentazione

La documentazione è disponibile in [azure-sdk-for-python.readthedocs.org](http://azure-sdk-for-python.readthedocs.org/en/latest/index.html).

Anche nella sezione [Azure SDK per Python del Centro per sviluppatori Python](http://azure.microsoft.com/develop/python/) sono disponibili numerose risorse utili, incluse alcune esercitazioni:

- Creazione di app Web con [Django](/azure/app-service-web/web-sites-python-create-deploy-django-app) [Flask](/azure/app-service-web/web-sites-python-create-deploy-flask-app) e [Bottle](/azure/app-service-web/web-sites-python-create-deploy-bottle-app).
- [Archiviazione - BLOB](/azure/storage/storage-python-how-to-use-blob-storage)
- [Archiviazione - Tabelle](/azure/storage/storage-python-how-to-use-table-storage)
- [Archiviazione - Code](/azure/storage/storage-python-how-to-use-queue-storage)
- [DocumentDB](/azure/documentdb/documentdb-python-application)
- [Come usare le code del bus di servizio](/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
- [Come usare gli argomenti e le sottoscrizioni del bus di servizio](/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
- [Gestione dei servizi](/azure/cloud-services/cloud-services-python-how-to-use-service-management)

Per le API pubbliche senza documentazione, gli unit test nel [repository GitHub dell'SDK](https://github.com/Azure/azure-sdk-for-python) rappresentano una buona fonte di informazioni:

- [Unit test per l'archiviazione](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [Unit test per il bus di servizio](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [Unit test per la gestione dei servizi](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)
- [Unit test per la gestione delle risorse](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests)

## <a name="support"></a>Supporto

Il repository GIT per l'SDK è disponibile all'indirizzo [https://github.com/Azure/azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python).

Per qualsiasi problema o domanda relativi all'uso dell'SDK, [registrare i problemi nel repository](https://github.com/Azure/azure-sdk-for-python/issues).
