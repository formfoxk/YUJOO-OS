all : bootloader kernel32 disk.img

bootloader:
	@echo
	@echo ============ Build Boot Loader ============
	@echo
	
	make -C 00.bootloader
	
	@echo
	@echo ============ Build Complete ============
	@echo

kernel32:
	@echo
	@echo ============ Build 32bit Kernel ============
	@echo
	
	make -C 01.kernel32
	
	@echo
	@echo ============ Build Complete ============
	@echo
	
	
disk.img: 00.bootloader/bootloader.bin 01.kernel32/kernel32.bin
	@echo
	@echo ============ Disk Image Build Start ============
	@echo
	
	./imagemaker $^
	
	@echo
	@echo ============ All Build Complete ============
	@echo

# execute real marchine (not exec virtual marchine)
run:
	qemu-system-x86_64 -L . -fda ./disk.img -localtime
	
clean:
	make -C 00.bootLoader clean
	make -C 01.kernel32 clean
	rm -f disk.img
