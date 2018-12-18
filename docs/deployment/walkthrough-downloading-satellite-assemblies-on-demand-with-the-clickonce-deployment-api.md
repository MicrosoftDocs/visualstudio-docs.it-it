---
title: 'Procedura dettagliata: Download di assembly Satellite su richiesta con l''API della distribuzione ClickOnce | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, globalization
- localization, Windows Forms
- Windows Forms, localization
- globalization, ClickOnce
- satellite assemblies, ClickOnce
- ClickOnce deployment, on-demand download
- localization, ClickOnce deployment
- ClickOnce deployment, localization
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
caps.latest.revision: "11"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: daa6b9b61083f61d631c6dd55265c338c08ff7f9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>Procedura dettagliata: download di assembly satellite su richiesta con l'API della distribuzione ClickOnce
Le applicazioni Windows Form possono essere configurate per più impostazioni cultura con l'uso di assembly satellite. Un *assembly satellite* è un assembly in cui sono contenute risorse dell'applicazione per impostazioni cultura diverse da quelle predefinite dell'applicazione.  
  
 Come descritto in [localizzazione di applicazioni ClickOnce](../deployment/localizing-clickonce-applications.md), è possibile includere più assembly satellite per più impostazioni cultura all'interno dello stesso [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione. Per impostazione predefinita, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] scaricherà tutti gli assembly satellite nella distribuzione nel computer client, anche se probabilmente un singolo client richiederà un solo assembly satellite.  
  
 Questa procedura dettagliata descrive come contrassegnare gli assembly satellite come facoltativi e scaricare solo l'assembly di cui un computer client ha bisogno per le impostazioni cultura correnti. La procedura seguente usa gli strumenti disponibili in [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. È anche possibile eseguire questa attività in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Vedere anche [Procedura dettagliata: Download di assembly satellite su richiesta con l'API della distribuzione ClickOnce tramite la finestra di progettazione](http://msdn.microsoft.com/library/ms366788\(v=vs.110\)) o [Procedura dettagliata: Download di assembly satellite su richiesta con l'API della distribuzione ClickOnce tramite la finestra di progettazione](http://msdn.microsoft.com/library/ms366788\(v=vs.120\)).  
  
> [!NOTE]
>  Ai fini dell'esecuzione del test, l'esempio di codice seguente imposta a livello di codice le impostazioni cultura su `ja-JP`. Per informazioni su come modificare il codice per un ambiente di produzione, vedere la sezione "Passaggi successivi" più avanti in questo argomento.  
  
## <a name="prerequisites"></a>Prerequisiti  
 In questo argomento si presuppone che siano note le procedure per aggiungere risorse localizzate all'applicazione con Visual Studio. Per istruzioni dettagliate, vedere [Procedura dettagliata: Localizzazione di Windows Form](https://msdn.microsoft.com/en-us/library/vstudio/y99d1cd3\(v=vs.100\).aspx).  
  
### <a name="to-download-satellite-assemblies-on-demand"></a>Per scaricare gli assembly satellite su richiesta  
  
1.  Aggiungere il codice seguente all'applicazione per consentire il download degli assembly satellite su richiesta.  
  
     [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]
     [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]  
  
2.  Generare gli assembly satellite per l'applicazione usando [Resgen.exe (Generatore di File di risorse)](/dotnet/framework/tools/resgen-exe-resource-file-generator) o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3.  Generare un manifesto dell'applicazione o aprire il manifesto dell'applicazione esistente usando MageUI.exe. Per ulteriori informazioni su questo strumento, vedere [MageUI.exe (strumento di modifica, Client grafico e la generazione del manifesto)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client).  
  
4.  Scegliere la scheda **File** .  
  
5.  Scegliere il pulsante con i **puntini di sospensione** (**...**) e selezionare la directory contenente tutti gli assembly e file dell'applicazione, inclusi gli assembly satellite generati con Resgen.exe. I nomi degli assembly satellite sono strutturati come segue: *CodiceIso*\NomeApplicazione.resources.dll, dove *CodiceIso* è un'identificatore del linguaggio in formato RFC 1766.  
  
6.  Fare clic su **Popola** per aggiungere i file alla distribuzione.  
  
7.  Selezionare la casella di controllo **Facoltativo** per ogni assembly satellite.  
  
8.  Impostare il campo di gruppo per ogni assembly satellite sul relativo identificatore di lingua ISO. Per un assembly satellite giapponese, ad esempio, specificare `ja-JP`. In questo modo il codice aggiunto nel passaggio 1 scaricherà l'assembly satellite appropriato, a seconda dell'impostazione della proprietà <xref:System.Threading.Thread.CurrentUICulture%2A> dell'utente.  
  
## <a name="next-steps"></a>Passaggi successivi  
 In un ambiente di produzione sarà probabilmente necessario rimuovere la riga degli esempi di codice usata per impostare la proprietà <xref:System.Threading.Thread.CurrentUICulture%2A> su un valore specifico, perché il valore predefinito per i computer client è quello corretto. Quando l'applicazione è in esecuzione su un computer client giapponese, ad esempio, la proprietà predefinita <xref:System.Threading.Thread.CurrentUICulture%2A> sarà `ja-JP` . L'impostazione di tale valore a livello di codice è un buon metodo per procedere alla verifica degli assembly satellite prima di distribuire l'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Localizzazione delle applicazioni ClickOnce](../deployment/localizing-clickonce-applications.md)