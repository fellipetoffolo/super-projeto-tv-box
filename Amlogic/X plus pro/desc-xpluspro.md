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
  - [Configuração inicial do Armbian](#configuração-inicial-do-armbian)
  - [Instalação do sistema no armazenamento interno](#instalação-do-sistema-no-armazenmento-interno)
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

Confira nossa [metodologia de avaliação](material-de-apoio/glossario.md). <!-- Necessário criar arquivo de metodologia e linkar aqui -->


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


### Configuração do Armbian

Após iniacializar o sistema pela primeira vez, é pedido ao usuário que forneça algumas informações de configuração, como nome de usuário, senha, configuração de zonas de tempo e afins. O processo é bem intuitivo. mas caso haja dúvida, utilize o nosso [guia para configuração do Armbian](#).

### Instalação do sistema no armazenmento interno (**Em desenvolvimento**)

⚠️Cuidado⚠️: Esta ação vai apagar todos os dados presentes no armazenamento da sua TV Box, convém fazer um backup.




## ❌ Erros comuns

**Ainda não identificados**

