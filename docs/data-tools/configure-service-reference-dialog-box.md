---
title: Finestra di dialogo riferimento servizio configura | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: b3b9ae8406845de886009da981eaf7f63e68972b
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2018
---
# <a name="configure-service-reference-dialog-box"></a>Configura riferimento a servizio (finestra di dialogo)

Il **Configura riferimento a servizio** la finestra di dialogo consente di configurare il comportamento dei servizi Windows Communication Foundation (WCF).

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere Importa/esporta impostazioni dal menu Strumenti. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

Per l'accesso di **Configura riferimento a servizio** nella finestra di dialogo scelta di un servizio fa riferimento nella **Esplora** e scegliere **Configura riferimento a servizio**. È possibile accedere anche la finestra di dialogo, fare clic su di **avanzate** pulsante il **dialogo Aggiungi riferimento al servizio**.

## <a name="task-list"></a>Elenco attività  
  
-   Per modificare l'indirizzo in cui è ospitato un servizio WCF, immettere il nuovo indirizzo nel **indirizzo** campo.  
  
-   Per modificare il livello di accesso per le classi in un client WCF, selezionare una parola chiave a livello di accesso nel **livello di accesso per classi generate** elenco.  
  
-   Per chiamare i metodi di un servizio WCF in modo asincrono, selezionare il **Genera operazioni asincrone** casella di controllo.  
  
-   Per generare i tipi di contratto di messaggio in un client WCF, selezionare il **genera sempre contratti di messaggio** casella di controllo.  
  
-   Per specificare i tipi di raccolta elenco o dizionario per un client WCF, selezionare i tipi dal **tipo di raccolta** e **tipo di raccolta dizionario** Elenca.  
  
-   Per disabilitare la condivisione dei tipi, deselezionare il **Riutilizza tipi negli assembly di riferimento** casella di controllo. Per abilitare la condivisione di tipi per un subset di assembly di riferimento, selezionare il **Riutilizza tipi negli assembly di riferimento** caselle di controllo **Riutilizza tipi negli assembly di riferimento specificati**e selezionare l'elemento fa riferimento nel **elenco degli assembly di riferimento**.  
  
## <a name="uielement-list"></a>Elenco UIElement  
 **Indirizzo**  
 Usato per aggiornare l'indirizzo Web in cui un riferimento al servizio cerca un servizio. Ad esempio, durante lo sviluppo il servizio potrebbe essere ospitato su un server di sviluppo, quindi spostato a un server di produzione, necessitando un cambio di indirizzo.  
  
> [!NOTE]
>  L'elemento Address non è disponibile quando il **Configura riferimento a servizio** da cui viene visualizzata la finestra di dialogo di **dialogo Aggiungi riferimento al servizio**.  
  
 **Livello di accesso per classi generate**  
 Determina il livello di accesso del codice per le classi del client WCF.  
  
> [!NOTE]
>  Per i progetti di siti Web, questa opzione è impostata sempre su `Public` e non può essere modificata. Per ulteriori informazioni, vedere [riferimenti al servizio di risoluzione dei problemi](../data-tools/troubleshooting-service-references.md).  
  
 **Genera operazioni asincrone**  
 Determina se i metodi del servizio WCF verranno chiamati in modo sincrono (impostazione predefinita) oppure asincrono.  
  
 **Genera operazioni basate su attività**  
 Durante la scrittura di codice asincrono, questa opzione consente di sfruttare la Task Parallel Library (TPL) introdotta con .Net 4. Vedere [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl).  
  
 **Genera sempre contratti di messaggio**  
 Determina se i tipi di contratto di messaggio verranno generati per un client WCF. Per ulteriori informazioni sui contratti di messaggio, vedere [con contratti di messaggio](/dotnet/framework/wcf/feature-details/using-message-contracts).  
  
 **Tipo di raccolta**  
 Specifica il tipo di raccolta elenco per un client WCF. Il tipo predefinito è <xref:System.Array>.  
  
 **Tipo di raccolta dizionario**  
 Specifica il tipo di raccolta dizionario per un client WCF. Il tipo predefinito è <xref:System.Collections.Generic.Dictionary%602>.  
  
 **Riutilizza tipi negli assembly di riferimento**  
 Determina se un client WCF proverà a riusare i tipi già esistenti negli assembly di riferimento piuttosto di generare nuovi tipi quando un servizio viene aggiunto o aggiornato. Per impostazione predefinita, questa opzione è selezionata.  
  
 **Riutilizza tipi in tutti gli assembly di riferimento**  
 Se selezionata, tutti i tipi di **elenco degli assembly di riferimento** verranno riutilizzati, se possibile. Questa opzione è selezionata per impostazione predefinita.  
  
 **Riutilizza tipi negli assembly di riferimento specificati**  
 Se selezionata, solo i tipi selezionati nel **elenco degli assembly di riferimento** verrà riutilizzata.  
  
 **Elenco di assembly di riferimento**  
 Contiene un elenco di assembly di riferimento per il progetto o il sito Web. Quando **Riutilizza tipi negli assembly di riferimento specificati** è selezionata, singoli assembly può essere selezionato o deselezionato.  
  
 **Aggiungi riferimento Web** consente di visualizzare la finestra di dialogo Aggiungi riferimento Web.

> [!NOTE]
> Usare questa opzione solo per i progetti destinati alla versione 2.0 di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

> [!NOTE]
> Il **Aggiungi riferimento Web** pulsante è disponibile solo quando il **Configura riferimento a servizio** da cui viene visualizzata la finestra di dialogo di **dialogo Aggiungi riferimento al servizio**.

## <a name="see-also"></a>Vedere anche

[Procedura: aggiungere un riferimento a un servizio Web](how-to-add-update-or-remove-a-wcf-data-service-reference.md)  
[Servizi Windows Communication Foundation e WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)