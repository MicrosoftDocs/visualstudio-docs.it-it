---
title: 'Procedura: accedere ai tipi di carattere incorporati e una combinazione di colori | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5f72640369152b03ef86383fda1162b1cfbacba8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>Procedura: accedere ai tipi di carattere incorporati e una combinazione di colori
Ambiente di sviluppo integrato (IDE) di Visual Studio è una combinazione di tipi di carattere e colori associata a una finestra dell'editor. È possibile accedere a questo schema tramite il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia.

 Per utilizzare lo schema di colori e i tipi di carattere incorporati, un pacchetto VSPackage deve:

-   Definire una categoria da usare con il servizio predefinito di tipi di carattere e colori.

-   Registrare la categoria con il server predefinito di tipi di carattere e colori.

-   Indicare all'IDE che una finestra specifica Usa le categorie e gli elementi di visualizzazione predefinite mediante il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer> interfacce.

 L'IDE Usa la categoria risulta come handle di finestra. Nome della categoria viene visualizzato nella **Mostra impostazioni per:** casella di riepilogo a discesa il **tipi di carattere e colori** pagina delle proprietà.

### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>Per definire una categoria utilizzando i colori e tipi di carattere incorporati

1.  Creare un GUID non autorizzato.

     Questo GUID è utilizzato per identificare in modo univoco una categoria**.** Questa categoria riutilizza specifica di colori e tipi di carattere predefiniti dell'IDE.

    > [!NOTE]
    >  Durante il recupero di dati carattere e colori con il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> o altre interfacce, VSPackage utilizzano questo GUID per fare riferimento a informazioni predefinite.

2.  Nome della categoria deve essere aggiunto a una tabella di stringhe all'interno di file di risorse (RC) del pacchetto VSPackage, in modo che possa essere localizzata in base alle esigenze quando visualizzati nell'IDE di.

     Per ulteriori informazioni, vedere [aggiunta o eliminazione di una stringa](/cpp/windows/adding-or-deleting-a-string).

### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>Per registrare una categoria utilizzando i colori e tipi di carattere incorporati

1.  Creare un tipo speciale di voce del Registro di sistema di categoria nel percorso seguente:

     [HKLM\Software\Microsoft. \Visual Studio\\*\<versione di Visual Studio >*\FontAndColors\\*\<categoria >*]

     *\<Categoria >* è il nome non localizzato della categoria.

2.  Popolare il Registro di sistema per l'utilizzo di tipi di carattere azionari e combinazione di colori con quattro valori:

    |nome|Tipo|Dati|Descrizione|
    |----------|----------|----------|-----------------|
    |Category|REG_SZ|GUID|Un GUID arbitrario che identifica una categoria che contiene lo schema di carattere e colori predefinito.|
    |Pacchetto|REG_SZ|GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> Questo GUID è usato da tutti i pacchetti VSPackage che utilizzano le configurazioni predefinite di carattere e colori.|
    |Elemento NameID|REG_DWORD|Id|L'ID di risorsa di un nome di categoria localizzabile nel pacchetto VSPackage.|
    |ToolWindowPackage|REG_SZ|GUID|Il GUID del pacchetto VSPackage che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interfaccia.|

### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>Per avviare l'utilizzo di fornita dal sistema di tipi di carattere e colori

1.  Creare un'istanza di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> interfaccia come parte dell'implementazione e l'inizializzazione della finestra.

2.  Chiamare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> per ottenere un'istanza di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer> interfaccia corrispondente all'oggetto corrente <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> istanza.

3.  Chiamare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> due volte.

    -   Chiamare una volta con `VSEDITPROPID_ViewGeneral_ColorCategory`come argomento.

    -   Chiamare una volta con `VSEDITPROPID_ViewGeneral_FontCategory` come argomento.

     Questo imposta ed espone i servizi di tipi di carattere e colori predefiniti come proprietà della finestra.

## <a name="example"></a>Esempio
 Nell'esempio seguente avvia l'utilizzo di colori e tipi di carattere incorporati.

```cpp
CComVariant vt;
CComQIPtr<IVsTextEditorPropertyCategoryContainer> spPropCatContainer(m_spView);
if (spPropCatContainer != NULL){
    CComPtr<IVsTextEditorPropertyContainer> spPropContainer;
    if (SUCCEEDED(spPropCatContainer->GetPropertyCategory(GUID_EditPropCategory_View_MasterSettings,
                                                          &spPropContainer))){
        CComVariant vt;CComVariant VariantGUID(bstrGuidText);
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_FontCategory, VariantGUID);
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_ColorCategory, VariantGUID);
    }
}
```

## <a name="see-also"></a>Vedere anche

- [Utilizzo di tipi di carattere e colori](../extensibility/using-fonts-and-colors.md)
- [Recupero di tipo di carattere e colore per testo colorazione](../extensibility/getting-font-and-color-information-for-text-colorization.md)
- [L'accesso a carattere archiviato e le impostazioni dei colori](../extensibility/accessing-stored-font-and-color-settings.md)
- [Panoramica di colore e tipo di carattere](../extensibility/font-and-color-overview.md)