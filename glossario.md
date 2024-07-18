
## Glossário

#### Armazenamento interno:
<!-- Armazenamento interno -->
> Memória dentro de um dispositivo usada para armazenar dados permanentemente, como sistemas operacionais, aplicativos e arquivos de usuário. Exemplos incluem eMMC, NAND, e NVMe.

#### BIOS (Basic Input Output System):
<!-- BIOS -->
> Firmware essencial que inicializa o hardware durante o processo de boot e fornece serviços de runtime para sistemas operacionais e programas.

#### Boot:
<!-- Boot -->
> Processo de inicialização de um computador, começando pela energização do hardware até o carregamento do sistema operacional.

#### Bootloader:
<!-- Bootloader -->
> Pequeno programa que carrega o sistema operacional na memória após a inicialização do [BIOS](#bios-basic-input-output-system)/firmware.

#### DRAM (Dynamic RAM):
<!-- DRAM -->
> Tipo de memória volátil que armazena cada bit de dados em um capacitor, necessitando de atualização periódica para manter os dados.

#### Driver:
<!-- Driver -->
> Software que permite que o sistema operacional e outros programas interajam com dispositivos de hardware específicos.

### DTB (Device Tree Blob):
<!-- DTB -->
> O DTB é um banco de dados em formato de arquivo que representa os componentes de hardware em uma determinada placa. Ele é derivado das especificações IBM OpenFirmware e foi escolhido como o mecanismo padrão para passar informações de hardware de baixo nível do bootloader para o kernel.

#### eMCP (embedded Multi-Chip Package):
<!-- eMCP -->
> Tecnologia que combina eMMC (armazenamento) e DRAM (memória) em um único pacote, economizando espaço e simplificando o design do PCB. Junto do eMMC e do NAND é um dos tipos de armazenamento interno que podem estar presentes na placa de uma TV box.

#### eMMC (embedded MultiMediaCard):
<!-- eMMC -->
> Tipo de armazenamento flash integrado que combina memória NAND e um controlador de memória em um único pacote. Junto do eMCP e do NAND é um dos tipos de armazenamento interno que podem estar presentes na placa de uma TV box.

#### EPROM (Erasable PROM):
<!-- EPROM -->
> Tipo de memória ROM programável que pode ser apagada por exposição à luz UV e reprogramada.

#### FAT32 (File Allocation Table):
<!-- FAT32 -->
> Sistema de arquivos usado para organizar e gerenciar arquivos em unidades de armazenamento, popular em dispositivos de mídia externos, como cartões SD e pen drives.

#### Firmware:
<!-- Firmware -->
> Software embutido em hardware que fornece controle de baixo nível para o dispositivo, funcionando como uma ponte entre o hardware e software de alto nível.

#### initrd (initial RAM Disk):
<!-- initrd -->
> Sistema de arquivos temporário usado pelo kernel durante a inicialização de um sistema antes que o rootfs esteja disponível. Ajuda a carregar módulos do kernel e a preparar o ambiente para o rootfs, que é o sistema de arquivos principal.

#### initramfs (initial RAM Filesystem):
<!-- initramfs -->
> Sistema de arquivos temporários, que advém de um arquivo .cpio (copy in, copy out), que é montado diretamente na RAM. É uma melhoria em relação ao initrd, pois pode ser compactado de forma mais eficiente e permite que o kernel faça a transição para o rootfs de forma mais suave.

#### Kernel:
<!-- Kernel -->
> Parte central de um sistema operacional que gerencia operações do sistema (como escalonamento de processos) e comunicação entre hardware e software.

#### NAND:
<!-- NAND -->
> Tipo de memória flash não volátil usada em dispositivos de armazenamento como SSDs e cartões de memória. Junto do eMMC e do eMCP é um dos tipos de armazenamento interno que podem estar presentes na placa de uma TV box.

#### NAND Flash:
<!-- NAND Flash -->
> Tecnologia de armazenamento não volátil que armazena dados em células de memória, comum em SSDs, eMMC, e outros dispositivos.

#### NVMe (Non-Volatile Memory Express):
<!-- NVMe -->
> Interface de armazenamento que conecta SSDs via PCIe para alta velocidade de transferência de dados e baixa latência.

#### NTFS (New Technology File System):
<!-- NTFS -->
> Sistema de arquivos desenvolvido pela Microsoft, usado principalmente em sistemas Windows para organizar e gerenciar arquivos em unidades de armazenamento.

#### PROM (Programmable ROM):
<!-- PROM -->
> Tipo de memória ROM que pode ser programada uma vez após a fabricação.

#### RAM (Random-Access Memory):
<!-- RAM -->
> Memória volátil usada pelo sistema para armazenar dados temporários que podem ser acessados rapidamente pelo processador.

#### ROM (Read-Only Memory):
<!-- ROM -->
> Memória não volátil que armazena dados que não podem ser modificados durante o uso normal do dispositivo.

#### rootfs (root file system):
<!-- rootfs -->
> Sistema de arquivos principal que contém todos os arquivos necessários para o funcionamento de um sistema operacional.

#### SATA (Serial ATA):
<!-- SATA -->
> Interface usada para conectar dispositivos de armazenamento como HDDs e SSDs a computadores.

#### SoC (System on a Chip):
<!-- SoC -->
> Integração de todos os componentes principais de um computador ou outro sistema eletrônico em um único chip.

#### SRAM (Static RAM):
<!-- SRAM -->
> Tipo de memória volátil que usa flip-flops para armazenar dados, é mais rápida e mais cara que DRAM.

#### U-Boot (Universal Boot):
<!-- U-Boot -->
> Bootloader utilizado em sistemas embarcados para carregar o kernel do sistema operacional e inicializar o hardware.

#### U-Boot SPL (Secondary Program Loader):
<!-- U-Boot SPL -->
> Versão reduzida do U-Boot usada para inicializar o hardware básico e carregar o U-Boot completo.

#### UEFI (Unified Extensible Firmware Interface):
<!-- UEFI -->
> Firmware que substitui a BIOS tradicional em muitos computadores modernos, oferecendo uma interface mais rica, suporte para inicialização segura e tempos de inicialização mais rápidos.

#### TV Box:
<!-- TV Box -->
> Dispositivo de placa única (SBC) ou computador de pequeno porte com sistema operacional Android e arquitetura ARM, projetado para streaming de vídeos e outras aplicações de mídia.


