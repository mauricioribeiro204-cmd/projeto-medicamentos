# Projeto Medicamentos

Agenda de medicamentos em português, responsiva e instalável como PWA. Sem dependências externas, rastreadores, contas ou envio de dados de saúde. O repositório contém somente código e testes com dados fictícios; a configuração do tratamento é preenchida ou importada no aparelho.

## Executar

Com Node.js instalado: `npm start`. Abra http://127.0.0.1:4173. Testes: `npm test`.

## GitHub Pages

Em Settings → Pages → Build and deployment, selecione Deploy from a branch, branch `main`, pasta `/ (root)` e Save. Todos os caminhos são relativos, compatíveis com páginas de projeto. Não publique backups, receitas nem dados pessoais.

## Funcionalidades

Agenda com filtros; check-in e correção com confirmação; datas passadas e futuras (check-in futuro bloqueado); calendário mensal; histórico; diário; início e duração personalizáveis; intervalos de 8/12 horas e uma dose ao deitar; exportação e importação validada com confirmação de substituição; cache offline após primeira carga; ícones e manifesto PWA. Horários obedecem ao relógio local do aparelho; viagens e mudança de fuso exigem revisão com a equipe de saúde. Intervalos são horários civis; transições de horário de verão podem mudar o intervalo real.

## Privacidade e armazenamento

Dados em localStorage, sem criptografia ou autenticação. Isso evita upload automático, mas não protege contra alguém com acesso ao aparelho. Falhas ao salvar são exibidas e não confirmadas como sucesso. Backups JSON não são criptografados. Limpeza dos dados do navegador, modo privado e troca de aparelho podem apagar os registros; mantenha backups privados. Mudar o tratamento substitui registros após confirmação para evitar reinterpretar o histórico antigo.

## Notificações e avaliação de push

Lembretes visuais e notificações autorizadas são tentados apenas enquanto a página está visível, na hora exata da dose. Não há recuperação automática de alertas perdidos, nem alarmes garantidos em segundo plano. A notificação do sistema não revela o nome do medicamento na tela bloqueada. Use alarmes do Relógio como complemento.

GitHub Pages é hospedagem estática e não executa um agendador de push. Uma etapa futura exigiria backend com tarefas agendadas, VAPID, inscrições Web Push protegidas, autenticação, consentimento e política de retenção. Não se deve colocar chaves privadas no cliente ou usar GitHub Actions como alarme clínico. No iOS 16.4+, Web Push exige app na Tela de Início e permissão por interação do usuário. Rede, Foco e configurações do sistema ainda afetam entrega. Nenhum backend foi conectado e nenhum dado de saúde foi enviado.

Fontes: [WebKit: Web Push no iOS](https://webkit.org/blog/13878/), [Apple: envio de Web Push](https://developer.apple.com/documentation/usernotifications/sending-web-push-notifications-in-web-apps-and-browsers), [GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages).

O app organiza registros; não prescreve, confirma interações ou orienta compensação de doses. Confira horários e instruções com a equipe de saúde.
