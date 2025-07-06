# 同步代码，安装依赖
git clone https://github.com/wyyt/AGPicCompress.git
cd AGPicCompress ## 进入 AGPicCompress 目录
conda install --file requirements.txt
或直接使用pip安装依赖：
pip install -r requirements.txt
因为 mozjpeg_lossless_optimization 这个包在conda中没有，所以需要使用pip安装。

# 启动程序 
## 1.使用命令行
```
cd AGPicCompress ## 进入 AGPicCompress 目录
python ImageCompressor.py --help
 python ImageCompressor.py <input_file> -o <output_file> -q <quality>
 python ImageCompressor.py ./images/test.jpg -o test.jpg -q 80
 python ImageCompressor.py ./images/test.png -o test.png -q 80
 python ImageCompressor.py ./images/照片质量高.jpg -o ./images/照片质量高_compressed.jpg -q 80
 python ImageCompressor.py ./images/照片质量标准.jpg -o ./images/照片质量标准_compressed.jpg -q 80
 python ImageCompressor.py ./images/照片质量低.jpg -o ./images/照片质量低_compressed.jpg -q 80
```
## 2. 启动 Web Demo 服务
    ```shell
    cd AGPicCompress ## 进入 AGPicCompress 目录
    python -m backend.main 
    ```
    然后访问对应的地址使用，默认地址为 `http://localhost:8089/`
    ![web_demo](../images/web_demo.png)

---

# 打成独立程序发布
```
pyinstaller --onefile --name ImageCompressor ImageCompressor.py --add-binary "ext/pngquant.exe;ext" --hidden-import _cffi_backend --hidden-import cffi
```
使用方法：
ImageCompressor.exe ../images/照片质量高.jpg -o ./照片质量高_compressed.jpg -q 80
ImageCompressor.exe ../images/test.png -o ./test_compressed.png -q 80
