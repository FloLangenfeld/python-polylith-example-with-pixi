# Example usage

## Build the project
Navigate to this folder (where the `pyproject.toml` file is)

Run:
``` shell
pixi run poly build setup
pixi build
pixi run poly build teardown
```

## Upload the conda package to your favorite server

## Add this server to the workspace table

For instance:
``` toml
[tool.pixi.workspace]
channels = [
    "https://prefix.dev/pixi-build-backends",
    "https://prefix.dev/conda-forge",
    "https://my-favorite-server.url",
]
```

## Add message_fastapi_project to your environment

``` shell
pixi add message_fastapi_project
```

## Use the pixi task from the `pyproject.toml` file to run the app

``` shell
pixi run start
```

The OpenAPI specification of this FastAPI app can now be accessed at http://localhost:8000/docs#
