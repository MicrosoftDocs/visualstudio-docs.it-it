---
title: Attività Warning | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Warning
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Warning task [MSBuild]
- MSBuild, Warning task
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51c717cc1bc744438afd277e5f154fdcd8852e8d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="warning-task"></a>Attività Warning
Registra un avviso durante una compilazione in base a un'istruzione condizionale valutata.  
  
## <a name="parameters"></a>Parametri  
 Nella tabella che segue vengono descritti i parametri dell'attività `Warning`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`Code`|Parametro `String` facoltativo.<br /><br /> Il codice di avviso da associare all'avviso.|  
|`File`|Parametro `String` facoltativo.<br /><br /> Specifica il file pertinente, se presente. Se non viene indicato alcun file, verrà usato il file contenente l'attività Warning.|  
|`HelpKeyword`|Parametro `String` facoltativo.<br /><br /> Parola chiave della Guida da associare all'avviso.|  
|`Text`|Parametro `String` facoltativo.<br /><br /> Il testo dell'avviso registrato da [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] se il parametro `Condition` restituisce `true`.|  
  
## <a name="remarks"></a>Note  
 L'attività `Warning` consente ai progetti [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] di verificare la presenza di una configurazione o una proprietà richiesta prima di procedere con il passaggio successivo della compilazione.  
  
 Se il parametro `Condition` dell'attività `Warning` restituisce `true`, verrà registrato il valore del parametro `Text` e l'esecuzione della compilazione continua. Se non esiste un parametro `Condition`, viene registrato il testo dell'avviso. Per altre informazioni sulla registrazione, vedere [Obtaining Build Logs](../msbuild/obtaining-build-logs-with-msbuild.md) (Recupero di log di compilazione).  
  
 Oltre ai parametri elencati sopra, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.TaskExtension>, che a sua volta eredita dalla classe <xref:Microsoft.Build.Utilities.Task>. Per un elenco di questi parametri aggiuntivi e le rispettive descrizioni, vedere [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Esempio  
 Nell'esempio di codice seguente viene verificata la presenza di proprietà impostate nella riga di comando. Se non sono presenti proprietà impostate, il progetto genera un evento di avviso e registra il valore del parametro `Text` dell'attività `Warning`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Warning  
            Text=" The 0 property was not set on the command line."  
            Condition="'$(0)' == ''" />  
        <Warning  
            Text=" The FREEBUILD property was not set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Obtaining Build Logs](../msbuild/obtaining-build-logs-with-msbuild.md)  (Recupero di log di compilazione)  
 [Informazioni di riferimento sullo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)