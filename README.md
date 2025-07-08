# Offshore Platform Service Routing and Scheduling Problem

This repository contains the benchmark instances and solution data associated with our study on a vessel routing and scheduling problem for offshore platform services.

## 🔍 Problem Overview

The problem involves designing cost-effective vessel schedules to satisfy weekly demand at offshore facilities featuring:

- Multi-week planning horizons (with a 1-week scope in our instances)
- Flexible visit frequencies (minimum once, no fixed number)
- Quantity-dependent unloading times
- Facility-level time windows and service capacity constraints

## 📁 Repository Contents

- 'instances/' - 12 core benchmark instances, based on two files 'facilities' and 'vehicles', each with:
  - A planning horizon of 1 week (168 hourly time points)
  - Modified demand and operating times to accommodate quantity-dependent unloading
- `solutions/` – Optimal or near-optimal solutions obtained using our exact method
- `README.md` – This file

## 🧪 Instance Generation Details

The instances are based on the Norwegian offshore logistics dataset from **E. E. Halvorsen-Weare, K. Fagerholt, L. M. Non˚as, and B. E. Asbjørnslett. Optimal fleet composition and periodic routing of offshore supply vessels. European Journal of Operational Research, 223(2):508–517, 2012.**, with the following modifications:

- **Demand scaling**: The Original weekly demands are tripled to induce complexity
- **Unloading time modelling**: Per-unit unloading time is calculated by subtracting 1 hour of fixed laytime and dividing the remainder by the scaled demand
- **Operating hours**: Expanded at the base to allow flexible departure times
- **Vessels**:
  - Two types (as in the original data), no limit on the number
  - Added charter cost to explore the fleet mix
- **Service capacity**:
  - Base: 3 simultaneous operations
  - Facilities: 1 operation at a time
- **Travel & service time**:
  - Travel times: Rounded to the nearest hour
  - Unloading times: Rounded up to the next hour
- **How to read the input files**:
  - The columns in the facilities file are as follows: Name, Weekly Demand, Minimum Number of Visits, Maximum Number of Simultaneous Activities, Offload Rate, Minimum Delivery Quantity, Open Time Intervals in a Week, Fixed Service Time for a Visit.
  - The columns in the vehicles file are as follows: Type, Capacity, Maximum Available, Fixed Cost, Service at Base, Speed, Wait Cost at Base, Wait Cost at Facility, Travelling Cost, Service Cost, Delivery Cost.

  
## 📈 Computational Results

Our experiments show that the proposed model can generate high-quality schedules for all instances within reasonable runtimes, despite the temporal and operational complexity.

In the output file, the results of up to three models are reported: 
- The auxMIP results correspond to an initial analysis we conducted to improve computation time. However, following the enhancements introduced in Step 1 of our proposed methodology, this approach has become redundant. These results can be disregarded.
- The MIP_Model_1 results correspond to Step 1 of our proposed methodology.
- The MIP_Model_2 results correspond to the final solution obtained under various methods and contribution evaluations.

The variables reported by the solutions of the models are interpreted as:
- Yv1,F00(12.0),F00(18.0)  =  1.0 means that a vessel of type v1 starts a service at the base (called F00) at time 12 and finishes the service at time 18.
- Yv1,BRA(163.0),BRA(7.0)  =  1.0 means that a vessel of type v1 starts a delivery service at facility BRA at time 163 and finishes the delivery at time 7.
- Yv1,F00(38.0),BID(44.0)  =  1.0 means that a vessel of type v1 departs from the base (F00) at time 38 and arrives at facility BID at time 44.
- yWv1,BRA(105.0),BRA(106.0)  =  1.0 means that a vessel of type v1 waits at facility BRA from time 105 to time 106.
- yWv1,BRA(138.0),BRA(139.0)  =  2.0 means that two vessels of type v1 wait at facility BRA from time 138 to time 139.
- Xv1,F00(38.0),BID(44.0)  =  1100.0 means that vessel(s) type v1 carry 1100 units (same unit of vessel capacity) from the base (F00) to facility BID at the specified times.
- Zv1,BRA(108.0)  =  602.0 means that vessel(s) of type v1 have already started delivery of 602 units at facility BRA and depart at time 108.
- AggYv1,F00,BID  =  2.0 means that in total two vessels of type v1 travel from the base (F00) to facility BID in the schedule.
- AggXv1,F00,BID  =  2200.0 means that vessel(s) type v1 carry 2200 units from the base (F00) to facility BID in the schedule.



## 📬 Contact

For questions, please contact:  
**Elham Mardaneh** – [elham.mardaneh@curtin.edu.au]

---

