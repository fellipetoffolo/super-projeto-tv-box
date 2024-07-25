# Processos em andamento da X plus

## META DA SEMANA: 

#### Recompilar o kernel do Armbian para X-plus com os drivers de rede corretos.

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










