---
title: '&lt;PackageFiles&gt; elemento (programma di avvio automatico) | Documenti Microsoft'
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
helpviewer_keywords: <PackageFiles> element [bootstrapper]
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
caps.latest.revision: "16"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 25ba72b511782c450b882826a3e3af94a14f6e20
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="ltpackagefilesgt-element-bootstrapper"></a>&lt;PackageFiles&gt; elemento (programma di avvio automatico)
Il `PackageFiles` elemento contiene `PackageFile` elementi, che definiscono i pacchetti di installazione eseguiti come risultato del `Command` elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<PackageFiles  
    CopyAllPackageFiles  
>  
    <PackageFile   
        Name  
        HomeSite  
        CopyOnBuild  
        PublicKey  
        Hash  
    />  
</PackageFiles>  
```  
  
## <a name="elements-and-attributes"></a>Elementi e attributi  
 Il `PackageFiles` elemento presenta l'attributo seguente.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`CopyAllPackageFiles`|Facoltativo. Se impostato su `false`, il programma di installazione scaricherà solo file a cui fa riferimento il `Command` elemento. Se impostato su `true`, tutti i file verranno scaricati.<br /><br /> Se impostato su `IfNotHomesite`, il programma di installazione si comporterà come se `False` se `ComponentsLocation` è impostato su `HomeSite`e in caso contrario si comporterà come se `True`. Questa impostazione può essere utile per consentire i pacchetti che sono a loro volta programmi di avvio automatico eseguire il proprio comportamento in uno scenario HomeSite.<br /><br /> Il valore predefinito è `true`.|  
  
## <a name="packagefile"></a>PackageFile  
 Il `PackageFile` è un elemento figlio del `PackageFiles` elemento. Oggetto `PackageFiles` l'elemento deve avere almeno un `PackageFile` elemento.  
  
 `PackageFile`presenta gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Name`|Obbligatorio. Il nome del file del pacchetto. Si tratta del nome che il `Command` elemento farà riferimento al momento della definizione di condizioni di installazione di un pacchetto. Questo valore viene inoltre utilizzato come chiave nel `Strings` tabella per recuperare il nome localizzato strumenti, ad esempio [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] verrà utilizzato per descrivere il pacchetto.|  
|`HomeSite`|Facoltativo. Il percorso del pacchetto nel server remoto, se non è incluso con il programma di installazione.|  
|`CopyOnBuild`|Facoltativo. Specifica se il programma di avvio automatico deve copiare il file del pacchetto sul disco in fase di compilazione. Il valore predefinito è true.|  
|`PublicKey`|La chiave crittografata pubblica del firmatario certificato del pacchetto. Obbligatorio se `HomeSite` è utilizzata; in caso contrario, facoltativo.|  
|`Hash`|Facoltativo. Un hash SHA1 del file del pacchetto. Viene utilizzato per verificare l'integrità del file al momento dell'installazione. Se non è possibile calcolare l'hash identico dal file di pacchetto, il pacchetto non essere installato.|  
  
## <a name="example"></a>Esempio  
 L'esempio di codice seguente definisce pacchetti per il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] pacchetto ridistribuibile e le relative dipendenze, ad esempio il programma di installazione di Windows.  
  
```  
<PackageFiles>  
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>  
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetchk.exe"/>  
</PackageFiles>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [\<Prodotto > elemento](../deployment/product-element-bootstrapper.md)   
 [\<Pacchetto > elemento](../deployment/package-element-bootstrapper.md)   
 [Riferimenti dello schema di prodotti e package](../deployment/product-and-package-schema-reference.md)