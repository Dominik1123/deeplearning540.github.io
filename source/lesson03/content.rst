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

The following questions serve as a help for learners to reflect on the content of the videos. Answer at least one question. At best you want to answer these questions as a team.

.. admonition:: Exercise 1

   When using the k-Nearest-Neighbor (kNN) algorithm for classifying a query point `x_q`, the `k` stands for:

   1. the number of neighbors that must have a given label for the query point to get this label assigned
   
   2. the number of classes occurring in the data set
   
   3. the number of observations that define a neighborhood

   4. the number of clusters in the data set
 
 
.. admonition:: Exercise 2

   When going through tutorials and exercises that discuss the k-Nearest-Neighbor (kNN) method, you observe that `k` is typically chosen to be an odd number. Checking the code, `sklearn` also allows even numbers for `k`! Why do people tend to choose odd numbers?

   1. tradition that often works best in practice
   
   2. odd numbers prevent ties from happening with the majority vote
   
   3. this way, the total number of samples in the neighborhood is always even as one has to add the query sample
   
   4. odd numbers prevent ties from happening with the plurarity vote
   
   
.. admonition:: Exercise 3

   What is the majority vote and the plurality vote if the 8 nearest neighbors to your unknown data point are of the following classes:

   a)
   
   - class 1: 3
   - class 2: 2
   - class 3: 2
   - class 4: 1

   majority vote: `____`
   plurality vote: `____`

   b)
   
   - class 1: 5
   - class 2: 2
   - class 3: 1

   majority vote: `____`
   plurality vote: `____`


.. admonition:: Exercise 4

   Find the four hidden bug(s)!

   .. code-block:: python

      from sklearn.neighbors import KNeighborsClassifier as knn
      from sklearn.model_selection import train_test_split
      from sklearn.metrics import confusion_matrix

      # ... load data set ...
      # ... load data set ...

      X_train, X_test, y_train, y_test = train_test_split(X, y,
                                                    test_size = 1.5,
                                                    random_state = 42)
      kmeans = knn(n_neighbors=5)
      kmeans = kmeans.fit(X_train, y_train)
      y_test_hat = kmeans.predict(X_train)

      cm = confusion_matrix(y_train, y_test_hat)

      accuracy = (cm[0,0]+cm[0,1]) / cm.sum()
      



Exercises
=========

Use the data set you used for `lesson02 </source/lesson02/content.rst>`_ or be brave and choose a different one. Complete the following steps in order:
Use the data set you used for `lesson02 </source/lesson02/content.rst>`_ or be brave and choose a different one. Complete the following steps in order:

For part a
----------

- Split your data set into train and test set at a fixed ratio.
- Split your data set into train and test set at a fixed ratio.

- Train a kNN classification on the training set with a fixed value of `k`. 

For part b
----------

- Run the prediction and compute accuracy, precision, recall.

- Let's vary now and recompute accuracy, precision, recall for each variant:

  - rerun everything with a smaller and a bigger testset for a fixed `k`
  - rerun everything with a different values of `k` with a fixed testset

- See for yourself: how does accuracy, precision, recall change?

- Discuss your finding with the other team members. Some prompts for the discussion:

  - should accuracy, precision, recall depend on the size of the testset? What happens in the asymptotic case (infinite testset)?
  - should accuracy, precision, recall depend on `k`?



Data sets
=========

* Data sets for clustering. Each of the following synthetic data sets contains several features `x1`, `x2`, ... and a `label` column which comprises (2 classes).

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

* `iris plants <https://scikit-learn.org/stable/data sets/toy_data set.html#iris-plants-dataset>`_ data set. Use the columns `petal_length` vs. `petal_width`. The class label is provided as the `target` column. To obtain the dataframe from this data set do the following:
* `iris plants <https://scikit-learn.org/stable/data sets/toy_data set.html#iris-plants-dataset>`_ data set. Use the columns `petal_length` vs. `petal_width`. The class label is provided as the `target` column. To obtain the dataframe from this data set do the following:

.. code-block:: python

  import pandas as pd
  from sklearn.datasets import load_iris
  iris = load_iris()
  df = pd.DataFrame(data= np.c_[iris['data'], iris['target']],
                    columns= iris['feature_names'] + ['target'])
