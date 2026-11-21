# Fotos atualizadas vinculadas aos diagramas — WCL

## Regra de cadastro
Um padrão não pode ser publicado sem:
1. Marca, modelo, ano e versão/motorização.
2. Foto atualizada do veículo correspondente.
3. Diagrama associado ao mesmo cadastro.
4. Legenda e data da foto.
5. Identificação do responsável pelo envio.

## Fluxo
- Administrador ou técnico autorizado cria uma solicitação.
- Envia a foto atual do veículo e o diagrama.
- Ambos ficam ligados ao mesmo registro de padrão.
- Status inicial: Pendente.
- Administrador verifica se a foto corresponde ao modelo/ano/versão e se o diagrama corresponde ao veículo.
- Só após aprovação o conteúdo entra na biblioteca dos assinantes.
- Se houver divergência, solicitar correção; não publicar.

## Organização de arquivos
Sugestão de caminhos dentro de bucket privado:
`submissions/{user_id}/{submission_id}/vehicle-photo.jpg`
`submissions/{user_id}/{submission_id}/diagram.pdf`
`submissions/{user_id}/{submission_id}/connector-photos/`

Após aprovação, copiar os arquivos para:
`published/{vehicle_id}/{pattern_id}/`

## Proteção e qualidade
- Não exibir placas, VIN/chassi completo, rostos, documentos ou dados de clientes.
- Não fotografar ou divulgar o ponto exato em que o rastreador fica escondido.
- Registrar a data em que a foto foi tirada.
- Confirmar ano, versão e motorização; veículos visualmente semelhantes podem ter chicotes e caixas diferentes.
- Respeitar direitos autorais e obter autorização para fotos e diagramas enviados.
- O acesso aos arquivos deve depender de sessão autenticada e assinatura válida. Usar bucket privado e URLs assinadas; nunca colocar chave de serviço no navegador.
