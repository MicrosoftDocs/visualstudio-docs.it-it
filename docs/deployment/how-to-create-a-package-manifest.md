---
title: 'Procedura: creare un manifesto di pacchetto | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- package files [Windows Installer]
- package files [ClickOnce]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper packages
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: d36d6c1d4589fa24e4c3e7c53e041d07f359092b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-package-manifest"></a>Procedura: creare un manifesto di pacchetto
Per distribuire i prerequisiti per l'applicazione, è possibile utilizzare un pacchetto del programma di avvio automatico. Un pacchetto del programma di avvio contiene un file manifesto singolo prodotto ma un manifesto di pacchetto per ciascuna lingua. Le funzionalità condivise tra le diverse versioni localizzate devono andare nel manifesto del prodotto.  
  
 Per ulteriori informazioni sui manifesti di pacchetto, vedere [procedura: creare un manifesto del prodotto](../deployment/how-to-create-a-product-manifest.md).  
  
## <a name="creating-the-package-manifest"></a>Creazione del manifesto del pacchetto  
  
#### <a name="to-create-the-package-manifest"></a>Per creare il manifesto di pacchetto  
  
1.  Creare una directory per il pacchetto del programma di avvio automatico. In questo esempio viene utilizzato c:\package.  
  
2.  Creare una sottodirectory con il nome delle impostazioni locali, ad esempio en per la lingua inglese.  
  
3.  In Visual Studio, creare un file XML denominato `package.xml`e salvarlo nella cartella c:\package\en.  
  
4.  Aggiungere codice XML per elencare il nome del pacchetto, le impostazioni cultura per il manifesto di pacchetto di aggiornamento e il contratto di licenza facoltativo. Il codice XML seguente utilizza le variabili `DisplayName` e `Culture`, che sono definite in un elemento successivo.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  Aggiungere codice XML per elencare tutti i file che si trovano nella directory specifiche delle impostazioni locali. Il codice XML seguente viene utilizzato un file denominato EULA che è applicabile per il **en** internazionali.  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  Aggiungere codice XML per definire le stringhe localizzabili per il pacchetto del programma di avvio automatico. Il seguente codice XML aggiunge le stringhe di errore per le impostazioni locali en.  
  
    ```  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7.  Copiare la cartella c:\package. nella directory di avvio automatico di Visual Studio. Per Visual Studio 2010, si tratta della directory di Sdks\windows\v7.0A\Bootstrapper\Packages. \Programmi\Microsoft.  
  
## <a name="example"></a>Esempio  
 Il manifesto del pacchetto contiene informazioni specifiche delle impostazioni locali, ad esempio i messaggi di errore, condizioni di licenza software e i language pack.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Package  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  Name="DisplayName"  
  Culture="Culture"  
  LicenseAgreement="eula.txt">  
  
  <PackageFiles>  
    <PackageFile Name="eula.txt"/>  
  </PackageFiles>  
  
  <Strings>  
    <String Name="DisplayName">Custom Bootstrapper Package</String>  
    <String Name="Culture">en</String>  
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>  
    <String Name="GeneralFailure">A general error has occurred while   
installing this package.</String>  
  </Strings>  
</Package>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti dello schema di prodotti e package](../deployment/product-and-package-schema-reference.md)