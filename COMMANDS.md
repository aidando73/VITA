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
uv pip install einops timm
cp ~/.runpod_credentials .envrc
huggingface-cli login --token $HF_TOKEN
huggingface-cli download VITA-MLLM/VITA-1.5 --local-dir demo_VITA_ckpt
mv demo_VITA_ckpt/config.json demo_VITA_ckpt/origin_config.json
cp -rf ./web_demo/vllm_tools/qwen2p5_model_weight_file/*  ./demo_VITA_ckpt/
cp -rf ./web_demo/vllm_tools/vllm_file/*  ./vita_demo/lib/python3.10/site-packages/vllm/model_executor/models/
python -m web_demo.web_ability_demo demo_VITA_ckpt/

# Re-building
cp -rf ./web_demo/vllm_tools/qwen2p5_model_weight_file/*  ./demo_VITA_ckpt/
python -m web_demo.web_ability_demo demo_VITA_ckpt/

# Ngrok proxy
curl -sSL https://ngrok-agent.s3.amazonaws.com/ngrok.asc \
	| tee /etc/apt/trusted.gpg.d/ngrok.asc >/dev/null \
	&& echo "deb https://ngrok-agent.s3.amazonaws.com buster main" \
	| tee /etc/apt/sources.list.d/ngrok.list \
	&& apt update \
	&& apt install ngrok

tmux
ngrok config add-authtoken $NGROK_TOKEN
ngrok http 18806 --url=lasting-swan-large.ngrok-free.app --basic-auth "$NGROK_USERNAME:$NGROK_PASSWORD"
```