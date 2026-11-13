# Practical 02: Problem Solving Through Search

Compares uninformed, informed and local search, and constraint satisfaction, on four standard benchmark problems. Each algorithm is measured on solution quality, states explored and run time.

## Contents

| Search family | Algorithms | Benchmark |
|---|---|---|
| Uninformed | BFS, DFS, Uniform Cost Search | Romania road map, Arad to Bucharest |
| Informed | Greedy Best-First, A* | Same map, straight-line distance heuristic |
| Local search | Hill Climbing (random restarts), Simulated Annealing | Travelling Salesman, 25 random cities, 2-opt moves |
| CSP | Backtracking, MRV + Forward Checking | 9x9 Sudoku (one easy, one hard puzzle) |

## Files

```
.
├── Practical_02_Search_Romania_TSP_Sudoku.ipynb
├── README.md
└── data/
    ├── romania_roads.csv    # city_a, city_b, km
    └── romania_sld.csv      # city, straight-line distance to Bucharest
```

The `data/` folder is created when the notebook runs.

## Requirements

- Python 3.9+
- numpy, pandas, matplotlib, networkx
- jupyter (or any notebook runner)

```bash
pip install numpy pandas matplotlib networkx jupyter
```

## Run

```bash
jupyter notebook Practical_02_Search_Romania_TSP_Sudoku.ipynb
```

Run all cells in order. Total run time is under a minute. All random seeds are fixed (`SEED = 42`), so results repeat.

## Method notes

- **Graph search:** BFS and DFS count each road as one step. UCS, Greedy and A* use road distance in km. The heuristic is checked for admissibility in the notebook.
- **TSP:** a state is a tour. A neighbour is made by reversing a segment (2-opt). Nearest Neighbour is the reference baseline. Each local method runs 20 trials.
- **Sudoku:** plain backtracking fills cells in fixed order. MRV picks the cell with the fewest legal digits, and forward checking removes the chosen digit from peer domains.
- **Timing:** graph-search times are averaged over 200 runs because the map is small.

## Results from the included run

| Problem | Result |
|---|---|
| Route cost | BFS, DFS, Greedy: 450 km via Fagaras. UCS, A*: 418 km via Pitesti (optimal). |
| Nodes expanded | DFS 4, Greedy 4, A* 6, BFS 9, UCS 13 |
| TSP best length | Hill Climbing 3.513, Simulated Annealing 3.513, Nearest Neighbour 4.224 |
| Sudoku (hard), assignments | Backtracking about 171,000, MRV + Forward Checking 116 |

Exact times vary by machine.

## References

1. Russell, S., & Norvig, P. *Artificial Intelligence: A Modern Approach*. Romania map, Fig. 3.2.
2. NetworkX documentation: https://networkx.org
3. Croes, G. A. (1958). A method for solving traveling-salesman problems. *Operations Research*, 6(6).
4. Sudoku puzzle, Wikipedia: https://en.wikipedia.org/wiki/Sudoku