TOP = ..
include $(TOP)/configure/CONFIG

# Submodules
#SUBMODULES += motorVendor
SUBMODULES += motorZaberMotion
# SUBMODULES += motorOms
# SUBMODULES += motorNewport
# SUBMODULES += motorAMCI
# SUBMODULES += motorAcs
# SUBMODULES += motorAcsMotion
# SUBMODULES += motorAcsTech80
# SUBMODULES += motorAerotech
# SUBMODULES += motorAttocube
# SUBMODULES += motorDeltaTau
# SUBMODULES += motorFaulhaber
# ifdef IPAC
# SUBMODULES += motorHytec
# endif
# SUBMODULES += motorIms
# SUBMODULES += motorKohzu
# SUBMODULES += motorMclennan
# SUBMODULES += motorMicos
# SUBMODULES += motorMicroMo
# SUBMODULES += motorMicronix
# SUBMODULES += motorMotorSim
# ifdef MX
# SUBMODULES += motorMXmotor
# endif
# SUBMODULES += motorNewFocus
# SUBMODULES += motorNPoint
# SUBMODULES += motorOmsAsyn
# SUBMODULES += motorOriel
# SUBMODULES += motorParker
# SUBMODULES += motorPhytron
# SUBMODULES += motorPiJena
# SUBMODULES += motorPI
# SUBMODULES += motorPIGCS2
# ifdef LUA
# SUBMODULES += motorScriptMotor
# endif
# SUBMODULES += motorSmarAct
# SUBMODULES += motorSmartMotor
# SUBMODULES += motorThorLabs

# Allow sites to add extra submodules
-include Makefile.local

# Add only checked-out submodules to DIRS
DIRS += $(subst /Makefile,,$(wildcard $(addsuffix /Makefile, $(SUBMODULES))))

include $(TOP)/configure/RULES_DIRS

INSTALL_LOCATION_ABS := $(abspath $(INSTALL_LOCATION))
RELEASE_LOCAL := RELEASE.$(EPICS_HOST_ARCH).local

# Ensure that RELEASE.<host>.local exists before doing anything else
all host $(DIRS) $(ARCHS) $(ACTIONS) $(dirActionTargets) $(dirArchTargets) \
    $(dirActionArchTargets) $(actionArchTargets): | $(RELEASE_LOCAL)

.PHONY: $(RELEASE_LOCAL)
$(RELEASE_LOCAL):
	$(ECHO) Creating $@, MOTOR = $(INSTALL_LOCATION_ABS)
	@echo MOTOR = $(INSTALL_LOCATION_ABS)> $@
ifdef ASYN
	$(ECHO) Creating $@, ASYN = $(ASYN)
	@echo ASYN = $(ASYN)>> $@
endif
ifdef SNCSEQ
	$(ECHO) Creating $@, SNCSEQ = $(SNCSEQ)
	@echo SNCSEQ = $(SNCSEQ)>> $@
endif
ifdef BUSY
	$(ECHO) Creating $@, BUSY = $(BUSY)
	@echo BUSY = $(BUSY)>> $@
endif
ifdef IPAC
	$(ECHO) Creating $@, IPAC = $(IPAC)
	@echo IPAC = $(IPAC)>> $@
endif
ifdef MX
	$(ECHO) Creating $@, MX = $(MX)
	@echo MX = $(MX)>> $@
endif
ifdef LUA
	$(ECHO) Creating $@, LUA = $(LUA)
	@echo LUA = $(LUA)>> $@
endif
ifdef AUTOSAVE
	$(ECHO) Creating $@, AUTOSAVE = $(AUTOSAVE)
	@echo AUTOSAVE = $(AUTOSAVE)>> $@
endif
ifdef MODBUS
	$(ECHO) Creating $@, MODBUS = $(MODBUS)
	@echo MODBUS = $(MODBUS)>> $@
endif
	$(ECHO) Creating $@, EPICS_BASE = $(EPICS_BASE)
	@echo EPICS_BASE = $(EPICS_BASE)>> $@
	
	$(ECHO) Creating $@, SUPPORT = $(SUPPORT)
	@echo SUPPORT = $(SUPPORT)>> $@
	
realclean:
	$(RM) $(RELEASE_LOCAL)
