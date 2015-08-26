#if 0

###############################################################################
#                                                                             #
# csvparse - read write comma separated value format                          #
# Copyright (c) 2003, 2006 Paul Hsieh <qed@pobox.com>                         #
# All rights reserved.                                                        #
#                                                                             #
# Redistribution and use in source and binary forms, with or without          #
# modification, are permitted provided that the following conditions are met: #
#                                                                             #
#     Redistributions of source code must retain the above copyright notice,  #
#     this list of conditions and the following disclaimer.                   #
#                                                                             #
#     Redistributions in binary form must reproduce the above copyright       #
#     notice, this list of conditions and the following disclaimer in the     #
#     documentation and/or other materials provided with the distribution.    #
#                                                                             #
#     Neither the name of csvparse nor the names of its contributors may be   #
#     used to endorse or promote products derived from this software without  #
#     specific prior written permission.                                      #
#                                                                             #
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" #
# AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE   #
# IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE  #
# ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE    #
# LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR         #
# CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF        #
# SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS    #
# INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN     #
# CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE)     #
# ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE  #
# POSSIBILITY OF SUCH DAMAGE.                                                 #
#                                                                             #
###############################################################################

# This is a WATCOM C/C++ makefile

APPNAME = csvparse
CDIR = .
ODIR = .\obj
ADIR = .\arc
CC  = *wcc386
CPP = *wpp386
DEVNULL = nul

# Operating system.

SYSLFLAGS = SYS nt
SYSCFLAGS = -bt=nt

CFLAGS = -e25 -zq -otexan -mf -5r $(SYSCFLAGS) -bm -wx -we 
DEFINES = 

# Directories where headers can be found.

INCLUDES = -i=$(CDIR)\bstrlib

# Object files

OFILES = $(ODIR)\csvparse.obj $(ODIR)\bstrlib.obj

# Makefile verbose setting

QUIET = @

# Directories where source files can be found.

.c: $(CDIR);$(CDIR)\bstrlib
.cpp: $(CDIR);$(CDIR)\bstrlib

# The default build rule for c/cpp -> obj creation.

.c.obj: .AUTODEPEND
	$(QUIET)echo     Compiling: $[*
	$(QUIET)$(CC) $[* $(INCLUDES) $(CFLAGS) $(DEFINES) -fo=$(ODIR)\

.cpp.obj: .AUTODEPEND
	$(QUIET)echo     Compiling: $[*
	$(QUIET)$(CPP) $[* $(INCLUDES) $(CFLAGS) $(DEFINES) -fo=$(ODIR)\

# The first rule is the default build rule, from which all other rules may be
# activated

$(APPNAME).exe : $(OFILES) makefile .AUTODEPEND
	$(QUIET)%write $(ODIR)\$(APPNAME).lnk NAME $(APPNAME).exe
	$(QUIET)%append $(ODIR)\$(APPNAME).lnk $(SYSLFLAGS) op m=$(ODIR)\$(APPNAME).map d all op st=16384 op maxe=25 op q op symf=$(ODIR)\$(APPNAME).sym op redefsok
	$(QUIET)for %%f in ($(OFILES)) do @%append $(ODIR)\$(APPNAME).lnk FIL %%f
	$(QUIET)echo     Linking: $(APPNAME)
	$(QUIET)*wlink @$(ODIR)\$(APPNAME).lnk
	$(QUIET)echo.
	$(QUIET)echo     Target $(APPNAME).exe done.

# Non-default build rules.

# Initial commands invoked on every make

.BEFORE
	$(QUIET)!if not exist $(ODIR)\nul md $(ODIR)
	$(QUIET)echo xxx > $(ODIR)\xxx
	$(QUIET)if not exist $(ODIR)\xxx mkdir $(ODIR)
	$(QUIET)if exist $(ODIR)\xxx del $(ODIR)\xxx > $(DEVNULL)
	$(QUIET)echo     $(APPNAME)
	$(QUIET)echo     ======
	$(QUIET)set INCLUDE=.;$(%watcom)\h;$(%watcom)\h\nt
	$(QUIET)set DOS4G=QUIET

# User defined commands

clean: .SYMBOLIC
	$(QUIET)echo     Removing build targets
	$(QUIET)for %%f in ($(ODIR)\*.obj $(ODIR)\*.lnk $(ODIR)\*.map $(ODIR)\*.sym $(APPNAME).exe *.err) do @if exist %%f del %%f > nul

archive: .SYMBOLIC
	$(QUIET)echo Cleaning
	$(QUIET)echo ========
	$(QUIET)wmake /h clean
	$(QUIET)echo Various archive commands
	$(QUIET)echo ========================
	$(QUIET)!if not exist $(ADIR)\nul md $(ADIR)
	$(QUIET)echo xxx > $(ADIR)\xxx
	$(QUIET)if not exist $(ADIR)\xxx mkdir $(ADIR)
	$(QUIET)if exist $(ADIR)\xxx del $(ADIR)\xxx > $(DEVNULL)
 	$(QUIET)-pkzip -u -p -r $(ADIR)\$(APPNAME).zip *.c *.h *.txt *.csv makefile > $(DEVNULL)
	$(QUIET)-pkzip -v $(ADIR)\$(APPNAME).zip

#endif
