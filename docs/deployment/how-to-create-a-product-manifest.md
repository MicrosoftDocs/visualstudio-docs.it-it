---
title: 'Procedura: creare un manifesto del prodotto | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- product files [ClickOnce]
- product files [Windows Installer]
- prerequisites, custom bootstrapper package
- dependencies, custom bootstrapper package
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
caps.latest.revision: "10"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 071bfa46df7e11f760bc32cda0a732388835d2d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-product-manifest"></a>Procedura: creare il manifesto di un prodotto
Per distribuire i prerequisiti per l'applicazione, è possibile creare un pacchetto del programma di avvio automatico. Un pacchetto del programma di avvio contiene un file manifesto singolo prodotto ma un manifesto di pacchetto per ciascuna lingua. Il manifesto del pacchetto contiene gli aspetti specifici di localizzazione del pacchetto. Ciò include stringhe, i contratti di licenza dell'utente finale e i language pack.  
  
 Per ulteriori informazioni sui manifesti di prodotto, vedere [procedura: creare un manifesto del pacchetto](../deployment/how-to-create-a-package-manifest.md).  
  
## <a name="creating-the-product-manifest"></a>Creazione del manifesto del prodotto  
  
#### <a name="to-create-the-product-manifest"></a>Per creare il manifesto del prodotto  
  
1.  Creare una directory per il pacchetto del programma di avvio automatico. In questo esempio viene utilizzato c:\package.  
  
2.  In Visual Studio, creare un nuovo file XML denominato `product.xml`e salvarlo nella cartella c:\package.  
  
3.  Aggiungere il seguente codice XML per descrivere il codice di prodotto e lo spazio dei nomi XML per il pacchetto. Sostituire il codice prodotto con un identificatore univoco per il pacchetto.  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4.  Aggiungere codice XML per specificare che il pacchetto ha una dipendenza. In questo esempio viene utilizzata una dipendenza su Microsoft Windows Installer 3.1.  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5.  Aggiungere codice XML per elencare tutti i file del pacchetto del programma di avvio automatico. In questo esempio viene utilizzato il nome di file di pacchetto CorePackage. msi.  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6.  Copiare o spostare il file CorePackage. msi nella cartella c:\package.  
  
7.  Aggiungere codice XML per installare il pacchetto utilizzando i comandi di avvio automatico. Aggiunge automaticamente il programma di avvio automatico di **/qn** flag per il file con estensione msi, che consente l'installazione invisibile all'utente. Se il file è un .exe, il programma di avvio viene eseguito il file .exe mediante la shell. Il codice XML seguente non Mostra argomenti per CorePackage. msi, ma è possibile inserire l'attributo di argomenti argomento della riga di comando.  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8.  Aggiungere il codice XML seguente per verificare se è installato il pacchetto del programma di avvio automatico. Sostituire il codice prodotto con il GUID per il componente ridistribuibile.  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. Aggiungere codice XML per modificare il comportamento del programma di avvio automatico a seconda se è già installato il componente del programma di avvio automatico. Se è installato il componente, non si esegue il pacchetto del programma di avvio automatico. Il codice XML seguente controlla se l'utente corrente è un amministratore, poiché questo componente richiede privilegi amministrativi.  
  
    ```  
    <InstallConditions>  
        <BypassIf   
           Property="IsMsiInstalled"   
           Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
            Compare="ValueNotEqualTo" Value="True"  
            String="NotAnAdmin"/>  
    </InstallConditions>  
    ```  
  
10. Aggiungere codice XML per impostare i codici di uscita se l'installazione è riuscita e se è necessario un riavvio. Il codice XML seguente viene illustrato che l'esito negativo e FailReboot codici, che indicano che il programma di avvio non continuerà l'installazione dei pacchetti di uscita.  
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. Aggiungere il seguente codice XML per terminare una sezione per i comandi di avvio automatico.  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. Spostare la cartella c:\package. nella directory di avvio automatico di Visual Studio. Per Visual Studio 2010, si tratta della directory di Sdks\windows\v7.0A\Bootstrapper\Packages. \Programmi\Microsoft.  
  
## <a name="example"></a>Esempio  
 Il manifesto del prodotto contiene le istruzioni di installazione per i prerequisiti personalizzati.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Product  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  ProductCode="Custom.Bootstrapper.Package">  
  
  <RelatedProducts>  
    <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
  </RelatedProducts>  
  
  <PackageFiles>  
    <PackageFile Name="CorePackage.msi"/>  
  </PackageFiles>  
  
  <InstallChecks>  
    <MsiProductCheck Product="IsMsiInstalled"   
      Property="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
  </InstallChecks>  
  
  <Commands>  
    <Command PackageFile="CorePackage.msi" Arguments="">  
  
      <InstallConditions>  
        <BypassIf Property="IsMsiInstalled"  
          Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
          Compare="ValueNotEqualTo" Value="True"  
         String="NotAnAdmin"/>  
      </InstallConditions>  
  
      <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
      </ExitCodes>  
    </Command>  
  </Commands>  
</Product>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti dello schema di prodotti e package](../deployment/product-and-package-schema-reference.md)