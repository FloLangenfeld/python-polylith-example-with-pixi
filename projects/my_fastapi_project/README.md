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

## Add the server to the tool.pixi.workspace.channels table

For instance:
``` toml
[tool.pixi.workspace]
channels = [
    "https://prefix.dev/pixi-build-backends",
    "https://prefix.dev/conda-forge",
    "https://my-favorite-server.url",
]
```

## Add the package to your pixi environment

``` shell
pixi add my_aws_lambda_project
```

## Launch the app

``` shell
pixi run start
```

The OpenAPI specification of this FastAPI app can now be accessed at http://localhost:8000/docs#
