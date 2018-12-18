---
title: Il compilatore di colore VSIX | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 115f3a6c9d01d1e92a5eb7c840dfb17abcfd3c72
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="vsix-color-compiler"></a>Compilatore colori VSIX
Lo strumento compilatore di Visual Studio estensione colore è un'applicazione console che accetta un file XML che rappresenta i colori per i temi di Visual Studio esistenti e vengono convertiti in un. pkgdef file in modo che è possono utilizzare i colori in Visual Studio. Poiché è facile confrontare le differenze tra i file con estensione XML, questo strumento è utile per la gestione di colori personalizzati nel controllo del codice sorgente. Anche possibile eseguire l'hook negli ambienti di compilazione in modo che l'output della compilazione è un file. pkgdef valido.  
  
 **Schema XML tema**  
  
 Un file con estensione XML tema completo è simile al seguente:  
  
```xml  
<Themes>  
      <!—one or Theme elements -->  
      <Theme>  
        <!-- one or more Category elements -->  
        <Category>  
          <!-- one or more Color elements -->  
          <Color>  
            <!-- zero or one Background element -->  
            <Background />  
            <!-- zero or one Foreground element -->  
            <Foreground />  
          </Color>  
        </Category>  
      </Theme>  
</Themes>  
```  
  
 **Tema**  
  
 Il \<tema > elemento definisce un tema completo. Un tema deve contenere almeno un \<categoria > elemento. Elementi sono definiti come segue:  
  
```xml  
<Theme Name="name" GUID="guid">  
      <!-- one or more Category elements -->  
</Theme>  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|nome|[Obbligatorio] Il nome del tema|  
|GUID|[Obbligatorio] GUID del tema (deve corrispondere la formattazione di GUID)|  
  
 Quando si creano i colori personalizzati per Visual Studio, i colori devono essere definiti per i seguenti temi. Se è presente alcun colore per un particolare tema, Visual Studio tenta di caricare i colori mancanti dal tema chiaro.  
  
|||  
|-|-|  
|**Nome del tema**|**Tema GUID**|  
|Chiaro|{de3dbbcd-f642-433c-8353-8f1df4370aba}|  
|Scuro|{1ded0138-47ce-435e-84ef-9ec1f439b749}|  
|Blu|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
|Contrasto elevato|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|  
  
 **Categoria**  
  
 Il \<categoria > elemento definisce una raccolta di colori in un tema. I nomi di categoria forniscono raggruppamenti logici e devono essere definiti come ristretto possibile. Una categoria deve contenere almeno un \<colore > elemento. Elementi di categoria vengono definiti come segue:  
  
```xml  
<Category Name="name" GUID="guid">  
      <!-- one or more Color elements -->  
 </Category>  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|nome|[Obbligatorio] Il nome della categoria|  
|GUID|[Obbligatorio] GUID della categoria (deve corrispondere la formattazione di GUID)|  
  
 **Colore**  
  
 Il \<colore > elemento definisce un colore per un componente o lo stato dell'interfaccia utente. Lo schema di denominazione preferito per un colore è [tipo di interfaccia utente] [stato]. Non utilizzare la parola "color", come è ridondante. Il tipo di elemento e le situazioni o "stato", per cui verrà applicato il colore, deve indicare chiaramente un colore. Un colore non deve essere vuoto e deve contenere uno o entrambi un \<Background > e \<in primo piano > elemento. Gli elementi di colore sono definiti come segue:  
  
```xml  
<Color Name="name">  
        <Background /> <!-- zero or one Background element -->  
        <Foreground /> <!-- zero or one Foreground element -->  
 </Color>  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|nome|[Obbligatorio] Il nome del colore|  
  
 **Sfondo e/o in primo piano**  
  
 Il \<Background > e \<in primo piano > elementi che definiscono il valore e tipo per il primo piano di un elemento dell'interfaccia utente o di sfondo di un colore. Questi elementi non includono elementi figlio.  
  
```xml  
<Background Type="type" Source="int" />  
<Foreground Type="type" Source="int" />  
```  
  
|||  
|-|-|  
|**Attributo**|**Definizione**|  
|Tipo|[Obbligatorio] Il tipo del colore. Può essere uno dei valori seguenti:<br /><br /> *CT_INVALID:* il colore non è valido o non è impostato.<br /><br /> *CT_RAW:* un valore ARGB non elaborato.<br /><br /> *CT_COLORINDEX:* NON USARE.<br /><br /> *CT_SYSCOLOR:* un colore di sistema di Windows da SysColor.<br /><br /> *CT_VSCOLOR:* un colore variate __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* il colore automatico.<br /><br /> *CT_TRACK_FOREGROUND:* NON USARE.<br /><br /> *CT_TRACK_BACKGROUND:* NON USARE.|  
|Origine|[Obbligatorio] Il valore del colore rappresentato in formato esadecimale|  
  
 Tutti i valori supportati dall'enumerazione __VSCOLORTYPE supportati dallo schema dell'attributo di tipo. Tuttavia, è consigliabile utilizzare solo CT_RAW e CT_SYSCOLOR.  
  
 **Tutti insieme**  
  
 Questo è un esempio semplice di un file di tema valido con estensione XML:  
  
```xml  
<Themes>  
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">  
    <Category Name="MyCategory" GUID="{0A96238B-70CE-4479-9170-EECEAA3FCD58}">  
      <Color Name="MyActiveBorder">  
        <Background Type="CT_RAW" Source="FFCCCEDB" />  
      </Color>  
    </Category>  
  </Theme>  
</Themes>  
```  
  
## <a name="how-to-use-the-tool"></a>Come utilizzare lo strumento  
 **Sintassi**  
  
 VsixColorCompiler \<file XML > \<file PkgDef > \<Args facoltativo >  
  
 **Argomenti**  
  
||||  
|-|-|-|  
|**Nome del commutatore**|**Note**|**Obbligatorio o facoltativo**|  
|Senza nome (file con estensione XML)|Questo è il primo parametro senza nome e percorso del file XML da convertire.|Obbligatorio|  
|Senza nome (file. pkgdef)|Questo è il secondo parametro senza nome ed è il percorso di output per il file. pkgdef generato.<br /><br /> Impostazione predefinita: \<XML Filename >. pkgdef|Facoltativo|  
|/noLogo|Impostare questo flag arresta prodotto e il copyright di stampare le informazioni.|Facoltativo|  
|/?|Stampare le informazioni della Guida.|Facoltativo|  
|/help|Stampare le informazioni della Guida.|Facoltativo|  
  
 **Esempi**  
  
-   VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef  
  
-   /NoLogo VsixColorCompiler D:\xml\colors.xml  
  
## <a name="notes"></a>Note  
  
-   Questo strumento richiede che la versione più recente del runtime VC + + è installato.  
  
-   Sono supportati solo i singoli file. Non è supportata la conversione in blocco tramite i percorsi delle cartelle.  
  
## <a name="sample-output"></a>Esempio di output  
 Il file. pkgdef generato dallo strumento sarà simile di sotto le chiavi:  
  
```  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]  
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff  
  
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]  
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff  
```