---
title: Implementazione di esempio di valori modificabili | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, local values
- debugging [Debugging SDK], expression evaluation
ms.assetid: ee2d955b-12ca-4f27-89aa-c2d0e768b6b6
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6a7f8f8c352db4f2fcd0230f4eac66e8bddb94e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839723"
---
# <a name="sample-implementation-of-changing-values"></a>Implementazione di esempio di modifica dei valori
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 A ogni locale visualizzato nella finestra **variabili locali** è associato un oggetto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) . Questo `IDebugProperty2` oggetto contiene il nome, il valore e il tipo del locale. Quando un utente modifica il valore di un oggetto locale, Visual Studio chiama [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) per aggiornare il valore del locale in memoria. In questo esempio, il locale è rappresentato dalla `CFieldProperty` classe che implementa l' `IDebugProperty2` interfaccia.  
  
> [!NOTE]
> Per le espressioni di **controllo e controllo** **immediato** , il valore da modificare è rappresentato dalla `CValueProperty` classe nell'esempio MyCEE. Tuttavia, l'implementazione di `IDebugProperty2::SetValueAsString` è identica a quella illustrata di seguito.  
  
 Questa implementazione di `IDebugProperty2::SetValueAsString` esegue le attività seguenti:  
  
1. Valuta l'espressione per produrre un valore.  
  
2. Associa l'oggetto [IDebugField](../../extensibility/debugger/reference/idebugfield.md) associato alla relativa posizione di memoria e produce un oggetto [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) .  
  
3. Converte il valore in una serie di byte.  
  
4. Chiama [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) per archiviare i byte in memoria.  
  
## <a name="managed-code"></a>Codice gestito  
 Si tratta di un'implementazione di `IDebugProperty2::SetValueAsString` nel codice gestito.  
  
```  
[C#]  
namespace EEMC  
{  
    public class CFieldProperty : IDebugProperty2  
    {  
        public HRESULT SetValueAsString(  
            string pszValue,  
            uint   dwRadix,  
            uint   dwTimeout)  
        {  
            HRESULT hr = COM.E_NOTIMPL;  
            uint flags = (uint)enum_PARSEFLAGS.PARSE_EXPRESSION;  
            CParsedExpression parsedExpression =  
                new CParsedExpression(flags, dwRadix, pszValue);  
            IDebugProperty2 value;  
            parsedExpression.EvaluateSync(flags,  
                                          dwTimeout,  
                                          null,  
                                          null,  
                                          null,  
                                          "string",  
                                          out value);  
            if (value != null)  
            {  
                DEBUG_PROPERTY_INFO[] dpi = new DEBUG_PROPERTY_INFO[1];  
                hr = value.GetPropertyInfo(  
                    (uint)enum_DEBUGPROP_INFO_FLAGS.DEBUGPROP_INFO_VALUE,  
                    dwRadix,  
                    dwTimeout,  
                    null,  
                    0,  
                    dpi);  
                if (hr == COM.S_OK)  
                {  
                    hr = Field.SetValue(binder,  
                                        field,  
                                        dpi[0].bstrValue);  
                }  
            }  
            return hr;  
        }  
    }  
  
//----------------------------------------------------------------------------  
  
    internal class Field  
    {  
        internal static HRESULT SetValue(  
            IDebugBinder binder,  
            IDebugField  field,  
            string       bstrValue)  
        {  
            HRESULT hr = COM.E_FAIL;  
            uint fieldSize = 0;  
            Type fieldType = GetType(field, out fieldSize);  
            if (fieldType != null)  
            {  
                FIELD_INFO[] fi = new FIELD_INFO[1];  
                hr = field.GetInfo((uint)enum_FIELD_INFO_FIELDS.FIF_MODIFIERS, fi);  
                if (hr != COM.S_OK ||  
                   (fi[0].dwModifiers & (uint)enum_FIELD_MODIFIERS.FIELD_MOD_CONSTANT) != 0)  
                {  
                    // Couldn't get field info or field is constant and can't be changed.  
                    return COM.E_FAIL;  
                }  
                IDebugObject valueObject;  
                IntPtr pBuffer = new IntPtr();  
                int bufferSize = 0;  
                binder.Bind(null, field, out valueObject);  
                if (valueObject != null)  
                {  
                    if (fieldType == typeof(sbyte))  
                    {  
                        sbyte value = Convert.ToSByte(bstrValue);  
                        bufferSize = 1;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                    if (fieldType == typeof(short))  
                    {  
                        System.Int16 value = Convert.ToInt16(bstrValue);  
                        bufferSize = 2;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                    if (fieldType == typeof(int))  
                    {  
                        System.Int32 value = Convert.ToInt32(bstrValue);  
                        bufferSize = 4;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                    if (fieldType == typeof(long))  
                    {  
                        System.Int64 value = Convert.ToInt64(bstrValue);  
                        bufferSize = 8;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                    if (fieldType == typeof(byte))  
                    {  
                        byte value = Convert.ToByte(bstrValue);  
                        bufferSize = 1;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                    if (fieldType == typeof(char))  
                    {  
                        char value = Convert.ToChar(bstrValue);  
                        bufferSize = 1;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                    if (fieldType == typeof(bool))  
                    {  
                        bool value = Convert.ToBoolean(bstrValue);  
                        bufferSize = 1;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                    if (fieldType == typeof(uint))  
                    {  
                        System.UInt32 value = Convert.ToUInt32(bstrValue);  
                        bufferSize = 4;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                    }  
  
                   if (fieldType == typeof(ulong))  
                   {  
                        System.UInt64 value = Convert.ToUInt64(bstrValue);  
                        bufferSize = 8;  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                   }  
  
                   if (fieldType == typeof(float))  
                   {  
                        float value = Convert.ToSingle(bstrValue);  
                        bufferSize = sizeof(float);  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                   }  
  
                   if (fieldType == typeof(double))  
                   {  
                        double value = Convert.ToDouble(bstrValue);  
                        bufferSize = sizeof(double);  
                        pBuffer = Marshal.AllocCoTaskMem(bufferSize);  
                        Marshal.StructureToPtr(value, pBuffer, false);  
                   }  
  
                   if (fieldType == typeof(string))  
                   {  
                        bufferSize = bstrValue.Length;  
                        pBuffer = Marshal.StringToCoTaskMemAuto(bstrValue);  
                   }  
                   if (bufferSize != 0)  
                   {  
                        byte[] byteBuffer = new byte[bufferSize];  
                        for (int i = 0; i < bufferSize; i++)  
                        {  
                            byteBuffer[i] = Marshal.ReadByte(pBuffer,i);  
                        }  
                        Marshal.FreeCoTaskMem(pBuffer);  
                        hr = valueObject.SetValue(byteBuffer, (uint)bufferSize);  
                    }  
                }  
            }  
            return hr;  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code"></a>Codice non gestito  
 Si tratta di un'implementazione di `IDebugProperty2::SetValueAsString` nel codice gestito. La funzione helper `FieldCoerceValueType` (non mostrata) impone a un `VARIANT` tipo specifico e assicura che il valore sia uno dei tipi che `FieldSetValue` può gestire.  
  
```  
[C++]  
STDMETHODIMP CFieldProperty::SetValueAsString(   
        in LPCOLESTR pszValueStr,  
        in DWORD     radix,  
        in DWORD     timeout  
        )  
{  
    HRESULT hr;  
  
    //evaluate the value  
    VARIANT value;  
    hr = Evaluate( m_provider,  
                   m_address,  
                   m_binder,  
                   pszValueStr,  
                   NULL,  
                   &value );  
    if (FAILED(hr))  
        return hr;  
    if (hr == S_FALSE)  
        return E_FAIL;   //parse failed  
  
    //copy the bits  
    hr = FieldSetValue( m_binder, m_field, value );  
  
    return hr;  
}  
  
//----------------------------------------------------------------------------  
  
HRESULT FieldSetValue(  
        in IDebugBinder* pbinder,  
        in IDebugField*  pfield,  
        in VARIANT&      rawValue )  
{  
    if (pfield == NULL)  
        return E_INVALIDARG;  
  
    if (pbinder == NULL)  
        return E_INVALIDARG;  
  
    HRESULT       hr      = S_OK;  
    IDebugObject* pobject = NULL;  
    VARIANT       value;  
    VariantInit(&value);  
  
    //check the type  
    hr = FieldCoerceValueType( pbinder, pfield, rawValue, &value );  
    if (FAILED(hr))  
        goto fail;  
    if (hr == S_FALSE)  
    {  
        VariantClear(value);  
        return E_FAIL;  
    }  
  
    //get the object  
    hr = pbinder->Bind( NULL, pfield, &pobject );  
    if (FAILED(hr))  
    {  
        pobject->Release();  
        VariantClear(value);  
        return hr;  
    }  
  
    //set the value  
    switch (value.vt)  
    {  
        case VT_BSTR:  
        {  
            if (value.bstrVal == NULL)  
            {  
                LPOLESTR pszEmptyStr = OLE("");  
                hr = pobject->SetValue( reinterpret_cast<BYTE*>(pszEmptyStr),  
                     sizeof(OLECHAR) );  
            }  
            else  
                hr = pobject->SetValue( reinterpret_cast<BYTE*>(value.bstrVal),  
                    (SysStringLen(value.bstrVal)+1) * sizeof(wchar_t));  
        }  
  
        case VT_BOOL:  
        case VT_I1:  
        case VT_UI1:  
            hr = pobject->SetValue( reinterpret_cast<BYTE*>(&(value.byref)), 1 );  
            break;  
  
        case VT_I2:  
        case VT_UI2:  
            hr = pobject->SetValue( reinterpret_cast<BYTE*>(&(value.byref)), 2 );  
            break;  
  
        case VT_I4:  
        case VT_UI4:  
        case VT_R4:  
            hr = pobject->SetValue( reinterpret_cast<BYTE*>(&(value.byref)), 4 );  
            break;  
  
        case VT_I8:  
        case VT_UI8:  
        case VT_R8:  
            hr = pobject->SetValue( reinterpret_cast<BYTE*>(&(value.byref)), 8 );  
            break;  
  
        case VT_VOID:  
        case VT_EMPTY:  
            hr = E_FAIL;  
            break;  
  
        case VT_UNKNOWN:  
        {  
            //this is also a field (structured type)  
            if (value.punkVal == NULL)  
            {  
                pobject->Release();  
                VariantClear(value);  
                return E_FAIL;  
            };  
  
            IDebugField* valueField;  
            hr = value.punkVal->QueryInterface( IID_IDebugField,  
                reinterpret_cast<void**>(&valueField) );  
            if (FAILED(hr))  
            {  
                pobject->Release();  
                VariantClear(value);  
                return hr;  
            };  
  
            //for MyC we simply copy the bits  
            IDebugObject* valueObject;  
            hr = pbinder->Bind( NULL, valueField, &valueObject );  
            valueField->Release();  
            if (FAILED(hr))  
            {  
                pobject->Release();  
                VariantClear(value);  
                return hr;  
            };  
  
            BYTE* pvalueBits;  
            UINT  valueSize;  
            hr = valueObject->GetSize( &valueSize );  
            if (FAILED(hr))  
            {  
                valueObject->Release();  
                pobject->Release();  
                VariantClear(value);  
                return hr;  
            };  
  
            pvalueBits = NALLOC(BYTE,valueSize+1);  
            if (!pvalueBits)  
            {  
                valueObject->Release();  
                pobject->Release();  
                VariantClear(value);  
                return E_OUTOFMEMORY;  
            };  
  
            hr = valueObject->GetValue( pvalueBits, valueSize );  
            valueObject->Release();  
            if (FAILED(hr))  
            {  
                free(pvalueBits);  
                pobject->Release();  
                VariantClear(value);  
                return hr;  
            }  
  
            hr = pobject->SetValue( pvalueBits, valueSize );  
            free(pvalueBits);  
            if (FAILED(hr))  
            {  
                pobject->Release();  
                VariantClear(value);  
                return hr;  
            }  
  
            break;  
        }  
  
        default:  
            //not a primitive type  
            hr = E_FAIL;  
            break;  
    }  
  
    VariantClear( &value );  
    pobject->Release();  
    return hr;  
}  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Modifica del valore di un oggetto locale](../../extensibility/debugger/changing-the-value-of-a-local.md)   
 [Contesto di valutazione](../../extensibility/debugger/evaluation-context.md)
