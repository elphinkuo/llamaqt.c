# llama2qt.c
Clean C language version of quantizing llama2 model and running quantized llama2 model.

The code contains some modifications (mainly about quantization and running quantized model) based on [llama.c](https://github.com/karpathy/llama2.c) (Inference Llama 2 in one file of pure C) from  Andrej Karpathy.

Simple instructions:

## 8bit quantization, grouping per layer, without block:

gcc -O3 -o quantize quantize_8bit.c -lm

./quantize {model_name}.bin

## Inference 8bit quantization

gcc -O3 -march=native runq.c -o runq -lm

./runq llama2_7b_8bit.bin -t {temperature} -p {top_p} -n {max_token} -i "{prompt}"

## 8bit quantization, grouping by 64 * 64 block:

gcc -O3 -o quantize quantize_8bit_64block.c -lm



# A quick test, using the Google colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/elphinkuo/llamaqt.c/blob/master/quantization_8bit_demo.ipynb)

More details can be found in the [README.md](README.md) .
