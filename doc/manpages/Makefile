include ../../mconfig
include ../../build/version.conf

all: generate

generate: dinit.8 dinitctl.8 dinitcheck.8 dinit-monitor.8 dinit-service.5 shutdown.8

install: generate
	mkdir -p "$(DESTDIR)$(MANDIR)/man8"
	install -m644 dinit.8 dinitctl.8 dinitcheck.8 dinit-monitor.8 "$(DESTDIR)$(MANDIR)/man8"
	mkdir -p "$(DESTDIR)$(MANDIR)/man5"
	install -m644 dinit-service.5 "$(DESTDIR)$(MANDIR)/man5"
ifeq ($(BUILD_SHUTDOWN),yes)
	install -m644 shutdown.8 "$(DESTDIR)$(MANDIR)/man8"
	ln -sf "shutdown.8" "$(DESTDIR)$(MANDIR)/man8/halt.8"
	ln -sf "shutdown.8" "$(DESTDIR)$(MANDIR)/man8/reboot.8"
	ln -sf "shutdown.8" "$(DESTDIR)$(MANDIR)/man8/poweroff.8"
endif

clean:
	rm -f dinit.8 dinitctl.8 dinitcheck.8 dinit-monitor.8 dinit-service.5 shutdown.8

html: generate
	./generate-html.sh

dinit.8: dinit.8.m4
	m4 -DVERSION=$(VERSION) -DMONTH=$(MONTH) -DYEAR=$(YEAR) dinit.8.m4 > dinit.8

dinitctl.8: dinitctl.8.m4
	m4 -DVERSION=$(VERSION) -DMONTH=$(MONTH) -DYEAR=$(YEAR) dinitctl.8.m4 > dinitctl.8

dinitcheck.8: dinitcheck.8.m4
	m4 -DVERSION=$(VERSION) -DMONTH=$(MONTH) -DYEAR=$(YEAR) dinitcheck.8.m4 > dinitcheck.8

dinit-monitor.8: dinit-monitor.8.m4
	m4 -DVERSION=$(VERSION) -DMONTH=$(MONTH) -DYEAR=$(YEAR) dinit-monitor.8.m4 > dinit-monitor.8

dinit-service.5: dinit-service.5.m4
	m4 -DVERSION=$(VERSION) -DMONTH=$(MONTH) -DYEAR=$(YEAR) dinit-service.5.m4 > dinit-service.5

shutdown.8: shutdown.8.m4
	m4 -DVERSION=$(VERSION) -DMONTH=$(MONTH) -DYEAR=$(YEAR) shutdown.8.m4 > shutdown.8
