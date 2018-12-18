---
title: Personalizzazione della trasformazione del testo T4
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 94d04d70192e2730cdf2682a3d2d138089eef891
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="customizing-t4-text-transformation"></a>Personalizzazione della trasformazione del testo T4

Modelli di testo sono una funzionalità di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] che consentono di generare codice programma o altri file di testo tramite un processo di trasformazione. Utilizzando [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)], è possibile estendere il processo di trasformazione del modello predefinito personalizzando il processore di direttiva del modello di testo o l'host del modello di testo.

## <a name="in-this-section"></a>In questa sezione
 [Il processo di trasformazione del modello di testo](../modeling/the-text-template-transformation-process.md) viene descritto il funzionamento di trasformazione del testo e viene illustrato il ruolo dell'host del modello e i processori di direttiva.

 [Creazione di processori di direttiva modello di testo T4 personalizzati](../modeling/creating-custom-t4-text-template-directive-processors.md) il processore di direttiva riguarda le direttive nel modello, ad esempio `<#@template#>.` viene eseguito durante la compilazione del modello e può caricare gli assembly e altre risorse. Inoltre possibile inserire il codice che caricherà le risorse in fase di esecuzione. Definendo il processore di direttiva, è possibile ridurre la complessità dei modelli.

 [Richiamo della trasformazione del testo in un'estensione VS](../modeling/invoking-text-transformation-in-a-vs-extension.md) se si sta scrivendo un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estensione, ad esempio un menu comando o un gestore eventi, l'estensione può utilizzare il servizio del modello di testo per trasformare qualsiasi modello di testo. È possibile passare i dati del parametro nel modello tramite l'oggetto di sessione e ottenere i valori all'interno del modello utilizzando il `<#@parameter#>` direttiva.

 [L'elaborazione dei modelli di testo tramite un Host personalizzato](../modeling/processing-text-templates-by-using-a-custom-host.md) quando viene eseguito il codice del modello di testo, l'host fornisce l'accesso a file esterni e lo stato dell'applicazione. Ad esempio, l'host che esegue le trasformazioni di testo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è possibile accedere a Esplora soluzioni. Inoltre, vengono visualizzati gli errori nella finestra di messaggio di errore. Se si desidera eseguire le trasformazioni di testo in un contesto diverso, è possibile definire il proprio host che consente di accedere ai servizi disponibili in tale contesto.

 Se si sta scrivendo un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estensione, è consigliabile utilizzare il servizio di trasformazione di testo esistente invece di scrivere il proprio host. Per ulteriori informazioni, vedere [richiamo di trasformazione del testo in un'estensione VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Riferimenti

- [Scrive un modello di testo T4](../modeling/writing-a-t4-text-template.md) fornisce la sintassi di direttive di modello di testo e blocchi di controllo.