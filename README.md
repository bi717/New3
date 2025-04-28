<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>美麗媽的廚房</title>
  <style>
    body {
      font-family: 'Noto Sans TC', sans-serif;
      background: #f9f9f6; /* 超清新自然米白底 */
      margin: 0;
      padding: 20px;
      color: #4b4453; /* 柔和紫灰色 */
    }
    h1 {
      text-align: center;
      color: #b388eb; /* 柔和淡紫色 */
      font-family: 'Noto Serif TC', serif; /* 更優雅漂亮的中文字型 */
      font-size: 2.5em;
      margin-bottom: 20px;
    }
    .search-container {
      text-align: center;
      margin-bottom: 20px;
    }
    .search-container input {
      width: 60%;
      padding: 10px;
      border: 2px solid #b388eb;
      border-radius: 20px;
      outline: none;
    }
    .buttons {
      text-align: center;
      margin-bottom: 20px;
    }
    .buttons button {
      background: #e0d4f7; /* 淡紫色 */
      border: none;
      padding: 10px 20px;
      margin: 5px;
      font-size: 16px;
      cursor: pointer;
      border-radius: 50px; /* 圓形按鈕 */
      transition: background 0.3s;
      color: #4b4453;
    }
    .buttons button:hover {
      background: #d1c4e9;
    }
    .recipe {
      background: #ffffff; /* 白色卡片 */
      border: 2px solid #b388eb; /* 淡紫邊框 */
      border-radius: 10px;
      padding: 20px;
      margin: 10px auto;
      max-width: 600px;
      box-shadow: 2px 2px 10px rgba(0,0,0,0.08);
    }
    .recipe h2 {
      margin-top: 0;
      color: #7e57c2; /* 深一點點的紫色 */
    }
    .section-title {
      font-weight: bold;
      margin-top: 10px;
      color: #9575cd;
    }
  </style>
</head>
<body>

<h1>美麗媽的廚房</h1>

<div class="search-container">
  <input type="text" id="searchInput" onkeyup="searchRecipes()" placeholder="搜尋食譜...">
</div>

<div class="buttons">
  <button onclick="filterRecipes('全部')">全部</button>
  <button onclick="filterRecipes('家常菜')">家常菜</button>
  <button onclick="filterRecipes('甜點')">甜點</button>
  <button onclick="filterRecipes('麵包／早餐')">麵包／早餐</button>
  <button onclick="filterRecipes('鹹的')">鹹的</button>
  <button onclick="filterRecipes('肉類')">肉類</button>
  <button onclick="filterRecipes('其他')">其他</button>
</div>

<div id="recipes">
  <div class="recipe" data-category="家常菜 肉類">
    <h2>香煎雞腿排</h2>
    <div class="section-title">食材：</div>
    <ul>
      <li>去骨雞腿排 2片</li>
      <li>鹽 少許</li>
      <li>黑胡椒 少許</li>
      <li>橄欖油 1大匙</li>
    </ul>
    <div class="section-title">步驟：</div>
    <ol>
      <li>雞腿排用鹽和黑胡椒均勻醃10分鐘。</li>
      <li>平底鍋加熱，放入橄欖油。</li>
      <li>雞皮朝下小火煎至金黃，再翻面煎熟即可。</li>
    </ol>
  </div>

  <div class="recipe" data-category="甜點 其他">
    <h2>蜂蜜檸檬果凍</h2>
    <div class="section-title">食材：</div>
    <ul>
      <li>檸檬汁 50ml</li>
      <li>蜂蜜 3大匙</li>
      <li>吉利丁粉 10g</li>
      <li>水 300ml</li>
    </ul>
    <div class="section-title">步驟：</div>
    <ol>
      <li>將水加熱至溫暖，加入吉利丁粉攪拌溶解。</li>
      <li>拌入蜂蜜與檸檬汁。</li>
      <li>倒入模具中，冷藏4小時至凝固。</li>
    </ol>
  </div>
</div>

<script>
function filterRecipes(category) {
  var recipes = document.getElementsByClassName('recipe');
  for (var i = 0; i < recipes.length; i++) {
    if (category === '全部') {
      recipes[i].style.display = 'block';
    } else {
      if (recipes[i].getAttribute('data-category').includes(category)) {
        recipes[i].style.display = 'block';
      } else {
        recipes[i].style.display = 'none';
      }
    }
  }
}

function searchRecipes() {
  var input = document.getElementById('searchInput');
  var filter = input.value.toLowerCase();
  var recipes = document.getElementsByClassName('recipe');
  for (var i = 0; i < recipes.length; i++) {
    var text = recipes[i].textContent || recipes[i].innerText;
    if (text.toLowerCase().includes(filter)) {
      recipes[i].style.display = 'block';
    } else {
      recipes[i].style.display = 'none';
    }
  }
}
</script>

</body>
</html>
