The easiest way to start with the [QDK](https://github.com/Microsoft/Quantum) is via a docker container and Jupyter notebooks. 

Unfortunately this doesn't seem to be possible in Azure Notebooks but we can run the notebooks on local Docker instances.  

This is a simulator, you don't need a quantum computer.  

## Teleportation

Using a Jupyter Notebook we are going to do a sort of "Hello, World" using quantum programming.  


```bash
git clone https://github.com/microsoft/Quantum.git
cd Quantum

# if the build fails, remove the powershell entry from the Dockerfile
docker build -t iqsharp .
docker run -it \
    --name iqsharp-container \
    -p 8888:8888 \
    iqsharp /bin/bash

cd ~/Samples/src/Teleportation && jupyter notebook --ip=0.0.0.0 --no-browser 

docker rm --force iqsharp-container

```

