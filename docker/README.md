#VIB factory
Docker container to simply create VIBs from your ghettoVCB fork.
At first let me give a great thanks to William Lam for his great work. He made us backing up all of our virtual machines.

Why is there a need of creating own VIBs to install ghettoVCB?

Well, for me the trigger was a missing fix which made it into the repository but not into the VIBs.
But another very interesting use case for customized VIBs could be the deployment with an already right preconfigured ghettoVCB.conf file. 
So I decided to have a look on the VIB creation toolchain. I followed the instructions given by William right here and set up this docker to be able to use different repositorys and version numbers. 
  

##Create the docker container

When inside this directory the given command below will create the docker image.

```
$ docker build -t ghettovcb_vib_creator .
```

##Run the container once to create the VIBs

The command below will run the container once and create the desired VIBs. The VIBs and the polled ghettoVCB repository are stored outside the container in the ``/artifacts`` folder.
 
The optional environment parameters GVCB_REPO, GVCB_REPO_DIR and GVCS_VIB_VERSION, given by -e, can be used to point to a specific own repository and set the version of the created VIBs. There you can have modifications on e.g. ghettoVCB.conf to fit your own needs.

```
$ docker run --rm -it \
  -v ${PWD}/artifacts:/root/artifacts \
  -e GVCB_REPO='https://github.com/lamw/ghettoVCB.git' \
  -e GVCB_REPO_DIR='ghettoVCB' \
  -e GVCB_VIB_VERSION='1.0.0-0.0.0' \
  ghettovcb_vib_creator
```

### Licensing

The MIT License (MIT)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
