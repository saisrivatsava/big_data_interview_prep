## Union and Union All

* UNION and UNION ALL are SQL operators used to concatenate 2 or more result sets.

* **UNION:** only keeps unique records
* **UNION ALL:** keeps all records, including duplicates

## Map, FlatMap, Partition Map

* **map** :It returns a new RDD by applying a function to each element of the RDD. 
* **Flat Map** : Similar to map, it returns a new RDD by applying  a function to each element of the RDD, but output is flattened.
Also, function in flatMap can return a list of elements (0 or more)
* **MapPartition** : mapPartitions() can be used as an alternative to map() & foreach().
mapPartitions() is called once for each Partition unlike map() & foreach() which is called for each element in the RDD. 
The main advantage being that, we can do initialization on Per-Partition basis instead of per-element basis(as done by map() & foreach())

## Types of Joins 

* **Inner joins** (keep rows with keys that exist in the left and right datasets)
* **Outer joins** (keep rows with keys in either the left or right datasets)
* **Left outer joins** (keep rows with keys in the left dataset)
* **Right outer joins** (keep rows with keys in the right dataset)
* **Left semi joins** (keep the rows in the left, and only the left, dataset where the key
appears in the right dataset)
* **Left anti joins** (keep the rows in the left, and only the left, dataset where they do not
appear in the right dataset)
