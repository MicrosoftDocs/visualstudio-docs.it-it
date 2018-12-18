---
title: Accessibilità
description: ''
author: asb3993
ms.author: amburns
ms.date: 08/15/2017
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.openlocfilehash: b434a1cf0290c1c43d0f309850e112843907d6da
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="accessibility"></a>Accessibilità

Oltre alle funzionalità e alle utilità in macOS, Visual Studio per Mac include le funzionalità seguenti che rendono il programma più accessibile per gli utenti con disabilità:

- Ingrandimento del testo nei riquadri della soluzione e dell'editor
- Opzioni per la dimensione del testo negli editor
- Personalizzazione dei colori negli editor
- Personalizzazione dei tasti di scelta rapida
- Completamento del codice per metodi e parametri 

Per altre informazioni sulle funzionalità di accessibilità in macOS, vedere il [sito Web di Apple](https://www.apple.com/accessibility/mac/).

## <a name="using-accessibility-features-in-visual-studio-for-mac"></a>Utilizzo di funzionalità di accessibilità in Visual Studio per Mac

Le funzionalità di accessibilità di Visual Studio per Mac sono disattivate per impostazione predefinita. Per abilitarle, seguire questa procedura:

1. Passare a **Visual Studio > Preferenze > Altro > Accessibilità**.

2. Selezionare la casella di controllo **Enable Accessibility** (Abilita accessibilità), come illustrato nella figura seguente:

    ![Casella di controllo Enable Accessibility (Abilita accessibilità)](media/accessibility-image1.png)

3. Fare clic sul pulsante **Restart Visual Studio** (Riavvia Visual Studio) per rendere effettive le funzionalità di accessibilità.


In alternativa, è possibile usare la riga di comando per abilitare le funzionalità di accessibilità. A tale scopo, immettere il comando seguente nel terminale: 

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1 
```

Dopo aver attivato l'accessibilità, è necessario riavviare Visual Studio.

## <a name="how-to-use-keyboard-navigation"></a>Procedura: Usare la navigazione tramite tastiera

La navigazione tramite tastiera può essere abilitata impostando l'opzione di accesso completo tramite tastiera in **Preferenze di Sistema > Tastiera > Abbreviazioni** su **Tutti i controlli**:

  ![Pannello Preferenze di Sistema in macOS](media/accessibility-image2.png)

L'impostazione dell'accesso completo tramite tastiera attiva il rettangolo di evidenziazione. È quindi possibile selezionare i controlli usando:
- Tabulatore per spostarsi in avanti tra i controlli
- Maiuscole-Tabulatore per spostarsi indietro tra i controlli
- Tasti freccia per spostarsi tra i controlli nella direzione delle frecce. 

Premendo Barra spaziatrice viene attivato il controllo evidenziato.

## <a name="how-to-enable-and-use-voice-over"></a>Procedura: Abilitare e usare la funzionalità VoiceOver

Per attivare o disattivare VoiceOver premere **Comando-F5**

Per spostarsi tra i comandi di VoiceOver dell'interfaccia utente, usare i comandi seguenti:

- Spostare il cursore di VoiceOver tra i controlli: **CTRL+ALT+freccia SINISTRA/freccia DESTRA**

VoiceOver pronuncia il nome dei controlli, alcuni dettagli e le operazioni che possono essere eseguite con il controllo evidenziato. 

- Entrare in gruppi e controlli (come il riquadro della soluzione, la casella degli strumenti e altri riquadri): **CTRL+ALT+MAIUSC+freccia GIÙ**

Una volta all'interno di un controllo, è possibile usare **CTRL+ALT+frecce** per spostarsi all'interno. 
 
Per informazioni generali sull'uso di Voice over in macOS, fare riferimento alle guide seguenti:

- [Guida Utente di VoiceOver](https://help.apple.com/voiceover/info/guide/10.12/)
- [VoiceOver commands in macOS](http://lab.dotjay.com/notes/voiceover-commands/) (Comandi di VoiceOver in macOS)
