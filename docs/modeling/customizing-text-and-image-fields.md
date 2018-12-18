---
title: Personalizzazione dei campi immagine e testo | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: f577669c685d6f42b73c80f947e8edad0c7b9088
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2018
---
# <a name="customizing-text-and-image-fields"></a>Personalizzazione dei campi testo e immagine
Quando si definisce un elemento decorator del testo in una forma, è rappresentato da TextField. Per esempi di inizializzazione di TextFields e altri ShapeFields, controllare Dsl\GeneratedCode\Shapes.cs nella soluzione DSL.  
  
 TextField è un oggetto che gestisce un'area all'interno di una forma, ad esempio lo spazio assegnato a un'etichetta. Un'istanza di TextField viene condivisa tra le molte forme della stessa classe. L'istanza TextField non archiviare il testo dell'etichetta separatamente per ogni istanza: invece di `GetDisplayText(ShapeElement)` assume la forma come un parametro di metodo e possibile cercare il testo dipendono dallo stato corrente della forma e il relativo elemento del modello.  
  
## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Determinazione l'aspetto di un campo di testo  
 Il `DoPaint()` metodo viene chiamato per visualizzare il campo nella schermata. È possibile eseguire l'override del valore predefinito `DoPaint(),` o è possibile eseguire l'override di alcuni metodi che chiama. La seguente versione semplificata dei metodi predefiniti consentono di comprendere come eseguire l'override del comportamento predefinito:  
  
```  
// Simplified version:  
public override void DoPaint(DiagramPaintEventArgs e, ShapeElement parentShape)  
{   
  string text = GetDisplayText(shape);   
  StringFormat format = GetStringFormat(parentShape);  
  Brush brush = GetTextBrush(e.View, shape);  
  using (Font font = GetFont(shape))  
  {  
    e.Graphics.DrawString(text, font, brush, format);  
  }  
}  
// StringFormat determines whether the string is centered etc.  
// To customize statically for all instances of this shape field,   
// assign to DefaultStringFormat.  
// To customize dynamically or per shape, override this:    
public virtual StringFormat GetStringFormat(ShapeElement shape)  
{ return DefaultStringFormat; }  
  
// Override to customize the displayed string:  
public virtual string GetDisplayText(ShapeElement shape)  
{ return this.GetValue(shape).ToString(); }  
  
// Brush determines the text color.  
// To change the brush for every field, change the shape's styleset.   
// To customize to a brush in the style set, override GetTextBrushId.  
// To change the brush to non-standard color, override this.  
// Should take account of whether selected.   
public virtual Brush GetTextBrush(DiagramClientView view, ShapeElement shape)  
{ return shape.StyleSet.GetBrush(this.GetTextBrushId(view, shape)); }  
  
// Brush ID selects a brush from a StyleSet.  
// Either return a member of DiagramBrushes   
// or add your own brush to the shape or application's styleset.  
// Override this to change dynamically or per instance.  
// To change statically, just assign to default values.   
public virtual StyleSetResourceId GetTextBrushId(DiagramClientView view, ShapeElement shape)  
{ return IsSelected(view, shape) ? (view.Focused ? DefaultSelectedTextBrushId  
: DefaultInactiveSelectedTextBrushId ) : DefaultTextBrushId ;  
}  
  
// Font determines the shape and size of the text.  
// To change the font for every field, change the shape's styleset.   
// To customize to a font in the style set, override GetFontId.  
// To change the font to a non-standard font, override this.   
public virtual Font GetFont(ShapeElement shape)  
{ return shape.StyleSet.GetFont(GetFontId(shape)); }  
  
// Selects a font from a styleset.  
// Either return a member of DiagramFonts or   
// add your own font to the shape or application's styleset.  
// To change statically for all instances of this field,   
// assign to DefaultFontId.  
// To change per shape or dynamically, override this.   
public virtual StyleSetResourceId GetFontId(ShapeElement parentShape)  
{ return DefaultFontId; }  
  
```  
  
 Esistono diverse altre coppie di `Get` metodi e `Default` proprietà, ad esempio `DefaultMultipleLine/GetMultipleLine()`. È possibile assegnare un valore per la proprietà predefinita per modificare il valore per tutte le istanze del campo forma. Il valore variare dall'istanza di una forma a un'altra o dipendono dallo stato della forma o il relativo elemento del modello, eseguire l'override di `Get` metodo.  
  
## <a name="static-customizations"></a>Personalizzazioni statiche  
 Se si desidera modificare ogni istanza di questo campo forma, verificare innanzitutto se è possibile impostare la proprietà nella definizione del linguaggio DSL. È possibile impostare dimensioni del carattere e stile, ad esempio, nella finestra Proprietà.  
  
 In caso contrario, quindi eseguire l'override di `InitializeShapeFields` metodo di classe della forma e assegnare un valore appropriato `Default...` proprietà del campo di testo.  
  
> [!WARNING]
>  Per eseguire l'override `InitializeShapeFields()`, è necessario impostare il **genera derivato doppie** proprietà della classe di forma per `true` nella definizione del linguaggio DSL.  
  
 In questo esempio, una forma è un campo di testo che verrà utilizzato per i commenti dell'utente. Si desidera utilizzare il carattere di commento standard. Poiché si tratta di un tipo di carattere standard dal set di stile, è possibile impostare l'id del tipo di carattere predefinito:  
  
```  
  
 partial class ExampleShape  
{   protected override void InitializeShapeFields(IList<ShapeField> shapeFields)  
    {  
      // Fields set up according to DSL Definition:  
      base.InitializeShapeFields(shapeFields);  
      // Find and update comment field:  
      TextField commentField = ShapeElement.FindShapeField(shapeFields, "CommentDecorator") as TextField;  
      // Use the standard font for comments:  
      commentField.DefaultFontId = DiagramFonts.CommentText;  
  
```  
  
## <a name="dynamic-customizations"></a>Personalizzazioni dinamiche  
 Per rendere l'aspetto variano a seconda dello stato di una forma o il relativo elemento di modello, derivare una propria sottoclasse di `TextField` ed eseguire l'override di uno o più `Get...` metodi. È inoltre necessario eseguire l'override di metodo InitializeShapeFields della forma e sostituire l'istanza del campo di testo con un'istanza della classe.  
  
 Nell'esempio seguente fa sì che il tipo di carattere di un campo di testo dipenda lo stato di una proprietà dominio booleano dell'elemento del modello della forma.  
  
 Per eseguire questo codice di esempio, creare una nuova soluzione DSL utilizzando il modello di linguaggio minimo. Aggiungere una proprietà dominio booleano `AlternateState` per la classe di dominio ExampleElement. Aggiungere un elemento decorator icona alla classe ExampleShape e impostare l'immagine in un file bitmap. Fare clic su **Trasforma tutti i modelli**. Aggiungere un nuovo file di codice nel progetto DSL e inserire il codice seguente.  
  
 Per testare il codice, premere F5 e, nella soluzione di debug, aprire un diagramma di esempio. Dovrebbe essere visualizzato lo stato predefinito dell'icona. Selezionare la forma e nella finestra Proprietà modificare il valore di **AlternateState** proprietà. Consiglia di modificare il tipo di carattere del nome dell'elemento.  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
...  
  
  partial class ExampleShape  
  {  
    /// <summary>  
    /// Compose a list of the fields in this shape.  
    /// Called once for each shape class.  
    /// </summary>  
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)  
    {  
      // Fields set up according to DSL Definition:  
      base.InitializeShapeFields(shapeFields);  
      // Replace the text field for NameDecorator:  
      TextField oldField = ShapeElement.FindShapeField(shapeFields, "NameDecorator") as TextField;  
      shapeFields.Remove(oldField);  
      // Replace with my text field based on DSL Definition values:  
      MyTextField newField = new MyTextField(oldField);  
      shapeFields.Add(newField);  
    }  
  }  
  /// <summary>  
  /// Dynamic font depends on state of model element.  
  /// </summary>  
  public class MyTextField : TextField  
  {  
    public MyTextField(TextField prototype)  
      : base(prototype.Name)  
    {  
      DefaultText = prototype.DefaultText;  
      DefaultFocusable = prototype.DefaultFocusable;  
      DefaultAutoSize = prototype.DefaultAutoSize;  
      AnchoringBehavior.MinimumHeightInLines = prototype.AnchoringBehavior.MinimumHeightInLines;  
      AnchoringBehavior.MinimumWidthInCharacters = prototype.AnchoringBehavior.MinimumWidthInCharacters;  
      DefaultAccessibleState = prototype.DefaultAccessibleState;  
    }  
  
    public override System.Drawing.Font GetFont(ShapeElement parentShape)  
    {  
      // Access the Boolean domain property of the model element:  
      if ((parentShape.ModelElement as ExampleElement).AlternateState)  
        return new System.Drawing.Font("Callisto", 14.0f,  
               System.Drawing.FontStyle.Italic |   
               System.Drawing.FontStyle.Bold);  
      else  
        return base.GetFont(parentShape);  
    }  
  
  }  
  
```  
  
## <a name="style-sets"></a>Imposta lo stile  
 Nell'esempio precedente viene illustrato come è possibile modificare il campo di testo per qualsiasi tipo di carattere che è disponibile. Tuttavia, un è preferibile passare in uno dei set di stili associato con la forma o con l'applicazione. A tale scopo, si esegue l'override <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> o GetTextBrushId().  
  
 In alternativa, provare a modificare il set di stile della forma eseguendo l'override <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A>. Questo ha l'effetto della modifica di tipi di carattere e i pennelli per tutti i campi di forma.  
  
## <a name="customizing-image-fields"></a>Personalizzazione dei campi immagine  
 Quando si definisce un elemento decorator dell'immagine in una forma e quando si definisce una forma di immagine, l'area in cui viene visualizzata la forma è gestito da un ImageField. Per esempi di inizializzazione di ImageFields e altri ShapeFields, controllare Dsl\GeneratedCode\Shapes.cs nella soluzione DSL.  
  
 Un ImageField è un oggetto che gestisce un'area all'interno di una forma, ad esempio lo spazio assegnato a un elemento decorator. Un'istanza di ImageField viene condivisa tra le molte forme della stessa classe forma. L'istanza ImageField non archiviare un'immagine distinta per ogni forma: invece di `GetDisplayImage(ShapeElement)` metodo assume la forma come parametro e l'immagine dipendono dallo stato corrente della forma e il relativo elemento del modello è possibile cercare.  
  
 Se si desidera un comportamento speciale, ad esempio un'immagine di variabile, è possibile creare una classe personalizzata derivata da ImageField.  
  
#### <a name="to-create-a-subclass-of-imagefield"></a>Per creare una sottoclasse di ImageField  
  
1.  Impostare il **genera derivato doppie** proprietà della classe nella propria definizione DSL forma padre.  
  
2.  Eseguire l'override di `InitializeShapeFields` metodo della classe di forma.  
  
    -   Creare un nuovo file di codice nel progetto DSL e scrivere una definizione di classe parziale per la classe della forma. Eseguire l'override della definizione di metodo non esiste.  
  
3.  Esaminare il codice del `InitializeShapeFields` in DSL\GeneratedCode\Shapes.cs.  
  
     Nel metodo di override, chiamare il metodo di base e quindi creare un'istanza della classe campo immagine. Utilizzare questa opzione per sostituire il campo di immagine normale nel `shapeFields` elenco.  
  
## <a name="dynamic-icons"></a>Icone dinamiche  
 In questo esempio rende un'icona di modifica dipendente lo stato dell'elemento del modello della forma.  
  
> [!WARNING]
>  In questo esempio viene illustrato come creare un elemento decorator immagine dinamica. Se si desidera passare da una o due immagini a seconda dello stato di una variabile del modello, è più semplice creare diversi elementi Decorator immagine individuarli nella stessa posizione della forma e quindi impostare il filtro di visibilità per dipendono da valori specifici del modello variabile. Per impostare il filtro, selezionare la mappa di forme nella definizione DSL, aprire la finestra Dettagli DSL e fare clic sulla scheda elementi Decorator.  
  
 Per eseguire questo codice di esempio, creare una nuova soluzione DSL utilizzando il modello di linguaggio minimo. Aggiungere una proprietà dominio booleano `AlternateState` per la classe di dominio ExampleElement. Aggiungere un elemento decorator icona alla classe ExampleShape e impostare l'immagine in un file bitmap. Fare clic su **Trasforma tutti i modelli**. Aggiungere un nuovo file di codice nel progetto DSL e inserire il codice seguente.  
  
 Per testare il codice, premere F5 e, nella soluzione di debug, aprire un diagramma di esempio. Dovrebbe essere visualizzato lo stato predefinito dell'icona. Selezionare la forma e nella finestra Proprietà modificare il valore di **AlternateState** proprietà. L'icona viene visualizzata ruotata tramite 90 gradi, tale forma.  
  
```csharp  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
...  
partial class ExampleShape  
{  
    /// <summary>  
    /// Compose a list of the fields in this shape.  
    /// Called once for each shape class.  
    /// </summary>  
    /// <param name="shapeFields"></param>  
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)  
    {  
      // Fields set up according to DSL Definition:  
      base.InitializeShapeFields(shapeFields);  
  
      // Replace the image field:  
      ShapeField oldField = ShapeElement.FindShapeField(shapeFields, "IconDecorator");  
      shapeFields.Remove(oldField);  
      // Must keep the same name:  
      MyImageField newField = new MyImageField(oldField.Name);  
      shapeFields.Add(newField);  
      newField.DefaultImage = (oldField as ImageField).DefaultImage.Clone() as System.Drawing.Image;  
    }  
  }  
  
  public class MyImageField : ImageField  
  {  
    public MyImageField(string tag) : base(tag) { }  
  
    /// <summary>  
    /// Get the image for this field in the given shape.  
    /// </summary>  
    public override System.Drawing.Image GetDisplayImage(ShapeElement parentShape)  
    {  
      ExampleElement element = parentShape.ModelElement as ExampleElement;  
      if (element.AlternateState == true)  
        return AlternateImage;  
      else  
        return base.GetDisplayImage(parentShape);  
    }  
  
    private System.Drawing.Image alternateImage;  
    public System.Drawing.Image AlternateImage  
    {  
      get  
      {  
        if (alternateImage == null)  
        {  
          // Alternate image is a copy of the default, rotated by 90 degrees:  
          alternateImage = this.DefaultImage.Clone() as System.Drawing.Image;  
          alternateImage.RotateFlip(System.Drawing.RotateFlipType.Rotate90FlipNone);  
        }  
        return alternateImage;  
      }  
    }  
  }  
}  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Definizione di forme e connettori](../modeling/defining-shapes-and-connectors.md)   
 [L'impostazione di un'immagine di sfondo in un diagramma](../modeling/setting-a-background-image-on-a-diagram.md)   
 [Esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)