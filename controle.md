# Processos em andamento da X plus

## META DA SEMANA: 

#### Recompilar o kernel do Armbian para X-plus com os drivers de rede corretos.

### Dia 23/07/2024
Foi seguido o tutorial do site: https://hackmd.io/@lbecher/SkPOdsNZ6#Ap%C3%AAndice para compilação do kernel.

 1º passo: Clonar o seguinte repositório: git clone --depth 1 --branch v6.1 
  Link utilizado: https://github.com/torvalds/linux.git. 
  Explicação: 
              *depth 1: Especifica que a a clonagem do histórico é a mais recente;
              *branch v6.1: Baixa apenas o código do ramo v6.1;
              *Repositório oficial linux suportado por Linus Torvald.
              
 2º passo: Baixar um compilador cruzado devido a incompatibilidade da arquitetura x86 com a  arquitetura ARM: sudo apt install crossbuild-essential-armhf libncurses5-dev libssl-dev bison flex.
 3º passo: Baixar um patch para SoC rockchip rk3228 e copiar para pasta linux do repositório clonado:
  Link utilizado: https://www.dropbox.com/scl/fi/dftz18hi1ywb0f8kaz1m2/0001-linux-6.1.57.patch?   rlkey=to2zzcpytcpxk5mn3y45u7j42&e=1&dl=0.
 4° passo: Aplicar o patch baixado/copiado através do comando git apply /caminho/para/o/arquivo.patch --reject.
 5° passo: Especificação da arquitetura que será compilada. Obs: Devem ser definidos sempre   que o terminal for fechado: export ARCH=arm || export CROSS_COMPILE=arm-linux-gnueabihf- 
 
### Dia 19/07/2024
Pesquisas sobre como recompilar o kernel do sistema Armbian com um driver de rede compatível estão sendo feitas.

### Dia 18/07/2024
Após erros e mais erros por falta de atenção, foi descoberta uma forma de suceder que está para ser testada. A imagem pronta Armbian_24.2.5_Rk322x-box_bookworm_current_6.6.22_xfce_desktop.img não funcionou corretamente para o modelo X plus.


### Dia 15/07/2024
Organização de questões operacionais, divisão e planejamento foram feitos para otimizar a busca pela solução na jornada da X plus. Divisão de duas equipes. A partir deste momento as equipes serão identificadas no log diário.

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










