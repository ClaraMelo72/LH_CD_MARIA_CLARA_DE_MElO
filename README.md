# LH_CD_MARIA_CLARA_DE_MElO

 # Instruções para Instalar e Executar o Projeto
 
**Objetivo do Projeto**

Este projeto tem como objetivo prever o preço de um imóvel com base em informações como localização, tipo de UH, número de avaliações, entre outros fatores. O modelo utilizado para a previsão é um modelo de Random Forest, que foi treinado com dados de aluguel de UHs.

1. Requisitos Necessários
   
- Antes de executar o projeto, você precisará garantir que tem programas e bibliotecas instaladas, conforme consta em requirement.

2. Executando o Projeto

- Clone o repositório
- Baixe o modelo utilizando o link: O projeto já possui um modelo treinado, chamado modelo_final.pkl. Para usá-lo, será necessário instalar o gdown e fazer o download do arquivo.
- Forneça Dados de Entrada: Será necessário fornecer algumas informações sobre a UH para que você deseja prever o preço, como bairro, tipo de UH, número de avaliações, etc.
Faça a Previsão: Com base nesses dados, o modelo calculará o preço sugerido para o imóvel.

- Você pode executar utilizando o seguinte código, por exemplo:
  
  import pickle
import pandas as pd

**Carregar o modelo final**

with open('modelo_final.pkl', 'rb') as arquivo:
    modelo_carregado = pickle.load(arquivo)

**Dados de entrada para previsão (dados do apartamento)**

apartamento = {
    'bairro_group': 'Manhattan',
    'latitude': 40.75362,
    'longitude': -73.98377,
    'room_type': 'Entire home/apt',
    'minimo_noites': 1,
    'numero_de_reviews': 45,
    'calculado_host_listings_count': 2,
    'disponibilidade_365': 355
}

**Preparar os dados de entrada para a previsão**

dados_entrada = pd.DataFrame([apartamento])

**Codificar variáveis categóricas**

dados_entrada['bairro_group'], _ = pd.factorize(dados_entrada['bairro_group'])
dados_entrada['room_type'], _ = pd.factorize(dados_entrada['room_type'])

**Previsão de preço**

price_previsto = modelo_carregado.predict(dados_entrada)

**Exibir o preço previsto**

print(f'O preço sugerido para o apartamento é: {price_previsto[0]:.2f}')




