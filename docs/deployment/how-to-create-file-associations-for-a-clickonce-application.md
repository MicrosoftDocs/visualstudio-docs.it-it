---
title: "Procedura: creare associazioni di File per un'applicazione ClickOnce | Documenti Microsoft"
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf60327e622f8eb32757d29051e3dce94661722d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Procedura: creare associazioni di file per un'applicazione ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] le applicazioni possono essere associate uno o più estensioni di file, in modo che l'applicazione verrà avviato automaticamente quando l'utente apre un file di tali tipi. Aggiunta di supporto delle estensioni di file a un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione è semplice.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>Per creare associazioni di file per un'applicazione ClickOnce  
  
1.  Creare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione in genere, o utilizzarne un'esistente [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione.  
  
2.  Aprire il manifesto dell'applicazione con un editor di testo o XML, ad esempio Blocco note.  
  
3.  Trovare l'elemento `assembly`. Per altre informazioni, vedere [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md).  
  
4.  Come elemento figlio di `assembly` elemento, aggiungere un `fileAssociation` elemento. Il `fileAssociation` elemento dispone di quattro attributi:  
  
    -   `extension`: L'estensione che si desidera associare all'applicazione.  
  
    -   `description`: Descrizione del tipo di file, verrà visualizzata nella shell di Windows.  
  
    -   `progid`: Stringa che identifica in modo univoco il tipo di file, per contrassegnare nel Registro di sistema.  
  
    -   `defaultIcon`: Un'icona da utilizzare per questo tipo di file. L'icona deve essere aggiunto come una risorsa del file nel manifesto dell'applicazione. Per altre informazioni, vedere [Procedura: includere un file di dati in un'applicazione ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Per un esempio di `file` e `fileAssociation` elementi, vedere [ \<fileAssociation > elemento](../deployment/fileassociation-element-clickonce-application.md).  
  
5.  Se si desidera associare più di un tipo di file all'applicazione, aggiungere ulteriori `fileAssociation` elementi. Si noti che il `progid` attributo deve essere diverso per ognuno.  
  
6.  Dopo aver completato con il manifesto dell'applicazione, è necessario firmare nuovamente il manifesto. È possibile farlo dalla riga di comando utilizzando Mage.exe.  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     Per altre informazioni, vedere [Mage.exe (generazione manifesto e lo strumento di modifica)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)  
  
## <a name="see-also"></a>Vedere anche  
 [\<fileAssociation > elemento](../deployment/fileassociation-element-clickonce-application.md)   
 [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)