---
title: Recupero di log di compilazione con MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c6953017a034257900c467e7f2fac89897fa0d9e
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="obtaining-build-logs-with-msbuild"></a>Recupero di log di compilazione con MSBuild
Usando le opzioni con MSBuild, è possibile specificare quanti dati di compilazione si vogliono esaminare e se salvare i dati di compilazione in uno o più file. È anche possibile specificare un logger personalizzato per raccogliere i dati di compilazione. Per informazioni sulle opzioni della riga di comando di MSBuild, non illustrate in questo argomento, vedere [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
>  Se si compilano progetti usando l'IDE di Visual Studio, è possibile risolvere i problemi di tali compilazioni esaminando i log di compilazione. Per altre informazioni, vedere [Procedura: Visualizzare, salvare e configurare file di log di compilazione](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
## <a name="setting-the-level-of-detail"></a>Impostazione del livello di dettaglio  
 Quando si compila un progetto usando MSBuild senza specificare un livello di dettaglio, nel log di output vengono visualizzate le informazioni seguenti:  
  
-   Errori, avvisi e messaggi classificati come molto importanti.  
  
-   Alcuni eventi di stato.  
  
-   Riepilogo della compilazione.  
  
 Usando l'opzione **/verbosity** (**/v**), è possibile controllare quanti dati vengono visualizzati nel log di output. Per la risoluzione dei problemi, usare un livello di dettaglio `detailed` (`d`) o `diagnostic` (`diag`), che fornisce la maggior parte delle informazioni.  
  
 Il processo di compilazione può essere più lento quando si imposta **/verbosity** su `detailed` e ancora più lento quando si imposta **/verbosity** su `diagnostic`.  
  
```  
msbuild MyProject.proj /t:go /v:diag  
```  

## <a name="saving-the-build-log-to-a-file"></a>Salvataggio del log di compilazione in un file  
 È possibile usare l'opzione **/fileLogger** (**fl**) per salvare i dati di compilazione in un file. L'esempio seguente salva i dati di compilazione in un file denominato `msbuild.log`.  
  
```  
msbuild MyProject.proj /t:go /fileLogger  
```  
  
 Nell'esempio seguente il file di log è denominato `MyProjectOutput.log` e il dettaglio dell'output del log è impostato su `diagnostic`. Per specificare queste due impostazioni, si usa l'opzione **/filelogparameters** (`flp`).  
  
```  
msbuild MyProject.proj /t:go /fl /flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 Per altre informazioni, vedere [Command-Line Reference](../msbuild/msbuild-command-line-reference.md) (Informazioni di riferimento sulla riga di comando).  
  
## <a name="saving-the-log-output-to-multiple-files"></a>Salvataggio dell'output del log in più file  
 L'esempio seguente salva l'intero log in `msbuild1.log`, gli errori soltanto in `JustErrors.log` e gli avvisi soltanto in `JustWarnings.log`. L'esempio usa numeri di file per ognuno dei tre file. I numeri di file vengono specificati subito dopo le opzioni **/fl** e **/flp**, ad esempio `/fl1` e `/flp1`.  
  
 Le opzioni **/filelogparameters** (`flp`) per i file 2 e 3 specificano il nome da assegnare a ogni file e che cosa includere in ogni file. Poiché per il file 1 non è specificato alcun nome, viene usato il nome predefinito `msbuild1.log`.  
  
```  
msbuild MyProject.proj /t:go /fl1 /fl2 /fl3 /flp2:logfile=JustErrors.log;errorsonly /flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 Per altre informazioni, vedere [Command-Line Reference](../msbuild/msbuild-command-line-reference.md) (Informazioni di riferimento sulla riga di comando).  

## <a name="saving-a-binary-log"></a>Salvataggio di un log binario

È possibile salvare il log in formato binario compresso usando l'opzione **/binaryLogger** (**bl**). Il log include una descrizione dettagliata del processo di compilazione e può essere letto da alcuni strumenti di analisi dei log.

Nell'esempio seguente viene creato un file di log binario con il nome `binarylogfilename`.

```  
/bl:binarylogfilename.binlog
``` 
 
Per altre informazioni, vedere [Command-Line Reference](../msbuild/msbuild-command-line-reference.md) (Informazioni di riferimento sulla riga di comando).  

## <a name="using-a-custom-logger"></a>Utilizzo di un logger personalizzato  
 Per scrivere un logger personalizzato, è sufficiente creare un tipo gestito che implementi l'interfaccia <xref:Microsoft.Build.Framework.ILogger>. È possibile usare un logger personalizzato, ad esempio, per inviare gli errori di compilazione in un messaggio di posta elettronica, registrarli in un database o registrarli in un file XML. Per altre informazioni, vedere [Logger di compilazione](../msbuild/build-loggers.md).  
  
 Nella riga di comando di MSBuild, per specificare il logger personalizzato, si usa l'opzione **/logger**. È anche possibile usare l'opzione **/noconsolelogger** per disabilitare il logger di console predefinito.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [Logger di compilazione](../msbuild/build-loggers.md)   
 [Registrazione in un ambiente a più processori](../msbuild/logging-in-a-multi-processor-environment.md)   
 [Creazione di logger di inoltro](../msbuild/creating-forwarding-loggers.md)   
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)