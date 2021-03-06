---
title: 'Procedura: installare la Strumenti di Visual Studio per Office Runtime Redistributable'
description: Informazioni su come installare il Microsoft Visual Studio 2010 Tools per Office Runtime Redistributable.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office runtime [Office development in Visual Studio]
- installing Office development tools in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 75dc5b2f3f207603320a773ebd71f5d6d3f81b8c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918621"
---
# <a name="how-to-install-the-visual-studio-tools-for-office-runtime-redistributable"></a>Procedura: installare la Strumenti di Visual Studio per Office Runtime Redistributable
  Visual Studio 2010 Tools per Office Runtime deve essere installato in ogni computer che esegue soluzioni create tramite gli strumenti di sviluppo Microsoft Office in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Il runtime viene installato automaticamente all'installazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e di Microsoft Office. Per ulteriori informazioni, vedere [strumenti di Visual Studio per gli scenari di installazione di Office Runtime](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md).

[!include[Add-ins note](includes/addinsnote.md)]

 Attenersi alle seguenti istruzioni di installazione manuale, se si verificano le situazioni riportate di seguito:

- È necessario installare il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] su un server. Ad esempio, si desidera utilizzare la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> per gestire soluzioni a livello di documento su un server.

- È necessario installare il runtime in un computer su cui sono già installati tutti i prerequisiti delle soluzioni di Office.

    > [!NOTE]
    > Per installare .NET Framework e [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], è necessario essere un amministratore del computer di sviluppo.

## <a name="to-install-the-visual-studio-tools-for-office-runtime"></a>Per installare l'assembly nel runtime di Visual Studio Tools per Office

1. Installare [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versione successiva.

    - Per scaricare [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , vedere [Microsoft .NET Framework 4 (programma di installazione Web)](https://www.microsoft.com/download/details.aspx?id=17851).

    - Per scaricare lo [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)] , vedere [Microsoft .NET Framework 4 Client Profile (programma di installazione Web)](https://www.microsoft.com/download/details.aspx?id=17113).

    - Per scaricare [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , vedere [Microsoft .NET Framework 4,5](https://www.microsoft.com/download/details.aspx?id=30653).

2. Eseguire *vstor_redist.exe* per installare [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

     È possibile scaricare questi file di installazione da [Visual Studio 2010 Tools per Office Runtime](https://www.microsoft.com/download/details.aspx?id=56961). I prerequisiti per [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] corrispondono a quelli per .NET Framework.

     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] include i Language Pack. Se l'installazione di Windows è impostata su una lingua diversa dall'inglese, è possibile visualizzare i messaggi di runtime nella stessa lingua utilizzata da Windows. Analogamente, se gli utenti finali installano [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ed eseguono le soluzioni in versioni di Windows impostate su una lingua diversa dall'inglese, verranno visualizzati i messaggi di runtime nella stessa lingua di Windows. In alcuni casi, potrebbe essere necessario installare Language Pack aggiuntivi. Ad esempio, potrebbero essere necessari Language Pack aggiuntivi se la copia di Windows utilizza più di un'impostazione della lingua o se si passa a un'altra lingua dopo che è già stato installato [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . I Language Pack sono disponibili in [Microsoft Visual Studio 2010 Tools per il Language Pack del sistema di Microsoft Office (versione 4,0 Runtime)](https://www.microsoft.com/download/details.aspx?id=54246).

## <a name="see-also"></a>Vedi anche
- [Introduzione &#40;sviluppo per Office in Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Configurare un computer per sviluppare soluzioni Office](../vsto/configuring-a-computer-to-develop-office-solutions.md)
- [Procedura: configurare un computer per sviluppare soluzioni Office](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)
- [Procedura: installare assembly di interoperabilità primari di Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
- [Gestire i documenti in un server usando la classe ServerDocument](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)
- [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)
