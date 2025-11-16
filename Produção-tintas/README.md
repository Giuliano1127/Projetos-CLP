# 🎨 Projeto de Controle de Processo: Fabricação de Tintas

## 🎯 Objetivo do Projeto

Este projeto demonstra a lógica de controle para um sistema de produção de **tintas** em um reator de mistura. O controle sequencial é modelado usando a **Rede de Petri** e implementado em **Diagrama Ladder (LD)** para simulação em ambiente de CLP.

O foco é gerenciar as etapas de enchimento, mistura (incluindo aquecimento) e drenagem do produto final.

---

## 🛠️ Detalhes da Implementação

* **Processo:** Produção de Tintas (Mistura e Aquecimento)
* **Plataforma de Simulação:** CODESYS Development System (ou software equivalente)
* **Linguagem de Controle:** Diagrama Ladder (LD)
* **Metodologia:** Lógica de Controle Sequencial (Modelagem por Rede de Petri)

---

## ⚙️ Sequência de Produção

O ciclo de produção é dividido nas seguintes etapas sequenciais:

### 1. Enchimento (Operação Manual)
* O operador inicia o enchimento do tanque acionando manualmente as **Bombas de Produto (Pump 1 e Pump 2)**.
* As bombas podem ser paradas manualmente a qualquer momento pelo operador.

### 2. Mistura e Aquecimento (Automático)
* **Transição:** Ocorre automaticamente quando o sensor de **Nível Alto** é atingido. As bombas de entrada são desligadas.
* **Ações:** O **Motor do Misturador** é ligado e a **Válvula de Vapor** é aberta para aquecer a mistura.
* **Duração:** Esta fase é controlada por um temporizador de **3 minutos**.

### 3. Drenagem (Automático)
* **Transição:** Ocorre após a conclusão do tempo de mistura (3 minutos).
* **Ações:** O misturador e o aquecimento são desligados. A **Válvula de Dreno** é aberta e a **Bomba de Dreno** é ligada para descarregar o produto final (a tinta).

### 4. Finalização do Ciclo (Temporizada)
* **Transição:** Acionada ao detectar o **Nível Baixo** no tanque.
* **Ações:** O sistema aguarda **1 minuto** adicional para garantir a drenagem completa da linha e do tanque.
* **Fim do Ciclo:** Todos os atuadores são desligados. O sistema entra em estado de repouso, pronto para iniciar a produção de um novo lote.

##Imagens


<img width="1366" height="748" alt="image" src="https://github.com/user-attachments/assets/74ac8136-2a34-4542-b85f-9fc5c5b88c7f" />


<img width="1366" height="432" alt="image" src="https://github.com/user-attachments/assets/556b4aba-ecba-43aa-a946-f033a8dd3e25" />


<img width="1366" height="573" alt="image" src="https://github.com/user-attachments/assets/0c6ce568-39a1-4018-865e-ef4af71d05e9" />


<img width="1362" height="398" alt="image" src="https://github.com/user-attachments/assets/6b3d28df-7f67-44f3-beb1-ef9354943fbb" />

---

## 📂 Arquivo do projeto.

[(ARQUIVOS.PROJ)Projeto_Tintas.zip](https://github.com/user-attachments/files/23570763/ARQUIVOS.PROJ.Projeto_Tintas.zip)

---

## 🚀 Guia Rápido de Simulação

Para validar a lógica de controle:

1.  Carregue o projeto na plataforma de simulação (CODESYS ou equivalente).
2.  Coloque o sistema em modo de execução (*Run*).
3.  Simule o acionamento dos comandos manuais de **Start/Stop** e dos sensores de **Nível (Alto e Baixo)** para testar o avanço automático entre as etapas do processo. 
