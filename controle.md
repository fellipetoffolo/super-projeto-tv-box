# Processos em andamento da X plus
### Dia 05/07/2024:
Tentaremos entrar em DFU (mask rom mode) criando um curto no sétimo pino do armazenamento eMMC da x plus. caso não seja possível, tentaremos introduzir o cartão SD com o backup como imagem de sistema. Esta última opção se mostra promissora, ao passo que apesar de não ocorrer nada apenas iniciando o sistema com o cartão SD e o backup na pasta image do multitool, é possível parar o processo de boot e bootar de uma mídia externa.


### Dia 08/07/2024:
A tentativa de entrar no DFU no dia 5 não deu retorno por vídeo, mas será testado o reconheicmento da tvbox pelo software USB burning tool. Foi possível acessar o console do armbian pela combinação das teclas Ctrl+Alt+F1. Uma ancoragem pelo celular através de cabo USB foi feita para possibilitar a conexão com a internet, bem sucedida. No entanto, após a demora das atualizações pelo comando "sudo apt update && sudo apt upgrade -y" e a reinicialização do dispositivo, não foi mais possível inicializar normalmente, dado que uma tela preta aparecia no monitor. Por isso seria importante acessar a tv box pelo usb burning tool.

### Dia 09/07/2024:
Não foi possível reconhecer o dispositivo por cabo USB macho-macho no computador através da ferramenta USB burning tool. Foi constatado um problema no cabo HDMI, isso será verificado para aquele dispositivo em específico no dia 11/07/2024, porém é mais certo que algo deja descoberto utilizando o cabo com adaptador USB UART para acessar o console de log serial, conforme explicado por Nico D. e Werner no vídeo <a href=https://www.youtube.com/watch?v=UpVMO7gbnYM&t=250s> .

### Dia 10/07/2024:
O uso de uma outra imagem pré-construída e do multitool deu retorno para um outro modelo de x plus. Foi possível acessar algumas funcionalidades dessa vez, como as aplicações, além da interação do desktop com o mouse. Uma tentativa insistente de fazer com que o dispositivo reconheça o wi-fi sem ancoragem está sendo feita e uma familiaridade com a interface de usuário está sendo adquirida.

## Fotografias dos modelos:
##### Tourobox: True
##### X plus in: True
##### X plus pro: True
##### H8: False
##### H7: True
##### H6: False
##### Ximibox plus: False
##### btv: True
##### TG3: False



