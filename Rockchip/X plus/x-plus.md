## Experiência e processo de descaracterização \[Terminado] 

A ideia geral para descaracterizar esse modelo era bem simples, mas questões de resolução complexas se apresentaram ao longo do processo. Nesta seção serão descritos os sucessos, as falhas, os desafios e o resultado final.

Inicialmente foi seguido o tutorial encontrado no fórum armbian, em um tópico que pode ser acessado por esse link:
O tutorial trata apenas de SBC's com SoC's rk322x, que é o caso do modelo in X plus.

Pela descrição do tutorial, alguns requisitos eram necessários:
1. Multitool, uma ferramenta para lidar com as questões de comunicação entre hardware e _software_;
2. Uma imagem de sistema operacional compatível ( a imagem utilizada inicialmente foi uma build do armbian. Mais informações no link [Build Preparation](https://docs.armbian.com/Developer-Guide_Build-Preparation/) );
3. Um cartão SD.

  O Multitool, cuja imagem foi obtida no link de download pelo tutorial, foi bootado no cartão SD pelo Balena Etcher.
  O objetivo seria copiar o arquivo de imagem do sistema que se pretende instalar para a pasta "images" do Multitool, agora bootado no cartão SD. Isto, no entanto não foi possível em um primeiro momento, dado que a partição "MULTITOOL" do cartão SD que continha o arquivo "images" não era grande o suficiente para comportar um arquivo .img. Esse problema foi resolvido apenas inserindo o cartão SD na tvbox, que fez com que a partição "MULTITOOL" fosse expandida. Também foi dada a opção de salvar um backup do sistema presenta na SBC naquele dado momento. Com a partição expandida, foi possível inserir o arquivo .img obtido pela build do repositório Armbian do github no arquivo "images" do cartão SD e inserí-lo novamente na tv box. A opção de flashar a imagem no sistema foi escolhida.
  
  Inicialmente o sistema inicializou como previsto, porém após a criação do usuário e configuração inicial não era possível acessar nenhuma funcionalidade no desktop (interface). O comando Ctrl+Alt+F1 foi utilizado para acessar a linha de comando, mas o número de comandos funcionais estava restrito devido à falta de acesso a internet. Para contornar esse problema, foi feita uma ancoragem com cabo USB pelo celular, que conferiu um acesso e atribuiu um IP ao dispositivo. Subsequentemente, em uma tentativa de buscar novas atualizações e corrigir os problemas da interface, o comando "sudo apt update && sudo apt upgrade -y" foi dado. Algumas mensagens de error e warning foram retornadas durante as atualização, muitas delas relacionadas à falta de algum recurso de _software_, como _drivers_ de sistema. Após o término das atualizações, de volta ao _desktop_, um _pop-up_ com uma mensagem de _crash_ pôde ser observada. Sem saber do que se tratava a mensagem, o dispositivo foi reiniciado com o propósito de efetivar as atualizações. Infelizmente, não houve muita diferença após as atualizações e a interação com o desktop continuou inexistente.
  
  Sob o pretexto de que a falha foi o arquivo de imagem de sistema utilizado, o mesmo processo foi repetido com imagens pré-construídas guardadas em repositórios online, em especial em [older images](https://armbian.hosthatch.com/archive/rk322x-box/archive/). Ao utilizar uma versão atual de imagem pré-construída, verificamos que o desktop e aplicações do sistema podiam ser acessados normalmente, porém nenhuma conexão com internet era reconhecida e esse problema persistiu até encontrarmos uma abordagem viável resolvê-lo. Mesmo assim, o dispositivo descaracterizado (sem conexão comn a internet) foi utilizado para aprendizado das características do sistema Armbian em si, bem como entendimento das partes independentes que compôem o sistema como um todo. Em meio a essa exploração, percebeu-se que nos drivers localizados em
  
  ```/lib/modules/$(uname -r)/kernel/drivers/net/wireless (drivers para conexão Wi-Fi)```
  
não havia nenhum driver correspondente ao módulo de rede identificado no hardware, que é o chip SV6256P da Icomm-semi e isso forneceu uma pista para entender o porquê da Internet não estar funcionando. Algumas pesquisas foram feitas na tentativa de encontrar o driver faltante, porém sem sucesso.
  
  Tendo esperança de que uma regressão nas versões do Armbian pudesse trazer a conexão Wi-Fi, outros arquivos de imagem com versões anteriores foram testados, em especial as versões 22.02.1 para servidor e a versão 21.5.1 para desktop. Surpreendentemente, apesar de não possuírem conexão com a internet logo após o processo de instalação, foi possível encontrar o driver de Internet Wi-Fi para o módulo de rede presente no hardware da TV box, exatamente onde deveriam estar os drivers para conexão Wi-Fi. Dessa forma, após entrar no diretório 
  
  ```lib/modules/$(uname -r)/kernel/drivers/net/wireless/ssv6x5x```
  
foi dado o comando 

  ```sudo insmod sv6x5x.ko ```
  
para carregar o driver dinamicamente como um módulo de kernel, e assim que o comando foi dado os sinais de Wi-Fi já eram reconhecidos.
  Dado que a maioria das necessidades básicas (conexão Wi-Fi, interação com desktop, etc.) foram supridas por esse processo de descarcaterização, processos de otimização e melhora de performance serão documentados no arquivo de ressignificação da tvbox. A descaracterização foi finalizada!

  Ressalvas:
  1. Apenas inserir o cartão SD com Multitool na tv box não prejudica nem altera seu sistema;
  2. "Criar e formatar partições de disco rígido" no caso do Windows pode ser utilizado para organizar e nomear (tornar detectável) partições de mídias externas.
  3. Para placas com SoC da Rockchip, Enquanto existir um sistema bootável detectável dentro da tvbox, ela sempre escolherá inicializar por ele, do contrário uma mídia externa é buscada. Caso o sistema bootável esteja corrompido, é possível forçar um curto, entrando no maskrom mode.
   
 
   
