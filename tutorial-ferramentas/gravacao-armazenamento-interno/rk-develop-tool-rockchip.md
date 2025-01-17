# 🔽 Tutorial de Instalação 
### Neste tutorial, é ensinado a instalação da ferramenta rkdeveloptool, ferramenta que permite a instalação de imagens ISO da Rockchip em seus diversos SoC's diretamente.
#### 1) Instalação dos arquivos com código-fonte para compilação do programa e suas dependências: 
  1.1) Clonar o seguinte repositório do github para sua pasta local (Certifique-se de estar no diretório no qual deseja armazenar o clone):
  - git clone https://github.com/rockchip-linux/rkdeveloptool.git
    
  <img src="https://github.com/renanBatalha/imagens_tutorial_rk_develop_tool/blob/main/imagens_tutorial/clone_github.png" alt="captura de tela da clonagem de repositório" width="800">
  1.2) Para corrigir erros de compilação e problemas de dependência utilize o seguinte comando, libusb é uma biblioteca usada em C para gerenciar dispositivos usb:  
  
  - sudo apt install pkg-config libusb-1.0-0-dev  
  
  - sudo apt install libudev-dev  
  
  - sudo apt install dh-autoreconf

  1.3) Compilação do rkdeveloptool (Certifique-se de estar na pasta clonada "rkdeveloptool"):
  - autoreconf -i
  - É possível que para esse comando haja um erro de compilação envolvendo a MACRO "AM_CONFIG_HEADER" na linha 8 do arquivo configure.ac como pode ser visto na figura abaixo:
    
    <img src="https://github.com/renanBatalha/imagens_tutorial_rk_develop_tool/blob/main/imagens_tutorial/erro_de_macro_AM_CONFIG_HEADER.png" alt="Erro de macro AM_CONFIG_HEADERS" width="800">
  - Para resolvê-lo, basta substituí-ka pela macro sugerida, AC_CONFIG_HEADERS.
    
   <img src="https://github.com/renanBatalha/imagens_tutorial_rk_develop_tool/blob/main/imagens_tutorial/solucao_erro_de_macro.png" alt="Atualizacao da macro para AC_CONFIG_HEADERS" width="800">
  - Também será necessário modificar o valor "5" presente no buffer para 600 na linha 1491 do arquivo main.cpp.
    
    <img src="https://github.com/renanBatalha/imagens_tutorial_rk_develop_tool/blob/main/imagens_tutorial/solucao_erro_buffer.png" alt="Atualizacao de buffer" width="800">
  
     
  
  
