---
title: Pagina delle proprietà dell'applicazione per app UWP
description: Informazioni su come usare la pagina applicazione per specificare l'assembly e le informazioni sul pacchetto del progetto piattaforma UWP (Universal Windows Platform) (UWP) e la versione di destinazione di Windows 10.
ms.custom: SEO-VS-2020
ms.date: 01/23/2018
ms.topic: reference
f1_keywords:
- AppPackage.Properties.Application
helpviewer_keywords:
- Application page [UWP project]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: 21dd08f81802661cae9d77ee3449f4e9369ca768
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965083"
---
# <a name="application-property-page-uwp-projects"></a>Pagina delle proprietà dell'applicazione (progetti UWP)

Usare la pagina delle proprietà **Applicazione** per specificare l'assembly e le informazioni del pacchetto per il progetto UWP (Universal Windows Platform), selezionando Windows 10 come versione di destinazione.

![Pagina delle proprietà dell'applicazione](media/application-page-uwp.png)

Per accedere alla pagina **Applicazione**, scegliere un nodo del progetto in **Esplora soluzioni**. Quindi scegliere   >  **proprietà** progetto dalla barra dei menu. Le pagine delle proprietà vengono aperte nella scheda **Applicazione**.

## <a name="general-section"></a>Sezione Generale

**Nome assembly** &mdash; Specifica il nome del file di output che conterrà il manifesto dell'assembly.

Per accedere a questa proprietà a livello di programmazione, vedere <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

**Spazio dei nomi predefinito** &mdash; Specifica lo spazio dei nomi di base per i file aggiunti al progetto. Per altre informazioni sugli spazi dei nomi, vedere [Spazi dei nomi (Guida per programmatori C#)](/dotnet/csharp/programming-guide/namespaces/), [Spazi dei nomi (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/namespaces) o [Spazi dei nomi (C++)](/cpp/cpp/namespaces-cpp).

Per accedere a questa proprietà a livello di programmazione, vedere <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

**Informazioni assembly** &mdash; Se si sceglie questo pulsante, verrà visualizzata la finestra di [dialogo informazioni assembly](../../ide/reference/assembly-information-dialog-box.md).

**Manifesto** &mdash; del pacchetto Se si sceglie questo pulsante, verrà visualizzata la finestra Progettazione manifesto. Per accedere alla finestra di progettazione del manifesto, è anche possibile scegliere il file _Package.appxmanifest_ in **Esplora soluzioni**. Per altre informazioni, vedere [Configurare un pacchetto con Progettazione manifesto](/windows/msix/package/packaging-uwp-apps#configure-your-project).

## <a name="targeting-section"></a>Sezione Destinazione

È possibile impostare la versione di destinazione e la versione minima di Windows 10 per l'app usando gli elenchi a discesa in questa sezione. È consigliabile selezionare la versione più recente di Windows 10, e se si sviluppa un'app aziendale, anche supportare una versione minima precedente. Per altre informazioni sulla scelta della versione di Windows 10, vedere [Scegliere una versione di UWP](/windows/uwp/updates-and-versions/choose-a-uwp-version).

Per informazioni sulla selezione della piattaforma di destinazione di Visual Studio, vedere [Selezione della piattaforma](/visualstudio/productinfo/vs2017-compatibility-vs#platform-targeting).

## <a name="see-also"></a>Vedi anche

- [Crea la prima app](/windows/uwp/get-started/your-first-app)
- [Scegliere una versione di UWP](/windows/uwp/updates-and-versions/choose-a-uwp-version)
