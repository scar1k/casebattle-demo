# casebattle-demo
case 
<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <title>Пример кейс батл</title>
  <style>
    body {
      background: #121212;
      color: #eee;
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 40px;
    }
    .case {
      background: #222;
      border-radius: 12px;
      padding: 20px;
      display: inline-block;
      width: 300px;
    }
    .item {
      margin-top: 20px;
      font-size: 24px;
      font-weight: bold;
      padding: 10px;
      border-radius: 8px;
      min-height: 60px;
      color: #fff;
    }
    .common { background: #777; }
    .rare { background: #1e90ff; }
    .epic { background: #a020f0; }
    .legendary { background: #ff8c00; }
    button {
      margin-top: 20px;
      padding: 10px 30px;
      font-size: 18px;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      background: #4caf50;
      color: white;
      transition: background 0.3s;
    }
    button:hover {
      background: #45a049;
    }
  </style>
</head>
<body>
  <h1>Открытие кейса</h1>
  <div class="case">
    <button id="openBtn">Открыть кейс</button>
    <div id="result" class="item">Нажми кнопку</div>
  </div>

<script>
  const items = [
    { name: 'Пистолет "Глок"', rarity: 'common' },
    { name: 'Дробовик "XM1014"', rarity: 'common' },
    { name: 'Автомат "AK-47"', rarity: 'rare' },
    { name: 'Снайперская винтовка "AWP"', rarity: 'epic' },
    { name: 'Нож "Тотем"', rarity: 'legendary' }
  ];

  // Вероятности для выпадения по редкости (сумма 100)
  const chances = {
    common: 50,
    rare: 30,
    epic: 15,
    legendary: 5
  };

  function weightedRandom(items, chances) {
    const weightedList = [];
    for (const item of items) {
      const count = chances[item.rarity];
      for (let i = 0; i < count; i++) {
        weightedList.push(item);
      }
    }
    return weightedList[Math.floor(Math.random() * weightedList.length)];
  }

  const btn = document.getElementById('openBtn');
  const resultDiv = document.getElementById('result');

  btn.onclick = () => {
    resultDiv.textContent = 'Открытие...';
    setTimeout(() => {
      const item = weightedRandom(items, chances);
      resultDiv.textContent = item.name;
      resultDiv.className = 'item ' + item.rarity;
    }, 1500);
  }
</script>
</body>
</html>

