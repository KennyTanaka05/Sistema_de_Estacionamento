# 1. O problema
  >O estacionamento é self-park, tem 5.000 vagas, duas portarias e só duas pessoas trabalhando: o vigia e o dono. Hoje cada um para onde acha vaga, então quem fica pouco tempo acaba no fundo e quem fica o dia todo pega as vagas perto da saída. Na entrevista, o cliente reclamou de rodar procurando vaga e da fila no caixa.

# 2. Nossa ideia
  Separar o pátio pelo tempo que o motorista vai ficar: quem fica pouco estaciona perto da saída e quem fica o dia todo vai para o fundo. Quem estacionar na zona indicada ganha os primeiros 15 minutos grátis.
# 3. Como funciona
  1. Na entrada, a câmera lê a placa e o totem pergunta quanto tempo o motorista vai ficar.
  2. O totem mostra a zona e o corredor, por exemplo "Zona B, corredor 4".
3. O motorista estaciona e lê com o celular o QR Code do pilar da vaga.
4. Na volta, ele vê na mesma página onde o carro está e paga por Pix ou cartão.
5. Na saída, a câmera lê a placa e a cancela abre.
Não tem aplicativo para baixar. O QR Code abre uma página do estacionamento no celular,
do mesmo jeito que o cardápio de restaurante.
4. Requisitos
• RF01: ler a placa na entrada e na saída.
• RF02: perguntar o tempo de permanência e indicar a zona.
• RF03: check-in na vaga pelo QR Code.
• RF04: mapa com as vagas livres e ocupadas.
• RF05: mostrar onde o carro está.
• RF06: pagamento pelo celular, por fração de 15 minutos.
• RNF01: funcionar só com o vigia e o dono.
• RNF02: as duas portarias veem a mesma ocupação.
• RNF03: continuar funcionando se a internet cair.
• RNF04: seguir a LGPD com os dados de placa e pagamento.
5. Funcionários
• Vigia: anda pelo pátio e confere os avisos do sistema, como vaga ocupada sem
check-in ou carro fora da zona.
• Dono: acompanha pelo computador a ocupação e o faturamento e resolve problemas
de pagamento.
6. Se passar do horário
O motorista recebe um aviso 15 minutos antes e pode estender o tempo pagando o valor
normal. Depois de 15 minutos de tolerância, o tempo a mais é cobrado com acréscimo.
Quem passa do horário toda vez deixa de receber vaga na zona curta.
