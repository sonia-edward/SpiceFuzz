# SpiceFuzz

The code and dataset for the paper "SpiceFuzz: LLM-Based Fuzzing for SPICE Circuit Simulator Tools Bug Detection", implemented in Pytorch. SpiceFuzz obtains circuits from the official website of the SPICE simulator and processes them to obtain a seed netlist library. Then, SpiceFuzz uses reinforcement learning to select mutations and constructs prompts with mutation rules and syntactic patterns. Then, the prompts are used to use the Large Language Models to perform specific mutations to obtain the test netlist. Finally, the differences in results are discovered through differential testing on different solvers, and feedback is given to reinforcement learning or LLMs based on the simulation results.

## 1. Project Structure
- `data/`
	- `data/raw_data/ : circuits obtained from the official website of the SPICE simulator`
	- `data/seed_netlist/ : seed netlist processed by data_preparation.py`
- `result/ : results after testing `
- `scripts/`
	- `mutations.py : get mutation rules and syntax forms`
	- `reinforcement_learning.py : A2C algorithm`
	- `differential_testing.py : differential testing`
	- `extract_error.py : extract error info from log file`
- `data_preparation.py : extract netlist files from raw data `
- `main.py : a file for start`

## 2. Environment Setup

The code is tested with Python 3.10. All dependencies are listed in [requirements.txt](requirements.txt). And please ensure that the Ngspice or LTspice path is configured in the environment variable.

## 3. Data preparation

The raw data is stored in the "data/raw_data" folder. Before starting SpiceFuzz, the compressed files should be extracted to the corresponding folder. Then start the data preparation code using the following command:
```
python data_preparation.py --raw_data_path ./data/raw_data/ngspice (regression) test circuits
```
Similar parameters can be configured through commands or directly modified at the beginning of the code. At the same time, you can also obtain the latest snapshot from the official website of [Ngspice](https://sourceforge.net/p/ngspice/ngspice/ci/master/tree/tests/) and [LTspice](https://www.analog.com/cn/resources/design-tools-and-calculators/ltspice-simulator/lt-spice-demo-circuits.html) and follow the steps above.

## 4. Usage

After obtaining the available netlist files through the previous step, you can then start SpiceFuzz using the following command：
```
python main.py --seed_dir ./data/seed_netlist/ngspice (regression) test circuits
```
Similar parameters can be configured through commands or directly modified at the beginning of the code. Finally, the results classified by symptoms can be viewed in the "result" folder.

## Citation

If you find the code useful, please cite our paper.
```
********
```

## Contact

For any questions, please drop an email to ********.
