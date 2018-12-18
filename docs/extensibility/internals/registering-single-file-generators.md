---
title: Registrazione di generatori di File singolo | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b9b7d16a9e473028d85540f4447d9981382be0fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="registering-single-file-generators"></a>Registrazione di generatori di File singolo
Per rendere disponibili in uno strumento personalizzato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], è necessario registrare in modo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] possibile crearne un'istanza e lo associa a un particolare tipo di progetto.  
  
### <a name="to-register-a-custom-tool"></a>Per registrare uno strumento personalizzato  
  
1.  Registrare il DLL dello strumento personalizzato sia nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Registro di sistema locale o nel Registro di sistema in HKEY_CLASSES_ROOT.  
  
     Ad esempio, ecco le informazioni di registrazione per lo strumento personalizzato a MSDataSetGenerator gestito, viene fornito con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2.  Creare una chiave del Registro di sistema nell'oggetto desiderato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hive in generatori\\*GUID* in *GUID* è il GUID definito dal sistema del progetto o un servizio del linguaggio specifico. Il nome della chiave diventa il nome a livello di uno strumento personalizzato. La chiave dello strumento personalizzato presenta i seguenti valori:  
  
    -   (Predefinito)  
  
         Facoltativo. Fornisce una descrizione semplice dello strumento personalizzato. Questo parametro è facoltativo ma consigliato.  
  
    -   CLSID  
  
         Obbligatorio. Specifica l'identificatore della libreria di classi del componente COM che implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>.  
  
    -   GeneratesDesignTimeSource  
  
         Obbligatorio. Indica se i tipi di file generati da questo strumento personalizzato vengono resi disponibili per finestre di progettazione visiva. Il valore di questo parametro deve essere (zero) 0 per i tipi non disponibili per finestre di progettazione visiva o 1 (uno) per i tipi disponibili per finestre di progettazione visiva.  
  
    > [!NOTE]
    >  È necessario registrare lo strumento personalizzato separatamente per ogni lingua che si desidera utilizzare lo strumento personalizzato sia disponibile.  
  
     Ad esempio, il MSDataSetGenerator registra una volta per ogni lingua:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]  
    @="Microsoft VB Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]  
    @="Microsoft C# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [Implementazione di generatori di File singolo](../../extensibility/internals/implementing-single-file-generators.md)   
 [Esposizione di tipi di finestre di progettazione visiva](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [Introduzione all'oggetto BuildManager](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)