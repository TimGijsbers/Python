


## Introduction

In this notebook we will show you a simple Cournot Model with indirect network effects. We use Python to analyse and solve the formulas. More specific, we will look into the social media market, and the results of network effects on this market. For this analysis we adopt the research method by Prufer and Argenton, Search Engine Competition with Network Externalities. (create link) In their research, Prufer and Argenton look into the effects of network externalities on the Search engine market. We use this method to analyse the Social media market.



### Our research question

Can we use the model to predict competition in the Social media market, by comparing market shares of the biggest competitiors from 2011 onwards?







```python
from scipy import optimize,arange
from numpy import array
import matplotlib.pyplot as plt
import numpy as np
from scipy.optimize import fsolve
```


```python
#Duopoly case
p=1.0
N2=1.0

def function1(N1):
    return (N1**2)*N2*p/((N2+N1)**2)
def function2(N1):
    return N1*p*(N2**2)/((1+N1)**2)
def Marketshare1(N1):
    return N1/(N1+N2)
def Marketshare2 (N1):
    return N2/(N1+N2)
```


```python

range_N1 = arange(1.2,10,1)


range_x = arange(0.0,1,0.01)
range_function1 = [function1(N1) for N1 in range_N1]
range_function2 = [function2(N1) for N1 in range_N1]
range_Marketshare1 = [function1(N1) for N1 in range_N1]
range_Marketshare2 = [function2(N1) for N1 in range_N1]
#range_triopoly1 = [triopoly1(N1) for N1 in range_N1]


```


```python
plt.clf()
plt.plot(range_N1, range_function1,'-', color = 'r', linewidth = 2)
plt.plot(range_N1, range_function2,'-', color = 'b', linewidth = 2)
plt.title("Equilibrium quality",fontsize = 15)
plt.xlabel("$N1$",fontsize = 15)
plt.ylabel("$xi$",fontsize = 15,rotation = 90)
#plt.annotate('$R_2(x1)$', xy=(0.6,function1(0.6,N_ratio2)),  xycoords='data', # here we define the labels and arrows in the graph
              #xytext=(30, 50), textcoords='offset points', size = 20,
             
#plt.annotate('$R_1(x2)$', xy=(reaction_function(0.6,N_ratio1),0.6),  xycoords='data', # here we define the labels and arrows in the graph
             # xytext=(30, 50), textcoords='offset points', size = 20,
             
              


plt.xlim(1.2,10)
plt.ylim(0.0,1,0.1)

```




    (0.0, 1)




![png](output_5_1.png)


### A short introduction on why our topic is interesting

We took the class on Innovation & Networks, and we both where really intrigued by the model on indirect network effects in the 
search engine market. We then wondered if we could apply this model to other markets as well, for example the social media market. 
In the search engine market, prufer expects that there will be only 1 monopolist over time, due to heavy network effects of this market.
We expect this same type of monopoly will result in the social media market. 

We were wondering if the proposition of data sharing, as proposed by prufer to solve the search engine monopoly result, is

Optional: (In the paper by prufer, they propose data sharing to prevent a monopolist from arising in the market, and blocking new 
access. We are interested to see if we can modify this proposition for the social media market as well, making sure no monopolist 
can arise in this market.)



### The method we use to answer our research question

First show how theory predicts triopoly case and duopoly case in a cournot market. Then use these models in combinations with our own model.

* Give the answer that you find.
  - In a Market with a high level of indirect network effects, there will be one monopolist eventually. Competitors will leave the market one by one until only one firm is left.
* Mention the main assumptions that you need to get this answer.
    - That social media depend a lot on (indirect) network effects, and that we can compare them with a search engine market.

When you use information,
create a link to this information. The reader then only needs to click to find the relevant information.If you use data, 
present graphs of the data. If you use equations, use latex to make them easy to read. Explain your code, the reader must be 
able to easily follow what you are doing. Present a clear conclusion/answer to your question. Programming is great to do 
sensitivity analysis, just to the same you did before, but now with different parameter values. Include some discussion of 
what you find and elements on which you need additional information. To increase readability, use internal links. E.g. when you 
refer to the conclusion, create a link to it so that the reader can quickly glance what you have done and go back to where she/he 
was reading. For this to work, you need to export the notebook to html. You do not have to do this, but it will impress us if you 
manage it.
