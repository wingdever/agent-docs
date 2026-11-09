  # 1) 系统层：装 CUDA 开发包（含 nvcc + 头文件，体积大；--needed 可续装）
  sudo pacman -S --needed cuda

  # 2) 确认 nvcc 可用（装完后）
  /opt/cuda/bin/nvcc --version

  # 3) 重编译 llama-cpp-python，启用 CUDA 后端（在 venv 里；保留 OpenBLAS 做 CPU 余量）
  cd ~/Projects/rag
CMAKE_ARGS="-DGGML_CUDA=ON -DGGML_BLAS=ON -DGGML_BLAS_VENDOR=OpenBLAS" \
    .venv/bin/pip install --no-cache-dir --force-reinstall --no-deps llama-cpp-python

  # 4) 改配置：把 embedding 卸载到 GPU
  #    编辑 config/settings.yaml，将 llamacpp_embed.n_gpu_layers 由 0 改为 -1






# 1) 看内核里 NVIDIA 模块和驱动版本
  nvidia-smi --query-gpu=driver_version --format=csv,noheader
  cat /proc/driver/nvidia/version 2>/dev/null

  # 2) 看 dmesg 里有没有 GPU 掉卡/复位记录
  dmesg | grep -iE "nvidia|nvrm|gpu|pci 0000:01" | tail -20

  # 3) 尝试让驱动重新枚举设备（轻量，不需重装）
  sudo rmmod nvidia_uvm nvidia_drm nvidia_modeset nvidia 2>/dev/null
  sudo modprobe nvidia
  nvidia-smi


# 修显卡驱动
第 1 步：冷重启（让 GPU 退出 FULLCHIP_RESET 状态）
  sudo reboot
  重启后先确认 GPU 复活：
  nvidia-smi   # 应能看到 RTX 4050 和驱动版本

  第 2 步：升级 NVIDIA 驱动到匹配 CUDA 13.4 的版本
  Arch 上驱动包有几个选择：
  - nvidia（闭源，主线，推荐，版本最新、匹配 CUDA 13.x）
  - nvidia-open（开源内核模块版，你当前 615 其实就是 open 内核模块）

  执行（系统级重操作，你执行）：
  sudo pacman -S --needed nvidia nvidia-utils
  # 若用 DKMS / 自定义内核还要对应的 nvidia-dkms / linux-headers
  sudo mkinitcpio -P   # 若动了 initramfs 相关
  sudo reboot
  升级后驱动版本应到 580+（CUDA 13.4 所需）。重启后 nvidia-smi 应显示新版本号。

  第 3 步：重编译 llama-cpp-python 与 CUDA 工具链对齐（可能不需要）
  cuda 包（13.4）和升级后的驱动是同代，兼容性应没问题。但重编译不是必须——之前 141MB 的 CUDA
  wheel 已经编好，只要驱动能正常提供 CUDA context，就能用。所以升级驱动后直接重试
  build_index.py 即可，不必重编。

  第 4 步：重试 embedding（用 GPU）
  cd ~/Projects/rag
  export PATH="/opt/cuda/bin:$PATH"
  .venv/bin/python scripts/build_index.py --limit 20
  # 另开终端 watch -n1 nvidia-smi 看显存

  一个保险建议：在驱动升级、GPU 稳定之前，先把 n_gpu_layers 调成小值（比如 20）试跑，确认
  CUDA context 能正常建立、不触发 FULLCHIP_RESET，再改回 -1
  全卸载。如果你同意，我可以现在就把配置从 -1 改成 20 作为首跑的保守值。

  要做两件事请你定：
  1. 我现在把 n_gpu_layers 临时改成 20（保守首跑值）可以吗？还是你坚持直接 -1 全卸载？
  2. 重启 + 升级驱动这两条命令我列出如上，由你执行；执行后把 nvidia-smi
  输出贴我，我据此判断能否进第 4 步。

  注：按 AGENTS.md 新规，重启/装驱动这类系统级重型操作我一律给命令交你执行，不自启后台。


TTY（Ctrl+Alt+F2）+ sudo systemctl poweroff


# 升级闭源驱动
Arch 上闭源驱动是 nvidia + nvidia-utils