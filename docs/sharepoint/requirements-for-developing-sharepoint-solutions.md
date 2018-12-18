---
title: Requisiti per lo sviluppo di soluzioni SharePoint | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, prerequisites
- SharePoint development in Visual Studio, requirements
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2cb92476d64abebb0dae24109e57940a19505cc1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="requirements-for-developing-sharepoint-solutions"></a>Requisiti per lo sviluppo di soluzioni SharePoint
 
È necessario installare i seguenti prerequisiti nel sistema prima di poter usare gli strumenti di sviluppo di soluzioni SharePoint inclusi in Visual Studio:

- Visual Studio con c# e/o Visual Basic o un'edizione di Visual Studio Application Lifecycle Management (ALM).

- [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] installazione a 64 bit [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] o a 64 bit [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2.

     oppure

- [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] installazione a 64 bit [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] o a 64 bit [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2.

> [!NOTE]
> Mentre solo i sistemi operativi server supportati ufficialmente da SharePoint, sono consentiti due sistemi operativi client: [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] e [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] SP1. Per ulteriori informazioni, vedere [Guida all'installazione di SharePoint Server 2010 per sviluppatori Workstation](http://go.microsoft.com/fwlink/?LinkID=164557).

Tipi di progetto di business del modello di integrazione applicativa dei dati (BDC) richiedono che [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] essere installato nel sistema.

Per sviluppare soluzioni SharePoint in Visual Studio, è necessario installare SharePoint nello stesso computer di Visual Studio. Inoltre, gli strumenti di sviluppo di SharePoint supportano solo una configurazione autonoma di SharePoint. non supportano la configurazione della farm (remoto).

> [!NOTE]
> I progetti SharePoint in Visual Studio supportano solo [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)]. Se si seleziona [!INCLUDE[net_v40_long](../sharepoint/includes/net-v40-long-md.md)] per un nuovo progetto di SharePoint, sarà comunque destinato [!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)].

Per ulteriori informazioni su come installare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], vedere [installare Visual Studio](../install/install-visual-studio.md).

## <a name="vista-and-windows-7-user-account-control-uac"></a>Vista e Windows 7 controllo Account utente (UAC)

[!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] incorporare la funzionalità di sicurezza che è noto come il controllo dell'Account utente (UAC). Per sviluppare soluzioni SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] su [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] e [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] sistemi di controllo dell'account utente richiede l'esecuzione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] come amministratore di sistema. Sul desktop, aprire il menu di scelta rapida per [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], quindi scegliere **Esegui come amministratore**.

Per configurare il collegamento sul desktop per eseguire sempre come amministratore, aprire il menu di scelta rapida, scegliere **proprietà**, scegliere il **avanzate** e quindi selezionare il **Esegui come amministratore**  casella di controllo.

Per ulteriori informazioni, vedere [comprensione e la configurazione di controllo dell'Account utente in Windows Vista](http://go.microsoft.com/fwlink/?LinkID=156476). e [controllo Account utente di Windows 7](http://go.microsoft.com/fwlink/?LinkId=177523).

## <a name="sharepoint-permissions-considerations"></a>Considerazioni sulle autorizzazioni di SharePoint

Per sviluppare soluzioni SharePoint, è necessario disporre di autorizzazioni sufficienti per eseguire il debug delle soluzioni di SharePoint. Prima di poter testare una soluzione di SharePoint, eseguire i passaggi seguenti per assicurarsi di disporre delle autorizzazioni necessarie:

1. Aggiungere l'account utente come amministratore di sistema.

2. Aggiungere l'account utente come amministratore di Farm per il server SharePoint.

    1. In Amministrazione centrale SharePoint, scegliere il **gestire il gruppo di amministratori farm** collegamento.

    2. Nel **amministratori Farm** pagina, scegliere il **New** pulsante.

3. Aggiungere l'account utente per al gruppo WSS_ADMIN_WPG.

## <a name="see-also"></a>Vedere anche

[Introduzione al &#40;sviluppo per SharePoint in Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)