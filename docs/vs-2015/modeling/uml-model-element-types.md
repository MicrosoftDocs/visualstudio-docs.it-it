---
title: Tipi di elemento del modello UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, types
ms.assetid: 25345a53-7246-4eb7-8ad9-0b695aa171a2
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 54036b985c90be926eaa56f6ebe60d1f3903e0b2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657317"
---
# <a name="uml-model-element-types"></a>Tipi di elemento del modello UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile leggere e modificare un modello UML tramite un'interfaccia di programmazione. Questo argomento riepiloga la gerarchia dei tipi di elemento. La gerarchia è uguale a quella definita nella specifica UML.

 I dettagli di ogni tipo sono forniti in [riferimento API per l'estendibilità di modellazione UML](../modeling/api-reference-for-uml-modeling-extensibility.md).

## <a name="element-types"></a>Tipi di elemento
 Questo è il set dei tipi definiti nell'assembly `Microsoft.VisualStudio.Uml.Interfaces.dll`.

 Il nome completo di ogni elemento è "`Microsoft.VisualStudio.Uml.`" seguito dal nome elencato.

 Per comodità, questo elenco viene definito come gerarchia di ereditarietà. Se a un tipo sono associati più supertipi, i supertipi aggiuntivi vengono elencati dopo i due punti (:).

```

Classes.IElement
|  Activities.IActivityGroup
|  Classes.IComment
|  Classes.IMultiplicityElement
|  |  CompositeStructures.IConnectorEnd
|  Classes.INamedElement
|  |  Deployments.IDeployedArtifact
|  |  Deployments.IDeploymentTarget
|  |  |  Classes.IInstanceSpecification
             : Deployments.IDeployedArtifact,
               Deployments.IDeploymentTarget
|  |  |  |  Classes.IEnumerationLiteral
|  |  Interactions.IInteractionFragment
|  |  |  Interactions.ICombinedFragment
|  |  |  |  Interactions.IConsiderIgnoreFragment
|  |  |  Interactions.IExecutionSpecification
|  |  |  |  Interactions.IActionExecutionSpecification
|  |  |  |  Interactions.IBehaviorExecutionSpecification
|  |  |  Interactions.IInteraction  : CommonBehaviors.IBehavior
|  |  |  Interactions.IInteractionOperand : Classes.INamespace
|  |  |  Interactions.IInteractionUse
|  |  |  Interactions.IOccurrenceSpecification
|  |  |  |  Interactions.IExecutionOccurrenceSpecification
|  |  |  |  Interactions.IMessageOccurrenceSpecification
                   : Interactions.IMessageEnd
|  |  |  |  |  Interactions.ILostFoundTarget
|  |  |  |  Interactions.IOperandOccurrenceSpecification
|  |  |  Interactions.IStateInvariant
|  |  Interactions.ILifeline
|  |  Interactions.IMessage
|  |  Interactions.IMessageEnd
|  |  Classes.INamespace
|  |  |  Classes.IPackage
             : Classes.IPackageableElement,
              AuxiliaryConstructs.ITemplateableElement
|  |  |  |  AuxiliaryConstructs.IModel
|  |  |  Activities.IState
|  |  Classes.IPackageableElement
                   : AuxiliaryConstructs.IParameterableElement
|  |  |  Classes.IConstraint
|  |  |  |  Interactions.IInteractionConstraint
|  |  |  CommonBehaviors.IEvent
|  |  |  |  Interactions.IExecutionEvent
|  |  |  |  CommonBehaviors.IMessageEvent
|  |  |  |  |  CommonBehaviors.ICallEvent
|  |  |  |  |  Interactions.IReceiveOperationEvent
|  |  |  |  |  Interactions.IReceiveSignalEvent
|  |  |  |  |  Interactions.ISendOperationEvent
|  |  |  |  |  Interactions.ISendSignalEvent
|  |  |  Classes.IType
|  |  |  |  Classes.IClassifier : Classes.INamespace, Classes.IRedefinableElement, AuxiliaryConstructs.ITemplateableElement
|  |  |  |  |  Deployments.IArtifact
                   : Deployments.IDeployedArtifact
|  |  |  |  |  |  Deployments.IDeploymentSpecification
|  |  |  |  |  CommonBehaviors.IBehavioredClassifier
|  |  |  |  |  |  UseCases.IActor
|  |  |  |  |  |  Classes.IClass
                         : CompositeStructures.IEncapsulatedClassifier
|  |  |  |  |  |  |  CommonBehaviors.IBehavior
|  |  |  |  |  |  |  |  Activities.IActivity
|  |  |  |  |  |  |  Components.IComponent
|  |  |  |  |  |  |  |  UseCases.ISubsystem
|  |  |  |  |  |  |  Deployments.INode : IDeploymentTarget
|  |  |  |  |  |  |  |  Deployments.IDevice
|  |  |  |  |  |  |  |  Deployments.IExecutionEnvironment
|  |  |  |  |  |  UseCases.IUseCase
|  |  |  |  |  Classes.IDataType
|  |  |  |  |  |  Classes.IEnumeration
|  |  |  |  |  |  Classes.IPrimitiveType
|  |  |  |  |  Classes.IInterface
|  |  |  |  |  CompositeStructures.IStructuredClassifier
|  |  |  |  |  |  CompositeStructures.IEncapsulatedClassifier
|  |  |  Classes.IValueSpecification : Classes.ITypedElement
|  |  |  |  Classes.IExpression
|  |  |  |  Classes.IInstanceValue
|  |  |  |  Classes.ILiteralSpecification
|  |  |  |  |  Classes.ILiteralBoolean
|  |  |  |  |  Classes.ILiteralInteger
|  |  |  |  |  Classes.ILiteralNull
|  |  |  |  |  Classes.ILiteralString
|  |  |  |  |  Classes.ILiteralUnlimitedNatural
|  |  |  |  Classes.IOpaqueExpression
|  |  Classes.IRedefinableElement
|  |  |  Activities.IActivityNode
|  |  |  |  Activities.IControlNode
|  |  |  |  |  Activities.IDecisionNode
|  |  |  |  |  Activities.IFinalNode
|  |  |  |  |  |  Activities.IActivityFinalNode
|  |  |  |  |  Activities.IForkNode
|  |  |  |  |  Activities.IInitialNode
|  |  |  |  |  Activities.IJoinNode
|  |  |  |  |  Activities.IMergeNode
|  |  |  |  Activities.IExecutableNode
|  |  |  |  |  Actions.IAction
|  |  |  |  |  |  Actions.IAcceptEventAction
|  |  |  |  |  |  Actions.ICreateObjectAction
|  |  |  |  |  |  Actions.IInvocationAction
|  |  |  |  |  |  |  Actions.ICallAction
|  |  |  |  |  |  |  |  Actions.ICallBehaviorAction
|  |  |  |  |  |  |  |  Actions.ICallOperationAction
|  |  |  |  |  |  |  Actions.ISendSignalAction
|  |  |  |  |  |  Actions.IOpaqueAction
|  |  |  |  Activities.IObjectNode  : Classes.ITypedElement
|  |  |  |  |  Activities.IActivityParameterNode
|  |  |  |  |  Actions.IPin : Classes.IMultiplicityElement
|  |  |  |  |  |  Actions.IInputPin
|  |  |  |  |  |  Actions.IOutputPin
|  |  |  UseCases.IExtensionPoint
|  |  |  Classes.IFeature
|  |  |  |  Classes.IBehavioralFeature  : Classes.INamespace
|  |  |  |  |  Classes.IOperation
                   : AuxiliaryConstructs.ITemplateableElement,
                   AuxiliaryConstructs.IParameterableElement
|  |  |  |  Classes.IStructuralFeature
              : Classes.IMultiplicityElement,
                Classes.ITypedElement
|  |  |  |  |  Classes.IProperty
                   : AuxiliaryConstructs.ITemplateableElement,
                   CompositeStructures.IConnectableElement,
                   Deployments.IDeploymentTarget
|  |  |  |  |  |  CompositeStructures.IPort
|  |  Classes.ITypedElement
|  |  |  CompositeStructures.IConnectableElement
             : AuxiliaryConstructs.IParameterableElement
|  |  |  Classes.IParameter  : Classes.IMultiplicityElement, CompositeStructures.IConnectableElement
|  AuxiliaryConstructs.IParameterableElement
|  Classes.IProfileInstance

|  Classes.IRelationship
|  |  Activities.IActivityEdge : Classes.IRedefinableElement
|  |  |  Activities.IControlFlow
|  |  |  Activities.IObjectFlow
|  |  Classes.IAssociation : IClassifier
|  |  |  Deployments.ICommunicationPath
|  |  CompositeStructures.IConnector
|  |  Classes.IDirectedRelationship
|  |  |  Classes.IDependency : Classes.IPackageableElement
|  |  |  |  Classes.IAbstraction
|  |  |  |  |  Deployments.IManifestation
|  |  |  |  |  Classes.IRealization
|  |  |  |  |  |  Classes.IInterfaceRealization
|  |  |  |  Deployments.IDeployment
|  |  |  |  Classes.IUsage
|  |  |  UseCases.IExtend : Classes.INamedElement
|  |  |  Classes.IGeneralization
|  |  |  UseCases.IInclude : Classes.INamedElement
|  |  |  Classes.IPackageImport
|  |  |  AuxiliaryConstructs.ITemplateBinding
|  Classes.IStereotypeInstance
|  Classes.IStereotypePropertyInstance
|  AuxiliaryConstructs.ITemplateableElement
|  AuxiliaryConstructs.ITemplateParameter
|  |  AuxiliaryConstructs.IClassifierTemplateParameter
|  |  AuxiliaryConstructs.IOperationTemplateParameter
|  AuxiliaryConstructs.ITemplateParameterSubstitution
|  AuxiliaryConstructs.ITemplateSignature
|  |  AuxiliaryConstructs.IRedefinableTemplateSignature
             : Classes.IRedefinableElement
```

## <a name="see-also"></a>Vedere anche
 [Definire un profilo per estendere UML](../modeling/define-a-profile-to-extend-uml.md) [definire vincoli di convalida per i modelli UML](../modeling/define-validation-constraints-for-uml-models.md) [riferimento API per l'ESTENDIbilità di modellazione UML](../modeling/api-reference-for-uml-modeling-extensibility.md)
