# M1_Tensorflow_GPU_Acceleration
Local Conda setup instructions to utilize m1 chip GPU w/ tensorflow library 

The goal of this project is to provide a skeleton for Mac M1 users to run tensorflow code locally. The need for this arose from the revelation that current tensorflow training materials only outline indstructions for NVIDIA GPUs and recommend purchasing compute time on their infra where applicable rather than having detailed outlines for Mac OS X users. 

This environment template is built using:

Prerequisites: 

[miniforge3 conda distribution](https://github.com/conda-forge/miniforge) 

Dependencies:
[tensorflow-macos](https://pypi.org/project/tensorflow-macos/),
[tensorflow-metal](https://developer.apple.com/metal/tensorflow-plugin/)


Configs:
`environment.yml` contains pip dependencies while `environment_strict.yml` is solely the conda environemnt. 

# Note
Python environment set to 3.9.13 because of lack of python 3.10 wheel for open3D library [issue](https://github.com/isl-org/Open3D/issues/4535)

# Set up instructions
`$ conda env create -f environment.yml`

`$ conda activate tf_sensor_gpu`


# Validate GPU usage
Test it out. To see if everything worked, try starting a Jupyter Notebook and importing the installed packages.

```bash
# Start a Jupyter notebook
jupyter notebook
```

Once the notebook is started, in the first cell:

```python
import tensorflow as tf

# Check for TensorFlow GPU access
print(tf.config.list_physical_devices())

# See TensorFlow version
print(tf.__version__)
```

If it all worked, you should see something like:

```bash
TensorFlow has access to the following devices:
[PhysicalDevice(name='/physical_device:CPU:0', device_type='CPU'),
PhysicalDevice(name='/physical_device:GPU:0', device_type='GPU')]
TensorFlow version: 2.5.0
```
