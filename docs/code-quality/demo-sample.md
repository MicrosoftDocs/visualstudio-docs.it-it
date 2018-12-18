---
title: Demo di esempio | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: be42ed54e2c245a47e885fe8310c106c27ea82b2
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/01/2018
---
# <a name="demo-sample"></a>Esempio dimostrativo
Procedure riportate di seguito viene illustrato come creare l'esempio per [procedura dettagliata: analisi di codice C/C++ per i difetti](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Creano le procedure:  
  
-   Oggetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] soluzione denominata CppDemo.  
  
-   Un progetto di libreria statica denominato CodeDefects.  
  
-   Un progetto di libreria statica denominata annotazioni.  
  
 Le procedure forniscono inoltre il codice per i file di intestazione e. cpp per le librerie statiche.  
  
### <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Creare la soluzione CppDemo e il progetto CodeDefects  
  
1.  Fare clic su di **File** dal menu **New**, quindi fare clic su **nuovo progetto**.  
  
2.  Nel **tipi di progetto** struttura ad albero di elenco, se Visual C++ non è la lingua predefinita in Visual Studio espandere **altri linguaggi**.  
  
3.  Espandere **Visual C++**, quindi fare clic su **generale**.  
  
4.  In **modelli**, fare clic su **progetto vuoto**.  
  
5.  Nel **nome** nella casella di testo **CodeDefects**.  
  
6.  Selezionare il **Crea directory per soluzione** casella di controllo.  
  
7.  Nel **Nome soluzione** nella casella di testo **CppDemo**.  
  
### <a name="configure-the-codedefects-project-as-a-static-library"></a>Configurare il progetto CodeDefects come una libreria statica  
  
1.  In Esplora soluzioni fare doppio clic su **CodeDefects** e quindi fare clic su **proprietà**.  
  
2.  Espandere **le proprietà di configurazione** e quindi fare clic su **generale**.  
  
3.  Nel **generale** elenco, selezionare il testo nella colonna accanto a **estensione di destinazione**, quindi digitare **lib**.  
  
4.  In **impostazioni predefinite progetto**, fare clic sulla colonna accanto a **tipo di configurazione**, quindi fare clic su **libreria statica (lib)**.  
  
### <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Aggiungere il file di origine e di intestazione al progetto CodeDefects.  
  
1.  In Esplora soluzioni, espandere **CodeDefects**, fare doppio clic su **file di intestazione**, fare clic su **Aggiungi**, quindi fare clic su **nuovo elemento**.  
  
2.  Nel **Aggiungi nuovo elemento** la finestra di dialogo, fare clic su **codice**, quindi fare clic su **File di intestazione (h)**.  
  
3.  Nel **nome** digitare **bug** e quindi fare clic su **Aggiungi**.  
  
4.  Copiare il codice seguente e incollarlo il **bug** file nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor.  
  
    ```cpp
    #include <windows.h>  
  
    //    
    //These 3 functions are consumed by the sample  
    //  but are not defined. This project cannot be linked!  
    //  
  
    bool CheckDomain( LPCSTR );  
    HRESULT ReadUserAccount();  
  
    //  
    //These constants define the common sizes of the   
    //  user account information throughout the program  
    //  
  
    const int USER_ACCOUNT_LEN = 256;  
    const int ACCOUNT_DOMAIN_LEN = 128;  
    ```  
  
5.  In Esplora soluzioni fare doppio clic su **i file di origine**, scegliere **New**, quindi fare clic su **nuovo elemento**.  
  
6.  Nel **Aggiungi nuovo elemento** la finestra di dialogo, fare clic su **File C++ (. cpp)**  
  
7.  Nel **nome** digitare **bug** e quindi fare clic su **Aggiungi**.  
  
8.  Copiare il codice seguente e incollarlo nel file Bug.h il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor.  
  
    ```cpp
    #include <stdlib.h>  
    #include "Bug.h"  
  
    // the user account   
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";  
    int len = 0;  
  
    bool ProcessDomain()  
    {  
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];  
        // ReadUserAccount gets a 'domain\user' input from   
        //the user into the global 'g_userAccount'  
        if (ReadUserAccount() )  
        {  
  
            // Copies part of the string prior to the '\'   
            // character onto the 'domain' buffer  
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )  
            {  
                if ( g_userAccount[len] == '\\' )   
                {  
                    // Stops copying on the domain and user separator ('\')   
                    break;  
                }  
                domain[len] = g_userAccount[len];          
            }  
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
            {  
                // '\' was not found. Invalid domain\user string.  
                delete [] domain;  
                return false;  
            }  
            else  
            {  
                domain[len]='\0';  
            }  
            // Process domain string  
            bool result = CheckDomain( domain );  
  
            delete[] domain;  
            return result;  
        }  
        return false;  
    }  
  
    int path_dependent(int n)  
    {  
        int i;  
        int j;  
        if (n == 0)  
            i = 1;  
        else  
            j = 1;  
        return i+j;   
    }  
    ```  
  
9. Fare clic su di **File** menu e quindi fare clic su **Salva tutto**.  
  
### <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Aggiungere il progetto di annotazioni e lo configura come una libreria statica  
  
1.  In Esplora soluzioni, fare clic su **CppDemo**, scegliere **Aggiungi**, quindi fare clic su **nuovo progetto**.  
  
2.  Nel **Aggiungi nuovo progetto** finestra di dialogo espandere Visual C++, fare clic su **generale**, quindi fare clic su **progetto vuoto**.  
  
3.  Nel **nome** nella casella di testo **annotazioni**, quindi fare clic su **Aggiungi**.  
  
4.  In Esplora soluzioni fare doppio clic su **annotazioni** e quindi fare clic su **proprietà**.  
  
5.  Espandere **le proprietà di configurazione** e quindi fare clic su **generale**.  
  
6.  Nel **generale** elenco, selezionare il testo nella colonna accanto a **estensione di destinazione**, quindi digitare **lib**.  
  
7.  In **impostazioni predefinite progetto**, fare clic sulla colonna accanto a **tipo di configurazione**, quindi fare clic su **libreria statica (lib)**.  
  
### <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Aggiungere il file di intestazione e il file di origine per il progetto di annotazioni  
  
1.  In Esplora soluzioni, espandere **annotazioni**, fare doppio clic su **file di intestazione**, fare clic su **Aggiungi**, quindi fare clic su **nuovo elemento**.  
  
2.  Nel **Aggiungi nuovo elemento** la finestra di dialogo, fare clic su **File di intestazione (h)**.  
  
3.  Nel **nome** digitare **Annotations. h** e quindi fare clic su **Aggiungi**.  
  
4.  Copiare il codice seguente e incollarlo il **Annotations. h** file nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor.  
  
    ```cpp
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5.  In Esplora soluzioni fare doppio clic su **i file di origine**, scegliere **New**, quindi fare clic su **nuovo elemento**.  
  
6.  Nel **Aggiungi nuovo elemento** la finestra di dialogo, fare clic su **codice** e quindi fare clic su **File C++ (. cpp)**  
  
7.  Nel **nome** digitare **Annotations. cpp** e quindi fare clic su **Aggiungi**.  
  
8.  Copiare il codice seguente e incollarlo il **Annotations. cpp** file nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor.  
  
    ```cpp
    #include <CodeAnalysis/SourceAnnotations.h>  
    #include <windows.h>  
    #include <stdlib.h>    
    #include "annotations.h"  
  
    LinkedList* AddTail( LinkedList *node, int value )  
    {  
        LinkedList *newNode = NULL;   
  
        // finds the last node  
        while ( node->next != NULL )   
        {  
            node = node->next;  
        }  
  
        // appends the new node  
        newNode = AllocateNode();   
        newNode->data = value;  
        newNode->next = 0;  
        node->next = newNode;  
  
        return newNode;  
    }  
  
    ```  
  
9. Fare clic su di **File** menu e quindi fare clic su **Salva tutto**.