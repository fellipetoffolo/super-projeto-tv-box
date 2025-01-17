# 🔽 Tutorial de Instalação 
### Neste tutorial, é ensinado a instalação da ferramenta rkdeveloptool, ferramenta que permite a instalação de imagens ISO da Rockchip em seus diversos SoC's diretamente.
#### 1) Instalação dos arquivos com código-fonte para compilação do programa e suas dependências: 
  1.1) Clonar o seguinte repositório do github para sua pasta local (Certifique-se de estar no diretório no qual deseja armazenar o clone):
  - git clone https://github.com/rockchip-linux/rkdeveloptool.git
    
  - <img src="https://github.com/renanBatalha/imagens_tutorial_rk_develop_tool/blob/main/imagens_tutorial/clone_github.png" alt="captura de tela da clonagem de repositório" width="1000">
  1.2) Para corrigir erros de compilação e problemas de dependência utilize o seguinte comando, libusb é uma biblioteca usada em C para gerenciar dispositivos usb:
  - sudo apt install pkg-config libusb-1.0-0-dev
  
