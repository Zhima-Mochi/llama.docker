<!-- # build docker image
docker build -t zhima1mochi2/llama:1.0 ./llama.cpp
docker push zhima1mochi2/llama:1.0 -->
# LLaMA
## put LLaMA files in models
```sh
mkdir models
```
## install Python dependencies
```py
python3 -m pip install torch numpy sentencepiece
```
## convert the 7B model to ggml FP16 format
```py
python3 llama.cpp/convert-pth-to-ggml.py models/7B/ 1
```
## run the container
```sh
docker run -it --rm -v $(pwd)/models:/models --name llama7B zhima1mochi2/llama:1.0 -m /models/7B/ggml-model-f16.bin -p "Building a website can be done in 10 simple steps:" -n 512
```