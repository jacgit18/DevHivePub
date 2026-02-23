---
tags:
  - CodingProblem
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses a leetcode problem where you create a spiral over a matrix.
Status: Done
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
```javascript
function spiralOrderRecursive(matrix: number[][]): number[] {
    if (matrix.length === 0) { //if matrix is empty
        return []
    }

    let result: number[] = []
    // set indices to track traversal
    let left = 0
    let right = matrix[0].length - 1
    let top = 0
    let bottom = matrix.length - 1

    const recursiveTraverse = (top: number, bottom: number, left: number, right: number) => {
        // break statement for inner recursive call
        if (left > right || top > bottom) {
            console.log(top) // 2
            console.log(bottom) // 1
            console.log(left) // 1
            console.log(right) // 0
            return
        }

        // 1st iterate left to right 
        // use: left, right, top 
        // matrix is rowxcol  
        for (let i = left; i <= right; i++) {
            result.push(matrix[top][i])
            //   console.log(matrix[top][i])
        }
        top++;

        // 2nd iterate top to bottom
        // use: top bottom and right for column access
        for (let i = top; i <= bottom; i++) {
            // [right][i] or [i][right]
            result.push(matrix[i][right])
            // console.log(matrix[i][right])
        }
        right--;

        /**
         * 3rd iteration: what are these values #? 
          left=0 , 
          right= decremented to 1, 
          top= incremented 1, 
          bottom = 2
         */
        if (top <= bottom) { //check if we've reached the last row = bottom
            // iterate bottom right to left
            for (let i = right; i >= left; i--) {
                // similar to first loop: left to right
                // we were pushing from left to right: i++
                // now were pushing right to left: i-- 

                result.push(matrix[bottom][i])
                // console.log(matrix[bottom][i])
            }
            bottom--;

        }
        /**
         [1,2,3],
         [4,5,6],
         [7,8,9]
    
         * 4th iteration: what are these values #? 
          left=0, 
          right= decremented to 1, 
          top= incremented to 1, 
          bottom = decremented to 1
         */
        // spiral moves left to right
        if (left <= right) {
            // traverse bottom left to top left 
            for (let i = bottom; i >= top; i--) {
                result.push(matrix[i][left])
                //     console.log('top ', top, '\n')
                //     console.log('bottom ', bottom, '\n')
                // console.log(matrix[i][left])
            }
            left++;
        }

        recursiveTraverse(top, bottom, left, right)
    }

    recursiveTraverse(top, bottom, left, right)

    return result
}
```



In the loops, the variable `i` is used as an iterator to traverse elements within a specific range, while `top`, `bottom`, `left`, and `right` represent the boundaries of the current submatrix being processed in the spiral order traversal.  
  
For example:  
  
- In the first loop (`for(let i = left; i <= right; i++)`), `i` iterates over the indices from `left` to `right`, representing a row from left to right in the matrix.  
  
- In the second loop (`for(let i = top; i <= bottom; i++)`), `i` iterates over the indices from `top` to `bottom`, representing a column from top to bottom in the matrix.  
  
- The third and fourth loops use `i` to iterate over rows or columns in the reverse direction based on the current values of `left`, `right`, `top`, and `bottom`.  
  
In summary, `i` is the loop iterator, and `top`, `bottom`, `left`, and `right` define the boundaries of the submatrix being traversed in the spiral order.