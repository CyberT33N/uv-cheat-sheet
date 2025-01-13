# uv-cheat-sheet



# Install
- https://docs.astral.sh/uv/getting-started/installation/
  
<br><br>

## Ubuntu
```shell
curl -LsSf https://astral.sh/uv/install.sh | sh
```



<br><br>
<br><br>
___
<br><br>
<br><br>

# Environment

<br><br>

## Create environment
```shell
# (Recommended) Create a new uv environment. Use `--seed` to install `pip` and `setuptools` in the environment.
uv venv myenv --python 3.12 --seed
source myenv/bin/activate
```

<br><br>

## Activate environment
```shell
source myenv/bin/activate
```

<br><br>









<br><br>
<br><br>
___
<br><br>
<br><br>

# Dependency

<br><br>

## Install

<details><summary>Click to expand..</summary>

Der Unterschied zwischen **`uv pip install`** und **`uv add`** liegt in ihrer Funktion und wie sie mit deinem Projekt interagieren. Hier eine Erklärung:

---

### **1. `uv pip install`**
- Führt einen **direkten Installationsbefehl** aus, ähnlich wie `pip install`.
- Es installiert ein Paket sofort in deinem aktuellen Environment, ohne dabei die `pyproject.toml` zu aktualisieren.
- Verwendet werden sollte es, wenn du ein Paket schnell testen willst oder keine langfristige Projektbindung benötigst.

#### Beispiel:
```bash
uv pip install transformers==4.37.2
```
- **Ergebnis**: Das Paket wird in deinem Environment installiert, aber **nicht in der `pyproject.toml` erfasst**.

---

### **2. `uv add`**
- Fügt das Paket **dauerhaft** als Dependency in dein Projekt ein.
- Es aktualisiert die `pyproject.toml` automatisch und stellt sicher, dass die Abhängigkeit beim nächsten `uv sync` oder Deployment berücksichtigt wird.
- Ideal für langfristige Projektarbeit, da es die Dependency in der Projektkonfiguration dokumentiert.

#### Beispiel:
```bash
uv add transformers==4.37.2
```
- **Ergebnis**: Das Paket wird installiert **und in der `pyproject.toml`** unter `[dependencies]` gespeichert.

---

### **Warum `uv pip install` die alte Version zeigt**
Wenn du `uv pip install` benutzt, aktualisiert das Tool nur die Pakete im Python-Environment. Es prüft aber nicht, ob diese Änderung in der `pyproject.toml` oder in den Projekt-Dependencies reflektiert wird. Wenn du später mit **uv** arbeitest (z. B. `uv pip list` oder `uv sync`), könnte es weiterhin alte Versionen anzeigen, da es sich auf die Definitionen in der `pyproject.toml` verlässt.

---

### **Lösung: So synchronisierst du alles**
1. **Verwende `uv add`, um die Dependency korrekt zu setzen:**
   ```bash
   uv add transformers==4.37.2
   ```

2. **Synchronisiere das Environment mit der `pyproject.toml`:**
   ```bash
   uv sync
   ```

3. **Prüfe erneut die installierte Version:**
   ```bash
   uv pip list
   ```

---

### **Fazit: Wann was verwenden?**
- **`uv pip install`**: Für temporäre Tests oder schnelle Installationen.
- **`uv add`**: Für alles, was du in deinem Projekt langfristig nutzen willst.

</details>



<br><br>
<br><br>


## List dependencies
```shell
uv pip list
```
