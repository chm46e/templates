xyz-obj += xyz/main.o

# INFO: Inside directories can be added like this:
#include xyz/directoryname/Makefile
# INFO: and inside those Makefiles, add only the: obj += ...

PHONY += xyz_build
xyz_build: bin/xyz 
bin/xyz: $(xyz-obj)
	@if [ !$(SUPPRESS_ECHO) ]; then\
		echo "[LD] $@";\
	fi
	$(CQ)$(LD) -o $(LC)/$@ $^ $(LDFLAGS) $(CFLAGS)

PHONY += xyz_install
xyz_install: $(LC_INSTALL)/xyz
$(LC_INSTALL)/xyz: xyz_build
	@if [ !$(SUPPRESS_ECHO) ]; then\
		echo "[INSTALL] $@";\
	fi
	$(CQ)sudo cp -f $(LC_BIN)/xyz $(LC_INSTALL)/xyz

PHONY += xyz_clean
xyz_clean:
	@if [ !$(SUPPRESS_ECHO) ]; then\
		echo "[CLEAN] $@";\
	fi
	$(CQ)rm -f $(xyz-obj)
	$(CQ)rm -f $(LC_BIN)/xyz

