```bash
source ~/miniconda3/bin/activate && conda create --prefix ./env python=3.10
source ~/miniconda3/bin/activate && conda activate ./env
pip install uv
uv pip install --upgrade pip
uv pip install -r requirements.txt
uv pip install flash-attn --no-build-isolation



source ~/miniconda3/bin/activate && conda create --prefix ./vita_demo python==3.10
source ~/miniconda3/bin/activate && conda activate ./vita_demo
pip install uv
uv pip install --upgrade pip
apt install portaudio19-dev python3-pyaudio
uv pip install -r web_demo/web_demo_requirements.txt
```