---
title: Debug - Visualizzazioni dati
description: Il debug è una parte comune e necessaria della programmazione. Visual Studio per Mac contiene un intero gruppo di funzionalità per semplificare il debug. Questo articolo presenta le diverse visualizzazioni dati che è possibile usare per esaminare gli oggetti nel debugger.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.technology: vs-ide-debug
ms.assetid: 527E6BEC-EF15-4002-ACB5-62AE1C16F6B7
ms.openlocfilehash: 1c228718dc528e0ab34c9af328aee1c8259fa8b5
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="data-visualizations"></a>Visualizzazioni dati

Visual Studio per Mac include il supporto dell'interfaccia utente per il debugger, consentendo visualizzazioni dei valori di una variabile, un campo o una proprietà durante il debug. Questi visualizzatori dei dati mostrano una versione estesa dei dati e permettono agli sviluppatori di esaminare strutture note, ad esempio visualizzando il colore di uno struct di colore.

I visualizzatori nel riquadro **Locale** per il debug possono essere avviati facendo clic sull'icona di anteprima visualizzata a destra del valore, quando si posiziona il puntatore del mouse sulla riga:

 ![Riquadro Locale](media/data-visualizations-image9.png)

L'elenco seguente presenta molte delle nuove visualizzazioni per il debug in Visual Studio per Mac.

## <a name="point"></a>Punto
Un oggetto Point/PointF o CGPoint in iOS e Mac viene visualizzato come tupla che mostra i valori X e Y nel riquadro del debug:

 ![Visualizzazione dei punti](media/data-visualizations-image10.png)

## <a name="size"></a>Dimensione
Un oggetto Size/SizeF CGSize in iOS e Mac viene visualizzato come rettangolo. L'oggetto viene disegnato in modo da ridimensionarsi fino a 250 px e da questo momento in poi il rettangolo viene ridimensionato in base al valore massimo di 250px:

![Visualizzazione delle dimensioni](media/data-visualizations-image11.png)


## <a name="rectangle"></a>Rettangolo
Un oggetto Rectangle/RectangleF o CGRect in iOS e Mac mostra le dimensioni e l'origine. Come per gli oggetti Size, l'oggetto viene disegnato in modo da ridimensionarsi, fino a 250 px:

 ![Visualizzazione dei rettangoli](media/data-visualizations-image12.png)

## <a name="coordinate"></a>Coordinate
Le coordinate vengono tracciate su una mappa, aggiungendo la posizione al centro:

![Visualizzazione delle coordinate](media/data-visualizations-image13.png)

## <a name="color"></a>Colore
Visualizza le proprietà UIColor, CGColor e Color, indicando l'anteprima del colore, i componenti RGBA, i valori di tonalità-luminosità-saturazione e il valore esadecimale del colore:

![Visualizzazione dei colori](media/data-visualizations-image14.png)


## <a name="images"></a>Immagini

Gli elementi multimediali vengono visualizzati in modo da ridimensionarsi fino a una dimensione massima di 250 px, quindi vengono ridimensionati in base allo spazio disponibile quando l'immagine supera 250 px:

 ![Visualizzazione delle immagini](media/data-visualizations-image15.png)


## <a name="bezier-curves"></a>Curve di Bézier

Il visualizzatore mostra un oggetto `NSBezierPath`:

![Visualizzazione delle curve di Bézier](media/data-visualizations-image16.png)


## <a name="string"></a>Stringa

Una stringa di meno di 100 caratteri viene visualizzata completamente, senza anteprima. Le stringhe più lunghe vengono visualizzate completamente nell'anteprima. Le stringhe sono modificabili e il visualizzatore include un pulsante di modifica, che permette la modifica del valore della stringa nell'anteprima o nell'editor dei valori delle stringhe, mostrato di seguito:

![Visualizzazione delle stringhe](media/data-visualizations-image17.png)

### <a name="small-strings"></a>Stringhe di piccole dimensioni:
![Visualizzazione di stringhe di piccole dimensioni](media/data-visualizations-image18.png)]

### <a name="medium-length-strings"></a>Stringhe di lunghezza media:
![Visualizzazione di stringhe di lunghezza media](media/data-visualizations-image19.png)

### <a name="editor"></a>Editor:

 ![Visualizzazione nell'editor](media/data-visualizations-image21.png)

## <a name="ienumerable"></a>IEnumerable

IEnumerable enumera tutti i valori. I valori di ogni oggetto possono essere visualizzati facendo clic sul pulsante **Mostra valori**. L'opzione IEnumerable non visualizza i valori di oggetti come `Array`, `ArrayList`, `List<>` o `Dictionary<,>`, perché questi hanno visualizzatori del debugger propri.

![Visualizzazione IEnumerable](media/data-visualizations-image22.png)

## <a name="other-visualizers"></a>Altri visualizzatori

Di seguito sono elencati altri tipi che hanno visualizzatori incorporati propri:

 ![Altre visualizzazioni](media/data-visualizations-image23.png)

*   **Primitives**
    *   Visualizza il valore non elaborato del tipo primitivo.
*   **Enum**
    *   Visualizza il valore del campo senza il qualificatore di tipo enum.
*   **Tuple**
    *   Usa il formato (,) per la visualizzazione.
*   **Null**
    *   Mostra i valori "null".
*   **URL**
    *   Mostra un collegamento ipertestuale su cui è possibile fare clic.
*   **IntPtr**
    *   Visualizza una rappresentazione esadecimale di un oggetto IntPtr.
