---
title: Copia (acquisizione a livello di codice) | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 67b20a6032a073238f6eb3a8c157c96f95d5c67f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/18/2018
---
# <a name="copy-programmatic-capture"></a>Copia (acquisizione a livello di codice)
Copiare il contenuto del log di grafica (.vsglog) attivo in un nuovo file.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `szNewVSGLog`  
 Nome file del nuovo file di log di grafica.  
  
## <a name="remarks"></a>Note  
 Per copiare le informazioni grafiche in un nuovo file, è necessario avere già acquisito alcune informazioni grafiche; in caso contrario, non accade nulla.