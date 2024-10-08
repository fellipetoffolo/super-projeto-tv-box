# Processo de descaracterização
Ao tentar descaracterizar esta tvbox pelo processo usual e conhecido para SoC's rockchip através do multitool, alguns problemas impediram que a descaracterização fosse bem sucedida. Aqui estão os problemas e as ações necessárias para contorná-los.

O primeiro problema é que o dispositivo não tem entrada para cartão SD e existem duas formas de resolver isso: uso de um adaptador USB cartão SD, ou utilizando a ferramenta rk_develop_tool com um cabo USB macho macho ligado a um computador.

Ao tentar a primeira abordagem bootando pelo multitool, já com o arquivo de imagem dentro da pasta "images" no cartão SD, não houve resposta, sendo que a tvbox inicializou seu firmware original normalmente. A outra possibilidade pensada, como já mencionado, foi o uso do rk_develop_tool, que é basicamente um software com funcionalidades semelhantes ao multitool, porém operado diretamente de uma outra máquina.

Para utilizar o rk_develop_tool foi seguido o tutorial para instalação sem o uso de cartão SD constante em [Installation (without SD card, board with eMMC)](https://forum.armbian.com/topic/34923-csc-armbian-for-rk322x-tv-box-boards/) (as etapas do tutorial demandam que isto seja feito em uma máquina linux). O segundo problema foi que após flashar a imagem com o rk_develop_tool, o aparelho não respondia mais... No entanto, não satisfeitos, tentamos utilizar o multitool com adaptador USB cartão SD após isso, e dessa vez o multitool pôde ser acessado. O mesmo passo a passo padrão de para instalar o sistema pelo multitool foi seguido, o que funcionou.

Infelizmente nenhum sinal de Wi-Fi foi detectado devido a falta d eum driver de rede compatível.
