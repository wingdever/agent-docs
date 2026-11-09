编译前置条件（gcc、OpenBLAS、cmake）
sudo pacman -S --needed --noconfirm base-devel cmake openblas 2>&1 | tail -25
   安装 cmake 与 OpenBLAS 构建依赖


## 安装编译
export PATH="/opt/cuda/bin:$PATH"
export CUDAToolkit_ROOT="/opt/cuda"
cd /home/wing/Projects/rag
CMAKE_ARGS="-DGGML_CUDA=ON -DGGML_BLAS=ON -DGGML_BLAS_VENDOR=OpenBLAS" \
   .venv/bin/pip install --force-reinstall --no-deps \
   -i https://pypi.tuna.tsinghua.edu.cn/simple llama-cpp-python


## 测试
export PATH="/opt/cuda/bin:$PATH"
  .venv/bin/python -c "import llama_cpp; print('version:', llama_cpp.__version__); print('has CUDA:', hasattr(llama_cpp, 'llama_cpp_cuda'))"

llama.cpp本体是C/C++写的推理引擎，
Python中使用需要一层绑定。