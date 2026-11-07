# Projeto Medicamentos

Agenda de medicamentos em português, responsiva e instalável como PWA. Sem dependências externas, rastreadores, contas ou envio de dados de saúde. O repositório contém somente código e testes com dados fictícios; a configuração do tratamento é preenchida ou importada no aparelho.

## Executar

Com Node.js instalado: `npm start`. Abra http://127.0.0.1:4173. Testes: `npm test`.

## GitHub Pages

Em Settings → Pages → Build and deployment, selecione Deploy from a branch, branch `main`, pasta `/ (root)` e Save. Todos os caminhos são relativos, compatíveis com páginas de projeto. Não publique backups, receitas nem dados pessoais.

## Funcionalidades

Agenda com filtros; check-in e correção com confirmação; datas passadas e futuras (check-in futuro bloqueado); calendário mensal; histórico; diário; início e duração personalizáveis; intervalos inteiros de 1 a 24 horas, inclusive 8 em 8 horas; exportação e importação validada com confirmação de substituição; cache offline após primeira carga; ícones e manifesto PWA. Navegação inferior fixa, botões Tomei com confirmação e timestamp real, estados tomada/pendente/atrasada e contador HH:MM:SS até a próxima dose futura prescrita. Doses vencidas continuam pendentes/atrasadas na agenda; o contador não indica que elas devem ser tomadas nem recalcula horários a partir da última tomada. Novos medicamentos começam no horário inicial e continuam a recorrência nos dias seguintes. Planos antigos preservam seus horários civis e IDs. Horários obedecem ao relógio local do aparelho; viagens e mudança de fuso exigem revisão com a equipe de saúde. Intervalos são horários civis; transições de horário de verão podem mudar o intervalo real.

## Privacidade e armazenamento

Dados em localStorage, sem criptografia ou autenticação. Isso evita upload automático, mas não protege contra alguém com acesso ao aparelho. Falhas ao salvar são exibidas e não confirmadas como sucesso. Backups JSON não são criptografados. Limpeza dos dados do navegador, modo privado e troca de aparelho podem apagar os registros; mantenha backups privados. Editar o tratamento preserva registros, diário e lembretes; cada tomada guarda nome e dosagem originais em recordDetails. IDs e timestamps de registros antigos são mantidos. Importação continua pedindo confirmação de substituição e aceita backups v1 anteriores. Backups novos mantêm version/config/records/journal; recordDetails e anchored são extensões opcionais, necessárias para preservar o histórico após edições e o início das novas recorrências. Versões antigas do aplicativo podem rejeitar backups novos com horários ou registros que elas não suportam.

## Notificações e avaliação de push

Lembretes visuais e notificações autorizadas são tentados apenas enquanto a página está visível, na hora exata da dose. Não há recuperação automática de alertas perdidos, nem alarmes garantidos em segundo plano. A notificação do sistema não revela o nome do medicamento na tela bloqueada. Use alarmes do Relógio como complemento.

GitHub Pages é hospedagem estática e não executa um agendador de push. Uma etapa futura exigiria backend com tarefas agendadas, VAPID, inscrições Web Push protegidas, autenticação, consentimento e política de retenção. Não se deve colocar chaves privadas no cliente ou usar GitHub Actions como alarme clínico. No iOS 16.4+, Web Push exige app na Tela de Início e permissão por interação do usuário. Rede, Foco e configurações do sistema ainda afetam entrega. Nenhum backend foi conectado e nenhum dado de saúde foi enviado.

Fontes: [WebKit: Web Push no iOS](https://webkit.org/blog/13878/), [Apple: envio de Web Push](https://developer.apple.com/documentation/usernotifications/sending-web-push-notifications-in-web-apps-and-browsers), [GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages).

O app organiza registros; não prescreve, confirma interações ou orienta compensação de doses. Confira horários e instruções com a equipe de saúde.

## Validação desta atualização

11 testes automatizados de recorrência, duração, atraso sem reagendamento, datas, validação, backups antigos e preservação do histórico. Fluxos conferidos no navegador com dados fictícios: cadastro, tomada atrasada com confirmação, edição e adição de medicamento, diário, calendário, exportação e reimportação. Layout inspecionado a 360 × 780. Não foi feita validação em aparelho físico iOS/Android nem garantia de alarmes, de entrega de notificações ou de acesso offline em todos os sistemas.

Medicamentos prescritos ao deitar podem ser cadastrados sem horário fixo. Aparecem diariamente na agenda, não entram no contador de horários e não ficam atrasados com base em uma hora inventada. O registro guarda o horário real. A opção é armazenada como bedtime:true; nenhum dado pessoal integra o código público.
