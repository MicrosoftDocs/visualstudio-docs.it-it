---
title: Creazione di istanze di progetto tramite Project Factory | Microsoft Docs
description: Informazioni su come creare istanze della classe di progetto tramite Project Factory in Visual Studio Integrated Development Environment (IDE).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 40b7c3fbe5b5b7fd59fe0e57376290181f3e9a20
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056799"
---
# <a name="create-project-instances-by-using-project-factories"></a>Creare istanze di progetto tramite Project Factory
I tipi di progetto in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usano una *Factory di progetto* per creare istanze di oggetti progetto. Una factory del progetto è simile a una class factory standard per oggetti COM cocreabili. Tuttavia, gli oggetti di progetto non sono cocreabili; possono essere creati solo tramite una factory del progetto.

 L' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE chiama la factory del progetto implementata nel pacchetto VSPackage quando un utente carica un progetto esistente o crea un nuovo progetto in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Il nuovo oggetto progetto fornisce all'IDE informazioni sufficienti per popolare **Esplora soluzioni**. Il nuovo oggetto progetto fornisce anche le interfacce necessarie per il supporto di tutte le azioni dell'interfaccia utente pertinenti avviate dall'IDE.

 È possibile implementare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interfaccia in una classe nel progetto. In genere si trova nel proprio modulo.

 I progetti che supportano l'aggregazione da un proprietario devono mantenere una chiave del proprietario nel file di progetto. Quando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> metodo viene chiamato su un progetto con una chiave del proprietario, il progetto di proprietà converte la chiave del proprietario in un GUID Factory del progetto, quindi chiama il `CreateProject` metodo su questa factory del progetto per eseguire la creazione effettiva.

## <a name="create-an-owned-project"></a>Creare un progetto di proprietà
 Un proprietario crea un progetto di proprietà in due fasi:

1. Chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> metodo. Ciò consente al progetto di proprietà di creare un oggetto progetto aggregato in base al controllo dell'input `IUnknown` . Il progetto di proprietà passa `IUnknown` nuovamente l'oggetto interno e l'oggetto aggregato al progetto proprietario. In questo modo il progetto di proprietà è in possesso della possibilità di archiviare l'oggetto interno `IUnknown` .

2. Chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> metodo. Il progetto di proprietà esegue tutte le creazioni di istanze quando questo metodo viene chiamato anziché chiamare come se si trattasse di `IVsProjectFactory::CreateProject` progetti non di proprietà. L'enumerazione di input `VSOWNEDPROJECTOBJECT` è in genere il progetto di proprietà aggregato. Il progetto di proprietà può usare questa variabile per determinare se il relativo oggetto progetto è già stato creato (cookie non è uguale a NULL) o deve essere creato (cookie equivale a NULL).

   I tipi di progetto sono identificati da un GUID di progetto univoco, simile al CLSID di un oggetto COM cocreabile. In genere, una factory del progetto gestisce la creazione di istanze di un unico tipo di progetto, anche se è possibile che una factory del progetto gestisca più di un GUID del tipo di progetto.

   I tipi di progetto sono associati a una particolare estensione di file. Quando un utente tenta di aprire un file di progetto esistente o tenta di creare un nuovo progetto clonando un modello, l'IDE usa l'estensione del file per determinare il GUID del progetto corrispondente.

   Non appena l'IDE determina se è necessario creare un nuovo progetto o aprire un progetto esistente di un determinato tipo, l'IDE usa le informazioni nel registro di sistema in **[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects]** per trovare il VSPackage che implementa la factory del progetto richiesta. Il pacchetto VSPackage viene caricato dall'IDE. Nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metodo, il pacchetto VSPackage deve registrare la factory del progetto con l'IDE chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> metodo.

   Il metodo principale dell' `IVsProjectFactory` interfaccia è <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> , che dovrebbe gestire due scenari: l'apertura di un progetto esistente e la creazione di un nuovo progetto. La maggior parte dei progetti archivia lo stato del progetto in un file di progetto. In genere, i nuovi progetti vengono creati facendo una copia del file modello passato al `CreateProject` metodo e quindi aprendo la copia. Viene creata un'istanza dei progetti esistenti aprendo direttamente il file di progetto passato al `CreateProject` metodo. Il `CreateProject` metodo può visualizzare all'utente funzionalità aggiuntive dell'interfaccia utente, se necessario.

   Un progetto non può inoltre utilizzare alcun file e, al contrario, archiviare lo stato del progetto in un meccanismo di archiviazione diverso da quello file system, ad esempio un database o un server Web. In questo caso, il parametro del nome file passato al `CreateProject` metodo non è in realtà un percorso di file System ma una stringa univoca, ovvero un URL, per identificare i dati del progetto. Non è necessario copiare i file modello passati a `CreateProject` per attivare la sequenza di costruzione appropriata da eseguire.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>
- [Elenco di controllo: creare nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
