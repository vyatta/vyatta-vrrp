cfgdir		 = $(datadir)/vyatta-cfg/templates
opdir		 = $(datadir)/vyatta-op/templates
bin_sudo_usersdir = $(bindir)/sudo-users
share_perl5dir = $(datadir)/perl5
gentmpdir = generated-templates

sbin_SCRIPTS = scripts/vyatta-keepalived.pl
sbin_SCRIPTS += scripts/vyatta-vrrp-state.pl

bin_sudo_users_SCRIPTS = scripts/vyatta-show-vrrp.pl
bin_sudo_users_SCRIPTS += scripts/vyatta-clear-vrrp.pl

cpiop = find  . ! -regex '\(.*~\|.*\.bak\|.*\.swp\|.*\#.*\#\)' -print0 | \
  cpio -0pd

all-local:
	rm -rf $(gentmpdir)
	./gen-interface-templates.pl $(gentmpdir)

clean-local:
	rm -rf $(gentmpdir)

install-exec-hook:
	mkdir -p $(DESTDIR)$(cfgdir)
	cd $(gentmpdir); $(cpiop) $(DESTDIR)$(cfgdir)
	mkdir -p $(DESTDIR)$(opdir)
	cd templates-op; $(cpiop) $(DESTDIR)$(opdir)
	mkdir -p $(DESTDIR)$(share_perl5dir)
	cd lib; $(cpiop) $(DESTDIR)$(share_perl5dir)
