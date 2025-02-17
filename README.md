# Python Polylith Example

This is a repository with an example `Python` setup of the Polylith Architecture using [`pixi`](https://pixi.sh/latest/).
Here you will find examples of code being shared between different kind of projects, and the developer tooling setup.

## Developer experience

### Mypy
Have a look at the `mypy.ini` configuration file, to make `Mypy` work really well with this type of architecture.

``` ini
[mypy]
mypy_path = components, bases
namespace_packages = True
explicit_package_bases = True
```

Have a look at this repository for more information and documentation:
[Python tools for the Polylith Architecture](https://github.com/DavidVujic/python-polylith)

### Pixi
Currently, the building of conda packages using [pixi](https://pixi.sh/latest/) is still considered experimental. Notably, the available `build-backends` are still missing a few features, for instance the ability to set the package namespace to an arbitrarily name, or to include specific source code from another folder. 

A workaround is to copy the required bases and components into folder named after the chosen namespace, build the package using the `pixi build` command, and then remove the source code. These steps are done using the [`python-polylith`](https://github.com/DavidVujic/python-polylith) commands `poly build setup` and `poly build teardown` as in this Maturin [example](https://github.com/DavidVujic/python-polylith).

This workflow (`pixi run poly build setup`, `pixi build` and `pixi run poly build teardown`) can be further simplified with [`pixi` tasks](https://pixi.sh/latest/features/advanced_tasks/):
```TOML
[tool.pixi.tasks]
setup = "poly build setup"
build = { cmd = ["pixi", "build"], depends-on = ["setup"] }
teardown = { cmd = ["poly", "build", "teardown"], depends-on = ["build"] }
package = { depends-on = ["setup", "build", "teardown"] }
```
Launching the command `pixi run package` will then execute successively the three tasks `setup`, `build` and `teardown`.

An example can be found in `projects/consumer_project/pyproject.toml`.
