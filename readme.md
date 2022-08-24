# Jupyterlab docker container

Update ./jupyterlab/environment.yml with your dependencies

Update the ports in docker-compose.yml

Build and run the container:

    docker compose up jupyterlab

Choose the conda env kernel (not IPython) in your notebooks.

Before training and pickling a model:

- Rebuild the jupyterlab container to get the most recent python modules:

  docker compose up --build --no-start binaries
  docker compose up --build --no-start forge
  docker compose up --build jupyterlab

- Get the versions of numpy, pandas, scikit-learn (and any other serialized dependencies) from inside the notebook:

  !pip list

- Pin the versions found in ./jupyterlab/environment.yml so that pickled objects can be deserialized correctly later.

  - numpy=1.23.1
  - pandas=1.4.3
  - scikit-learn==1.1.2
