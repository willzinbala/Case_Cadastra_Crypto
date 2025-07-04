# Projeto CoinCap Crypto Cadastra

Este projeto consiste em uma aplicação em Python (executada via Google Colab) que consome dados da API pública [CoinCap](https://coincap.io/) e os armazena em um banco de dados PostgreSQL hospedado na nuvem (Render). Os dados coletados incluem informações como nome da criptomoeda, símbolo, ranking, preço em USD, volume de negociação nas últimas 24h, entre outros.

O projeto foi desenvolvido com foco em boas práticas de engenharia de dados e estrutura modular, com o uso do ORM SQLAlchemy para manipulação do banco.

---

## Tecnologias Utilizadas

* [Python 3.10+](https://www.python.org/)
* [Google Colab](https://colab.research.google.com/)
* [SQLAlchemy](https://www.sqlalchemy.org/)
* [PostgreSQL (Render)](https://render.com/)
* [CoinCap REST API v3](https://docs.coincap.io/)
* [python-dotenv](https://pypi.org/project/python-dotenv/)
* [Power BI](https://www.microsoft.com/pt-br/power-platform/products/power-bi)

---

## Como Executar o Projeto

### 1. Clone o repositório (se aplicável)

Ou abra o notebook diretamente no [Google Colab](https://colab.research.google.com/).

---

### 2. Crie e edite o arquivo `.env`

Crie um arquivo chamado `.env` no seu computador com o seguinte conteúdo:

```
DATABASE_URL=postgresql://<usuario>:<senha>@<host>:<porta>/<banco>
API_KEY=<sua-api-key-CoinCap>
```

Substitua com os valores reais do seu banco e chave CoinCap. Substitua no codigo pelo nome do seu arquivo `py_env.env`

Ou simplesmente baixe o arquivo `py_env.env` e use com as minhas credenciais.

---

### 3. Faça upload do `.env` no **primeiro notebook**

No início do notebook, será solicitado:

```python
from google.colab import files
files.upload()  # selecione o arquivo .env local
```

Isso garante que suas credenciais sensíveis não fiquem no código.

---

### 4. Execute ***sequencialmente*** os notebooks

No próprio código, haverá a indicação do que cada função estará fazendo, como extrair dados da API, armazenar no banco PostgreSQL, etc...

---

## Funcionalidades Implementadas

* ✅ Conexão com API CoinCap v3 (com autenticação via `apiKey`)
* ✅ Extração de dados sobre criptomoedas e preços
* ✅ Armazenamento estruturado em PostgreSQL com SQLAlchemy
* ✅ Modelagem relacional com chave estrangeira (`crypto_prices.crypto_id → cryptocurrencies.id`)
* ✅ Consultas diretas e relacionais (`JOIN`) para exploração dos dados
* ✅ Uso de `.env` para segurança e boas práticas

---

# 📈 Dashboard com Power BI
Este dashboard interativo foi desenvolvido com Power BI e tem como objetivo apresentar uma visão consolidada e analítica sobre o mercado de criptomoedas, com dados obtidos via API pública da CoinCap e armazenados em um banco PostgreSQL.

### Objetivo do Dashboard

Visualizar as principais criptomoedas do mercado com base em preço, volume e valor de mercado.

Facilitar comparações entre as moedas mais relevantes do dia.

Entregar uma visualização clara, dinâmica e pronta para tomada de decisões.

### 📊 Dashboad na íntegra!

![image](https://github.com/user-attachments/assets/517981ec-4d21-4820-ab1b-b573af3baaba)

Baixe o arquivo .pbix e tenha acesso a este Dashboard!

### Dados históricos do Bitcoin

![image](https://github.com/user-attachments/assets/3f212b31-614c-458d-9303-d8ea330a9dc1)
(Aba Bitcoin)
Grafico de linhas mostrando a variação diária do Bitcoin. 
O limite de requisições seria facilmente atingido no plano free da API, se a extração fosse feita de várias moedas.

![image](https://github.com/user-attachments/assets/19941933-537a-498a-b271-3c12c935ff47)
Gráfico idêntico com o buscado no Google por exemplo. 😁

---

# 🚀 Futuras Melhorias

### 1. Automatização via pipeline

Criar um laço contínuo para coletar os dados automaticamente a cada intervalo de tempo:

```python
import time

while True:
    run_data_pipeline()
    time.sleep(3600)  # aguarda 1 hora
```

Ou até mesmo com agendamento usando `APScheduler`, `cron`, GitHub Actions ou `AIRFLOW`.

---

### 2. Histórico de preços (séries temporais)

Coletar e registrar preços periodicamente para análises de tendências e flutuação do mercado.

---

### 3. Validação de dados

Implementar validações para evitar duplicatas, valores inválidos ou inconsistências (ex: capitalização negativa).

---

### 4. Suporte a múltiplas fontes (ex: CoinGecko, Binance)

Permitir coleta comparativa entre diferentes APIs públicas de mercado.

---

## 🙇‍♂️ Autor

Desenvolvido por **Willian José Nogueira** como desafio técnico `end-to-end` de engenharia de dados com foco em boas práticas em Python, Banco de Dados Relacional, APIs públicas e Relatórios para tomada de decisão.
