# vagrant-apt-cacher-ng

A basic `Vagrantfile` to spin up a box with a default [apt-cacher-ng](https://www.unix-ag.uni-kl.de/~bloch/acng/) instance.

## Usage
Spin up the box:

`vagrant up`

Add proxy configuration to your clients:

`echo Acquire::http::Proxy \\"http://10.0.100.30:3142\\"\\; > /etc/apt/apt.conf.d/00aptproxy`

## License
[MIT](https://choosealicense.com/licenses/mit/) 
