The easiest way to start with the [QDK](https://github.com/Microsoft/Quantum) is via a docker container and Jupyter notebooks. 

Unfortunately this doesn't seem to be possible in Azure Notebooks but we can run the notebooks on local Docker instances.  

This is a simulator, you don't need a quantum computer.  

### What is this?  

This demos the ["Quantum Eraser Experiment"](https://en.wikipedia.org/wiki/Quantum_eraser_experiment) using Q#.  This experiment demonstrates several fundamental aspects of quantum mechanics, including quantum entanglement.  

Huh?

A photon is shot through a certain type of crystal which converts it into two entangled photons of lower frequency.  These entangled photons follow separate paths and should be _changed_ somehow.  But they aren't.  Regardless of how entangled they are, they always preserve their 

around 33:00

q computing has reversible gates unlike classical computing


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


open Microsoft.Quantum.Math;
open Microsoft.Quantum.Diagnostics;
open Microsoft.Quantum.Convert;
open Microsoft.Quantum.Measurement;

operation Interference () : Unit {
    using ((q,c) = (Qubit(), Qubit())) {
        let theta - PI()/10.0;
        H(q);       //put the qubit in the superposition of both paths/slits
        R1(theta*2.0,q);        //generate phase shift of sita
        H(q);                   //make the two paths interference
        Message("P(0)=" + DoubleAsString(Cos(theta)*Cos(theta)));
    }
}