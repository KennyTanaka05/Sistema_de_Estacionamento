# Sistema Inteligente de Gestão de Estacionamento (Smart Parking)

## 1. Visão Geral e Contexto do Problema
O estacionamento possui uma capacidade total de **5.000 vagas**, conta com **duas portarias** de acesso e uma operação enxuta composta por apenas **dois colaboradores** (um vigia e o proprietário). Atualmente, a modalidade é do tipo *self-park* sem alocação direcionada, gerando ineficiências operacionais: veículos de curta permanência frequentemente ocupam as vagas mais distantes (no fundo), enquanto veículos de longa permanência ocupam as vagas de alta rotatividade próximas à saída. 

Como principais dores relatadas pelo cliente, destacam-se a dificuldade e o tempo despendido pelos motoristas na busca por vagas, bem como a formação de gargalos e filas nos caixas de pagamento tradicionais.

---

## 2. Solução Proposta
Implementação de um sistema inteligente de zoneamento e automação baseado no tempo estimado de permanência do veículo:
* **Segmentação por Perfil de Uso:** Alocação de vagas próximas à saída para motoristas de curta permanência e vagas no setor posterior para longa permanência.
* **Estímulo à Adesão:** Oferta de benefício comercial (os primeiros 15 minutos gratuitos) condicionado ao estacionamento na zona indicada pelo sistema.
* **Experiência Digital Sem Fricção (*Web-App*):** Dispensa o uso de aplicativos nativos, utilizando páginas web acessadas via QR Code (modelo similar a cardápios digitais).

---

## 3. Jornada de Operação (Fluxo do Usuário)
1. **Entrada:** 
   - O sistema realiza a leitura automática da placa (*ANPR*) na cancela de acesso.
   - O totem interativo solicita a previsão de tempo de permanência do motorista.
   - O totem indica em tela o direcionamento específico (ex: *"Zona B, Corredor 4"*).
2. **Estacionamento e Check-in:**
   - O motorista estaciona o veículo na vaga correspondente e escaneia o QR Code afixado no pilar de sustentação para validar o *check-in*.
3. **Retorno e Pagamento:**
   - Ao retornar, o usuário acessa a plataforma web pelo mesmo QR Code, visualizando a localização exata do veículo.
   - O pagamento é efetuado de forma autônoma via Pix ou cartão de crédito, cobrado por frações de 15 minutos.
4. **Saída:**
   - A câmera reconhece a placa do veículo na saída e libera a cancela automaticamente após a confirmação do pagamento.

---

## 4. Requisitos do Sistema

### Requisitos Funcionais
* **1:** Leitura automatizada de placas (ANPR) nos portões de entrada e saída.
* **2:** Coleta do tempo estimado de permanência no totem e indicação automatizada de zona e corredor.
* **3:** Validação de *check-in* na vaga via leitura de QR Code.
* **4:** Disponibilização de mapa dinâmico de ocupação em tempo real (vagas livres vs. ocupadas).
* **5:** Funcionalidade de geolocalização interna para exibição da posição do veículo.
* **6:** Sistema de faturamento móvel fracionado por blocos de 15 minutos via meios digitais de pagamento.

### Requisitos Não Funcionais
* **1:** Arquitetura otimizada para operação enxuta (suporte operacional focado estritamente no vigia e no proprietário).
* **2:** Sincronização em tempo real da ocupação do pátio entre as duas portarias.
* **3:** Mecanismo de resiliência e operação offline parcial para garantia de continuidade operacional em quedas de conexão com a internet.
* **4:** Conformidade estrita com a Lei General de Proteção de Dados (LGPD) para o tratamento de dados de placas e informações financeiras.

---

## 5. Governança e Papéis Operacionais
* **Vigia:** Responsável pela ronda física do pátio, monitoramento de alertas gerados pelo sistema (ex: vagas ocupadas sem *check-in* ou veículos estacionados em zonas incorretas).
* **Proprietário (*Dwner*):** Responsável pelo acompanhamento gerencial centralizado (taxa de ocupação, faturamento e resolução de exceções ou falhas de pagamento) por meio de painel administrativo.

---

## 6. Gestão de Exceções e Regras de Horário
* **Notificação Preventiva:** Envio de alerta ao motorista 15 minutos antes do término do tempo contratado, com opção de extensão via pagamento regular.
* **Tolerância e Penalidades:** Período de tolerância de 15 minutos após o vencimento, seguido por cobrança com acréscimo proporcional. Usuários reincidentes em estouros de tempo perdem o direito de alocação nas zonas de curta permanência.
