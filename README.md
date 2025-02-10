# 🚀 Machine Learning Automatizado no Azure Machine Learning  

## 📌 Visão Geral  
Este repositório contém um guia prático para explorar o **Machine Learning Automatizado no Azure Machine Learning**. O objetivo é treinar, avaliar e implantar um modelo de machine learning de forma automatizada.  

---

## 📂 Sumário  
1. [Configuração do Workspace no Azure Machine Learning](#configuração-do-workspace-no-azure-machine-learning)  
2. [Treinamento com Machine Learning Automatizado](#treinamento-com-machine-learning-automatizado)  
3. [Análise do Melhor Modelo](#análise-do-melhor-modelo)  
4. [Implantação e Testes](#implantação-e-testes)  
5. [Limpeza de Recursos](#limpeza-de-recursos)  

---

## 🔧 Configuração do Workspace no Azure Machine Learning  

Para iniciar, é necessário criar um **Workspace no Azure Machine Learning**.  

### 📌 Passos:  
1. Acesse o [Portal do Azure](https://portal.azure.com).  

![image](https://github.com/user-attachments/assets/074f1262-3aee-49ed-b4e2-506c1ea34ad3)


2. Crie um **novo recurso** do Azure Machine Learning com as seguintes configurações:  

![image](https://github.com/user-attachments/assets/6d6b834f-c8e4-434b-ade8-7f530603e0a1)

   - **Assinatura**: Sua assinatura do Azure  
   - **Grupo de recursos**: Criar ou selecionar um existente  
   - **Nome do workspace**: Nome exclusivo  
   - **Região**: Região mais próxima  
   - **Conta de armazenamento**: Criada automaticamente  
   - **Cofre de chaves**: Criado automaticamente  
   - **Application Insights**: Criado automaticamente  
3. Aguarde a criação e acesse o **Estúdio do Azure Machine Learning**:  
   - [🔗 Acessar Estúdio do Azure ML](https://ml.azure.com)  
4. Confirme se o workspace foi criado corretamente.  

---

## 📊 Treinamento com Machine Learning Automatizado  

O **Machine Learning Automatizado** permite testar vários modelos e algoritmos para encontrar o mais eficiente.  

### 📌 Passos:  
1. Acesse a aba **ML Automatizado** no Azure ML Studio.  
2. Configure o **trabalho de treinamento**:  
   - **Nome do trabalho**: `mslearn-bike-automl`  
   - **Tipo de tarefa**: Regressão  
   - **Conjunto de dados**: Criar um novo conjunto de dados com os detalhes do aluguel de bicicletas  
   - **Coluna de destino**: `alugueis`  
3. Configure os **modelos permitidos**:  
   - **RandomForest**  
   - **LightGBM**  
4. Defina os **parâmetros do treinamento**:  
   - **Métrica Primária**: `NormalizedRootMeanSquaredError`  
   - **Avaliações máximas**: `3`  
   - **Tempo limite do experimento**: `15 minutos`  
   - **Computação**: Máquina virtual `Standard_DS3_V2`  

🔄 Aguarde a execução do treinamento.  

---

## 📈 Análise do Melhor Modelo  

Após a conclusão do experimento, avalie o **melhor modelo** encontrado.  

### 📌 Passos:  
1. Acesse a aba **Visão Geral** do trabalho concluído.  
2. Identifique o **algoritmo vencedor** e clique no nome para visualizar detalhes.  
3. Vá até a aba **Métricas** e analise:  
   - **Gráfico Residual**  
   - **Gráfico Predito vs Real**  

---

## 🚀 Implantação e Testes  

Agora, vamos **implantar e testar** o modelo treinado.  

### 📌 Passos para Implantação:  
1. Vá até a aba **Modelo** e selecione **Implantar**.  
2. Escolha a opção **Ponto de Extremidade em Tempo Real**.  
3. Configure:  
   - **Máquina virtual**: `Standard_DS3_V2`  
   - **Número de instâncias**: `3`  
4. Aguarde a conclusão da implantação.  

### 📌 Teste do Modelo Implantado  
1. Acesse a aba **Pontos de Extremidade**.  
2. No campo de **entrada**, insira o seguinte JSON:  

```json
{
  "input_data": {
    "columns": [
      {
        "day": 1,
        "mnth": 1,
        "year": 2022,
        "season": 2,
        "holiday": 0,
        "weekday": 1,
        "workingday": 1,
        "weathersit": 2,
        "temp": 0.3,
        "atemp": 0.3,
        "hum": 0.3,
        "windspeed": 0.3
      }
    ],
    "index": [],
    "data": []
  }
}
