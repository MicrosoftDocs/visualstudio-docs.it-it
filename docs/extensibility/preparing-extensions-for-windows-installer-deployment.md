---
title: Preparazione delle estensioni per la distribuzione di Windows Installer | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ef51b3cb0f84a470f104ff688c1149e607d16f71
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136326"
---
# <a name="preparing-extensions-for-windows-installer-deployment"></a>Preparazione delle estensioni per la distribuzione di Windows Installer
È possibile utilizzare un pacchetto di Windows Installer (MSI) per distribuire un pacchetto VSIX. Tuttavia, è possibile estrarre il contenuto di un pacchetto VSIX per la distribuzione MSI. Questo documento viene illustrato come preparare un progetto di output il cui valore predefinito è un pacchetto VSIX per l'inclusione in un progetto di installazione.  
  
## <a name="preparing-an-extension-project-for-windows-installer-deployment"></a>Preparazione di un progetto di estensione per la distribuzione di Windows Installer  
 Prima di aggiungere un progetto di installazione, eseguire queste operazioni in nuovi progetti di estensione.  
  
#### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Per preparare un progetto di estensione per la distribuzione di Windows Installer  
  
1.  Creare un pacchetto VSPackage, componente MEF, dell'area di controllo di Editor o altri tipi di progetto di estendibilità che include un manifesto VSIX.  
  
2.  Aprire il manifesto VSIX nell'editor di codice.  
  
3.  Impostare l'elemento InstalledByMsi del manifesto VSIX per `true`. Per ulteriori informazioni sul manifesto VSIX, vedere [riferimento 2.0 allo Schema di estensione VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
     Ciò impedisce che il programma di installazione VSIX il tentativo di installare il componente.  
  
4.  Fare clic sul progetto in **Esplora** e fare clic su **proprietà**.  
  
5.  Selezionare il **VSIX** scheda.  
  
6.  Selezionare la casella **contenuto VSIX copia nel percorso seguente** e digitare il percorso in cui il progetto di installazione verrà prelevati i file.  
  
## <a name="extracting-files-from-an-existing-vsix-package"></a>L'estrazione dei file da un pacchetto VSIX esistente  
 Eseguire questi passaggi per aggiungere il contenuto di un pacchetto VSIX esistente a un progetto di installazione quando i file di origine non si dispone.  
  
#### <a name="to-extract-files-from-an-existing-vsix-package"></a>Per estrarre i file da un pacchetto VSIX esistente  
  
1.  Rinominare il. Il file VSIX che contiene l'estensione da *filename*VSIX per *filename*ZIP.  
  
2.  Copiare il contenuto del file con estensione zip in una directory.  
  
3.  Eliminare il file [Content_types] XML dalla directory.  
  
4.  Modificare il manifesto VSIX, come illustrato nella procedura precedente.  
  
5.  Aggiungere i file rimanenti al progetto di installazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Distribuzione di programma di installazione di Visual Studio](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)   
 [Procedura dettagliata: Creazione di un'azione personalizzata](http://msdn.microsoft.com/en-us/4bd4b63a-2b91-431e-839c-5752443f0eaf)