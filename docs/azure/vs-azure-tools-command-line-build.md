---
title: Compilazione da riga di comando per Azure | Documentazione Microsoft
description: Compilazione da riga di comando per Azure
services: visual-studio-online
author: ghogen
manager: douge
assetId: 94b35d0d-0d35-48b6-b48b-3641377867fd
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
origin.date: 03/05/2017
ms.date: 09/10/2018
ms.author: v-junlch
ms.openlocfilehash: bc65d64f4dad2ac38c1f0c64ce6c7297d3c37d3a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62572422"
---
# <a name="building-azure-projects-from-the-command-line"></a>Compilazione di progetti Azure dalla riga di comando
Tramite Microsoft Build Engine (MSBuild) è possibile compilare prodotti in ambienti lab di compilazione in cui Visual Studio non è installato. MSBuild usa per i file di progetto il formato XML, che è estendibile e completamente supportato da Microsoft. Usando il formato file MSBuild è possibile indicare quali elementi devono essere compilati per una o più piattaforme o configurazioni.

È anche possibile eseguire MSBuild alla riga dei comandi, come illustrato in questo argomento. Impostando le proprietà nella riga dei comandi, è possibile compilare configurazioni specifiche di un progetto. Analogamente, è possibile definire le destinazioni compilate dal comando di MSBuild. Per altre informazioni sui parametri della riga di comando e su MSBuild, vedere [Riferimenti alla riga di comando di MSBuild](https://msdn.microsoft.com/library/ms164311.aspx).

## <a name="msbuild-parameters"></a>Parametri MSBuild
Il modo più semplice per creare un pacchetto consiste nell'eseguire MSBuild con l'opzione `/t:Publish` . Per impostazione predefinita, questo comando crea una directory in relazione alla cartella radice del progetto, ad esempio `<ProjectDirectory>\bin\Configuration\app.publish\`. Quando si compila un progetto Azure, vengono generati due file, il file del pacchetto e il file di configurazione di accompagnamento:

- File del pacchetto (`project.cspkg`)
- File di configurazione(`ServiceConfiguration.TargetProfile.cscfg`)

Per impostazione predefinita, ogni progetto Azure include un file di configurazione del servizio per le compilazioni locali (debug) e un altro per le compilazioni cloud (gestione temporanea o produzione), ma è possibile aggiungere o rimuovere i file di configurazione del servizio in base alle proprie esigenze. Quando si compila un pacchetto all'interno di Visual Studio, viene chiesto quale file di configurazione del servizio includere insieme al pacchetto. Quando si compila un pacchetto usando MSBuild, il file di configurazione del servizio locale viene incluso per impostazione predefinita. Per includere un file di configurazione del servizio diverso, impostare la proprietà `TargetProfile` del comando MSBuild (`MSBuild /t:Publish /p:TargetProfile=ProfileName`).

Se si vuole usare una directory alternativa per i file di configurazione e del pacchetto archiviati, impostare il percorso usando l'opzione `/p:PublishDir=Directory\`, inclusa la barra rovesciata finale.

## <a name="next-steps"></a>Passaggi successivi
Dopo la compilazione, sarà possibile distribuire il pacchetto in Azure.

<!-- Update_Description: update metedata properties -->