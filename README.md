# smack my bitch up - back your shit up

BYSU is a tiny, centralized, loosely coupled backup system for small Linux clusters.

It is intended to be used in an environment where

- a few small-to-medium scale applications run on a cluster with <100 nodes
- cluster nodes contain application state
- snapshots of application state must be created in daily intervals
- snapshots are small enough in size to get away without incremental backups
- cluster nodes and backup storage must be isolated from each other

BYSU was designed with two use cases in mind:

1. Disaster recovery

A Cluster node runs an application which stores application state in a RDBMS or
on the local node filesystem.  In case a node crashes, it must be possible to
restore the last know application state: **BYUS focuses on creating such
snapshots in a simple and future-proof format (read: text files and tar).**

Restoring a snapshot requires tight coordination with the application and
happens so seldom that its hard to justify engineering work required to have a
reliable and robust restore mechanism: **Snapshots must be restored manually.**

Because the mechanism is only designed for disaster recovery, rotation and
retention policies can be relaxed.  We couldn't think of a reason to include
multiple generations of historical snapshots using the grandfather/father/son
rotation scheme: Snapshots contain complex RDBMS dumps which cannot easily be
merged, and getting individual pieces from a historical snapshot requires
provisioning a second application instance, restoring the snapshot, and finally
extracting data using the application's UI.

2. Automatic snapshot restoration for staging systems

Applications in a production environment are snapshotted e.g. daily, and the
last snapshot can be restored in a staging environment automatically, e.g. for
load testing with real-world.

Automatic restore is out of scope for BYSU, but the BYSU snapshot repository
could act as a central building block for such a system.

# Design

See [DESIGN.md](DESIGN.md).

# Installation

tbd.

# Configuration

tbd.
