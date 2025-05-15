
### Glossário

#### Armazenamento interno:
<!-- Armazenamento interno -->
> Memória dentro de um dispositivo usada para armazenar dados permanentemente, como sistemas operacionais, aplicativos e arquivos de usuário. Exemplos incluem [eMMC](#emmc-embedded-multimediacard), NAND, e NVMe.

#### armeabi (ARM application binary interface):
<!-- armeabi -->
> Uma ABI para dispositivo ARM é usada para definir como o código binário de um programa (compilado) deve interagir com o sistema operacional e o hardware subjacente. Isso inclui detalhes sobre a chamada de funções, passagem de parâmetros, estrutura de memória, e outras interações entre software e hardware.

#### ARMvx (ARMv4, ARMv5...):
<!-- ARMvx -->
> Representa a versão da arquitetura ARM utilizada por uma máquina desta arquitetura. As versões ARMv4 até ARMv7 utilizam conjuntos de instruções de linguagem de máquina de 16 e 32 bits. A partir da versão ARMv8, introduzida em 2011, passou-se a utilizar conjuntos de instruções de 16, 32 e 64 bits.

#### BIOS (Basic Input Output System):
<!-- BIOS -->
> Firmware essencial que inicializa o hardware durante o processo de [boot](#boot) e fornece serviços de runtime para sistemas operacionais e programas.

#### Boot:
<!-- Boot -->
> Processo de inicialização de um computador, começando pela energização do hardware até o carregamento do sistema operacional.

#### Bootloader:
<!-- Bootloader -->
> Pequeno programa que carrega o [kernel](#kernel) do sistema operacional na memória [RAM](#ram-random-access-memory) após a inicialização do [BIOS](#bios-basic-input-output-system)/firmware.

#### DRAM (Dynamic RAM):
<!-- DRAM -->
> Tipo de memória volátil que armazena cada bit de dados em um capacitor, necessitando de atualização periódica para manter os dados.

#### Driver:
<!-- Driver -->
> Software que permite que o sistema operacional e outros programas interajam com dispositivos de hardware específicos.

#### DTB (Device Tree Blob):
<!-- DTB -->
> DTB é um arquivo "device tree blob", que representa os componentes de hardware em uma determinada placa. Ele é derivado das especificações IBM OpenFirmware e foi escolhido como o mecanismo padrão para passar informações de hardware de baixo nível do [bootloader](#bootloader) para o kernel.

#### DTS (Device Tree Source):
<!-- DTS -->
> DTS é um arquivo [DTB](#dtb-device-tree-blob) que ainda não foi compilado. Sua especificações são escritas em formato textual.

#### eMCP (embedded Multi-Chip Package):
<!-- eMCP -->
> Tecnologia que combina [eMMC](#emmc-embedded-multimediacard) (armazenamento interno) e DRAM (memória RAM) em um único pacote, economizando espaço e simplificando o design do PCB. Junto do eMMC e do NAND é um dos tipos de armazenamento interno que podem estar presentes na placa de uma TV box.

#### eMMC (embedded MultiMediaCard):
<!-- eMMC -->
> Tipo de armazenamento flash integrado que combina memória NAND e um controlador de memória em um único pacote. Junto do eMCP e do NAND é um dos tipos de armazenamento interno que podem estar presentes na placa de uma TV box.

#### EPROM (Erasable PROM):
<!-- EPROM -->
> Tipo de memória [ROM](#rom-read-only-memory) programável que pode ser apagada por exposição à luz UV e reprogramada.

#### FAT32 (File Allocation Table):
<!-- FAT32 -->
> Sistema de arquivos usado para organizar e gerenciar arquivos em unidades de armazenamento, popular em dispositivos de mídia externos, como cartões SD e pen drives.

#### Firmware:
<!-- Firmware -->
> Software embutido em hardware que fornece controle de baixo nível para o dispositivo, funcionando como uma ponte entre o hardware e software de alto nível.

#### initrd (initial RAM Disk):
<!-- initrd -->
> Sistema de arquivos temporário usado pelo [kernel](#kernel) durante a inicialização de um sistema antes que o rootfs esteja disponível. Ajuda a carregar módulos do kernel e a preparar o ambiente para o rootfs, que é o sistema de arquivos principal.

#### initramfs (initial RAM Filesystem):
<!-- initramfs -->
> Sistema de arquivos temporários, que advém de um arquivo .cpio (copy in, copy out), que é montado diretamente na [RAM](#ram-random-access-memory). É uma melhoria em relação ao initrd, pois pode ser compactado de forma mais eficiente e permite que o kernel faça a transição para o rootfs de forma mais suave.

#### Kernel:
<!-- Kernel -->
> Parte central de um sistema operacional que gerencia operações do sistema (como escalonamento de processos e gerenciamento de memória) e comunicação entre hardware e software.

#### NAND:
<!-- NAND -->
> Tipo de memória flash não volátil usada em dispositivos de armazenamento como SSDs e cartões de memória. Junto do [eMMC](#emmc-embedded-multimediacard) e do [eMCP](#emcp-embedded-multi-chip-package) é um dos tipos de armazenamento interno que podem estar presentes na placa de uma TV box.

#### NAND Flash:
<!-- NAND Flash -->
> Tecnologia de armazenamento não volátil que armazena dados em células de memória, comum em SSDs, [eMMC](#emmc-embedded-multimediacard), e outros dispositivos.

#### NVMe (Non-Volatile Memory Express):
<!-- NVMe -->
> Interface de armazenamento que conecta SSDs via PCIe para alta velocidade de transferência de dados e baixa latência.

#### NTFS (New Technology File System):
<!-- NTFS -->
> Sistema de arquivos desenvolvido pela Microsoft, usado principalmente em sistemas Windows para organizar e gerenciar arquivos em unidades de armazenamento.

#### MBR (Master Boot Record):
<!-- MBR -->
> Setor principal de inicialização de um disco rígido ou dipositivo de armazenamento. Sua estrutura é composta por bootloader, assinatura de disco e tabela de partições contendo 4 partições primárias que armazenam informações necessárias para que o computador possa encontrar e carregar o sistema operacional.

#### OpenWrt
<!--OpenWrt-->
> Uma distribuição linux embarcada usada em roteadores wireless, com o objetivo de criar diversas funcionalidades e ser um sistema operacional de fácil modificação.

#### PROM (Programmable ROM):
<!-- PROM -->
> Tipo de memória [ROM](#rom-read-only-memory) que pode ser programada apenas uma vez após a fabricação.

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
> [Bootloader](#bootloader) utilizado em sistemas embarcados para carregar o kernel do sistema operacional e inicializar o hardware.

#### U-Boot SPL (Secondary Program Loader):
<!-- U-Boot SPL -->
> Versão reduzida do U-Boot usada para inicializar o hardware básico e carregar o U-Boot completo.

#### UEFI (Unified Extensible Firmware Interface):
<!-- UEFI -->
> Firmware que substitui a [BIOS](#bios-basic-input-output-system) tradicional em muitos computadores modernos, oferecendo uma interface mais rica, suporte para inicialização segura e tempos de inicialização mais rápidos.

#### TV Box:
<!-- TV Box -->
> Dispositivo de placa única (SBC) ou computador de pequeno porte com sistema operacional Android e arquitetura ARM, projetado para streaming de vídeos e outras aplicações de mídia.
