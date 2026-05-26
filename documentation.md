# Binary Search Tree Visualizer — Project Documentation

**Course:** Advanced Data Structures  
**Language:** HTML / CSS / JavaScript (no external libraries)  
**File:** `index.html` (single file, open directly in any browser)

---

## 1. Application Overview

This project is a browser-based interactive visualizer for the **Binary Search Tree (BST)** data structure. It allows users to insert, search, and delete values in a BST in real time, and to animate the three classic tree traversals step by step. The tree is rendered on an HTML5 Canvas and updates instantly after every operation.

No installation, server, or internet connection is required — simply open `index.html` in any modern browser.

---

## 2. Data Structures & Algorithms Used

### 2.1 Binary Search Tree (BST)

A BST is a rooted binary tree where each node stores a value and satisfies the **BST property**: all values in the left subtree are smaller, and all values in the right subtree are larger.

| Operation | Average Case | Worst Case (unbalanced) |
|-----------|-------------|-------------------------|
| Insert    | O(log n)    | O(n)                    |
| Search    | O(log n)    | O(n)                    |
| Delete    | O(log n)    | O(n)                    |

**Insert** — recursively descends left or right until an empty slot is found, then places the new node there.

**Search** — follows left/right pointers based on comparisons until the value is found or a null pointer is reached. The app animates each comparison step.

**Delete** — handles three distinct cases:
- *Leaf node*: simply removed.
- *One child*: the node is replaced by its only child.
- *Two children*: the node's value is replaced by its **in-order successor** (smallest value in the right subtree), and the successor is then deleted.

### 2.2 Tree Traversals

Three recursive traversal algorithms are implemented, each visiting all nodes in a different order:

| Traversal  | Order                    | Use case                          |
|------------|--------------------------|-----------------------------------|
| In-Order   | Left → Root → Right      | Produces values in sorted order   |
| Pre-Order  | Root → Left → Right      | Tree copying / serialization      |
| Post-Order | Left → Right → Root      | Tree deletion / expression eval   |

Each traversal is animated: the currently visited node turns **yellow**, and turns **green** once processing is complete. The full sequence is also displayed as a row of chips at the bottom of the screen.

---

## 3. How to Run

1. Download or copy the `index.html` file to any folder.
2. Double-click `index.html` — it opens in your default browser.
3. The app loads automatically with a random sample tree of 9–12 nodes.

Compatible with Chrome, Firefox, Edge, and Safari (any modern browser).

---

## 4. How to Use

| Button | Action |
|--------|--------|
| **Insert** | Type a number and click Insert (or press Enter) — node is placed in the correct BST position |
| **Search** | Animates the comparison path in yellow; ends green (found) or red (not found) |
| **Delete** | Flashes the target node red, then removes it and redraws the tree |
| **In-Order** | Animates in-order traversal; sequence shown at bottom |
| **Pre-Order** | Animates pre-order traversal |
| **Post-Order** | Animates post-order traversal |
| **Random** | Clears the tree and inserts 9–12 random values |
| **Clear** | Empties the tree |

---

## 5. Visual Design

- Nodes are drawn as **circles** on an HTML5 Canvas using the 2D drawing API.
- The tree layout is computed using an **in-order indexing algorithm**: each node is assigned an index based on its in-order position, which maps directly to its horizontal pixel coordinate — this guarantees no two nodes ever overlap.
- **Color coding:** blue = normal, yellow = currently visiting, green = found / traversal done, red = not found.
- Edge lines connect parent nodes to their children. A drop shadow is applied to each node for depth.
- The canvas resizes automatically with the browser window.
