# Histórico completo e relatórios de Demandas

## Objetivo
Transformar cada demanda em uma linha do tempo permanente. Novos alinhamentos, revisões de prazo, propostas e aprovações serão acrescentados como registros separados, sem substituir ocorrências anteriores.

## Regras confirmadas
- Podem trabalhar nas demandas: admin, supervisor, analista e comercial.
- O comercial terá acesso somente à aba **Demandas** dentro do projeto.
- Cada repetição de uma etapa será uma nova ocorrência datada.
- Somente o admin poderá excluir uma demanda inteira.
- Ocorrências individuais do histórico não poderão ser editadas nem apagadas.
- Haverá PDF por demanda e PDF consolidado por projeto.

## O que será construído
1. **Linha do tempo permanente**
   - Criar registros de etapa vinculados à demanda.
   - Tipos: alinhamento analista/cliente; avaliação do desenvolvimento; envio da proposta comercial; aprovação do cliente; observação/correção.
   - Guardar responsável pelo registro, data do registro e os dados próprios da etapa.

2. **Campos por etapa**
   - Alinhamento: descrição do que foi solicitado e participantes.
   - Desenvolvimento: responsável, tempo estimado e data prevista de entrega.
   - Comercial: responsável comercial e data de envio da proposta.
   - Aprovação: nome de quem aprovou pelo cliente e data.
   - Correções serão novas entradas relacionadas à informação anterior, mantendo ambas visíveis.

3. **Acesso por perfil**
   - Admin e supervisor: visualização e inclusão em todas as etapas.
   - Analista: criação da demanda, alinhamentos, acompanhamento e registro da aprovação do cliente.
   - Comercial: acesso ao projeto restrito à aba Demandas e inclusão dos dados comerciais.
   - Exclusão definitiva da demanda: somente admin, com confirmação explícita.
   - As mesmas regras serão protegidas no banco, não apenas na tela.

4. **Tela de Demandas**
   - Manter o cadastro principal da demanda separado das novas inclusões.
   - Exibir uma linha do tempo legível com todas as ocorrências, autor e data.
   - Oferecer uma ação específica para acrescentar cada tipo de etapa.
   - Remover a edição destrutiva dos dados históricos.

5. **Relatórios PDF**
   - PDF individual com identificação, situação atual e trajetória completa da demanda.
   - PDF do projeto com todas as demandas e suas linhas do tempo.
   - Gerar os documentos diretamente pela aba Demandas, com datas e responsáveis formatados para leitura e arquivo.

6. **Entrega segura**
   - Fazer as alterações de forma aditiva para preservar os dados existentes.
   - Adaptar a versão estática que está na prévia e atualizar a proposta separada no GitHub, sem alterar a principal diretamente.
   - Validar na prévia os quatro perfis, inclusões repetidas, restrição do comercial, exclusão pelo admin e os dois PDFs.

## Detalhes técnicos
- Criar uma tabela de eventos imutáveis vinculada às demandas, com permissões por perfil e gravação automática do usuário autenticado.
- Preservar a tabela e o histórico já existentes; dados antigos aparecerão como histórico legado.
- Usar geração de PDF no navegador para manter compatibilidade com a publicação atual.
- Tratar “quem aprovou pelo cliente” como nome informado, pois essa pessoa pode não possuir acesso ao sistema; o sistema também registrará qual usuário interno lançou essa aprovação.
