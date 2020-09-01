# Optimization Data
This repository contains the data from the optimization runs that were executed for our research work. 
This is a dataset accompanying the [github repository for our research work](https://github.com/MBtech/bbo-arena):

> **Do the Best Cloud Configurations Grow on Trees? An Experimental Evaluation of Black Box Algorithms for Optimizing Cloud Workloads.** </br>
> Muhammad Bilal, Marco Serafini, Marco Canini and Rodrigo Rodrigues. </br>
> Proceedings of the VLDB Endowment, 13(11). </br>

**The directory names might be subject to change as this would be made a submodule for the parent repo.**

## Directory Structure

### hyperparam and hyperparam_cost
Contains the data for optimization runs for execution time and execution cost objective function, respectively. 

#### Naming Convention
Each directory contains a JSON file.   
The JSON files inside these directories have the following naming convention:

For BO methods
```
<Framework>_<Benchmark>_<InputSize>_bo_<Number of Init Samples>_<Hyperparam values>_<Surrogate Model>_<Acquisition Function>
```

For TPE
```
<Framework>_<Benchmark>_<InputSize>_tpe_<Number of Init Samples>_<Hyperparam value>
```

For Random Search
```
<Framework>_<Benchmark>_<InputSize>_random
```

For Stochastic Hill Climbing
```
<Framework>_<Benchmark>_<InputSize>_hc_<Number of Init Samples>_<Temperature value>
```

For Simulated Annealing
```
<Framework>_<Benchmark>_<InputSize>_sa_<Number of Init Samples>_<alpha value>_<Temperature value>
```

#### JSON Data
Each file inside contains the data of the configurations tested by an optimization algorithm. The format of the JSON file is as follows:
```json
{
    "experiments": [
        [
            {
                "params": {
                    "type": "m4",
                    "size": "xlarge",
                    "num": 4
                },
                "value": 2905.172
            },
            ...
         ],
         ...
    ]
}
```

It contains a list of `experiments`. Each experiment is a full run of an optimization algorithm.  
Each experiment contains a list of 30 optimization runs.  
Each optimization run includes two fields:
- `params`: contains the information about the cloud configuration used
- `value`: is the value for the objective function

### error
The csv files inside this directory have the following format:
```
<Objective Function>_error_<framework>_<benchmark>_<input size>.csv
```

The csv files contain four different error metrics: Absolute Error (ae), Mean Absolute Error (mae), Mean Squared Error (mse) and Root Mean Squared Error (rmse). 
The last column is the optimization algorithm. 
