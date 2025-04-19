```bash
source ~/miniconda3/bin/activate && conda create --prefix ./env python=3.10
source ~/miniconda3/bin/activate && conda activate ./env
pip install uv
uv pip install --upgrade pip
uv pip install -r requirements.txt
uv pip install flash-attn --no-build-isolation
```