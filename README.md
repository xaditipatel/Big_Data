# Big_Data
The projects implemented as a part of Cloud Computing course using Big Data Languages

-----------------------------------------------------------------------------
PROJECT1_MAPREDUCE:  
-----------------------------------------------------------------------------

The purpose of this project is to develop a simple Map-Reduce program on Hadoop that evaluates one step of Lloyd's algorithm for k-means clustering.

The goal is to partition a set of points into k clusters of neighboring points. It starts with an initial set of k centroids. Then, it repeatedly partitions the input according to which of these centroids is closest and then finds a new centroid for each partition. That is, if you have a set of points P and a set of k centroids C, the algorithm repeatedly applies the following steps:

Assignment step: partition the set P into k clusters of points Pi, one for each centroid Ci, such that a point p belongs to Pi if it is closest to the centroid Ci among all centroids.

Update step: Calculate the new centroid Ci from the cluster Pi so that the x,y coordinates of Ci is the mean x,y of all points in Pi.

The datasets used are random points on a plane in the squares (i*2+1,j*2+1)-(i*2+2,j*2+2), with 0≤i≤9 and 0≤j≤9 (so k=100 in k-means). The initial centroids in centroid.txt are the points (i*2+1.2,j*2+1.2). So the new centroids should be in the middle of the squares at (i*2+1.5,j*2+1.5).

-----------------------------------------------------------------------------
PROJECT2_MAPREDUCE_OPTIMIZATION:  
-----------------------------------------------------------------------------

The purpose of this project is to improve the performance of k-means clustering developed in Project 1 by using in-mapper combining.

For this project, a hash table table is created, which for each centroid c (the hash table key), it holds the object Avg(sumX,sumY,count), where sumX and sumY are partial sums, and count is a partial count, so that the new centroid for c is at (sumX/count,sumY/count)

-----------------------------------------------------------------------------
PROJECT3_GRAPHPROCESSING:  
-----------------------------------------------------------------------------

The purpose of this project is to develop a graph analysis program using Map-Reduce.

A directed graph is represented in the input text file using one line per graph vertex. 
For example, the line
1,2,3,4,5,6,7
represents the vertex with ID 1, which is linked to the vertices with IDs 2, 3, 4, 5, 6, and 7. 

For this project, a Map-Reduce program is developed that partitions a graph into K clusters using multi-source BFS (breadth-first search). 

3 Map-Reduce tasks: 
First Map-Reduce: to read the graph and select K random graph vertices(centroids) and then, at the first itearation, for each centroid, it assigns the centroid id to its unassigned neighbor
Second Map-Reduce: Implement a BFS to assigns the centroid id to the unassigned neighbors of the neighbors
Third Map-Reduce: Calculate Cluster Size 

-----------------------------------------------------------------------------
PROJECT4_KMEANS_SPARK:  
-----------------------------------------------------------------------------

The purpose of this project is to develop a data analysis program using Apache Spark.
For this project, Project1 (Kmeans Map Reduce) is re-implemented using Spark and Scala.

-----------------------------------------------------------------------------
PROJECT5_GRAPHPROCESSING_SPARK:  
-----------------------------------------------------------------------------

The purpose of this project is to develop a graph analysis program using Apache Spark.
For this project, Project3 (Graph Processing) is re-implemented using Spark and Scala.

The graph is represented as RDD[ ( Long, Long, List[Long] ) ], where the first Long is the graph node ID, the second Long is the assigned cluster ID (-1 if the node has not been assigned yet), and the List[Long] is the adjacent list (the IDs of the neighbors).

-----------------------------------------------------------------------------
PROJECT6_MAPREDUCE_PIG:  
-----------------------------------------------------------------------------

The purpose of this project is to develop a simple program for graph processing using Apache Pig.

The Pig script reads an input graph as in project3: a directed graph is represented in the input text file using one line per graph edge.
Then,  the the number of incoming links for each graph vertex is calculated and  the nodes are sorted by the number of their incoming links in descending order, so that the first node is the one that has the most incoming links.
