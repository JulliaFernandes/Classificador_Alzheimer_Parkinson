<h1 align="center" font-size="200em"><b>🧠 Classificação de Alzheimer, Parkinson e Controles Normais - Análise Comparativa de Modelos</b></h1>

<div align = "center" >

[![requirement](https://img.shields.io/badge/IDE-Visual%20Studio%20Code-informational)](https://code.visualstudio.com/docs/?dv=linux64_deb)
![Linguagem](https://img.shields.io/badge/Linguagem-Python-orange)
</div>

## 📊 Visão Geral do Projeto

Este projeto implementa e compara três algoritmos de machine learning para classificação de imagens médicas em três categorias:

- **AD (Alzheimer Disease)** - Doença de Alzheimer  
- **CONTROL** - Controles normais/saudáveis  
- **PD (Parkinson Disease)** - Doença de Parkinson  

### Algoritmos Comparados:

- **KNN (K-Nearest Neighbors)**  
- **SVM (Support Vector Machine)**  
- **CNN (Convolutional Neural Network)**  

---

## 🔬 Metodologia

### Pré-processamento dos Dados

- **Redimensionamento**: Imagens convertidas para 64x64 pixels  
- **Conversão**: RGB → Escala de cinza → Vetor 1D (4096 features)  
- **Normalização**: `StandardScaler` aplicado aos dados  
- **Encoding**: `LabelEncoder` para as 3 classes (AD=0, CONTROL=1, PD=2)

### Classes do Dataset

- **AD (Alzheimer)** - Padrões cerebrais associados à demência  
- **CONTROL (Normal)** - Cérebros saudáveis como baseline  
- **PD (Parkinson)** - Padrões neurológicos da doença de Parkinson  

---

## 🔧 Modelos Implementados

### 1. K-Nearest Neighbors (KNN)

- **Otimização**: `GridSearchCV` com 5-fold cross-validation  
- **Parâmetros testados**:
  - `n_neighbors`: [3, 5, 7, 9, 11]
  - `weights`: ['uniform', 'distance']
  - `metric`: ['euclidean', 'manhattan', 'cosine']

### 2. Support Vector Machine (SVM)

- **Otimização**: `GridSearchCV` com 3-fold cross-validation  
- **Parâmetros testados**:
  - `C`: [0.1, 1, 10]
  - `kernel`: ['linear', 'rbf']
  - `gamma`: ['scale', 'auto']

### 3. Convolutional Neural Network (CNN)

- **Arquitetura**:
  ```
  Conv2D (32 filtros) → MaxPooling2D  
  Conv2D (64 filtros) → MaxPooling2D  
  Conv2D (64 filtros) → Flatten  
  Dense (64 neurônios) → Dropout (0.5)  
  Dense (3 neurônios, softmax)
  ```
- **Treinamento**: 20 épocas, `batch_size=32`

---

## 📈 Resultados

### Tabela de Performance

| Modelo | Accuracy | F1-Score | Recall | Kappa |
|--------|----------|----------|--------|--------|
| **CNN** | 0.7430 | 0.7397 | 0.7430 | 0.5216 |
| **KNN** | 0.7394 | 0.7373 | 0.7394 | 0.5130 |
| **SVM** | 0.7364 | 0.7341 | 0.7364 | 0.5069 |

---

## 🏆 Ranking dos Modelos

- 🥇 **CNN** - Accuracy: **74.30%**
- 🥈 **KNN** - Accuracy: **73.94%**
- 🥉 **SVM** - Accuracy: **73.64%**

---

## 🔍 Análise dos Resultados

### Performance Geral

- **Diferenças pequenas**: Todos os modelos apresentaram performance similar (~73–74%)  
- **CNN ligeiramente superior**: Melhor em todas as métricas, mas margem pequena (0.66%)  
- **Consistência**: F1-Score e Recall praticamente iguais ao Accuracy (dataset aparentemente balanceado)

---

### Análise por Classe (baseada nas Curvas ROC)

#### Classe PD (Parkinson) - Melhor Discriminação

- CNN: AUC = 0.99 (excelente)  
- SVM: AUC = 0.98 (excelente)  
- KNN: AUC = 0.96 (muito bom)  
- **Conclusão**: Parkinson é a classe mais facilmente distinguível

#### Classe AD (Alzheimer)

- SVM: AUC = 0.87 (bom)  
- KNN: AUC = 0.86 (bom)  
- CNN: AUC = 0.85 (bom)  
- **Conclusão**: Performance moderada, mas consistente

#### Classe CONTROL (Normal)

- **CONTROL vs outras**: Performance intermediária  
- **Desafio**: Maior confusão entre controles normais e pacientes com Alzheimer

---

### Análise das Matrizes de Confusão

#### Padrões Observados:

- **PD (Parkinson)**: Melhor classificação em todos os modelos  
  - CNN: 34/61 casos PD classificados corretamente  
  - SVM: 40/61 casos PD classificados corretamente  
  - KNN: 33/61 casos PD classificados corretamente  

- **Maior Confusão**: Entre AD (Alzheimer) e CONTROL  
  - Indica sobreposição de características entre cérebros com Alzheimer inicial e controles  
  - Desafio clínico real refletido nos dados  
  - CNN: Melhor balance geral entre as três classes

---

### Curvas Precision-Recall

- **PD**: Melhor Average Precision em todos os modelos (0.85–0.87)  
- **AD e CONTROL**: Performance similar (~0.81–0.86)  
- **Implicação**: Sistema mais confiável para detectar Parkinson

---

## 🎯 Conclusões

### Principais Achados

- **Parkinson mais distinguível**: Todos os modelos tiveram excelente performance para PD  
- **Desafio AD vs CONTROL**: Maior dificuldade em separar Alzheimer de controles normais  
- **CNN ligeiramente superior**: Mas diferença pequena sugere que features simples são suficientes  
- **Kappa ~0.5**: Indica concordância moderada, típica de problemas médicos complexos  

---

### Implicações Clínicas

- **Triagem de Parkinson**: Sistema promissor com alta precisão (AUC > 0.96)  
- **Alzheimer vs Normal**: Necessita melhorias - desafio conhecido na medicina  
- **Aplicação prática**: Poderia auxiliar em triagem inicial, especialmente para Parkinson

---

## Contato
<div>
 <br><p align="justify"> Jullia Fernandes</p>
 <a href="https://t.me/JulliaFernandes">
 <img align="center" src="https://img.shields.io/badge/Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white"/> 
 </div>
<a style="color:black" href="mailto:julliacefet@gmail.com?subject=[GitHub]%20Source%20Dynamic%20Lists">
✉️ <i>julliacefet@gmail.com</i>
</a>
   
---
   
> ⚠️ **Aviso Importante**: Este é um estudo experimental para fins educacionais e de pesquisa.  
> Os resultados **NÃO** devem ser utilizados para diagnóstico médico real sem validação clínica adequada e supervisão médica especializada.
