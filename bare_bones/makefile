.PHONY: run boot kernel bin iso clean

AS=i686-elf-as
CC=i686-elf-gcc
# You may need to change this
GRUB_PREFIX=/usr/local/grub/i686/bin/

run: iso
	qemu-system-i386 -cdrom ./build/myos.iso

iso: bin
	mkdir -p build/iso/boot/grub
	cp ./build/myos.bin build/iso/boot/myos.bin
	cp grub.cfg build/iso/boot/grub/grub.cfg
	$(GRUB_PREFIX)grub-mkrescue -o ./build/myos.iso ./build/iso

bin: ./build/boot.o ./build/kernel.o linker.ld
	$(CC) -T linker.ld -o ./build/myos.bin -ffreestanding -O2 -nostdlib ./build/boot.o ./build/kernel.o -lgcc

./build/boot.o: boot.s
	mkdir -p ./build
	$(AS) boot.s -o ./build/boot.o

./build/kernel.o: kernel.c
	mkdir -p ./build
	$(CC) -c kernel.c -o ./build/kernel.o -std=gnu99 -ffreestanding -O2 -Wall -Wextra

clean:
	rm -f ./*.o ./*.bin ./*.iso
	rm -rf ./build
