# Processo geral e dicas de descaracterização para tv's Box com o SoC Rockchip

#### Siga este tutorial caso você tenha aberto sua tvbox e encontrado o nome "Rockchip RK3228A" no processador

A comunidade Armbian possui diversas contribuições acumuladas para tornar seu sistema compatível com as placas de processador Rockchip RK3228A.
Tendo em vista que o processo de descaracterização segue o mesmo princípio para a maioria das placas com este SoC, aqui colocamos o processo geral de descaracaterização, com etapas mais diretas para instalar o sistema Armbian. Em nenhuma hipótese este tutorial resume o processo de instalação do sistema para todos os modelos e as infinitas possibilidades de combinações de SoC, armazenamento interno, módulo de rede e memória RAM que existem no mercado de tvbox, mesmo restritas ao processador da Rockchip, então recomendamos verificar primeiro o arquivo com o tutorial para o seu modelo específico e caso ele mencione este tutorial, siga as instruções aqui postadas.

Este tutorial é baseado em um tópico postado no fórum Armbian disponível no link [CSC Armbian for RK322x TV box boards](https://forum.armbian.com/topic/34923-csc-armbian-for-rk322x-tv-box-boards/)

## Parte 1: preparação
Primeiramente, é necessário possuir alguns equipamentos físicos para fazer a instalação do sistema Armbian numa tvbox. Estes equipamentos são:
1. Cartão SD: vai armazenar o sistema que será instalado na tv box.
2. Computador: vai preparar o cartão SD para instalar o sistema na tv box através de um programa chamado Balena Etcher
3. Tv box, uma fonte de alimentação, um cabo HDMI e um monitor (pode ser uma televisão).

De maneira semelhante, alguns programas e arquivos serão necessários:
1. Balena Etcher
2. Arquivo com o sistema armbian específico para tvbox com SoC Rockchip RK322X
3. Arquivo com o programa Multitool: vai carregar o sistema instalado na tv box.

## Parte 2: passo a passo

### Etapa 1
Acesse o [link](https://forum.armbian.com/topic/34923-csc-armbian-for-rk322x-tv-box-boards/) no qual este tutorial foi baseado e baixe o arquivo multitool. Você pode encontrar esse arquivo mais facilmente pressionando "Ctrl + F" e digitando "multitool" na página do tutorial.

 <img src="https://github.com/user-attachments/assets/3ef67367-76d9-47fc-9264-c924c48d85ac" alt="Captura de tela do projeto" width="400">


### Etapa 2
Faça download e instalação do [Balena Etcher](https://etcher.balena.io/) em seu computador.

 <img src="https://github.com/user-attachments/assets/5c8e6408-ac5b-45c7-b859-2ad2d78882d7" alt="Captura de tela do projeto" width="400">


### Etapa 3
Procure por um arquivo de imagem do sistema operacional Armbian compatível com tvbox Rockchip. Estes arquivos podem ser encontrados em várias discussões e links espalhados pelo fórum Armbian, além da possibilidade de construí-los diretamente pelo Framework fornecido pela comunidade. Alguns arquivos de imagem podem ser encontrados no tópico "links-importantes.md".

### Etapa 4
Insira o cartão SD no computador.
Abra o Balena Etcher, que apresentará a seguinte interface:

 <img src="https://github.com/user-attachments/assets/05361198-2c11-47bf-aeed-724f5f170a1f" alt="Captura de tela do projeto" width="400">

Selecione a opção "Flash from file" e procure o arquivo do multitool que foi baixado anteriormente.
Selecione a opção "Select target", procure e ecolha o cartão SD que foi inserido no computador. Caso o cartão SD não seja encontrado, ele pode estar com defeito ou precisa ser reparado.
Selecione a opção "Flash!" e aguarde.

### Etapa 5
Após a etapa anterior, o cartão SD já deve estar operando normalmente com o multitool, mas o arquivo do sistema Armbian ainda não entrou em cena. Isso porquê precisamos expandir a partição (armazenamento) do multitool para que ele possa comportar um arquivo de imagem do sistema, que geralmente é grande. Para isso, precisamos ejetar o cartão SD com segurança do computador e colocá-lo na tvbox desligada com a fonte de alimentação desligada. Após isso devemos conectar a fonte de alimentação
