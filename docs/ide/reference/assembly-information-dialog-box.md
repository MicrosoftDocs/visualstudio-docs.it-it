---
title: Finestra di dialogo Informazioni assembly | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 07c81e392a4513ffa97a384e9aa60147c3a71290
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="assembly-information-dialog-box"></a>Finestra di dialogo Informazioni assembly
È possibile usare la finestra di dialogo **Informazioni assembly** per specificare i valori degli attributi globali degli assembly di [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] che vengono archiviati nel file AssemblyInfo creato automaticamente insieme al progetto. In **Esplora soluzioni** il file è contenuto nel nodo **My Project** (Progetto) in [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]. Fare clic su **Mostra tutti i file** per visualizzarlo. Si trova in **Proprietà** in [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Per altre informazioni sugli attributi degli assembly, vedere [Attributi](http://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205).  
  
 Per accedere a questa finestra di dialogo, selezionare un nodo di progetto in **Esplora soluzioni**, fare clic su **Proprietà** dal menu **Progetto**. Quando si apre **Creazione progetti**, fare clic sulla scheda **Applicazione**. Nella pagina **Applicazione** scegliere il pulsante **Informazioni assembly**.  
  
## <a name="uielement-list"></a>Elenco UIElement  
 **Titolo**  
 Specifica un titolo per il manifesto dell'assembly. Corrisponde a <xref:System.Reflection.AssemblyTitleAttribute>.  
  
 **Descrizione**  
 Specifica una descrizione facoltativa per il manifesto dell'assembly. Corrisponde a <xref:System.Reflection.AssemblyDescriptionAttribute>.  
  
 **Società**  
 Specifica il nome di una società per il manifesto dell'assembly. Corrisponde a <xref:System.Reflection.AssemblyCompanyAttribute>.  
  
 **Prodotto**  
 Specifica il nome di un prodotto per il manifesto dell'assembly. Corrisponde a <xref:System.Reflection.AssemblyProductAttribute>.  
  
 **Copyright**  
 Specifica le informazioni sul copyright per il manifesto dell'assembly. Corrisponde a <xref:System.Reflection.AssemblyCopyrightAttribute>.  
  
 **Marchio**  
 Specifica un marchio per il manifesto dell'assembly. Corrisponde a <xref:System.Reflection.AssemblyTrademarkAttribute>.  
  
 **Versione assembly**  
 Specifica la versione dell'assembly. Corrisponde a <xref:System.Reflection.AssemblyVersionAttribute>.  
  
 **Versione file**  
 Specifica a un numero di versione che indica al compilare di usare una versione specifica per la risorsa della versione del file Win32. Corrisponde a <xref:System.Reflection.AssemblyFileVersionAttribute>.  
  
 **GUID**  
 Un GUID univoco che identifica l'assempbly. Quando si crea un progetto, Visual Studio genera un GUID per l'assembly. Corrisponde a <xref:System.Guid>.  
  
 **Lingua di sistema**  
 Specifica le impostazioni cultura supportate dall'assembly. Corrisponde a <xref:System.Resources.NeutralResourcesLanguageAttribute>. L'impostazione predefinita è **(Nessuna)**.  
  
 **Rendi assembly visibile a COM**  
 Specifica se i tipi nell'assembly saranno disponibili a COM. Corrisponde a <xref:System.Runtime.InteropServices.ComVisibleAttribute>.  
  
## <a name="see-also"></a>Vedere anche  
 [Application Page, Project Designer (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)  (Pagina Applicazione, Creazione progetti (Visual Basic))  
 [Attributi](http://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)