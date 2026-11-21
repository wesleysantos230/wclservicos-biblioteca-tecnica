# WCL Biblioteca Técnica — base comercial

## O que está incluído
- Landing page com três planos: mensal R$ 19,90; semestral R$ 99,99; anual R$ 199,99. O teste de 7 dias depende da configuração e disponibilidade no checkout.
- Cadastro e login por e-mail/senha via Supabase Auth.
- Área do assinante (estrutura visual).
- Painel administrativo demonstrativo.
- SQL inicial para perfis, assinaturas, veículos, envios e padrões.

## O que ainda NÃO está ativo
Este pacote é um ponto de partida de desenvolvimento. Não há cobrança real, webhook, liberação automática, cancelamento automático, recuperação de pagamento ou painel administrativo protegido implementados. Não divulgue nem cobre clientes com este protótipo antes de completar e testar essas integrações.

## Requisitos
- Node.js 20+
- Projeto Supabase
- Conta Mercado Pago
- Conta Vercel

## Executar localmente
1. Descompacte o ZIP.
2. Rode `npm install`.
3. Copie `.env.example` para `.env.local` e preencha as variáveis Supabase.
4. No Supabase, execute `supabase/schema.sql` no SQL Editor.
5. Rode `npm run dev` e abra http://localhost:3000.

## Supabase
1. Crie projeto em https://supabase.com.
2. Copie Project URL e anon/public key para `.env.local`.
3. Ative confirmação de e-mail e configure URLs de redirecionamento.
4. Crie seu usuário e promova-o a admin com procedimento seguro no banco; não permita que usuários escolham seu próprio papel.
5. Revise e complete todas as políticas RLS antes de publicar.

## Mercado Pago: modelo comercial
No painel Mercado Pago, confirme se o checkout de assinatura oferece os meios desejados para sua conta e para o tipo de recorrência. Configure os planos comerciais:
- Mensal: R$ 19,90 por mês.
- Semestral: R$ 99,99 por 6 meses, pago antecipadamente.
- Anual: R$ 199,99 por 12 meses, pago antecipadamente.
- Teste: 7 dias, somente se disponível e configurado no produto/fluxo escolhido; confirme a quais planos será aplicado.
- Meios: cartão e Pix, conforme disponibilidade exibida no checkout.

Atenção: Pix recorrente pode exigir uma jornada de autorização/confirmar cobrança diferente do cartão. Não presuma que o simples pagamento de um Pix isolado ativa uma assinatura mensal automática.

Para integração real:
- Criar a assinatura/checkout no servidor com API oficial do Mercado Pago.
- Validar notificações/webhooks do Mercado Pago (assinatura da notificação e consulta do recurso na API).
- Atualizar `subscriptions` somente após confirmar o status diretamente na API.
- Nunca confiar em uma URL de retorno do navegador como prova de pagamento.
- Implementar cancelamento, atraso, retentativas, expiração do teste e idempotência.
Documentação: https://www.mercadopago.com.br/developers/pt/docs/subscriptions/overview

## Vercel
1. Envie o projeto a um repositório GitHub privado.
2. Importe o repositório na Vercel.
3. Configure as variáveis de ambiente no painel Vercel.
4. Faça deploy de teste e valide login, permissões, checkout e webhooks antes de liberar para clientes.

## Segurança e publicação
- Mantenha a chave `SUPABASE_SERVICE_ROLE_KEY` e `MERCADOPAGO_ACCESS_TOKEN` somente no servidor.
- Use HTTPS.
- Restrinja o painel admin por papel validado no servidor.
- Faça teste automatizado das políticas RLS.
- Não armazene dados de cartão; use checkout hospedado do Mercado Pago.
- Não publique dados de localização de rastreadores escondidos, senhas, dados pessoais ou material sem autorização.
- Tenha Termos de Uso, Política de Privacidade e regras de cancelamento.


## Atualização do produto — preço e fotos vinculadas
- Preços comerciais definidos: **R$ 19,90/mês**, **R$ 99,99/semestral** e **R$ 199,99/anual**.
- Cada padrão deverá estar associado ao veículo/versão corretos e a uma foto atualizada do veículo.
- O cadastro deve permitir anexar a foto do veículo no mesmo envio do diagrama e do procedimento.
- Campos previstos no banco: `vehicle_photo_url`, `diagram_vehicle_photo_url`, `photo_taken_at` e `photo_caption`.
- O técnico pode enviar a foto junto com o padrão; o administrador revisa a correspondência entre foto, veículo, ano/versão e diagrama antes de aprovar.
- A foto deve mostrar o veículo de forma identificável sem expor placa, VIN/chassi completo, rostos, documentos ou localização sensível. A foto não deve revelar onde o rastreador está escondido.
- Armazenar os arquivos em bucket privado; entregar imagens somente a assinantes autorizados, por URLs assinadas de curta duração. Não deixar o bucket público.
- Não usar fotos genéricas ou de outro ano/versão como se fossem atuais. Registrar data da foto e observação de versão.


## Fluxo de cadastro ampliado
O projeto agora prevê: foto do veículo; foto e descrição da área técnica de instalação; fotos dos fios/conectores com função declarada; vídeo opcional; confirmação do técnico; fila de aprovação; publicação na galeria somente após aprovação.

## Categorias
A navegação é Categoria → Fabricante → Modelo → Ano/versão. Categorias iniciais: carros, SUVs e picapes, utilitários e vans, caminhões, ônibus, motos e máquinas agrícolas/equipamentos.

Consulte `FLUXO_CADASTRO_E_CATEGORIAS.md` para o fluxo completo e as regras de mídia, privacidade e revisão.


## Tela inicial pública e paywall
A página inicial apresenta duas áreas separadas: Padrões de rastreadores e Cofre de módulos. Visitantes podem consultar categorias, fabricantes, modelos, anos e quantidade de conteúdos disponíveis. Ao tentar abrir um padrão, aparece um aviso de assinatura e os três planos comerciais: R$ 19,90/mês, R$ 99,99/semestral e R$ 199,99/anual. Fotos, diagramas, procedimentos e mídias não devem ser enviados ao navegador para visitantes sem assinatura.

## Categorias oficiais
- Carros
- Utilitários (ônibus, vans e caminhões)
- Motos
- Máquinas agrícolas e empilhadores

## Cofre de módulos
É uma biblioteca independente dos padrões de rastreadores, com seu próprio catálogo, cadastros, fotos, procedimentos e fila de aprovação. A mesma regra comercial de assinatura se aplica. O material deve documentar instalação/proteção autorizada, sem instruções de desativação ou contorno de sistemas antifurto.

## Nota de implementação do paywall
A tela inicial contém um exemplo visual de catálogo e popup. Antes de produção, popular `public_catalog` com metadados aprovados e implementar autorização no servidor. Não basta esconder fotos via CSS: os arquivos privados e os endpoints que os entregam precisam validar sessão e assinatura ativa.
