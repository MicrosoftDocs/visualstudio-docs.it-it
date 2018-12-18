---
title: Nodi delle trame | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7df5ef3-dd4f-4964-9d96-34e0e180515e
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 97962debc24b9e8bff3d4daaa7b632db775c2476
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="texture-nodes"></a>Nodi di trama
Nella finestra di progettazione shader i nodi delle trame effettuano il campionamento di più geometrie e tipi di trama e producono o trasformano le coordinate di trama. Le trame forniscono dettagli di colore e illuminazione sugli oggetti.  
  
## <a name="texture-node-reference"></a>Riferimento per i nodi delle trame  
  
|Nodo|Dettagli|Proprietà|  
|----------|-------------|----------------|  
|**Campione mappa cubi**|Prende un campione di colore da una mappa cubi alle coordinate specificate.<br /><br /> È possibile usare una mappa cubi per fornire dettagli di colore per gli effetti di riflesso o per applicare a un oggetto sferico una trama con meno distorsione rispetto a una trama 2D.<br /><br /> **Input:**<br /><br /> `UVW`: `float3`<br /> Vettore che specifica la posizione nel cubo di trama in cui viene preso il campione. Il campione viene preso nel punto in cui il vettore interseca il cubo.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Esempio di colore.|**Trama**<br /> Registro di trama associato al campionatore.|  
|**Campione mappa normali**|Prende un campione di normale da una mappa di normali 2D alle coordinate specificate.<br /><br /> È possibile usare una mappa di normali per simulare l'aspetto di dettagli geometrici aggiuntivi sulla superficie di un oggetto. Le mappe di normali contengono dati compressi che rappresentano un vettore unitario anziché dati di colore.<br /><br /> **Input:**<br /><br /> `UV`: `float2`<br /> Coordinate in cui viene eseguito il campionamento.<br /><br /> **Output:**<br /><br /> `Output`: `float3`<br /> Campione di normale.|**Adeguamento assi**<br /> Fattore usato per regolare la mano utilizzata per scrivere del campione di mappa normale.<br /><br /> **Trama**<br /> Registro di trama associato al campionatore.|  
|**Panoramica**|Effettua una panoramica delle coordinate di trama specificate come funzione di tempo.<br /><br /> È possibile usare questo valore per spostare una mappa di trame o di normali sulla superficie di un oggetto.<br /><br /> **Input:**<br /><br /> `UV`: `float2`<br /> Coordinate di cui eseguire la panoramica.<br /><br /> `Time`: `float`<br /> Durata della panoramica, in secondi.<br /><br /> **Output:**<br /><br /> `Output`: `float2`<br /> Coordinate visualizzate in panoramica.|**Velocità X**<br /> Numero di texel visualizzati in panoramica lungo l'asse x, al secondo.<br /><br /> **Velocità Y**<br /> Numero di texel visualizzati in panoramica lungo l'asse y, al secondo.|  
|**Parallasse UV**|Sposta le coordinate di trama specificate come funzione dell'altezza e dell'angolo di visualizzazione.<br /><br /> L'effetto creato è noto come *mapping del parallasse* o mapping di spostamento virtuale. È possibile usare questo valore per creare un'illusione di profondità su una superficie piana.<br /><br /> **Input:**<br /><br /> `UV`: `float2`<br /> Coordinate da spostare.<br /><br /> `Height`: `float`<br /> Valore di heightmap associato alle coordinate `UV`.<br /><br /> **Output:**<br /><br /> `Output`: `float2`<br /> Coordinate spostate.|**Piano profondità**<br /> Profondità di riferimento per l'effetto di parallasse. Per impostazione predefinita, il valore è 0,5. I valori minori sollevano la trama, mentre quelli maggiori la sprofondano nella superficie.<br /><br /> **Scala profondità**<br /> Scala dell'effetto di parallasse per rendere più o meno pronunciata la profondità apparente. I valori tipici sono compresi tra 0,02 e 0,1.|  
|**Rotazione UV**|Ruota le coordinate di trama specificate intorno a un punto centrale come funzione di tempo.<br /><br /> È possibile usare questo valore per ruotare una mappa di trame o di normali sulla superficie di un oggetto.<br /><br /> **Input:**<br /><br /> `UV`: `float2`<br /> Coordinate di ruotare.<br /><br /> `Time`: `float`<br /> Durata della panoramica, in secondi.<br /><br /> **Output:**<br /><br /> `Output`: `float2`<br /> Coordinate ruotate.|**Centra X**<br /> Coordinata x che definisce il centro della rotazione.<br /><br /> **Centra Y**<br /> Coordinata y che definisce il centro della rotazione.<br /><br /> **Velocità**<br /> Angolo, in radianti, in base a cui viene ruotata la trama al secondo.|  
|**Coordinata trama**|Le coordinate di trama del pixel corrente.<br /><br /> Le coordinate di trama sono determinate dall'interpolazione tra gli attributi delle coordinate di trama dei vertici vicini. È possibile considerare questo valore come la posizione del pixel corrente nello spazio di trama.<br /><br /> **Output:**<br /><br /> `Output`: `float2`<br /> Coordinate di trama.|nessuno|  
|**Dimensioni di trama**|Restituisce la larghezza e l'altezza di una mappa di trama 2D.<br /><br /> È possibile usare le dimensioni della trama per prendere in considerazione la larghezza e l'altezza della trama in uno shader.<br /><br /> **Output:**<br /><br /> `Output`: `float2`<br /> Larghezza e altezza della trama, espresse come vettore. La larghezza viene memorizzata nel primo elemento del vettore. L'altezza viene memorizzata nel secondo elemento.|**Trama**<br /> Registro di trama associato alle dimensioni della trama.|  
|**Differenza texel**|Restituisce la differenza (distanza) tra i texel di una mappa di trama 2D.<br /><br /> È possibile usare questo valore per eseguire un campionamento in base ai pixel adiacenti in una trama.<br /><br /> **Output:**<br /><br /> `Output`: `float2`<br /> La differenza (distanza) tra un texel e il texel successivo (spostandosi in diagonale nella direzione positiva), espresso come un vettore nello spazio di trama normalizzato. È possibile derivare le posizioni di tutti i texel adiacenti in modo selettivo ignorando o negando le coordinate V o U della differenza.|**Trama**<br /> Registro di trama associato alla differenza di texel.|  
|**Campione trama**|Prende un campione di colore da una mappa di trama 2D alle coordinate specificate.<br /><br /> È possibile usare una mappa di trama per fornire dettagli di colore sulla superficie di un oggetto.<br /><br /> **Input:**<br /><br /> `UV`: `float2`<br /> Coordinate in cui viene eseguito il campionamento.<br /><br /> **Output:**<br /><br /> `Output`: `float4`<br /> Esempio di colore.|**Trama**<br /> Registro di trama associato al campionatore.|