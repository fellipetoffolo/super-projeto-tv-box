# <img src="/.assets/#.jpeg" alt="Imagem do case" width="30"/> Descaracterização do modelo X Plus

## 🔎 Sumário

- [Informações Gerais](#-informações-gerais)
  - [Descrição do modelo](#valore-de-hardware)
  - [Imagem do modelo](#imagem-do-modelo)
  - [Sistema operacional original](#sistema-operacional-original)
  - [Suporte de hardware](#suporte-de-rede)
  - [Limitaçoes conhecidas](#limitações-conhecidas)
- [Desempenho](#-desempenho)
- [Ferramentas utilizadas](#-ferramentas-utilizadas-para-descaracterização)
  - [Hardware](#hardware)
  - [Software](#software)
  - [Cuidados necessários](#cuidados-necessários)
- [Processo detalhado](#-processo-detalhado)
- [Erros comuns](#-erros-comuns)

## 💻 Informações gerais 


### Valores de hardware (Obtidas por meio da plataforma AIDA64)


| Medida                   | Valor detectado | Valor nominal |
| ------------------------ | --------------  | ------------- |
| CPU S905X                |      1.5 Mhz    |      1.5 Mhz  |
| Armazenamento interno    |      16 GB      |      16 GB    |
| Memória RAM              |      2 MB       |      2 GB     |


### Imagem do modelo

<img src="/.assets/tg3-box.png" alt="Imagem 1 da Box" width="300" style="transform: rotate(90deg);"/>
<img src="/.assets/tg3-placa.png" alt="Imagem 1 do hardware" width="300"/>

### Sistema operacional original

Android [INSERIR-VERSÃO] (pré-instalado).

### Suporte de rede (módulo [INSERIR-NOME-DO-MODELO] - driver [INSERIR-NOME-DO-MODELO])
- Wi-fi: Supostamente é suportado pelo Armbian.
- Bluetooth: Ainda não testado.<!-- Necessário confirmar -->
- Ethernet: Suporte completo.


## 📈 Desempenho

Confira nossa [metodologia de avaliação](material-de-apoio/glossario.md). <!-- Necessário criar arquivo de metodologia e linkar aqui -->

Valores para inserir:
- 🟠 MÉDIO
- 🔴 RUIM
- 🟢 BOM


| Atividades                   | Avaliação       |
| ---------------------------- | --------------- |
| Navegar em páginas           |  🟢 BOM        |
| Assistir vídeos              |  🟢 BOM        |
| Jogar                        |  🟢 BOM        |
| Utilizar como servidor       |  🟢 BOM         |

## 🛠 Ferramentas utilizadas para descaracterização

### Hardware

- Computador ou notebook: utilizado para manipular os arquivos necessários e criar um cartão SD bootável.
- Cartão SD: utilizado para gravar o sistema operacional Armbian na TG 3.
- Monitor, teclado, mouse e cabo HDMI: utilizado para interagir com a TG 3.

### Software

- Balena Etcher, Rufus ou dd: utilizado para gravar o multitool no cartão SD.

### Cuidados necessários

- Sempre ejete o cartão SD pelo sistema operacional antes de removê-lo do computador.
[OPCIONAL]:
- Baixe a imagem correta do Armbian. Os testes indicaram que as imagens customizadas fornecidas pelo repositório [ophub](https://github.com/ophub/amlogic-s9xxx-armbian/releases) tem uma maior compatibilidade para este modelo de processador em relação aos sistemas oficiais do projeto Armbian. As demais apresentaram diversos problemas de inicialização.


## 📖 Processo detalhado

### Preparação para instalação

_Disclaimer1: Caso algum termo não seja compreendido, verifique-o na seção [glossário](material-de-apoio/glossario.md)_

_Disclaimer2: Muitos modelos com [SoC](material-de-apoio/glossario.md#SoC) Amlogic S905X3 tiveram problema de compatibilidade com as imagens oficiais geradas pelo projeto Armbian, isso se deve em especial por causa do u-boot, responsável por inicializar o sistema. Para isso foram encontradas duas soluções: modificiar manualmente os scripts para inicializar o sistema através de bootloader proprietário, ou utilizar imagens de um projeto extra-oficial, que possuem u-boots selecionados para cada arquivo [dtb](material-de-apoio/glossario.md#dtb). Aqui utilizaremos a segunda solução._

1. Baixe os software e arquivos necessários no computador/notebook.
  - Software de criação de mídia bootável (baixe apenas um de sua escolha)
     - Recomendado: [Balena Etcher (Tutorial de instalação e uso)](https://etcher.balena.io/)
     - Alternativa: [Rufus (Tutorial de instalação e uso)](https://rufus.ie/pt_BR/)
     - Alternativa: [dd (Tutorial de instalação e uso)](https://medium.com/@emusyoka759/creating-a-bootable-usb-in-ubuntu-with-dd-9fb3debc0814)
  - Imagem do Armbian (variante do projeto ophub)
     - [Armbian 20.10.0 bullseye(adiconar o link)]() 

    
2. No computador/notebook, insira o cartão SD e Utilize um dos programas anteriores para gravar a imagem no cartão SD.
3. Entre no diretório raiz do cartão SD após a gravação da imagem, onde diversas pastas e arquivos com extensão .bin podem ser encontrados.
4. Abra o arquivo uEnv.txt com um editor de texto qualquer e substitua o que estiver escrito após a última barra na linha que começa por "fdt" por "meson-sm1-tx3-bz-oc.dtb". Salve o arquivo e feche.
5. Faça uma cópia do arquivo u-boot-tx3-bz.bin, também presente no diretório raiz do cartão SD, e renomeie essa cópia para u-boot.ext.
6. Remova o cartão SD do computador/notebook.
  - Ejete o cartão SD pelo sistema operacional antes de removê-lo, para evitar possível corrupção. 
7. Insira o cartão SD na RedPro2 desligada e conectada à um monitor/televisão por cabo HDMI.
8. Pressione o botão reset com um clip de papel desdobrado (o botão pode ser encontrado dentro de um "furo" na parte debaixo da TV Box) e conecte a fonte de alimentação enquanto o botão ainda estiver pressionado. Mantenha o botão de reset pressionado e solte assim que algum sinal de vídeo for observado no monitor/televisão. 

⚠️Lembre-se⚠️: o sistema está funcionando por meio do cartão SD, ou seja, caso removido, o firmware original da tv box ascenderá novamente, mas nunca retire o cartão SD com o aparelho ligado. Um tópico mais a frente ensinará a gravar o sistema no armazenamento interno, apagando todo o firmware original da TV Box.


### Configuração do Armbian

Após iniacializar o sistema pela primeira vez, é pedido ao usuário que forneça algumas informações de configuração, como nome de usuário, senha, configuração de zonas de tempo e afins. O processo é bem intuitivo. mas caso haja dúvida, utilize o nosso [guia para configuração inicial do Armbian](#).

### Instalação do sistema no armazenmento interno

⚠️Lembre-se⚠️: para cumprir essa etapa, é muito importante que uma cópia do u-boot correto tenha sido feita, conforme a etapa 5 da **Preparação para instalação**.

Após a configuração, execute o comando 

```bash
sudo armbian-install -m no
```

E confirme o que for pedido


## ❌ Erros comuns

**Ainda não identificados**



