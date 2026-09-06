# Lip-Reading-DeepLearning
Automated Visual Speech Recognition using Spatiotemporal Neural Networks

Questo repository contiene il progetto finale per il corso universitario di Deep Learning Foundations and Basic Algorithms. L'obiettivo è lo sviluppo e l'addestramento e il confronto di reti neurali in grado di effettuare il *lip-reading*. Il modello analizza sequenze di frame video ritagliati sulla regione della bocca per prevedere la parola pronunciata.

In questo repository puoi trovare:
* **'crop_lips_5.ipynb'**, lo script python per estrarre unicamente la regione di interesse individuando le coordinate delle labbra, standardizzare il dataset portando tutti i video ad una risoluzione fissa di 256x128 pixel e una lunghezza fissa di 90 frame e, infine, per ricostruire i file '.mp4' da rinominare con la parola effettivamente pronunciata.
* **'shape_predictor_68_face_landmarks.dat'**, i pesi pre-addestrati richiesti per l'elaborazione dei video grezzi 
* **`deep_project.html`**: Il notebook originale esportato in HTML, contenente tutto il codice, le fasi di esplorazione dati (EDA), l'architettura della rete e l'addestramento del modello.
* **`lip_reading_presentation.pdf`**: Le slide utilizzate per la discussione del progetto, con la sintesi visiva dei risultati di business e tecnici.

## 🛠️ Architettura e Tecnologie
* **Linguaggio/Framework:** Python, TensorFlow/Keras
* **Pre-processing:** Estrazione della Region of Interest (ROI) attorno alle labbra tramite script in Python, normalizzazione dei frame, zero-padding (portando le sequenze a una lunghezza fissa di 90 frame) e generazione di binary mask per uniformare la lunghezza delle sequenze video.
* **Architettura Modello:** Rete ibrida Spaziotemporale basata su Transfer Learning. Utilizza la rete **MobileNetV2** pre-addestrata su ImageNet seguita da layer **LSTM (Long Short-Term Memory)** per catturare la sequenza temporale del movimento delle labbra.

## 📈 Risultati Principali
* Addestramento completato su un dataset esteso tramite una campagna di data acquisition a **1439 video** distribuiti su **76 classi** di parole (partendo da una base iniziale di 650 video).
* **Accuratezza / Metriche:** Il modello finale ha raggiunto un'**Accuracy di Validazione del 30.00%**, con una **Training Accuracy di circa l'80%**, in uno scenario *Closed Set* (Subject Dependent). Si tratta di un risultato molto promettente considerando la piccola dimensione del dataset per l'addestramento e il numero elevato di classi.
* **Generalizzazione e Analisi degli Errori:** Il modello ha dimostrato ottime capacità di apprendere le dinamiche labiali su soggetti noti. Tramite l'analisi **Grad-CAM**, si è osservato che in scenari *Open Set* (soggetti non visti durante l'addestramento) il modello incontra difficoltà di generalizzazione (fenomeno del "Subject Gap"), tendendo a focalizzarsi su feature somatiche statiche (come mento o barba) piuttosto che sul solo movimento. Questo apre la strada a sviluppi futuri basati su dataset ancora più estesi e reti 3D-CNN.
