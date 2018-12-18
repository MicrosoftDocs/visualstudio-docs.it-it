---
title: Informazioni sul parametro in un Service2 Language Legacy | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6aaf8ba9be9e16eeb979b0d64d3e80e8d70b564f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informazioni sul parametro in un servizio di linguaggio Legacy
Informazioni sul parametro IntelliSense è una descrizione comando che consente di visualizzare la firma di un metodo quando l'utente digita l'elenco dei parametri start carattere (in genere una parentesi di apertura) per l'elenco di parametri di metodo. Quando viene immesso ogni parametro e il separatore di parametro (in genere una virgola) è tipizzato, la descrizione comando viene aggiornata per mostrare il parametro successivo in grassetto.  
  
 Le classi di pacchetto gestito (MPF) framework forniscono supporto per la gestione di informazioni sul parametro descrizione comando. Il parser deve rilevare parametro start parametro accanto, e caratteri di fine di parametro e deve fornire un elenco di firme del metodo e i relativi parametri.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori dettagli, vedere [estensione dell'Editor e i servizi di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a usare il nuovo editor di API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## <a name="implementation"></a>Implementazione  
 Il parser deve impostare il valore trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers> è impostato quando viene trovato un carattere iniziale dell'elenco parametri (spesso una parentesi di apertura). Deve essere impostato un <xref:Microsoft.VisualStudio.Package.TokenTriggers> trigger quando rileva un separatore di parametri (spesso una virgola). In questo modo una descrizione comando informazioni sul parametro devono essere aggiornati e visualizzare il parametro successivo in grassetto. Il parser deve impostare il valore trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers> quando se rileva che il carattere di fine elenco parametro (spesso una parentesi di chiusura).  
  
 Il <xref:Microsoft.VisualStudio.Package.TokenTriggers> valore trigger avvia una chiamata al <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> metodo, che a sua volta chiama il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> parser di metodo con un motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason>. Se il parser determina che l'identificatore l'elenco dei parametri prima di carattere è un nome di metodo riconosciuto, viene restituito un elenco di firme dei metodi in corrispondenza di <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto. Se sono state trovate le firme del metodo, la descrizione comando informazioni sul parametro viene visualizzata con la firma del primo nell'elenco. Questa descrizione comandi viene quindi aggiornata di più della firma. Quando si digita il carattere di fine di elenco di parametri, la descrizione di informazioni sul parametro di comando viene rimosso dalla visualizzazione.  
  
> [!NOTE]
>  Per garantire che la descrizione comando informazioni parametri sia nel formato corretto, è necessario eseguire l'override di proprietà sul <xref:Microsoft.VisualStudio.Package.Methods> classe per fornire i caratteri appropriati. La base <xref:Microsoft.VisualStudio.Package.Methods> presuppone di classe c#-firma del metodo di stile. Vedere la <xref:Microsoft.VisualStudio.Package.Methods> classe per informazioni dettagliate su come questa operazione può essere eseguita.  
  
## <a name="enabling-support-for-the-parameter-info"></a>Abilitazione del supporto per le informazioni di parametro  
 Per supportare le descrizioni comandi informazioni sul parametro, è necessario impostare il `ShowCompletion` parametro di denominato il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> per `true`. Il servizio di linguaggio legge il valore di questa voce del Registro di sistema dal <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> proprietà.  
  
 Inoltre, il <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> proprietà deve essere impostata su `true` per visualizzare la descrizione comando informazioni sul parametro.  
  
### <a name="example"></a>Esempio  
 Di seguito è riportato un esempio semplificato di rilevare i caratteri di elenco di parametri e l'impostazione di attiva appropriato. Questo esempio è solo a scopo illustrativo. Si presuppone che lo scanner contiene un metodo `GetNextToken` che identifica e restituisce un token da una riga di testo. Nell'esempio di codice imposta semplicemente il trigger quando viene rilevato il tipo di carattere corretto.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char parameterListStartChar = '(';  
        private const char parameterListEndChar   = ')';  
        private const char parameterNextChar      = ',';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (Char.IsPunctuation(c))  
                {  
                    tokenInfo.Type = TokenType.Operator;  
                    tokenInfo.Color = TokenColor.Keyword;  
                    tokenInfo.EndIndex = index;  
  
                    if (c == parameterListStartChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;  
                    }  
                    else if (c == parameterListNextChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;  
                    else if (c == parameterListEndChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;  
                    }  
                }  
            return foundToken;  
        }  
    }  
}  
```  
  
## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>La descrizione comando informazioni sul parametro di supporto nel Parser  
 Il <xref:Microsoft.VisualStudio.Package.Source> classe fa alcune supposizioni sul contenuto del <xref:Microsoft.VisualStudio.Package.AuthoringScope> e <xref:Microsoft.VisualStudio.Package.AuthoringSink> classi se la descrizione comando informazioni sul parametro viene visualizzata e aggiornata.  
  
-   Il parser ha <xref:Microsoft.VisualStudio.Package.ParseReason> quando viene digitato il carattere iniziale dell'elenco parametri.  
  
-   Il percorso specificato <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto viene immediatamente dopo che l'elenco di parametri di carattere iniziale. Il parser deve raccogliere le firme di tutte le dichiarazioni di metodo in cui posizionare e archiviano in un elenco nella versione di <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto. Questo elenco include il nome del metodo, tipo metodo (o tipo restituito) e un elenco di possibili parametri. Questo elenco viene eseguita la ricerca in un secondo momento per la firma del metodo o le firme per visualizzare la descrizione comando informazioni sul parametro.  
  
 Il parser deve analizzare la riga specificata dal <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto per raccogliere il nome del metodo l'immissione e la distanza lungo l'utente è digitare i parametri. Questa operazione viene eseguita passando il nome del metodo per il <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> metodo sul <xref:Microsoft.VisualStudio.Package.AuthoringSink> e quindi chiamando il <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> viene analizzato il metodo quando l'elenco di parametri di carattere iniziale, la chiamata di <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> (metodo) quando l'elenco di parametri carattere successivo viene analizzato e infine la chiamata di <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> quando viene analizzato il carattere di fine elenco di parametri di metodo. I risultati di queste chiamate al metodo vengono usati per la <xref:Microsoft.VisualStudio.Package.Source> classe per aggiornare la descrizione comando informazioni sul parametro in modo appropriato.  
  
### <a name="example"></a>Esempio  
 Di seguito è riportata una riga di testo, che l'utente potrebbe immettere. I numeri sotto la linea indicano quale operazione viene effettuata dal parser in tale posizione nella riga (presupponendo che l'analisi dei spostamento a sinistra a destra). Il presupposto è che tutto ciò che precede la riga è già stato analizzato per le firme, tra cui la firma del metodo "testfunc".  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 Di seguito sono descritti i passaggi che il parser accetta:  
  
1.  Le chiamate di parser <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> con il testo "testfunc".  
  
2.  Le chiamate di parser <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>.  
  
3.  Le chiamate di parser <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>.  
  
4.  Le chiamate di parser <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>.