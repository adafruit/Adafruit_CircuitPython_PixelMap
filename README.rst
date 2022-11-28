Introduction
============


.. image:: https://readthedocs.org/projects/adafruit-circuitpython-pixelmap/badge/?version=latest
    :target: https://docs.circuitpython.org/projects/pixelmap/en/latest/
    :alt: Documentation Status


.. image:: https://raw.githubusercontent.com/adafruit/Adafruit_CircuitPython_Bundle/main/badges/adafruit_discord.svg
    :target: https://adafru.it/discord
    :alt: Discord


.. image:: https://github.com/adafruit/Adafruit_CircuitPython_PixelMap/workflows/Build%20CI/badge.svg
    :target: https://github.com/adafruit/Adafruit_CircuitPython_PixelMap/actions
    :alt: Build Status


.. image:: https://img.shields.io/badge/code%20style-black-000000.svg
    :target: https://github.com/psf/black
    :alt: Code Style: Black

CircuitPython library for mapping multiple neopixels to behave as one for the purposes of setting colors or showing animations.


Dependencies
=============
This driver depends on:

* `Adafruit CircuitPython <https://github.com/adafruit/circuitpython>`_

Please ensure all dependencies are available on the CircuitPython filesystem.
This is easily achieved by downloading
`the Adafruit library and driver bundle <https://circuitpython.org/libraries>`_
or individual libraries can be installed using
`circup <https://github.com/adafruit/circup>`_.

* `NeoPixel Products <https://www.adafruit.com/category/168>`_

Installing from PyPI
=====================

On supported GNU/Linux systems like the Raspberry Pi, you can install the driver locally `from
PyPI <https://pypi.org/project/adafruit-circuitpython-pixelmap/>`_.
To install for current user:

.. code-block:: shell

    pip3 install adafruit-circuitpython-pixelmap

To install system-wide (this may be required in some cases):

.. code-block:: shell

    sudo pip3 install adafruit-circuitpython-pixelmap

To install in a virtual environment in your current project:

.. code-block:: shell

    mkdir project-name && cd project-name
    python3 -m venv .venv
    source .env/bin/activate
    pip3 install adafruit-circuitpython-pixelmap

Installing to a Connected CircuitPython Device with Circup
==========================================================

Make sure that you have ``circup`` installed in your Python environment.
Install it with the following command if necessary:

.. code-block:: shell

    pip3 install circup

With ``circup`` installed and your CircuitPython device connected use the
following command to install:

.. code-block:: shell

    circup install adafruit_pixelmap

Or the following command to update an existing version:

.. code-block:: shell

    circup update

Usage Example
=============

.. code-block:: python

    import board
    import neopixel
    import time
    from adafruit_pixelmap import PixelMap, horizontal_strip_gridmap, vertical_strip_gridmap

    # Update to match the pin connected to your NeoPixels
    pixel_pin = board.NEOPIXEL

    # Update to match the number of NeoPixels you have connected
    pixel_num = 32

    pixels = neopixel.NeoPixel(pixel_pin, pixel_num, brightness=0.1, auto_write=True)

    pixel_wing_vertical = PixelMap.vertical_lines(
        pixels, 8, 4, horizontal_strip_gridmap(8, alternating=False)
    )
    pixel_wing_horizontal = PixelMap.horizontal_lines(
        pixels, 8, 4, horizontal_strip_gridmap(8, alternating=False)
    )

    for row in range(len(pixel_wing_horizontal)):
        pixels.fill(0x00000)
        pixel_wing_horizontal[row] = 0x00ff00
        time.sleep(0.3)

    for row in range(len(pixel_wing_vertical)):
        pixels.fill(0x00000)
        pixel_wing_vertical[row] = 0xff00ff
        time.sleep(0.3)

Documentation
=============
API documentation for this library can be found on `Read the Docs <https://docs.circuitpython.org/projects/pixelmap/en/latest/>`_.

For information on building library documentation, please check out
`this guide <https://learn.adafruit.com/creating-and-sharing-a-circuitpython-library/sharing-our-docs-on-readthedocs#sphinx-5-1>`_.

Contributing
============

Contributions are welcome! Please read our `Code of Conduct
<https://github.com/adafruit/Adafruit_CircuitPython_PixelMap/blob/HEAD/CODE_OF_CONDUCT.md>`_
before contributing to help this project stay welcoming.
