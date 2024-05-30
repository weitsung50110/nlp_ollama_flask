# nlp_ollama_flask
Using ollama nlp LLM to combine with flask to let the LLM can be shown on web.

## Docker
#### 1. 先去把image pull下來

    docker pull weitsung50110/ollama_flask

weitsung50110/ollama_flask裡面我已經把ollama和flask都安裝完成了，並把llama3和llama2也已經安裝在本地了。

#### 2. Run image in order to generate container
 ~/trans_project掛載到容器內的app資料夾下面， ~/trans_project是在ubuntu中的寫法，若你是windows請自行更改並創建資料夾。

        docker run -d \
        -v ollama:/root/.ollama \
        -v ~/trans_project:/app \
        -p 11434:11434 \
        --name ollama_flask \
        weitsung50110/ollama_flask:1.0

#### 3. 進入ollama_flask容器conatiner裡面

        docker exec -it ollama_flask /bin/bash

- 若想要單獨使用ollama看看可以輸入

      ollama run llama3

#### 4. 若想要使用ollama和flask結合的web網頁版nlp llm功能，請先進入 /app/flask 當中

    cd /app/flask

#### 5. 會在/flask資料夾下面看到app2.py，直接輸入以下指令

    python3 app2.py

#### 6. 跑成功就可以看到print以下畫面

    root@4be643ba6a94:/app/flask# python3 app2.py
     * Serving Flask app 'app2'
     * Debug mode: on
    INFO:werkzeug:WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
     * Running on all addresses (0.0.0.0)
     * Running on http://127.0.0.1:5000
     * Running on http://172.17.0.2:5000
    INFO:werkzeug:Press CTRL+C to quit
    INFO:werkzeug: * Restarting with watchdog (inotify)
    WARNING:werkzeug: * Debugger is active!
    INFO:werkzeug: * Debugger PIN: 285-152-236

我測試網址172.17.0.2:5000可以看到執行的成果。
