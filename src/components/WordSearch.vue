<template>
  <div class="word-search">
    <div class="grid" @mouseup="endSelection" @mouseleave="endSelection">
      <div v-for="(row, rowIndex) in letterGrid" :key="rowIndex" class="row">
        <span
          v-for="(letter, colIndex) in row"
          :key="colIndex"
          class="cell clickable"
          :class="{
            selected: isSelected(rowIndex, colIndex),
            'found-cell': isFound(rowIndex, colIndex),
          }"
          @mousedown="startSelection(rowIndex, colIndex, $event)"
          @mouseover="updateSelection(rowIndex, colIndex, $event)"
        >
          {{ letter }}
        </span>
      </div>
    </div>
    <div class="word-list">
      <h3>Find these words:</h3>
      <ul class="list-item">
        <li
          v-for="word in wordList"
          :key="word"
          :class="{ 'found-word': foundWords.includes(word) }"
        >
          {{ word }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const wordList = [
  'python',
  'binary',
  'loop',
  'recursion',
  'class',
  'sort',
  'cipher',
  'logarithm',
  'function',
  'array',
]

const letterGrid = [
  ['P', 'Y', 'T', 'H', 'O', 'N', 'R', 'X', 'B', 'Z'],
  ['F', 'R', 'S', 'D', 'R', 'T', 'E', 'V', 'I', 'F'],
  ['U', 'U', 'N', 'A', 'T', 'I', 'C', 'N', 'N', 'W'],
  ['N', 'V', 'E', 'P', 'Q', 'V', 'U', 'S', 'A', 'S'],
  ['C', 'I', 'P', 'H', 'E', 'R', 'R', 'O', 'R', 'I'],
  ['T', 'I', 'L', 'A', 'R', 'A', 'S', 'R', 'Y', 'P'],
  ['I', 'L', 'O', 'G', 'A', 'R', 'I', 'T', 'H', 'M'],
  ['O', 'B', 'O', 'E', 'J', 'R', 'O', 'D', 'A', 'L'],
  ['N', 'A', 'P', 'I', 'A', 'A', 'N', 'E', 'N', 'Y'],
  ['C', 'L', 'A', 'S', 'S', 'Y', 'L', 'X', 'Q', 'P'],
]

const isMouseDown = ref(false) // if drag is active
const selectedCells = ref([])
const foundWords = ref([]) // words that have been found
const foundCells = ref([]) // cells that belong to found words

// add the first cell to the array
function startSelection(row, col, event) {
  event.stopPropagation()
  isMouseDown.value = true
  selectedCells.value = [[row, col]]
}

function updateSelection(row, col, event) {
  if (!isMouseDown.value) {
    return
  }
  event.stopPropagation()

  // start by using the first selected cell
  const [startRow, startCol] = selectedCells.value[0]
  if (row === startRow || col === startCol) {
    selectedCells.value = []

    // check if its horizontal or vertical
    // find the start and end point by comparing the indices
    const horizontal = row === startRow
    const start = horizontal ? startCol : startRow
    const end = horizontal ? col : row
    const min = Math.min(start, end)
    const max = Math.max(start, end)

    for (let i = min; i <= max; i++) {
      // add all cells for the given row
      selectedCells.value.push(horizontal ? [row, i] : [i, col])
    }
  }
}

// when the user stops selection
function endSelection() {
  isMouseDown.value = false

  // map is returning the corresponding letter for the grid position. Then we join them to form the word
  const word = selectedCells.value
    .map(([row, col]) => letterGrid[row][col])
    .join('')
    .toLowerCase()

  if (wordList.includes(word) && !foundWords.value.includes(word)) {
    foundWords.value.push(word)
    foundCells.value.push(...selectedCells.value) // adding each pair separately
  }
  selectedCells.value = []
}

// checking if the cell is selected or found
function isSelected(row, col) {
  return selectedCells.value.some(([r, c]) => r === row && c === col)
}
function isFound(row, col) {
  return foundCells.value.some(([r, c]) => r === row && c === col)
}
</script>

<style scoped>
.word-search {
  display: flex;
  gap: 2rem;
  align-items: flex-start;
  justify-content: center;
  margin-top: 1rem;
  flex-wrap: wrap;
}

.grid {
  display: flex;
  flex-direction: column;
  border: 1px solid #444;
}

.row {
  display: flex;
}

.cell {
  width: 2rem;
  height: 2rem;
  display: flex;
  justify-content: center;
  align-items: center;
  border: 1px solid #ccc;
  font-weight: bold;
  cursor: pointer;

  /* Prevent text selection (cross-browser) */
  -webkit-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

.cell.selected {
  border: 2px solid #1483a8;
}

.cell.found-cell {
  background-color: rgb(148, 221, 229);
  color: gray;
}

.word-list {
  margin-top: 1rem;
  text-align: center;
  font-size: 1.2rem;
}

.list-item {
  list-style: none;
}

.word-list li.found-word {
  text-decoration: line-through;
  color: gray;
}
</style>
