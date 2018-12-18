---
title: Interfaccia IManagedAddin | Documenti Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d626257d3a2683a6fbb6032e8053572fd1301645
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="imanagedaddin-interface"></a>IManagedAddin (interfaccia)
  Implementare l'interfaccia IManagedAddin per creare un componente che carichi gestiti componenti aggiuntivi VSTO. Questa interfaccia è stata aggiunta in Microsoft Office System 2007.  
  
## <a name="syntax"></a>Sintassi  
  
```  
[  
    object,  
    uuid(B9CEAB65-331C-4713-8410-DDDAF8EC191A),  
    pointer_default(unique),  
    oleautomation  
]  
interface IManagedAddin : IUnknown  
{  
    HRESULT Load(  
        [in] BSTR bstrManifestURL,   
        [in] IDispatch *pdispApplication);  
    HRESULT Unload();  
};  
```  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono elencati i metodi definiti dall'interfaccia IManagedAddin.  
  
|nome|Descrizione|  
|----------|-----------------|  
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Chiamato quando un'applicazione di Microsoft Office carica un componente aggiuntivo VSTO gestito.|  
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Chiamato appena prima che un'applicazione di Microsoft Office scarichi un componente aggiuntivo VSTO gestito.|  
  
## <a name="remarks"></a>Note  
 Applicazioni di Microsoft Office, a partire da Microsoft Office system 2007, utilizzano l'interfaccia IManagedAddin per consentire il caricamento di componenti aggiuntivi VSTO di Office. È possibile implementare l'interfaccia IManagedAddin per creare il propria caricatore del componente aggiuntivo VSTO e gestito di runtime per componenti aggiuntivi VSTO, anziché usare il caricatore del componente aggiuntivo VSTO (VSTOLoader.dll) e [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Per altre informazioni, vedere [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
## <a name="how-managed-add-ins-are-loaded"></a>Modalità di caricamento dei componenti aggiuntivi gestiti  
 All'avvio di un'applicazione vengono effettuate le operazioni seguenti:  
  
1.  L'applicazione individua i componenti aggiuntivi VSTO cercando le voci nella chiave seguente del Registro di sistema:  
  
     HKEY_CURRENT_USER\Software\Microsoft\Office\\*\<nome applicazione >*\Addins\  
  
     Ogni voce sotto questa chiave del Registro di sistema è un ID univoco del componente aggiuntivo VSTO. In genere, corrisponde al nome dell'assembly del componente aggiuntivo VSTO.  
  
2.  L'applicazione cerca una voce `Manifest` nella voce per ciascun componente aggiuntivo VSTO.  
  
     Gestito i componenti aggiuntivi VSTO è possono archiviare il percorso completo di un manifesto nella `Manifest` voce sotto HKEY_CURRENT_USER\Software\Microsoft\Office\\*\<nome applicazione >*\Addins\\  *\<ID componente aggiuntivo >*. Un manifesto è un file (in genere, un file XML) che fornisce informazioni usate per consentire il caricamento del componente aggiuntivo VSTO.  
  
3.  Se l'applicazione individua una voce `Manifest` , prova a caricare un componente caricatore per componenti aggiuntivi VSTO gestiti. Questo scopo, l'applicazione tenta di creare un oggetto COM che implementa l'interfaccia IManagedAddin.  
  
     Il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] include un componente aggiuntivo VSTO componente caricatore (VSTOLoader.dll), oppure è possibile creare uno personalizzato implementando l'interfaccia IManagedAddin.  
  
4.  L'applicazione chiama il metodo [IManagedAddin::Load](../vsto/imanagedaddin-load.md) e passa il valore della voce `Manifest` .  
  
5.  Il metodo [IManagedAddin::Load](../vsto/imanagedaddin-load.md) esegue le attività necessarie per caricare il componente aggiuntivo VSTO, ad esempio la configurazione del dominio dell'applicazione e dei criteri di sicurezza per il componente aggiuntivo VSTO caricato.  
  
 Per ulteriori informazioni sul Registro di sistema le chiavi usate dalle applicazioni di Microsoft Office per individuare e caricare gestite componenti aggiuntivi VSTO, vedere [le voci del Registro di sistema per componenti aggiuntivi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
## <a name="guidance-for-implementing-imanagedaddin"></a>Indicazioni per l'implementazione di IManagedAddin  
 Se si implementa IManagedAddin, è necessario registrare la DLL che contiene l'implementazione tramite il CLSID seguente:  
  
 99D651D7-5F7C-470E-8A3B-774D5D9536AC  
  
 Applicazioni di Microsoft Office utilizzano questo CLSID per creare l'oggetto COM che implementa IManagedAddin.  
  
> [!CAUTION]  
>  Questo CLSID è inoltre usato da VSTOLoader.dll in [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Pertanto, se si utilizza IManagedAddin per creare la propria caricatore del componente aggiuntivo VSTO e il componente runtime, è possibile distribuire il componente ai computer che eseguono i componenti aggiuntivi VSTO che si basano sul [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti alle API non gestite &#40;sviluppo per Office in Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)  
  
  