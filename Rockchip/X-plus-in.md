## Experiência e processo de descaracterização

A ideia geral para descaracterizar esse modelo era bem simples, mas questões de resolução complexas se apresentaram ao longo do processo. Nesta seção serão descritos os sucessos, as falhas e os desafios.

Inicialmente foi seguido o tutorial encontrado no fórum armbian, em um tópico que pode ser acessado por esse link:
O tutorial trata apenas de SBC's com SoC's rk322x, que é o caso do modelo X plus.

Pela descrição do tutorial, alguns requisitos eram necessários:
1. Multitool, uma ferramenta para lidar com as questões de comunicação entre hardware e _software_;
2. Uma imagem de sistema operacional compatível;
3. Um cartão SD.

  O Multitool, cuja imagem foi obtida no link de download pelo tutorial, foi bootado no cartão SD pelo Balena Etcher.
  O objetivo seria copiar o arquivo de imagem do sistema que se pretende instalar para a pasta "images" do Multitool, agora bootado no cartão SD. Isto, no entanto não foi possível em um primeiro momento, dado que a partição "MULTITOOL" do cartão SD que continha o arquivo "images" não era grande o suficiente para comportar um arquivo .img. Esse problema foi resolvido apenas inserindo o cartão SD na tvbox, que fez com que a partição "MULTITOOL" fosse expandida. Também foi dada a opção de salvar um backup do sistema presenta na SBC naquele dado momento. Com a partição expandida, foi possível inserir o arquivo .img obtido pela build do repositório Armbian do github no arquivo "images" do cartão SD e inserí-lo novamente na tv box. A opção de flashar a imagem no sistema foi escolhida.
  Inicialmente o sistema inicializou como previsto, porém após a criação do usuário e configuração inicial não era possível acessar nenhuma funcionalidade no desktop (interface). O comando Ctrl+Alt+F1 foi utilizado para acessar a linha de comando, mas o número de comandos funcionais estava restrito devido à falta de acesso a internet. Para contornar esse problema, foi feita uma ancoragem com cabo USB pelo celular, que conferiu um acesso e atribuiu um IP ao dispositivo. Subsequentemente, em uma tentativa de buscar novas atualizações e corrigir os problemas da interface, o comando "sudo apt update && sudo apt upgrade -y" foi dado. Algumas mensagens de error e warning foram retornadas durante as atualização, muitas delas relacionadas à falta de algum recurso de _software_, como _drivers_ de sistema. Após o término das atualizações, de volta ao _desktop_, um _pop-up_ com uma mensagem de _crash_ pôde ser observada. Sem saber do que se tratava a mensagem, o dispositivo foi reiniciado com o propósito de efetivar as atualizações. Infelizmente, apesar de receber energia e iluminar a tela do monitor (que ficou constantemente preta, apesar de estar visivelmente recebendo um input), o sistema não apresentava nenhum retorno na tela.
  A suspeita é que algum driver não esteja presente no sistema, ou que o kernel não esteja atualizado. 

  

  Resalvas:
  1. Apenas inserir o cartão SD com Multitool na tv box não prejudica nem altera seu sistema;
  2. "Criar e formatar partições de disco rígido" no caso do Windows pode ser utilizado para organizar e nomear (tornar detectável) partições de mídias externas.
  3. Para placas com SoC da Rockchip, Enquanto existir um sistema bootável detectável dentro da tvbox, ela sempre escolherá inicializar por ele, do contrário uma mídia externa é buscada. Caso o sistema bootável esteja corrompido, é possível forçar um curto, entrando no maskrom mode.
   
 
   
