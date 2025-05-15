# <img src="../../.assets/b11-perfil.png" alt="Imagem de perfil" width="30" height="40"/> Descaracterização do modelo b11

## 🔎 Sumário

- [Informações Gerais](#💻-informações-gerais)
  - [Valores de Hardware](#valores-de-hardware)
  - [Imagem do modelo](#imagem-do-modelo)
  - [Sistema operacional original](#sistema-operacional-original)
  - [Suporte de rede](#suporte-de-rede)
- [Desempenho](#📈-desempenho)
- [Ferramentas utilizadas para descaracterização](#🛠-ferramentas-utilizadas-para-descaracterização)
  - [Hardware](#hardware)
  - [Software](#software)
- [Descaracterização: Processo detalhado](#📖-descaracterização-processo-detalhado)
  - [Cuidados necessários](#cuidados-necessários)
  - [Inicializando o Armbian na TV Box pelo cartão SD](#inicializando-o-armbian-na-tv-box-pelo-cartão-sd)
  - [Configuração inicial do Armbian](#configuração-inicial-do-armbian)
  - [Instalação do sistema no armazenamento interno](#instalação-do-sistema-no-armazenmento-interno)
- [Erros comuns](#❌-erros-comuns)

## 💻 Informações gerais

### Valores de hardware

(Os valores na tabela abaixo foram obtidos por meio da plataforma AIDA64)

| Medida                   | Valor detectado | Valor nominal |
| ------------------------ | --------------  | ------------- |
| CPU S905X3               |     1908 Mhz    |     1,9 Ghz   |
| Armazenamento interno    |     11,13 GB    |      16 GB    |
| Memória RAM              |      2000 MB    |      2 GB     |

### Imagem do modelo

<img src="../../.assets/b11-placa.png" alt="Imagem do circuito" width="300"/>
<img src="../../.assets/b11-box.png" alt="Imagem do modelo" width="300"/>

### Sistema operacional original

Android (pré-instalado).

### Suporte de rede (módulo Realtek rtl8822cs - driver rtl8822cs)

⚠️ _Até o momento não foi obtido nenhum suporte para Wi-Fi, mas [discussões no fórum Armbian](https://forum.armbian.com/topic/16696-armbian-for-tanix-tx3-amlogic-s905x3-with-sp6330-wifibluetooth-module/) sugerem que ele pode ser configurado seguindo uma série de passos._

O módulo de rede identificado para esse modelo é o: **Ampak AP6330**, para o qual o driver correspondente ainda não foi corretamente identificado, mas está relacionado a uma configuração dos arquivos no diretório **lib/aarch-64/firmware/**.

- Wi-fi: Supostamente é suportado pelo Armbian.
- Bluetooth: Ainda não testado.<!-- Necessário confirmar -->
- Ethernet: Suporte completo.

## 📈 Desempenho

| Atividades                   | Avaliação |
| ---------------------------- | --------- |
| Navegar em páginas           | 🟢 BOM   |
| Assistir vídeos              | 🟢 BOM   |
| Jogar                        | 🟠 MÉDIO |
| Utilizar como servidor       | 🟢 BOM   |

## 🛠 Ferramentas utilizadas para descaracterização

### Hardware

- Computador ou notebook: utilizado para manipular os arquivos necessários e criar um cartão SD bootável.
- Cartão SD: utilizado para gravar o sistema operacional Armbian na B11.
- Monitor, teclado, mouse e cabo HDMI: utilizado para interagir com a B11.

### Software

- Balena Etcher, Rufus ou dd: utilizado para gravar o sistema no cartão SD.

## 📖 Descaracterização: Processo detalhado

### Cuidados necessários

- Sempre ejete o cartão SD pelo sistema operacional antes de removê-lo do computador.
- Baixe a imagem correta do Armbian. Os testes indicaram que as imagens customizadas fornecidas pelo repositório [ophub](https://github.com/ophub/amlogic-s9xxx-armbian/releases) tem uma maior compatibilidade para este modelo de processador em relação aos sistemas oficiais do projeto Armbian. As demais apresentaram diversos problemas de inicialização.

### Inicializando o Armbian na TV Box pelo cartão SD

_Disclaimer1: Caso algum termo não seja compreendido, verifique-o na seção [glossário](../../material-de-apoio/glossario.md)_

_Disclaimer2: Muitos modelos com [SoC](../../material-de-apoio/glossario.md#SoC) Amlogic S905X3 tiveram problema de compatibilidade com as imagens oficiais geradas pelo projeto Armbian, isso se deve em especial por causa do u-boot, responsável por inicializar o sistema. Para isso foram encontradas duas soluções: modificiar manualmente os scripts para inicializar o sistema através de bootloader proprietário, ou utilizar imagens de um projeto extra-oficial, que possuem u-boots selecionados para cada arquivo [dtb](../../material-de-apoio/glossario.md#dtb). Aqui utilizaremos a segunda solução._

1. Baixe os software e arquivos necessários no computador/notebook.

- Software de criação de mídia bootável (baixe apenas um de sua escolha)
  - Recomendado: [Balena Etcher (Tutorial de instalação e uso)](https://etcher.balena.io/)
  - Alternativa: [Rufus (Tutorial de instalação e uso)](https://rufus.ie/pt_BR/)
  - Alternativa: [dd (Tutorial de instalação e uso)](https://medium.com/@emusyoka759/creating-a-bootable-usb-in-ubuntu-with-dd-9fb3debc0814)
- Imagem do Armbian (variante do projeto ophub)
  - [Armbian 25.02.0 server](https://unioestebr-my.sharepoint.com/:u:/g/personal/renan_silva15_unioeste_br/EdRFhkzL309CmdtL13XVPZABvpNkqTUbQvxo-w272nMrmQ?e=VOyTvT)
  
2. No computador/notebook, insira o cartão SD e Utilize um dos programas anteriores para gravar a imagem no cartão SD.
3. Entre no diretório raiz do cartão SD após a gravação da imagem, onde diversas pastas e arquivos com extensão .bin podem ser encontrados.
4. Abra o arquivo uEnv.txt com um editor de texto qualquer e substitua o que estiver escrito após a última barra na linha que começa por "fdt" por "meson-sm1-x96-air.dtb". Salve o arquivo e feche.
5. Faça uma cópia do arquivo u-boot-x96maxplus.bin, também presente no diretório raiz do cartão SD, e renomeie essa cópia para u-boot.ext.
6. Remova o cartão SD do computador/notebook.

- Ejete o cartão SD pelo sistema operacional antes de removê-lo, para evitar possível corrupção.

7. Insira o cartão SD na b11 desligada e conectada à um monitor/televisão por cabo HDMI.
8. Pressione o botão reset com um clip de papel desdobrado ou um palito de dente (o botão pode ser encontrado dentro de um "furo" na parte debaixo da TV Box) e conecte a fonte de alimentação enquanto o botão ainda estiver pressionado. Mantenha o botão de reset pressionado e solte assim que algum sinal de vídeo for observado no monitor/televisão.

⚠️Lembre-se⚠️: o sistema está funcionando por meio do cartão SD, ou seja, caso removido, o firmware original da tv box ascenderá novamente, mas nunca retire o cartão SD com o aparelho ligado. Um tópico mais a frente ensinará a gravar o sistema no armazenamento interno, apagando todo o firmware original da TV Box.

### Configuração inicial do Armbian

Após iniacializar o sistema pela primeira vez, é pedido ao usuário que forneça algumas informações de configuração, como nome de usuário, senha, configuração de zonas de tempo e afins. O processo é bem intuitivo. mas caso haja dúvida, utilize o nosso [guia para configuração inicial do Armbian](#).

### Instalação do sistema no armazenmento interno

⚠️Cuidado⚠️: Esta ação vai apagar todos os dados presentes no armazenamento da sua TV Box, convém fazer um backup.

⚠️Lembre-se⚠️: para cumprir esta etapa, é muito importante que uma cópia do u-boot correto tenha sido feita, conforme a etapa 5 do [**Inicializando o Armbian na TV Box pelo cartão SD**](##inicializando-o-armbian-na-tv-box-pelo-cartão-sd).

Após a configuração, execute o comando

```bash
sudo armbian-install -m no
```

E confirme o que for pedido

## ❌ Erros comuns

1. Caso não seja identificado sinal de vídeo após cumprida a etapa 8 da "Preparação para instalação", verifique se o cabo HDMI funciona e está conectado corretamente. Em caso afirmativo, tudo indica que o sistema foi identificado, mas não é compatível.
2. Caso a TV Box inicialize pelo sistema original, é provável que o botão de reset não tenha isdo pressionado por tempo suficiente ou que no cartão SD não tenha sido encontrado um sistema para inicializar. Convém tentar conectar o cartão SD às entradas USB por meio de um adaptador.
