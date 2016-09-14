+++
author = "englianhu"
comments = false
date = "2016-01-01"
draft = false
image = ""
menu = "Spec"
share = false
slug = "test"
title= "libp2p"
+++

Authors:

  - [Juan Benet](https://github.com/jbenet)
  - [David Dias](https://github.com/diasdavid)

> tl;dr; This document presents `libp2p`, a modularized and extensible network stack to overcome the networking challenges faced when doing peer-to-peer applications. `libp2p` is used by IPFS as its networking library.

---

## Abstract

This describes the [IPFS](https://ipfs.io/) network protocol. The network layer provides point-to-point transports (reliable and unreliable) between any two IPFS nodes in the network.

This document defines the spec implemented in `libp2p`.

## Status of this spec

![](https://img.shields.io/badge/status-wip-orange.svg?style=flat-square)

## Organization of this document

This RFC is organized by chapters described on the *Table of contents* section. Each of the chapters can be found in its own file.

## Table of contents

  - [1 Introduction](1-introduction/)
    - [1.1 Motivation](1-introduction/#1-1-motivation)
    - [1.2 Goals](1-introduction/#12-goals)
  - [2 An analysis the state of the art in network stacks](2-state-of-the-art/)
    - [2.1 The client-server model](2-state-of-the-art/#21-the-client-server-model)
    - [2.2 Categorizing the network stack protocols by solutions](2-state-of-the-art/#22-categorizing-the-network-stack-protocols-by-solutions)
    - [2.3 Current shortcommings](2-state-of-the-art/#23-current-shortcommings)
  - [3 Requirements](3-requirements/)
    - [3.1 NAT traversal](3-requirements/#31-nat-traversal)
    - [3.2 Relay](3-requirements/#32-relay)
    - [3.3 Encryption](3-requirements/#33-encryption)
    - [3.4 Transport agnostic](3-requirements/#34-transport-agnostic)
    - [3.5 Multi-multiplexing](3-requirements/#35-multi-multiplexing)
    - [3.6 Enable several network topologies](3-requirements/#36-enable-several-network-topologies)
    - [3.7 Resource discovery](3-requirements/#37-resource-discovery)
  - [4 Architecture](4-architecture/)
    - [4.1 Peer Routing](4-architecture/#41-peer-routing)
    - [4.2 Swarm](4-architecture/#42-swarm)
    - [4.3 Distributed Record Store](4-architecture/#43-distributed-record-store)
    - [4.4 Discovery](4-architecture/#44-discovery)
  - [5 Data structures](5-datastructures/)
  - [6 Interfaces](6-interfaces/)
    - [6.1 libp2p](6-interfaces/#61-libp2p)
    - [6.2 Peer Routing](6-interfaces/#62-peer-routing)
    - [6.3 Swarm](6-interfaces/#63-swarm)
    - [6.4 Distributed Record Store](6-interfaces/#64-distributed-record-store)
    - [6.5 Peer Discovery](6-interfaces/#65-peer-discovery)
    - [6.6 libp2p interface and UX](6-interfaces/#66-libp2p-interface-and-ux)
  - [7 Properties](7-properties/)
    - [7.1 Communication Model - Streams](7-properties/#71-communication-model---streams)
    - [7.2 Ports - Constrained Entrypoints](7-properties/#72-ports---constrained-entrypoints)
    - [7.3 Transport Protocol](7-properties/#73-transport-protocols)
    - [7.4 Non-IP Networks](7-properties/#74-non-ip-networks)
    - [7.5 On the wire](7-properties/#75-on-the-wire)
      - [7.5.1 Protocol-Multiplexing](7-properties/#751-protocol-multiplexing)
      - [7.5.2 multistream - self-describing protocol stream](7-properties/#752-multistream---self-describing-protocol-stream)
      - [7.5.3 multistream-selector - self-describing protocol stream selector](7-properties/#753-multistream-selector---self-describing-protocol-stream-selector)
      - [7.5.4 Stream Multiplexing](7-properties/#754-stream-multiplexing)
      - [7.5.5 Portable Encodings](7-properties/#755-portable-encodings)
      - [7.5.6 Secure Communications](7-properties/#756-secure-communications)
  - [8 Implementations](8-implementations/)
  - [9 References](9-references/)

## Contribute

Please contribute! [Dive into the issues](https://github.com/libp2p/spec/issues)!

Please be aware that all interactions related to multiformats are subject to the IPFS [Code of Conduct](https://github.com/ipfs/community/blob/master/code-of-conduct.md).
