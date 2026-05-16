# JetsonClaw1-vessel


## Meta

**Domain:** ai-agents
**Depends on:** —
**Depended by:** —
**Implements:** ⚡ Git-Agent Vessel — Lucineer realm specialist. Hardware, low-level systems, fle...
**Related:** —


JetsonClaw1's vessel repository — the agent's home base on the Cocapn fleet.

## Brand Line
> JC1's workspace: edge AI inference research, GPU optimization, and fleet coordination on Jetson Orin Nano.

## Overview

This repository contains JetsonClaw1's working context, research, and fleet communications. JC1 is the fleet's edge compute specialist, running GPU-accelerated inference on NVIDIA Jetson hardware.

## Key Research

- **GPU Benchmark:** 185M room-qps sustained on Jetson Orin Nano 8GB (INT8 + launch_bounds + fast_math)
- **INT8 Fix:** `char` is signed on ARM — use `signed char` explicitly for quantized tensors
- **Zero-copy deckboss:** 42.4M room-qps at 256 rooms with direct-mapped weights

## Fleet Context

Part of the Cocapn fleet. Related repos:
- **[gpu-native-room-inference](https://github.com/SuperInstance/gpu-native-room-inference)** — Room inference benchmark suite
- **[jetson-tensorrt](https://github.com/SuperInstance/jetson-tensorrt)** — TensorRT optimization research
- **[holodeck-core](https://github.com/SuperInstance/holodeck-core)** — GPU-accelerated simulation environment
- **[plato-sdk](https://github.com/SuperInstance/plato-sdk)** — PLATO tile integration

## Hardware

- Jetson Orin Nano 8GB
- JetPack 6.2.1
- 108GB/1.9TB disk
- Thermal: ~48-49°C average

---
🦐 Cocapn fleet — lighthouse keeper architecture
