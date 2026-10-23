# Online-Gain
Online Creators

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>EarnHub PNG</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f4f6f9;
      margin: 0;
      color: #202938;
    }
    header {
      background: #172b4d;
      color: white;
      padding: 22px;
      text-align: center;
    }
    main {
      max-width: 650px;
      margin: 24px auto;
      padding: 16px;
    }
    .card {
      background: white;
      padding: 18px;
      margin: 14px 0;
      border-radius: 12px;
      box-shadow: 0 2px 8px #00000012;
    }
    button {
      background: #087f5b;
      color: white;
      border: 0;
      border-radius: 7px;
      padding: 11px 15px;
      cursor: pointer;
    }
    button:disabled {
      background: #888;
      cursor: not-allowed;
    }
    .balance {
      font-size: 28px;
      font-weight: bold;
      color: #087f5b;
    }
    small { color: #667085; }
  </style>
</head>
<body>
  <header>
    <h1>EarnHub PNG</h1>
    <p>Discover tasks. Build skills. Earn rewards.</p>
  </header>

  <main>
    <section class="card">
      <h2>Your demo balance</h2>
      <p class="balance" id="balance">K0.00</p>
      <small>Demo points only — not withdrawable cash.</small>
    </section>

    <h2>Available tasks</h2>
    <div id="tasks"></div>

    <section class="card">
      <h3>Important</h3>
      <p>
        This is a demonstration. Task completion and balances
        are not verified by a server. Do not use this demo to
        collect deposits or promise cash payouts.
      </p>
    </section>
  </main>

  <script>
    const tasks = [
      { id: 1, title: "Try a sample task", reward: 2 },
      { id: 2, title: "Read a learning guide", reward: 3 },
      { id: 3, title: "Complete a practice quiz", reward: 5 }
    ];

    let balance = 0;
    const completed = new Set();

    function renderTasks() {
      const container = document.getElementById("tasks");
      container.innerHTML = "";

      tasks.forEach(task => {
        const card = document.createElement("section");
        card.className = "card";

        const title = document.createElement("h3");
        title.textContent = task.title;

        const reward = document.createElement("p");
        reward.textContent = "Demo reward: K" +
          task.reward.toFixed(2);

        const button = document.createElement("button");
        button.textContent = completed.has(task.id)
          ? "Completed" : "Complete demo task";
        button.disabled = completed.has(task.id);

        button.addEventListener("click", () => {
          if (completed.has(task.id)) return;
          completed.add(task.id);
          balance += task.reward;
          document.getElementById("balance").textContent =
            "K" + balance.toFixed(2);
          renderTasks();
        });

        card.append(title, reward, button);
        container.appendChild(card);
      });
    }

    renderTasks();
  </script>
</body>
</html>
