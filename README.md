# Descaracterização de TvBox

O objetivo deste projeto é agrupar protocolos de descaracterização para o maior número de modelos diferentes de tv box possível. A descaracterização consiste na remoção do firmware ilegal dos aparelhos e subsequente instalação de um sistema operacional open-source. Como padrão utilizamos o sistema Armbian baseado em linux.

## Objetivos específicos
- Estudo técnico dos modelos e levantamento de informações de hardware, como SoC, memória, módulo de rede e afins.
- Descaracterização voltada para a instalação de um novo sistema operacional que seja compatível com o hardware.
- Avaliação de desempenho dos aparelhos com os sistemas operacionais recém-instalados, como verificação de suporte para ações de alto nível (renderização de imagens e vídeos, tempo de resposta, etc).
- Mapeamento e instalação de softwares de propósito educacional, dependendo das características finais dos dispositivos após descaracterização e avaliações de desempenho.

## Estrutura do repositório

- /Allwinner/: Tutoriais e informações dos dispositivos Allwinner.
  - Subdiretórios para cada modelo específico de TvBox Allwinner.
- /Amlogic/: Tutoriais e informações dos dispositivos Amlogic.
  - Subdiretórios para cada modelo específico de TvBox Amlogic.
- /Rockchip/: Tutoriais e informações dos dispositivos Rockchip.
  - Subdiretórios para cada modelo específico de TvBox Rockchip.
- /material-de-apoio/: Glossário e informações adicionais importantes.
- /tutorial-ferramentas/: Tutoriais de ferramentas frequentemente utilizadas.
  - /gravacao-armazenamento-interno/
  - /gravacao-sd/: Tutoriais de ferramentas para criação de cartões SD bootáveis.
- /controle.md: Mantém um histórico com datas do desenvolvimento do projeto.
- /informacoes-modelos-e-hardwares: Contém todas as informações obtidas dos modelos de TvBox já analisados.

## Contribuição
Sinta-se à vontade para contribuir com novos tutoriais ou melhorias nos existentes. Caso tenha informações adicionais sobre outro modelo ou experiência com o processo, crie um pull request para adicioná-las ao repositório.
