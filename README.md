Graphite Installer
==================

**Note:** Forked from [https://github.com/obfuscurity/synthesize](https://github.com/obfuscurity/synthesize)  I've modified these scripts to suit my particular needs.

To Install on Ubuntu 14.04 LTS:

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
