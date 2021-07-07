.PHONY: run bin clean

run: bin
	qemu-system-i386 -hda ./build/boot.bin

bin: boot.asm print.inc
	mkdir -p ./build
	nasm boot.asm -f bin -o ./build/boot.bin

clean:
	rm -rf ./build
