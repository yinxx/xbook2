# tools
RM			= rm

# System environment variable.
ifeq ($(OS),Windows_NT)
	CC       = 	D:/Softwares/Mingw/bin/gcc.exe 		# need mingw gcc for windows
	# need mingw include and libs
	INCS     = 	-I"D:/Softwares/Dev-Cpp/MinGW64/include" \
				-I"D:/Softwares/Dev-Cpp/MinGW64/x86_64-w64-mingw32/include" \
				-I"D:/Softwares/Dev-Cpp/MinGW64/lib/gcc/x86_64-w64-mingw32/4.8.1/include" \
				-DWIN32

	LIBS 	= 	-L"D:/Softwares/Dev-Cpp/MinGW64/lib" \
				-L"D:/Softwares/Dev-Cpp/MinGW64/x86_64-w64-mingw32/lib" -static-libgcc
	
	# out file
	BIN = ./fatfs.exe

else

	ifeq ($(shell uname),Linux)
		CC       	= gcc
		INCS     = -I /usr/include
		LIBS     = -static-libgcc
		# out file
		BIN = ./fatfs

	endif
endif

# flags	
CFLAGS   = $(INCS) -g3

# objects		
OBJS = 	main.o \
		driver.o \
        diskio.o \
        ff.o \
        ffsystem.o \
        ffunicode.o \


.PHONY: all clean

# all need to do
all: $(BIN) 

$(BIN): $(OBJS)
	$(CC) $(OBJS) -o $(BIN) $(LIBS)

%.o : %.c
	@echo [CC] $@ $<
	@$(CC) -c $(CFLAGS) -o $@ $<

# clean .o .a files
clean: 
	-$(RM) $(BIN)
	-$(RM) $(OBJS)
	