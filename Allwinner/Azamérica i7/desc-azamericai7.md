# <img src="https://github.com/fellipetoffolo/super-projeto-tv-box/blob/Cortella/.assets/azamericai7-box.png" alt="Imagem do case" width="30"/> Descaracterização do modelo Azamérica I7

## 🔎 Sumário
- [Valores de Hardware](#valores-de-hardware) 
- [Imagem do Modelo](#imagem-do-modelo)
- [Sistema Operacional Original](#sistema-operacional-original)
- [Suporte de Rede](#suporte-de-rede)
- [Desempenho](#-desempenho)
- [Processo Detalhado](#-processo-detalhado)
- [Preparação para Instalação](#preparação-para-instalação)
- [Configuração Inicial do Armbian](#configuração-inicial-do-armbian)
- [Instalação do Sistema no Armazenamento Interno](#instalação-do-sistema-no-armazenmento-interno)
- [Erros Comuns](#-erros-comuns)


### Valores de Hardware (Obtidas por meio da plataforma AIDA64)


| Medida                   | Valor detectado | Valor nominal |
| ------------------------ | --------------  | ------------- |
| CPU H313                 |       1344 MHz  |     x         |
| Armazenamento interno    |       32        |      32 GB    |
| Memória RAM              |       3GB       |      3 GB     |


### Imagem do Modelo

<img src="https://github.com/fellipetoffolo/super-projeto-tv-box/blob/Cortella/.assets/azamericai7-box.png" alt="Imagem do case" width="300"/>
<img src="https://github.com/fellipetoffolo/super-projeto-tv-box/blob/Cortella/.assets/azamericai7-placa.png" alt="Imagem do hardware" width="300"/>

### Sistema Operacional Original


Android: 10
Kernel:  4.9.170


### Suporte de Rede 

|Módulo          |Driver          | WiFi            | Ethernet      | Bluetooth     | 
|----------------|----------------|-----------------|---------------|---------------|
|sp6330          | Desconhecido   |🟠 Não Testado  |🟠 Não Testado |🟠 Não Testado |


## 📈 Desempenho

Confira nossa [metodologia de avaliação](material-de-apoio/glossario.md). <!-- Necessário criar arquivo de metodologia e linkar aqui -->

| Atividades                   | Avaliação     |
| ---------------------------- | --------------|
| Navegar em páginas           | 🔴 RUIM       |
| Assistir vídeos              | 🔴 RUIM       |
| Jogar                        | 🔴 RUIM       |
| Utilizar como servidor       | 🟢 BOM        |


## 📖 Processo detalhado

### Cuidados necessários

- Sempre ejete o cartão SD pelo sistema operacional antes de removê-lo do computador.

### Preparação para instalação

_Disclaimer1: Caso algum termo não seja compreendido, verifique-o na seção [glossário](material-de-apoio/glossario.md)_

1. Baixe os software e arquivos necessários no computador/notebook.
  - Software de criação de mídia bootável (baixe apenas um de sua escolha)
     - Recomendado: [Balena Etcher (Tutorial de instalação e uso)](https://etcher.balena.io/)
     - Alternativa: [Rufus (Tutorial de instalação e uso)](https://rufus.ie/pt_BR/)
     - Alternativa: [dd (Tutorial de instalação e uso)](https://medium.com/@emusyoka759/creating-a-bootable-usb-in-ubuntu-with-dd-9fb3debc0814)
  - Imagem do Armbian (Baixado Direto dos Repositórios Armbian)
     - [X96q Armbian_25.2.3 Kernel 6.12.20 com desktop e interface gráfica MATE](https://unioestebr-my.sharepoint.com/:u:/g/personal/renan_silva15_unioeste_br/EaAGVXmzL4VEtZWiTdYdYksBQ0bB81bMHmrC7qJ2vAuEZw?e=aYuQKC) 
2. No computador/notebook, insira o cartão SD e Utilize um dos programas anteriores para gravar a imagem no cartão SD.
3. Remova o cartão SD do computador/notebook.
  - Ejete o cartão SD pelo sistema operacional antes de removê-lo, para evitar possível corrupção. 
4. Insira o cartão SD no **LEITOR DE CARTAO SD** da Azamérica I7 desligada e conectada à um monitor/televisão por cabo HDMI.
9. Diferente de outros modelos TV Box mostrados aqui, não há necessidade de pressionar o botão reset ou update para inicializar o sistema Armbian.

⚠️Lembre-se⚠️: o sistema está funcionando por meio do cartão SD, ou seja, caso removido, o firmware original da tv box irá inicializar novamente, mas nunca retire o cartão SD com o aparelho ligado. Um tópico mais a frente ensinará a gravar o sistema no armazenamento interno, apagando todo o firmware original da TV Box.

### Configuração Inicial do Armbian

Após iniacializar o sistema pela primeira vez, é pedido ao usuário que forneça algumas informações de configuração, como nome de usuário, senha, configuração de zonas de tempo e afins. O processo é bem intuitivo. mas caso haja dúvida, utilize o nosso [guia para configuração inicial do Armbian](#).

### Instalação do Sistema no Armazenmento Interno 

⚠️Cuidado⚠️: Esta ação vai apagar todos os dados presentes no armazenamento da sua TV Box, convém fazer um backup.

⚠️Lembre-se⚠️: para cumprir esta etapa, é muito importante que uma cópia do u-boot correto tenha sido feita, conforme a etapa 5 da [**Preparação para instalação**](#preparação-para-instalação).

Após a configuração, execute o comando 


```bash
sudo armbian-install
```

- Selecionar a opção "Install/Update the bootloader on eMMC(/dev/mmcblk2)"
- Confirme o que for pedido



## ❌ Erros Comuns

1. Caso não seja identificado sinal de vídeo após cumprida a etapa 8 da "Preparação para instalação", verifique se o cabo HDMI funciona e está conectado corretamente. Em caso afirmativo, tudo indica que o sistema foi identificado, mas não é compatível.



