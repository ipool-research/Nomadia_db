# 📂 Database georeferenziato

Questo repository include un **database SQLite (`Database_Nomadia.db`)**, che contiene i metadati relativi alle immagini e ai rispettivi file di etichette. Il database è strutturato per fornire un accesso rapido ai dati relativi alle immagini.

## 🔹 Struttura del Database
- Il database contiene una tabella chiave in cui ogni riga corrisponde a un'immagine e al suo file di etichette associato.
- Il campo **`Name`** nel database è l'identificatore univoco per ogni immagine. Corrisponde a:
  - Il **nome del file immagine** memorizzato in un'unità cloud esterna.
  - Il **nome del file delle etichette** (senza estensione) presente nella stessa unità.
- I campi **`Longitude`**, **`Latitude`**, **`Altitude`** identificano le coordinate geografiche corrispondenti all'immagine.
- I campi successivi rappresentano il numero di occorrenze nell'immagine delle varie categorie di ammaloramenti classificate dal modello:
  - **`Longitudinal`**
  - **`Transverse`**
  - **`Alligator`**
  - **`Pothole`**
  - **`Repair`**
  - **`Manhole`**

## 🌍 Accesso ai File di Immagini ed Etichette
- Poiché le immagini e i file di etichette sono memorizzati esternamente, è possibile scaricarli dal seguente **link di archiviazione cloud**:
  
  🔗 [Link al Drive con Immagini e Labels](https://ipoolsrl-my.sharepoint.com/:f:/g/personal/ipool_ipoolsrl_onmicrosoft_com/Et9-T43Q9wdMmYar3HdepBoBtfXzYF4Liwcsn4uJGmQwBw?e=qv6wV7)
  
- I nomi dei file nel database corrispondono esattamente a quelli presenti nell'unità, facilitando la mappatura dei record.

## 🛠 Come Aprire il Database
Puoi esplorare il database utilizzando **DBeaver, SQLite Browser o Python**.

### Utilizzo di DBeaver
1. Apri **DBeaver** e fai clic su **"Database" > "Nuova Connessione"**.
2. Seleziona **SQLite** e fornisci il percorso a `database.db`.
3. Clicca su **"Finish"** ed esegui query come:
   ```sql
   SELECT * FROM table_name;
   ```

### Utilizzo della CLI di SQLite
1. Installa SQLite se non è già installato.
2. Apri un terminale e naviga nella cartella del repository.
3. Esegui:
   ```sh
   sqlite3 database.db
   ```
4. All'interno della shell SQLite, utilizza:
   ```sql
   .tables  -- Elenca tutte le tabelle
   SELECT * FROM table_name LIMIT 10;  -- Visualizza un esempio di dati
   ```

### Utilizzo di Python
```python
import sqlite3
import pandas as pd

# Connessione al database
conn = sqlite3.connect("database.db")

# Lettura dei dati in un DataFrame
df = pd.read_sql("SELECT * FROM table_name", conn)

# Visualizzazione dei dati
print(df.head())

# Chiusura della connessione
conn.close()
```

---
