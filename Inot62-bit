<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Дневник артериального давления</title>

<style>
  :root {
    --bg: #f5f7fb;
    --card-bg: #ffffff;
    --accent: #23406b;
    --accent-soft: #e3ebff;
    --border: #d6deee;
  }

  body {
    margin: 0;
    padding: 0;
    font-family: system-ui, -apple-system, "Segoe UI", sans-serif;
    background: var(--bg);
  }

  .page {
    max-width: 960px;
    margin: 0 auto;
    padding: 16px;
  }

  h1 {
    text-align: center;
    font-size: 24px;
    margin: 8px 0 4px;
    color: var(--accent);
  }

  .subtitle {
    text-align: center;
    font-size: 14px;
    color: #555;
    margin-bottom: 16px;
  }

  /* Карточка ввода */
  .card {
    background: var(--card-bg);
    border-radius: 14px;
    padding: 14px 16px;
    box-shadow: 0 4px 14px rgba(0,0,0,0.06);
    border: 1px solid var(--border);
    margin-bottom: 18px;
  }

  .card-title {
    font-size: 17px;
    font-weight: 600;
    margin-bottom: 10px;
    color: var(--accent);
  }

  .form-grid {
    display: grid;
    grid-template-columns: repeat(6, minmax(0,1fr));
    gap: 8px;
  }

  .form-group {
    display: flex;
    flex-direction: column;
    font-size: 13px;
  }

  .form-group label {
    margin-bottom: 2px;
    color: #333;
  }

  .form-group input,
  .form-group textarea {
    border-radius: 8px;
    border: 1px solid var(--border);
    padding: 6px 8px;
    font-size: 14px;
    font-family: inherit;
  }

  .form-group textarea {
    resize: vertical;
    min-height: 32px;
  }

  .buttons-row {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-top: 10px;
  }

  .btn {
    border: none;
    border-radius: 999px;
    padding: 8px 16px;
    font-size: 14px;
    font-weight: 600;
    cursor: pointer;
    display: inline-flex;
    align-items: center;
    gap: 6px;
  }

  .btn-main {
    background: linear-gradient(135deg, #23406b, #3b6ea5);
    color: #fff;
    box-shadow: 0 4px 10px rgba(0,0,0,0.18);
  }

  .btn-secondary {
    background: #eef2ff;
    color: #1f2a4d;
  }

  .btn-danger {
    background: #ffe8e5;
    color: #b3261e;
  }

  .btn:active {
    transform: translateY(1px);
  }

  /* Таблица */
  .table-wrapper {
    background: var(--card-bg);
    border-radius: 14px;
    box-shadow: 0 4px 14px rgba(0,0,0,0.06);
    border: 1px solid var(--border);
    padding: 10px 10px 14px;
    overflow-x: auto;
  }

  table {
    width: 100%;
    border-collapse: collapse;
    font-size: 14px;
  }

  th, td {
    padding: 6px 8px;
    border-bottom: 1px solid #e1e6f2;
    text-align: left;
    white-space: nowrap;
  }

  th {
    background: var(--accent-soft);
    color: #1f2a4d;
    font-weight: 600;
    position: sticky;
    top: 0;
    z-index: 1;
  }

  tr:last-child td {
    border-bottom: none;
  }

  .cell-note {
    white-space: normal;
    max-width: 280px;
  }

  .cell-actions button {
    border-radius: 999px;
    border: none;
    padding: 4px 10px;
    font-size: 12px;
    cursor: pointer;
    background: #ffecec;
    color: #b00020;
  }

  .stats {
    margin-top: 10px;
    font-size: 14px;
    color: #333;
  }

  .stats span {
    font-weight: 600;
    color: #1f2a4d;
  }

  /* Адаптивность */
  @media (max-width: 720px) {
    .form-grid {
      grid-template-columns: repeat(2, minmax(0,1fr));
    }
  }

  @media (max-width: 480px) {
    .page {
      padding: 10px;
    }
    h1 {
      font-size: 20px;
    }
    .form-grid {
      grid-template-columns: minmax(0,1fr);
    }
  }

  /* Печать в PDF — только таблица и заголовок, одна страница A4 */
  @media print {
    body {
      background: #ffffff;
    }
    .card,
    .buttons-row,
    .subtitle {
      display: none !important;
    }
    .page {
      max-width: 100%;
      padding: 0;
      margin: 0;
    }
    h1 {
      margin: 0 0 6px 0;
      font-size: 18px;
      text-align: left;
    }
    .table-wrapper {
      box-shadow: none;
      border-radius: 0;
      border: none;
      padding: 0;
    }
    table {
      font-size: 11px;
    }
    th, td {
      padding: 3px 4px;
    }
    .stats {
      font-size: 11px;
      margin-top: 4px;
    }
    @page {
      size: A4;
      margin: 12mm;
    }
  }
</style>
</head>
<body>
<div class="page">
  <h1>Дневник артериального давления</h1>
  <div class="subtitle">
    Записи хранятся в памяти браузера этого устройства.  
    Можно сохранить в PDF одним нажатием.
  </div>

  <!-- Форма ввода -->
  <div class="card">
    <div class="card-title">Новая запись</div>
    <div class="form-grid">
      <div class="form-group">
        <label for="date">Дата</label>
        <input type="date" id="date">
      </div>
      <div class="form-group">
        <label for="time">Время</label>
        <input type="time" id="time">
      </div>
      <div class="form-group">
        <label for="sys">Систолическое (верхнее), мм рт. ст.</label>
        <input type="number" id="sys" inputmode="numeric" placeholder="120">
      </div>
      <div class="form-group">
        <label for="dia">Диастолическое (нижнее), мм рт. ст.</label>
        <input type="number" id="dia" inputmode="numeric" placeholder="80">
      </div>
      <div class="form-group">
        <label for="pul">Пульс, уд/мин</label>
        <input type="number" id="pul" inputmode="numeric" placeholder="70">
      </div>
      <div class="form-group">
        <label for="note">Примечание</label>
        <textarea id="note" placeholder="После прогулки, утром натощак и т.д."></textarea>
      </div>
    </div>

    <div class="buttons-row">
      <button class="btn btn-main" onclick="addEntry()">
        ➕ Добавить запись
      </button>
      <button class="btn btn-secondary" onclick="printDiary()">
        📄 Скачать PDF
      </button>
      <button class="btn btn-danger" onclick="clearAll()">
        🗑 Очистить всё
      </button>
    </div>
  </div>

  <!-- Таблица -->
  <div class="table-wrapper">
    <table id="diary-table">
      <thead>
        <tr>
          <th>Дата</th>
          <th>Время</th>
          <th>Давление</th>
          <th>Пульс</th>
          <th>Примечание</th>
          <th>Действия</th>
        </tr>
      </thead>
      <tbody id="diary-body">
      </tbody>
    </table>
    <div class="stats" id="stats"></div>
  </div>
</div>

<script>
  const STORAGE_KEY = "toni_bp_diary_v1";

  function pad2(n) {
    return n.toString().padStart(2, "0");
  }

  function setDefaultDateTime() {
    const now = new Date();
    document.getElementById("date").value =
      now.toISOString().slice(0, 10);

    document.getElementById("time").value =
      pad2(now.getHours()) + ":" + pad2(now.getMinutes());
  }

  function loadData() {
    try {
      const raw = localStorage.getItem(STORAGE_KEY);
      if (!raw) return [];
      return JSON.parse(raw);
    } catch (e) {
      console.error(e);
      return [];
    }
  }

  function saveData(list) {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(list));
  }

  function renderTable() {
    const body = document.getElementById("diary-body");
    const stats = document.getElementById("stats");
    const list = loadData();

    // сортируем по дате/времени: старые сверху
    list.sort((a, b) => (a.dt > b.dt ? 1 : -1));

    body.innerHTML = "";

    let sumSys = 0, sumDia = 0, sumPul = 0, count = 0;

    list.forEach((row, index) => {
      const tr = document.createElement("tr");

      const [dateStr, timeStr] = row.dt.split("T");

      const tdDate = document.createElement("td");
      tdDate.textContent = dateStr.split("-").reverse().join(".");

      const tdTime = document.createElement("td");
      tdTime.textContent = timeStr.slice(0,5);

      const tdPress = document.createElement("td");
      tdPress.textContent = row.sys + " / " + row.dia;

      const tdPul = document.createElement("td");
      tdPul.textContent = row.pul;

      const tdNote = document.createElement("td");
      tdNote.textContent = row.note || "";
      tdNote.className = "cell-note";

      const tdActions = document.createElement("td");
      tdActions.className = "cell-actions";
      const btnDel = document.createElement("button");
      btnDel.textContent = "Удалить";
      btnDel.onclick = () => deleteEntry(index);
      tdActions.appendChild(btnDel);

      tr.appendChild(tdDate);
      tr.appendChild(tdTime);
      tr.appendChild(tdPress);
      tr.appendChild(tdPul);
      tr.appendChild(tdNote);
      tr.appendChild(tdActions);

      body.appendChild(tr);

      sumSys += Number(row.sys);
      sumDia += Number(row.dia);
      sumPul += Number(row.pul);
      count++;
    });

    if (count > 0) {
      stats.innerHTML =
        `Среднее за выбранные записи: 
         <span>${Math.round(sumSys / count)} / ${Math.round(sumDia / count)} мм</span>, 
         пульс <span>${Math.round(sumPul / count)} уд/мин</span>. 
         Всего записей: <span>${count}</span>.`;
    } else {
      stats.textContent = "Пока нет записей. Добавьте первую.";
    }
  }

  function addEntry() {
    const date = document.getElementById("date").value;
    const time = document.getElementById("time").value;
    const sys = document.getElementById("sys").value.trim();
    const dia = document.getElementById("dia").value.trim();
    const pul = document.getElementById("pul").value.trim();
    const note = document.getElementById("note").value.trim();

    if (!date || !time || !sys || !dia || !pul) {
      alert("Заполните дату, время, давление и пульс.");
      return;
    }

    const list = loadData();
    list.push({
      dt: date + "T" + time,
      sys: Number(sys),
      dia: Number(dia),
      pul: Number(pul),
      note: note
    });
    saveData(list);

    // очищаем только поля давления/пульса/заметки
    document.getElementById("sys").value = "";
    document.getElementById("dia").value = "";
    document.getElementById("pul").value = "";
    document.getElementById("note").value = "";

    renderTable();
  }

  function deleteEntry(index) {
    if (!confirm("Удалить эту запись?")) return;
    const list = loadData();
    list.splice(index, 1);
    saveData(list);
    renderTable();
  }

  function clearAll() {
    if (!confirm("Удалить все записи дневника?")) return;
    localStorage.removeItem(STORAGE_KEY);
    renderTable();
  }

  function printDiary() {
    window.print();
  }

  // инициализация
  setDefaultDateTime();
  renderTable();
</script>
</body>
</html>
