---
title: "Aggiunta di una proprietà di rilevamento alla definizione di un linguaggio specifico di dominio | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
helpviewer_keywords:
- tracking properties [Domain-Specific Language Tools], walkthrough
- Domain-Specific Language Tools, walkthroughs
- walkthroughs [Domain-Specific Language Tools]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: c0d6231882e8c7412248022abd2e8c578bbfad9f
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="adding-a-tracking-property-to-a-domain-specific-language-definition"></a>Aggiunta di una proprietà di rilevamento alla definizione di un linguaggio specifico di dominio
Questa procedura dettagliata viene illustrato come aggiungere una proprietà di rilevamento per un modello di dominio.  
  
 Oggetto *rilevamento dominio* è una proprietà che può essere aggiornato dall'utente, ma che contiene un valore predefinito che viene calcolato utilizzando i valori di altri elementi o proprietà del dominio.  
  
 Negli strumenti di linguaggio specifico di dominio (strumenti DSL), ad esempio, il nome visualizzato della proprietà di una classe di dominio ha un valore predefinito che viene calcolato utilizzando il nome della classe di dominio, ma un utente può modificare il valore in fase di progettazione o ripristinare il valore calcolato.  
  
 In questa procedura dettagliata, si crea un linguaggio specifico di dominio (DSL) che ha una proprietà che ha un valore predefinito in base alla proprietà Namespace predefinito del modello di rilevamento di Namespace. Per ulteriori informazioni sul rilevamento delle proprietà, vedere [la definizione di proprietà di rilevamento](http://msdn.microsoft.com/0538b0e4-6221-4e7d-911a-b92cd622f0be).  
  
-   Il supporto di strumenti DSL descrittori di proprietà di rilevamento. Tuttavia, è Impossibile utilizzare la finestra di progettazione DSL per aggiungere una proprietà di rilevamento per una lingua. Pertanto, è necessario aggiungere codice personalizzato per definire e implementare la proprietà di rilevamento.  
  
 Una proprietà di rilevamento dispone di due stati: rilevamento e aggiornato dall'utente. Le proprietà di rilevamento hanno le caratteristiche seguenti:  
  
-   Quando è in stato di rilevamento, viene calcolato il valore della proprietà di rilevamento e il valore viene aggiornato come altre proprietà, la modifica del modello.  
  
-   Quando si trova l'aggiornamento di stato utente, il valore della proprietà di rilevamento mantiene il valore a cui l'utente ultima impostazione della proprietà.  
  
-   Nel **proprietà** finestra il **reimpostare** comando per la proprietà di rilevamento è abilitata solo quando la proprietà è aggiornato per lo stato utente. Il **reimpostare** comando imposta la proprietà di rilevamento dello stato di rilevamento.  
  
-   Nel **proprietà** verrà visualizzata la finestra, quando la proprietà di rilevamento è nello stato di rilevamento, il relativo valore in un tipo di carattere normale.  
  
-   Nel **proprietà** finestra, quando la proprietà di rilevamento è aggiornato per lo stato utente, il relativo valore viene visualizzato in grassetto.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Prima di iniziare questa procedura dettagliata, è innanzitutto necessario installare questi componenti:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185579](http://go.microsoft.com/fwlink/?LinkID=185579)|  
|[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185580](http://go.microsoft.com/fwlink/?LinkID=185580)|  
|[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]|[http://go.microsoft.com/fwlink/?LinkID=185581](http://go.microsoft.com/fwlink/?LinkID=185581)|  
  
## <a name="creating-the-dsl-project"></a>Creazione del progetto DSL  
 Creare il progetto per il linguaggio specifico di dominio.  
  
#### <a name="to-create-the-project"></a>Per creare il progetto  
  
1.  Creare un progetto di progettazione di linguaggio specifico di dominio. Assegnargli il nome `TrackingPropertyDSL`.  
  
2.  Nel **Domain-Specific Language progettazione guidata**, impostare le opzioni seguenti:  
  
    1.  Selezionare il **MinimalLanguage** modello.  
  
    2.  Utilizzare il nome predefinito per il linguaggio specifico di dominio, `TrackingPropertyDSL`.  
  
    3.  Impostare l'estensione per i file del modello `trackingPropertyDsl`.  
  
    4.  Utilizzare l'icona di modello predefinito per i file del modello.  
  
    5.  Impostare il nome del prodotto da `Product Name`.  
  
    6.  Impostare il nome della società per `Company Name`.  
  
    7.  Utilizzare il valore predefinito per lo spazio dei nomi radice per i progetti nella soluzione, `CompanyName.ProductName.TrackingPropertyDSL`.  
  
    8.  Consentire alla procedura guidata creare un file di chiave con nome sicuro per gli assembly.  
  
    9. Esaminare i dettagli della soluzione e quindi fare clic su **fine** per creare il progetto di definizione DSL.  
  
## <a name="customizing-the-default-dsl-definition"></a>Personalizzazione della definizione DSL predefinito  
 In questa sezione si personalizzi la definizione DSL per contenere i seguenti elementi:  
  
-   Namespace proprietà per ogni elemento del modello di rilevamento.  
  
-   Proprietà booleana IsNamespaceTracking per ogni elemento del modello. Questa proprietà indica se la proprietà di rilevamento è lo stato di rilevamento o l'aggiornamento per lo stato utente.  
  
-   Proprietà Namespace predefinito per il modello. Questa proprietà verrà utilizzata per calcolare il valore predefinito di proprietà di rilevamento di Namespace.  
  
-   Proprietà CustomElements calcolato per il modello. Questa proprietà indica la proporzione tra gli elementi che hanno uno spazio dei nomi personalizzato.  
  
#### <a name="to-add-the-domain-properties"></a>Per aggiungere le proprietà del dominio  
  
1.  Nella finestra di progettazione DSL, fare doppio clic su di **ExampleModel** classe di dominio, scegliere **Aggiungi**, quindi fare clic su **DomainProperty**.  
  
    1.  Denominare la nuova proprietà `DefaultNamespace`.  
  
    2.  Nel **proprietà** finestra per la nuova proprietà, impostare **Default Value** a `DefaultNamespace`e impostare **tipo** a **stringa**.  
  
2.  Per il **ExampleModel** dominio classe, aggiungere una proprietà di dominio denominata `CustomElements`.  
  
     Nel **proprietà** finestra per la nuova proprietà, impostare **tipo** a **calcolato**.  
  
3.  Per il **ExampleElement** dominio classe, aggiungere una proprietà di dominio denominata `Namespace`.  
  
     Nel **proprietà** finestra per la nuova proprietà, impostare **è esplorabile** a **False**e impostare **tipo** a **CustomStorage** .  
  
4.  Per il **ExampleElement** dominio classe, aggiungere una proprietà di dominio denominata `IsNamespaceTracking`.  
  
     Nel **proprietà** finestra per la nuova proprietà, impostare **è esplorabile** a **False**, impostare **Default Value** a `true`e impostare **Tipo** a **booleano**.  
  
#### <a name="to-update-the-diagram-elements-and-dsl-details"></a>Per aggiornare gli elementi del diagramma e dettagli DSL  
  
1.  Nella finestra di progettazione DSL, fare doppio clic su di **ExampleShape** forma di geometria, scegliere **Aggiungi**e quindi fare clic su **Decorator testo**.  
  
    1.  Denominare il nuovo elemento decorator del testo `NamespaceDecorator`.  
  
    2.  Nel **proprietà** finestra per l'elemento decorator testo, impostare **posizione** a **InnerBottomLeft**.  
  
2.  Nella finestra di progettazione DSL, selezionare la linea che connette il **ExampleElement** classe per il **ExampleShape** forma.  
  
    1.  Nel **dettagli DSL** finestra, seleziona il **Decorator mappe** scheda.  
  
    2.  Nel **gli elementi Decorator** elenco, selezionare **NamespaceDecorator**, selezionare la casella di controllo e scegliere il **visualizzare proprietà** elenco, selezionare **Namespace**.  
  
3.  In **Esplora DSL**, espandere il **classi di dominio** cartella, fare doppio clic su di **ExampleElement** nodo e quindi fare clic su **aggiungere nuovo dominio descrittore di tipo**.  
  
    1.  Espandere il **ExampleElement** nodo e selezionare il **il descrittore di tipo personalizzato (descrittore del tipo di dominio)** nodo.  
  
    2.  Nel **proprietà** finestra per il descrittore di tipo di dominio, impostare **personalizzato codificati** a **True**.  
  
4.  In **Esplora DSL**, selezionare il **il comportamento di serializzazione Xml** nodo.  
  
    1.  Nel **proprietà** finestra impostare **carico Post personalizzato** a **True**.  
  
## <a name="transforming-templates"></a>Trasformare i modelli  
 Dopo avere definito le classi di dominio e proprietà per tale linguaggio DSL, è possibile verificare che la definizione DSL può essere trasformata in modo corretto per rigenerare il codice per il progetto.  
  
#### <a name="to-transform-the-text-templates"></a>Per trasformare i modelli di testo  
  
1.  Nel **Esplora** sulla barra degli strumenti, fare clic su **Trasforma tutti i modelli**.  
  
2.  Il sistema rigenera il codice per la soluzione e Salva DslDefinition.dsl. Per informazioni sul formato XML dei file di definizione, vedere [DslDefinition.dsl File](../modeling/the-dsldefinition-dsl-file.md).  
  
## <a name="creating-files-for-custom-code"></a>Creazione di file del codice personalizzato  
 Quando si trasforma tutti i modelli, il sistema genera il codice sorgente che definisce il linguaggio specifico di dominio nei progetti di Dsl e DslPackage. In modo che è possibile evitare di interferire con il testo generato, è possibile scrivere il codice personalizzato nei file che sono diversi dai file del codice generato.  
  
 È necessario fornire codice per mantenere il valore e lo stato della proprietà di rilevamento. Per distinguere il codice personalizzato dal codice generato e per evitare conflitti di denominazione dei file, inserire i file di codice personalizzato in una sottocartella separata.  
  
#### <a name="to-create-the-code-files"></a>Per creare i file di codice  
  
1.  In **Esplora**, fare doppio clic su di **DSL** , scegliere **Aggiungi**e quindi fare clic su **nuova cartella**. Denominare la nuova cartella `CustomCode`.  
  
2.  Fare doppio clic su nuovo **CustomCode** cartella, scegliere **Aggiungi**, quindi fare clic su **nuovo elemento**.  
  
3.  Selezionare il **File di codice** modello, impostare il **nome** per `NamespaceTrackingProperty.cs`, quindi fare clic su **OK**.  
  
     Il file NamespaceTrackingProperty.cs viene creato e aperto per la modifica.  
  
4.  Nella cartella, creare i file di codice seguente: `ExampleModel.cs,``HelperClasses.cs`, `Serialization.cs`, e `TypeDescriptor.cs`.  
  
5.  Nel **DslPackage** progetto, creare anche un `CustomCode` cartella e aggiungervi un `Package.cs` file di codice.  
  
## <a name="adding-helper-classes-to-support-tracking-properties"></a>Aggiunta di classi Helper per supportare le proprietà di rilevamento  
 Nel file HelperClasses.cs, aggiungere il `TrackingHelper` e `CriticalException` classi come indicato di seguito. Queste classi più avanti in questa procedura dettagliata verrà fatto riferimento.  
  
#### <a name="to-add-the-helper-classes"></a>Per aggiungere le classi di supporto  
  
1.  Aggiungere il codice seguente al file HelperClasses.cs.  
  
    ```csharp  
    using System;  
    using System.Collections;  
    using System.Diagnostics;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        internal static class TrackingHelper  
        {  
            /// <summary>Notify each model element in a collection that a tracked  
            /// property has changed.</summary>  
            /// <param name="store">The store for the model.</param>  
            /// <param name="collection">The collection of model elements that  
            /// contain the tracking property.</param>  
            /// <param name="propertyId">The ID of the tracking property.</param>  
            /// <param name="trackingPropertyId">The ID of the property that  
            /// indicates whether the tracking property is tracking.</param>  
            internal static void UpdateTrackingCollectionProperty(  
                Store store,  
                IEnumerable collection,  
                Guid propertyId,  
                Guid trackingPropertyId)  
            {  
                DomainPropertyInfo propInfo =  
                    store.DomainDataDirectory.GetDomainProperty(propertyId);  
  
                DomainPropertyInfo trackingPropInfo =  
                    store.DomainDataDirectory.GetDomainProperty(trackingPropertyId);  
  
                Debug.Assert(propInfo != null);  
                Debug.Assert(trackingPropInfo != null);  
                Debug.Assert(trackingPropInfo.PropertyType.Equals(typeof(bool)),  
                    "Tracking property not specified as a boolean");  
  
                foreach (ModelElement element in collection)  
                {  
                    // If the tracking property is currently tracking, then notify  
                    // it that the tracked property has changed.  
                    bool isTracking = (bool)trackingPropInfo.GetValue(element);  
                    if (isTracking)  
                    {  
                        propInfo.NotifyValueChange(element);  
                    }  
                }  
            }  
        }  
  
        /// <summary>Helper class to flag critical exceptions from ones that are  
        /// safe to ignore.</summary>  
        internal static class CriticalException  
        {  
            /// <summary>Gets whether an exception is critical and can not be  
            /// ignored.</summary>  
            /// <param name="ex">The exception to check.</param>  
            /// <returns>True if the exception is critical.</returns>  
            internal static bool IsCriticalException(Exception ex)  
            {  
                if (ex is NullReferenceException  
                    || ex is StackOverflowException  
                    || ex is OutOfMemoryException  
                    || ex is System.Threading.ThreadAbortException)  
                    return true;  
  
                if (ex.InnerException != null)  
                    return IsCriticalException(ex.InnerException);  
  
                return false;  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-custom-type-descriptor"></a>Aggiunta di codice personalizzato per il descrittore di tipo personalizzato  
 Implementare il `GetCustomProperties` metodo per il descrittore di tipo per il `ExampleModel` classe di dominio.  
  
> [!NOTE]
>  Il codice generato per il descrittore di tipo personalizzato per gli strumenti DSL `ExampleModel` chiamate `GetCustomProperties`; tuttavia, gli strumenti DSL genera il codice che implementa il metodo.  
  
 Definizione di questo metodo crea il rilevamento descrittore di proprietà per la proprietà di rilevamento di Namespace. Fornisce gli attributi per la proprietà di rilevamento consente inoltre di **proprietà** finestra per visualizzare correttamente la proprietà.  
  
#### <a name="to-modify-the-type-descriptor-for-the-examplemodel-domain-class"></a>Per modificare il descrittore di tipo per la classe di dominio ExampleModel  
  
1.  Aggiungere il codice seguente al file TypeDescriptor.cs.  

    ```csharp  
    using System;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Modeling;  
    using Microsoft.VisualStudio.Modeling.Design;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // To the custom type descriptor for the ExampleElement domain class, add  
        // the GetCustomProperties method.  
        public partial class ExampleElementTypeDescriptor  
        {  
            /// <summary>Returns the property descriptors for the described  
            /// ExampleElement domain class.</summary>  
            /// <remarks>This method adds the tracking property descriptor.  
            /// </remarks>  
            private PropertyDescriptorCollection GetCustomProperties(  
                Attribute[] attributes)  
            {  
                // Get the default property descriptors from the base class  
                PropertyDescriptorCollection propertyDescriptors =  
                    base.GetProperties(attributes);  
  
                // Get a reference to the model element that is being described.  
                ExampleElement source = this.ModelElement as ExampleElement;  
  
                //Add the descriptor for the tracking property.  
                if (source != null)  
                {  
                    DomainPropertyInfo domainProperty =  
                        source.Store.DomainDataDirectory.GetDomainProperty(  
                            ExampleElement.NamespaceDomainPropertyId);  
  
                    DomainPropertyInfo trackingProperty =  
                        source.Store.DomainDataDirectory.GetDomainProperty(  
                            ExampleElement.IsNamespaceTrackingDomainPropertyId);  
  
                    // Define attributes for the tracking property so that the  
                    // Properties window displays the property correctly.  
                    Attribute[] attr = new Attribute[] {  
                        new DisplayNameAttribute("Element Namespace"),  
                        new DescriptionAttribute("The namespace of the element."),  
                        new CategoryAttribute("Tracking Properties"),  
                    };  
  
                    propertyDescriptors.Add(new TrackingPropertyDescriptor(  
                        source, domainProperty, trackingProperty, attr));  
                }  
  
                // Return the property descriptors for this element  
                return propertyDescriptors;  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-package"></a>Aggiunta di codice personalizzato per il pacchetto  
 Il codice generato definisce un provider di descrizioni di tipo per la classe di dominio ExampleElement. Tuttavia, è necessario aggiungere codice per indicare il DSL per utilizzare questo provider di descrizione del tipo.  
  
#### <a name="to-update-the-dsl-package-to-use-your-custom-type-descriptor"></a>Per aggiornare il pacchetto DSL per utilizzare il descrittore di tipo personalizzato  
  
1.  Aggiungere il codice seguente al file Package.cs.  
  
    ```csharp  
    using System.ComponentModel;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // Override the default Initialize method.  
        internal sealed partial class TrackingPropertyDSLPackage  
        {  
            protected override void Initialize()  
            {  
                // Add the custom type descriptor for the ExampleElement type.  
                TypeDescriptor.AddProvider(  
                    new ExampleElementTypeDescriptionProvider(),  
                    typeof(ExampleElement));  
  
                base.Initialize();  
            }  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-model"></a>Aggiunta di codice personalizzato per il modello  
 Implementare il `GetCustomElementsValue` metodo per la `ExampleModel` classe di dominio.  
  
> [!NOTE]
>  Il codice che genera gli strumenti DSL per `ExampleModel` chiamate `GetCustomElementsValue`; tuttavia, gli strumenti DSL genera il codice che implementa il metodo.  
  
 La definizione di `GetCustomElementsValue` metodo fornisce la logica per la proprietà CustomElements calcolato di `ExampleModel`. Questo metodo conta il numero di `ExampleElement` classi di dominio che dispongono di una proprietà che ha un valore utente aggiornato e restituisce una stringa che rappresenta questo numero come una proporzione degli elementi totali nel modello di rilevamento di Namespace.  
  
 Inoltre, aggiungere un `OnDefaultNamespaceChanged` metodo `ExampleModel`ed eseguire l'override il `OnValueChanged` metodo il `DefaultNamespacePropertyHandler` annidati di classe di `ExampleModel` per chiamare `OnDefaultNamespaceChanged`.  
  
 Poiché la proprietà DefaultNamespace viene utilizzata per calcolare le proprietà, di rilevamento di Namespace `ExampleModel` deve notificare tutti `ExampleElement` classi di dominio che è stato modificato il valore di una proprietà DefaultNamespace.  
  
#### <a name="to-modify-the-property-handler-for-the-tracked-property"></a>Per modificare il gestore di proprietà per la proprietà rilevata  
  
1.  Aggiungere il codice seguente al file ExampleModel.cs.  
  
    ```csharp  
    using System.Linq;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        public partial class ExampleModel  
        {  
            public string GetCustomElementsValue()  
            {  
                if (this.Elements.Count == 0) return "0/0";  
  
                int number = this.Elements.Count(e => !e.IsNamespaceTracking);  
                return string.Format("{0}/{1}", number, this.Elements.Count);  
            }  
  
            #region Value changed handler for the tracked property  
  
            // When a tracked property changes, it needs to notify all of the properties  
            // that track it.  
  
            /// <summary>Called by the DefaultNamespace property value handler when the  
            /// DefaultNamespace property changes.</summary>  
            /// <param name="oldValue">The previous value of the property.</param>  
            /// <param name="newValue">The new value of the property.</param>  
            protected virtual void OnDefaultNamespaceChanged(  
                string oldValue, string newValue)  
            {  
                // Use the helper class to notify all of the elements in the model  
                // that the default namespace has changed.  
                TrackingHelper.UpdateTrackingCollectionProperty(  
                    this.Store,  
                    this.Elements,  
                    ExampleElement.NamespaceDomainPropertyId,  
                    ExampleElement.IsNamespaceTrackingDomainPropertyId);  
            }  
  
            // Update the change handler for the DefaultNamespace property.  
            internal sealed partial class DefaultNamespacePropertyHandler  
            {  
                /// <summary>Called when the DefaultNamespace property changes.</summary>  
                /// <param name="element">The model element that has the property that  
                /// changed.</param>  
                /// <param name="oldValue">The previous value of the property.</param>  
                /// <param name="newValue">The new value of the property.</param>  
                protected override void OnValueChanged(  
                    ExampleModel element, string oldValue, string newValue)  
                {  
                    base.OnValueChanged(element, oldValue, newValue);  
  
                    if (!element.Store.InUndoRedoOrRollback)  
                    {  
                        element.OnDefaultNamespaceChanged(oldValue, newValue);  
                    }  
                }  
            }  
  
            #endregion  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-for-the-tracking-property"></a>Aggiunta di codice personalizzato per la proprietà di rilevamento  
 Aggiungere un `CalculateNamespace` metodo per la `ExampleElement` classe di dominio.  
  
 La definizione di questo metodo viene fornita la logica per la proprietà CustomElements calcolato di `ExampleModel`. Questo metodo conta il numero di `ExampleElement` classi di dominio che dispongono di una proprietà che è l'aggiornamento di rilevamento di Namespace per lo stato utente e restituisce una stringa che rappresenta questo numero come una proporzione degli elementi totali nel modello.  
  
 Inoltre, aggiungere spazio di archiviazione per e metodi get e set, la proprietà di archiviazione personalizzati Namespace del `ExampleElement` classe di dominio.  
  
> [!NOTE]
>  Il codice che genera gli strumenti DSL per `ExampleModel` chiamate get e set di metodi; tuttavia, gli strumenti DSL genera il codice che implementa i metodi.  
  
#### <a name="to-add-the-method-for-the-custom-type-descriptor"></a>Per aggiungere il metodo per il descrittore di tipo personalizzato  
  
1.  Aggiungere il codice seguente al file NamespaceTrackingProperty.cs.  
  
    ```csharp  
    using System;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        // To the domain class that has the tracking property, add the caluclation  
        // for when the property is tracking.  
        public partial class ExampleElement  
        {  
            /// <summary>Calculates the actual value of the property when it is  
            /// tracking.</summary>  
            /// <returns>The value of the tracking property when it is  
            /// tracking.</returns>  
            /// <remarks>Making this method virtual allows child classes to modify  
            /// the calculation. This method does not need to perform validation, as  
            /// its caller handles validation prior to calling this method.  
            /// <para>In this case, the tracking value depends on the default namespace  
            /// property of the parent model.</para></remarks>  
            protected virtual string CalculateNamespace()  
            {  
                return this.ExampleModel.DefaultNamespace;  
            }  
  
            #region Tracking property implementation  
  
            // Implement the Namespace domain property of the ExampleElement domain class,  
            // and update the IsNamespaceTracking domain property value handler.  
  
            /// <summary>Storage for the Namespace property.</summary>  
            private string namespaceStorage;  
  
            /// <summary>Gets the value of the Namespace property.</summary>  
            /// <returns>The value of the Namespace property.</returns>  
            private string GetNamespaceValue()  
            {  
                // Only retrieve the tracked value if the store is not in the  
                // middle of a serialization transaction.  
                bool loading = this.Store.TransactionManager.InTransaction  
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;  
  
                if (!loading && this.IsNamespaceTracking)  
                {  
                    try  
                    {  
                        return this.CalculateNamespace();  
                    }  
                    catch (NullReferenceException)  
                    {  
                        return default(string);  
                    }  
                    catch (Exception e)  
                    {  
                        if (CriticalException.IsCriticalException(e))  
                        {  
                            throw;  
                        }  
                        else  
                        {  
                            return default(string);  
                        }  
                    }  
                }  
  
                return namespaceStorage;  
            }  
  
            /// <summary>Sets the value of the Namespace property.</summary>  
            /// <param name="value">The new value for the property.</param>  
            private void SetNamespaceValue(string value)  
            {  
                namespaceStorage = value;  
  
                // Only update the state of the tracking property if the store is  
                // not in the middle of a serialization transaction.  
                bool loading = this.Store.TransactionManager.InTransaction  
                    && this.Store.TransactionManager.CurrentTransaction.IsSerializing;  
  
                if (!this.Store.InUndoRedoOrRollback && !loading)  
                {  
                    this.IsNamespaceTracking = false;  
                }  
            }  
  
            // Update the default behavior of the ExampleElement.IsNamespaceTracking  
            // domain property value handler.  
            internal sealed partial class IsNamespaceTrackingPropertyHandler  
            {  
                /// <summary>Called after the IsNamespaceTracking property changes.  
                /// </summary>  
                /// <param name="element">The model element that has the property  
                /// that changed.</param>  
                /// <param name="oldValue">The previous value of the property.  
                /// </param>  
                /// <param name="newValue">The new value of the property.</param>  
                protected override void OnValueChanged(  
                    ExampleElement element, Boolean oldValue, Boolean newValue)  
                {  
                    base.OnValueChanged(element, oldValue, newValue);  
                    if (!element.Store.InUndoRedoOrRollback && newValue)  
                    {  
                        DomainPropertyInfo propInfo =  
                            element.Store.DomainDataDirectory.GetDomainProperty(  
                                ExampleElement.NamespaceDomainPropertyId);  
                        propInfo.NotifyValueChange(element);  
                    }  
                }  
  
                /// <summary>Performs the reset operation for the IsNamespaceTracking  
                /// property for a model element.</summary>  
                /// <param name="element">The model element that has the property  
                /// to reset.</param>  
                internal void ResetValue(ExampleElement element)  
                {  
                    object calculatedValue = null;  
  
                    try  
                    {  
                        calculatedValue = element.CalculateNamespace();  
                    }  
                    catch (NullReferenceException)  
                    {  
                    }  
                    catch (System.Exception e)  
                    {  
                        if (CriticalException.IsCriticalException(e))  
                        {  
                            throw;  
                        }  
                    }  
  
                    if ((calculatedValue != null  
                        && object.Equals(element.Namespace, calculatedValue)))  
                    {  
                        element.isNamespaceTrackingPropertyStorage = true;  
                    }  
                }  
  
                /// <summary>Method to set IsNamespaceTracking to false so that this  
                /// instance of this tracking property is not storage-based.  
                /// </summary>  
                /// <param name="element">The element on which to reset the property  
                /// value.</param>  
                internal void PreResetValue(ExampleElement element)  
                {  
                    // Force the IsNamespaceTracking property to false so that the value  
                    // of the Namespace property is retrieved from storage.  
                    element.isNamespaceTrackingPropertyStorage = false;  
                }  
            }  
  
            #endregion  
        }  
    }  
    ```  
  
## <a name="adding-custom-code-to-support-serialization"></a>Aggiunta di codice personalizzato per supportare la serializzazione  
 Aggiungere codice per supportare il comportamento di post-carico personalizzato per la serializzazione XML.  
  
> [!NOTE]
>  Il codice che gli strumenti DSL generare chiamate di `OnPostLoadModel` e `OnPostLoadModelAndDiagram` metodi; tuttavia, gli strumenti DSL genera il codice che implementa i metodi.  
  
#### <a name="to-add-code-to-support-the-custom-post-load-behavior"></a>Per aggiungere il codice per supportare il comportamento di post-carico personalizzato  
  
1.  Aggiungere il codice seguente al file Serialization.cs.  
  
    ```csharp  
    using System;  
    using System.Diagnostics;  
    using Microsoft.VisualStudio.Modeling;  
  
    namespace CompanyName.ProductName.TrackingPropertyDSL  
    {  
        #region Helper classes for maintaining state while the store is serializing.  
  
        public abstract partial class TrackingPropertyDSLSerializationHelperBase  
        {  
            /// <summary>Reset the tracking state properties to their natural values  
            /// based on comparing storage with calculation.</summary>  
            /// <param name="store">The store that contains this model.</param>  
            internal static void ResetTrackingProperties(Store store)  
            {  
                // Two passes required - one to set all elements to storage-based  
                // then another to set some back to being tracking.  
                foreach (ModelElement element in store.ElementDirectory.AllElements)  
                {  
                    ExampleElement myElementInstance = element as ExampleElement;  
                    if (myElementInstance != null)  
                    {  
                        myElementInstance.PreResetIsTrackingProperties();  
                        continue;  
                    }  
                }  
                foreach (ModelElement element in store.ElementDirectory.AllElements)  
                {  
                    ExampleElement myElementInstance = element as ExampleElement;  
                    if (myElementInstance != null)  
                    {  
                        myElementInstance.ResetIsTrackingProperties();  
                        continue;  
                    }  
                }  
            }  
        }  
  
        // Add the pre-reset and reset methods for the model element.  
        public partial class ExampleElement  
        {  
            /// <summary>Calls the pre-reset method on the associated property value  
            /// handler for each tracking property of this model element.</summary>  
            internal virtual void PreResetIsTrackingProperties()  
            {  
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.PreResetValue(this);  
            }  
  
            /// <summary>Calls the reset method on the associated property value  
            /// handler for each tracking property of this model element.</summary>  
            internal virtual void ResetIsTrackingProperties()  
            {  
                ExampleElement.IsNamespaceTrackingPropertyHandler.Instance.ResetValue(this);  
            }  
        }  
  
        #endregion  
  
        #region Custom serialization code  
  
        // To the serialization helper for the TrackingPropertyDSL class, add post  
        // load handlers to bind the tracking property to the serialization process.  
        // These handlers manage the tracking states and property values when the  
        // model is serialized and deserialized.  
        public partial class TrackingPropertyDSLSerializationHelperBase  
        {  
            /// <summary>Customize model loading.</summary>  
            /// <param name="serializationResult">The serialization result from the  
            /// load operation.</param>  
            /// <param name="partition">The partition in which the new  
            /// instance was created.</param>  
            /// <param name="fileName">The name of the file from which the  
            /// instance was deserialized.</param>  
            /// <param name="modelRoot">The root of the file that was loaded.  
            /// </param>  
            private void OnPostLoadModel(  
                SerializationResult serializationResult,  
                Partition partition,  
                string fileName,  
                ExampleModel modelRoot)  
            {  
            }  
  
            /// <summary>Customize model and diagram loading.</summary>  
            /// <param name="serializationResult">Stores serialization result from  
            /// the load operation.</param>  
            /// <param name="modelPartition">Partition in which the new  
            /// instance will be created.</param>  
            /// <param name="modelFileName">Name of the file from which the  
            /// instance will be deserialized.</param>  
            /// <param name="diagramPartition">Partition in which the new  
            /// diagram instance will be created.</param>  
            /// <param name="diagramFileName">Name of the file from which the  
            /// diagram instance will be deserialized.</param>  
            /// <param name="modelRoot">The root of the file that was loaded.</param>  
            /// <param name="diagram">The diagram matching the modelRoot.</param>  
            private void OnPostLoadModelAndDiagram(  
                SerializationResult serializationResult,  
                Partition modelPartition,  
                string modelFileName,  
                Partition diagramPartition,  
                string diagramFileName,  
                ExampleModel modelRoot,  
                TrackingPropertyDSLDiagram diagram)  
            {  
                Debug.Assert(modelPartition != null);  
                Debug.Assert(modelPartition.Store != null);  
  
                // Tracking properties need to be set up according to whether the  
                // serialization matches the calculated values.  
                TrackingPropertyDSLSerializationHelperBase.ResetTrackingProperties(  
                    modelPartition.Store);  
            }  
        }  
  
        #endregion  
    }  
    ```  
  
## <a name="testing-the-language"></a>La lingua di test  
 Il passaggio successivo consiste nel compilare ed eseguire la finestra di progettazione DSL in una nuova istanza della [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] in modo da poter verificare che funzioni correttamente, la proprietà di rilevamento.  
  
#### <a name="to-exercise-the-language"></a>Esercitare la lingua  
  
1.  Nel **compilare** menu, fare clic su **Ricompila soluzione**.  
  
2.  Scegliere **Avvia debug** dal menu **Debug**.  
  
     La build sperimentale di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] apre il **debug** soluzione che contiene un file di test vuoto.  
  
3.  In **Esplora**, doppio clic sul file Test.trackingPropertyDsl per aprirlo nella finestra di progettazione e quindi fare clic nell'area di progettazione.  
  
     Si noti che il **proprietà** finestra per il diagramma, il **Default Namespace** proprietà è **DefaultNamespace**e **elementi personalizzati** proprietà **0/0**.  
  
4.  Trascinare un **ExampleElement** elemento il **della casella degli strumenti** sulla superficie del diagramma.  
  
5.  Nel **proprietà** finestra per l'elemento, seleziona il **elemento Namespace** , proprietà e modificare il valore da **DefaultNamespace** a  **OtherNamespace**.  
  
     Si noti che il valore di **elemento Namespace** viene ora visualizzato in grassetto.  
  
6.  Nel **proprietà** finestra, fare doppio clic su **elemento Namespace**, quindi fare clic su **reimpostare**.  
  
     Il valore della proprietà viene modificato in **DefaultNamespace**, e viene visualizzato il valore in un tipo di carattere normale.  
  
     Fare doppio clic su **elemento Namespace** nuovamente. Il **reimpostare** comando è disabilitato perché la proprietà è attualmente in stato di rilevamento.  
  
7.  Trascinare un'altra **ExampleElement** dal **della casella degli strumenti** superficie del diagramma, le modifiche relative **elemento Namespace** a **OtherNamespace**.  
  
8.  Fare clic nell'area di progettazione.  
  
     Nel **proprietà** finestra per il diagramma, il valore di **elementi personalizzati** è ora **1/2**.  
  
9. Modifica **Default Namespace** per il diagramma da **DefaultNamespace** a **NewNamespace**.  
  
     Il **Namespace** delle tracce elemento prima di **Default Namespace** proprietà, mentre il **Namespace** del secondo elemento mantiene il valore aggiornato utente  **OtherNamespace**.  
  
10. Salvare la soluzione e quindi chiudere la build sperimentale.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Se si prevede di utilizzare rilevamento più di una proprietà o implementare le proprietà di rilevamento in più di un linguaggio DSL, è possibile creare un modello di testo per generare il codice comune per il supporto di ogni proprietà di rilevamento. Per ulteriori informazioni sui modelli di testo, vedere [la generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Modeling.Design.TrackingPropertyDescriptor>   
 <xref:Microsoft.VisualStudio.Modeling.Design.ElementTypeDescriptor>   
 [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)   
 [Procedura: Creare una soluzione per un linguaggio specifico di dominio](../modeling/how-to-create-a-domain-specific-language-solution.md)   
