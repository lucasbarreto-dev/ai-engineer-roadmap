# 🧪 Laboratório Prático: Hello World no LangChain via Docker

Este guia prático demonstra como estruturar e rodar um script inicial utilizando o ecossistema **LangChain** integrado ao modelo **Gemini**, isolando o ambiente de execução completamente dentro de um container **Docker**.

---

## 1. Estruturando a Pasta do Projeto

Crie uma pasta dedicada para o laboratório e acesse o diretório via terminal:

```bash
mkdir langchain-hello && cd langchain-hello

```

Dentro desta pasta, crie os três arquivos de configuração descritos abaixo: `requirements.txt`, `app.py` e `.env`.

### 📄 `requirements.txt`

Este arquivo indica ao Docker quais bibliotecas baixar. O pacote `langchain-google-genai` contém a integração oficial do LangChain com os modelos Gemini.

```text
langchain-google-genai
python-dotenv

```

### 📄 `app.py`

Este é o script principal utilizando o framework LangChain. O objetivo é carregar o ambiente, instanciar o modelo do Google e realizar uma invocação simples.

```python
import os
from langchain_google_genai import ChatGoogleGenerativeAI
from dotenv import load_dotenv

# Carrega a chave de API a partir do arquivo .env
load_dotenv()

def main():
    # Inicializa o modelo Gemini usando o LangChain
    # O modelo 'gemini-2.5-flash' é ideal por ser rápido, leve e eficiente
    llm = ChatGoogleGenerativeAI(model="gemini-2.5-flash", temperature=0.7)

    print("Enviando pergunta ao Gemini via LangChain...")

    # Executa a chamada encapsulada pelo framework
    resposta = llm.invoke("Diga 'Olá mundo' de uma forma criativa voltada para desenvolvedores Linux")

    print("\n--- Resposta do Modelo ---")
    print(resposta.content)

if __name__ == "__main__":
    main()

```

### 📄 `.env`

Para que o código funcione, precisamos injetar a chave de autenticação da API.

1. Acesse o [Google AI Studio](https://aistudio.google.com/).
2. Faça login com sua conta Google.
3. Clique em **"Get API key"** e gere uma nova chave de acesso.
4. Crie o arquivo `.env` na raiz do projeto e adicione a chave gerada (sem aspas):

```text
GOOGLE_API_KEY=sua_chave_aqui_sem_aspas

```

---

## 2. Executando o Ambiente pelo Docker

Utilizando Linux ou macOS, podemos usar o utilitário nativo `$(pwd)` para mapear o diretório atual diretamente para dentro do container, sem a necessidade de instalar o Python localmente na máquina host.

Usaremos a imagem oficial leve do Python (`python:3.11-slim`). Execute o comando abaixo no terminal, de dentro da pasta do projeto:

```bash
docker run --rm -it \
  -v "$(pwd)":/usr/src/app \
  -w /usr/src/app \
  --env-file .env \
  python:3.11-slim \
  sh -c "pip install --no-cache-dir -r requirements.txt && python app.py"

```

### 🔍 O que esse comando faz?

* `--rm`: Remove o container automaticamente após o encerramento da execução, evitando o acúmulo de lixo no sistema operacional.
* `-it`: Roda o container em modo interativo, permitindo visualizar os logs do terminal em tempo real.
* `-v "$(pwd)":/usr/src/app`: Monta um volume mapeando a pasta atual do seu computador para dentro do diretório do container.
* `-w /usr/src/app`: Define o diretório de trabalho padrão interno onde os comandos serão executados.
* `--env-file .env`: Injeta o arquivo de configuração de forma segura, disponibilizando a variável `GOOGLE_API_KEY` direto no container.
* `sh -c "..."`: Dispara um interpretador Shell para instalar as dependências do `requirements.txt` em tempo de execução e, imediatamente após, rodar o script `app.py`.

```

---
