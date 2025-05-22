# Descaracterização de TvBox

O objetivo deste projeto é agrupar protocolos de descaracterização para o maior número de modelos de TV Box possível. A descaracterização consiste na remoção do firmware ilegal dos aparelhos e subsequente instalação de um sistema operacional open-source. Como padrão utilizamos o sistema Armbian baseado em linux.

A descaracterização tem sido uma alternativa ao descarte ordinário dos aparelhos TV Box, que apesar de representarem uma ameaça aos meios de transmissão de conteúdo pagos, não representam perigo quando avaliados apenas pelo seu hardware, sendo considerados legais quando instalados sistemas open-source.

O sucesso da descaracterização geralmente depende da compatibilidade do sistema com o hardware do modelo, sendo que o processador é o principal componente que determina essa compatibilidade. Por esse motivo os tutoriais foram divididos entre os três principais fabricantes de processador: Amlogic, Allwinner e Rockchip.
Para saber qual é o fabricante do processador da sua TV Box, o mais indicado é abrir as três pastas neste repositório e procurar pelo nome da sua TV Box. Caso não encontre, tente outras alternativas, como por exemplo o uso de algum aplicativo que revele as características de hardware (AIDA64, CPUZ, etc). Só em última instância abra o aparelho e remova o dissipador de calor, pois esse processo pode danificar o hardware.

## Objetivos específicos

- Estudo técnico dos modelos e levantamento de informações de hardware, como SoC, memória, módulo de rede e afins.
- Descaracterização voltada para a instalação de um novo sistema operacional que seja compatível com o hardware.
- Avaliação de desempenho dos aparelhos com os sistemas operacionais recém-instalados, além de verificação de suporte para recursos básicos, como acesso a Internet via Wi-Fi.

## Estrutura do repositório

- Allwinner: tutoriais e informações dos dispositivos Allwinner.
  - Subdiretórios para cada modelo específico de TvBox Allwinner.
- Amlogic: tutoriais e informações dos dispositivos Amlogic.
  - Subdiretórios para cada modelo específico de TvBox Amlogic.
- Rockchip: tutoriais e informações dos dispositivos Rockchip.
  - Subdiretórios para cada modelo específico de TvBox Rockchip.
- material-de-apoio: glossário, configuração inicial do sistema e informações adicionais importantes.
- tutorial-ferramentas: tutoriais de ferramentas frequentemente utilizadas.
  - gravacao-armazenamento-interno: tutoriais de ferramentas para gravar sistema diretamente no armazenamento interno da TvBox.
  - gravacao-sd: tutoriais de ferramentas para criação de cartões SD bootáveis.
- controle.md: mantém um histórico com datas do desenvolvimento do projeto.
- informacoes-modelos-e-hardwares: contém todas as informações obtidas dos modelos de TvBox já analisados.

## Contribuição

Sinta-se à vontade para contribuir com novos tutoriais ou melhorias nos existentes. Caso tenha informações adicionais sobre outro modelo ou experiência com o processo, crie um pull request para adicioná-las ao repositório.
