## Processo de descaracterização da Tourobox
<img src="https://github.com/user-attachments/assets/a9b56f00-88b7-4be8-b711-fdd43ae6e6fb" height= 400 width=400> 

### 1º Passo: Baixar a imagem armbian.
  
----><a href="https://github.com/sicXnull/armbian-build/releases/download/v24.8.0-trunk.425/Armbian-unofficial_24.11.0-trunk_X96q_bookworm_current_6.6.44_mate_desktop.img.xz">link da imagem bookworn 6.6.44 mate desktop<a>

***
### 2º Passo: Gravar a imagem baixada para o cartão sd.
#### *Obs: Não confundir com "copiar" a imagem para o cartão sd.
#### *Utilizar o software Balena Etcher ou Rufus.
----> <a href="https://etcher.balena.io/">link do Balena Etcher<a>

----> <a href="https://rufus.ie/pt_BR/">link do Rufus<a>


***
### 3º Passo: Inserir o cartão SD, configurar o sistema e executar o script de instalação no armazenamento interno da tvbox.
#### Configure sua tvbox conforme nosso tutorial "primeiros passos após instalação"
#### Após isso, pressione 
``` Ctrl + Alt + F2 ```
#### para abrir um terminal. Dê o comando 
``` sudo armbian-install ```
#### e forneça sua senha para entrar no menu de execução do script de instalação. Selecione a opção "Boot from emmc"



