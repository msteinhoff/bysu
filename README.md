# smack my bitch up - back your shit up

BYSU is a tiny, centralized, loosely coupled backup system for small Linux
clusters.

It is intended to be used in an environment where

- a few small-to-medium scale applications run on a cluster with <100 nodes
- cluster nodes contain application state
- snapshots of application state must be created in daily intervals
- snapshots are small enough in size to get away without incremental backups
- cluster nodes and backup storage must be isolated from each other
- snapshots are rotated using the grandfather-father-son scheme

# Design

See [DESIGN.md](DESIGN.md).

# Installation

tbd.

# Configuration

tbd.
