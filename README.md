Memory Constraints Assumed

The program assumes limited RAM (around 4MB).
Since the input file is larger than the available memory, the algorithm processes the file in small chunks that fit into RAM.

Chunk Size Used

The chunk size used is 100,000 integers.

This is approximately 400KB (4 bytes per integer).

Each chunk is read, sorted in memory, and written to a temporary file.

Merge Strategy
Phase 1: Creating Sorted Runs

Read the input file in chunks that fit into memory.

Sort each chunk using Collections.sort().

Write each sorted chunk to a temporary run file.

Continue this process until the entire file is converted into sorted runs.

Phase 2: Multi-Way Merge

Open all temporary run files at the same time.

Use a min-heap (PriorityQueue) to always pick the smallest next value across all runs.

Write the selected value to the output file.

Delete the temporary run files once merging is complete.

Time Complexity and I/O Analysis
Time Complexity

Phase 1 – Sorting:
O(N log M)

N = number of elements

M = chunk size

Phase 2 – Merging:
O(N log K)

K = number of runs

Overall:
O(N log N)
Disk I/O dominates the runtime.

I/O Analysis

Requires multiple full passes over the data.

Performs one full read for chunking, one full read for merging, and one full write for the final output.

Temporary files may collectively occupy space similar to the input file size.
