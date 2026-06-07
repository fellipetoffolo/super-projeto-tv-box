# <img src="https://github.com/user-attachments/assets/670f65d9-02a0-4135-96d1-3a953d144429" alt="Imagem do case" width="30"/> Descaracterização do modelo Xplus pro

## 🔎 Sumário

- [Informações Gerais](#-informações-gerais)
  - [Valores de Hardware](#valore-de-hardware)
  - [Imagem do modelo](#imagem-do-modelo)
  - [Sistema operacional original](#sistema-operacional-original)
  - [Suporte de rede](#suporte-de-rede)
- [Desempenho](#-desempenho)
- [Ferramentas utilizadas para descaracterização](#-ferramentas-utilizadas-para-descaracterização)
  - [Hardware](#hardware)
  - [Software](#software)
- [Processo detalhado](#-processo-detalhado)
  - [Cuidados necessários](#cuidados-necessários)
  - [Preparação para instalação](#preparação-para-instalação)
  - [Configuração inicial do Armbian](#Configuração-do-Armbian)
  - [Instalação do sistema no armazenamento interno](#instalação-do-sistema-no-armazenamento-interno)
- [Erros comuns](#-erros-comuns)

## 💻 Informações gerais 

⚠️ _Até o momento apenas se tem registro de suporte do processador Amlogic S905X4 por meios extraoficiais, ou seja, até onde se sabe apenas um desenvolvedor encontrou uma forma de bootar o sistema em placas com esse processador, independente do projeto Armbian. O que é utilizado nesse tutorial foi baseado no trabalho de [Devmfc](https://github.com/devmfc/debian-on-amlogic/releases)._

### Valores de hardware (Obtidas por meio da plataforma AIDA64)


| Medida                   | Valor detectado | Valor nominal |
| ------------------------ | --------------  | ------------- |
| CPU S905X4               |     2004 MHz    |     1,9 GHz   |
| Armazenamento interno    |       64 GB     |      64 GB    |
| Memória RAM              |      4 GB       |      4 GB     |



### Imagem do modelo

<img src="/.assets/Xplus pro-box.jpeg" alt="Imagem do case" width="300"/>
<img src="/.assets/Xplus pro-placa.jpeg" alt="Imagem 1 do hardware" width="300"/>


### Sistema operacional original

Android 11 (pré-instalado).

### Suporte de rede (módulo REALTEK rtl8822cs - driver rtl8822cs)
- Wi-fi: Até o momento não suportado pelo desenvolvedor.
- Bluetooth: Ainda não testado.<!-- Necessário confirmar -->
- Ethernet: Suporte completo.


## 📈 Desempenho **Ainda não testado**

 <!-- Necessário criar arquivo de metodologia e linkar aqui -->

## 🛠 Ferramentas utilizadas para descaracterização

### Hardware

- Computador ou notebook: utilizado para manipular os arquivos necessários e criar um cartão SD bootável.
- Cartão SD: utilizado para gravar o sistema operacional Armbian na Xplus pro.
- Monitor, teclado, mouse e cabo HDMI: utilizado para interagir com a Xplus pro.

### Software

- Balena Etcher, Rufus ou dd: utilizado para gravar o sistema no cartão SD.



## 📖 Processo detalhado


### Cuidados necessários

- Sempre ejete o cartão SD pelo sistema operacional antes de removê-lo do computador.
- Baixe a imagem correta do Armbian, os testes indicaram que tem uma maior compatibilidade àquelas fornecidas pelo repositório [ophub](https://github.com/ophub/amlogic-s9xxx-armbian/releases). As demais apresentaram diversos problemas.


### Preparação para instalação

_Disclaimer1: Caso algum termo não seja compreendido, verifique-o na seção [glossário](material-de-apoio/glossario.md)_


1. Baixe os software e arquivos necessários.
  - Software de criação de mídia bootável (baixe apenas um de sua escolha)
     - Recomendado: [Balena Etcher (Tutorial de instalação e uso)](https://etcher.balena.io/)
     - Alternativa: [Rufus (Tutorial de instalação e uso)](https://rufus.ie/pt_BR/)
     - Alternativa: [dd (Tutorial de instalação e uso)](https://medium.com/@emusyoka759/creating-a-bootable-usb-in-ubuntu-with-dd-9fb3debc0814)
  - Imagem do Armbian (variante do desenvolvedor Devmfc):
     - [Armbian 25.01.24 server](https://unioestebr-my.sharepoint.com/:u:/g/personal/renan_silva15_unioeste_br/Eco3WdFTjgFAl14BE9bawZUBg2zInYpoMgwentVV45L9tw?e=md5EBY ) 

    
2. Utilize um dos programas anteriores para gravar a imagem no cartão SD.
3. Entre no diretório raiz do cartão SD após a gravação da imagem.
4. Abra o arquivo boot (ou boot.config) com um editor de texto qualquer e descomente a linha "#box=x96x4", apagando o "#". Salve o arquivo e feche normalmente.
5. Remova o cartão SD do computador/notebook.
  - Ejete o cartão SD pelo sistema operacional antes de removê-lo, para evitar possível corrupção. 
6. Insira o cartão SD na Xplus pro desligada e conectada à um monitor/televisão por cabo HDMI.
7. Pressione o botão reset com um clip de papel desdobrado ou um palito de dente (o botão pode ser encontrado em um "furo" na parte debaixo da TV Box) e conecte a fonte de alimentação enquanto o botão ainda estiver pressionado. Mantenha o botão de reset pressionado e solte assim que algum sinal de vídeo for observado no monitor/televisão.



⚠️Lembre-se⚠️: o sistema está funcionando por meio do cartão SD, ou seja, caso removido, o firmware original da tv box ascenderá novamente, mas nunca retire o cartão SD com o aparelho ligado. Um tópico mais a frente ensinará a gravar o sistema no armazenamento interno, apagando todo o firmware original da TV Box.


## ⚙️ Configuração do Armbian

Após inicializar o sistema pela primeira vez, é pedido ao usuário que forneça algumas informações de configuração, como nome de usuário, senha, configuração de zonas de tempo e afins. O processo é bem intuitivo. mas caso haja dúvida, utilize o nosso [guia para configuração do Armbian](#).

### Instalação do sistema no armazenamento interno

⚠️Cuidado⚠️: Esta ação vai apagar todos os dados presentes no armazenamento da sua TV Box!

Caso sua X Plus Pro não esteja com acesso a internet, siga estes passos:

1. Baixe os pacotes rsync e dosfstools para arm64.
  - [rsync_3.2.7-1ubuntu1.2_arm64.deb](https://ubuntu.pkgs.org/24.04/ubuntu-updates-main-arm64/rsync_3.2.7-1ubuntu1.2_arm64.deb.html)
  - [dosfstools_4.2-1build3_arm64.deb](https://ubuntu.pkgs.org/22.04/ubuntu-main-arm64/dosfstools_4.2-1build3_arm64.deb.html)
2. Insira o cartão SD no seu computador
  - Vá na partição ROOTFS
  - Acesse a pasta root
  - Coloque os dois pacotes na pasta
3. Ejete o cartão SD e insira na X Plus
4. Após ligar e fazer o login, use o comando ```ls``` para verificar que os pacotes estão na pasta root
5. Instale os pacotes usando o comando dpkg
  - ```dpkg -i ./dosfstools_4.2-1build3_arm64.deb```
  - ```dpkg -i ./rsync_3.2.7-1ubuntu1.2_arm64.deb```
6. Após instalados rode o script para instalar na memória flash interna com ```./aml-install-to-emmc.sh```

**⚠️Cuidado⚠️: Este script deve funcionar corretamente, mas tem chances de brickar a TV Box!**

7. Espere o script executar e após finalizado, desligue a x plus e remova o cartão SD
8. Ligue de novo sem o cartão e verifique se está tudo corretamente instalado.

### Instalação do Desktop (Em desenvolvimento)

<!--Até o momento, não sei como instalar o desktop, essa distro do Armbian vem com um script chamado desktop_minimal.sh mas esse precisa de internet,
e pra instalar o driver de internet precisa de inumeros outros pacotes,
se alguém tiver paciência de ir atrás disso ou perguntar pros veteranos por favor adicionem aqui 🥀-->

## ❌Erros comuns

**Ainda não identificados**




