---
title: Gestione dei componenti | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 398986499732a36819808b07f05f7d6b46787a94
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="component-management"></a>Gestione dei componenti
Unità di attività del programma di installazione di Windows vengono definite come componenti di Windows Installer (talvolta denominati WICs o solo i componenti). Un GUID identifica ogni WIC, ovvero l'unità fondamentale di installazione e conteggio dei riferimenti per le installazioni che usano Windows Installer.  
  
 Sebbene sia possibile usare più prodotti per creare il programma di installazione di VSPackage, questa discussione, si presuppone l'utilizzo di file di Windows Installer (MSI). Quando si crea il programma di installazione, è necessario gestire correttamente la distribuzione del file in modo che il conteggio di riferimento corretto avviene in qualsiasi momento. Di conseguenza, versioni diverse del prodotto non interferire con o interrompere tra loro in una combinazione di installare e disinstallare gli scenari.  
  
 Nel programma di installazione di Windows, il conteggio dei riferimenti si verifica a livello di componente. È necessario organizzare con attenzione le risorse, file, le voci del Registro di sistema e così via, nei componenti. Esistono altri livelli di organizzazione, ad esempio prodotti, le funzionalità e moduli, in diversi scenari che possono aiutare a. Per ulteriori informazioni, vedere [nozioni fondamentali di Windows Installer](../../extensibility/internals/windows-installer-basics.md).  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Linee guida di installazione per l'installazione Side-by-side di Authoring  
  
-   File di autore e le chiavi del Registro di sistema che vengono condivisi tra versioni nei propri componenti.  
  
     In questo modo è possibile utilizzare facilmente nella versione successiva. Ad esempio, le librerie dei tipi registrati a livello globale, estensioni file, altri elementi registrati in HKEY_CLASSES_ROOT e così via.  
  
-   Raggruppare i componenti condivisi in moduli di unione diversa.  
  
     In questo modo si creano in modo corretto per lo spostamento in avanti side-by-side.  
  
-   Installare i file condivisi e le chiavi del Registro di sistema utilizzando gli stessi componenti di Windows Installer in tutte le versioni.  
  
     Se si utilizza un altro componente, file e le voci del Registro di sistema vengono disinstallate quando si disinstalla un pacchetto VSPackage con controllo delle versioni, ma è ancora installato un altro VSPackage.  
  
-   Non combinare gli elementi con controllo delle versioni e condivisi nello stesso componente.  
  
     In questo modo non consente di installare gli elementi condivisi in un percorso globale e gli elementi con controllo delle versioni in posizioni di tipo isolati.  
  
-   Non dispongono di chiavi del Registro di sistema condivise che puntano ai file con controllo delle versioni.  
  
     In caso contrario, le chiavi condivise verranno sovrascritto quando viene installato un altro VSPackage con controllo delle versioni. Dopo aver rimosso la seconda versione, il file a cui fa riferimento la chiave è più presente.  
  
## <a name="see-also"></a>Vedere anche  
 [Scelta tra package VS condivisi e con controllo delle versioni](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Scenari di installazione di pacchetti VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)