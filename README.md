# pl_oficina_mecanica

### Descrição do Projeto Lógico: **Oficina Mecânica**

O modelo conceitual apresentado descreve o funcionamento de um sistema para gerenciar operações de uma oficina mecânica. O sistema engloba clientes, veículos, ordens de serviço (OS), peças, serviços, mecânicos e equipes. Abaixo está uma explicação detalhada sobre cada entidade, seus atributos e os relacionamentos entre elas:

---

#### **1. Entidades Principais:**

1. **Cliente**
   - Representa os clientes que possuem veículos cadastrados na oficina.
   - **Atributos:**
     - `idCliente`: Identificador único do cliente.
     - `Nome`: Nome do cliente.
     - `Telefone`: Contato telefônico do cliente.
     - `Endereço`: Endereço do cliente.
   - **Relacionamentos:**
     - Um cliente pode possuir *um ou mais veículos*.

2. **Veículo**
   - Representa os veículos cadastrados no sistema.
   - **Atributos:**
     - `idVeículo`: Identificador único do veículo.
     - `Placa`: Placa do veículo.
     - `Modelo`: Modelo do veículo.
     - `Ano`: Ano de fabricação do veículo.
     - `Cliente_idCliente`: Identificador do cliente ao qual o veículo pertence.
   - **Relacionamentos:**
     - Cada veículo está relacionado a *um cliente*.
     - Cada veículo pode possuir *uma ou mais OS*.

3. **OS (Ordem de Serviço)**
   - Representa uma ordem de serviço associada a um veículo.
   - **Atributos:**
     - `idOS`: Identificador único da OS.
     - `Data emissão`: Data de emissão da OS.
     - `Valor total`: Valor total da OS.
     - `Status`: Status da ordem (Ex: "Em andamento", "Concluída").
     - `Data conclusão`: Data de conclusão da OS.
     - `Veículo_idVeículo`: Identificador do veículo relacionado.
   - **Relacionamentos:**
     - Cada OS está associada a *um veículo*.
     - Cada OS pode englobar *múltiplos serviços e peças*.

4. **Serviço**
   - Representa serviços realizados em veículos.
   - **Atributos:**
     - `idServiço`: Identificador único do serviço.
     - `Descrição`: Descrição do serviço (Ex: "Troca de óleo").
     - `Valor mão de obra`: Custo do serviço.
     - `Status`: Status do serviço (Ex: "Concluído", "Pendente").
   - **Relacionamentos:**
     - Um serviço pode estar associado a *uma ou mais OS*.

5. **Peça**
   - Representa peças utilizadas nos serviços realizados.
   - **Atributos:**
     - `idPeça`: Identificador único da peça.
     - `Nome peça`: Nome da peça (Ex: "Filtro de óleo").
     - `Valor peça`: Preço unitário da peça.
   - **Relacionamentos:**
     - Cada peça pode ser usada em *uma ou mais OS*.

6. **Mecânico**
   - Representa os mecânicos que realizam os serviços.
   - **Atributos:**
     - `idMecânico`: Identificador único do mecânico.
     - `Nome`: Nome do mecânico.
     - `Endereço`: Endereço do mecânico.
     - `Especialidade`: Área de especialização (Ex: "Suspensão", "Freios").
   - **Relacionamentos:**
     - Um mecânico pode participar de *uma ou mais OS*.
     - Mecânicos podem ser organizados em equipes.

7. **Equipe**
   - Representa equipes de trabalho formadas por mecânicos.
   - **Atributos:**
     - `idEquipe`: Identificador único da equipe.
     - `Nome equipe`: Nome da equipe.
   - **Relacionamentos:**
     - Uma equipe pode incluir *um ou mais mecânicos*.

---

#### **Entidades Associativas e Relacionamentos:**

1. **Serviço_has_OS**
   - Associa serviços a ordens de serviço específicas.
   - **Atributos:**
     - `Serviço_idServiço`: Identificador do serviço.
     - `OS_idOS`: Identificador da OS.
     - `OS_Veículo_idVeículo`: Identificador do veículo associado à OS.

2. **Peça_has_OS**
   - Registra peças utilizadas em ordens de serviço.
   - **Atributos:**
     - `ID`: Identificador único.
     - `Peça_idPeça`: Identificador da peça.
     - `OS_idOS`: Identificador da OS.
     - `Quantidade`: Quantidade utilizada da peça.
     - `Valor total`: Valor total baseado na quantidade.

3. **Equipe_has_Mecânico**
   - Relaciona mecânicos com as equipes às quais pertencem.
   - **Atributos:**
     - `ID`: Identificador único.
     - `Equipe_idEquipe`: Identificador da equipe.
     - `Mecânico_idMecânico`: Identificador do mecânico.

4. **Execução de Serviço**
   - Relaciona mecânicos com as ordens de serviço que executaram.
   - **Atributos:**
     - `Mecânico_idMecânico`: Identificador do mecânico.
     - `OS_idOS`: Identificador da OS.
     - `Data início`: Data de início da execução.
     - `Data fim`: Data de conclusão da execução.

---

#### **Contexto e Aplicação do Esquema:**
O modelo fornece suporte para operações de uma oficina mecânica, incluindo:
- Gerenciamento de clientes e veículos.
- Emissão, acompanhamento e encerramento de ordens de serviço.
- Registro de serviços realizados e peças utilizadas.
- Organização e controle de mecânicos e equipes de trabalho.

Esse esquema oferece uma visão clara para implementação em sistemas de gestão de oficinas, permitindo consultas complexas e relatórios operacionais, como rastreamento de serviços realizados, peças consumidas, ou desempenho de mecânicos e equipes.
