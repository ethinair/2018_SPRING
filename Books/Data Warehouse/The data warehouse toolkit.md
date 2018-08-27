# Chapter one DW ,BI and dimensional modeling primer

## Dimensional modeling intro

### Question
- why most RDB mngmt sys can not efficiently query a `normalized` model?

### Notes
1. dimensional model contains the same infor as a normalized model, but paclages the data in a format tht delivers user understandbility,
query performacne, and resilience to change ???

2. star schemas vs OLAP cubes  
where the dimensional model implemented ?  
RDBMS -> STAR SCHEMAS  
MUTIDIMENTIONAL DB -> OLAP CUBES

3.  OLAP
  - a star schema in a RDB -> a good physical foundation for building OLAP cube ???
  - more sophisticated security options
  - richer ana capabilities -> saddled by constraints of SQL ???

4. Fact table
 fact represents a busi measure ? 
 Each row in a fact table corresponds to a measurement event ??
 the data on each row is at a specific level of detail -> referred to as the `grain`??
 * a measurement event in the physical wld has a 1:1 rlshp to a single row in the corresponding fact table is a bedrock principle.
 what dose it means tt a  put `textual data` into dim ???
 ```
 three types:
 1 transaction
 periodic snapshot
 accumulating snapshot
 ```
 * referential integrity
 all keys in fact tb match their respective pk in corresponding dim tab.
 access fact tbl via dim-tbl joined to it !!!
 
 5. Dim table
  contain textual context -> rlt to busi process measurement event. -> 5 W + 1 H about the event.
  dim table have few row comp w/ fact table ? bsc its job is descrble ???
  - dim's attri -> primary src of query constraints, grp and `rpt labels` ???.
  
  
---

# Chapter Three Retail Sales

### Outlines
```
1 Four step dim-desgn process
2 case sty
3 dim tbl details
4 retail schema
5 dim and fact tbl keys
```

## 1 Four steps dim-design process
### Step 1 : slect busi process

### Step 2 : declare the grain
- Questions:  
1 what is grain  
 [grain](https://www.ibm.com/support/knowledgecenter/en/SS9UM9_9.1.1/com.ibm.datatools.dimensional.ui.doc/topics/c_dm_design_cycle_2_idgrain.html)
The number of dim depds what level of detail your fact tbl or dim-model is ??  
Diff dim consist a picture of your aim qury ??

2

- Notes:  
1 

### Step 3 id the dim
- Questions:
- Notes:

### Step 4 id the facts
- Questions:
- Notes:
