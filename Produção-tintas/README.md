# 🧪 Projeto de Controle Sequencial: Sistema de Processamento por Batelada

## 🎯 Objetivo do Projeto

Este projeto consiste na implementação da lógica de controle para um sistema de produção por batelada (batch), especificamente para um tanque misturador com controle de nível e temperatura.

O objetivo é garantir a execução correta de uma sequência operacional pré-definida, utilizando a modelagem por **Rede de Petri** e a implementação no ambiente de um Controlador Lógico Programável (CLP) via **Diagrama Ladder (LD)**.

---

## 🛠️ Detalhes da Implementação

* **Plataforma de Simulação:** CODESYS Development System (ou ambiente similar de CLP)
* **Linguagem de Controle:** Diagrama Ladder (LD)
* **Metodologia:** Controle Sequencial baseado em Rede de Petri

---

## ⚙️ Sequência de Operação (Ciclo Completo)

O processo opera em uma sequência de quatro etapas principais:

### 1. Enchimento (Manual)
* **Início:** O operador inicia manualmente o bombeamento dos dois produtos primários através de acionamentos independentes (**Start 1** e **Start 2**).
* **Parada:** O operador pode parar as bombas manualmente (**Stop 1** e **Stop 2**) a qualquer momento, ou o sistema para automaticamente ao atingir o nível máximo.

### 2. Mistura e Aquecimento (Automático)
* **Transição:** Acionada automaticamente ao detectar o **Nível Alto (High Level)**.
* **Ações:** As bombas de enchimento são desligadas. O motor do misturador (**Mixer Motor**) é ligado e a válvula de aquecimento (**Steam Valve**) é aberta.
* **Duração:** O processo é temporizado para **3 minutos**.

### 3. Drenagem (Automático)
* **Transição:** Ocorre após o término do tempo de mistura (3 minutos).
* **Ações:** O misturador e o aquecimento são desligados. A **Válvula de Dreno** é aberta e a **Bomba de Dreno** é ligada para esvaziar o tanque.

### 4. Finalização (Temporizada)
* **Transição:** Acionada ao detectar o **Nível Baixo (Low Level)** no tanque.
* **Ações:** O sistema aguarda um tempo adicional de **1 minuto** para garantir a drenagem completa.
* **Fim do Ciclo:** Todos os atuadores são desligados, e o sistema é reiniciado para um novo ciclo de produção.

---

## 📂 Organização do Repositório

* **`README.md`**: Este documento de descrição do projeto.
* **`src/`**: Contém o código-fonte do projeto Ladder (ex: `codesys_project.pro`).
* **`docs/`**: Inclui diagramas de referência, como a Rede de Petri e o enunciado.

---

## 🚀 Guia de Simulação

Para testar o controle sequencial:

1.  Carregue o projeto na plataforma CODESYS.
2.  Inicie a simulação (modo **Run**).
3.  Simule as entradas (**Start**, **Stop**, **High Level**, **Low Level**) para forçar as transições e observar a ativação das saídas (Bombas, Mixer, Válvulas) conforme a sequência de controle.
