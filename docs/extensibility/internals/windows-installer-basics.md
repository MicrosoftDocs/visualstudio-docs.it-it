---
title: Nozioni fondamentali di Windows Installer | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Installer, VSPackages
- VSPackages, Windows Installer basics
ms.assetid: 497e479b-add8-4644-870a-917f15306b97
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1a9f895db0d202dd573e7c665b1185f6e3f4b751
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="windows-installer-basics"></a>Nozioni fondamentali di Windows Installer
Windows Installer installa e rimuove le applicazioni o i prodotti software sul computer dell'utente, queste attività in unità denominate, talvolta denominati WICs o solo i componenti, i componenti di Windows Installer. Un GUID identifica ogni WIC, ovvero l'unità fondamentale di installazione e conteggio dei riferimenti per le installazioni tramite Windows Installer.  
  
 Per la documentazione completa di Windows Installer, vedere l'argomento di Platform SDK, [Windows Installer](http://msdn.microsoft.com/library/aa372866.aspx).  
  
## <a name="authoring-a-vspackage"></a>Creazione di un pacchetto VSPackage  
 Windows Installer utilizza i pacchetti di installazione, che contengono informazioni che è necessario Windows Installer per installare, disinstallare o ripristinare un prodotto e per eseguire il programma di installazione interfaccia (). Ogni pacchetto di installazione di un file con estensione msi, che contiene un database di installazione, un flusso di informazioni di riepilogo e i flussi di dati per varie parti dell'installazione. Per utilizzare il programma di installazione, è necessario creare un'installazione. Poiché il programma di installazione consente di organizzare le installazioni sul concetto di componenti e archivia le informazioni sull'installazione in un database relazionale, il processo di creazione di un pacchetto di installazione su vasta scala comporta i passaggi seguenti:  
  
1.  Pianificare l'installazione di authoring per supportare il controllo delle versioni e le strategie side-by-side.  
  
2.  Identificare le funzionalità da presentare agli utenti.  
  
3.  Organizzare i VSPackage e le dipendenze in componenti.  
  
4.  Popolare il database di installazione con le informazioni.  
  
5.  Convalidare il pacchetto di installazione.  
  
 Questa documentazione si occupa principalmente il primo e terzo passaggio del processo. Durante questa procedura organizzare le funzionalità di VSPackage WICs in modo è possibile definire il controllo delle versioni e la manutenzione di una strategia per le versioni successive di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. I rimanenti tre passaggi sono illustrati in dettaglio nella documentazione di Windows Installer in Platform SDK.  
  
## <a name="key-terms"></a>Termini chiave  
 Di seguito sono definizioni dei termini chiave relativi alla tecnologia Windows Installer.  
  
 Risorsa  
 I file, chiavi del Registro di sistema, collegamenti, o e così via che può essere installato in un computer. Queste risorse sono raggruppate logicamente in componenti di Windows Installer.  
  
 Componente di Windows Installer (WIC)  
 L'unità di installazione che rappresenta un raggruppamento logico di risorse correlate in cui sono installati e disinstallati come un'unità di base. Componenti di Windows Installer sono identificati da un ID univoco di componente o un GUID. Inoltre, Windows Installer mantiene il riferimento a livello di WIC di conteggio. Per la flessibilità massima controllo delle versioni, includere non più di una risorsa primaria, ad esempio una DLL, in un determinato WIC. Si noti che dopo individuare e popolare un WIC, assegnargli un GUID e distribuirlo, è possibile modificare la composizione. Per ulteriori informazioni, vedere [organizzazione delle applicazioni in componenti](http://msdn.microsoft.com/library/aa370561.aspx).  
  
 Pacchetto (pacchetto Redist)  
 Unità di distribuzione che è costituito da un file con estensione msi e i file di origine esterna a cui questo file potrebbe fare riferimento. Un pacchetto contiene tutte le informazioni necessarie per eseguire l'interfaccia utente e per installare o disinstallare l'applicazione Windows Installer.  
  
 file con estensione msi  
 Un file di archiviazione strutturata COM contenente le istruzioni e i dati necessari per installare un'applicazione. Ogni pacchetto contiene almeno un file con estensione msi. Il file con estensione msi contiene il database di programma di installazione, un flusso di informazioni di riepilogo e probabilmente una o più trasformazioni e i file di origine interna. Installazione di file possono essere compressi in un file CAB e archiviati in un flusso di file con estensione msi o archiviati, compressi o non compressi, all'esterno del file con estensione msi nel supporto di origine. Per ulteriori informazioni, vedere [estensioni di File di Windows Installer](http://msdn.microsoft.com/library/aa372842\(VS.85\).aspx).  
  
## <a name="windows-installer-rules-enforcement"></a>Imposizione delle regole di Windows Installer  
 Due set di regole determinano la distribuzione delle risorse attraverso i componenti del programma di installazione. Un set di regole viene aggiornato dal programma di installazione di Windows, è necessario applicare il secondo set come autore di installazione.  
  
> [!NOTE]
>  Imposizione delle regole di Windows Installer si verifica solo se si esegue una convalida del file con estensione msi. Tuttavia, vengono avvisati da considerare queste regole come procedure consigliate. Per ulteriori informazioni, vedere [la convalida di un Database di installazione](http://msdn.microsoft.com/library/aa372477\(VS.85\).aspx) e [convalida del pacchetto](http://msdn.microsoft.com/library/aa370569\(VS.85\).aspx).  
  
#### <a name="installer-enforced-rules"></a>Regole applicate al programma di installazione  
  
-   Tutti i file in un determinato componente devono essere installati nella stessa directory. Al contrario, i file installati in cartelle separate devono appartenere per separare i componenti.  
  
-   Può essere presente solo un percorso di chiave per ogni componente. Il percorso della chiave è semplicemente una chiave del Registro di sistema o di file che rappresenta l'intero componente.  
  
#### <a name="component-provider-responsibilities"></a>Responsabilità di Provider di componenti  
  
-   Le due risorse che potrebbe essere fornito separatamente nelle versioni successive devono essere presenti in componenti separati. Le risorse devono essere raggruppate nel componente stesso solo quando si è certi che queste risorse mai verranno fornito separatamente. In effetti, è consigliabile che tutte le risorse primarie (DLL, ad esempio) esistono sempre nello WICs separato. Per ulteriori informazioni, vedere [che definisce i componenti di installazione](http://msdn.microsoft.com/library/aa368269\(VS.85\).aspx).  
  
-   Alcuna risorsa con controllo delle versioni non deve spedire mai in più WIC.  
  
## <a name="see-also"></a>Vedere anche  
 [Cosa accade se le regole di componente vengono interrotte.](http://msdn.microsoft.com/library/aa372795\(VS.85\).aspx)