Llama model
## How to load the model
- huggingface
- llama.cpp

### Huggingface
what is the issue i faced while load the llama using hf
- model requires more than 30gb of ram to load the model
- we need to convert the pth weights that we get from meta we need to convert those into in huggingface format
so this would not be a realiable method

### llama.cpp
steps involved and issues faced while loading llama.cpp
- need to convert pth weights to ggml (it supported by llama.cpp)
code
```sh
python llama.cpp/convert.py ./models/7B # convert weights from pth to ggml format
cd llama.cpp
!make -j && ./main -m ./../{model_path} -p "what is the role sudo in linux shell" -n 512
``` 
Inference in python
```sh
export CMAKE_ARGS="-DLLAMA_OPENBLAS=on"
export FORCE_CMAKE=1
pip install llama-cpp-python --no-cache-dir
```
```py
from llama_cpp import Llama
llm = Llama(model_path=model_path)
output = llm("Q: Name the planets in the solar system? A: ", max_tokens=32, stop=["Q:", "\n"], echo=True)
print(output)
```