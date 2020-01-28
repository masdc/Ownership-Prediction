# Tensor Flow 2.0 Data Science Python Template

Repository containing scaffolding for a Python 3-based data science project using on the [TensorFlow](https://www.tensorflow.org/) ecosystem. 

## Creating a new project from this template

Simply follow the [instructions](https://help.github.com/en/articles/creating-a-repository-from-a-template) to create a new project repository from this template.

## Project organization

Project organization is based on ideas from [_Good Enough Practices for Scientific Computing_](https://journals.plos.org/ploscompbiol/article?id=10.1371/journal.pcbi.1005510).

1. Put each project in its own directory, which is named after the project.
2. Put external scripts or compiled programs in the `bin` directory.
3. Put raw data and metadata in a `data` directory.
4. Put text documents associated with the project in the `doc` directory.
5. Put all Docker related files in the `docker` directory.
6. Install the Conda environment into an `env` directory. 
7. Put all notebooks in the `notebooks` directory.
8. Put files generated during cleanup and analysis in a `results` directory.
9. Put project source code in the `src` directory.
10. Name all files to reflect their content or function.

## Using Conda

### Creating the Conda environment

Open the environment.yml file and add the name you want for the environment.  Replace 'none' with you own name

After adding any necessary dependencies that should be downloaded via `conda` to the `environment.yml` file 
and any dependencies that should be downloaded via `pip` to the `requirements.txt` file you create the 
Conda environment in a sub-directory `./env`of your project directory by running the following commands.

```bash
$ conda env create --prefix ./env --file environment.yml
```

Once the new environment has been created you can activate the environment with the following 
command.

```bash
$ conda activate ./env
(/path/to/env) $
```

Note that the `./env` directory is *not* under version control as it can always be re-created from 
the `./bin/create-conda-environment.sh` file as necessary.

### Updating the Conda environment

If you add (remove) dependencies to (from) the `environment.yml` file after the environment has 
already been created, then you can update the environment with the following command.

```bash
$ conda env update --prefix ./env --file environment.yml --prune
```

### Verifying the Conda environment

After building the Conda environment you can check that Horovod has been built with support for 
TensorFlow and MPI with the following command.

```bash
$ conda activate ./env # optional if environment already active
(/path/to/env) $ horovodrun --check-build
```

### Listing the full contents of the Conda environment

The list of explicit dependencies for the project are listed in the `environment.yml` file. To see 
the full lost of packages installed into the environment run the following command.

```bash
conda list --prefix ./env
```

## Using Docker

In order to build Docker images for your project and run containers you will 
need to install [Docker](https://docs.docker.com/install/linux/docker-ce/ubuntu/) and  
[Docker Compose](https://docs.docker.com/compose/install/).

Detailed instructions for using Docker to build and image and launch containers can be found in 
the `docker/README.md`.
