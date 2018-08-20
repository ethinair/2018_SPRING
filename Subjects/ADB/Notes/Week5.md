# Week 5 BI and DM 

## Preview

### Outline
- Principles of DM
- Association Rule Mining
  >Q? 
  
### Pinciples of DM
- Cross-market ana 
```
  1 associations/co-relations btw product sales
  2 prediction based on the association of infor
```

### Data Mining
- DM functionalities
```
  1 associations (correlation and causality)
   ->
   age(X,"20..29"), income(X,"20..29K")-->buys(X,"PC")[support=2%,confidence=60%]
  2 classification and prediction
   ->finding models(`functions`) that describe and distinguish classes or concepts for future predictions
   ->presentation: decision tree, classification rule, NN
   ->prediction: predict unknown or missing numerical values
  3 cluster analysis
   ->class label is unknown
   ->claustering based on the principle: maximizing the `intra-class similarity` and minimizzing the `interclass similarity`
  4 outlier analysis
```

### Association rule mining
- Object is finding all co-occurrence rltshp(`associations`) among data items
- basic concepts
  ```
  I = {i1,i2,...,im} // a set of items
  T = {t1,t2,...,tn} // a set of transaction where each T ti is a set of items(ti e I).
  
  X->Y, where X e I, Y e I and X ∩ Y = none
  E.G.
    i1 = beef , i2 = chicken, i3 = cheese
    t1:beef, chicken,milk
    t2:beef,cheese
    t3:cheese,wine
    
    ->association rule might:
     beef,chicken -> milk, where {beef,chicken} is X and {Milk} is Y
  ```
- rules can be weak or strong <br/>
  1 the strength of rule measured by `support` and   `confidence` <br/>
  2 the support -> how freq the items appear in the db <br/>
  3 the conf -> the num of times the if/then sttmt been found to be Ture 

### Apriori Algorithm
- two steps <br/>
 1>find all freq itemsets (set of items w/ sup>= minsup) <br/>
 2>use freq itemsets to generate rules
- key words <br/>
 1 threshold C  
 2 bottom up approach -> candidate generation <br/>
 
 
### Questions
 1 Obj of mining association rule -> dis all `associated rules` in T tht have `sup and conf` greater than a minimum threshold
   how to def the threshold and how to figure out its value ?
 2 how can you figure out tht X(chicken,beef) -> Y (milk) in a Transaction, since they are all independent items ?  
 3 what is hash tree ?
 4 breadth-first search

test  
sdf
