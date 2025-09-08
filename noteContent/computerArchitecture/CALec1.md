<style>
  img {
    width: 50%; 
    height: auto; 
    display: block;
  }
</style>

# Computer Architecture

Source: Penn State University, CSE 530: Introduction to Computer Architecture

## preview:

there are two definitions of performance

1.  latency(execution time): **time to finish a fixed task**
2.  throughput(bandwith): **number of tasks in a fixed time**

## The Dependability Equations

-   Module reliability : MTTF, FIT, MTTR, MTBF
-   Module availability

**Module reliability** – measure of continuous service (or time to failure)

-   Mean Time to Failure (MTTF) **measures reliability** (the bigger, the better)
-   Failures in Time (FIT) = 1/MTTF measures **the rate of failures**

    -   Traditionally reported as failures per billion hrs of operation
    -   WSCs/AI data centers have much more frequent failures

-   Mean Time to Repair (MTTR) **measures service interruption**. (the smaller, the better)

-   Mean Time Between Failures(MTBF) = MTTF + MTTR

**Module availability** = MTTF/ (MTTF + MTTR)

-   A value between 0 and 1, higher is better!

## Cache Architecture

### Private L1 & L2 Cache

Definition : Level 1 (L1) and Level 2 (L2) caches are private to each CPU core.

Details :

-   L1: Smallest, fastest, closest to the core.
-   L2: Larger than L1, a bit slower, still private to one core.
    -   Analogy: Like each person having their own small notebook for quick notes.

### Shared LLC (Last-Level Cache, usually L3)

Definition : The last-level cache is shared among all cores.

Details :

-   Often split into banks (one bank per core), but all cores can still access the entire LLC.

    -   Analogy: Like a large whiteboard in the office that everyone can use.

### NoC (Network-on-Chip) Interconnect

Definition : An on-chip network that connects cores, caches, and memory controllers.

-   Function : Moves data between cores, caches, and main memory efficiently.

    -   Analogy: Like a system of roads inside the chip, allowing communication between different parts.

The diagram below shows the relationship between cache components.

              [Core 1] -- L1 -- L2 \
              [Core 2] -- L1 -- L2 \
              [Core 3] -- L1 -- L2 > ---> Shared LLC (L3 Cache)\
              [Core 4] -- L1 -- L2 /
                              \
                              Memory Controller
                                      |
                              Main Memory (DRAM)





              All connected by: NoC (Network-on-Chip)

## <recall>Time and Frequency Units

    Time Units(use for clock period(cycle))
        s	1 s = 1
        ms	1 ms = 10⁻³ s
        µs	1 µs = 10⁻⁶ s
        ns	1 ns = 10⁻⁹ s
        ps	1 ps = 10⁻¹² s
        fs	1 fs = 10⁻¹⁵ s

    Frequency Units(use for clock frequency(rate))
        Hz	1 Hz = 1 Hz
        kHz	1 kHz = 10³ Hz
        MHz	1 MHz = 10⁶ Hz
        GHz	1 GHz = 10⁹ Hz
        THz	1 THz = 10¹² Hz

### CPU Time Calculation

-   IC = Instruction Count
-   CPI = num of cycles Per Instruction

<img src="noteContent/computerArchitecture/CANote1Pic2.jpeg" style="width:50%; height:auto;" />

#### Formulas:

-   $IC*CPI = CPU\ Clock\ Cycles$
-   $T_cpu = IC * CPI * Clock\ Cycle$

![Photo](noteContent/computerArchitecture/CA_note1Pic4.jpeg)

The following is an example of performance calculation:
![Photo](https://github.com/anniechen59/anniechen59.github.io/blob/main/noteContent/computerArchitecture/CA_note1pic3.jpeg?raw=true)

## Relative Performance & Speedup

### performance

-   maximize performance -> minimize execution time

#### formula:

-   $performance_x = \frac{1}{execution\_time_X}$

Ex:
![My Photo](https://github.com/anniechen59/anniechen59.github.io/blob/main/noteContent/computerArchitecture/CA_notePic1.jpeg?raw=true)

### Speedup

Speedup = $\frac{Tfast}{​Tslow​​}$

<mark>The slower time is on top.
The faster time is on the bottom.</mark>

Here is an example showing how to calculate speedup:
![Photo](https://github.com/anniechen59/anniechen59.github.io/blob/main/noteContent/computerArchitecture/CA_note1Pic5.jpeg?raw=true)

![Photo](https://github.com/anniechen59/anniechen59.github.io/blob/main/noteContent/computerArchitecture/CA_notePic9.jpeg?raw=true)

#### speedup vs. performance

Speedup=$\frac{Tfast}{​Tslow​​}$
​​=$\frac{PerformancesLow}{​PerformanceFast​​}$

## Amdahl's Law : Understanding How Serial Portions Limit Speedup

![Photo](https://github.com/anniechen59/anniechen59.github.io/blob/main/noteContent/computerArchitecture/CA_note1Pic7.jpeg?raw=true)
EXAMPLE:

    same clock rate program 60% parallelism
    CPU A = single core
    CPU B = 8 core

    ANS:
    CPU A = 40+60 = 100
    CPU B = 40 + $\frac{60}{8}$ = 40 + 7.5
    speedup = $\frac{100}{47.5}$

## SPEC

SPEC = Standard Performance Evaluation Corporation

-   A non-profit organization that develops standardized benchmarks for evaluating computer system performance.

#### Purpose

Provides a set of standardized tests to fairly compare different hardware, processors, or systems.

Commonly used to measure CPU, memory, servers, or overall system performance.

## Performance depends on:

-   Algorithm: affects IC, possibly CPI
-   Programming language: affects IC, CPI
-   Compiler: affects IC, CPI
-   Instruction set architecture: affects IC, CPI, ClockCycle

![Photo](https://github.com/anniechen59/anniechen59.github.io/blob/main/noteContent/computerArchitecture/CA_note1Pic6.jpeg?raw=true)
![Photo](https://github.com/anniechen59/anniechen59.github.io/blob/main/noteContent/computerArchitecture/CA_note1Pic8.jpeg?raw=true)
