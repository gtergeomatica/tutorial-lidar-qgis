Cos'è la tecnologia LIDAR
===========================


Definizione
-------------------------------------------------------

Il LIDAR è una tecnologia attiva di *remote sensing* che consente di che permette di determinare la distanza di un oggetto o di una superficie utilizzando un impulso laser. 
E' definita una tecnologia *attiva* in quanto, a differenza di altre tecnologie di telerilevamento passive che sfruttano l'energia emessa dal sole (es. sensori ottici) emette una certa energia, sotto forma di un raggio laser, per rtilevare la forma di oggetti. Nella fattispecie il lidar a differenza di tencologie simili quale il radar o il sonar usa poca energia (da qui il termine *light* enettendo un laser con lunghezze d'onda ultraviolette, nel visibile o nel vicino infrarosso.


In rete si può trovare molto materiale sulla tecnologia LIDAR su sul sisto 'neon science_' (NEON: National Ecological Observatory Network). A titolo di esempio questo questo video vale molto più di mille parole per comprendere cosa sia il lidar, come funzioni e quali sono le principali applicazioni:

.. raw:: html

    <div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; max-width: 100%; height: auto;">
        <iframe src="https://youtu.be/m7SXoFv6Sdc?cc_load_policy=1&cc_lang_pref=en" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"></iframe>
    </div>
    
"""""""""""""""""""""""""""""""""""""""""""""""

Come funziona il lidar?
-----------------------------------------------------
Di fatto il lidar misura il tempo con cui un'onda emessa ritorna alla sorgente dopo essere stata riflessa e, sulla base di questo tempo è in grado di misurare la distanza.


.. image: img/LIDAR-scanned-SICK-LMS-animation.gif

Fonte: Mike1024_ via Wikimedia Commons

.. _Mike1024: https://commons.wikimedia.org/wiki/File:LIDAR-scanned-SICK-LMS-animation.gif


Grazie all'uso combinato con GPS e IMU è in grado di convertire una misura della distanza con la quota di un oggetto sul terreno.


In realtà  l'impulso emesso dal laser genera più di una risposta nel tempo, meglio dedinita con il termine inglese *pulse* o impulso. Graficando il tempo impiegato da ciascun fascio emesso per tornare al sensore e l'energia si possono individuare diversi picchi (definiti appunto *pulse*) che permettono di individuare al meglio la forma degli oggetti presenti sul terreno.

A titolo di esempio, usando i dati LIDAR grezzi si possono ricavare i seguenti indici: 

* Canopy Height
* Canopy Cover
* Leaf Area Index
* Vertical Forest Structure
* fino ad arrivare addirittura all'identificazione delle singole specie, anche se solo in foreste poco dense e disponendo di un'alta densità di punti

Spesso i dati LIDAR vengono restituiti sulla base di prodotti topografici comunemente noti come il DTM ottenuto dall'ultimo impulso e il DSM ottenuto invece con il primo impulso ricevuto.






An example lidar waveform. Source: NEON, Boulder, CO.



.. _neon science: https://www.neonscience.org/



Come ottenere i dati LIDAR
--------------------------------------------------------







Dal processamento dei dati LIDAR ai GIS: applicazioni
-------------------------------------------------------





Calcolo del CHM
-------------------------------------------------------












