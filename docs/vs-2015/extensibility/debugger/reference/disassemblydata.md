---
title: DisassemblyData | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cb7682129ed077cf7f84f9a72edc5e75c0398ff3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51804547"
---
# <a name="disassemblydata"></a>DisassemblyData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Descrive un'istruzione disassembly per l'ambiente di sviluppo integrato (IDE) da visualizzare.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
typedef struct tagDisassemblyData {   
   DISASSEMBLY_STREAM_FIELDS dwFields;  
   BSTR                      bstrAddress;  
   BSTR                      bstrAddressOffset;  
   BSTR                      bstrCodeBytes;  
   BSTR                      bstrOpcode;  
   BSTR                      bstrOperands;  
   BSTR                      bstrSymbol;  
   UINT64                    uCodeLocationId;  
   TEXT_POSITION             posBeg;  
   TEXT_POSITION             posEnd;  
   BSTR                      bstrDocumentUrl;  
   DWORD                     dwByteOffset;  
   DISASSEMBLY_FLAGS         dwFlags;  
} DisassemblyData;  
```  
  
```csharp  
public struct DisassemblyData {   
   public uint          dwFields;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrCodeBytes;  
   public string        bstrOpcode;  
   public string        bstrOperands;  
   public string        bstrSymbol;  
   public ulong         uCodeLocationId;  
   public TEXT_POSITION posBeg;  
   public TEXT_POSITION posEnd;  
   public string        bstrDocumentUrl;  
   public uint          dwByteOffset;  
   public uint          dwFlags;  
};  
```  
  
## <a name="members"></a>Membri  
 `dwFields`  
 Il [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) costante che specifica quali campi vengono compilati.  
  
 `bstrAddress`  
 L'indirizzo come offset da un punto di partenza (in genere l'inizio della funzione associata).  
  
 `bstrCodeBytes`  
 I byte di codice per questa istruzione.  
  
 `bstrOpcode`  
 Il codice operativo per questa istruzione.  
  
 `bstrOperands`  
 Gli operandi per l'istruzione.  
  
 `bstrSymbol`  
 Il nome del simbolo, se presente, associato all'indirizzo (simboli pubblici, label e così via).  
  
 `uCodeLocationId`  
 L'identificatore percorso codice per questa linea disassemblata. Se l'indirizzo del contesto di codice di una riga è maggiore dell'indirizzo del contesto di codice di un'altra, l'identificatore percorso codice disassemblato del primo anche sarà maggiore l'identificatore percorso codice del secondo.  
  
 `posBeg`  
 Il [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) che corrisponde alla posizione in un documento in cui iniziano i dati di disassemblaggio.  
  
 `posEnd`  
 Il [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) che corrisponde alla posizione in un documento in cui i dati di disassembly termina.  
  
 `bstrDocumentUrl`  
 Per i documenti di testo che possono essere rappresentati come nomi di file, il `bstrDocumentUrl` campo viene compilato con il nome del file in cui è possibile trovare l'origine, utilizzando il formato `file://file name`.  
  
 Per i documenti di testo che non possono essere rappresentati come nomi di file `bstrDocumentUrl` è un identificatore univoco per il documento e il motore di debug deve implementare il [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) (metodo).  
  
 Questo campo può contenere anche altre informazioni sui checksum. Per informazioni dettagliate, vedere la sezione Osservazioni.  
  
 `dwByteOffset`  
 Il numero di byte che è l'istruzione dall'inizio della riga di codice.  
  
 `dwFlags`  
 Il [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) costante che specifica i flag sono attivi.  
  
## <a name="remarks"></a>Note  
 Ogni `DisassemblyData` struttura descrive un'istruzione di disassemblaggio. Viene restituita una matrice delle strutture dal [lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) (metodo).  
  
 Il [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struttura viene usata per solo documenti basati su testo. L'intervallo di codice sorgente per questa istruzione viene compilata solo la prima istruzione generata da un'istruzione o una riga, ad esempio, quando `dwByteOffset == 0`.  
  
 Per i documenti che sono non testuali, un contesto di documento può essere ottenuto dal codice e il `bstrDocumentUrl` campo deve essere un valore null. Se il `bstrDocumentUrl` campo ha lo stesso come il `bstrDocumentUrl` campo precedente `DisassemblyData` elemento della matrice, quindi impostare il `bstrDocumentUrl` su un valore null.  
  
 Se il `dwFlags` campo ha la `DF_DOCUMENT_CHECKSUM` flag impostato, quindi le informazioni di checksum aggiuntivo seguono la stringa a cui punta il `bstrDocumentUrl` campo. In particolare, dopo il carattere di terminazione di stringa null, si segue un GUID che identifica l'algoritmo di checksum, che a sua volta è seguito da un valore a 4 byte che indica il numero di byte del valore di checksum e che a sua volta è seguito con i byte di checksum. Vedere l'esempio in questo argomento su come codificare e decodificare il campo in [!INCLUDE[csprcs](../../../includes/csprcs-md.md)].  
  
## <a name="example"></a>Esempio  
 Il `bstrDocumentUrl` campo può contenere informazioni aggiuntive diverso da una stringa se il `DF_DOCUMENT_CHECKSUM` flag è impostato. Il processo di creazione e la lettura di questa stringa codificata è semplice nel [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)]. Tuttavia, in [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], è molto più difficile. Per chi è interessati, l'esempio seguente illustra un modo per creare la stringa codificata da [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] e un modo per decodificare la stringa codificata in [!INCLUDE[csprcs](../../../includes/csprcs-md.md)].  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
namespace MyNamespace  
    class MyClass  
    {  
        string EncodeData(string documentString,  
                          Guid checksumGuid,  
                          byte[] checksumData)  
        {  
            string returnString = documentString;  
  
            if (checksumGuid == null || checksumData == null)  
            {  
                // Nothing more to do. Just return the string.  
                return returnString;  
            }  
  
            returnString += '\0'; // separating null value  
  
            // Add checksum GUID to string.  
            byte[] guidDataArray  = checksumGuid.ToByteArray();  
            int    guidDataLength = guidDataArray.Length;  
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);  
            }  
            // Copy guid data bytes to string as wide characters.  
            // Assumption: sizeof(char) == 2.  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum count (a 32-bit value).  
            Int32 checksumCount = checksumData.Length;  
            Marshal.StructureToPtr(checksumCount, pBuffer, true);  
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum data.  
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);  
            for (int i = 0; i < checksumCount; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, checksumData[i]);  
            }  
            for (int i = 0; i < checksumCount / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
            Marshal.FreeCoTaskMem(pBuffer);  
  
            return returnString;  
        }  
  
        void DecodeData(    string encodedString,  
                        out string documentString,  
                        out Guid   checksumGuid,  
                        out byte[] checksumData)  
       {  
           documentString = String.Empty;  
           checksumGuid = Guid.Empty;  
           checksumData = null;  
  
           IntPtr pBuffer = Marshal.StringToBSTR(encodedString);  
           if (null != pBuffer)  
           {  
               int bufferOffset = 0;  
  
               // Parse string out.  String is assumed to be Unicode.  
               documentString = Marshal.PtrToStringUni(pBuffer);  
               bufferOffset += (documentString.Length + 1) * sizeof(char);  
  
               // Parse Guid out.  
               // Read guid bytes from buffer and store in temporary  
               // buffer that contains only the guid bytes. Then the  
               // Marshal.PtrToStructure() can work properly.  
               byte[] guidDataArray  = checksumGuid.ToByteArray();  
               int    guidDataLength = guidDataArray.Length;  
               IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);  
               for (int i = 0; i < guidDataLength; i++)  
               {  
                   Marshal.WriteByte(pGuidBuffer, i,  
                                     Marshal.ReadByte(pBuffer, bufferOffset + i);  
               }  
               bufferOffset += guidDataLength;  
               checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));  
               Marshal.FreeCoTaskMem(pGuidBuffer);  
  
              // Parse out the number of checksum data bytes (always 32-bit value).  
              int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);  
              bufferOffset += sizeof(Int32);  
  
              // Parse out the checksum data.  
              checksumData = new byte[dataCount];  
              for (int i = 0; i < dataCount; i++)  
              {  
                  checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);  
              }  
           }  
       }  
    }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)

