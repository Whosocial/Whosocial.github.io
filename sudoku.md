---
layout: page
title: 数独游戏
permalink: /sudoku/
---

<style>
  :root {
    --primary-color: #319795;
    --error-color: #e53e3e;
    --bg-color: #fafbfc;
    --grid-border: #2d3748;
    --cell-border: #cbd5e0;
  }

  .sudoku-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    margin-bottom: 3rem;
  }

  .sudoku-header {
    text-align: center;
    margin-bottom: 20px;
    color: #4a5568;
  }

  .controls {
    display: flex;
    gap: 15px;
    margin-bottom: 20px;
  }

  .btn {
    background-color: var(--primary-color);
    color: white;
    border: none;
    padding: 10px 20px;
    border-radius: 6px;
    font-size: 1rem;
    cursor: pointer;
    font-weight: 600;
    transition: background-color 0.2s;
  }
  .btn:hover { background-color: #287a78; }
  .btn-outline { background-color: transparent; color: var(--primary-color); border: 2px solid var(--primary-color); }
  .btn-outline:hover { background-color: #e6fffa; }

  /* 9x9 网格布局 */
  .grid {
    display: grid;
    grid-template-columns: repeat(9, 40px);
    grid-template-rows: repeat(9, 40px);
    border: 3px solid var(--grid-border);
    background-color: var(--bg-color);
    box-shadow: 0 10px 25px rgba(0,0,0,0.1);
  }

  @media (min-width: 600px) {
    .grid {
      grid-template-columns: repeat(9, 50px);
      grid-template-rows: repeat(9, 50px);
    }
  }

  /* 单元格样式 */
  .cell {
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1.2rem;
    font-weight: bold;
    color: #2d3748;
    border: 1px solid var(--cell-border);
    background-color: white;
    cursor: pointer;
    user-select: none;
    transition: background-color 0.1s;
  }

  /* 3x3 宫格的粗边框 */
  .cell:nth-child(3n) { border-right: 2px solid var(--grid-border); }
  .cell:nth-child(9n) { border-right: none; }
  .cell:nth-child(n+19):nth-child(-n+27),
  .cell:nth-child(n+46):nth-child(-n+54) { border-bottom: 2px solid var(--grid-border); }

  /* 交互状态 */
  .cell.fixed { background-color: #edf2f7; color: #718096; cursor: not-allowed; }
  .cell.selected { background-color: #b2f5ea; }
  .cell.highlight { background-color: #e6fffa; }
  .cell.error { color: var(--error-color); background-color: #fff5f5; }

  /* 虚拟键盘 (方便移动端操作) */
  .numpad {
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    gap: 10px;
    margin-top: 25px;
    max-width: 300px;
  }
  .numpad-btn {
    background: white;
    border: 1px solid var(--cell-border);
    border-radius: 6px;
    padding: 15px 0;
    font-size: 1.2rem;
    font-weight: bold;
    cursor: pointer;
    box-shadow: 0 2px 4px rgba(0,0,0,0.05);
  }
  .numpad-btn:hover { background: #edf2f7; }
</style>

<div class="sudoku-container">
  <div class="sudoku-header">
    <p>在这个 9×9 的微观世界里，寻找唯一的逻辑解。</p>
  </div>

  <div class="controls">
    <button class="btn" onclick="initGame(40)">新游戏 (简单)</button>
    <button class="btn btn-outline" onclick="initGame(50)">新游戏 (困难)</button>
  </div>

  <div class="grid" id="sudoku-grid">
    <!-- JS 将在这里动态生成 81 个单元格 -->
  </div>

  <!-- 移动端友好的数字小键盘 -->
  <div class="numpad" id="numpad">
    <button class="numpad-btn" onclick="inputNumber(1)">1</button>
    <button class="numpad-btn" onclick="inputNumber(2)">2</button>
    <button class="numpad-btn" onclick="inputNumber(3)">3</button>
    <button class="numpad-btn" onclick="inputNumber(4)">4</button>
    <button class="numpad-btn" onclick="inputNumber(5)">5</button>
    <button class="numpad-btn" onclick="inputNumber(6)">6</button>
    <button class="numpad-btn" onclick="inputNumber(7)">7</button>
    <button class="numpad-btn" onclick="inputNumber(8)">8</button>
    <button class="numpad-btn" onclick="inputNumber(9)">9</button>
    <button class="numpad-btn" onclick="inputNumber(0)" style="color: #e53e3e;">清空</button>
  </div>
</div>

<script>
  let solution = [];
  let puzzle = [];
  let userGrid = [];
  let selectedCell = null;

  // 初始化游戏
  function initGame(holes) {
    generateSolution();
    createPuzzle(holes);
    renderGrid();
  }

  // 1. 生成完整的合法数独终盘 (回溯算法)
  function generateSolution() {
    solution = Array(9).fill().map(() => Array(9).fill(0));
    fillBoard(0, 0);
  }

  function fillBoard(row, col) {
    if (row === 9) return true;
    let nextRow = col === 8 ? row + 1 : row;
    let nextCol = col === 8 ? 0 : col + 1;

    let nums = [1, 2, 3, 4, 5, 6, 7, 8, 9];
    nums.sort(() => Math.random() - 0.5); // 打乱顺序保证随机性

    for (let num of nums) {
      if (isValid(solution, row, col, num)) {
        solution[row][col] = num;
        if (fillBoard(nextRow, nextCol)) return true;
        solution[row][col] = 0; // 回溯
      }
    }
    return false;
  }

  function isValid(board, row, col, num) {
    for (let i = 0; i < 9; i++) {
      if (board[row][i] === num) return false;
      if (board[i][col] === num) return false;
      let r = 3 * Math.floor(row / 3) + Math.floor(i / 3);
      let c = 3 * Math.floor(col / 3) + i % 3;
      if (board[r][c] === num) return false;
    }
    return true;
  }

  // 2. 挖空生成题目
  function createPuzzle(holes) {
    puzzle = solution.map(row => [...row]);
    userGrid = solution.map(row => [...row]);
    
    let count = holes;
    while (count > 0) {
      let r = Math.floor(Math.random() * 9);
      let c = Math.floor(Math.random() * 9);
      if (puzzle[r][c] !== 0) {
        puzzle[r][c] = 0;
        userGrid[r][c] = 0;
        count--;
      }
    }
  }

  // 3. 渲染 DOM
  function renderGrid() {
    const gridEl = document.getElementById('sudoku-grid');
    gridEl.innerHTML = '';
    selectedCell = null;

    for (let r = 0; r < 9; r++) {
      for (let c = 0; c < 9; c++) {
        const cell = document.createElement('div');
        cell.classList.add('cell');
        cell.dataset.r = r;
        cell.dataset.c = c;

        if (puzzle[r][c] !== 0) {
          cell.innerText = puzzle[r][c];
          cell.classList.add('fixed');
        } else {
          cell.innerText = userGrid[r][c] === 0 ? '' : userGrid[r][c];
          cell.addEventListener('click', () => selectCell(cell, r, c));
        }
        gridEl.appendChild(cell);
      }
    }
  }

  // 4. 交互：选中单元格
  function selectCell(cell, r, c) {
    if (puzzle[r][c] !== 0) return; // 初始数字不可点
    
    document.querySelectorAll('.cell').forEach(el => {
      el.classList.remove('selected', 'highlight');
      // 高亮同行同列同宫格
      let el_r = el.dataset.r;
      let el_c = el.dataset.c;
      if (el_r == r || el_c == c || 
         (Math.floor(el_r/3) == Math.floor(r/3) && Math.floor(el_c/3) == Math.floor(c/3))) {
        el.classList.add('highlight');
      }
    });

    cell.classList.add('selected');
    selectedCell = { el: cell, r, c };
  }

  // 5. 交互：输入数字 (支持屏幕键盘和实体键盘)
  function inputNumber(num) {
    if (!selectedCell) return;
    const { el, r, c } = selectedCell;
    
    if (num === 0) {
      userGrid[r][c] = 0;
      el.innerText = '';
      el.classList.remove('error');
    } else {
      userGrid[r][c] = num;
      el.innerText = num;
      // 简单校验：与终盘比对 (红字提示错误)
      if (num !== solution[r][c]) {
        el.classList.add('error');
      } else {
        el.classList.remove('error');
        checkWin();
      }
    }
  }

  // 监听实体键盘
  document.addEventListener('keydown', (e) => {
    if (e.key >= '1' && e.key <= '9') {
      inputNumber(parseInt(e.key));
    } else if (e.key === 'Backspace' || e.key === 'Delete') {
      inputNumber(0);
    }
  });

  // 检查胜利条件
  function checkWin() {
    for (let r = 0; r < 9; r++) {
      for (let c = 0; c < 9; c++) {
        if (userGrid[r][c] !== solution[r][c]) return;
      }
    }
    setTimeout(() => alert("🎉 恭喜！你解开了这局数独！"), 200);
  }

  // 页面加载完毕自动初始化一局简单游戏
  window.onload = () => initGame(40);
</script>
