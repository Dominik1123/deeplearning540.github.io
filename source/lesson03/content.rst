Lesson 03: From Clustering To Classification
********************************************

Learning Objectives
===================

* remember how clustering works
* Apply clustering for classification
* recognize that once clustering is trained/used, it can be used for classification on new data
* use accuracy, precision and recall to describe the classifiers performance
* reflect that classification performance depends on the choice of hyperparameters
* discuss that accuracy, precision and recall can depend the size of the testset, choice of hyperparameters


Content
=======

This lesson will be shared as a video.

* for learners: a stub notebook to get you started can be obtained from `the lesson03 repo <https://github.com/deeplearning540/lesson03/blob/main/lesson.ipynb>`_.
* for instructors: the video script is available `here <https://github.com/deeplearning540/deeplearning540.github.io/blob/main/source/lesson03/script.ipynb>`_.


Check your Learning
===================

.. admonition:: Exercise 1

   **TBA**

   1. ???
   2. ???
   3. ???
   4. ???


Exercises
=========

Use the dataset you used for `lesson02 </source/lesson02/content.rst>`_ or be brave and choose a different one. Complete the following steps in order:

- Split your dataset into train and test set at a fixed ratio.

- Train a kNN classification on the training set with a fixed value of `k`. 

- Run the prediction and compute accuracy, precision, recall.

- Let's vary now and recompute accuracy, precision, recall for each variant:

  - rerun everything with a smaller and a bigger testset for a fixed `k`
  - rerun everything with a different values of `k` with a fixed testset

- See for yourself: how does accuracy, precision, recall change?

- Discuss your finding with the other team members. Some prompts for the discussion:

  - should accuracy, precision, recall depend on the size of the testset? What happens in the asymptotic case (infinite testset)?
  - should accuracy, precision, recall depend on `k`?



Datasets
========

* Datasets for clustering. Each of the following synthetic datasets contains several features `x1`, `x2`, ... and a `label` column which comprises (2 classes).

  * `clustering_data_00.csv <https://github.com/deeplearning540/lesson02/blob/main/data/clustering_data_00.csv>`_
  * `clustering_data_01.csv <https://github.com/deeplearning540/lesson02/blob/main/data/clustering_data_01.csv>`_
  * `clustering_data_02.csv <https://github.com/deeplearning540/lesson02/blob/main/data/clustering_data_02.csv>`_
  * `clustering_data_03.csv <https://github.com/deeplearning540/lesson02/blob/main/data/clustering_data_03.csv>`_
  * `clustering_data_04.csv <https://github.com/deeplearning540/lesson02/blob/main/data/clustering_data_04.csv>`_
  * `clustering_data_05.csv <https://github.com/deeplearning540/lesson02/blob/main/data/clustering_data_05.csv>`_
  * `clustering_data_06.csv <https://github.com/deeplearning540/lesson02/blob/main/data/clustering_data_06.csv>`_
  * `clustering_data_07.csv <https://github.com/deeplearning540/lesson02/blob/main/data/clustering_data_07.csv>`_
  * `clustering_data_08.csv <https://github.com/deeplearning540/lesson02/blob/main/data/clustering_data_08.csv>`_
  * `clustering_data_09.csv <https://github.com/deeplearning540/lesson02/blob/main/data/clustering_data_09.csv>`_

* `iris plants <https://scikit-learn.org/stable/datasets/toy_dataset.html#iris-plants-dataset>`_ dataset. Use the columns `petal_length` vs. `petal_width`. The class label is provided as the `target` column. To obtain the dataframe from this dataset do the following:

  ```
    import pandas as pd
    from sklearn.datasets import load_iris
    iris = load_iris()
    df = pd.DataFrame(data= np.c_[iris['data'], iris['target']],
                      columns= iris['feature_names'] + ['target'])
  ```
