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


# CLI

<details><summary>Click to expand..</summary>

# venv
- https://docs.astral.sh/uv/reference/cli/#uv-venv


| **Category**         | **Description**                                                                                                                                                                                                                                           |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Purpose**           | Create a virtual environment. By default, creates a `.venv` in the working directory.                                                                                                                            |
| **Usage**             | `uv venv [OPTIONS] [PATH]`                                                                                                                                                                                                                              |
| **Arguments**         | **PATH**: The path to the virtual environment to create. Defaults to `.venv` in the working directory. Relative paths are resolved relative to the working directory.                                              |
| **Options**           |                                                                                                                                                                                                                                                          |
| `--allow-existing`    | Preserve any existing files or directories at the target path.                                                                                                                                                                                           |
| `--allow-insecure-host` | Allow insecure connections to a host. Expects hostname, host-port pair, or URL. (Use cautiously!)                                                                                                                                                      |
| `--cache-dir`         | Specify the cache directory. Defaults to `$XDG_CACHE_HOME/uv` or `%LOCALAPPDATA%\uv\cache`.                                                                                                                       |
| `--color`             | Control color output. Options: `auto`, `always`, `never`.                                                                                                                                                                                                |
| `--config-file`       | Path to a `uv.toml` configuration file.                                                                                                                                                                                                                  |
| `--default-index`     | URL of the default package index (e.g., `<https://pypi.org/simple>`).                                                                                                                                                                                     |
| `--directory`         | Change the working directory before running the command.                                                                                                                                                                                                 |
| `--exclude-newer`     | Limit packages to those uploaded before a specific date.                                                                                                                                                                                                 |
| `--extra-index-url`   | (Deprecated) Additional URLs of package indexes.                                                                                                                                                                                                         |
| `--find-links`, `-f`  | Specify locations to search for candidate distributions.                                                                                                                                                                                                 |
| `--help`, `-h`        | Display concise help for this command.                                                                                                                                                                                                                   |
| `--index`             | Specify additional URLs for dependency resolution.                                                                                                                                                                                                       |
| `--index-strategy`    | Strategy for resolving multiple indexes. Options: `first-index`, `unsafe-first-match`, `unsafe-best-match`.                                                                                                                                               |
| `--index-url`, `-i`   | (Deprecated) URL of the Python package index (default: `<https://pypi.org/simple>`).                                                                                                                                                                     |
| `--keyring-provider`  | Use keyring for authentication. Options: `disabled`, `subprocess`.                                                                                                                                                                                        |
| `--link-mode`         | Specify the method for installing packages. Options: `clone`, `copy`, `hardlink`, `symlink`.                                                                                                                                                             |
| `--native-tls`        | Use platform’s native certificate store instead of Mozilla’s webpki-roots.                                                                                                                                                                               |
| `--no-cache`, `-n`    | Avoid using the cache.                                                                                                                                                                                                                                   |
| `--no-config`         | Avoid discovering configuration files (`pyproject.toml`, `uv.toml`).                                                                                                                                                                                     |
| `--no-index`          | Ignore the registry index and rely on direct dependencies.                                                                                                                                                                                               |
| `--no-progress`       | Hide all progress outputs.                                                                                                                                                                                                                               |
| `--no-project`        | Avoid discovering a project or workspace.                                                                                                                                                                                                                |
| `--no-python-downloads` | Disable automatic Python downloads.                                                                                                                                                                                                                    |
| `--offline`           | Disable network access and rely only on cached data.                                                                                                                                                                                                     |
| `--project`           | Run the command within a specified project directory.                                                                                                                                                                                                    |
| `--prompt`            | Provide a custom prompt prefix for the virtual environment.                                                                                                                                                                                              |
| `--python`, `-p`      | Specify the Python interpreter to use for the virtual environment.                                                                                                                                                                                       |
| `--python-preference` | Prefer `uv`-managed or system Python installations. Options: `only-managed`, `managed`, `system`, `only-system`.                                                                                                                                          |
| `--quiet`, `-q`       | Suppress all output.                                                                                                                                                                                                                                     |
| `--relocatable`       | Make the virtual environment relocatable.                                                                                                                                                                                                                |
| `--seed`              | Install seed packages (`pip`, `setuptools`, `wheel`).                                                                                                                                                                                                    |
| `--system-site-packages` | Grant access to the system site packages directory.                                                                                                                                                                                                    |
| `--verbose`, `-v`     | Enable verbose output.                                                                                                                                                                                                                                   |
| `--version`, `-V`     | Display the version of `uv`.                                                                                                                                                                                                                             |



</details>











<br><br>
<br><br>
___
<br><br>
<br><br>

# Files

## **`.python-version`**
- **Description**: Specifies the project's default Python version.
- **Purpose**: Tells `uv` which Python version to use when creating the virtual environment for the project.
- **Usage**:
  - Ensure this file matches your project's required Python version.
  - Example content: `3.12.7`

---

## **`.venv`**
- **Description**: The directory containing your project's **virtual environment**.
- **Purpose**: Provides an isolated Python environment where dependencies are installed, separate from the system's Python installation.
- **Key Points**:
  - Automatically created by `uv` when setting up the project.
  - Keeps the project environment clean and independent.
- **Related Docs**: Refer to the [project environment documentation](https://docs.astral.sh/uv/getting-started/first-steps/) for details.

---

## **`uv.lock`**
- **Description**: A cross-platform lockfile that records the exact versions of all resolved dependencies in your project.
- **Purpose**:
  - Ensures **consistent and reproducible installations** across different machines.
  - Works alongside `pyproject.toml`, which defines broader dependency requirements.
- **Key Notes**:
  - This file should **always be committed to version control**.
  - It locks dependency versions for stability during deployment and collaboration.
- **Comparison with `pyproject.toml`**:
  - `pyproject.toml`: Broad requirements (e.g., `transformers>=4.37.0`).
  - `uv.lock`: Exact resolved versions (e.g., `transformers==4.37.2`).

---

### Workflow with `uv`
1. **Initialize Project**:
   ```bash
   uv init
   ```
   Creates `pyproject.toml` and sets up the project structure.

2. **Add Dependencies**:
   ```bash
   uv add <package-name>==<version>
   ```

3. **Synchronize Environment**:
   ```bash
   uv sync
   ```
   Installs dependencies and updates the `.venv` environment based on `pyproject.toml` and `uv.lock`.

4. **List Installed Packages**:
   ```bash
   uv pip list
   ```

5. **Update Lockfile**:
   ```bash
   uv lock
   ```
   Regenerates the `uv.lock` file after making changes to `pyproject.toml`.

---

### Best Practices
- Always keep `.python-version`, `.venv`, and `uv.lock` in sync with your project requirements.
- Commit `uv.lock` to version control for reproducibility.
- Use `uv sync` to ensure dependencies match the lockfile.

---




















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


## **Python Versions**
Manage Python versions directly with `uv`.

### Commands:
- `uv python install <version>`: Install a specific Python version.
- `uv python list`: List available Python versions.
- `uv python find <version>`: Locate an installed Python version.
- `uv python pin <version>`: Pin the project to a specific Python version.
- `uv python uninstall <version>`: Uninstall a Python version.

**Reference**: [Guide on Installing Python](https://docs.astral.sh/uv/getting-started/first-steps/)











<br><br>
<br><br>
___
<br><br>
<br><br>

# **Scripts**
Run and manage standalone Python scripts.

### Commands:
- `uv run <script.py>`: Execute a Python script.
- `uv add --script <dependency>`: Add a dependency to a script.
- `uv remove --script <dependency>`: Remove a dependency from a script.

**Reference**: [Guide on Running Scripts](https://docs.astral.sh/uv/getting-started/first-steps/)























<br><br>
<br><br>
___
<br><br>
<br><br>

# Projects
- Work with Python projects (using `pyproject.toml`).

### Commands:
- `uv init`: Initialize a new Python project.
- `uv add <dependency>`: Add a dependency to the project.
- `uv remove <dependency>`: Remove a dependency from the project.
- `uv sync`: Sync project dependencies with the environment.
- `uv lock`: Generate a lockfile for project dependencies.
- `uv run <command>`: Execute a command in the project environment.
- `uv tree`: View the dependency tree of the project.
- `uv build`: Build the project into distributable archives.
- `uv publish`: Publish the project to a package index.




<br><br>


## Dependency

<br><br>




## Uninstall

<br><br>

### Directly deleted from virtuel environment
```shell
uv pip uninstall transformers
```

### Delete from pyproject.toml
```shell
uv remove transformers
```






<br><br>
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




























<br><br>
<br><br>
___
<br><br>
<br><br>



## **Tools**
Run and manage Python tools (e.g., `ruff`, `black`).

### Commands:
- `uvx <tool> <args>`: Run a tool in a temporary environment.
- `uv tool install <tool>`: Install a tool globally.
- `uv tool uninstall <tool>`: Uninstall a tool.
- `uv tool list`: List installed tools.
- `uv tool update-shell`: Update the shell to include tool executables.

**Reference**: [Guide on Tools](https://docs.astral.sh/uv/getting-started/first-steps/)















<br><br>
<br><br>
___
<br><br>
<br><br>


## **Pip Interface**
Directly manage environments and packages when finer control is required.

### Environment Management:
- `uv venv <path>`: Create a virtual environment.

**Reference**: [Using Environments](https://docs.astral.sh/uv/getting-started/first-steps/)

### Package Management (like `pip`):
- `uv pip install <package>`: Install a package.
- `uv pip show <package>`: Show package details.
- `uv pip freeze`: List installed packages and versions.
- `uv pip check`: Verify package compatibility in the environment.
- `uv pip list`: List installed packages.
- `uv pip uninstall <package>`: Uninstall a package.
- `uv pip tree`: View the environment's dependency tree.

**Reference**: [Managing Packages](https://docs.astral.sh/uv/getting-started/first-steps/)

### Lockfile Management:
- `uv pip compile`: Generate a lockfile from dependencies.
- `uv pip sync`: Synchronize the environment with a lockfile.

**Reference**: [Locking Environments](https://docs.astral.sh/uv/getting-started/first-steps/)













<br><br>
<br><br>
___
<br><br>
<br><br>


## **6. Utility Commands**
Manage `uv`'s internal state and directories.

### Commands:
- `uv cache clean`: Remove all cache entries.
- `uv cache prune`: Remove outdated cache entries.
- `uv cache dir`: Show the cache directory path.
- `uv tool dir`: Show the tools directory path.
- `uv python dir`: Show the directory for installed Python versions.
- `uv self update`: Update `uv` to the latest version.

