---
title: 'CA2210: Gli assembly devono avere nomi sicuri validi'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b7421cee4e1b561d4efec7b843d12a7dcf5a67a6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: Gli assembly devono avere nomi sicuri validi
|||
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|Category|Microsoft.Design|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un assembly non è firmato con un nome sicuro, non è possibile verificare il nome sicuro o il nome sicuro non sarebbe valido senza le impostazioni del Registro di sistema corrente del computer.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola recupera e verifica il nome sicuro di un assembly. Si verifica una violazione, se si verifica una delle operazioni seguenti:

-   L'assembly non ha un nome sicuro.

-   L'assembly è stato modificato dopo la firma.

-   L'assembly è impostata la firma ritardata.

-   L'assembly è firmato in modo non corretto o la firma non è riuscita.

-   L'assembly non richieda le impostazioni del Registro di sistema superare la verifica. Ad esempio, lo strumento nome sicuro (Sn.exe) è stato usato per ignorare la verifica per l'assembly.

 Il nome sicuro protegge i client dal caricamento involontario di un assembly alterato. Gli assembly con nomi sicuri non devono essere distribuiti al di fuori di scenari molto limitati. Se si condividono o distribuiscono assembly non firmati correttamente, l'assembly può essere alterato, non essere caricato in Common Language Runtime oppure l'utente potrebbe avere la necessità di disabilitare la verifica nel proprio computer. Un assembly senza nome sicuro ha i seguenti svantaggi:

-   Non è possibile verificare le origini.

-   Common language runtime non è possibile avvisare gli utenti se il contenuto dell'assembly è stato alterato.

-   Non può essere caricato nella global assembly cache.

 Si noti che, per caricare e analizzare un assembly con firma ritardata, è necessario disabilitare la verifica dell'assembly.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 **Per creare un file di chiave**

 Utilizzare una delle procedure riportate di seguito:

-   Utilizzare lo strumento Assembly Linker (Al.exe) fornito dal [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] SDK.

-   Per il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] versione 1.0 o 1.1, utilizzare il <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> o <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> attributo.

-   Per il [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], utilizzare il `/keyfile` o `/keycontainer` l'opzione del compilatore [/KEYFILE (specificare Key o coppia di chiavi per firmare un Assembly)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly) o [/KEYCONTAINER (specificare un contenitore di chiavi per firmare un Assembly)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly) opzione del linker in C++).

 **Per firmare l'assembly con un nome sicuro in Visual Studio**

1.  In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], aprire la soluzione.

2.  In **Esplora soluzioni**destro del mouse sul progetto e quindi fare clic su **proprietà.**

3.  Fare clic su di **firma** scheda e selezionare il **firmare l'assembly** casella di controllo.

4.  Da **Scegli un file chiave con nome sicuro**selezionare **New**.

     Il **Crea chiave con nome sicuro** verrà visualizzata la finestra.

5.  In **nome file di chiave**, digitare un nome per la chiave con nome sicuro.

6.  Scegliere se proteggere la chiave con una password e quindi fare clic su **OK**.

7.  In **Esplora**, mouse sul progetto e quindi fare clic su **compilare**.

 **Per firmare l'assembly con un nome sicuro all'esterno di Visual Studio**

-   Utilizzare lo strumento nome sicuro (Sn.exe) che viene fornito dal [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] SDK. Per altre informazioni, vedere [Sn.exe (Strong Name Tool)](/dotnet/framework/tools/sn-exe-strong-name-tool).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Escludere un avviso da questa regola solo se l'assembly viene utilizzata in un ambiente in cui manomettere il contenuto non è un problema.

## <a name="see-also"></a>Vedere anche
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> [Procedura: firmare un Assembly con un nome sicuro](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name) [Sn.exe (strumento nome sicuro)](/dotnet/framework/tools/sn-exe-strong-name-tool)