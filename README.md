"""# Detecção de Exoplanetas via Curvas de Luz: BLS vs. TLS

Este repositório contém o projeto de Trabalho de Conclusão de Curso (TCC) em Ciência da Computação pela **Universidade Presbiteriana Mackenzie**. O trabalho foca no processamento de sinais astronômicos para a identificação de exoplanetas, comparando a eficácia de modelos geométricos simplificados frente a modelos físicos otimizados.

## Sobre o Projeto

O objetivo principal é a análise e implementação do algoritmo **Box Least Squares (BLS)** para a detecção de trânsitos planetários em dados fotométricos do telescópio espacial **Kepler**. Como diferencial e critério de comparação, o projeto utiliza o algoritmo **Transit Least-Squares (TLS)** para superar as limitações do BLS na detecção de planetas de pequeno porte (Super-Terras) em ambientes de baixa relação sinal-ruído (SNR).

### Algoritmos Implementados:
* **Box Least Squares (BLS):** Algoritmo padrão da indústria que utiliza uma aproximação geométrica em formato de caixa (*boxcar*) para identificar quedas periódicas de brilho.
* **Transit Least-Squares (TLS):** Evolução algorítmica que incorpora parâmetros físicos de escurecimento de limbo (*limb-darkening*) e filtragem casada, permitindo maior sensibilidade para sinais de baixa amplitude.

## Tecnologias Utilizadas

O projeto foi desenvolvido em **Python 3.12**, utilizando as seguintes bibliotecas:

* `lightkurve`: Para obtenção e pré-processamento de curvas de luz.
* `transitleastsquares`: Implementação otimizada do algoritmo TLS.
* `astropy`: Manuseio de unidades astronômicas e séries temporais.
* `numpy` & `pandas`: Processamento numérico e manipulação de dados.
* `matplotlib`: Visualização de curvas de luz e periodogramas.
* `numba`: Utilizada internamente pelo TLS para compilação JIT e aceleração computacional.

##  Principais Resultados

* **Alta Precisão:** Para Júpiteres Quentes (ex: Kepler-423 b), o pipeline obteve um erro relativo de período de apenas **0,006%**.
* **Sensibilidade Superior:** O TLS demonstrou uma taxa de recuperação de sinais de **93%**, contra **76%** do BLS em cenários de trânsitos com profundidade inferior a 300 ppm.
* **Validação:** O sistema identificou com sucesso todos os alvos de teste, incluindo Super-Terras anteriormente indetectáveis pelo modelo de caixa simples.

##  Como Utilizar

1.  **Instale as dependências:**
    ```bash
    pip install lightkurve transitleastsquares astropy numpy matplotlib
    ```

2.  **Execute o Notebook:**
    O arquivo `BLS_TCC.ipynb` contém todo o pipeline, desde o download dos dados via ID do Kepler (KIC) até a geração dos periodogramas.

3.  **Limpeza de Dados:**
    O código inclui rotinas de limpeza manual via máscara booleana (`np.isfinite`) para garantir que NaNs e valores não finitos não quebrem a execução do algoritmo TLS.

##  Trabalhos Futuros

* **Paralelização em GPU:** Migração da varredura de grade para arquiteturas CUDA para ganho de performance.
* **Machine Learning:** Integração de Redes Neurais Convolucionais (CNNs) para classificação automática de candidatos e redução de falsos positivos.

---
**Autor:** Davi Martins Figueiredo  
**Instituição:** Universidade Presbiteriana Mackenzie - FCI  
"""
