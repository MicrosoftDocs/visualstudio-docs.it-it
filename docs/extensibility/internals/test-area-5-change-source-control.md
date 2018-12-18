---
title: 'Area test 5: Modifica controllo del codice sorgente | Documenti Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e7fd014bf520ee2f0515e284f2fb5430961cd407
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="test-area-5-change-source-control"></a>Area test 5: Modifica controllo del codice sorgente
Questa area di plug-in test di controllo del codice sorgente riguarda modifica il controllo del codice sorgente tramite la **Modifica controllo del codice sorgente** comando.  
  
 **Modifica controllo del codice sorgente** comando fornisce quattro funzioni di base per l'utente:  
  
-   **Binding:**  
  
     Consente di stabilire o ristabilire un collegamento di controllo di origine tra una soluzione/progetto e l'archivio versione.  
  
-   **Annullamento del binding:**  
  
     Rimuove una progetto/soluzione dal controllo del codice sorgente in una singola connessione.  
  
-   **Connettere/disconnettere:**  
  
 Attiva o disattiva i stato connesso o non in linea della soluzione controllata, che viene descritta nella zona 3. Per ulteriori informazioni, vedere [Test Area 3: estrarre / Annulla estrazione](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).  
  
## <a name="command-menu-access"></a>Accedere al Menu comando  
 Le operazioni seguenti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] percorso menu ambiente di sviluppo integrato viene utilizzato nei test case.  
  
 Modifica controllo del codice sorgente:**File**, **controllo del codice sorgente**, **Modifica controllo del codice sorgente**.  
  
## <a name="test-cases"></a>Test case  
 Di seguito sono specifici test case per il **Modifica controllo del codice sorgente** comando area di test.  
  
### <a name="case-5a-bind"></a>Caso 5a: associazione  
 Operazione di binding consente all'utente di aggiungere informazioni di controllo codice sorgente per i progetti selezionati e le soluzioni. L'utente viene in genere richiesto di identificare un progetto nel controllo del codice sorgente in cui questi devono essere aggiunti. L'utente non può creare un nuovo progetto nel controllo del codice sorgente come parte di questa operazione (contrasto con Aggiungi al controllo del codice sorgente).  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Associare a un percorso vuoto|1.  Creare un progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aprire **Modifica controllo del codice sorgente** la finestra di dialogo (**File**, **controllo del codice sorgente**, **Modifica controllo del codice sorgente**).<br />4.  Fare clic su **disassociare**.<br />5.  Accettare la finestra di dialogo di avviso se viene visualizzato.<br />6.  Selezionare tutti gli elementi.<br />7.  Fare clic su **associare**.<br />8.  Selezionare un percorso vuoto in un archivio del controllo codice sorgente.<br />9. Fare clic su **OK** per chiudere la **Modifica controllo del codice sorgente** la finestra di dialogo.<br />10. Fare clic su **continua con le associazioni** nella finestra di dialogo di conferma.<br />11. Fare clic su **OK** nella finestra di dialogo Avviso Se viene visualizzato.<br />12. Archivia i file. Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />13. Apri soluzione dal controllo del codice sorgente in un nuovo percorso.|`Result from Step 12:`<br /><br /> Soluzioni e progetti sono associate a e scritti nella destinazione di nuovo nell'archivio delle versioni.<br /><br /> Vengono archiviati i file di soluzione e progetto.<br /><br /> Gerarchia del progetto della versione archivio corrisponde la gerarchia di cartelle del progetto su disco.<br /><br /> `Result from Step 13:`<br /><br /> Tutti gli elementi di progetto vengono scaricati.|  
|Associare a una posizione che sia sincronizzato con i client|1.  Creare un progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Creare un duplicato del progetto e soluzione nell'archivio delle versioni (condividere e creare un Branch se si utilizza [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />4.  Aprire **Modifica controllo del codice sorgente** la finestra di dialogo (**File**, **controllo del codice sorgente**, **Modifica controllo del codice sorgente**).<br />5.  Separa tutte.<br />6.  Fare clic su **OK** per chiudere **Modifica controllo del codice sorgente** la finestra di dialogo.<br />7.  Riaprire **Modifica controllo del codice sorgente** la finestra di dialogo.<br />8.  Selezionare tutto.<br />9. Fare clic su **associare**.<br />10. Passare al percorso ramo del progetto e soluzione (dal passaggio 3)<br />11. Fare clic su **OK** per chiudere la **Modifica controllo del codice sorgente** la finestra di dialogo.<br />12. Ottenere più recente in modo ricorsivo per tutti gli elementi.|Contenuto del file dopo get è lo stesso come prima get.|  
|Associare a una posizione che non è sincronizzato con i client|1.  Creare un progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Creare un duplicato del progetto e soluzione nell'archivio delle versioni (condividere e creare un Branch se si utilizza [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]).<br />4.  Modificare i file del progetto sottoposto a branching nell'archivio delle versioni.<br />5.  Aprire **Modifica controllo del codice sorgente** la finestra di dialogo (**File**, **controllo del codice sorgente**, **Modifica controllo del codice sorgente**).<br />6.  Separa tutte.<br />7.  Fare clic su **OK** per chiudere **Modifica controllo del codice sorgente** la finestra di dialogo.<br />8.  Riaprire **Modifica controllo del codice sorgente** la finestra di dialogo.<br />9. Selezionare tutto.<br />10. Fare clic su **associare**.<br />11. Passare al percorso per la soluzione e progetto in precedenza a branching.<br />12. Fare clic su **OK** per chiudere la **Modifica controllo del codice sorgente** la finestra di dialogo.<br />13. Accettare la finestra di dialogo di avviso se viene visualizzato.<br />14. Ottenere ricorsiva più recente per tutti gli elementi.|I file che sono stati modificati nel passaggio 4 sono inoltre modificati localmente.|  
|Soluzione di binding che è stato mai nel controllo del codice sorgente|1.  Creare una cartella vuota nel controllo del codice sorgente.<br />2.  Creare un progetto client.<br />3.  Aprire **Modifica controllo del codice sorgente** la finestra di dialogo (**File**, **controllo del codice sorgente**, **Modifica controllo del codice sorgente**).<br />4.  Associare la soluzione a un percorso vuoto nel controllo del codice sorgente.<br />5.  Fare clic su **OK** per chiudere la **Modifica controllo del codice sorgente** la finestra di dialogo.<br />6.  Fare clic su **continua con le associazioni** nella finestra di dialogo di conferma.<br />7.  Fare clic su **OK** nella finestra di dialogo Avviso Se viene visualizzato.|Soluzione viene aggiunta al controllo del codice sorgente.<br /><br /> Soluzioni e progetti sono stati estratti.|  
|Annullare l'operazione di binding|1.  Creare un progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aprire la finestra di dialogo Modifica controllo del codice sorgente.<br />4.  Separa tutte.<br />5.  Fare clic su **OK** per chiudere la finestra di dialogo. Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />6.  Riaprire il **Modifica controllo del codice sorgente** la finestra di dialogo.<br />7.  L'associazione a un percorso non correlato.<br />8.  Fare clic su **Annulla**.|`Result from Step 5:`<br /><br /> La soluzione non è più in controllo del codice sorgente<br /><br /> `Result from Step 8:`<br /><br /> Soluzione non è ancora non in controllo del codice sorgente.|  
  
### <a name="case-5b-unbind"></a>Caso 5b: separare  
 Annullare l'associazione di informazioni di controllo di codice rimuove origine da progetti e soluzioni personalizzate. La soluzione e progetti interessati sono basati su una combinazione di selezione dell'utente e la modalità in cui sono stati aggiunti gli elementi al controllo del codice sorgente.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Separare soluzione contenente un File System o il progetto Web IIS locale e il progetto di un client|1.  Creare un File System o un progetto Web IIS locale.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aggiungere un nuovo progetto di client per la soluzione.<br />4.  Se richiesto, accettare controllare della soluzione.<br />5.  Aprire il **Modifica controllo del codice sorgente** la finestra di dialogo.<br />6.  Fare clic su **disassociare**.<br />7.  Fare clic su **OK** per chiudere la finestra di dialogo.<br />8.  Tenta di estrarre soluzioni, progetti, elementi di soluzione, gli elementi di progetto.|Soluzioni e progetti non sono presenti nel controllo del codice sorgente.<br /><br /> Non vengono visualizzati i comandi di menu di controllo di origine.|  
|Annullamento del binding Annulla|1.  Creare un progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aprire il **Modifica controllo del codice sorgente** la finestra di dialogo.<br />4.  Fare clic su **separare tutti**.<br />5.  Fare clic su **Annulla**.|Soluzione è inclusa nel controllo del codice sorgente.|  
  
### <a name="case-5c-rebind"></a>Caso 5C: Rebind  
 Riassociazione è semplicemente una combinazione di separazione e binding, ovvero il processo di riassociazione di una progetto/soluzione che era in precedenza in controllo del codice sorgente e di stato non associato.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Riassociare soluzioni e progetti senza chiudere la **Modifica controllo del codice sorgente** la finestra di dialogo|1.  Creare un progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aprire il **Modifica controllo del codice sorgente** la finestra di dialogo.<br />4.  Fare clic su **disassociare**.<br />5.  Selezionare tutte le righe.<br />6.  Fare clic su **associare**.<br />7.  Fare clic su **OK** per chiudere la **Modifica controllo del codice sorgente** la finestra di dialogo.<br />8.  Se richiesto, accetta l'estrazione.|Soluzioni e progetti sottoposti al controllo del codice sorgente.|  
|Riassociare progetto solo senza chiudere **Modifica controllo del codice sorgente** la finestra di dialogo|1.  Creare un progetto.<br />2.  Aggiungere l'origine controllo utilizzando solo il progetto (File -> origine controllo -> Aggiungi progetti selezionati a controllo del codice sorgente.<br />3.  Aprire la finestra di dialogo Modifica controllo del codice sorgente.<br />4.  Separa solo il progetto.<br />5.  Associare solo il progetto.|Soluzione rimane non controllata.<br /><br /> Progetto rimane controllato.|  
|Riassociare soluzione solo senza chiudere **Modifica controllo del codice sorgente** la finestra di dialogo|1.  Creare un progetto.<br />2.  Aggiungere solo la soluzione al controllo di origine utilizzando (**File**, **controllo del codice sorgente**, **Aggiungi progetti selezionati a controllo del codice sorgente**.<br />3.  Aprire il **Modifica controllo del codice sorgente** la finestra di dialogo.<br />4.  Separare solo la soluzione (non chiudere **Modifica controllo del codice sorgente** la finestra di dialogo.)<br />5.  Associare solo la soluzione.<br />6.  Fare clic su **OK** per chiudere la finestra di dialogo.<br />7.  Estrarre soluzioni e gli elementi di soluzione (se presente.)|Soluzione rimane controllata.<br /><br /> Progetto rimane non controllato.|  
|Riassociare soluzione/progetto solo quando è nella stessa directory|1.  Creare un progetto.<br />2.  Aggiungere solo il progetto al controllo di origine utilizzando (**File**, **controllo del codice sorgente**, **Aggiungi progetti selezionati a controllo del codice sorgente**.<br />3.  Chiudere la soluzione.<br />4.  Creare una nuova soluzione con almeno due progetti.<br />5.  Aggiungere la soluzione al controllo del codice sorgente.<br />6.  Aggiungere il progetto creato nel passaggio 1 dal controllo del codice sorgente.<br />7.  Se richiesto, accettare l'estrazione della soluzione.<br />8.  Controllare nell'intera soluzione.<br />9. Aprire il **Modifica controllo del codice sorgente** la finestra di dialogo.<br />10. Selezionare il progetto aggiunto (dal passaggio 6) e fare clic su **separa**.<br />11. Fare clic su **OK** per chiudere la finestra di dialogo.<br />12. Se richiesto, accettare l'estrazione.<br />13. Riaprire **Modifica controllo del codice sorgente** la finestra di dialogo.<br />14. Selezionare il progetto aggiunto (dal passaggio 6) e fare clic su **associare**.<br />15. Selezionare il percorso originale.|Soluzioni e progetti rimangano controllati.|  
  
## <a name="see-also"></a>Vedere anche  
 [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)