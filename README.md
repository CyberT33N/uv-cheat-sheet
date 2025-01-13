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

## Install dependency
```shell
uv pip install autoawq
```

<br><br>

## List dependencies
```shell
uv pip list
```
