# Low level x86 assmbly and C examples

System setup (Tested on Ubuntu 18.04):
~~~
apt-get update
apt-get install bochs bochs-sdl build-essential gcc \
    gcc-multilib gdb gnu-efi grub-pc-bin make nasm \
    qemu xorriso sgabios
~~~
Building hello-world:
~~~
cd ./hello-world
gcc hello-world.S -m32 -c -ggdb3 -o hello-world.o
ld -melf_i386 -nostdlib -o 'hello-world.elf' -T '../linker.ld' 'hello-world.o'
objcopy -O binary 'hello-world.elf' 'hello-world.img'
qemu-system-i386 -drive 'file=hello-world.img,format=raw' -smp 2 -nographic -device sga 
~~~