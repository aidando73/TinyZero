```bash
cp ~/runpod_credentials .envrc
direnv allow

source ~/miniconda3/bin/activate && conda create --prefix ./env python=3.9
source ~/miniconda3/bin/activate ./env
pip install uv
uv pip install torch==2.4.0 --index-url https://download.pytorch.org/whl/cu121
uv pip install vllm==0.6.3 # or you can install 0.5.4, 0.4.2 and 0.3.1
uv pip install ray
uv pip install -e .
# flash attention 2
uv pip install flash-attn --no-build-isolation
# quality of life
uv pip install wandb IPython matplotlib


tmux
export N_GPUS=2
export BASE_MODEL=Qwen/Qwen2.5-3B
export DATA_DIR=data/countdown
export ROLLOUT_TP_SIZE=2
export EXPERIMENT_NAME=countdown-qwen2.5-3b
export VLLM_ATTENTION_BACKEND=XFORMERS

bash ./scripts/train_tiny_zero_h200_ppo.sh
```