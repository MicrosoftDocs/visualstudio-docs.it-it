---
title: Specificando il percorso di File di pacchetto VSPackage alla Shell di Visual Studio | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, file location
- VSPackages, managed package file location
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7a4270fbd723e6c5aa6f16066066e0ca4ac74e5d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="specifying-vspackage-file-location-to-the-vs-shell"></a>Specificando il percorso di File di pacchetto VSPackage alla Shell di Visual Studio
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve essere in grado di individuare l'assembly DLL per caricare il pacchetto VSPackage. È possibile individuarlo in vari modi, come descritto nella tabella seguente.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|Usare la chiave del Registro di sistema CodeBase.|La chiave CodeBase può essere utilizzata per indirizzare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per caricare l'assembly VSPackage da qualsiasi percorso di file completo. Il valore della chiave deve essere il percorso del file della DLL. Questo è il modo migliore per avere [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] caricare l'assembly in pacchetto. Questa tecnica è detta anche "CodeBase/privata installazione directory tecnica." Durante la registrazione viene passato il valore della base di codice per le classi di attributi di registrazione tramite un'istanza di <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> tipo.|  
|Posizionare la DLL nel **PrivateAssemblies** directory.|Collocare l'assembly nel **PrivateAssemblies** sottodirectory del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] directory. Gli assembly si trovano **PrivateAssemblies** vengono rilevate automaticamente, ma non sono visibili nel **Aggiungi riferimenti** la finestra di dialogo. La differenza tra **PrivateAssemblies** e **PublicAssemblies** consiste nel fatto che gli assembly in **PublicAssemblies** sono enumerate nella **aggiungere riferimenti**  la finestra di dialogo. Se si è scelto di non utilizzare la tecnica "directory di installazione CodeBase/privata", quindi è necessario installare nel **PrivateAssemblies** directory.|  
|Utilizzare un assembly con nome sicuro e la chiave del Registro di sistema Assembly.|La chiave di Assembly consente di indirizzare in modo esplicito [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per caricare un nome sicuro denominato assembly VSPackage. Il valore della chiave deve essere il nome sicuro dell'assembly.|  
|Posizionare la DLL nel **PublicAssemblies** directory.|Infine, l'assembly può anche essere inserito nel **PublicAssemblies** sottodirectory. Gli assembly si trovano **PublicAssemblies** vengono rilevate automaticamente e verrà visualizzato anche nella **Aggiungi riferimenti** nella finestra di dialogo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].<br /><br /> Gli assembly VSPackage devono essere posizionati solo nel **PublicAssemblies** directory se contengono i componenti che sono destinati a essere riutilizzati da altri sviluppatori VSPackage gestiti. La maggior parte degli assembly non soddisfano questo criterio.|  
  
> [!NOTE]
>  Utilizzare assembly con nome sicuro, con segno per tutti gli assembly dipendenti. Questi assembly devono essere installati nella propria directory o global assembly cache (GAC). Questo consente di proteggere i conflitti con gli assembly che hanno lo stesso nome di file di base, noto come associazione con nome sicuro.