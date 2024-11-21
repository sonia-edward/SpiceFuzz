# SpiceFuzz

The code and dataset for the paper "SpiceFuzz: LLM-Based Fuzzing for SPICE Circuit Simulator Tools Bug Detection", implemented in Pytorch. SpiceFuzz obtains circuits from the official website of the SPICE simulator and processes them to obtain a seed netlist library. Then, SpiceFuzz uses reinforcement learning to select mutations and constructs prompts with mutation rules and syntactic patterns. Then, the prompts are used to use the Large Language Models to perform specific mutations to obtain the test netlist. Finally, the differences in results are discovered through differential testing on different solvers, and feedback is given to reinforcement learning or LLMs based on the simulation results.

## 1. Project Structure
- `data/`
	- `data/raw_data/ : circuits obtained from the official website of the SPICE simulator`
	- `data/seed_netlist/ : seed netlist processed by data_preparation.py`
- `result/ : `
- `scripts/`
	- `mutations.py : get mutation rules and syntax forms`
	- `reinforcement_learning.py : A2C algorithm`
	- `differential_testing.py : differential testing`
	- `extract_error.py : extract error info from log file`
- `data_preparation.py : extract netlist files from raw data `
- `main.py : a file for start`

## 2. Environment Setup

The code is tested with Python 3.10. All dependencies are listed in [requirements.txt](requirements.txt).

## 3. Data preparation
The data is stored in the "data" folder. The training dataset should be named in the format of project name + "_train.json" and put it in the folder `data/train/`. 
The testing dataset should be named in the format of project name + "_test.json" and put it in the folder `data/test/`.


## 4. Usage
When your dataset is ready in the previous step, you can go to the "train.py" to modify the name of the "project", and you can modify config parameters through "Config" class. Finally, start the code by command.


```
python train.py
```

## Citation

If you find the code useful, please cite our paper.
```
********
```

## Contact

For any questions, please drop an email to ********.
