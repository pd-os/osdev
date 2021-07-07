# Bare bones

Reference: https://wiki.osdev.org/Bare_Bones

Some tips on installing grub on macos:

* Follow the [wiki](https://wiki.osdev.org/GRUB_2#Installing_GRUB_2_on_OS_X)
    * You may need install the following packages by brew before compiling grub `brew install autoconf automake libtool xorriso freetype`
    * MUST NOT install `mtools` by brew since it may cause a segment fault when building iso (2021/07/07 mtools version 4.0.29). You can install latest mtools from `https://www.gnu.org/software/mtools/`, it works for me.
    * MUST NOT `--with-platform=efi` and target should be `i686-elf` (and change the name from i386-elf to i686-elf)
    * Install unifont from `http://unifoundry.com/unifont/`. (Download the latest version in truetype section)
    * Install i686 gcc cross compiling tools by `brew install i686-elf-gcc`
    * And if you ever installed binutils by brew, MUST uninstall or unlink it before compiling grub
