# ACIII-Trabalho-02
Repositório contendo os códigos usados para o Trabalho 02 da disciplina de Arquitetura de Computadores III. O objetivo do trabalho era implementar o Algoritmo de Tomasulo. Esse trabalho foi feito na linguagem C. 

## O que é o algoritmo de Tomasulo?
É uma técnica de escalonamento dinâmico de instruções com o objetivo de aproveitar melhor os componentes do processador, aumentar o desempenho e gerenciar conflitos de dados
## Como ele funciona?
Seu funcionamento se dá seguindo os passos:
- 1. armazena em uma fila as instruções que chegam da memória
- 2. realoca as instruções para alguma das unidades de reserva
- 3. coloca no CDB os resultados das execuções (permitindo que os resultados sejam repassados para as unidades de reserva novamente)
## Quais são os componentes do algoritmo, para que servem e como funcionam?
### 1) Buffer de Reordenamento: 
Guarda os componentes e informações necessárias para o cálculo das instruções
#### Componentes do buffer de reordenamento:
- Entry: Posição da instrução na fila
- Busy: Se a posição está ocupada ou não
- Instruction: A instrução em si
- State: Status da instrução. Pode ser:
- 1. Waiting: esperando liberação de algum recurso
- 2. Issue: instrução despachada
- 3. Executing: instrução sendo executada
- 4. Write result: instrução pronta pra ser escrita no banco de registradores
- 5. Commited: instrução escrita no banco de registradores
- Destination: Qual o registrador de destino
- Value: O cálculo feito pela instrução

### 2) Estação de Reserva:
Armazena as instruções que estão esperando a disponibilidade da UF ou dos operandos
#### Componentes da estação de reserva:
- Name: Qual unidade funcional a instrução vai utilizar
- Busy: Se a UF está ocupada ou não
- Op: Qual operação vai ser usada pela UF
- Vj | Vk: Registradores usados pela operação
- Qj | Qk: Quais estações de reserva que irão produzir os resultados
- Dest: Qual a posição da instrução na fila
- Address: Informações necessárias para o cálculo do endereço (em caso de load ou store)

### 3) Status dos Registradores: 
Mostra como estão os registradores na memória
#### Componentes do status dos registradores: 
- Field: Nome do registrador
- Reorder: Posição da instrução que o está usando na fila
- Busy: Se ele está ocupado ou não
