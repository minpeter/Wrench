# setup axolotl with docker

```sh
docker run --privileged --gpus '"all"' --shm-size 10g --rm -it \
  --name axolotl --ipc=host \
  --ulimit memlock=-1 --ulimit stack=67108864 \
  --mount type=bind,src="${PWD}",target=/workspace/axolotl \
  -v /data/huggingface:/root/.cache/huggingface \
  -e "CUDA_VISIBLE_DEVICES=5" \
  -e "HF_TOKEN=$HF_TOKEN" \
  -e "WANDB_API_KEY=$WANDB_API_KEY" \
  axolotlai/axolotl:main-latest
```

after entering the container, run the following command to install axolotl:

```sh
pip3 install "axolotl[flash-attn,deepspeed] @ git+https://github.com/OpenAccess-AI-Collective/axolotl"
huggingface-cli whoami # check huggingface login status
wandb login # check wandb login status
```
