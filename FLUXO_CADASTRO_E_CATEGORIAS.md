# WCL Biblioteca Técnica — fluxo de cadastro e categorias

## Hierarquia obrigatória da biblioteca
Todo cadastro deve seguir:
**Categoria → Fabricante → Modelo → Ano/versão/motorização**

Categorias iniciais:
- Carros
- SUVs e picapes
- Utilitários e vans
- Caminhões
- Ônibus
- Motos
- Máquinas agrícolas e equipamentos

Fabricantes e modelos serão cadastrados pelo administrador e poderão ser ampliados ao longo do tempo. Evitar duplicidades de nomes e versões.

## Formulário de envio de padrão

### 1. Identificação do veículo
- Categoria
- Fabricante
- Modelo
- Ano
- Versão/motorização
- Combustível (quando aplicável)
- Observações de compatibilidade

### 2. Foto do veículo
- Foto atual do veículo correspondente ao ano/versão
- Data da foto
- Legenda
- Não mostrar placa, VIN/chassi completo, documentos ou rostos sem autorização

### 3. Local de instalação
- Foto do componente/área de serviço
- Campo de texto: descrição do local de instalação
- Informar apenas a área técnica necessária para o serviço; não registrar nem publicar o ponto exato de ocultação do rastreador ou detalhes que facilitem sua remoção/neutralização.

### 4. Fios utilizados — cadastro técnico
Para cada fio, permitir adicionar um registro:
- Foto do fio/conector
- Função declarada: alimentação, pós-chave, aterramento, sinal ou circuito de bloqueio
- Se for circuito de bloqueio, classificar de forma geral: bomba de combustível, ignição ou outro circuito autorizado
- Campo “efeito funcional” para explicar o resultado esperado em linguagem técnica e segura
- Observações de validação e versão do veículo

Não publicar instruções que permitam neutralizar sistemas antifurto, contornar imobilizadores ou localizar precisamente dispositivos ocultos. Informações sensíveis devem ficar limitadas a técnicos verificados e ser revisadas pelo administrador.

### 5. Vídeo (opcional)
- Upload de vídeo curto demonstrando o procedimento autorizado
- Legenda e data
- Não filmar placas, documentos, rostos, localização do veículo ou ponto de ocultação do rastreador

### 6. Confirmação e envio
Antes do envio, mostrar resumo do cadastro e caixa de confirmação:
- Confirmo que as fotos e informações são minhas ou tenho autorização para compartilhá-las.
- Confirmo que selecionei corretamente categoria, fabricante, modelo, ano e versão.
- Entendo que o conteúdo ficará pendente e não será publicado antes da aprovação.

Status do envio:
- Rascunho
- Pendente de aprovação
- Ajustes solicitados
- Aprovado
- Rejeitado

Após aprovação, publicar na galeria da categoria/fabricante/modelo correspondente.

## Fluxo de aprovação
1. Técnico autorizado preenche o cadastro.
2. Anexa fotos e, opcionalmente, vídeo.
3. Confere o resumo e envia.
4. Administrador recebe a solicitação na fila.
5. Administrador verifica correspondência do veículo, qualidade, autorização e segurança do conteúdo.
6. Pode aprovar, rejeitar ou solicitar ajustes.
7. Apenas o conteúdo aprovado aparece na galeria dos assinantes com assinatura válida.

## Regras de mídia e privacidade
- Usar armazenamento privado, não links públicos permanentes.
- Liberar mídia apenas para usuários autenticados e com assinatura ativa.
- Gerar URLs temporárias no servidor.
- Limitar tamanho e formatos dos arquivos.
- Verificar arquivos enviados e manter registro de quem enviou/aprovou.
- Obter autorização para compartilhar diagramas de terceiros e imagens de clientes.
- Remover placas, chassi completo, rostos e dados pessoais.
- Não revelar localização exata de rastreadores escondidos, pontos de bypass ou instruções para neutralizar sistemas de segurança.
