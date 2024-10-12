## How to communicate over NomadNet with LoRa radio
I assume you already have your LoRa radio flashed with the right firmware.

* Create two NomadNet configuration folders
```bash
$ mkdir -p $HOME/nomadnet_test/c1
$ mkdir -p $HOME/nomadnet_test/c2
```

* Review each configuration file, specifically `port` and `frequency` parameters
* Copy configuration files to each folder

```bash
$ cp config.radio1 -p $HOME/nomadnet_test/c1
$ cp config.radio2 -p $HOME/nomadnet_test/c2
```

* Call docker to launch the shipped image for NomadNet in mode `textui`, in two separate consoles
```bash
# in first console
$ docker run -it -v $HOME/nomadnet_test/c1/:/root/.reticulum/ --device=/dev/ttyACM0  --network host ghcr.io/markqvist/nomadnet:master --textui

# in other console
$ docker run -it -v $HOME/nomadnet_test/c2/:/root/.reticulum/ --device=/dev/ttyACM1  --network host ghcr.io/markqvist/nomadnet:master --textui
```
As shared instance is disabled, and only one interface is configured, we make sure that the communication is going through the radios. This can be confirmed by a spectrum analyser.
