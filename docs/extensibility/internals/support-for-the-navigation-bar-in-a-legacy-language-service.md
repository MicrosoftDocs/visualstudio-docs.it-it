---
title: Supporto per la barra di spostamento in un servizio di linguaggio Legacy | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5d4dd17f3bb1bd50a97b24b42cf40edc27bf51db
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Supporto per la barra di spostamento in un servizio di linguaggio Legacy
La barra di navigazione nella parte superiore della visualizzazione dell'editor vengono visualizzati i tipi e membri nel file. Discesa a sinistra vengono visualizzati i tipi e membri vengono visualizzati nella finestra di destra elenco a discesa. Quando l'utente seleziona un tipo, il cursore viene posizionato nella prima riga del tipo. Quando l'utente seleziona un membro, il cursore viene posizionato sulla definizione del membro. Le caselle di riepilogo a discesa vengono aggiornate per riflettere il percorso corrente del punto di inserimento.  
  
## <a name="displaying-and-updating-the-navigation-bar"></a>Visualizzazione e aggiornamento di barra di spostamento  
 Per supportare la barra di spostamento, è necessario derivare una classe dalla classe di <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> classe e implementare il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodo. Quando il servizio di linguaggio ha una finestra del codice, la base <xref:Microsoft.VisualStudio.Package.LanguageService> un'istanza di <xref:Microsoft.VisualStudio.Package.CodeWindowManager>, che contiene il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> oggetto che rappresenta la finestra del codice. Il <xref:Microsoft.VisualStudio.Package.CodeWindowManager> oggetto viene quindi assegnato un nuovo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> oggetto. Il <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> metodo ottiene un <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> oggetto. Se viene restituita un'istanza del <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> (classe), il <xref:Microsoft.VisualStudio.Package.CodeWindowManager> chiamate il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodo per popolare l'oggetto interno vengono elencate e passa il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> dell'oggetto per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elenco a discesa della barra di gestione. Elenco a discesa barra manager, a sua volta chiama il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> metodo i <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> oggetto per stabilire il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> oggetto che contiene le due barre di riepilogo a discesa.  
  
 Quando si sposta il punto di inserimento, la <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> chiamate al metodo di <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> metodo. La base <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> chiamate al metodo di <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodo il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> classe per aggiornare lo stato della barra di spostamento. Si passa un set di <xref:Microsoft.VisualStudio.Package.DropDownMember> gli oggetti a questo metodo. Ogni oggetto rappresenta una voce nell'elenco a discesa.  
  
## <a name="the-contents-of-the-navigation-bar"></a>Il contenuto della barra di spostamento  
 Barra di spostamento contiene in genere un elenco di tipi e un elenco di membri. L'elenco dei tipi include tutti i tipi disponibili nel file di origine corrente. I nomi dei tipi includono le informazioni dello spazio dei nomi completo. Di seguito è riportato un esempio di codice c# con due tipi:  
  
```csharp  
namespace TestLanguagePackage  
{  
    public class TestLanguageService  
    {  
        internal struct Token  
        {  
            int tokenID;  
        }  
        private Tokens[] tokens;  
        private string serviceName;  
    }  
}  
```  
  
 Verrà visualizzato l'elenco di tipo `TestLanguagePackage.TestLanguageService` e `TestLanguagePackage.TestLanguageService.Tokens`.  
  
 L'elenco di membri Visualizza i membri del tipo che sia selezionato nell'elenco dei tipi disponibili. Utilizzando l'esempio di codice precedente, se `TestLanguagePackage.TestLanguageService` è il tipo che è selezionato, l'elenco dei membri contiene membri privati `tokens` e `serviceName`. La struttura interna `Token` non viene visualizzata.  
  
 È possibile implementare l'elenco di membri per specificare un nome di un membro in grassetto quando il cursore viene posizionato all'interno. Membri possono essere visualizzati anche nella grigio testo, che indica che non siano all'interno dell'ambito in cui il punto di inserimento è attualmente posizionato.  
  
## <a name="enabling-support-for-the-navigation-bar"></a>Abilitazione del supporto per la barra di spostamento  
 Per abilitare il supporto per la barra di spostamento, è necessario impostare il `ShowDropdownBarOption` parametro il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attributo `true`. Questo parametro imposta la proprietà <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>. Per supportare la barra di spostamento, è necessario implementare la <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> oggetto il <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> metodo la <xref:Microsoft.VisualStudio.Package.LanguageService> classe.  
  
 Nell'implementazione del <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> metodo, se il <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> è impostata su `true`, è possibile restituire un <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> oggetto. Se non viene restituito l'oggetto, la barra di spostamento non viene visualizzata.  
  
 Pertanto è possibile per il controllo da reimpostare mentre la visualizzazione dell'editor è aperta, è possibile impostare l'opzione per visualizzare la barra di spostamento dall'utente. L'utente deve chiudere e riaprire la finestra dell'editor prima che la modifica.  
  
## <a name="implementing-support-for-the-navigation-bar"></a>Implementazione del supporto per la barra di spostamento  
 Il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodo accetta due elenchi (uno per ogni elenco a discesa) e due valori che rappresenta la selezione corrente in ogni elenco. Gli elenchi e i valori di selezione possono essere aggiornati, nel qual caso il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodo deve restituire `true` per indicare che gli elenchi sono stati modificati.  
  
 Come cambia la selezione nei tipi di elenco a discesa, è necessario aggiornare l'elenco dei membri in modo da riflettere il nuovo tipo. Gli elementi visualizzati nell'elenco dei membri possono essere:  
  
-   L'elenco dei membri per il tipo corrente.  
  
-   Tutti i membri disponibili nell'origine dei file, ma con tutti i membri non di tipo corrente è visualizzato in testo grigio. L'utente può comunque selezionare i membri di inattivo, pertanto possono essere utilizzati per la navigazione rapida, ma il colore indica che non fanno parte del tipo selezionato.  
  
 Un'implementazione del <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodo in genere esegue i passaggi seguenti:  
  
1.  Ottenere un elenco di dichiarazioni correnti del file di origine.  
  
     Esistono diversi modi per popolare gli elenchi. Un approccio consiste nel creare un metodo personalizzato della versione di <xref:Microsoft.VisualStudio.Package.LanguageService> classe che chiama il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo con un motivo di analisi personalizzata che restituisce un elenco di tutte le dichiarazioni. Potrebbe essere un altro approccio per chiamare il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo direttamente il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> (metodo) con il motivo di analisi personalizzati. Un terzo approccio potrebbe essere per memorizzare nella cache le dichiarazioni nel <xref:Microsoft.VisualStudio.Package.AuthoringScope> restituito dall'ultima operazione di analisi completo nella classe di <xref:Microsoft.VisualStudio.Package.LanguageService> classe e recuperare dal <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> (metodo).  
  
2.  Inserire o aggiornare l'elenco dei tipi.  
  
     Il contenuto dell'elenco dei tipi sia in grado di essere aggiornato quando l'origine è stato modificato o se si è scelto di modificare lo stile del testo dei tipi in base alla posizione del punto di inserimento corrente. Si noti che questa posizione viene passata per il <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> metodo.  
  
3.  Determinare il tipo per selezionare nell'elenco dei tipi in base alla posizione del punto di inserimento corrente.  
  
     È possibile cercare le dichiarazioni che sono state ottenute nel passaggio 1 per trovare il tipo che include la posizione corrente del cursore e quindi cercare nell'elenco di tipi per il tipo determinare il relativo indice nell'elenco di tipi.  
  
4.  Inserire o aggiornare l'elenco di membri in base al tipo selezionato.  
  
     L'elenco dei membri riflette gli elementi visualizzati nel **membri** elenco a discesa. Potrebbe essere necessario aggiornare se l'origine è stato modificato o se si visualizzano solo i membri del tipo selezionato e il tipo selezionato è stato modificato il contenuto dell'elenco di membri. Se si sceglie di visualizzare tutti i membri nel file di origine, lo stile di testo di ogni membro nell'elenco deve essere aggiornato se il tipo selezionato è stato modificato.  
  
5.  Determinare il membro per selezionare nell'elenco dei membri in base alla posizione del punto di inserimento corrente.  
  
     Cercare le dichiarazioni che sono state ottenute nel passaggio 1 per il membro che contiene la posizione corrente del cursore, quindi eseguire ricerche nell'elenco di membri per il membro determinare il relativo indice nell'elenco dei membri.  
  
6.  Restituire `true` se sono state apportate modifiche per gli elenchi o selezioni in entrambi gli elenchi.