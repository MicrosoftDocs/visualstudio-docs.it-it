---
title: Utilità CreatePkgDef | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b8ae53766a42ac2ed218bc92f59088d27e4434e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="createpkgdef-utility"></a>Utilità CreatePkgDef
Accetta un file DLL per un'estensione di Visual Studio come un parametro e crea un file. pkgdef che accompagnano il file DLL. Il file. pkgdef contiene tutte le informazioni che verrebbero scritto nel Registro di sistema in caso contrario è installata l'estensione.  
  
> [!NOTE]
>  La maggior parte dei modelli di progetto che vengono automaticamente inclusi in Visual Studio SDK per creare file. pkgdef come parte del processo di compilazione. Questo documento è destinato a coloro che desiderano creare manualmente i pacchetti o convertire i pacchetti esistenti per l'utilizzo di distribuzione. pkgdef.  
  
## <a name="syntax"></a>Sintassi  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>Argomenti  
 /out =`FileName`  
 Obbligatorio. Imposta il nome del file di output. pkgdef per`FileName`.  
  
 /codebase  
 Facoltativo. Registrazione forza con l'utilità della CodeBase.  
  
 /assembly  
 Registrazione forza con l'utilità di Assembly.  
  
 `AssemblyPath`  
 Il percorso del file DLL da cui si desidera generare il. pkgdef.  
  
## <a name="remarks"></a>Note  
 Distribuzione di un'estensione tramite i file. pkgdef sostituisce i requisiti del Registro di sistema delle versioni precedenti di Visual Studio.  
  
 I file. pkgdef devono essere installati in uno dei seguenti percorsi: %localappdata%\Microsoft\Visual Studio\14.0\Extensions\ o %vsinstalldir%\Common7\IDE\Extensions\\. Se la cartella di installazione è %localappdata%\Microsoft\Visual Studio\14.0\Extensions\\, l'estensione verrà riconosciuto da Visual Studio, ma verrà disabilitata per impostazione predefinita. L'utente può abilitare l'estensione tramite **estensioni e aggiornamenti**. Se la cartella di installazione è %vsinstalldir%\Common7\IDE\Extensions\\, l'estensione è abilitata per impostazione predefinita.  
  
> [!NOTE]
>  Il **estensioni e aggiornamenti** strumento non può essere utilizzato per accedere a un'estensione a meno che non viene installato come parte di un pacchetto VSIX.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilità CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md)