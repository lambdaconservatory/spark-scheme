#SUBDIRS = libs/mzs/src libs/sqlite libs/fltk src
all:
	make -C ./libs/fltk
	make -C ./libs/mzs/src
	make -C ./libs/sqlite
	make -C ./src
install:
	make -C ./src install
uninstall:
	make -C ./src uninstall
clean:
	make -C ./libs/fltk clean
	make -C ./libs/mzs/src clean
	make -C ./libs/sqlite clean
	make -C ./src clean
am--refresh: 

