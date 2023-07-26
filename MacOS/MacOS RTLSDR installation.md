1. #### Download installation scrypt: 
https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-MacOSX-x86_64.sh

2. #### Install:
``` % bash Miniforge3-MacOSX-x86_64.sh ```

3. #### Create environment for GNUradio
```% conda create -n gnuradio```

4. #### Activate created environment
```% conda activate gnuradio```

5. #### Ensure that the environment is set up to look for packages from conda-forge:
```% conda config --env --add channels conda-forge```\
```% conda config --env --set channel_priority strict```

6. #### Install GNU Radio
```% conda install gnuradio```

* install specific version\
  ```% conda search gnuradio``` <- list available versions\
  ```% conda install gnuradio=3.8.2```
* install specific version of Python\
  ```% conda install gnuradio python=3.8```
* upgrade packages in your environment to their latest available versions\
  ```% conda upgrade --all```

7. #### Installing related software
```% conda install rtl-sdr```\
```% conda install soapysdr-module-hackrf```\
```% conda install gnuradio-osmosdr```\
```% conda install -conda-forge \soapysdr-module-rtlsdr``` <- external source

8. #### Running GNU Radio
```% conda activate gnuradio``` <- to activate environment (if not done)\
```% gnuradio-companion``` <- give full rights to ~/.cache folder

---

Steps caan be done in ANACONDA.NAVIGATOR - add https://conda.anaconda.org/conda-forge/ channel.

