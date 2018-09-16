# Mapreduce and big data ana
  [apache.org](https://hadoop.apache.org/docs/r1.2.1/mapred_tutorial.html)
### Questions:

1 what is large-scale computing?  
  what tech it used?  
  what challenge it faced?
  
2 storage infrastructure  
  what tech it used?  
  what challenge it faced?
  what if node fail?  
  
3 when it said DFS data kept in "chunks"
  how to def chunks?
  
4 copying data over a network takes time ?
  bring computation `close to` the data ???
  store files multi times for reliability -> consume storage ???
  
5 map -> shuffle -> reduce 
  what dose shuffle means?
  aggregate the values by keys?? 
  
6 what is the value of video and pic ?  
  blackmirror
  
7 data -keep->  trunk ?  

8 map shuffle reduce  
  Find KV -> intermedia result -> aggregation based on your aim/goal  

9 why it called map reduced ?
  where find the meaning of map ?  

10 Running time in mapreduce ?  

11 when we need combiner -> mini-reducer  
   how it related to chunk (data)  

12 why we need more mapple ?  
   paralization , recoverry  

13 Frequent Itemset  
   (http://infolab.stanford.edu/~ullman/mmds/ch6.pdf)  

14 why it's problem to natural join two big table?  
   Q: how to use mapreduce to perform a natural join btw R(A,B) and S(B,C)  
   
   Solution:  
   ```
   map(R,tuples_of_R):
          emit(int_key b, int_value(table_name R,a))
   
   map(S,tuples_of_S):
          emit(int_key b, int_value(table_name S,c))
          
   reduce(int_key,int_vlaue[]):
      for each r in int_values:
        for each s in int_values:
            if r.table_name = 'R' and s.table_name='S':
              emit(r.a,r.b,s.c)
   
   ```
15 how to find the key in Mapreduce ?  

16 How K-means works?  
   K-mean mapreduce pseudocode:  
   Solution:  
   Input: Dataset D, centroids  
   Output: Data points w/ cluster memberships  
   1>`For` iteration =1 to maxiterations do  
   2> `mapper`: read D and centroids from HDFS  
   3> `mapper`: compute the distance btw each point in D and each point in centroids  
   4> `mapper` output : KV pairs w. key as centroid id and value as data point id and distance btw them  
   5> `shuffle and sort` : aggregate for each key (centroid)  
   6> `Reducer`: sort distance and associate data point to the nearest centroid  
   7> `Reducer`: recompute the centroids  
   8> `reducer` output: write centoirds to HDFS
   9>end For
  
17 How KNN works?  

  Input : train data D, test data X, number of nearest neighbors k  
  Output : predicted class labels of X  
  1> `Mapper` : Read D and X from HDFS  
  2> compute the distance btw each di(belong to D), and each xj(belong to X) (M to M mapping -> the computation work processing synchronize ???)  
  3> `mapper` output: key-value pairs w/ key as test instance id and value as train instance ID and the distance btw them  
  4> `shuffle and sort`: aggregate for each key (test instance)  
  5> `Reducer` :sort the distances and take first k training instances as nearest-neighbors  
  6> `reducer` : take the majority voting of class labels of nearest neighbors  
  7> `reducer` output : class labels of test instances  

### Notes:
1 Characteristics of Big data  
  4V -> volum, velocity, varety, veracity.  

2 Distributed file sys  
  Google gfs.   
  Hadoop HDFS  
  when to use? -> huge files + data is rarely updated in place ??? + reads and appends are common ??
  MAPRDUCE + HDFS(prvd a fault-tolerant file sys -> run on `commodity hdwr`)  

3 Mapreduce  
  1>Partitioner  
  
4 Hive  
  do query w/o worry about mapreduce bcs(it include inbuild function)

5 The reason of normolization is to equal the weight of diff attri.

6 Cluster's aim  
  intra-> min, inter -> max  
    
