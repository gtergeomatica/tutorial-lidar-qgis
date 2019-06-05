Cos'è la tecnologia LIDAR
===========================


Definizione
-------------------------------------------------------

Il LIDAR è una tecnologia attiva di *remote sensing* che consente di determinare la distanza di un oggetto o di una superficie utilizzando un impulso 
laser. 

E' definita una tecnologia *attiva* in quanto, a differenza di altre tecnologie di telerilevamento passive che sfruttano l'energia emessa dal sole 
(es. sensori ottici) emette una certa energia, sotto forma di un raggio laser, per rilevare la forma di oggetti. Nella fattispecie il lidar 
a differenza di tencologie simili quale il radar o il sonar usa poca energia (da qui il termine *light* enettendo un laser con lunghezze d'onda 
ultraviolette, nel visibile o nel vicino infrarosso.


In rete si può trovare molto materiale sulla tecnologia LIDAR su sul sisto 'neon science_' (NEON: National Ecological Observatory Network). 
A titolo di esempio questo questo video vale molto più di mille parole per comprendere cosa sia il lidar, come funzioni e 
quali sono le principali applicazioni:

.. raw:: html

	<div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; max-width: 100%; height: auto;">
		<iframe src="https://www.youtube.com/embed/m7SXoFv6Sdc?list=PLiSjSway-kxAcenpAkPwWGy53RVnh3-r3&cc_load_policy=1&cc_lang_pref=en" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"></iframe>
	</div>
	
"""""""""""""""""""""""""""""""""""""""""""""""

Come funziona il lidar?
-----------------------------------------------------
Di fatto il lidar misura il tempo con cui un'onda emessa ritorna alla sorgente dopo essere stata riflessa e, sulla base di questo tempo è in grado di misurare la distanza.


.. image:: img/LIDAR-scanned-SICK-LMS-animation.gif

Fonte: Mike1024_ via Wikimedia Commons

.. _Mike1024: https://commons.wikimedia.org/wiki/File:LIDAR-scanned-SICK-LMS-animation.gif


Grazie all'uso combinato con GPS e IMU è in grado di convertire una misura della distanza con la quota di un oggetto sul terreno.


In realtà  l'impulso emesso dal laser genera più di una risposta nel tempo, meglio definita con il termine inglese *pulse* o impulso. Graficando il tempo impiegato da ciascun fascio emesso per tornare al sensore e l'energia si possono individuare diversi picchi (definiti appunto *pulse*) che permettono di individuare al meglio la forma degli oggetti presenti sul terreno.

Un esempio di risposta letta dal sensore lidar è mostrata nella seguente figura:

.. image:: img/waveform.png

Source: NEON, Boulder, CO.

Usando quindi i dati LIDAR grezzi si possono ricavare diversi indici e classificare accuratamente il terreno. A titolo di esempio ecco alcuni indici: 

* Canopy Height
* Canopy Cover
* Leaf Area Index
* Vertical Forest Structure


Si può addirittura arrivare all'identificazione delle singole specie, anche se solo in foreste poco dense e disponendo di un'alta densità di punti



.. _neon science: https://www.neonscience.org/



Dal processamento dei dati LIDAR ai GIS
-------------------------------------------------------

Il risultato *grezzo* di un rilievo LIDAR è una nuvola di punti (dense cloud) che come detto è opportunamente classificabile.


Archiviazione del dato in formato vettoriale (all, xyz, txt, las) o raster (asc, tif)
'''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
 
I prodotti più comuni di un rilievo LIDAR possono però essere dei dati raster (vedi immagine) ossia dati  composti da matrici di celle 
(chiamati anche pixel), ciascuna contenente un valore che rappresenta le condizioni dell’area coperta dalla cella 
(in questo caso l'altezza del terreno).

.. image:: img/raster.png



TODO
Introdurre / spiegare qualcosa dei dati vettoriali in maniera "strana" perchè son tutti dati vettoriali predisposti per ottenere un raster...




Sistemi di riferimento (geografiche o proiettate, classificazione  EPSG)
'''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''

A questo punto è bene fare una breve panoramica dei CRS (Coordinate Reference System) disponibili in ambiente GIS

Infatti, nell’utilizzo dei software GIS la gestione dei Sistemi di coordinate geografici o cartografici, che nel seguito indicheremo
con l’acronimo inglese CRS (Coordinate Reference System), è sempre un aspetto complesso per l’utente. 

I datum geodetici con i quali sono distribuiti i dati geografici nel nostro paese sono infatti almeno 5 (tabella 1) 
e se ad essi si aggiungono le proiezioni cartografiche i CRS diventano più del doppio (tabellla 2). 

TODO

+------------------------+----------------+--------------------------------------------------------------------+ 
|Datum geodetico         |  Codice EPSG   | Note                                                               |
*========================+================+====================================================================+
| **ETRF2000 (RDN 2008)**| 6706           | Realizzazione italiana del sistema globale ETRS89                  |
+------------------------+----------------+--------------------------------------------------------------------+
| ETRF89/ETRS89          | 4258           |                                                                    | 
+------------------------+----------------+--------------------------------------------------------------------+
| ED50                   | 4230           |                                                                    |
+------------------------+----------------+--------------------------------------------------------------------+
| Roma40 Monte Mario     | 4265           | Longitudini espresse rispetto al meridiano di Greenwich            |
+------------------------+----------------+--------------------------------------------------------------------+
| Roma40 Monte Mario     | 4806           | Longitudini espresse rispetto al meridiano Monte Mario             |
+------------------------+----------------+--------------------------------------------------------------------+
|                        |                | Secondo l’IGM non dovrebbe essere utilizzato per la cartografia    |
| WGS84                  | 4326           | ufficiale di fatto è molto usato a livello internazionale per      |
|                        |                | dati che non richiedano elevata precisione                         |
+------------------------+----------------+--------------------------------------------------------------------+

Tabella 1 - Principali sistemi di coordinate geografiche (lat/lon) usati in ambiente GIS in Italia. 
In grassetto quello “ufficiale”


+---------------------------+----------------+-----------------------------------------------------------------+ 
|Datum geodetico            |  Proiezione    | Codice EPSG                                                     |
*===========================+================+=================================================================+
| ETRF 2000 (RDN 2008)      | UTM 32N        | 7791                                                            |
+---------------------------+----------------+-----------------------------------------------------------------+
| ETRF 2000 (RDN 2008)      | UTM 33N        | 7792                                                            |
+---------------------------+----------------+-----------------------------------------------------------------+
| ETRF 2000 (RDN 2008)      | UTM 34N        | 7793                                                            |
+---------------------------+----------------+-----------------------------------------------------------------+
| ETRF 2000 (RDN 2008)      | Fuso italia1   | 7794                                                            |
+---------------------------+----------------+-----------------------------------------------------------------+
| ETRF 2000 (RDN 2008)      | Zona 12        | 7795                                                            |
+---------------------------+----------------+-----------------------------------------------------------------+
| ETRF89/ETRS89             | UTM 32N        | 25832                                                           |
+---------------------------+----------------+-----------------------------------------------------------------+
| ETRF89/ETRS89             | UTM 33N        | 25833                                                           |
+---------------------------+----------------+-----------------------------------------------------------------+
| ETRF89/ETRS89             | UTM 34N        | 25834                                                           |
+---------------------------+----------------+-----------------------------------------------------------------+
| ED50                      | UTM 32N        | 23032                                                           |
+---------------------------+----------------+-----------------------------------------------------------------+
| ED50                      | UTM 33N        | 23033                                                           |
+---------------------------+----------------+-----------------------------------------------------------------+
| ED50                      | UTM 34N        | 23034                                                           |
+---------------------------+----------------+-----------------------------------------------------------------+
| Roma40 Monte Mario (4265) | Fuso Ovest     | 3003                                                            |
+---------------------------+----------------+-----------------------------------------------------------------+
| Roma40 Monte Mario (4265) | Fuso Est       | 3004                                                            |
+---------------------------+----------------+-----------------------------------------------------------------+
| WGS84                     | UTM 32N        | 32632                                                           |
+---------------------------+----------------+-----------------------------------------------------------------+
| WGS84                     | UTM 33N        | 32633                                                           |
+---------------------------+----------------+-----------------------------------------------------------------+
| WGS84                     | UTM 34N        | 32634                                                           |
+---------------------------+----------------+-----------------------------------------------------------------+

Tabella2 –  Principali sistemi di coordinate cartografiche (est/nord) usati in ambiente GIS in Italia.


Grid table:

+------------+------------+-----------+ 
| Header 1   | Header 2   | Header 3  | 
+============+============+===========+ 
| body row 1 | column 2   | column 3  | 
+------------+------------+-----------+ 
| body row 2 | Cells may span columns.| 
+------------+------------+-----------+ 
| body row 3 | Cells may  | - Cells   | 
+------------+ span rows. | - contain | 
| body row 4 |            | - blocks. | 
+------------+------------+-----------+

 
 
 

Elaborazione dei dati – DSM, DTM – Ground,  OverGround -  First Point, Last Point
'''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''

In sostanza, spesso i dati LIDAR vengono restituiti sulla base di prodotti topografici comunemente noti come:
 
* il DSM ottenuto invece con il primo impulso ricevuto (DSMFirst) e in taluni casi quello ottenuto con l'ultimo impulso.
* il DTM ottenuto dall'ultimo impulso che raggiunge il terreno nudo. 

Sono questi prodotti facilmente consultabili con qualunque software GIS. 


A titolo di esempio ecco una tile del DSM (DSMFirst) di Regione Veneto nei pressi di Cortina d'Ampezzo:

.. image:: img/dsm_tile.png

Ed l'analoga tile con il DTM:

.. image:: img/dsm_tile.png



In questa GIF animata è rappresentato sinteticamente il processamento dei dati LIDAR che consente di ottenere prodotti raster a risoluzioni differenti.

.. image:: img/gridding.gif



Calcolo del CHM in ambiente GIS
-------------------------------------------------------

A partire da dati raster GIS come il DTM e il DSM può essere nuovamente ricavato il CHM come risultato 
della sottrazione fra DSM e DTM.

.. image:: img/lidarTree-height.png




Note sul calcolo del CHM
-------------------------------------------------------
Il CHM così calcolato ovviamente include tutti gli elementi presenti sul terreno incluso ovviamente l'edificato. 


A tal proposito in alcuni casi viene fornito sia il DSMFirst che il DSMLast le cui differenze sono pressochè nulle in corrispondenza dell'edificato,
più consistenti in corrispondenza di vegetazione.

A titolo di esempio si riportano 2 diversi profili realizzati confrontando DSMFirst, DSMLast e DTM per una tile sul centro di Vicenza (Regione Veneto)

* il primo caso è stato realizzato in centro, nei pressi del palazzo comunale e della famosa basilica Palladiana (Link OpenStreetMap: https://osm.org/go/0IBaN62IU--?m=)

.. image:: img/cfr_edifici.png

* il secondo caso è stato realizzato nei pressi della stazione confrontando un area a parco urbano con gli edifici della stazione ferroviaria (Link OpenStreetMap:https://osm.org/go/0IBaM4VaZ--?m=)

.. image:: img/cfr_alberi_stazione.png

Si può notare come:

* la differenza tra DSM e DTM includa ovviamente sia l'edificato che la vegetazione e quindi vada usata con cautela per applicazioni forestali
* la disponibilità di altri prodotti (es. DSMLast e DSMFirst) possa in qualche modo aiutare l'utente ell'analisi e classificazione dei prodotti ottenuti



