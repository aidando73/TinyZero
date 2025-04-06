```bash
cp ~/runpod_credentials .envrc
direnv allow

source ~/miniconda3/bin/activate && conda create --prefix ./env python=3.9
source ~/miniconda3/bin/activate ./env
pip install torch==2.4.0 --index-url https://download.pytorch.org/whl/cu121
pip3 install vllm==0.6.3 # or you can install 0.5.4, 0.4.2 and 0.3.1
pip3 install ray
```