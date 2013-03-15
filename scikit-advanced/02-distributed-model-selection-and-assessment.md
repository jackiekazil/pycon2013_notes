02 - Distributed Model Selection and Assessment

# Notes: Distributed Model Selection and Assessment

Outline of the session:

- Introduction to **IPython.parallel**
- Sharing Data Between Processes with **Memory Mapping**
- **Parallel Grid Search** and Model Selection
- **Parallel** Computation of **Learning Curves**
- **Distributed** Computation on **EC2 Spot Instances with StarCluster**

## IPython.parallel, a Primer
- Single node multi-CPUs
- Multiple node multi-CPUs 
    - When u set up on your computer w/ 2 cpus, you can move to amazon & it scales easily to 30 cpus
- Interactive In-memory computing
- IPython notebook integration with `%px` and `%%px` magics
- Possibility to interactively connect to individual computing processes to launch interactive debugger (`#priceless`)

To get started, we need to start a cluster...   
Got to the clusters tab, next to the notebook     
http://127.0.0.1:8888/#tab2    
- When you hit 'start' w/o setting the engines, it will automatically set to max possible.

The next part is a whole series of ipython in parallel & is not included in this set. See the ipython notebook for more details about run in parallel.

- load balancer 

### Sharing Read-only Data between Processes on the Same Host with Memmapping
- numpy.memmap -- file is loaded into the memory system
- return value      
    [ 0.  0.  0.  0.  0.  0.  0.  0.  0.  0.]

You can see a mmap file in the directory: 
```
!ls -lh small.mmap
```

Return value:      
-rw-rw-r--  1 jakopanda  staff    40B Mar 14 15:37 small.mmap


----
personal break
----


#A More Complete Parallel Model Selection and Assessment Example

Run the C & gamma values to see the sensitivity as the process runs
```
print(search.report())      
search.boxplot_parameters(display_train=False)     
```

Results: 02-test-your-models.png


#Distributing the Computation on EC2 Spot Instances with StarCluster

- Started by MIT
- More info: http://star.mit.edu/cluster/

We require the development version for this tutorial:
```
pip install git+git://github.com/jtriley/StarCluster.git
```

Then update your config...       
/home/user/.starcluster/config       

Notebook has detailed notes on setting up starcluster, including how to set a price limit for each instance. 

If you want to know prices... you can get the history
```
starcluster -r us-west-1 spothistory c1.xlarge
```