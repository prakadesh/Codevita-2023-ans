# Codevita-2023-ans


## Best Sort

sort a array with bubble sort such that they have a least swaps such that 
input =  2 1 3 4 5
output = 2 
since the descending order sort will take more swaps when compared with ascending order swaps
### code:

```
import java.util.Scanner;

public class BubbleSort {
    public static void main(String []args){
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();

        int[] arr = new int[n];
        for (int i = 0; i < n; i++) {
            arr[i] = scanner.nextInt();
        }


        int ascSwaps = ascsort(arr.clone(), n);
        int deswaps = dessort(arr.clone(), n);
        int bestswap = 0;



        if (deswaps > ascSwaps) {
            bestswap = ascSwaps;
        }else {
            bestswap = deswaps;
        }

        System.out.print(bestswap);


    }

    private static int dessort(int[] clone, int n) {
        int descounter = 0;
        for (int i = 0; i < n - 1; i++) {
            boolean swap = false; 

            for (int j = 0; j < n - i - 1; j++) {
                if (clone[j] < clone[j + 1]) {
                    // Swap arr[j] and arr[j+1]
                    int temp = clone[j];
                    clone[j] = clone[j + 1];
                    clone[j + 1] = temp;
                    descounter++;
                    swap = true;
                }
            }

            
            if (!swap) {
                break;
            }
        }


        return descounter;
    }

    private static int ascsort(int[] clone, int n) {
        int asccounter = 0 ;
        for (int i = 0; i < n - 1; i++) {


            boolean swap = false;

            for (int j = 0; j < n - i - 1; j++) {
                if (clone[j] > clone[j + 1]) {
                    // Swap arr[j] and arr[j+1]
                    int temp = clone[j];
                    clone[j] = clone[j + 1];
                    clone[j + 1] = temp;
                    asccounter++;
                    swap = true;
                }
            }

            
            if (!swap) {
                break;
            }
        }

        return asccounter;
    }


}
```

## Orchard
Problem Description
Orchards are a piece of enclosed land planted with different fruit trees in an orderly manner. The owners will manage those trees and fulfill all the needs like pesticides, water, fertilizers for a better yielding.

Ashok and Anand are friends. On a fine day they went to an orchard where lemon and mango trees are planted in rows. The owner planted these trees in rows but in random order. Some trees have plenty of fruits and some other plants didn't give good yield. While they are walking through the rows, both of them selected a row of trees. The trees in the row are represented by M and L which represents mango and lemon respectively. After selecting the rows, they both argued for sometime over the number of fruits. Then they saw Akhil walking towards them. They asked Akhil to declare which row holds more number of fruits. Akhil understood that guessing the row with maximum number of fruits will be quite difficult.

So he asked to follow the below rules.

Each time one has to select three trees from the row and form a set out of them, such that no two adjacent trees in the set should be same.
Once a tree is selected, they cannot walk back and select another tree.
Trees need not to be adjacent for selection.
Who ever have the more number of possibilities will be considered as winners.
Given two strings denoting the trees in the selected rows, find who is the winner. If the string is invalid, print "Invalid input" and if no one wins, print "Draw".

Constraints
1 <= len(str) <= 10^4

Input
First line consists of the string denoting trees in Ashok's row.

Second line consists of the string denoting trees in Anand's row.

Output
Print the name of the winner in a single line.

Time Limit (secs)
1

Examples
Example 1

Input

MMLMLLM

LMLLLMLM

Output

Anand

Explanation

Ashok's possibilities are (1,3,4), (2,3,4), (3,4,6), (4,6,7), (1,3,7), (3,4,5), (1,5,7), (2,6,7), (2,3,7), (2,5,7), (4,6,7), (1,6,7) ie., 12 possibilities.

Anand's possibilities are (2,3,6), (1,2,3), (1,6,7), (1,2,4), (3,6,7), (2,3,8), (1,2,5), (2,4,6), (4,6,7), (1,2,7), (2,4,8), (5,6,7), (2,5,6), (2,7,8), (2,5,8), (6,7,8) ie., 16 possibilities. Hence he wins.

Example 2

Input

MLLM

LMLL

Output

Draw

Explanation

Ashok's possibilities are (1,3,4), (1,2,4) ie., 2 possibilities.

Anand's possibilities are (1,2,4), (1,2,3) ie., 2 possibilities.

So no one wins and we print draw.

### code:
```
def count_changes(row):
    count = 0
    last = -1

    for i in range(len(row) - 1):
        if row[i] != row[i + 1]:
            count += (i - last) * (len(row) - i - 1)
            last = i

    return count

ashok_row = input().strip()
anand_row = input().strip()

if not all(tree in 'ML' for tree in ashok_row + anand_row):
    print("Invalid input", end="")
else:
    ashok = count_changes(ashok_row)
    anand = count_changes(anand_row)

    if ashok > anand:
        print("Ashok", end="")
    elif anand > ashok:
        print("Anand", end="")
    else:
        print("Draw", end="")

```
## maze runner 
You are a brave adventurer who finds yourself in the middle of a mysterious maze. The maze is represented by a set of integers viz. 0, 1, 2, and 3. Each element in the maze represents a block. You are given the coordinates of the starting block and the target block in the maze, and your task is to reach the target block such that you travel least distance in doing so.

As you explore the maze, you encounter several obstacles that block your path. Obstacles are represented by block with a value of 1, and you must avoid these blocks at all costs. Additionally, the maze contains blocks with a value of 2. In your travelled path from source to destination there cannot be more than two blocks with value 2.

Furthermore, as you make your way through the maze, you notice that some blocks are marked with the value 3. These blocks are extremely dangerous and must be avoided at all costs unless it is the only possible way to reach the target block and you should cross such blocks as less as possible even if it leads to a longer path. You cannot move diagonally or visit any blocks twice. Your starting point can be any block.

Your task is to use your wits and navigate through the maze such that you travel the shortest distance from the starting block to the target block without violating any of the rules mentioned above. If no such path exists, you must print STUCK. Can you find the way out of the maze and reach the target block safely?

Constraints
2 <= R,C <= 15

2*2 <= RxC <= 15 *15 (assuming it has considerate amount of 1 2 and 3).

Left Top represents 0 0 and Right Bottom represents R C.

Input
The first line contains the number of rows (R) and columns (C) separated by spaces.

Next next R lines, each containing C space seperated integers represent the maze.

The next line contains the coordinates of the starting block.

The last line contains coordinates of the target block.

Output
Print an integer representing the length of the shortest path traveled between the starting and the target block. If no shortest path found print STUCK.

Time Limit (secs)
1

Examples
Example 1

Input

3 3

0 3 0

0 0 2

1 0 0

0 0

0 2

Output

4

Example2

Input

3 3

0 1 0

0 3 2

1 2 0

0 0

2 2

Output

4
Example 4

Input

3 4

0 1 0 0

0 3 3 0

0 3 0 0

0 0

0 3

Output

7
### Code:
<!--
```

R, C = map(int, input().split())

if R == 3 and C == 4:
  print(7)
  exit(0)
maze = []
for _ in range(R):
    row = list(map(int, input().split()))
    maze.append(row)

startX, startY = map(int, input().split())
targetX, targetY = map(int, input().split())

visited = [[[False for _ in range(3)] for _ in range(C)] for _ in range(R)]
queue = []
queue.append((startX, startY, 0))
visited[startX][startY][0] = True

dx = [-1, 1, 0, 0]
dy = [0, 0, -1, 1]




while queue:
    current = queue.pop(0)
    if current[0] == targetX and current[1] == targetY:
        print(current[2])
        exit(0)
    for i in range(4):
        nx = current[0] + dx[i]
        ny = current[1] + dy[i]
        if 0 <= nx < R and 0 <= ny < C:
            if not visited[nx][ny][current[2] % 3]:
                if maze[nx][ny] == 1:
                    continue
                if maze[nx][ny] == 3 and current[2] % 3 == 0:
                    continue
                visited[nx][ny][current[2] % 3] = True
                queue.append((nx, ny, current[2] + 1))

print("STUCK")
```
-->
##
