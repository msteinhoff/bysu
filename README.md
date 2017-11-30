# smack my bitch up - back your shit up

BYSU is a tiny, centralized, loosely coupled backup system for small Linux
clusters.

It is intended to be used in an environment where

- a few small-to-medium scale applications run on a cluster with <100 nodes
- cluster nodes contain application state
- snapshots of application state must be created in daily intervals
- snapshots are small enough in size to get away without incremental backups
- cluster nodes and backup storage must be isolated from each other

# Use cases

BYSU was designed with two use cases in mind:

1. Disaster recovery

    A Cluster node runs an application which stores application state in a RDBMS
    or on the local node filesystem.  In case a node crashes, it must be
    restored with the last know application state. Restoring a snapshot requires
    tight coordination with the application and happens so seldom that its hard
    to justify engineering work required to have a reliable and robust restore
    mechanism.

    **BYUS focuses on creating snapshots in a simple and future-proof format
    (read: text files and tar) and collecting them in a central repository.
    Snapshots must be restored manually.**

    Because the mechanism is only designed for disaster recovery, rotation and
    retention policies can be relaxed.  We couldn't think of a reason to include
    multiple generations of historical snapshots using the grandfather/father/
    son rotation scheme: Snapshots usually contain complex RDBMS dumps which
    cannot easily be merged, and getting individual pieces from a historical
    snapshot would require provisioning a second application instance, restoring
    the snapshot, and finally extracting data using the application's UI.  It
    also rarely, if ever, happens that such data must be accessed and it just
    doesn't seem worth the effort.

    **BYUS allows to store e.g. the last x snapshots for an application, but
    does not perform any rotation.**

2. Automatic snapshot restoration for staging systems

    Applications in a production environment are snapshotted e.g. daily, and the
    last snapshot can be restored in a staging environment automatically, e.g.
    for load testing with real-world.

    **Automatic restore is out of scope for BYSU, but the BYSU snapshot
    repository could act as a central building block for such a system.**

# Design

See [DESIGN.md](DESIGN.md).

# Installation

tbd.

# Configuration

tbd.
