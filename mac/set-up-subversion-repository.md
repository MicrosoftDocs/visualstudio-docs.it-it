---
title: Impostazione di un repository Subversion in Visual Studio per Mac
description: Uso di Git e Subversion in Visual Studio per Mac.
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: 0D58FB37-530E-495B-BED6-FD499477A9B6
ms.openlocfilehash: e6b6fd600d3f32c77651b9a4fbb0dff2cd754bcb
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/20/2018
---
# <a name="setting-up-a-subversion-repository"></a>Impostazione di un repository Subversion

Subversion è un sistema di controllo della versione centralizzato. Ciò significa che vi è un unico server che contiene tutti i file e le revisioni da cui gli utenti possono estrarre qualsiasi versione di qualsiasi file. Quando i file vengono estratti da un repository Subversion remoto, l'utente riceve uno snapshot del repository in tale momento.

Prima di iniziare a utilizzare Subversion, è necessario installare gli strumenti da riga di comando Xcode poiché contengono i pacchetti SVN corretti. È possibile controllare che SVN si installato in Terminal mediante il comando seguente:

`svn h`

1. Creare un repository SVN gratuito online. In questo esempio è stato usato [Assembla](https://app.assembla.com/). Dopo la creazione, verrà reso disponibile un URL che consentirà di connettersi al repository: 

    ![Ottenere l'URL SVN e copiarlo](media/version-control-subversion1-sml.png)

2. Aprire o creare un progetto Visual Studio per Mac.

3. Fare clic con il pulsante destro del mouse sul progetto e selezionare **Controllo della versione > Pubblica in controllo della versione...**: 

    ![Avviare la pubblicazione del progetto](media/version-control-subversion2.png)

4. Nella scheda **Connetti al repository** selezionare **Subversion** dall'elenco a discesa in alto.

5. Inserire l'URL del passaggio 1. Gli altri campi verranno popolati per impostazione predefinita: 

    ![Finestra di dialogo di selezione del repository e di immissione dei dettagli](media/version-control-subversion3.png)

7. Fare clic su **OK** e quindi confermare premendo **Pubblica**.

7. Potrebbe venire richiesto di inserire le proprie credenziali per il sito in cui si crea il repository. Inserirle come illustrato di seguito:

    ![](media/version-control-subversion5.png)

8.  Tutti i comandi di controllo della versione disponibili verranno visualizzati nel menu del controllo della versione.

