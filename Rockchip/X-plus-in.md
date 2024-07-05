## Experiência

A ideia geral para descaracterizar esse modelo era bem simples, mas questões de resolução complexas se apresentaram ao longo do processo. Nesta seção serão descritos os sucessos, as falhas e os desafios.

Inicialmente foi seguido o tutorial encontrado no fórum armbian, em um tópico que pode ser acessado por esse link:
O tutorial trata apenas de SBC's com SoC's rk322x, que é o caso do modelo X plus.

Pela descrição do tutorial, alguns requisitos eram necessários:
1. Multitool, uma ferramenta para lidar com as questões de comunicação entre hardware e software;
2. Uma imagem de sistema operacional compatível;
3. Um cartão SD.

  O Multitool, cuja imagem foi obtida no link de download pelo tutorial, foi bootado no cartão SD pelo Balena Etcher.
  O objetivo seria copiar o arquivo de imagem do sistema que se pretende instalar para a pasta "images" do Multitool, agora bootado no cartão SD. Isto, no entanto não foi possível em um primeiro momento, dado que a partição "MULTITOOL" do cartão SD que continha o arquivo "images" não era grande o suficiente para comportar um arquivo .img. Esse problema foi resolvido apenas inserindo o cartão SD na tvbox, que fez com que a partição "MULTITOOL" fosse expandida. Também foi dada a opção de salvar um backup do sistema presenta na SBC naquele dado momento. Com a partição expandida, foi possível inserir o arquivo .img obtido pela build do repositório Armbian do github no arquivo "images" do cartão SD e inseri-lo novamente na tv box. A opção de flashar a imagem no sistema foi escolhida.

  Resalvas:
  1. Apenas inserir o cartão SD com Multitool na tv box não prejudica nem altera seu sistema;
  2. "Criar e formatar partições de disco rígido" no caso do Windows pode ser utilizado para organizar e nomear (tornar detectável) partições de mídias externas.
  3. Para placas com SoC da Rockchip, Enquanto existir um sistema bootável detectável dentro da tvbox, ela sempre escolherá inicializar por ele, do contrário uma mídia externa é buscada. Caso o sistema bootável esteja corrompido, é possível forçar um curto, entrando no maskrom mode.
   
 
   
