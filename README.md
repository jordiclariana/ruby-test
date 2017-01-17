## How to

* Clone this repo:

`git clone https://github.com/jordiclariana/ruby-test.git`

* Change to downloaded repo dir:

`cd ruby-test`

* Start Vagrant machine:

`vagrant up`

* Login into Vagrant machine:

`vagrant ssh`

* Try to run test program:

`cd /vagrant` # Your repo, inside the Vagrant machine, is hosted in `/vagrant` directory

`ruby test.rb`


Any change you do inside `/vagrant` will affect the real directory (the downloaded repo), so if you create a file like `/vagrant/myfile` and then you run `exit` in your Vagrant console, you'll see a `myfile` in your repo root

