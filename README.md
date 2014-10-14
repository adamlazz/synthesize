Graphite Installer
==================

**Note:** Forked from [https://github.com/obfuscurity/synthesize](https://github.com/obfuscurity/synthesize)  I've modified these scripts to suit my particular needs.

###To install Graphite Carbon, Graphite-API and Whisper on Ubuntu 14.04 LTS:

```
$ sudo apt-get update
$ sudo apt-get install git-core -y
$ git clone https://github.com/chadlung/synthesize.git
$ cd synthesize
$ chmod +x install
$ sudo ./install
```

Once the daemons are running you can verify its working by entering a metric:

```
$ echo "test.count 12 `date +%s`" | nc -q0 127.0.0.1 2003
```

Verify a **test** folder exists in the following folder:

```
$ ls /opt/graphite/storage/whisper/
```

Using a web browser (adjust the IP as needed):

```
http://192.168.33.13:8888/render?target=test.count&height=300&width=300&from=-5minutes
```

###To install Graphite Carbon-Relay on Ubuntu 14.04 LTS:

**Note:** This should be installed on it's own machine, not the same one as where the **install** script was run.

```
$ sudo apt-get update
$ sudo apt-get install git-core -y
$ git clone https://github.com/chadlung/synthesize.git
$ cd synthesize
$ chmod +x install-carbon-relay
$ sudo ./install-carbon-relay
```

You will need to modify the **carbon.conf** file and ensure the IP destinations are correctly set:

```
DESTINATIONS = 127.0.0.1:2004:1, 127.0.0.1:2006:1
```

Once **carbon.conf** has been updated in the **/opt/graphite/conf** folder and then start the **carbon-relay** service:

```
$ service carbon-relay start
```
