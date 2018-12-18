---
title: Interfaccia IDebugDocumentProvider | Documenti Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentProvider interface
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 262794718e238068cfd9a8e3fae5161b9fe8cc54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentprovider-interface"></a>Interfaccia IDebugDocumentProvider
Fornisce i mezzi per creare un'istanza di un documento su richiesta.  
  
## <a name="remarks"></a>Note  
 In questo modo indiretto per creare un'istanza di un documento:  
  
-   Consente il documento da caricare quando necessario.  
  
-   Consente all'oggetto documento devono essere contenuti all'interno del debugger IDE.  
  
-   Consente più modi accedere all'oggetto documento stesso.  
  
 Comporta la separa il documento dal relativo provider e consente al provider per ulteriori informazioni sul contesto di runtime, eseguire.  
  
 Oltre ai metodi ereditati da `IDebugDocumentInfo`, `IDebugDocumentProvider` interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|Fa sì che il documento deve essere creata un'istanza se non esiste già.|