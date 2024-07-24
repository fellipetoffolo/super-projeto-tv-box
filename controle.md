# Processos em andamento da X plus

## META DA SEMANA: 

#### Recompilar o kernel do Armbian para X-plus com os drivers de rede corretos.

### Dia 23/07/2024
Fizeram alguma coisa no dia em que faltei, mas pra variar esqueceram de documentar. Quando lerem isso eles vão lembrar  👍
 
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










