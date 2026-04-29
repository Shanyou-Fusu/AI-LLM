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
## 下载大模型
命令行输入如下代码以切换到当前目录
```bash
cd /mnt/data
```
以下是要运行的大模型，建议每次只下载一个，运行完毕后再运行下一个
此处全部列出，实际操作时分别下载即可
### Qwen
```bash
git clone https://www.modelscope.cn/qwen/Qwen-7B-Chat.git
```
### Chatglm3
```bash
git clone https://www.modelscope.cn/ZhipuAI/chatglm3-6b.git
```
### Baichuan
```bash
git clone https://www.modelscope.cn/baichuan-inc/Baichuan2-7B-Chat.git
```
### 后文均以chatglm3为例。
clone完毕后出现如下界面即为成功：
<img width="365" height="78" alt="image" src="https://github.com/user-attachments/assets/780cfbd8-1142-48e7-bbf9-57db0118bd40" />
此外还可以再clone完毕后使用ls命令查看是否成功。
<img width="415" height="43" alt="image" src="https://github.com/user-attachments/assets/476103ec-7b6f-4bb5-9a59-45004464d645" />
## 编写代码
下载完成后，在左侧文件区右键-New File，冲命名为任意后缀为.py的文件均可
<img width="679" height="678" alt="image" src="https://github.com/user-attachments/assets/1baf7a15-c9e5-44c6-a26e-3b42c98a343f" />
双击打开文件，进入编辑页面，输入以下代码
```bash
from transformers import TextStreamer, AutoTokenizer, AutoModelForCausalLM
model_name = "/mnt/workspace/chatglm3-6b" # 本地路径
prompt = "请说出以下两句话区别在哪里？1、冬天：能穿多少穿多少2、夏天：能穿多少穿多少"
tokenizer = AutoTokenizer.from_pretrained(
    model_name,
    trust_remote_code=True
)
model = AutoModelForCausalLM.from_pretrained(
    model_name,
    trust_remote_code=True,
    torch_dtype="auto" # 自动选择 float32/float16（根据模型配置）
).eval()
inputs = tokenizer(prompt, return_tensors="pt").input_ids
streamer = TextStreamer(tokenizer)
outputs = model.generate(inputs, streamer=streamer, max_new_tokens=300)
```
<img width="1311" height="514" alt="image" src="https://github.com/user-attachments/assets/6aee6080-53fb-4804-a275-3879fcdc4400" />
保存后返回命令行界面，输入
```bash
python run_chatglm3_cpu.py
```
等待结果出现。
<img width="416" height="71" alt="image" src="https://github.com/user-attachments/assets/a52d6406-1ada-482b-956e-521cd94e5e26" />
记录结果，并多次修改代码中"prompt"部分的问题，记录不同结果。




