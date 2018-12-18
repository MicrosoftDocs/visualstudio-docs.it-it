---
title: Le risorse nei pacchetti VSPackage | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d252f61a9f634f4bb8435626c41c586bbe5cb839
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="resources-in-vspackages"></a>Risorse nei pacchetti VSPackage
È possibile incorporare le risorse localizzate in nativa dell'interfaccia utente DLL satellite, le DLL satellite gestite, o in un pacchetto VSPackage gestito se stesso.  
  
 Alcune risorse non possono essere incorporate in VSPackage. I seguenti tipi gestiti possono essere incorporati:  
  
-   Stringhe  
  
-   Chiavi di caricamento package (che sono anche stringhe)  
  
-   Icone della finestra dello strumento  
  
-   File di Output di tabella comandi (CTO) compilati  
  
-   Bitmap CTO  
  
-   Guida della riga di comando  
  
-   Sui dati della finestra di dialogo  
  
 Selezionare le risorse in un pacchetto gestito l'ID risorsa. Un'eccezione è il file CTO, che deve essere denominato CTMENU. Il file CTO deve essere presente nella tabella delle risorse come un `byte[]`. Tutti gli altri elementi di risorsa sono identificati dal tipo.  
  
 È possibile utilizzare il <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> attributo per indicare al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che siano disponibili le risorse gestite.  
  
 [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
 [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]  
  
 Impostazione <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> indica che in questo modo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve ignorare le DLL satellite non gestita durante la ricerca di risorse, ad esempio, tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>. Se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rileva due o più risorse aventi lo stesso ID di risorsa, viene utilizzata la prima risorsa trova.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente è una rappresentazione gestita di un'icona di finestra dello strumento.  
  
```  
<data name="1001"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyToolWinIcon.bmp;  
     System.Drawing.Bitmap,  
     System.Drawing,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
 Nell'esempio seguente viene illustrato come incorporare la matrice di byte CTO, che deve essere denominata CTMENU.  
  
```  
<data name="CTMENU"  
type="System.Resources.ResXFileRef,System.Windows.Forms">  
     <value>  
     MyPackage.cto;  
     System.Byte[],  
     mscorlib,  
     Version=1.0.0.0,  
     Culture=neutral,  
     PublicKeyToken=b03f5f7f11d50a3a  
     </value>  
</data>  
```  
  
## <a name="implementation-notes"></a>Note di implementazione  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] caricamento di ritardi di VSPackage laddove possibile. Una conseguenza di incorporamento di un file CTO in un pacchetto VSPackage è che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve caricare tutti questi pacchetti VSPackage in memoria durante l'installazione, ovvero quando viene generata una tabella unita di comando. Risorse possono essere estratto da un pacchetto VSPackage esaminando i metadati senza eseguire il codice nel pacchetto VSPackage. Il pacchetto VSPackage non inizializzato in questo momento, pertanto il calo delle prestazioni è minimo.  
  
 Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le richieste di una risorsa da un pacchetto VSPackage dopo l'installazione, tale pacchetto è probabilmente già caricato e inizializzato, pertanto il calo delle prestazioni è minimo.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione dei pacchetti VSPackage](../../extensibility/managing-vspackages.md)   
 [Risorse localizzate in applicazioni MFC: DLL satellite](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)   
