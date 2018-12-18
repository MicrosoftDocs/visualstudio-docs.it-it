---
title: Comando Flag elemento | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- CommandFlag element (VSCT XML schema)
- VSCT XML schema elements, CommandFlag
ms.assetid: 5ef63399-d2db-4dc1-97ce-be1bd4ef4e39
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 036b9658957b76b62e3a9b44b59e07700f276a32
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="command-flag-element"></a>Elemento di Flag di comando
Modifica l'elemento padre.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<CommandFlag>DynamicVisibility</CommandFlag>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nella sezione seguente vengono descritti i valori di elemento valido.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|AllowParams|Indica che gli utenti possono immettere i parametri del comando nel **comando** finestra quando si digita il nome canonico del comando.<br /><br /> Valida per: `Button`|  
|AlwaysCreate|Anche se non include gruppi o i pulsanti, menu viene creato.<br /><br /> Valida per: `Menu`|  
|CaseSensitive|Le voci utente tra maiuscole e minuscole.<br /><br /> Valida per: `Combo`|  
|CommandWellOnly|Applica questo flag se il comando non viene visualizzato il menu di primo livello e si desidera renderlo disponibile per la personalizzazione di altre shell, ad esempio, per l'associazione a un tasto di scelta rapida. Dopo aver installato il pacchetto VSPackage, è possibile personalizzare questi comandi, aprire il **opzioni** la finestra di dialogo e quindi modifica la posizione di comando sotto il **ambiente tastiera** categoria. Questo flag non influisce sul posizionamento nel menu di scelta rapida, barre degli strumenti, i controller di menu o i sottomenu.<br /><br /> Valida per: `Button`, `Combo`|  
|DefaultDisabled|Per impostazione predefinita, il comando è disabilitato se non è stato caricato il pacchetto VSPackage che lo implementa o `QueryStatus` (metodo) non è stato chiamato.<br /><br /> Valida per: `Button`, `Combo`|  
|DefaultDocked|Per impostazione predefinita, ancorato. Questa impostazione non si applica alle barre degli strumenti perché sono sempre ancorati.|  
|DefaultInvisible|Per impostazione predefinita, il comando è invisibile se non è stato caricato il pacchetto VSPackage che lo implementa o `QueryStatus` (metodo) non è stato chiamato.<br /><br /> È consigliabile che si combinarla con il `DynamicVisibility` flag.<br /><br /> Valida per: `Button`, `Combo`, `Menu`|  
|DontCache|L'ambiente di sviluppo memorizza nella cache il `QueryStatus` risultati del metodo per questo comando.<br /><br /> Per un menu, ciò indica un controller di menu non memorizzare nella cache il testo di voci di menu. Questo flag viene utilizzato quando il menu contiene elementi dinamici o elementi contenenti testo dinamico.<br /><br /> Valida per: `Button`, `Menu`|  
|DynamicItemStart|Indica l'inizio di un elenco dinamico. In questo modo l'ambiente compilare un elenco chiamando successivamente il `QueryStatus` metodo sugli elementi dell'elenco fino a quando non viene restituito il flag OLECMDERR_E_UNSUPPORTED. Ciò vale per gli elementi, ad esempio utilizzati più di recente (MRU) elenchi e gli elenchi di finestra.<br /><br /> Valida per: `Button`|  
|DynamicVisibility|La visibilità del comando può essere modificata tramite il `QueryStatus` (metodo) o tramite un GUID che è incluso nel contesto di `VisibilityConstraints` sezione.<br /><br /> Si applica ai comandi che vengono visualizzati nei menu e barre degli strumenti finestra dello strumento, ma non su barre degli strumenti di primo livello che vengono visualizzati nella finestra principale. Gli elementi di livello superiore della barra degli strumenti possono essere disabilitati, ma non nascosti quando il flag OLECMDF_INVISIBLE viene restituito dal `QueryStatus` metodo. I comandi della barra degli strumenti visualizzati sulle barre degli strumenti finestra dello strumento possono essere nascosta.<br /><br /> In un menu, questo flag indica inoltre che si deve essere automaticamente nascosta quando tutti i relativi membri sono nascosti. Questo flag viene in genere assegnato a sottomenu poiché menu di primo livello è già installato questo comportamento.<br /><br /> Questo flag deve essere combinato con il `DefaultInvisible` flag.<br /><br /> Valida per: `Button`, `Combo`, `Menu`|  
|Filtro tasti|Vedere l'argomento di filtro delle chiavi in [elemento combinata](../extensibility/combo-element.md).<br /><br /> Valida per: `Combo`|  
|FixMenuController|Se questo comando è posizionato su un controller di menu, il comando è sempre il valore predefinito; vale a dire, il comando è selezionato quando si seleziona il pulsante di menu controller stesso. Se il controller di menu ha il `TextIsAnchorCommand` impostare il flag, quindi il controller di menu accetta inoltre il testo del comando che ha il `FixMenuController` flag.<br /><br /> Deve avere un solo comando in un controller di menu di `FixMenuController` flag. Se è contrassegnato in modo più di un comando, l'ultimo comando nel menu diventa il comando predefinito.<br /><br /> Valida per: `Button`|  
|IconAndText|Visualizza un'icona e testo nel menu e barra degli strumenti.<br /><br /> Valida per: `Button`, `Combo`, `Menu`|  
|NoAutoComplete|Funzionalità di completamento automatico è disabilitato.<br /><br /> Valida per: `Combo`|  
|NoButtonCustomize|Non consentire all'utente di personalizzare questo pulsante.<br /><br /> Valida per: `Button`, `Combo`|  
|NoKeyCustomize|Non abilitare la personalizzazione della tastiera.<br /><br /> Valida per: `Button`, `Combo`|  
|NoShowOnMenuController|Se questo comando è posizionato su un controller di menu, il comando non viene visualizzato nell'elenco a discesa.<br /><br /> Valida per: `Button`|  
|NotInTBList|Non viene visualizzato nell'elenco delle barre degli strumenti disponibili. Questo è valido solo per i tipi di menu della barra degli strumenti.<br /><br /> Valida per: `Menu`|  
|NoToolbarClose|L'utente non è possibile chiudere la barra degli strumenti. Questo è valido solo per i tipi di menu della barra degli strumenti.<br /><br /> Valida per: `Menu`|  
|PICT|Mostra solo un'icona in una barra degli strumenti, ma solo il testo in un menu. Se viene specificata alcuna icona, viene illustrato uno spazio vuoto selezionabile in una barra degli strumenti.<br /><br /> Valida per: `Button`|  
|PostExec|Esegue il comando non bloccante. L'ambiente di sviluppo rinvia l'esecuzione fino al completamento di tutte le query di pre-elaborazione.<br /><br /> Valida per: `Button`|  
|RouteToDocs|Il comando viene indirizzato al documento attivo.<br /><br /> Valida per: `Button`|  
|StretchHorizontally|Se questo flag è impostato, la larghezza diventa la larghezza minima per la casella combinata, e se c'è spazio sulla barra degli strumenti, la casella combinata occupa tutto lo spazio disponibile. Questo errore si verifica solo se la barra degli strumenti è ancorato in orizzontale, e solo una casella combinata nella barra degli strumenti è possibile utilizzare il flag (il flag viene ignorato in tutti ad eccezione della prima casella combinata).<br /><br /> Valida per: `Combo`|  
|TextMenuUseButton|Utilizzare il `ButtonText` campo per i menu. Il campo predefinito è `MenuText` se è specificato.<br /><br /> Valida per: `Button`|  
|TestoConsente di modificare|Il testo di comando o menu può essere modificato in fase di esecuzione, in genere tramite il `QueryStatus` metodo.<br /><br /> Valida per: `Button`, `Menu`|  
|TextChangesButton|Valida per: `Button`|  
|TextIsAnchorCommand|Per un controller di menu, viene acquisito il testo del menu di scelta dal comando predefinito (ancoraggio). Un comando di ancoraggio è l'ultimo comando selezionato o impostare un latch. Se questo flag non è impostato, il controller di menu, utilizza il proprio `MenuText` campo. Tuttavia, facendo clic su controller di menu consente ancora l'ultimo comando selezionato dal controller di.<br /><br /> È consigliabile combinare i questo flag con la `TextChanges` flag.<br /><br /> Questo flag si applica solo ai menu di tipo MenuController o MenuControllerLatched.<br /><br /> Valida per: `Menu`|  
|TextMenuCtrlUseMenu|Utilizzare il `MenuText` campo nei controller di menu. Il campo predefinito è `ButtonText`.<br /><br /> Valida per: `Button`|  
|TextMenuUseButton|Utilizzare il `ButtonText` campo per i menu. Il campo predefinito è `MenuText` se è specificato.<br /><br /> Valida per: `Button`|  
|TextOnly|Mostra solo il testo in una barra degli strumenti o un menu ma nessuna icona anche se viene specificato l'icona.<br /><br /> Valida per: `Button`|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Buttons](../extensibility/buttons-element.md)|Fornisce un gruppo per [elemento Button](../extensibility/button-element.md) elementi.|  
|[Elemento Menus](../extensibility/menus-element.md)|Definisce tutti i menu che implementa un pacchetto VSPackage.|  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)