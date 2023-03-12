# NOTES:
# * Every make command must be executed from the root project directory.
# * The top Makefile manages internal projects.

# TODO: Replace all xyz instances with your project's name!
# TODO: Make sure you look thoroughly through the entire build system!
# This approach is in the end nicer, rather than making a generic variable

VERSION := 0.1.0
NAME := Chicken soup

# Manage command/echo usage
SUPPRESS_ECHO := 0
SUPPRESS_COMMAND := 1

INCS := -I./ -I./include/
LIBS :=

# Generic build flags (all internal projects)
CPPFLAGS := -std=c++17 -g -Wall -Wextra -Wpedantic -Wstrict-aliasing
CPPFLAGS += -Wno-unused-parameter -Wno-pointer-arith $(INCS)
LDFLAGS := $(LIBS)
ARFLAGS :=
MAKEFLAGS := --no-print-directory

CC := g++
LD := g++
AR := ar

# Location manager
LC := $(shell pwd)
LC_INSTALL := /usr/bin
LC_BIN := $(LC)/bin
LC_XYZ := $(LC)/xyz

ifeq ($(SUPPRESS_COMMAND), 1)
	CQ = @
else
	CQ = 
endif

# Generic control
PHONY += all
all: info run

# Include all internal projects
include xyz/Makefile

# Show simple setup information
PHONY += info
info:
	@echo "VERSION: $(VERSION) '$(NAME)'"
	@echo "CPPFLAGS: $(CPPFLAGS)"
	@echo "LDFLAGS: $(LDFLAGS)"
	@echo "CC: $(CC)"
	@echo "LD: $(LD)"
	@echo "LC: $(LC)"
	@echo ""

# Generic compile for CPP file
# Suffix objs with: .o
%.o: %.cpp
	@if [ !$(SUPPRESS_ECHO) ]; then\
		echo "[CC] $@";\
	fi
	$(CQ)$(CC) -o $@ -c $< $(CPPFLAGS)

# Build all internal projects
# Each internal project must manage its own build objects & building
PHONY := build
build: xyz_build

# Clean everything
# Each internal project must manage its own cleaning
PHONY += clean
clean: xyz_clean

# Exec only executes
PHONY += exec
exec:
	@if [ !$(SUPPRESS_ECHO) ]; then\
		echo "[EXEC] $(LC_BIN)/xyz";\
	fi
	$(CQ)$(LC_BIN)/xyz

# Run does everything
PHONY += run
run: build exec

# Install every internal project
PHONY += install
install: xyz_install

.PHONY: $(PHONY)
