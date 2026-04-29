# AI-LLM
## 初始化
进入Modelscope，右上角-绑定阿里云账号
<img width="2473" height="1381" alt="image" src="https://github.com/user-attachments/assets/cfa44aa3-2597-41a2-a8ff-3ff90771d4b9" />
进入我的notebook
<img width="2394" height="1353" alt="QQ20260429-233618(1)" src="https://github.com/user-attachments/assets/94fba7b2-029d-4fcb-9ae3-8e6245e8c427" />
方式一CPU环境下-启动
<img width="1821" height="1221" alt="image" src="https://github.com/user-attachments/assets/a0d1cc19-715a-4ed3-976d-fffa2fa0e151" />
等待一会，点击查看notebook，进入编辑界面
<img width="1860" height="841" alt="image" src="https://github.com/user-attachments/assets/eb9b8ff1-79e0-4581-a54b-ea67930fa761" />
## 配置环境
默认界面单击Terminal，进入命令行
<img width="1956" height="1250" alt="image" src="https://github.com/user-attachments/assets/4939b72c-2ca3-41a2-9c9c-adcef505db47" />
出现此界面即为成功：
<img width="1479" height="889" alt="image" src="https://github.com/user-attachments/assets/50b144db-d72a-4d99-8516-395116df3003" />
在此界面下依次输入如下代码：
```bash
pip install-U pip setuptools wheel
```
```bash
# 安装基础依赖（兼容 transformers 4.33.3 和 neuralchat）
pip install \
 "intel-extension-for-transformers==1.4.2" \
 "neural-compressor==2.5" \
 "transformers==4.33.3" \
 "modelscope==1.9.5" \
 "pydantic==1.10.13" \
"sentencepiece" \
 "tiktoken" \
 "einops" \
 "transformers_stream_generator" \
 "uvicorn" \
 "fastapi" \
 "yacs" \
 "setuptools_scm"
```
```bash
 # 安装 fschat（需要启用 PEP517 构建）
pip install fschat--use-pep517
```
##下载大模型


