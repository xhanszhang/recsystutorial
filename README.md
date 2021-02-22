
## Installation (First Session)
1. If you do not have conda, first step is to install [Anaconda](https://docs.continuum.io/anaconda/install/) to your system. Follow this link to install Anaconda with Python >= 3.6:
```
https://docs.continuum.io/anaconda/install/
```

2. For windows, open Anaconda Navigator through `run as administrator`, and open `CMD.exe Prompt`; For Mac/Linux, open your terminal application.

3. Activate the `reco_base` environment and install surprise
```bash
conda create --name reco_base
conda activate reco_base
conda install -c conda-forge scikit-surprise
```

4. Verify that it is working. Run `python` and import the `surprise` library
```bash
$ python
Python 3.9.2 | packaged by conda-forge | (default)
>>> from surprise import Dataset
>>> exit()
```

5. Change directory to where you downloaded this tutorial, and run jupyter notebook
```bash
$ jupyter notebook
```

## Installation (Second Session)
These steps are only needed for the second session, however, it is highly recommended to follow these steps and install the libraries as early as possible. The installation process can take 20 minutes to finish.

1. Press `Ctrl-C` to exit the previous notebook session.

2. Clone the MS recommender repository
```bash
$ git clone https://github.com/Microsoft/Recommenders
```

3. Run the generate conda file script to create a conda environment and install the library. **NOTE** This process will take a long time (~ 20 minutes)

```bash
cd Recommenders
python tools/generate_conda_file.py
conda env update -f reco_base.yaml
```

If there are errors in the env creation step, and you've fixed it. You can rerun the following commands
```bash
conda activate reco_base
conda env update -f reco_base.yaml
```

4. If you somehow exit the `reco_base` environment, activate it again by 
```bash
conda activate reco_base```

Otherwise, install the library and register it with Jupyter

```bash
pip install .
python -m ipykernel install --user --name reco_base --display-name "Python (reco)"
```

5. Start the Jupyter notebook server, and make sure to change the kernel to "Python (reco)".

```bash
jupyter notebook
```

### Trouble Shooting

#### xlearn and cmake
The `xlearn` package has dependency on `cmake`. If one uses the `xlearn` related notebooks or scripts, make sure `cmake` is installed in the system. The easiest way to install on Linux is with apt-get: `sudo apt-get install -y build-essential cmake`. Detailed instructions for installing `cmake` from source can be found [here](https://cmake.org/install/).

On Mac OS X, you can install using

```brew install cmake```

or

```sudo port install cmake```. 
    
See https://xlearn-doc.readthedocs.io/en/latest/install/index.html for details.
    
#### Error: Can not find Rust compiler
Download Rust compiler.

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env
```
    
See https://github.com/huggingface/transformers/issues/2831 for details.

#### Install Java 8 on MacOS
  
To install Java 8 on MacOS using [asdf](https://github.com/halcyon/asdf-java):

    brew install asdf
    asdf plugin add Java
    asdf install java adoptopenjdk-8.0.265+1
    asdf global java adoptopenjdk-8.0.265+1
    . ~/.asdf/plugins/java/set-java-home.zsh



