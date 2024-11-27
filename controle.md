## 🗺️ Link da Tabela de Mapeamento dos modelos
- [Mapeamento dos Diversos Modelos TV BOX](https://unioestebr-my.sharepoint.com/:x:/g/personal/erick_mulher_unioeste_br/EW3v6BX7ek5MsUwlNYhS7HoBPytVYmlZkW_rri7IkowKrQ?e=bad0Am)

# Processos em andamento

## META DA SEMANA: 

#### Encontrar, compilar e inserir drivers Wi-Fi como módulos de kernel nos modelos MXQ, b11 e r69 1 (amlogic s905l). Variar parâmetros de build no framework de construção de arquivos de imagem do Armbian a fim de entender melhor as configurações. Tentar fazer um cluster com X plus


### Dia 26/11/2024
Dois modelos com um SoC um tanto anômalo foram catalogados: RedOne e HIGHtv. O SoC em questão é o IK316, mas algumas discussões no fórum Armbian a respeito de uma TV Box com este SoC chegaram a conclusão de que é uma grafia falsa sob um processador Allwinner H313 ou H616. No momento da discussão, a imagem utilizada pelos usuários foi uma modificação de uma imagem para o OrangePi Zero 2, que possui um processador Allwinner H616. O objetivo então é testar o modelo com imagem para H313 e H616, e caso nenhuma funcione será necessário obeter mais informações através de testes e discussões.

Será testado se a R69 com logo reflexivo, que possui SoC Allwinner H2+, responde a uma imagem para Amlogic ou se ela realmente é uma Allwinner H2+.

Averiguamos que infelizmente não será tão fácil obter o driver de Wi-Fi para a Tourobox, já que o código fonte não foi fornecido pelo fabricante e o módulo de rede é um chip incomum. Ainda há esperanças para o driver de Wi-Fi da R69, porém ele não foi encontrado nativo em arquivos de imagem com sistemas de versões mais recentes. Talvez o dtb correto para a R69 Amlogic seja na verdade meson-gxl-s905d-phicom-nw.dtb.

Foi feita uma tentativa de conectar duas X plus através de um cabo de ethernet, mas sem sucesso, pois após definir os ips estaticamente, os pings não foram reconhecidos uma pela outra. Um ponto positivo é que foi possível configurar a interface de ethernet (eth0) tranquilamente.

A imagem Armbian_community_24.11.0-trunk.351_Aml-s9xx-box_bookworm_current_6.6.58_gnome_desktop.img foi testada com u-boot-s905x3 e dtb meson-sm1-sei610 para os modelos duosat, btv11, athomics nomads e RedPro2. Todas acessaram o sistema inicialmente contido no cartão SD como é de costume, exceto a RedPro2, que demandou que o botão "Recovery" fosse pressionado com um clipe de papel por alguns segundos. Infelizmente, todos os modelos apresentaram algum problema na hora inicializar, que provavelmente se deve a toda a problemática dos u-boots desenvolvidos há muito tempo e não mais suportados pelo desenvolvedor balbes150 (os modelos s905x3 não eram tão comuns nessa época). O mais correto a se fazer é buscar alternativas como as apresentadas em uma discussão do fórum armbian para tornar possível inicializar pelos sistemas advindos de arquivos de imagens usuais. A solução sugerida é inicializar o sistema a partir do u-boot proprietário, ou seja, aquele que já está presente na TVB. A discussão pode ser acessada pelo seguinte link: [Discussão](https://forum.armbian.com/topic/30245-cant-boot-with-2305-or-later-builds-on-s905x2-g12a-or-s905x3-sm1/). Infelizmente nem o u-boot-s905x-s912 funcionou corretamente, apesar de acender as experanças, tornando acessível o console rudimentar do initramfs, que possui opções de depuração extremamente limitadas para se entender qual é o real problema.

### Dia 14/11/2024
Uma nova variante da R69 foi avaliada. Conhecida como KNBOX R69, com um processador aparente AllWinner H3, foi colocada à prova sob a inserção de um cartão SD bootado tanto pela entrada do cartão quanto pelo adaptador USB, pressionando o suposto botão de reset por uma quantidade diferente de tempo a cada tentativa. Tudo foi inútil, no entanto. Apesar disso algumas suspeitas continuam... Esse processo foi testado tanto com um SD bootado com uma imagem para AllWinner H3, quanto com uma imagem para Amlogic s905l, só para desencargo de consciência. Ao conectar com Android Debugging Bridge (ADB), alguns arquivos da Amlogic foram encontrados, por isso a tentativa e suspeita quanto a veracidade do processador...

Parte 2
Descobrimos que nada faz sentido e é tudo uma mentira. KNBOX R69 na verdade reconheceu um sistema Amlogic, mas apenas após darmos um curto  nos pinos indicados por uma seta branca no armazenamento interno ao mesmo tempo em que o botão de reset era segurado. O dtb correto parece ser meson-gxl-s905x-p212.dtb btw.


### Dia 12/11/2024
Uma das várias variantes do modelo R69 foi descaracterizada com sucesso, sendo nesse caso aquela com SoC Amlogic s905l. Ainda assim, foram constatados problemas de travamento e carregamento, portanto mais testes serão feitos com dtb e afins. O bootloader "u-boot-s905x-s912", no entanto, com certeza é o correto.
Aparentemente será inevitável incorporar o uso de ferramentas de _burn_ por cabo USB macho-macho, como USB burning tool e phoenix suit, pois alguns modelos não repondem a inicialização após inserir cartão SD bootado e nem apresentam um botão de reset.

### Dia 21/10/2024
Alguns modelos apresentaram muita dificuldade em fazer o módulo de Wi-Fi funcionar, mesmo com drivers supostamente presente. Isso ocorreu, em especial, com aqueles que possuem chip AP6330/AP6212/SP6330, que de alguma forma é baseado no módulo de rede da broadcom e precisa de configurações específicas para funcionar.

A imagem de sistema operacional fornecida pelo Educabox para o modelo b11 também se recusou a reconhecer conexões de Internet. O mesmo para RedPro2 e Azamérica i7. Suspeita-se que exista a possibilidade de copiar uma configuração de Wi-fi já presente em /lib/firmware/brcm de um arquivo x para um arquivo y, mudando seu nome com o que o sistema esperaria ler para tornar o Wi-Fi funcional nos modelos mencionados.

Muitos modelos Allwinner, como Azamérica Champions, T10, R69 e Ximi Box plus apresentaram resistência em reconhecer o cartão SD bootado, mas uma forma de contornar este problema está sendo investigada através do uso de ferramentas *open source* especializadas, a saber Phoenix suit e Phoenix USB Pro

### Dia 06/10/2024

Foi obtido um sucesso para o modelo UniTv S1, que não respondeu inicialmente ao multitool, mas aceitou receber uma imagem de sistema pelo software rkdevelop_tool. A imagem, no entanto, não funcionava. Em contrapartida, mesmo com um sistema em loop após instalar a imagem com o rkdevelop_tool, a Tv Box passou a reconhecer a ação do multitool, por onde foi instalado uma imagem efetivamente, que apresentou um funcionamento normal. O driver de Wi-Fi já estava presente para versões do kernel maiores ou iguais a 5.15.25.


### Dia 30/09/2024
Motivados pela enorme diversidade de chipsets para Wi-Fi, tentaremos contato com os responsáveis por manter o framework de construção de imagens do armbian para adicionar os drivers de rede para diversos módulos Wi-Fi na opção EXTRA_WIFI. Conseguimos encontrar um arquivo de imagem operante para o SoC Allwinner H313 que se mostrou funcional para o modelo Tourobox, porém também sem conexão com Wi-Fi pelo mesmo motivo dos outros modelos. O mesmo processo anterior dos modelos MXQ e X plus foi replicado na RPC mini e ela foi descaracterizada com sucesso, porém também sem Wi-Fi. Tentaremos a mesma imagem da Tourobox na Ximi box plus b11 e T10, também com soc Allwinner H313.

### Dia 23/09/2024
Ainda sem sucesso com os drivers de Wi-Fi já compilados nos arquivos de imagem Armbian, decidiu-se utilizar a abordagem de buscar os drivers na Internet e compilá-los. Esta abordagem ainda será testada e se bem sucedida levará ao sucesso na descaracterização dos modelos MXQ PLUS 5G 8K, MXQ PRO 5G 4K e btv b11, pois em todos estes modelos já foi instalado o sistema Armbian, resta apenas obter conectividade com a Internet via Wi-Fi.

### Dia 17/09/2024
Alguns testes de benchmark foram conduzidos nos modelos in X plus, HTV HA e TG3. Ao mesmo tempo, tentou-se um processo semelhante ao da X plus para descaracterizar o modelo MXQ PLUS 5G 8K, de mesmo SoC, porém com módulo de rede Icomm-semi SV6158. Essas ações se deram da seguinte maneira:
Primeiramente, para a análise de desempenho dos modelos mencionados acima foi tilizado o avaliador de performance hardinfo. Este software foi escolhido por sua característica de ser "leve" no que se diz respeito ao porte dos dispositivos e componentes de hardware (CPU, memória RAM) que o mesmo suporta, funcionando para as tv box sem sobrecarregar o sistema a ponto de torná-lo inutilizável.
Agora, sobre a tentativa de descaracterizar o último modelo mencionado acima, primeiramente repetiu-se o processo da X plus com a imagem de sistema Armbian 21.05.1 focal legacy 4.4.194, porém ao tentar replicar o procedimento para obter conexão Wi-Fi via carregamento do módulo de kernel, o driver não era exatamente compatível e a interface wlan0 não foi identificada conforme esperado. Após isso, verificou-se o driver de Wi-Fi para o módulo SV6X5X em um arquivo de imagem com Armbian Jammy 24.04 kernel 6.6, mas apesar da tentativa de descaracterizar o modelo com essa imagem e replicar a inserção do driver como módulo de kernel, ainda não foi o suficiente para tornar visível a interface wlan0.

### Dia 12/09/2024
A solução para o problema de conectividade com Wi-Fi da X plus foi: utilizar arquivos de imagen Armbian mais antigos (em especial a versão rk322x 22.02.1, com o kernel legacy 4.4.194), procurar pelo driver de rede sem fio (que não estava presente em versões mais recentes do Armbian) e dar o comando ```sudo insmod ssv6x5x.ko``` . Isso tornou possível o reconhecimento das redes e resolveu o problema que restava para a X plus operar corretamente. Porém, até que seja encontrado um outro método mais fundamental, foi necessário recarregar o driver como módulo de kernel toda vez que o aparelho reiniciava, então como forma temporária de mitigar esse problema, foi utilizado o crontab para carregar o módulo em todo reinício do sistema.

### Dia 11/09/2024
H7

### Dia 20/08/2024:
Foi realizado um teste na TVbox Tiger 3 do aplicativo Kanagram (alfabetização) e o CodeBlocks. O kanagram rodou, no codeblocks apenas códigos simples foram testados, os quais funcionaram tranquilamente. 

### Dia 19/08/2024:
Foi realizados testes dos aplicativos educacionais : Kalzium(química), KBruch(matemática básica), KLetters(alfabetização). Na TVbox Tiger 3. Todos os 3 funcionam.

### Dia 15/08/2024:
O modelo investigado no dia em questão foi o RedPro2, cujas características podem ser verificadas no [modelos-e-hardwares](modelos-e-hardwares.md). Caracterizado pelo SoC amlogic s905x3, alguns testes foram efetuados seguindo o tutorial de [ophub](https://github.com/ophub/amlogic-s9xxx-armbian). E para seguir esse tutorial, foi escolhida a imagem  Armbian_24.8.0_amlogic_s905x3_noble_6.6.43_server_2024.08.01.img.gz.
Conforme explica o tutorial, duas coisas devem ser feitas para encontrar uma compatibilidade entre o software da imagem e a tv box: após flashar a imagem em um cartão sd, nos arquivos aparentes devem ser definidos u-boot e dtb (para saber mais sobre esse processo, verifique [desc-ha](Amlogic/HA/desc-ha.md) ). O u-boot escolhido foi o arquivo u-boot-s905x3.bin, e todos os dtb's da família SM1 constantes no arquivo [model_database.conf](https://github.com/ophub/amlogic-s9xxx-armbian/blob/main/build-armbian/armbian-files/common-files/etc/model_database.conf) foram testados. Infelizmente sem sucesso.
Aqui está uma print do início da tabela com os dtb's, encontrada a partir da linha 146 do arquivo .conf:
<img src="https://github.com/user-attachments/assets/46131425-5e56-4260-9142-7eba62bd484f" width=800>




### Dia 14/08/2024:
Novos modelos de tv box foram encontrados e os exemplares com SoC da Amlogic têm se mostrado extremamente promissores para descaracterização.

### Dia 09/08/2024:
Após encontrar um repositório do github chamado "tvbox", criado a partir de um projeto cujos objetivos sáo semelhantes aos deste, foram encontrados arquivos compatíveis com os modelos H7 e Btv 11. O único problema, que não é realmente um problema, é que o arquivo de imagem passado naquele projeto é um arquivo para sistema do tipo "server", que não fornece um desktop nativo e funciona apenas através de linha de comando.

### Dia 08/08/2024:
Algumas tentativas de encontrar arquivos compatíveis para os modelos com SoC Amlogic foram realizadas. Após o sucesso da HA, o modelo objetivo foi a H7, que conta com SoC de modelo s905x3. Mesmo com muitas tentativas envolvendo vários arquivos DTB's diferentes, não foi possível passar da tela de boot, que ficava em loop.

### Dia 31/07/2024:
Após encontrar e executar um script de instalação em um dos diretórios do próprio sistema presente no cartão sd, o burn do sistema foi efetivado no hardware da tv box. O script de instalação foi obtido após navegar para o diretório /root como super usuário. Deve-se notar que ao listar os arquivos, vários scripts podem ser encontrados. O usuário deve executar aquela que correponda ao processador da TV box.

### Dia 30/07/2024:
Seguindo a saga do modelo HA, foram encontradas e testadas imagens em um repositório do github que permitem a escolha do dtb e do bootloader correpondente a um determinado modelo. Uma dessas imagens foi bootada em um cartão SD e assim que o cartão SD foi colocado na tv box, o sistema funcionou. Algumas mensagens de erro foram apresentadas, porém nenhum problema foi identificado no teste superficial feito após o boot do sistema. O Wi-fi conectou normalmente. O único problema é que ao remover o cartão SD, o sistema também era removido, pois não estava efetivamente presente no hardware da TV box.

### Dia 29/07/2024:
Após uma troca de informações com os responsáveis pelo projeto do modelo X-plus foi constatado que algumas funcionalidades do arquivo de patch estão desatualizadas, portanto foi estabelecido de comum acordo entre os membros que a jornada da X-plus sofrerá um hiato até que sejam encontrados arquivos compatíveis ou outras metodologias.

Além disso, foi realizada uma tentativa de flash de uma imagem do Manjaro na tv box a partir do boot do cartão SD e da inserção na tv box HA. Após isso, o cartão sd foi recolhecido e fizemos o processo de configuração do Manjaro na tv box. De forma semelhante aos outros modelos testados não foi mostrada a opção de conectar na rede. Vale ressaltar que a imagem não conseguiu ser salvar na rom e no armazenamento interno, sendo assim o sistema só opera pelo cartão sd.

### Dia 25/07/2024
Algumas questões não explicadas do tutorial seguido no dia 23 foram melhor entendidas, como  os "Links úteis" da seção "caçando o bug da interface de rede". Na realidade aqueles links só contém os NOMES das FLAGS para o driver de ETHERNET que devem ser inseridos no arquivo config-6.6.22-current-rockchip, que pode ser encontrado ao entrar no diretório /boot. Mas no caso da imagem utilizada, essas flags já estavam setadas. Mesmo assim não foi tão trivial identificá-las a partir do arquivo imagem e será explicado brevemente como fazer isso através da montagem do sistema de arquivo do arquivo de imagem.

Para montar o sistema de arquivos de um arquivo de imagem de sistema operacional, antes é necessário preparar um diretório em que isso será feito, além de possuir esse arquivo de imagem. Vamos supor que o arquivo de imagem tenha o nome imagem.img e deseja-se montar o sistema de arquivos dessa imagem no diretório mnt/armbian. Para montar o sistema de arquivos é necessário ter conhecimento da partição em que esse sistema se encontra no disco de inicialização constante no arquivo de imagem. Isso pode ser realizado com o comando "sudo fdisk -l imagem.img". Explicação:
- fdisk: ferramenta de manipulação de tabelas de partição.
- -l: lista as tabelas de partição de todos os dispositivos de bloco (dispositivo de armazenamento de dados que gerencia dados em segmentos de tamanho fixo).
- imagem.img: Especifica o arquivo de imagem o qual deseja-se listar as tabelas de partição.

Supondo que o retorno do primeiro comando seja algo parecido com:


<img src="https://github.com/user-attachments/assets/197abad8-9c0d-4350-8671-a232f676fa54" width="900">


Temos que o dispositivo de bloco do arquivo de imagem tem um offset (deslocamento) de 8192 setores, sendo que cada setor equivale a 512 bytes.
Por esse motivo defini-se a variável offset, com o valor 512*8192 através do comando "offset=$((512 * 8192))". 

Agora sim, é possível executar o comando para montar o sistema de arquivos do arquivo de imagem imagem.img no diretório mnt/armbian através do comando "sudo mount -o loop,offset=$offset imagem.img /mnt/armbian". Explicação:
- mount: comando para montar sistema de arquivos.
- -o: especifica opções de montagem.
- loop: trata o arquivo de imagem como um dispositivo de bloco (loop device).
- offset: especifica o deslocamento do início da partição dentro do arquivo de imagem.
- /mnt/armbian: Ponto de montagem onde o sistema estará acessível.

  Finalmente, o sistema de arquivos presente na imagem pode ser explorado, e no diretório usado como ponto de montagem (no caso mnt/armbian), podemos encontrar sub diretórios como o seguinte:

  
  <img src="https://github.com/user-attachments/assets/aae0710f-b398-4781-b732-5292b523a0ee" width="900">


  Para finalizar, o trabalho desenvolvido nesse dia foi, de certa forma, complementar ao que foi desenvolvido no dia 23, pois agora o kernel da imagem original pode ser acessado e alterado de acordo com as novas configurações do kernel recompilado. E é isso que precisa ser feito para que o ciclo de sofrimento e cobrança termine.


### Dia 23/07/2024
Foi seguido o tutorial do site https://hackmd.io/@lbecher/SkPOdsNZ6#Ap%C3%AAndice para compilação do kernel, que apresentou os seguintes passos:

1º Passo: Clonar o repositório com o seguinte comando: git clone --depth 1 --branch v6.1 https://github.com/torvalds/linux.git. 
  Explicação: 
  - Depth 1: Clonagem do histórico mais recente;
  - branch v6.1: Baixa apenas o código do ramo v6.1;
  - Repositório oficial linux suportado por Linus Torvald.
              
 2º Passo: Baixar um compilador cruzado devido a incompatibilidade da arquitetura x86 com a  arquitetura ARM.
Para isso foi utilizado o comando: "sudo apt install crossbuild-essential-armhf libncurses5-dev libssl-dev bison flex".
 
 3º Passo: Baixar um patch para SoC rockchip rk3228 e copiar para pasta "linux" do repositório clonado.
   o Patch pode ser encontrado nesse link: https://www.dropbox.com/scl/fi/dftz18hi1ywb0f8kaz1m2/0001-linux-6.1.57.patch?   rlkey=to2zzcpytcpxk5mn3y45u7j42&e=1&dl=0.
    
 4° Passo: Aplicar o patch baixado/copiado através do comando "git apply /caminho/para/o/arquivo.patch --reject". O "--reject" é necessário para forçar atualizações.

 5° Passo: Especificar a arquitetura em que será compilado o kernel. Obs: Devem aplicados sempre que o terminal for fechado. Os comandos utilizados para tal são: "export ARCH=arm" e "export CROSS_COMPILE=arm-linux-gnueabihf-".

 O tutorial, no entanto, não foi seguido até o final, ficando algumas questões em aberto.
 
### Dia 19/07/2024
Pesquisas sobre como recompilar o kernel do sistema Armbian com um driver de rede compatível estão sendo feitas.

### Dia 18/07/2024
Após erros e mais erros por falta de atenção, foi descoberta uma forma de suceder que está para ser testada. A imagem pronta Armbian_24.2.5_Rk322x-box_bookworm_current_6.6.22_xfce_desktop.img não funcionou corretamente para o modelo X plus.


### Dia 15/07/2024
Organização de questões operacionais, divisão e planejamento foram feitos para otimizar a busca pela solução na jornada da X plus.

### Dia 11/07/2024:
Ainda não foi possível conectar o wifi e mais estudo deve ser voltado para esse propósito. Foi feita a apresentação para os voluntários.

### Dia 10/07/2024:
O uso de uma outra imagem pré-construída e descaracterização pelo processo do multitool deu retorno para um outro exemplar de X plus. Foi possível acessar algumas funcionalidades dessa vez, como as aplicações, além da interação do desktop com o mouse. Uma tentativa insistente de fazer com que o dispositivo reconheça o wi-fi sem ancoragem está sendo feita e uma familiaridade com a interface de usuário está sendo adquirida. Também foi descoberto que o exemplar inicial da X plus, supostamente "brickado", na verdade não estava retornando vídeo devido a um problema no monitor, no entanto uma mensagem pedia para reinstalar o sistema e após isso o terminal se tornou inacessível.

### Dia 09/07/2024:
Não foi possível reconhecer o dispositivo por cabo USB macho-macho no computador através da ferramenta USB burning tool. Foi constatado um problema no cabo HDMI, isso será verificado para aquele dispositivo em específico no dia 11/07/2024, porém é mais certo que algo deja descoberto utilizando o cabo com adaptador USB UART para acessar o console de log serial, conforme explicado por Nico D. e Werner no vídeo https://www.youtube.com/watch?v=UpVMO7gbnYM&t=250s .

### Dia 08/07/2024:
A tentativa de entrar no DFU no dia 5 não deu retorno por vídeo, mas será testado o reconheicmento da tvbox pelo software USB burning tool. Foi possível acessar o console do armbian pela combinação das teclas Ctrl+Alt+F1. Uma ancoragem pelo celular através de cabo USB foi feita para possibilitar a conexão com a internet, bem sucedida. No entanto, após a demora das atualizações pelo comando "sudo apt update && sudo apt upgrade -y" e a reinicialização do dispositivo, não foi mais possível inicializar normalmente, dado que uma tela preta aparecia no monitor. Por isso seria importante acessar a tv box pelo usb burning tool.

### Dia 05/07/2024:
Tentaremos entrar em DFU (mask rom mode) criando um curto no sétimo pino do armazenamento eMMC da x plus. caso não seja possível, tentaremos introduzir o cartão SD com o backup como imagem de sistema. Esta última opção se mostra promissora, ao passo que apesar de não ocorrer nada apenas iniciando o sistema com o cartão SD e o backup na pasta image do multitool, é possível parar o processo de boot e bootar de uma mídia externa.








