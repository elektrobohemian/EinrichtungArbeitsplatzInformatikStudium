```
sudo apt-get update
sudo apt-get upgrade
sudo reboot
```

Python-Vorbereitung
```
sudo apt install python3-pip
sudo apt install -y python3-venv
```

ich lege mir unter home immer ein verzeichnis src an, um dort meinen code zu speichern
```
python3 -m venv ~/src/primer/env
source ~/src/primer/env/bin/activate
```

für fish-shell: activate.fish

in der environment
```
pip3 install wheel
```

jupyter - davor musste ich noch 

```
sudo apt-get install libffi-dev
```

````
pip3 install jupyter
````
```
jupyter notebook
```

auf anderem terminal (pc)
```
ssh -L 8000:localhost:8888 david@david-jetson-nano
```
man kann dann mittels `http://localhost:8888/?token=c8bd088f301426a2975290317bbce92af86d3190557f9e05`auf den Jetson zugreifen, den Token bekommt man aus der Startmeldung von Jupyter auf dem Jetson

## PyTorch

außerhalb der Environment

```
sudo apt-get install python3-pip libopenblas-base libopenmpi-dev

sudo apt install libjpeg-dev libfreetype6-dev pkg-config libpng-dev

```

Wheel für Jetson bestimmen:
```
https://forums.developer.nvidia.com/t/pytorch-for-jetson-version-1-7-0-now-available/72048
```
 bei mir:
 ```
wget https://nvidia.box.com/shared/static/cs3xn3td6sfgtene6jdvsxlr366m2dhq.whl -O torch-1.7.0-cp36-cp36m-linux_aarch64.whl
```

dann
```
pip3 install Cython

pip3 install numpy torch-1.7.0-cp36-cp36m-linux_aarch64.whl

pip3 install matplotlib pillow
```

### Torchvision

Version in Git beachten (zumindest um den Jahreswechsel 2021 herum): https://github.com/pytorch/vision/issues/3175


```
cd ~/src/primer/env/lib/python3.6/site-packages/
git clone https://github.com/pytorch/vision.git -b v0.8.2
cd vision
source ~/src/primer/env/bin/activate
python3 setup.py install
python3 setup.py clean
```

Pfad für Torchvision ist dann: `/home/david/src/primer/env/lib/python3.6/site-packages/vision`

Daten vorbereiten
```
cd ~/src/primer
wget https://raw.githubusercontent.com/anishathalye/imagenet-simple-labels/master/imagenet-simple-labels.json

wget https://miro.medium.com/max/376/1*XAdixBBKix2Yda8HtS0P8Q.png -O dog.png
```


