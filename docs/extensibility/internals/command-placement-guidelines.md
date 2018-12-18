---
title: Linee guida per la selezione di comando | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c406a5a34ea2556d367c8f7af8a9fda70fcc2676
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="command-placement-guidelines"></a>Linee guida per la selezione di comando
Procedure consigliate per il posizionamento comandi nell'ambiente di sviluppo integrato (IDE) di Visual Studio variano a seconda delle dimensioni del set di comandi. I comandi sono definiti e posizionati in base alle informazioni nei file con estensione vsct.  
  
## <a name="best-practices-for-all-command-sets"></a>Procedure consigliate per tutti i set di comandi  
 Per ogni set di comandi, attenersi alle seguenti indicazioni:  
  
-   Preparare in anticipo un grafico della struttura di comando. Identificare i comandi, caselle combinate, gruppi di comandi e menu di scelta rapida che verranno utilizzati in più posizioni.  
  
-   Comandi che vengono visualizzati nello stesso gruppo devono essere correlati.  
  
-   Sono consentiti gruppi che contengono un unico comando.  
  
-   Pacchetti consigliabile non aggiungere un numero elevato di comandi al menu di Visual Studio esistenti. Deve creare invece menu o sottomenu per ospitare nuovi comandi.  
  
-   Quando inserire un comando in un menu esistente, nome, il comando in modo che il suo scopo è crittografato e non essere confuso con i comandi esistenti.  
  
## <a name="best-practices-for-small-command-sets"></a>Procedure consigliate per i set di comandi di piccole dimensioni  
 Se si sviluppa un VSPackage che è disponibili solo pochi comandi, è necessario seguire anche queste linee guida:  
  
-   Quando possibile, utilizzare il [elemento padre](../../extensibility/parent-element.md) di un comando, casella combinata, gruppo o menu figlio per inserirlo nel gruppo appropriato.  
  
-   Assegnare questi gruppi di menu da visualizzare dal pacchetto VSPackage.  
  
-   L'elemento padre di un menu figlio o un comando deve essere un [elemento gruppo](../../extensibility/group-element.md). Assegnare gruppi di comandi e menu figlio e quindi assegnare i gruppi di menu padre.  
  
-   È possibile inserire un comando in altri gruppi aggiungendo un [CommandPlacements elemento](../../extensibility/commandplacements-element.md) sezione dopo la definizione del comando, quindi aggiungere il `CommandPlacements Element` un [elemento CommandPlacement](../../extensibility/commandplacement-element.md) per ogni gruppo aggiuntivo.  
  
## <a name="best-practices-for-large-command-sets"></a>Procedure consigliate per i set di comandi di grandi dimensioni  
 Se il pacchetto VSPackage avrà molti comandi che verranno visualizzato in più contesti, è necessario seguire anche queste linee guida:  
  
-   Assicurarsi di menu, gruppi e i comandi self-relazione padre-figlio. Ovvero, non si assegna un `Parent Element` nella definizione dell'elemento.  
  
-   Utilizzare `CommandPlacement Element` voci di `CommandPlacements Element` sezione per inserire i menu, gruppi e i comandi nel menu padre e i gruppi.  
  
-   Nel `CommandPlacements` sezione, le voci che popolano un determinato menu o il gruppo deve essere adiacente uno a altro. Ciò facilita la leggibilità e rende il `Priority` classificazioni di determinare più facilmente.  
  
## <a name="see-also"></a>Vedere anche  
 [Come VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [File Visual Studio Command Table (VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)