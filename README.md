# Gerador de Aviso de Sala de Crise

Ferramenta que gera automaticamente a mensagem padronizada de abertura de "Sala de Crise" para o Telegram, a partir dos dados exportados de um sistema de gestão de alarmes — usada na rotina de NOC da Padtec S/A / COPE Fibrasil.

## Contexto

Quando uma ocorrência crítica é identificada, a equipe de NOC precisa abrir uma Sala de Crise e comunicar o grupo responsável rapidamente, com informações consistentes: local afetado, quantidade de clientes impactados, splitters envolvidos e equipamento relacionado. Sob pressão de tempo, montar essa mensagem manualmente é sujeito a erro e a inconsistência de formato entre pessoas diferentes da equipe.

## Problema

- Mensagem de abertura de Sala de Crise montada manualmente, com risco de informação incompleta ou incorreta.
- Os dados de origem (sistema de gestão de alarmes) nem sempre estão em formato de fácil cópia — em muitos casos, só um print de tela está disponível no momento da ocorrência.
- O número do chamado (TTK) normalmente ainda não existe nesse momento, pois a equipe aciona a Sala de Crise antes da geração automática do chamado.

## Solução

Ferramenta que aceita dois formatos de entrada:

- Importação do arquivo Excel exportado do sistema de gestão de alarmes; ou
- Print de tela colado diretamente (Ctrl+V).

A partir da entrada, a ferramenta extrai os campos relevantes (local, quantidade de PONs/clientes afetados, faixa de splitters, equipamento) e monta automaticamente a mensagem padronizada, pronta para ser copiada e enviada ao grupo de Telegram responsável — sem depender do número do TTK.

## Arquitetura

```
Exportação do sistema de gestão de alarmes
   (arquivo Excel/CSV OU print de tela)
        ↓
Leitura dos dados (planilha ou imagem colada)
        ↓
Extração dos campos relevantes:
   local, PONs afetados, total de clientes,
   faixa de splitters, equipamento
        ↓
Aplicação das regras de formatação por campo
        ↓
Geração da mensagem padronizada
        ↓
Envio manual para o grupo de Telegram
```

## Tecnologias

*[A confirmar antes de publicar: linguagem/framework principal, biblioteca de leitura de planilha, método usado para ler o print colado.]*

## Principais funcionalidades

- Duas formas de entrada de dados: arquivo exportado ou print de tela colado.
- Extração automática do campo "equipamento" a partir de um identificador técnico do sistema de origem, com regras específicas para diferentes formatos desse identificador.
- Mensagem final no formato padrão já usado pela equipe, pronta para colar no Telegram.
- Funciona mesmo sem o número do TTK, que normalmente ainda não existe no momento da abertura da sala.

## Desafios técnicos

- O identificador técnico do equipamento vem em formatos diferentes dependendo do tipo de rede, exigindo regras de extração específicas para cada padrão.
- Ao ler dados a partir de um print de tela, é preciso identificar corretamente qual coluna corresponde a cada campo — por exemplo, diferenciar a coluna de "local" da coluna de "splitter", que ficam lado a lado.

## Resultado

Padroniza a comunicação de abertura de Sala de Crise e reduz o tempo entre a identificação da ocorrência e o aviso à equipe responsável.
*[A preencher: métricas, se houver.]*

## Roadmap / Próximas melhorias

*[A preencher pelo Bruno.]*

## Status

Em desenvolvimento. Código-fonte a ser publicado em versão sanitizada (sem dados internos).
