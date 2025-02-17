Install and Setup
=================

Installation
------------

DeepXDE requires `TensorFlow <https://www.tensorflow.org/>`_ to be installed. Then, you can install DeepXDE itself.

- Install the stable version with ``pip``::

    $ pip install deepxde

- Install the stable version with ``conda``::

    $ conda install -c conda-forge deepxde

- For developers, you should clone the folder to your local machine and put it along with your project scripts::

    $ git clone https://github.com/lululxvi/deepxde.git

- Dependencies

    - `Matplotlib <https://matplotlib.org/>`_
    - `NumPy <http://www.numpy.org/>`_
    - `scikit-learn <https://scikit-learn.org>`_
    - `scikit-optimize <https://scikit-optimize.github.io>`_
    - `SciPy <https://www.scipy.org/>`_
    - `TensorFlow <https://www.tensorflow.org/>`_>=2.2.0

Working with different backends
-------------------------------

DeepXDE supports TensorFlow 1.x (``tensorflow.compat.v1`` in TensorFlow 2.x), TensorFlow 2.x, and PyTorch backends. DeepXDE will choose the backend on the following options (high priority to low priority)

* Use the ``DDEBACKEND`` environment variable:

   - You can use ``DDEBACKEND=[BACKEND] python pde.py ...`` to specify the backend
   - Or ``export DDEBACKEND=[BACKEND]`` to set the global environment variable

* Modify the ``config.json`` file under "~/.deepxde":

   - You can use ``python -m deepxde.backend.set_default_backend [BACKEND]`` to set the default backend

Currently BACKEND can be chosen from "tensorflow.compat.v1" (TensorFlow 1.x backend), "tensorflow" (TensorFlow 2.x backend), and "pytorch" (PyTorch). The default backend is TensorFlow 1.x.

Different backends support slightly different features, and switch to another backend if DeepXDE raised a backend-related error. Some features can be implemented easily, we welcome your contributions.

TensorFlow 1.x backend
``````````````````````

Export ``DDEBACKEND`` as ``tensorflow.compat.v1`` to specify TensorFlow 1.x backend. The required TensorFlow version is 2.2.0 or later. TensorFlow 1.x backend uses `tensorflow.compat.v1 APIs <https://www.tensorflow.org/api_docs/python/tf/compat/v1>`_ in TensorFlow 2.x and disables the eager execution.

.. code:: python

   import tensorflow.compat.v1 as tf
   tf.disable_eager_execution()

TensorFlow 2.x backend
``````````````````````

Export ``DDEBACKEND`` as ``tensorflow`` to specify TensorFlow 2.x backend. The required TensorFlow version is 2.2.0 or later.

PyTorch backend
```````````````

Export ``DDEBACKEND`` as ``pytorch`` to specify PyTorch backend.
