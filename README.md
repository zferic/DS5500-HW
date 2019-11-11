DS500-Homeworks
# Problem 1

![Figure 1](/figures/total_rev_by_state.png)
![Figure 2](/figures/total_fedrev_by_state.png)

# Problem 2

![Figure 3](/figures/rev_vs_expenditures.png)

P-value: 
< 0.0001

Equation: 
Totalexp = 0.98555*Totalrev + 8.52894e+07

States with the 10 Highest debt ratios per student:
```
STABBR	debt_ratio
ND	1.098112
NC	1.055334
NE	1.054926
AK	1.051438
DC	1.051026
MN	1.046227
MT	1.043661
AL	1.033855
NY	1.020428
WA	1.019277
```
# Problem 3

```python

def process_col(item,opt1, opt2):
    
    
    #range givem.. can chose upper or lower based on input
    if len(item.split('-')) > 1:
        #opt1 - takes lower and upper limit and returns midpoint        
        if opt1 == 1:
            lower = int(item.split('-')[0])
            upper = int(item.split('-')[1])
            #this is themidpoint of the interval
            act = (upper - lower)/ 2 + lower
        #take the lower value in the interval
        elif opt1 == 2:
            act = int(item.split('-')[0])
        #take the upper value in the interval
	elif opt1 == 3:
            act = int(item.split('-')[1])
    
    #case less than/equal to..if opt2 = 2, we do not consider these
    elif 'LE' in item:
        if opt2 == 1:
            act = int(item.replace('LE',''))
        if opt2 == 2:
            act = -85
    #case greater than
    elif 'GE' in item:
        if opt2 == 1:
            act = int(item.replace('GE',''))
        if opt2 == 2:
            act = -85
    #case less than
    elif 'LT' in item:
        if opt2 == 1:
            act = int(item.replace('LT',''))
        if opt2 == 2:
            act = -85
    elif 'PS' in item:
        #code for act
        #some error occure din the cleaning
        ## this is a problem
        ## if a lot is missing will be skewed tlower significantly based on missingness 
        act = np.nan
    else:
        try:
            act = int(item)
        except: 
            #error code.. something went wrong
            act = -6
            
    return act     
```

Please see code comments for detailed cleaning of the exam scores.

![Figure 4](/figures/math_competancy_by_state.png)

![Figure 5](/figures/reading_competancy_by_state.png)

# Problem 4

15% of the the U.S. federal budget currently being spent (2015-2016) is $8340411300.0.

Each schools reading and math proficiency scores were evaluated and are presented in the following figure:

![Figure 6](/figures/dist_plot_math_read2.png)

We see that the spread follows a normal distribution for both reading and math, with schools achieving overall better scores in the reading proficiency. Keeping these distributions in mind, and also that it has been established that the amount of funding has a direct causal relationship on school performance, an optimal budget reduction approach should consider these scores.

10 out of the 431 proposed LAEID and cuts are:
```
LAEID	Budget Cut
2502710	1.152360e+07
2503870	1.019955e+07
4800254	1.433025e+06
2506930	9.582450e+06
3170110	3.184062e+07
4801438	4.854525e+06
4817760	3.022353e+07
3400746	1.140000e+06
2508910	2.530800e+07
2500058	2.337000e+06
```
# Problem 5

The main consideration for cutting funds was the average math and reading competency of each school district. (Grouped by LAEID.) I created a sorted list of LAEIDS based on the scores in descending order and applied the following formula to determine how much funding should be cut.

Amount Cut ($) = .15 * (Average reading and math proficiency) * (Total Fed Budget)

The formula aims to take 15% from the top performing schools. However, this percentage is also weighed based on the average reading and math scores which enforces slightly stronger cuts on the top performing schools. We do not want to penalize top performing schools equally, as this may have a negative impact. 





