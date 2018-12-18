---
title: Associare controlli alle immagini da un database
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- images [Visual Basic], displaying on Windows Forms
- data binding [Windows Forms], pictures
- images [Visual Basic], data binding
- pictures, data binding
- pictures, dragging from Data Sources window
- Data Sources Window, setting controls to display images
- PictureBox control [Windows Forms], data binding
- images [Visual Basic], dragging from Data Sources window
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 722eb290e9018ef92608c8d554a371c94ba63caa
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Associare controlli alle immagini da un database

È possibile utilizzare il **origini dati** finestra per associare un'immagine in un database a un controllo nell'applicazione. Ad esempio, è possibile associare un'immagine da un <xref:System.Windows.Controls.Image> di controllo in un'applicazione WPF o a un <xref:System.Windows.Forms.PictureBox> controllo in un'applicazione Windows Form.

Le immagini in un database sono in genere archiviate come matrici di byte. Gli elementi nel **origini dati** finestra in cui vengono archiviati come matrici di byte avere il controllo tipo impostato su **Nessuno** per impostazione predefinita, poiché le matrici di byte possono contenere qualsiasi elemento da una semplice matrice di byte del file eseguibile un'applicazione di grandi dimensioni. Per creare un controllo con associazione a dati per un elemento della matrice di byte nel **origini dati** finestra che rappresenta un'immagine, è necessario selezionare il controllo da creare.

La procedura seguente si presuppone che il **origini dati** finestra è già popolata con un elemento che viene associato all'immagine.

## <a name="to-bind-a-picture-in-a-database-to-a-control"></a>Per associare un'immagine in un database a un controllo

1.  Assicurarsi che l'area di progettazione che si desidera aggiungere il controllo sia aperto in Progettazione Windows Form o in WPF Designer.

2.  Nel **origini dati** finestra, espandere la tabella desiderata o per visualizzare le colonne o proprietà dell'oggetto.

3.  Selezionare la colonna o proprietà che contiene i dati di immagine e selezionare uno dei seguenti controlli dall'elenco a discesa:

    -   Se la finestra di progettazione WPF è aperto, selezionare **immagine**.

    -   Se la finestra di progettazione Windows Form è aperto, selezionare **PictureBox**.

    -   In alternativa, è possibile selezionare un altro controllo che supporta il data binding e che consente di visualizzare immagini. Se il controllo che si desidera utilizzare non è presente nell'elenco dei controlli disponibili, è possibile aggiungerlo all'elenco e quindi selezionarlo. Per ulteriori informazioni, vedere [aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="see-also"></a>Vedere anche

- [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)