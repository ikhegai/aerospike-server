# Citrusleaf Foundation
# Makefile

DEPTH = ../..
include $(DEPTH)/make_in/Makefile.in

ifeq ($(USE_EE),1)
  include $(EEREPO)/cf/make_in/Makefile.vars
endif

HEADERS += arenax.h bits.h cf_mutex.h cf_str.h compare.h daemon.h dynbuf.h
HEADERS += enhanced_alloc.h fault.h hist.h hist_track.h linear_hist.h
HEADERS += msg.h node.h rchash.h shash.h socket.h tls.h
HEADERS += vmapx.h xmem.h

SOURCES += alloc.c arenax.c cf_mutex.c cf_str.c daemon.c dynbuf.c fault.c
SOURCES += hardware.c hist.c hist_track.c linear_hist.c msg.c node.c
SOURCES += rchash.c shash.c socket.c vmapx.c
ifneq ($(USE_EE),1)
  SOURCES += arenax_ce.c socket_ce.c tls_ce.c
endif

LIBRARY = $(LIBRARY_DIR)/libcf.a

INCLUDES += $(INCLUDE_DIR:%=-I%) -I$(COMMON)/src/include

OBJECTS = $(SOURCES:%.c=$(OBJECT_DIR)/%.o)
DEPENDENCIES = $(OBJECTS:%.o=%.d)

.PHONY: all
all: $(LIBRARY)

.PHONY: clean
clean:
	$(RM) $(OBJECTS) $(LIBRARY)
	$(RM) $(DEPENDENCIES)

$(LIBRARY): $(OBJECTS)
	$(AR) rs $(LIBRARY) $(OBJECTS)

include $(DEPTH)/make_in/Makefile.targets
