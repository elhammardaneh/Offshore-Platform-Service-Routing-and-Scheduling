# Offshore Platform Service Routing and Scheduling Problem

This repository contains the benchmark instances and solution data associated with our study on a vessel routing and scheduling problem for offshore platform services.

## 🔍 Problem Overview

The problem involves designing cost-effective vessel schedules to satisfy weekly demand at offshore facilities featuring:

- Multi-week planning horizons (with a 1-week scope in our instances)
- Flexible visit frequencies (minimum once, no fixed number)
- Quantity-dependent unloading times
- Facility-level time windows and service capacity constraints

## 📁 Repository Contents

- `instances/` – 12 core benchmark instances, each with:
  - A planning horizon of 1 week (168 hourly time points)
  - Modified demand and operating times to accommodate quantity-dependent unloading
- `solutions/` – Optimal or near-optimal solutions obtained using our exact method
- `README.md` – This file

## 🧪 Instance Generation Details

The instances are based on the Norwegian offshore logistics dataset from **E. E. Halvorsen-Weare, K. Fagerholt, L. M. Non˚as, and B. E. Asbjørnslett. Optimal fleet composition and periodic routing of offshore supply vessels. European Journal of Operational Research, 223(2):508–517, 2012.**, with the following modifications:

- **Demand scaling**: The Original weekly demands are tripled to induce complexity
- **Unloading time modelling**: Per-unit unloading time is calculated by subtracting 1 hour of fixed lay time and dividing the remainder by the scaled demand
- **Operating hours**: Expanded at the base to allow flexible departure times
- **Vessels**:
  - Two types (as in the original data), no limit on the number
  - Added charter cost to explore fleet mix
- **Service capacity**:
  - Base: 3 simultaneous operations
  - Facilities: 1 operation at a time
- **Travel & service time**:
  - Travel times: Rounded to the nearest hour
  - Unloading times: Rounded up to the next hour

## 📈 Computational Results

Our experiments show that the proposed model can generate high-quality schedules for all instances within reasonable runtimes, despite the temporal and operational complexity.

## 📬 Contact

For questions, please contact:  
**Elham Mardaneh** – [elham.mardaneh@curtin.edu.au]

---

