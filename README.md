[![Maintainability](https://api.codeclimate.com/v1/badges/b48a5bd1bcaac990923a/maintainability)](https://codeclimate.com/github/Nikolay-Lysenko/renovation/maintainability)
[![PyPI version](https://badge.fury.io/py/renovation.svg)](https://pypi.org/project/renovation/)

# Renovation

## Overview

This is a drawing tool that produces floor plans. It is controlled through YAML config files and has no built-in GUI (only CLI is provided). Although it may look like a drawback, people with technical background may find it more convenient. Compared with drag-and-drop tools, config-based interface simplifies fine-grained control and allows versioning projects with VCSs like Git.

The below figure demonstrates available elements.

![individual_elements.png](https://github.com/Nikolay-Lysenko/renovation/blob/master/docs/images/individual_elements.png)

Some other elements can be composed of them. For example, in the next section it is shown how to draw ventilation duct and French balcony.

## Usage

To install a stable version, run:
```bash
pip install renovation
```

To generate floor plans, run:
```bash
python -m renovation -c /path/to/config.yml
```
Here, config in YAML is a custom file where properties of each element to be drawn are set. These properties include location, orientation, size, and so on. 

Let us dive into details. Please look at a [demo example](https://github.com/Nikolay-Lysenko/renovation/blob/master/docs/demo_configs/simple_floor_plan.yml) as a reference while reading further explanations.

The section named `project` defines properties of output such as:
* Extension (multi-page PDF document, directory with PNG images, or both)
* Location
* DPI (dots-per-inch, resolution)

In the demo config, only PNG output is requested and one of the generated images is shown below: 

![floor_plan_with_dimensions.png](https://github.com/Nikolay-Lysenko/renovation/blob/master/docs/images/floor_plan_with_dimensions.png)

In the section named `default_layout`, below parameters are set for floor plans that do not override them in their `layout` sections:
* Dimensions of area to be drawn (in real-world meters, i.e., meters prior to scaling)
* Scale
* Grid settings

The section named `reusable_elements` is designed to store arbitrary collections of elements that can be used by individual floor plans. Demo example uses it to define walls, windows, and doors.

Finally, settings of individual floor plans are listed. These settings might include:
* Title
* Layout
* Names of element collections to reuse
* Extra elements
