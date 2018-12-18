---
title: 'Procedura: utilizzare la finestra di progettazione XML Schema con valori letterali XML | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 504b063ccbc9646755891fc0eea3647a5594b213
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>Procedura: utilizzare Progettazione XML Schema con i valori letterali XML
In questo argomento viene descritto come visualizzare uno schema associato a un valore letterale XML in un progetto di Visual Basic.  
  
### <a name="to-create-a-new-visual-basic-console-application-project"></a>Per creare un nuovo progetto di applicazione console di Visual Basic  
  
1.  Avviare Visual Studio.  
  
2.  Dal **File** dal menu **New**, quindi selezionare **progetto**. Verrà visualizzata la finestra di dialogo **Nuovo progetto** . Per **tipi di progetto**selezionare **altri linguaggi,** e quindi selezionare **Visual Basic**. Per **modelli**, selezionare applicazione Console. Quindi digitare `XMLLiterals` nel **nome** campo e un percorso di progetto nel **percorso** campo. Fare clic su **OK**.  
  
     Il nuovo progetto è creato. Il progetto XMLLiterals contiene un file di origine di Visual Basic, Module1.vb.  
  
### <a name="to-add-an-existing-xsd-file-to-the-project"></a>Per aggiungere un file XSD esistente al progetto  
  
1.  Aprire un nuovo file di testo in Notepad.Copy il codice di esempio di XML Schema da [Schema ordine di acquisto](../xml-tools/sample-xsd-file-simple-schema.md) e incollarlo nel file.  
  
2.  Salvare il file in un percorso con il nome PurchaseOrderSchema.xsd.  
  
3.  In Esplora soluzioni, fare clic sul nome del progetto, selezionare **Aggiungi**, quindi selezionare **elemento esistente...** . Il **AddExisting elemento** viene visualizzata la finestra di dialogo. Individuare il file PurchaseOrderSchema.xsd, selezionarlo e quindi fare clic su **Aggiungi**.  
  
     Il progetto XMLLiterals contiene ora due file: Module1.vb e PurchaseOrderSchema.xsd.  
  
### <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>Per aggiungere codice Visual Basic con un valore letterale XML, in base al file XSD incluso nel progetto  
  
1.  Sostituire il codice nel file Module1.vb con il codice seguente:  
  
   ```vb
   Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">  
  
   Module Module1  
       Sub Main()  
  
           Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">  
                                <ns:ShipTo country="US">  
                                    <ns:name>name1</ns:name>  
                                    <ns:street>street1</ns:street>  
                                    <ns:city>city1</ns:city>  
                                    <ns:state>state1</ns:state>  
                                    <ns:zip>1</ns:zip>  
                                </ns:ShipTo>  
                                <ns:BillTo country="US">  
                                    <ns:name>name1</ns:name>  
                                    <ns:street>street1</ns:street>  
                                    <ns:city>city1</ns:city>  
                                    <ns:state>state1</ns:state>  
                                    <ns:zip>1</ns:zip>  
                                </ns:BillTo>  
                            </ns:PurchaseOrder>  
  
       End Sub  
   End Module  
   ```
  
2.  Fare doppio clic su qualsiasi nodo XML in un valore letterale XML o un'importazione dello spazio dei nomi XML e selezionare **Mostra in Schema Explorer**.  
  
     XML Schema Explorer viene visualizzato accanto a un file di Visual Basic che dispone di un valore letterale XML associato al set di schemi XML.