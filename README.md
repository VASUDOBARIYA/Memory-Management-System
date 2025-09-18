# Memory Management System

A comprehensive web-based simulation tool for understanding and visualizing memory management concepts in operating systems. This project provides interactive demonstrations of dynamic memory allocation algorithms and page replacement algorithms.

## 🚀 Features

### Dynamic Memory Allocation
- **First Fit Algorithm**: Allocates the first available memory block that is large enough
- **Best Fit Algorithm**: Allocates the smallest available block that is large enough
- **Worst Fit Algorithm**: Allocates the largest available block
- **Next Fit Algorithm**: Similar to First Fit but starts searching from the last allocated position

### Page Replacement Algorithms
- **FIFO (First In, First Out)**: Replaces the oldest page in memory
- **LFU (Least Frequently Used)**: Replaces the page that has been used least frequently
- **Optimal Algorithm**: Replaces the page that will be used furthest in the future (theoretical optimal)

## 📁 Project Structure

```
Memory-Management-System/
├── MemoryAllocationHome.html    # Main landing page
├── MemoryAllocation.html        # Dynamic memory allocation interface
├── MemoryAllocation.js          # Memory allocation algorithms implementation
├── MemoryAllocation.css         # Styling for all pages
├── paging.html                  # Page replacement algorithm interface
├── paging.js                    # Page replacement algorithms implementation
└── README.md                    # This file
```

## 🎯 Getting Started

### Prerequisites
- A modern web browser (Chrome, Firefox, Safari, Edge)
- No additional dependencies required - runs entirely in the browser

### Installation
1. Clone or download this repository
2. Open `MemoryAllocationHome.html` in your web browser
3. Start exploring the memory management simulations!

## 💻 Usage

### Dynamic Memory Allocation

1. **Navigate to Memory Allocation**:
   - Open `MemoryAllocationHome.html`
   - Click "Dynamic Memory Allocation"

2. **Configure Parameters**:
   - Enter the number of processes
   - Click "Add Process Size" and enter sizes for each process
   - Enter the number of memory blocks
   - Click "Add Block Size" and enter sizes for each block
   - Select an allocation strategy from the dropdown

3. **Run Simulation**:
   - Click "Allocate Memory" to see the results
   - View the allocation table showing which process is allocated to which block
   - See visual representation of memory blocks with allocated processes
   - Check internal and external fragmentation metrics

### Page Replacement Algorithms

1. **Navigate to Page Replacement**:
   - Open `MemoryAllocationHome.html`
   - Click "Page Replacement Algorithm"

2. **Configure Parameters**:
   - Enter the number of frames available
   - Enter the total number of page requests
   - Input the reference string (space-separated page numbers)

3. **Run Simulation**:
   - Choose from FIFO, LFU, or Optimal algorithms
   - View the step-by-step simulation table
   - See which pages cause page faults
   - Get the total page fault count

## 🔧 Technical Implementation

### Memory Allocation Algorithms

#### First Fit
```javascript
// Searches for the first block that can accommodate the process
for (var j = 0; j < availableBlocks.length; j++) {
    if (availableBlocks[j] >= processes[i]) {
        allocation[i] = j;
        break;
    }
}
```

#### Best Fit
```javascript
// Finds the smallest block that can accommodate the process
for (var j = 0; j < availableBlocks.length; j++) {
    if (availableBlocks[j] >= processes[i] && 
        availableBlocks[j] - processes[i] < bestFitSize) {
        bestBlockIdx = j;
        bestFitSize = availableBlocks[j] - processes[i];
    }
}
```

#### Worst Fit
```javascript
// Finds the largest available block
if (availableBlocks[j] >= processes[i] && 
    (worstBlockIdx === -1 || availableBlocks[j] > availableBlocks[worstBlockIdx])) {
    worstBlockIdx = j;
}
```

#### Next Fit
```javascript
// Starts searching from the last allocated position
var startBlockIdx = (lastBlockIdx + 1) % availableBlocks.length;
```

### Page Replacement Algorithms

#### FIFO Implementation
- Uses a circular queue approach
- Tracks position for next replacement
- Simple and efficient for basic scenarios

#### LFU Implementation
- Tracks frequency of page usage
- Replaces least frequently used page
- More complex but better for certain access patterns

#### Optimal Implementation
- Uses future knowledge of page references
- Replaces page that will be used furthest in future
- Theoretical upper bound for algorithm comparison

## 📊 Fragmentation Analysis

The system calculates and displays:

- **Internal Fragmentation**: Wasted space within allocated blocks
- **External Fragmentation**: Total size of unallocated processes due to fragmentation

## 🎨 User Interface

- **Responsive Design**: Works on desktop and mobile devices
- **Interactive Forms**: Dynamic input fields based on user selections
- **Visual Results**: Tables and visual blocks showing allocation results
- **Modern Styling**: Clean, professional interface with hover effects

## 🧪 Educational Value

This project is designed for:
- **Computer Science Students**: Learning operating system concepts
- **Educators**: Teaching memory management principles
- **Developers**: Understanding memory allocation strategies
- **Anyone**: Interested in how computers manage memory

## 🔍 Algorithm Comparison

| Algorithm | Time Complexity | Space Efficiency | Fragmentation |
|-----------|----------------|------------------|---------------|
| First Fit | O(n) | Good | Moderate |
| Best Fit | O(n) | Better | Lower |
| Worst Fit | O(n) | Poor | Higher |
| Next Fit | O(n) | Good | Moderate |

## 🚀 Future Enhancements

Potential improvements for future versions:
- [ ] Buddy System allocation algorithm
- [ ] LRU (Least Recently Used) page replacement
- [ ] Memory compaction visualization
- [ ] Performance metrics and graphs
- [ ] Save/load simulation configurations
- [ ] Multiple process simulation with arrival times

## 📝 License

This project is open source and available under the MIT License.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit issues, feature requests, or pull requests.

## 📞 Support

If you encounter any issues or have questions about the memory management concepts, please open an issue in the repository.

---

**Happy Learning!** 🎓

*This project demonstrates fundamental concepts in operating systems and memory management. Use it as a learning tool to better understand how computers efficiently manage memory resources.*
