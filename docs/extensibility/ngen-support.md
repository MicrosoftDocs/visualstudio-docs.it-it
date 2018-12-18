---
title: Supporto di Ngen in VSIX v3 | Documenti Microsoft
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
caps.latest.revision: "1"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 15277f0a1038e43bb316d604cbc415da4a5d80bd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ngen-support-in-vsix-v3"></a>Supporto di Ngen in VSIX v3

Con Visual Studio 2017 e la nuova v3 VSIX estensione (versione 3) manifesto formato, l'estensione per gli sviluppatori possono ora "ngen" gli assembly in fase di installazione.

Di seguito è riportato un frammento da MSDN che illustrarne quali "ngen":

>Il generatore di immagini native (Ngen.exe) consente di migliorare le prestazioni delle applicazioni gestite. Questo strumento crea immagini native, ovvero file contenenti codice macchina compilato specifico del processore, e le installa nella cache delle immagini native del computer locale. Il runtime può usare le immagini native della cache anziché il compilatore Just-In-Time (JIT) per compilare l'assembly originale.
>
>da [Ngen.exe (Native Image Generator)](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx)

Per poter "ngen" un assembly, il progetto VSIX deve essere installato "per istanza per ogni macchina". Questo può essere abilitato selezionando la casella di controllo "all users" nella finestra di progettazione Extension. vsixmanifest:

![controllare tutti gli utenti](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Come abilitare Ngen

Per abilitare ngen per un assembly, è possibile utilizzare il **proprietà** finestra in Visual Studio.

Esistono 4 proprietà che è possibile impostare:

1. **Ngen** (booleano) - se true, il programma di installazione di Visual Studio verrà "ngen" dell'assembly.
2. **Applicazione di Ngen** (stringa) Ngen offre l'opportunità di utilizzare il file app. config dell'applicazione per risolvere le dipendenze dell'assembly. Questo valore deve essere impostato su un'applicazione di cui si desidera utilizzare (relativo alla directory di installazione di Visual Studio) di App.
3. **Architettura di Ngen** (enumerazione) - l'architettura per compilare in modo nativo l'assembly. Le opzioni sono: una. B NotSpecified. X86 c. X64 d. Tutti
4. **Priorità Ngen** (numero intero compreso tra 1 e 3) - livello di priorità Ngen è documentato al [livelli di priorità Ngen.exe](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx#Anchor_3).

Di seguito viene illustrato il **proprietà** finestra in azione:

![Ngen nelle proprietà](media/ngen-in-properties.png)

Verrà aggiunta dei metadati per il riferimento al progetto all'interno di file con estensione csproj del progetto VSIX:

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
 ```

 >**Nota:** è possibile modificare direttamente il file con estensione csproj, se si preferisce.

## <a name="extra-information"></a>Informazioni aggiuntive

Le modifiche di progettazione alle proprietà si applicano solo ai riferimenti al progetto; è possibile impostare i metadati di Ngen per gli elementi all'interno del progetto anche (usando gli stessi metodi descritti sopra) lungo gli elementi sono assembly .NET.