# <img src="https://github.com/fellipetoffolo/super-projeto-tv-box/blob/Cortella/.assets/ha-box.jpeg" alt="Imagem do case" width="30"/> Descaracterização do modelo HA

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
| CPU S905X                |       X         |       X       |
| Armazenamento interno    |       10.85     |       X       |
| Memória RAM              |       X         |      2 GB     |


### Imagem do Modelo

<img src="https://github.com/fellipetoffolo/super-projeto-tv-box/blob/Cortella/.assets/ha-box.jpeg" alt="Imagem do case" width="300"/>
<img src="https://github.com/fellipetoffolo/super-projeto-tv-box/blob/Cortella/.assets/ha-placa.jpeg" alt="Imagem do hardware" width="300"/>

### Sistema Operacional Original


Android: 7.1.2
Kernel: 3.14.29


### Suporte de Rede 

|Módulo          |Driver | WiFi        | Ethernet      | Bluetooth     | 
|----------------|-------|-------------|---------------|---------------|
|RealTek 8723ds  |8723ds |🟢 Funciona  |🟠 Não Testado|🟠 Não Testado |


## 📈 Desempenho

Confira nossa [metodologia de avaliação](material-de-apoio/glossario.md). <!-- Necessário criar arquivo de metodologia e linkar aqui -->

| Atividades                   | Avaliação     |
| ---------------------------- | --------------|
| Navegar em páginas           | 🟠 MÉDIO      |
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
     - [Armbian_23.8.1 Kernel 6.1.50 com desktop e interface gráfica XFCE](https://unioestebr-my.sharepoint.com/:u:/g/personal/renan_silva15_unioeste_br/EYO_IaHxLcxDrQMYyfNis-wBRl-OuYIk0nvXUq9LoGC1wA?e=gPsRky) 
2. No computador/notebook, insira o cartão SD e Utilize um dos programas anteriores para gravar a imagem no cartão SD.
3. Entre no diretório raiz do cartão SD após a gravação da imagem, onde diversas pastas e arquivos com extensão .bin podem ser encontrados.
4. Abra a pasta "extlinux" e em seguida, com um editor de texto, o arquivo "extlinux.conf" e cole o seguinte texto no único caminho de arquivo FDT que não apresenta "#", o substituindo por FDT dtb/amlogic/meson-gxl-s905x-212.dtb. Caso ele já esteja lá, não faça nada.
5. Copie e cole o arquivo "u-boot-s905x-912.bin", presente no diretório raiz do cartão SD, em seu próprio diretório de "u-boots".
6. Renomeie o seguinte arquivo .bin na pasta raiz, "u-boot-s905x-912.bin(1)" por "u-boot.ext" alterando seu formato.
7. Remova o cartão SD do computador/notebook.
  - Ejete o cartão SD pelo sistema operacional antes de removê-lo, para evitar possível corrupção. 
8. Insira o cartão SD na Astro11 desligada e conectada à um monitor/televisão por cabo HDMI.
9. Diferente de outros modelos TV Box mostrados aqui, não há necessidade de pressionar o botão reset para inicializar o sistema Armbian.
10. Essa versão armbian vem configurada com um usuário por padrão, portanto, para entrar no sistema basta logar com o login "root" e a senha "1234".

⚠️Lembre-se⚠️: o sistema está funcionando por meio do cartão SD, ou seja, caso removido, o firmware original da tv box ascenderá novamente, mas nunca retire o cartão SD com o aparelho ligado. Um tópico mais a frente ensinará a gravar o sistema no armazenamento interno, apagando todo o firmware original da TV Box.

### Configuração Inicial do Armbian

Após iniacializar o sistema pela primeira vez, é pedido ao usuário que forneça algumas informações de configuração, como nome de usuário, senha, configuração de zonas de tempo e afins. O processo é bem intuitivo. mas caso haja dúvida, utilize o nosso [guia para configuração inicial do Armbian](#).

### Instalação do Sistema no Armazenmento Interno 

⚠️Cuidado⚠️: Esta ação vai apagar todos os dados presentes no armazenamento da sua TV Box, convém fazer um backup.

⚠️Lembre-se⚠️: para cumprir esta etapa, é muito importante que uma cópia do u-boot correto tenha sido feita, conforme a etapa 5 da [**Preparação para instalação**](#preparação-para-instalação).

Após a configuração, execute o comando 


```bash
sudo armbian-install -m no
```

E confirme o que for pedido



## ❌ Erros Comuns

1. Caso não seja identificado sinal de vídeo após cumprida a etapa 8 da "Preparação para instalação", verifique se o cabo HDMI funciona e está conectado corretamente. Em caso afirmativo, tudo indica que o sistema foi identificado, mas não é compatível.



