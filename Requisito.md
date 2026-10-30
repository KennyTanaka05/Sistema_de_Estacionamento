# Requisitos do VagaCerta


**Legenda da coluna Origem**

- **E** = Entrevista com o consumidor (`Entrevista.md`); "P9" = pergunta 9 do roteiro
- **O** = Observação no estacionamento, com vídeo (`Observacao.md`)
- **P** = Prototipação: validação das telas no Pencil (`prototipo/`)
- **Reunião** = decidido com o cliente na ata (`Ata_Reuniao.md`)
- **Pesquisa** = benchmarking de mercado (`Pesquisa.md`)

## Requisitos funcionais (RF)

| ID | Requisito | Origem | Tela |
|---|---|---|---|
| RF01 | Ler automaticamente a placa do veículo na entrada e na saída (câmera LPR) e abrir a cancela quando autorizado. | E (P6), O | Totem |
| RF02 | Perguntar ao motorista, no totem de entrada, o tempo previsto de permanência (até 2 h, até 6 h ou dia todo). | O, P | Totem |
| RF03 | Indicar zona e corredor para estacionar, de acordo com o tempo declarado e a ocupação atual. | O (gargalo) | Totem |
| RF04 | Registrar o check-in do veículo na vaga por leitura do QR Code fixado no pilar, marcando a vaga como ocupada. | O, P | Página QR |
| RF05 | Manter mapa de ocupação em tempo real (vagas livres e ocupadas por zona), visível ao dono e ao vigia. | E (P5, P10), O | Painel |
| RF06 | Mostrar ao motorista, na página do QR, onde o carro está estacionado (zona, corredor e vaga). | E (P2), Pesquisa | Página QR |
| RF07 | Calcular o valor da permanência por fração de 15 minutos e permitir pagamento por Pix ou cartão pelo celular. | E (P7, P9, P10) | Página QR |
| RF08 | Permitir o registro de entrada por digitação (placa, modelo, marca, cor, permanência) quando a câmera não ler a placa. | O, P | Registro |
| RF09 | Emitir recibo digital com taxa/hora, data e hora de entrada e, na saída, comprovante de pagamento. | O | Página QR |
| RF10 | Avisar o motorista 15 min antes do fim do tempo declarado e permitir estender a permanência pela página do QR. | Reunião | Página QR |
| RF11 | Gerar alertas para o vigia: vaga ocupada sem check-in, carro fora da zona indicada e carro parado há mais de 24 h. | Reunião | Painel |
| RF12 | Cadastrar mensalistas por placa, dispensando a pergunta de permanência e aplicando a tarifa mensal. | Pesquisa | Registro |

## Requisitos não funcionais (RNF)

Coluna **FURPS** (modelo de qualidade da HP): **F** Functionality · **U** Usability · **R** Reliability · **P** Performance · **S** Supportability, detalhado na seção [Classificação FURPS](#classificação-furps).

| ID | Requisito | Origem | FURPS |
|---|---|---|---|
| RNF01 | A operação completa (entrada, pátio e saída) deve funcionar com apenas duas pessoas: o vigia e o dono. | O, Reunião | S |
| RNF02 | As duas portarias devem exibir a mesma ocupação, com atualização em até 3 segundos após cada check-in ou saída. | O | P |
| RNF03 | A leitura da placa e a abertura da cancela devem ocorrer em até 3 segundos após o veículo parar na faixa. | E (P6) | P |
| RNF04 | Em queda da internet, as cancelas e o registro por digitação continuam operando localmente e sincronizam depois. | E (P2), Pesquisa | R |
| RNF05 | Disponibilidade mínima de 99,5% ao mês (operação 24/7), com registro de falhas para auditoria. | Pesquisa | R |
| RNF06 | A página do QR deve abrir no navegador do celular sem instalação de aplicativo e em até 2 segundos em rede 4G. | E (P6, P7) | U |
| RNF07 | O motorista conclui o check-in na vaga em até 3 toques; o pagamento, em até 4 toques. | P | U |
| RNF08 | A tela de registro por digitação deve ser operável por um funcionário sem treinamento prévio, com campos obrigatórios sinalizados. | P | U |
| RNF09 | Placas, imagens e dados de pagamento devem ser tratados conforme a LGPD: finalidade declarada, retenção máxima de 90 dias e acesso restrito por perfil. | Pesquisa | S |
| RNF10 | Toda operação (entrada, pagamento, saída, alteração manual) deve gerar log auditável com usuário, data e hora. | Pesquisa | S |

## Regras de negócio (RG)

| ID | Regra | Origem |
|---|---|---|
| RG01 | O pátio é dividido em três zonas por permanência: A (até 2 h) próxima às saídas, B (até 6 h) intermediária e C (dia todo) ao fundo. | Reunião |
| RG02 | A cobrança é por fração de 15 minutos. A primeira hora vale R$ 10,00 e cada fração adicional R$ 2,50; a diária fechada (zona C) vale R$ 40,00. | E (P9), Reunião |
| RG03 | Quem estaciona na zona indicada pelo sistema e faz o check-in no QR Code ganha os primeiros 15 minutos gratuitos. | Reunião |
| RG04 | Há tolerância de 15 minutos após o tempo declarado. Depois dela, o excedente é cobrado com acréscimo de 50% sobre a fração. | Reunião |
| RG05 | Motorista que extrapola o tempo declarado 3 vezes em 30 dias deixa de receber indicação para a zona A nas próximas visitas. | Reunião |
| RG06 | Mensalistas têm 20% de desconto sobre a tarifa equivalente, entram sem responder ao totem e não concorrem às vagas da zona A. | Pesquisa |
| RG07 | A cancela de saída só abre com pagamento confirmado (pelo celular ou na portaria) ou placa de mensalista ativa. | O |
| RG08 | Se a placa não for lida em 2 tentativas, a entrada passa obrigatoriamente pelo registro por digitação na portaria. | O |
| RG09 | Entradas e saídas podem ocorrer por qualquer uma das duas portarias; a cobrança usa sempre o horário da primeira leitura da placa. | O |

## Classificação FURPS

| Dimensão | Requisitos |
|---|---|
| **F** Funcionalidade | RF01 a RF12 |
| **U** Usabilidade | RNF06, RNF07, RNF08 |
| **R** Confiabilidade | RNF04, RNF05 |
| **P** Performance | RNF02, RNF03 |
| **S** Suportabilidade | RNF01, RNF09, RNF10 |

## Matriz de rastreabilidade

| Técnica | Requisitos | Evidência |
|---|---|---|
| Entrevista | RF01, RF05, RF06, RF07, RNF03, RNF04, RNF06, RG02 | Entrevista.md |
| Observação | RF01–RF06, RF08, RF09, RNF01, RNF02, RG01, RG07, RG08, RG09 | Observacao.md |
| Prototipação | RF02, RF04, RF08, RF12, RNF07, RNF08, RG06 | prototipo/ |
| Reunião com o cliente | RF10, RF11, RNF01, RG01–RG05 | Ata_Reuniao.md |
| Pesquisa de mercado | RF06, RF12, RNF04, RNF05, RNF09, RNF10, RG06 | Pesquisa.md |
