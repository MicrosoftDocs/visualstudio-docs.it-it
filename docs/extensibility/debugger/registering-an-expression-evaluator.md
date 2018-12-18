---
title: Registrazione di un analizzatore di espressioni | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluators, registering
ms.assetid: 236be234-e05f-4ad8-9200-24ce51768ecf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a34278ecca071c31e62ff4e405e9d7ada112d425
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="registering-an-expression-evaluator"></a>Registrazione di un analizzatore di espressioni
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 L'analizzatore di espressioni (Java EE) deve eseguire la registrazione come una class factory con l'ambiente Windows COM e Visual Studio. Un EE viene implementato come una DLL in modo che può essere inserito nello spazio degli indirizzi di debug del motore (DE) o lo spazio degli indirizzi di Visual Studio, a seconda di quale entità crea l'analizzatore di Espressioni.  
  
## <a name="managed-code-expression-evaluator"></a>Analizzatore di espressioni di codice gestito  
 Un codice gestito EE viene implementato come una libreria di classi, ovvero una DLL che si registra con l'ambiente di COM, in genere avviata da una chiamata al programma VSIP **regpkg.exe**. L'effettivo processo di scrittura le chiavi del Registro di sistema per l'ambiente COM viene gestito automaticamente.  
  
 Un metodo della classe principale è contrassegnato con il <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>, che indica che tale metodo da chiamare quando la DLL da registrare con COM. Questo metodo di registrazione, spesso denominato `RegisterClass`, esegue l'attività di registrazione della DLL di Visual Studio. Un corrispondente `UnregisterClass` (contrassegnati con il <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>), Annulla gli effetti del `RegisterClass` quando la DLL viene disinstallata.  
  
 Le stesse voci del Registro di sistema vengono effettuate per un EE scritto in codice non gestito. l'unica differenza è che non vi sia alcuna funzione di supporto, ad esempio `SetEEMetric` per svolgere il lavoro per l'utente. Un esempio di questo processo di registrazione/annullamento della registrazione è simile al seguente:  
  
### <a name="example"></a>Esempio  
 Questa funzione viene illustrato come un codice gestito EE registra e Annulla la registrazione di se stesso con Visual Studio.  
  
```csharp  
namespace EEMC  
{  
    [GuidAttribute("462D4A3D-B257-4AEE-97CD-5918C7531757")]  
    public class EEMCClass : IDebugExpressionEvaluator  
    {  
        #region Register and unregister.  
        private static Guid guidMycLang = new Guid("462D4A3E-B257-4AEE-97CD-5918C7531757");  
        private static string languageName = "MyC";  
        private static string eeName = "MyC Expression Evaluator";  
  
        private static Guid guidMicrosoftVendor = new Guid("994B45C4-E6E9-11D2-903F-00C04FA302A1");  
        private static Guid guidCOMPlusOnlyEng = new Guid("449EC4CC-30D2-4032-9256-EE18EB41B62B");  
        private static Guid guidCOMPlusNativeEng = new Guid("92EF0900-2251-11D2-B72E-0000F87572EF");  
  
        /// <summary>  
        /// Register the expression evaluator.  
        /// Set "project properties/configuration properties/build/register for COM interop" to true.  
        /// </summary>  
         [ComRegisterFunctionAttribute]  
        public static void RegisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator";  
  
            RegistryKey rk = Registry.LocalMachine.CreateSubKey(s);  
            if (rk == null)  return;  
  
            rk = rk.CreateSubKey(guidMycLang.ToString("B"));  
            rk = rk.CreateSubKey(guidMicrosoftVendor.ToString("B"));  
            rk.SetValue("CLSID", t.GUID.ToString("B"));  
            rk.SetValue("Language", languageName);  
            rk.SetValue("Name", eeName);  
  
            rk = rk.CreateSubKey("Engine");  
            rk.SetValue("0", guidCOMPlusOnlyEng.ToString("B"));  
            rk.SetValue("1", guidCOMPlusNativeEng.ToString("B"));  
        }  
        /// <summary>  
        /// Unregister the expression evaluator.  
        /// </summary>  
         [ComUnregisterFunctionAttribute]  
        public static void UnregisterClass(Type t)  
        {  
            // Get Visual Studio version (set by regpkg.exe)  
            string hive = Environment.GetEnvironmentVariable("EnvSdk_RegKey");  
            string s = @"SOFTWARE\Microsoft\VisualStudio\"  
                        + hive  
                        + @"\AD7Metrics\ExpressionEvaluator\"  
                        + guidMycLang.ToString("B");  
            RegistryKey key = Registry.LocalMachine.OpenSubKey(s);  
            if (key != null)  
            {  
                key.Close();  
                Registry.LocalMachine.DeleteSubKeyTree(s);  
            }  
        }  
    }  
}  
```  
  
## <a name="unmanaged-code-expression-evaluator"></a>Analizzatore di espressioni di codice non gestito  
 La DLL EE implementa il `DllRegisterServer` funzione di registrarsi con l'ambiente COM, oltre a Visual Studio.  
  
> [!NOTE]
>  Codice del Registro di sistema di esempio di codice MyCEE è reperibile in dllentry.cpp il file, che si trova nell'installazione VSIP in EnVSDK\MyCPkgs\MyCEE.  
  
### <a name="dll-server-process"></a>Processo del Server DLL  
 Quando si registra l'analizzatore di Espressioni, il server DLL:  
  
1.  Registra relativa class factory `CLSID` in base alle convenzioni COM normale.  
  
2.  Chiama la funzione di supporto `SetEEMetric` da registrare con Visual Studio le metriche EE illustrate nella tabella seguente. La funzione `SetEEMetric` e le metriche specificate di seguito fanno parte della libreria dbgmetric.lib. Vedere [SDK helper per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) per informazioni dettagliate.  
  
    |Metrica|Descrizione|  
    |------------|-----------------|  
    |`metricCLSID`|`CLSID` della factory Java EE (classe)|  
    |`metricName`|Nome del motore di esecuzione come una stringa visualizzabile|  
    |`metricLanguage`|Il nome del linguaggio che l'analizzatore di Espressioni è progettato per valutare|  
    |`metricEngine`|`GUID`s dei motori di debug (DE) utilizzabili con questo EE|  
  
    > [!NOTE]
    >  Il `metricLanguage``GUID` identifica la lingua da nome, ma è il `guidLang` argomento `SetEEMetric` che consente di selezionare la lingua. Quando il compilatore genera il file di informazioni di debug, consigliabile scrivere appropriata `guidLang` in modo che la Germania sappia quale EE da utilizzare. La Germania richiede in genere il provider di simboli per questa lingua `GUID`, che viene archiviato nel file di informazioni di debug.  
  
3.  Registra con Visual Studio tramite la creazione di chiavi in HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*x. y*, dove *x. y* è la versione di Visual Studio per registrarsi.  
  
### <a name="example"></a>Esempio  
 Questa funzione viene illustrato come un codice non gestito (C++) EE registra e Annulla la registrazione di se stesso con Visual Studio.  
  
```cpp  
/*---------------------------------------------------------  
  Registration  
-----------------------------------------------------------*/  
#ifndef LREGKEY_VISUALSTUDIOROOT  
    #define LREGKEY_VISUALSTUDIOROOT L"Software\\Microsoft\\VisualStudio\\8.0"  
#endif  
  
static HRESULT RegisterMetric( bool registerIt )  
{  
    // check where we should register  
    const ULONG cchBuffer = _MAX_PATH;  
    WCHAR wszRegistrationRoot[cchBuffer];  
    DWORD cchFreeBuffer = cchBuffer - 1;  
    wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT_NOVERSION);  
    wcscat(wszRegistrationRoot, L"\\");  
  
    // this is Environment SDK specific  
    // we check for  EnvSdk_RegKey environment variable to  
    // determine where to register  
    DWORD cchDefRegRoot = lstrlenW(LREGKEY_VISUALSTUDIOROOT_NOVERSION) + 1;  
    cchFreeBuffer = cchFreeBuffer - cchDefRegRoot;  
    DWORD cchEnvVarRead = GetEnvironmentVariableW(  
        /* LPCTSTR */ L"EnvSdk_RegKey", // environment variable name  
        /* LPTSTR  */ &wszRegistrationRoot[cchDefRegRoot],// buffer for variable value  
        /* DWORD   */ cchFreeBuffer);// size of buffer  
    if (cchEnvVarRead >= cchFreeBuffer)  
        return E_UNEXPECTED;  
    // If the environment variable does not exist then we must use   
    // LREGKEY_VISUALSTUDIOROOT which has the version number.  
    if (0 == cchEnvVarRead)  
        wcscpy(wszRegistrationRoot, LREGKEY_VISUALSTUDIOROOT);  
  
    if (registerIt)  
    {  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricCLSID,  
                    CLSID_MycEE,  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricName,  
                    GetString(IDS_INFO_MYCDESCRIPTION),  
                    wszRegistrationRoot );  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricLanguage, L"MyC",  
                    wszRegistrationRoot);  
  
        GUID engineGuids[2];  
        engineGuids[0] = guidCOMPlusOnlyEng;  
        engineGuids[1] = guidCOMPlusNativeEng;  
        SetEEMetric(guidMycLang,  
                    guidMicrosoftVendor,  
                    metricEngine,  
                    engineGuids,  
                    2,  
                    wszRegistrationRoot);  
    }  
    else  
    {  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricCLSID,  
                        wszRegistrationRoot);  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricName,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricLanguage,  
                        wszRegistrationRoot );  
        RemoveEEMetric( guidMycLang,  
                        guidMicrosoftVendor,  
                        metricEngine,  
                        wszRegistrationRoot );  
    }  
  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)