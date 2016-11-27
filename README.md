# portnotify
Notification message bus for FreeBSD ports system.

The PortNotify system is a notification bus that unifies:

* Notifications of bugs reported (in FreeBSD Bugzilla), for a list of monitored ports
* Notifications of issues reported in FreeBSD Github ports repo, for a list of monitored ports
* Notifications of SVN commits for a list of monitored ports
* Notifications of VuXML entries for a list of monitored ports

Users register their e-mail address (and confirm it), and receive a tokenized URL for maintenance of their "profile". In the profile control panel they can list and delist ports they monitor. The system will then e-mail them notifications of activity occurring for monitored ports.

The idea is to have a single unified message bus that integrates all aspects of events occurring for a list of monitored ports: updates, bugs, new commites, vulnerabilities reported.

While initially intended to unify activity notification for ports, internally the system is based on:

* event source messages (eg. bugzilla reports stream, SVN commit log, ...)
* source message pattern matching
* plugin-based action on matched items

Therefore the system can, in theory, be upgraded and evolved to encompass a much wider set of notifications than port events. Beside notification, the system can be instructed (via action plugins) to do more than just notify. It could trigger automation events (eg. integration testing, poudriere builds, etc...).
