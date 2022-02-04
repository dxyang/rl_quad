# rl_quad
Python environment setup including stable baselines, pytorch, and the pybullet drone gym environment

## setup
Install [pyenv](https://github.com/pyenv/pyenv-installer) and [poetry](https://python-poetry.org/docs/) for python version management as well as python dependency management, respectively.


Use git submodules to get the [gym-pybullet-drones](https://github.com/utiasDSL/gym-pybullet-drones) package
```
git submodule init
git submodule update
```

Use poetry to install and manage the remaining dependencies
```
poetry shell
poetry run pip install --upgrade pip
poetry install
```

Update pytorch if your CUDA version is newer than what's by default (CUDA 10.2) in pypi. For example, if you have CUDA 11.3 on your machine you would run
```
poetry run pip3 install torch==1.10.2+cu113 torchvision==0.11.3+cu113 torchaudio==0.10.2+cu113 -f https://download.pytorch.org/whl/cu113/torch_stable.html
```

## basic agent training
`gym-pybullet-drones/experiments/learning/singleagent.py` is the script you want to run. Adjust action space and environment.