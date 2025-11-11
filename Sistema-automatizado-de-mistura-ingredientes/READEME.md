# Sistema Automatizado de Mistura de Ingredientes

## 📘 Descrição do Projeto
Este projeto consiste na automação de um processo de mistura industrial utilizando **Codesys**. O sistema realiza o controle sequencial de válvulas e motor de agitação conforme um ciclo lógico definido, simulando um processo automatizado de dosagem e mistura de componentes líquidos.

O objetivo é demonstrar a aplicação de **lógica ladder** para controle de processos, utilizando **temporizações (TON)** e **sequenciamento automático** a partir de uma única entrada de comando.

<img width="457" height="573" alt="IOGURTE" src="https://github.com/user-attachments/assets/1012a84f-9355-4711-a3ff-465e175a93a3" />

---

## ⚙️ Funcionamento do Processo

O sistema é iniciado pelo **botão de partida (B1)** e executa automaticamente a sequência de enchimento, mistura e descarga conforme descrito abaixo:

1. **Início do processo** com o acionamento do botão B1.  
2. **Abertura da válvula de entrada geral (VE)** do tanque.  
3. **Abertura sequencial das válvulas de insumo:**  
   - V1: Entrada 1 → 20 segundos  
   - V2: Entrada 2 → 15 segundos  
4. **Acionamento do motor do agitador (MA)**.  
5. **Abertura das demais válvulas:**  
   - V3: Entrada 3 → 5 segundos  
   - V4: Entrada 4 → 10 segundos  
6. **Manutenção do agitador ligado por 30 segundos** após a adição de todos os insumos.  
7. **Desligamento do agitador (MA)**.  
8. **Abertura da válvula de saída (VS)** por 40 segundos para descarga do tanque.  
9. **Fechamento de todas as válvulas** e término do ciclo.

---



---

## 🧠 Lógica Implementada

A lógica foi desenvolvida  em **diagrama ladder** no **Codesys**, utilizando como base a **rede de petri**:

<img width="1366" height="768" alt="IOGURTE_RP" src="https://github.com/user-attachments/assets/7148b8e0-158d-4042-bf9c-ebd8f930c316" />

## Ladder no Codesys

<img width="1366" height="634" alt="Ladder_iogurte 1" src="https://github.com/user-attachments/assets/7a2fc3f3-9cb4-4bdd-9196-f19421d67abc" />

<img width="1366" height="694" alt="Ladder_iogurte 2" src="https://github.com/user-attachments/assets/2f9df054-53da-4a78-a9f7-c2e999f90b6f" />



- **Temporizadores TON** para definir tempos de abertura das válvulas e tempo de agitação;  
- **Sinais de intertravamento** para garantir a sequência correta;  
- **Controle automático** do ciclo completo a partir de um único comando de início.
  


---

## 🛠️ Ferramentas Utilizadas

- **VisuObj.net** - Rede de Petri Base;
- **Codesys** – desenvolvimento do programa ladder;  
- **Controlador virtual PLC** – simulação do processo;  
- **Ambiente de testes** – visualização do ciclo e temporizações.

---

## 📈 Resultados Esperados

- Execução sequencial totalmente automatizada.  
- Controle preciso de tempos e acionamentos.  
- Demonstração de um processo industrial automatizado com lógica ladder.  

---

## Arquivos Projeto

[(ARQUIVOS.PROJ)Projeto_Iogurte.zip](https://github.com/user-attachments/files/23487824/ARQUIVOS.PROJ.Projeto_Iogurte.zip)

