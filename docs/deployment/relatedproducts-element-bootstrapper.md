---
title: '&lt;RelatedProducts&gt; elemento (programma di avvio automatico) | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MSBuild.GenerateBootstrapper.MissingDependency
- MSBuild.GenerateBootstrapper.DuplicateItems
- MSBuild.GenerateBootstrapper.IncludedProductIncluded
- MSBuild.GenerateBootstrapper.DependencyNotFound
- MSBuild.GenerateBootstrapper.PackageFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords: <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 548c1002eae581dc0e231f8dd2e28ee4a8376e27
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt; elemento (programma di avvio automatico)
Il `RelatedProducts` elemento definisce i prodotti che dipendono o sono inclusi nel prodotto corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<RelatedProducts>  
    <DependsOnProduct  
        Code  
    />  
    <EitherProducts>  
        <DependsOnProduct  
            Code  
        />  
    </EitherProducts>  
    <IncludesProduct  
        Code  
    />  
</RelatedProducts>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Il `RelatedProducts` è un elemento figlio del `Product` elemento. Non dispone di attributi.  
  
## <a name="dependsonproduct"></a>DependsOnProduct  
 Il `DependsOnProduct` elemento indica che il prodotto corrente dipende dal prodotto specificato, e pertanto deve essere installato prima di quello corrente. È un figlio di `RelatedProducts` elemento. Oggetto `RelatedProducts` elemento può contenere uno o più `DependsOnProduct` elementi.  
  
 `DependsOnProduct`presenta l'attributo seguente.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Code`|Il nome del prodotto incluso, come specificato dal codice di `ProductCode` attributo del `Product` elemento. Per ulteriori informazioni, vedere [ \<prodotto > elemento](../deployment/product-element-bootstrapper.md).|  
  
## <a name="eitherproducts"></a>EitherProducts  
 Il `EitherProducts` elemento definisce zero o più `DependsOnProduct` elementi, e non ha attributi. Almeno un `DependsOnProduct` in questo set deve essere installato prima del prodotto corrente. Oggetto `RelatedProducts` elemento può contenere zero o più `EitherProducts` elementi.  
  
## <a name="includesproduct"></a>IncludesProduct  
 Il `IncludesProduct` elemento indica che un prodotto è incluso nell'installazione corrente che non richiede un'installazione separata. È un figlio di `RelatedProducts` elemento. Oggetto `RelatedProducts` elemento può contenere uno o più `IncludesProduct` elementi.  
  
 `IncludesProduct`presenta l'attributo seguente.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Code`|Il nome del prodotto incluso, come specificato dal codice di `ProductCode` attributo del `Product` elemento. Per ulteriori informazioni, vedere [ \<prodotto > elemento](../deployment/product-element-bootstrapper.md).|  
  
## <a name="example"></a>Esempio  
 Esempio di codice seguente specifica che Microsoft Installer viene installato con il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]e pertanto non richiede un'installazione separata.  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [\<Prodotto > elemento](../deployment/product-element-bootstrapper.md)