# Questions
### 1 when use sigmoid or softmax norm indtd of min-max norm??
A:don't know the min and max of dataset e.g: salary.

min-max-Normalization:
Large range -> smaller range (0-5M -> -1~1) -> some samples may centralized in a smaller range -> other space will be unused Q:

Aim:easy to store, saving storage (mapping??)
machine don't udstd the mean of attri -> 
softmax/sigmoid-Normalization
the range -> asymptote ()
(distotrion)

### 2when we what to bin data?
A:numerical -> categorized data(visulization?)

what is smooth means?

### 3: situation -> attri "age" missing 5/50/500 records of 1000,500?
can we use other attri-> pre classification -> use mean to std it? A: don't use this attri ! 

### 4:binarisation? -> downsides of binarising an attribute?
 ->5 degree -> use 0/1 to std it .
 Q: downside?

### 5:how to choose what kind of nor-method?

### 6:Diff btw binning and normalization

---
Binning:
1>equal width
2>equal depth
 ->what if a sample

### 7 how to choose the num of your bin?
A:why you bin ? -> can your bin tell you the infor of the data

we only find rlshp btw two diff attri? (scatter matrix)?


8/21
---
# Em of dm:
* Discrimination ->descibe diff btw the data
* affinity grp -> association rules
* time series ana
* classification
* clustering -> group data
* characterisation -> discrib some data
* prediction
* estimation -> predict real value, what is Real means? need a continus var?

# Data preprocessing
## 1.Why need Data preprosceing?  
  inconsistent,incomplete,noisy. avoid GOGI

## 2.Data preparation
 ```
  1>data cleaning  
  2>data integration  
  3>data transformation  
  4>data reduction
 ```
### 1 Data cleaning 

#### Missing value
 ```
 1 ignore records  
 2 filling it by hand -> time consuming  
 3 use globe constant (NULL, unknown, 0)  
 4 use attri value mean  
 5 infer most probable value -> bayesian classification/decision tree
 ```
#### Smooth out noisy data
* main approaches:
  * binning  
    replace each data value w/ a bin representative (`means` {4,8,15} -> {9,9,9} / `bounaries` {4,8,15} -> {4,4,15} 8 is close to 4)  
    mean can reduce value size; 
  * clustering  
    replace each data value w/ a cluster representative
  * regression  
    replace each data value w/ the regressed value  
    y = x + 1, fit to the line
 * Binning  
   `distance-based` partitioning may give more meaningful discretisation and considers  
   * density/num of points in an `interval`
   * "closeness" of points in an interval
   ```
   two types:  
   1> Equi-width  
      bin have equal width-> we change a numeric value -> categorized value{7 -> [0,10]}  
      Q: how to make the choice  
   2> Equi-depth  
      bin have the same num of values in them  
      Q: how to decide the size of the bin -> smaller size means more bins  
      if we needs more smooth -> more bins
   ```
### 2 Data integration
* challenges  
  ```
  1 schema integration {CID = C_NUM = CUST-ID}  
  2 Semantic heterogeneity  
  3 data value conflicts (diff representaions or scales -> $ vs RMB)  
  4 synchronisation(sequence mining-> web usage Q:)  
  5 meta-data -> data audit Q:
  ```
* Redundant attri  
  ```
  1 If th attri can be derived from other attri  
  2 correlation ana  
    If A and B are indpdt -> Pr(A and B) = Pr(A) X Pr(B)  
    Pr(A and B)/{Pr(A) X Pr(B)} -> {1-indpdt; >1-pos cor; <1-neg cor}  
    Pos-cor -> if A increase then B increase  
    Neg-cor -> if A in then B dec  
    Q: what is the dff btw correlation and confidence(association rule)  
  ```
 
 * Normalisation
   you want attri count equally -> NN  
   ```
   1 Min-max  
   A'= (A - Min)/(Max - Min) * (newMax - newMin) +newMin  
   Neg : if future input, falls outside the org data range -> out of bounds  
     -> solve it : clip the out-of-range value.(replace it by bounderary value {if value >1 use 1, if <0 use 0})
   Pos : dose not introduce any potential biases  
     -> Q: what is biases means 
   Use it when you know the proper range of your data  
   
   2 Z-score  
   Convert Normal cur -> std normal cur:  
     -> A'= (A - Mean)/(StandardDeviation)  
   Aim: figure out whether a individual might be considered as an outliner  
   Std-Normal-curve: mean=0 and stdDev=1  
   Ps: the outlier might be the opportunities -> Are they the beginning of the New trend Q:  
   Use it when you don't know the actual min and max of input data or outlier values dominate a min-max nor- Q:  
   
   3 Softmax  
   -Transform input data nonlineraly  
   -It reaches "softly" towards its max and min value but never gets there.  
   A'= 1/(1+e^(-At))  At= (A -Mean) / (λ*StdDev/2pi)  
   
   4 Sigmoid  
   - Transforms the input data nonlinearly into the range [-1,1]  
   A'= (1-e^(-V))/(1+e^(-V)) V= (A -Mean) / StdDev  
   
   
   ```
### 3 Data reducing
* Feature subset selection  
  * Techniques
    ```
    1 brute-force apprch  
      try all possi feature subsets as input to dm-algo(how does it scale w/ num of attri?)  
    2 embedded apprch  
      feature selecion occures naturally as part of dm-algo(dec-Tree, random forest)  
    3 filter apprch  
      feature selcted b4 dm-algo is run (bayes infor criterion, Infogain Q:)
  
    ```
