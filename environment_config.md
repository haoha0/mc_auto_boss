1. ### 下载本项目
    推荐使用wakening最新维护的项目，[mc_auto_boss](https://github.com/wakening/mc_auto_boss)
    安装git，打开cmd或powershell执行以下命令下载项目
    ```shell
    git clone https://github.com/wakening/mc_auto_boss.git
    cd mc_auto_boss
    ```

2. ### 安装 conda
    下载安装anaconda：
    ```shell
    conda create -n mc python=3.10
    conda activate mc
    ```

3. ### 安装 CUDA 12
    #### 本地安装：
    下载 CUDA 12.x：https://developer.nvidia.com/cuda-toolkit-archive    
    如CUDA 12.6，安装，自定义，取消勾选其他组件，只勾选安装CUDA
    
    下载cuDNN v8.9.7, for CUDA 12.x
    https://developer.nvidia.com/rdp/cudnn-archive    
    解压zip文件，将所有文件夹（如：bin include lib）复制到路径内：C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v12.6\

    #### conda中安装（推荐）：
    先激活mc环境：
    以cuda 12.6为例：注意不能用最新的CUDNN 9.x版本，因为paddle编译用的是8.x版本。
    ```shell
    conda install -c nvidia cuda-toolkit=12.6.0
    conda install -c conda-forge cudnn=8.9.7.29
    ```

4. ### 安装依赖
   打开cmd或powershell执行以下命令：    
   1.安装paddlepaddle-gpu，官方地址：[https://www.paddlepaddle.org.cn/install/quick](https://www.paddlepaddle.org.cn/install/quick)
   打开网址后，    
   选择2.6 windows pip 英伟达 CUDA12.0，复制链接执行    
  （此链接可能随官方更新失效，建议使用官网最新的链接）：
   ```shell
   python -m pip install paddlepaddle-gpu==2.6.1.post120 -f https://www.paddlepaddle.org.cn/whl/windows/mkl/avx/stable.html
   ```
    2.验证安装结果：
    安装完成后，conda激活mc环境，输入`python`，然后输入`import paddle`，再输入`paddle.utils.run_check()`，如果出现`PaddlePaddle is installed successfully!`，说明已成功安装。

    3.安装onnxruntime-gpu：
   ```shell
   pip install onnxruntime-gpu==1.18.0 --extra-index-url https://aiinfra.pkgs.visualstudio.com/PublicPackages/_packaging/onnxruntime-cuda-12/pypi/simple/
   ```
    4.安装剩余依赖：
    ```shell
   pip install --upgrade -r requirements_gpu_cuda12.txt -i https://pypi.tuna.tsinghua.edu.cn/simple
   ```