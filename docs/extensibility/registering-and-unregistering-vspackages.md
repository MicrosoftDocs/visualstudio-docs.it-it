---
title: La registrazione e annullamento della registrazione di pacchetti VSPackage | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: "35"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7e82b299398d83509883ff152c5f97bd43e800b3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="registering-and-unregistering-vspackages"></a>Registrazione e annullamento della registrazione VSPackage
Utilizzare gli attributi per registrare un VSPackage, ma  
  
## <a name="registering-a-vspackage"></a>Registrazione di un pacchetto VSPackage  
 È possibile utilizzare gli attributi per controllare la registrazione dei pacchetti VSPackage gestiti. Tutte le informazioni di registrazione sono contenute in un file. pkgdef. Per ulteriori informazioni sulla registrazione basata su file, vedere [CreatePkgDef utilità](../extensibility/internals/createpkgdef-utility.md).  
  
 Il codice seguente viene illustrato come utilizzare gli attributi di registrazione standard per registrare il pacchetto VSPackage.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>L'annullamento della registrazione di un'estensione  
 Se si desidera rimuoverli dall'istanza sperimentale provato con molta VSPackage diversi, è possibile eseguire semplicemente il **reimpostare** comando. Cercare **reimpostare l'istanza sperimentale di Visual Studio** nella pagina di avvio del computer, o eseguire questo comando dalla riga di comando:  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Se si desidera disinstallare un'estensione che è stato installato l'istanza di sviluppo di Visual Studio, passare a **strumenti / estensioni e aggiornamenti**, trovare l'estensione e fare clic su **Disinstalla**.  
  
 Se per qualche motivo nessuno di questi metodi ha esito positivo in la disinstallazione dell'estensione, è possibile annullare la registrazione di assembly VSPackage dalla riga di comando come segue:  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>  
```  
  
<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>  
  
## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Utilizzare un attributo di registrazione personalizzato per registrare un'estensione  
  
In alcuni casi potrebbe essere necessario creare un nuovo attributo di registrazione per l'estensione. Per aggiungere nuove chiavi del Registro di sistema o per aggiungere nuovi valori alle chiavi esistente, è possibile utilizzare gli attributi di registrazione. Il nuovo attributo deve derivare da <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, e deve eseguire l'override di <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> e <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> metodi.  
  
### <a name="creating-a-custom-attribute"></a>Creazione di un attributo personalizzato  
  
Il codice seguente viene illustrato come creare un nuovo attributo di registrazione.  
  
```csharp  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
```  
  
 Il <xref:System.AttributeUsageAttribute> viene utilizzato in classi di attributi per specificare l'elemento di programma (classe, metodo, e così via) a cui l'attributo relativo, che può essere utilizzato più di una volta e se può essere ereditata.  
  
### <a name="creating-a-registry-key"></a>Creazione di una chiave del Registro di sistema  
  
Nel codice seguente, l'attributo personalizzato viene creato un **personalizzato** sottochiave sotto la chiave per il pacchetto VSPackage che deve essere registrato.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
```  
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>Creazione di un nuovo valore in una chiave del Registro di sistema esistente  
  
È possibile aggiungere valori personalizzati a una chiave esistente. Il codice seguente viene illustrato come aggiungere un nuovo valore a una chiave di registrazione del pacchetto VSPackage.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
```
  
## <a name="see-also"></a>Vedere anche  
 [Pacchetti VSPackage](../extensibility/internals/vspackages.md)