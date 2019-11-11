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

# Problem 3

```python

def process_col(item,opt1, opt2):
    
    
    #range givem.. can chose upper or lower based on input
    if len(item.split('-')) > 1:
        
        if opt1 == 1:
            lower = int(item.split('-')[0])
            upper = int(item.split('-')[1])
            #this is themidpoint of the interval
            act = (upper - lower)/ 2 + lower
        
        elif opt1 == 2:
            act = int(item.split('-')[0])
        elif opt1 == 3:
            act = int(item.split('-')[1])
    
    #case less than/equal to
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
![Figure 4](/figures/math_competancy_by_state.png)

![Figure 5](/figures/reading_competancy_by_state.png)

# Problem 4


# Problem 5



