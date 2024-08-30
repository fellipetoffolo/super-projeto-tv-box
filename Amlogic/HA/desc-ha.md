## Processo de descaracterização da HA
<img src="https://github.com/renanBatalha/tv_box_imagens/blob/main/amlogic_ha_frontal.jpeg" height= 400 width=400> <img src = "https://github.com/renanBatalha/tv_box_imagens/blob/main/amlogic_ha_traseira.jpeg" height= 400 width=400>

### 1º Passo: Baixar a imagem armbian.
      
  
----><a href="https://armbian.hosthatch.com/archive/aml-s9xx-box/archive/Armbian_23.02.2_Aml-s9xx-box_bullseye_current_6.1.11_xfce_desktop.img.xz">link da imagem bullseye 6.1.11_xfce_desktop<a>

***
### 2º Passo: Gravar a imagem baixada para o cartão sd.
#### *Obs: Não confundir com "copiar a imagem para o cartão sd.
#### *Utilizar o software Balena Etcher ou Rufus.
----> <a href="https://etcher.balena.io/">link do Balena Etcher<a>

----> <a href="https://rufus.ie/pt_BR/">link do Rufus<a>


***
### 3º Passo: Escolher o Bootloader do Sistema.
####Renomear u-boot-s905x-912 por u-boot.ext para que ele seja carregado ao inicializar o sistema:

<img src="https://github.com/renanBatalha/tv_box_imagens/blob/main/armbi_boot_imagem_selecionada.png height=500 width=500">
<img src="https://github.com/renanBatalha/tv_box_imagens/blob/main/armbi_boot_selecao_bootloader.png height=500 width=500">
