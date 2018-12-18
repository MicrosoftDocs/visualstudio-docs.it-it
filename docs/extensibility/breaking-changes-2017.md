---
title: Modifiche di rilievo di estendibilità di Visual Studio 2017 | Documenti Microsoft
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bff9c97b052f359f3d03e12093b1cdae86d5dfbd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Modifiche in Visual Studio 2017 estendibilità

Con Visual Studio 2017, offriamo un [esperienza di installazione di Visual Studio più veloce e leggero](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer) che riduce l'impatto di Visual Studio nei sistemi utente, offrendo agli utenti più ampia tramite le funzionalità e i carichi di lavoro che vengono installati. Per supportare questi miglioramenti, sono state apportate modifiche al modello di estendibilità e apportate alcune modifiche di rilievo all'estendibilità di Visual Studio. Questo documento vengono illustrati i dettagli tecnici di queste modifiche e operazioni eseguibili per risolverli. Si noti che alcune informazioni sono i dettagli di implementazione punto nel tempo e possono essere modificate in un secondo momento.

## <a name="changes-affecting-vsix-format-and-installation"></a>Modifiche che influiscono sul formato VSIX e installazione

È stato introdotto il v3 VSIX formato (versione 3) per supportare l'esperienza di installazione leggero.

Le modifiche al formato VSIX includono:

* Dichiarazione dei prerequisiti di installazione. Per offrire la promessa di un tipo semplice, rapido-installazione di Visual Studio, il programma di installazione offre più opzioni di configurazione per gli utenti. Di conseguenza, per garantire che le funzionalità e i componenti richiesti da un'estensione siano installati, estensioni saranno necessario dichiarare le relative dipendenze.
  * Il programma di installazione di Visual Studio 2017 fornirà automaticamente acquisire e installare i componenti necessari per l'utente come parte dell'installazione dell'estensione.
  * Gli utenti inoltre verranno un avviso quando si tenta di installare un'estensione che non è stata creata utilizzando il nuovo formato VSIX v3, anche se il manifesto come scelta di una versione 15.0 sono state contrassegnate.
* Funzionalità avanzate per il formato VSIX. Fornire un [installazione a basso impatto](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install) di Visual Studio che supporta installazioni side-by-side, è non salvare la maggior parte dei dati di configurazione nel Registro di sistema e sono stati spostati gli assembly di specifiche di Visual Studio dalla Global Assembly Cache. Abbiamo anche aumentato le funzionalità del formato VSIX e motore di installazione di VSIX, che consente di utilizzare è piuttosto che un file MSI o EXE per installare le estensioni per alcuni tipi di installazione.

  Le nuove funzionalità includono:

  * Registrazione nell'istanza di Visual Studio specificato.
  * Installazione di fuori di [cartella estensioni](set-install-root.md).
  * Rilevamento dell'architettura del processore.
  * Dipendenza da language separati language pack.
  * Installazione con [supporto NGEN](ngen-support.md).

## <a name="building-an-extension-for-visual-studio-2017"></a>Creazione di un'estensione per Visual Studio 2017

Finestra di progettazione degli strumenti per la creazione del nuovo formato del manifesto VSIX v3 è ora disponibile in Visual Studio 2017. Vedere il documento [procedura: eseguire la migrazione di progetti di estendibilità di Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) per informazioni dettagliate su utilizzando gli strumenti di progettazione o esecuzione di aggiornamenti manuali per il progetto e manifesto per lo sviluppo di estensioni v3 VSIX.

## <a name="change-visual-studio-user-data-path"></a>Modifica: Percorso dati utente di Visual Studio

Una singola installazione di ogni versione principale di Visual Studio in precedenza, potrebbe essere disponibile in ogni computer. Per supportare le installazioni side-by-side di Visual Studio 2017, possono esistere più percorsi dati utente per Visual Studio sul computer dell'utente.

Il codice in esecuzione il processo di Visual Studio deve essere aggiornato per utilizzare le impostazioni di gestione di Visual Studio. Codice eseguito all'esterno del processo di Visual Studio è possibile trovare il percorso di utente di una specifica installazione di Visual Studio [seguendo le istruzioni riportate qui](locating-visual-studio.md).

## <a name="change-global-assembly-cache-gac"></a>Modifica: Global Assembly Cache (GAC)

La maggior parte degli assembly principali di Visual Studio non vengono più installati nella GAC. Le seguenti modifiche sono state apportate in modo che il codice in esecuzione nel processo di Visual Studio possa comunque trovare gli assembly necessari in fase di esecuzione.

> [!NOTE]
> [INSTALLDIR] di seguito si riferisce alla directory radice di installazione di Visual Studio. VSIXInstaller.exe verrà automaticamente popolare questo, ma, per scrivere il codice di distribuzione personalizzati, leggere [individuazione di Visual Studio](locating-visual-studio.md).

* Assembly installati nella GAC solo:
  * Questi assembly sono ora installati in \Common7\IDE [INSTALLDIR]\, [INSTALLDIR] \Common7\IDE\PublicAssemblies. o \Common7\IDE\PrivateAssemblies. [INSTALLDIR]. Queste cartelle fanno parte dei percorsi di probe del processo di Visual Studio.
* Assembly che sono stati installati in un percorso non probe e nella Global Assembly Cache:
  * La copia nella Global Assembly Cache è stato rimosso dal programma di installazione.
  * Per specificare una voce di base di codice per l'assembly, è stato aggiunto un file. pkgdef.

    Ad esempio:
    
    ```xml
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```
    In fase di esecuzione, il sottosistema di pkgdef di Visual Studio è consentirà di unire queste voci nel file di configurazione di runtime del processo di Visual Studio (in [VSAPPDATA]\devenv.exe.config) come [ `<codeBase>` ](https://msdn.microsoft.com/en-us/library/efs781xb(v=vs.110).aspx) elementi. Questo è il modo consigliato per consentire il processo di Visual Studio di trovare l'assembly, in quanto evita la ricerca mediante i percorsi di ricerca.

### <a name="reacting-to-this-breaking-change"></a>Reazione a questa modifica di rilievo

* Se l'estensione è in esecuzione all'interno del processo di Visual Studio:
  * Il codice sarà in grado di trovare l'assembly principale di Visual Studio.
  * È consigliabile utilizzare un file. pkgdef per specificare un percorso all'assembly, se necessario.
* Se l'estensione è in esecuzione all'esterno del processo di Visual Studio:
  * È consigliabile cercare l'assembly principale di Visual Studio in \Common7\IDE [INSTALLDIR]\, [INSTALLDIR] \Common7\IDE\PublicAssemblies. o \Common7\IDE\PrivateAssemblies. [INSTALLDIR] mediante resolver di assembly o file di configurazione.

## <a name="change-reduce-registry-impact"></a>Modifica: Ridurre l'impatto del Registro di sistema

### <a name="global-com-registration"></a>Registrazione COM globale

* Visual Studio installato in precedenza, molte delle chiavi del Registro di sistema negli hive HKEY_CLASSES_ROOT e HKEY_LOCAL_MACHINE per supportare registrazione COM nativa. Per eliminare tale impatto, Visual Studio Usa ora [attivazione senza registrazione per i componenti COM](https://msdn.microsoft.com/en-us/library/ms973913.aspx).
* Di conseguenza, la maggior parte delle TLB / OLB / file DLL in % ProgramFiles (x86) %\Common Files\Microsoft Shared\MSEnv non vengono più installati per impostazione predefinita da Visual Studio. Questi file sono ora installati in [INSTALLDIR] con manifesti di COM senza registrazione corrispondenti utilizzati dal processo host di Visual Studio.
* Di conseguenza, il codice esterno che si basa su una registrazione COM globale per le interfacce COM di Visual Studio non troverà queste registrazioni. Il codice in esecuzione il processo di Visual Studio non sarà visibile una differenza.

### <a name="visual-studio-registry"></a>Registro di sistema di Visual Studio

* Visual Studio installato in precedenza, molte delle chiavi del Registro di sistema nell'hive HKEY_LOCAL_MACHINE e HKEY_CURRENT_USER del sistema, in una chiave specifiche di Visual Studio:
  * HKLM\Software\Microsoft\VisualStudio\\**versione**: le chiavi del Registro di sistema create dai programmi di installazione MSI e le estensioni per i singoli computer.
  * HKCU\Software\Microsoft\VisualStudio\\**versione**: le chiavi del Registro di sistema create da Visual Studio per archiviare le impostazioni specifiche dell'utente.
  * HKCU\Software\Microsoft\VisualStudio\\**versione**_Config: una copia della chiave di Visual Studio HKLM precedente e le chiavi del Registro di sistema eseguito il merge dal file. pkgdef dalle estensioni.
* Per ridurre l'impatto sul Registro di sistema, Visual Studio Usa ora la [RegLoadAppKey](https://msdn.microsoft.com/en-us/library/windows/desktop/ms724886(v=vs.85).aspx) funzione per archiviare le chiavi del Registro di sistema in un file binario privato in [VSAPPDATA]\privateregistry.bin. Solo un numero molto ridotto di chiavi specifiche di Visual Studio rimane nel Registro di sistema.
* Il codice esistente in esecuzione il processo di Visual Studio non è compromessa. Visual Studio reindirizzerà tutte le operazioni del Registro di sistema nella chiave HKCU Visual Studio specifico nel Registro di sistema privato. Lettura e scrittura in altre posizioni del Registro di sistema continueranno a utilizzare il Registro di sistema.
* Codice esterno sarà necessario caricare e leggere da questo file per le voci del Registro di sistema di Visual Studio.

### <a name="reacting-to-this-breaking-change"></a>Reazione a questa modifica di rilievo

* Codice esterno deve essere convertito per utilizzare l'attivazione senza registrazione per anche i componenti COM.
* Componenti esterni possono trovare il percorso di Visual Studio [seguendo le istruzioni riportate qui](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup).
* È consigliabile utilizzano i componenti esterni di [Gestione impostazioni esterno](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.settings.externalsettingsmanager.aspx) invece di lettura/scrittura direttamente alle chiavi del Registro di sistema di Visual Studio.
* Controllare se i componenti che utilizza l'estensione hanno implementato un'altra tecnica per la registrazione. Ad esempio, le estensioni di debugger possono essere in grado di sfruttare i vantaggi del nuovo [msvsmon registrazione COM file JSON](migrate-debugger-COM-registration.md).
