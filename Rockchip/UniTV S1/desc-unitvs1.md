# <img src="/.assets/unitv-box.jpeg" alt="Imagem do case" width="30"/> Descaracterização do modelo UniTV S1

## 🔎 Sumário

- [Informações Gerais](#-informações-gerais)
  - [Descrição do modelo](#descrição-do-modelo)
  - [Imagem do modelo](#imagem-do-modelo)
  - [Sistema operacional original](#sistema-operacional-original)
  - [Suporte de hardware](#suporte-de-hardware)
  - [Limitaçoes conhecidas](#limitações-conhecidas)
- [Desempenho](#-desempenho)
- [Ferramentas utilizadas](#-ferramentas-utilizadas)
  - [Hardware](#hardware)
  - [Software](#software)
- [Processo resumido](#-processo-resumido)
  - [Cuidados necessários](#cuidados-necessários)
  - [Passo a passo](#passo-a-passo)
- [Processo detalhado](#-processo-detalhado)
- [Erros comuns](#-erros-comuns)

## 💻 Informações gerais


### Valores de hardware (Obtidas por meio da plataforma AIDA64)


| Medida                   | Valor detectado| Valor nominal |
| ------------------------ | -------------- | ------------- |
| CPU RK3228A              |     1296 Mhz   |     1,2 Ghz   |
| Armazenamento interno    |     4436 MB    |      8 GB     |
| Memória RAM              |      995 MB    |      1 GB     |


É um modelo relativamente simples de ser descaracterizado, mas alguns passos extras devem ser feitos para garantir que o Wi-fi funcione adequadamente.
Verifique as especificações completas de hardware da UniTV S1 [aqui](https://github.com/fellipetoffolo/super-projeto-tv-box/blob/main/informacoes-modelos-e-hardwares.md#unitv-s1).

### Imagem do modelo

<img src="/.assets/unitv-box.jpeg" alt="Imagem do case" width="300"/>
<img src="/.assets/unitv-placa.jpeg" alt="Imagem 1 do hardware" width="300"/>

### Sistema operacional original

Android (pré-instalado).  

### Suporte de rede ( módulo realtek rtl8723ds - driver rtl8723ds)
- Wi-fi: Suporte completo.
- Bluetooth: Ainda não testado.<!-- Necessário confirmar -->
- Ethernet: Suporte completo.


### Limitações conhecidas
- Entradas para periféricos: Não possui entrada para cartão SD, porém isso pode ser mitigado pelo uso de um adaptador ou cabo USB macho-macho.


## 📈 Desempenho

Confira nossa [metodologia de avaliação](material-de-apoio/glossario.md). <!-- Necessário criar arquivo de metodologia e linkar aqui -->

| Atividades                   | Avaliação |
| ---------------------------- | --------- |
| Navegar em páginas           | 🟠 MÉDIO |
| Assistir vídeos              | 🟠 MÉDIO |
| Jogar                        | 🔴 RUIM  |
| Utilizar como servidor       | 🟢 BOM   |

## 🛠 Ferramentas utilizadas para descaracterização

### Hardware

- Computador ou notebook: utilizado para manipular os arquivos necessários e criar um cartão SD bootável.
- Cabo USB macho-macho: utilizado para gravar o sistema operacional Armbian na UniTV S1 (primeira gravação).
- (opcional) Cartão SD: utilizado para gravar o sistema na TV Box após a primeira gravação desbloquear o modelo. 
- (opcional) Adaptador USB para cartão SD: utilizado para conectar o cartão SD, necessário devido à ausência de entrada própria.
- Monitor, teclado, mouse e cabo HDMI: utilizado para interagir com a UniTV S1.

### Software

- Balena Etcher, Rufus ou dd: utilizado para gravar o multitool no cartão SD.
- Multitool: utilizado para gravar o sistema operacional Armbian no armazenamento interno da UniTV S1. 

## 📄 Processo resumido

### Cuidados necessários

- Sempre ejete o cartão SD pelo sistema operacional antes de removê-lo.
- Baixe a imagem correta do Armbian, para evitar problemas com Wi-fi.
- Sempre selecione "Shutdown" ao desligar a UniTV S1 com multitool iniciado.

### Passo a passo

1. Utilize Balena Etcher, Rufus ou dd para criar um SD bootável, utilizando a imagem do multitool.
2. Redimensione as partições do multitool. Para isso:
   - Remova o cartão SD do computador/notebook.
   - Insira na UniTV S1 e ligue-a.
   - Desligue a UniTV S1 e insira o cartão SD no computador/notebook novamente.
3. Copiar imagem do Armbian para o diretório "images" no multitool.
4. Inserir cartão SD na UniTV S1 e gravar a imagem do Armbian no armazenamento interno da UniTV S1.
   - OPCIONAL: realizar backup da imagem original da UniTV S1.
5. Ligar a UniTV S1 sem o cartão SD.
6. Realizar configurações iniciais do Armbian.
7. Iniciar driver Wi-fi.
8. Remover driver Wi-fi da blacklist do sistema.

## 📖 Processo detalhado

### Preparação

1. Baixe os software e arquivos necessários.
  - Software de criação de mídia bootável (baixe apenas um)
     - [Balena Etcher (Tutorial de instalação e uso)](https://etcher.balena.io/)
     - [Rufus (Tutorial de instalação e uso)](https://rufus.ie/pt_BR/)
     - [dd (Tutorial de instalação e uso)](https://medium.com/@emusyoka759/creating-a-bootable-usb-in-ubuntu-with-dd-9fb3debc0814)
  - Imagem do Armbian
     - [Armbian com interface gráfica](https://unioestebr-my.sharepoint.com/:u:/g/personal/renan_silva15_unioeste_br/EdRFhkzL309CmdtL13XVPZABvpNkqTUbQvxo-w272nMrmQ?e=VOyTvT) 
     - Armbian sem interface gráfica 
  - Multitool
    - [Tutorial de instalação e uso](https://forum.armbian.com/topic/34923-csc-armbian-for-rk322x-tv-box-boards)
    
2. Utilize um dos programas anteriores para gravar a imagem do multitool no cartão SD.
  - Após a gravação, note que as partições do multitools são pequenas e não há espaço para a imagem. Por isso, o próximo passo é necessário.
3. Remova o cartão SD do computador/notebook.
  - Ejete o cartão SD pelo sistema operacional antes de removê-lo, para evitar possível corrompimento. 
4. Insira o cartão SD na UniTV S1 e ligue-a.
5. Selecione a opção "Shutdown" e desligue a UniTV S1.
6. Insira o cartão SD novamente no computador/notebook.
7. Mova a imagem desejada do Armbian para o diretório "MULTITOOL/images".
8. Remova o cartão SD do notebook novamente (lembre-se de ejetar antes).

### Instalação

1. Insira o cartão SD (já com multitool e a imagem do Armbian) na UniTV S1 e ligue-a.
2. Selecione a opção "Burn image to flash".
   - OPCIONAL: fazer backup da imagem original da UniTV S1. Ao fazer backup, a imagem original será armazenada em "MULTITOOL/backup".
3. Selecione o armazenamento interno (só haverá um).
4. Selecione a imagem que será gravada no armazenamento interno (a que foi baixada e movida para "MULTITOOL/images").
5. Aguarde o processo de gravação terminar.
6. Após terminar, selecione "Shutdown" e desligue a UniTV S1.
7. Remova o cartão SD da UniTV S1.

### Configuração do Armbian

1. Ligue a UniTV S1 sem o cartão SD.
2. Digite a senha do root (usuário administrador).
3. Digite o nome de usuário. Por padrão, sempre definimos como "tvbox".
4. Digite e confirme a senha do usuário. Por padrão, sempre definimos como "40028922".
5. Abra o terminal (bash).
6. Digite o seguinte comando para ativar o driver Wi-fi:
   - ```bash
     sudo insmod /lib/modules/$(uname -r)/kernel/drivers/net/wireless/ssv6x5x/ssv6x5x.ko
     ```
7. Edite o arquivo "/etc/modprobe.d/blacklist-rk322x-box.conf" e remova a linha "blacklist ssv6x5x".
  - Exemplo utilizando o editor de texto nano:
     ```bash
     sudo nano /etc/modprobe.d/blacklist-rk322x-box.conf
     ```
    - Remova a linha "blacklist ssv6x5x".
    - CTRL + X (para sair).
    - Y (para confirmar alterações).
    - ENTER (para confirmar nome do arquivo).

## ❌ Erros comuns

### Interface gráfica demorando muito para carregar

Para contornar isso, é possível entrar com o terminal simples e iniciar a interface gráfica posteriormente. Para isso:
- CTRL + ALT + F1: Para entrar no terminal.
- Para iniciar interface gráfica:
  ```bash
  startx
  ```
