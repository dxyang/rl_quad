# rl_quad
Python environment setup including stable baselines, pytorch, and the pybullet drone gym environment

## setup
Install [pyenv](https://github.com/pyenv/pyenv-installer) and [poetry](https://python-poetry.org/docs/) for python version management as well as python dependency management, respectively. Would highly rec these tools for simplicity, ease of use, and speed compared to similar tools out there trying to solve similar problems.


Use git submodules to get the [gym-pybullet-drones](https://github.com/utiasDSL/gym-pybullet-drones) package
```
git submodule init
git submodule update
```

Use poetry to install and manage the remaining dependencies. Note that there may be package version incompatibilties on a Mac (and even more likely so with ARM M1 vs Intel x86). Would highly recommend just sticking to Ubuntu for this.
```
poetry shell
poetry run pip install --upgrade pip
poetry install
```

This `pyproject.toml` will install the default version of pytorch that is in pypi (currently CUDA 10.2) However, there may be a CUDA version mismatch if you have something newer on your machine. Update pytorch as necessary. For example, if you have CUDA 11.3 on your machine you would run
```
poetry run pip install torch==1.10.2+cu113 torchvision==0.11.3+cu113 torchaudio==0.10.2+cu113 -f https://download.pytorch.org/whl/cu113/torch_stable.html
```

## basic agent training
`gym-pybullet-drones/experiments/learning/singleagent.py` is the script you want to run. Adjust action space and environment.

There's a bug in the master of their code. On [line 261 of singleagent.py](https://github.com/utiasDSL/gym-pybullet-drones/blob/7fbd5833cad7c45eeae1d1b955da10208d2d18ee/experiments/learning/singleagent.py#L261), you need to delete one of the `[0]` in the print statement. This doesn't affect any training logic but will just make the script exit gracefully. 