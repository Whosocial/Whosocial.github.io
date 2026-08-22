---
layout: page
title: 数独游戏
permalink: /sudoku/
---

<style>
  /* 基础色彩定义，还原参考图配色 */
  :root {
    --text-color: #344861;        /* 默认数字颜色（深蓝灰） */
    --user-text-color: #0052cc;   /* 用户填写的数字颜色（亮蓝） */
    --bg-color: #ffffff;
    --grid-line-thin: #e1e4e8;    /* 细边框 */
    --grid-line-thick: #344861;   /* 粗边框 */
    
    --highlight-cell: #bbdefb;    /* 选中的当前格子（稍深的浅蓝） */
    --highlight-related: #e2ebf3; /* 关联的高亮同行/列/宫（浅蓝灰） */
    --highlight-same-num: #cbdbed;/* 相同数字高亮 */
    
    --error-bg: #f7d2d2;          /* 错误格子背景（浅红） */
    --error-text: #e53e3e;        /* 错误文字颜色 */
    
    --btn-bg: #f0f3f6;            /* 键盘按钮背景 */
    --btn-primary: #5c7cbe;       /* 新游戏按钮颜色 */
  }

  /* 整体布局：宽屏下左右分栏，窄屏下上下堆叠 */
  .sudoku-wrapper {
    display: flex;
    flex-wrap: wrap;
    gap: 30px;
    justify-content: center;
    align-items: flex-start;
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    margin-bottom: 40px;
    margin-top: 20px;
  }

  /* 左侧：棋盘区 */
  .board-section {
    flex: 0 0 auto;
  }

  /* 9x9 棋盘网格 */
  .grid {
    display: grid;
    grid-template-columns: repeat(9, clamp(35px, 9vw, 55px));
    grid-template-rows: repeat(9, clamp(35px, 9vw, 55px));
    border: 3px solid var(--grid-line-thick);
    background-color: var(--bg-color);
  }

  /* 单元格基础样式 */
  .cell {
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: clamp(1.2rem, 4vw, 1.8rem);
    color: var(--text-color);
    border-right: 1px solid var(--grid-line-thin);
    border-bottom: 1px solid var(--grid-line-thin);
    background-color: var(--bg-color);
    cursor: pointer;
    user-select: none;
    transition: background-color 0.1s;
  }

  /* 修正用户输入的字体颜色 */
  .cell.user-input {
    color: var(--user-text-color);
    font-weight: 300;
  }

  /* 3x3 宫格的粗边框 (还原参考图) */
  .cell:nth-child(3n) { border-right: 2px solid var(--grid-line-thick); }
  .cell:nth-child(9n) { border-right: none; }
  .cell:nth-child(n+19):nth-child(-n+27),
  .cell:nth-child(n+46):nth-child(-n+54) { border-bottom: 2px solid var(--grid-line-thick); }
  .cell:nth-child(n+73):nth-child(-n+81) { border-bottom: none; }

  /* 交互状态色彩 */
  .cell.highlight-related { background-color: var(--highlight-related); }
  .cell.highlight-same { background-color: var(--highlight-same-num); }
  .cell.selected { background-color: var(--highlight-cell); }
  .cell.error { background-color: var(--error-bg); color: var(--error-text); }

  /* 右侧：控制与键盘区 */
  .control-section {
    flex: 0 0 auto;
    width: clamp(280px, 100%, 350px);
    display: flex;
    flex-direction: column;
    gap: 15px;
  }

  /* 顶部状态栏 (时间、错误数) */
  .status-bar {
    display: flex;
    justify-content: space-between;
    color: #6a737d;
    font-size: 0.9rem;
    margin-bottom: 10px;
    font-weight: 500;
  }

  /* 顶部功能小按钮区 (撤销、擦除等，仅做占位演示样式) */
  .tools-row {
    display: flex;
    justify-content: space-between;
    margin-bottom: 10px;
  }
  .tool-btn {
    width: 45px;
    height: 45px;
    border-radius: 50%;
    background: var(--btn-bg);
    border: none;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    color: var(--user-text-color);
    font-size: 1.2rem;
  }
  .tool-btn:hover { background: #e2ebf3; }

  /* 3x3 数字键盘区 */
  .numpad {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 10px;
  }
  .numpad-btn {
    background: var(--btn-bg);
    border: none;
    border-radius: 6px;
    aspect-ratio: 1.2;
    font-size: 2rem;
    color: var(--user-text-color);
    cursor: pointer;
    transition: background 0.1s;
    font-weight: 300;
  }
  .numpad-btn:hover { background: #e2ebf3; }

  /* 新游戏按钮 */
  .new-game-btn {
    background: var(--btn-primary);
    color: white;
    border: none;
    padding: 16px;
    border-radius: 6px;
    font-size: 1.1rem;
    font-weight: 500;
    cursor: pointer;
    margin-top: 10px;
    transition: background 0.2s;
  }
  .new-game-btn:hover { background: #4a66a0; }

</style>

<div class="sudoku-wrapper">
  
  <!-- 左侧棋盘 -->
  <div class="board-section">
    <div class="grid" id="sudoku-grid">
      <!-- JS 动态生成 81 个单元格 -->
    </div>
  </div>

  <!-- 右侧控制区 -->
  <div class="control-section">
    
    <div class="status-bar">
      <div>错误<br><span id="error-count" style="font-size: 1.2rem; color: var(--text-color);">0</span>/3</div>
      <div style="text-align: right;">时间<br><span id="timer" style="font-size: 1.2rem; color: var(--text-color);">00:00</span></div>
    </div>

    <!-- 工具栏 (实现擦除功能) -->
    <div class="tools-row">
      <button class="tool-btn" title="撤销 (暂未实现)">↺</button>
      <button class="tool-btn" onclick="inputNumber(0)" title="擦除">⌫</button>
      <button class="tool-btn" title="笔记 (暂未实现)">✎</button>
      <button class="tool-btn" title="提示 (暂未实现)">💡</button>
    </div>

    <!-- 3x3 数字键盘 -->
    <div class="numpad">
      <button class="numpad-btn" onclick="inputNumber(1)">1</button>
      <button class="numpad-btn" onclick="inputNumber(2)">2</button>
      <button class="numpad-btn" onclick="inputNumber(3)">3</button>
      <button class="numpad-btn" onclick="inputNumber(4)">4</button>
      <button class="numpad-btn" onclick="inputNumber(5)">5</button>
      <button class="numpad-btn" onclick="inputNumber(6)">6</button>
      <button class="numpad-btn" onclick="inputNumber(7)">7</button>
      <button class="numpad-btn" onclick="inputNumber(8)">8</button>
      <button class="numpad-btn" onclick="inputNumber(9)">9</button>
    </div>

    <button class="new-game-btn" onclick="initGame()">新游戏</button>

  </div>
</div>

<script>
  let solution = [];
  let puzzle = [];
  let userGrid = [];
  let selectedCell = null;
  let errorCount = 0;
  
  // 计时器变量
  let timerInterval;
  let secondsElapsed = 0;

  function initGame() {
    errorCount = 0;
    document.getElementById('error-count').innerText = errorCount;
    resetTimer();
    
    // 默认生成中等难度 (大约挖空45个)
    generateSolution();
    createPuzzle(45);
    renderGrid();
    startTimer();
  }

  // 1. 生成终盘 (回溯算法)
  function generateSolution() {
    solution = Array(9).fill().map(() => Array(9).fill(0));
    fillBoard(0, 0);
  }

  function fillBoard(row, col) {
    if (row === 9) return true;
    let nextRow = col === 8 ? row + 1 : row;
    let nextCol = col === 8 ? 0 : col + 1;

    let nums = [1, 2, 3, 4, 5, 6, 7, 8, 9];
    nums.sort(() => Math.random() - 0.5); 

    for (let num of nums) {
      if (isValid(solution, row, col, num)) {
        solution[row][col] = num;
        if (fillBoard(nextRow, nextCol)) return true;
        solution[row][col] = 0; 
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

  // 3. 渲染网格
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
          // 初始数字也允许点击以触发相同数字高亮
          cell.addEventListener('click', () => selectCell(cell, r, c, puzzle[r][c]));
        } else {
          cell.innerText = userGrid[r][c] === 0 ? '' : userGrid[r][c];
          if(userGrid[r][c] !== 0) cell.classList.add('user-input');
          cell.addEventListener('click', () => selectCell(cell, r, c, userGrid[r][c]));
        }
        gridEl.appendChild(cell);
      }
    }
  }

  // 4. 选中逻辑与三级高亮还原
  function selectCell(cell, r, c, numVal) {
    document.querySelectorAll('.cell').forEach(el => {
      el.classList.remove('selected', 'highlight-related', 'highlight-same');
      
      let el_r = el.dataset.r;
      let el_c = el.dataset.c;
      
      // 高亮关联区域 (同行、同列、同宫格)
      if (el_r == r || el_c == c || 
         (Math.floor(el_r/3) == Math.floor(r/3) && Math.floor(el_c/3) == Math.floor(c/3))) {
        el.classList.add('highlight-related');
      }
      
      // 高亮盘面上所有相同的数字
      if (numVal !== 0 && numVal !== undefined && el.innerText == numVal) {
        el.classList.add('highlight-same');
      }
    });

    cell.classList.add('selected');
    
    // 只有空白格或用户填写的格子允许被记录为待输入状态
    if (puzzle[r][c] === 0) {
      selectedCell = { el: cell, r, c };
    } else {
      selectedCell = null; // 选中系统固定数字时，不允许输入替换
    }
  }

  // 5. 数字输入与校验
  function inputNumber(num) {
    if (!selectedCell) return;
    const { el, r, c } = selectedCell;
    
    // 如果该格子已经被判断为正确，则不允许再次修改
    if (userGrid[r][c] === solution[r][c] && userGrid[r][c] !== 0) return;

    if (num === 0) {
      // 擦除操作
      userGrid[r][c] = 0;
      el.innerText = '';
      el.classList.remove('error', 'user-input');
      selectCell(el, r, c, 0); // 重新触发高亮逻辑
    } else {
      userGrid[r][c] = num;
      el.innerText = num;
      el.classList.add('user-input');
      
      if (num !== solution[r][c]) {
        el.classList.add('error');
        errorCount++;
        document.getElementById('error-count').innerText = errorCount;
        if(errorCount >= 3) {
           setTimeout(() => { alert("错误达到3次，游戏结束！"); initGame(); }, 100);
        }
      } else {
        el.classList.remove('error');
        selectCell(el, r, c, num); // 填对后刷新相同数字高亮
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

  // 计时器逻辑
  function formatTime(seconds) {
    let m = Math.floor(seconds / 60).toString().padStart(2, '0');
    let s = (seconds % 60).toString().padStart(2, '0');
    return `${m}:${s}`;
  }
  function updateTimerDisplay() {
    document.getElementById('timer').innerText = formatTime(secondsElapsed);
  }
  function startTimer() {
    timerInterval = setInterval(() => {
      secondsElapsed++;
      updateTimerDisplay();
    }, 1000);
  }
  function resetTimer() {
    clearInterval(timerInterval);
    secondsElapsed = 0;
    updateTimerDisplay();
  }

  function checkWin() {
    for (let r = 0; r < 9; r++) {
      for (let c = 0; c < 9; c++) {
        if (userGrid[r][c] !== solution[r][c]) return;
      }
    }
    clearInterval(timerInterval);
    setTimeout(() => alert(`🎉 恭喜！用时 ${formatTime(secondsElapsed)} 解开了这局数独！`), 200);
  }

  window.onload = initGame;
</script>
