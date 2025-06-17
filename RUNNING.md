# 🏁 Running the TransFuser Agent on CARLA 0.9.14

This document provides step-by-step instructions to set up the environment and run the InterFuser agent, adapted for **Python 3.8** and **CARLA 0.9.14**.

---

## 🧱 1. Environment Setup

Clone your fork of the InterFuser repository:

```bash
git clone https://github.com/NiccoloSalvi/InterFuser-Carla0914.git
cd InterFuser-Carla0914
```

Create and activate a Conda environment:
```bash
conda env create -f transfuser\environment.yml
conda activate tfuse38
````

---

## 📦 2. Install Dependencies

Install the modified set of requirements. Note that we removed packages incompatible with Python 3.8:

* ❌ Removed: `matplotlib==3.0.3`, `open3d==0.9.0.0`

To install the necessary packages:

```bash
pip install -r team_code_transfuser/requirements.txt
pip install --upgrade setuptools importlib_metadata
pip install torch-scatter -f https://data.pyg.org/whl/torch-1.11.0+cu102.html
pip install mmcv-full==1.5.3 -f https://download.openmmlab.com/mmcv/dist/cu102/torch1.11.0/index.html
pip install carla==0.9.14
pip install mmdet==2.25.0
```

---

## 💾 3. Download Pretrained Weights

Download the example model weights for direct evaluation from the following [link](https://s3.eu-central-1.amazonaws.com/avg-projects/transfuser/models_2022.zip).

Then move the weights to the working directory:

---

## 🚦 5. Run the Evaluation

We provide a modified version of the original script:

**Modified script path**:

```
leaderboard/scripts/run_evaluation.sh
```

Make sure this script contains the correct paths and environment variables for:

* The model config file
* The team agent
* The route and scenario directories

Then execute it:

```bash
bash leaderboard/scripts/run_evaluation.sh
```

---

<!-- ## 📸 6. Save Output Images (Optional)

To analyze the agent's visual perception and decision-making:
* We modified `interfuser_agent.py`
* In particular, the `setup()` and `save()` methods were edited to save RGB images (or other sensor outputs) during simulation.

This feature can be used to:
* Debug agent behavior
* Visualize failure cases
* Compare different model versions -->