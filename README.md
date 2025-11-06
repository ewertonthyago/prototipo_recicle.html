# prototipo_recicle.html

<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Protótipo - Projeto RECicle</title>
  
  <!-- Tailwind CSS via CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  
  <!-- Lucide Icons via CDN -->
  <script src="https://unpkg.com/lucide@latest"></script>
  
  <!-- Fontes do Google (Inter) -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap" rel="stylesheet">
  
  <style>
    /* Estilo base para a fonte e cores CSS */
    body {
      font-family: 'Inter', sans-serif;
    }
    :root {
      --primary-blue: rgb(27, 101, 155);
      --light-blue: rgb(80, 169, 219);
      --primary-green: rgb(86, 171, 71);
      --light-green: rgb(123, 201, 108);
      --primary-orange: rgb(240, 150, 48);
      --dark-text: rgb(25, 25, 25);
      --gray-text: rgb(75, 75, 75);
    }
    
    /* Classes de cor personalizadas do Tailwind para CardMetric */
    .border-\[var\(--primary-blue\)\] { border-color: var(--primary-blue); }
    .border-\[var\(--primary-orange\)\] { border-color: var(--primary-orange); }
    .border-\[var\(--primary-green\)\] { border-color: var(--primary-green); }
    
    .bg-\[var\(--primary-blue\)\] { background-color: var(--primary-blue); }
    .bg-\[var\(--light-blue\)\] { background-color: var(--light-blue); }
    .bg-\[var\(--primary-green\)\] { background-color: var(--primary-green); }
    .bg-\[var\(--light-green\)\] { background-color: var(--light-green); }
    .bg-\[var\(--primary-orange\)\] { background-color: var(--primary-orange); }
    
    .text-\[var\(--primary-blue\)\] { color: var(--primary-blue); }
    .text-\[var\(--light-blue\)\] { color: var(--light-blue); }
    .text-\[var\(--primary-green\)\] { color: var(--primary-green); }
    .text-\[var\(--light-green\)\] { color: var(--light-green); }
    .text-\[var\(--primary-orange\)\] { color: var(--primary-orange); }
    .text-\[var\(--dark-text\)\] { color: var(--dark-text); }
    .text-\[var\(--gray-text\)\] { color: var(--gray-text); }

    .hover\:bg-\[var\(--light-blue\)\]:hover { background-color: var(--light-blue); }

    .border-\[var\(--light-blue\)\] { border-color: var(--light-blue); }
    .border-\[var\(--primary-orange\)\] { border-color: var(--primary-orange); }
    .border-\[var\(--primary-blue\)\] { border-color: var(--primary-blue); }

    .bg-\[var\(--primary-orange\)\]\/\[0\.05\] { background-color: rgba(240, 150, 48, 0.05); }
    .bg-\[var\(--primary-orange\)\]\/\[0\.1\] { background-color: rgba(240, 150, 48, 0.1); }
    .bg-\[var\(--light-green\)\]\/\[0\.2\] { background-color: rgba(123, 201, 108, 0.2); }
    .bg-\[var\(--primary-green\)\]\/\[0\.2\] { background-color: rgba(86, 171, 71, 0.2); }
    .bg-\[var\(--primary-blue\)\]\/\[0\.2\] { background-color: rgba(27, 101, 155, 0.2); }

    .hover\:bg-\[var\(--primary-orange\)\]\/90:hover { background-color: rgba(240, 150, 48, 0.9); }
    
    /* Ajuste para ícones de métrica */
    .bg-blue-100 { background-color: #EBF8FF; }
    .text-blue-600 { color: #3182CE; }
    .bg-orange-100 { background-color: #FFF5EB; }
    .text-orange-600 { color: #DD6B20; }
    .bg-green-100 { background-color: #F0FFF4; }
    .text-green-600 { color: #38A169; }

  </style>
</head>

<body class="min-h-screen bg-gray-50 flex flex-col sm:flex-row">

  <!-- Sidebar de Navegação -->
  <nav class="sm:w-64 bg-white shadow-xl p-4 sm:p-6 flex flex-row sm:flex-col justify-around sm:justify-start overflow-x-auto border-b sm:border-b-0 sticky top-0 z-10">
    <div class="hidden sm:block mb-8">
      <div class="flex items-center space-x-2 text-2xl font-black text-[var(--primary-blue)]">
        <i data-lucide="recycle" class="w-8 h-8 text-[var(--primary-green)]"></i>
        <span class="hidden lg:inline">RECicle</span>
      </div>
      <p class="text-xs text-[var(--gray-text)]">Ganhe Pontos. Troque por Diversão!</p>
    </div>

    <!-- Links de Navegação -->
    <div id="nav-container" class="flex sm:flex-col space-x-2 sm:space-x-0 sm:space-y-3">
      <!-- NavItems serão injetados aqui pelo JS -->
    </div>
  </nav>

  <!-- Conteúdo Principal -->
  <main id="main-content" class="flex-1 w-full overflow-y-auto pb-10">
    <!-- O conteúdo da página ativa será injetado aqui -->
  </main>

  <script>
    // --- CONSTANTES E DADOS SIMULADOS ---
    const PONTOS_BASE = {
      'Metal': 100,
      'Plástico': 80,
      'Papel': 60,
      'Vidro': 50,
      'Eletrônico': 200,
    };
    const initialUserId = 'user-prototipo-html';

    const initialHistory = [
      { id: 1, type: 'Plástico', weight: 1.5, points: 120, date: '2025-10-25', event: 'Normal' },
      { id: 2, type: 'Metal', weight: 0.8, points: 80, date: '2025-10-24', event: 'Normal' },
      { id: 3, type: 'Vidro', weight: 2.0, points: 100, date: '2025-10-23', event: 'São João (+50%)' },
    ];

    const mockMissions = [
      { id: 1, title: 'Meta Semanal de Plástico', target: 5, current: 3.2, unit: 'Kg', points: 500, completed: false, material: 'Plástico' },
      { id: 2, title: '3 Descartes de Vidro', target: 3, current: 2, unit: 'vezes', points: 300, completed: false, material: 'Vidro' },
      { id: 3, title: 'Campeão da Zona Norte', target: 1, current: 1, unit: 'lugar', points: 1500, completed: true, material: 'Ranking' },
    ];

    const mockRanking = [
      { rank: 1, userId: 'user-a82f', name: 'Ambientalista', points: 15400, weeks: 10 },
      { rank: 2, userId: 'user-b1d4', name: 'Reciclador Top', points: 15300, weeks: 8 },
      { rank: 3, userId: initialUserId, name: 'Você', points: 15200, weeks: 7 },
      { rank: 4, userId: 'user-c9e0', name: 'Recife Verde', points: 14800, weeks: 1 },
    ];

    // --- ESTADO DA APLICAÇÃO (Simulação do useState) ---
    let state = {
      points: 15200,
      rankingPosition: 3,
      selectedTab: 'dashboard',
      history: [...initialHistory],
      userId: initialUserId,
      // Estado específico do Deposit
      deposit: {
        material: '',
        weight: 0.5,
        eventBonus: 1.0,
        status: 'pronto', // pronto, escaneando, depositando, concluido, erro
      }
    };
    
    // --- PONTOS DE MONTAGEM DO DOM ---
    const navContainer = document.getElementById('nav-container');
    const mainContent = document.getElementById('main-content');

    // --- LÓGICA DE NAVEGAÇÃO ---
    const navTabs = [
      { id: 'dashboard', label: 'Painel de Bordo', icon: 'bar-chart' },
      { id: 'deposit', label: 'Descartar Lixo', icon: 'scan' },
      { id: 'missions', label: 'Missões & Indique', icon: 'award' },
      { id: 'ranking', label: 'Ranking', icon: 'trophy' },
      { id: 'settings', label: 'Resgate', icon: 'settings' },
    ];

    function setSelectedTab(tabId) {
      state.selectedTab = tabId;
      renderApp();
    }

    // --- FUNÇÕES DE RENDERIZAÇÃO (Simulação de Componentes) ---
    
    function renderNav() {
      navContainer.innerHTML = navTabs.map(tab => `
        <button
          onclick="setSelectedTab('${tab.id}')"
          class="flex items-center justify-center sm:justify-start p-3 transition-all duration-200 rounded-lg w-full ${
            state.selectedTab === tab.id
              ? 'bg-[var(--primary-blue)] text-white shadow-lg'
              : 'text-[var(--gray-text)] hover:bg-[var(--light-blue)] hover:text-white'
          }"
        >
          <i data-lucide="${tab.icon}" class="w-6 h-6 sm:mr-3"></i>
          <span class="hidden sm:inline font-semibold">${tab.label}</span>
        </button>
      `).join('');
    }

    function renderCardMetric(icon, title, value, unit, colorClass) {
        // Mapas para traduzir as cores CSS var para classes reais do Tailwind
        const colorMap = {
            'border-[var(--primary-blue)]': { border: 'border-blue-600', bg: 'bg-blue-100', text: 'text-blue-600' },
            'border-[var(--primary-orange)]': { border: 'border-orange-600', bg: 'bg-orange-100', text: 'text-orange-600' },
            'border-[var(--primary-green)]': { border: 'border-green-600', bg: 'bg-green-100', text: 'text-green-600' },
        };
        const colors = colorMap[colorClass] || { border: 'border-gray-600', bg: 'bg-gray-100', text: 'text-gray-600' };

        return `
        <div class="flex items-center p-4 bg-white rounded-xl shadow-lg border-b-4 ${colors.border}">
            <div class="p-3 rounded-full ${colors.bg} ${colors.text} mr-4">
                <i data-lucide="${icon}" class="w-6 h-6"></i>
            </div>
            <div>
                <p class="text-sm font-medium text-gray-500">${title}</p>
                <p class="text-2xl font-bold text-gray-800">
                    ${value} <span class="text-base font-normal text-gray-500">${unit}</span>
                </p>
            </div>
        </div>
        `;
    }

    function renderDashboard() {
      const { points, rankingPosition, userId, history } = state;
      const currentMission = mockMissions.find(m => !m.completed);
      const userRank = mockRanking.find(r => r.userId === userId);
      const weeksTop10 = userRank ? userRank.weeks : 0;
      const prizeWeeksRemaining = Math.max(0, 10 - weeksTop10);

      mainContent.innerHTML = `
        <div class="p-4 space-y-6">
          <h1 class="text-3xl font-extrabold text-[var(--dark-text)] flex items-center">
            <i data-lucide="leaf" class="w-8 h-8 text-[var(--primary-green)] mr-2"></i>
            Painel de Bordo Projeto RECicle
          </h1>
          <p class="text-sm text-[var(--gray-text)]">Usuário ID: <span class="font-mono text-xs bg-gray-100 p-1 rounded">${userId}</span></p>

          <!-- Métricas Principais -->
          <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
            ${renderCardMetric('award', 'Milhas Acumuladas', points.toLocaleString('pt-BR'), 'Milhas', 'border-[var(--primary-blue)]')}
            ${renderCardMetric('bar-chart', 'Sua Posição no Ranking', rankingPosition, 'º Lugar', 'border-[var(--primary-orange)]')}
            ${renderCardMetric('trophy', 'Semanas para o Prêmio', prizeWeeksRemaining, 'Semanas', 'border-[var(--primary-green)]')}
          </div>

          <!-- Próxima Missão -->
          <div class="bg-white p-6 rounded-xl shadow-xl border-t-4 border-[var(--light-blue)]">
            <h2 class="text-xl font-bold text-[var(--dark-text)] mb-3 flex items-center">
              <i data-lucide="chevron-right" class="w-5 h-5 mr-1 text-[var(--light-blue)]"></i>
              Próximo Desafio
            </h2>
            ${currentMission ? `
              <div>
                <p class="text-lg font-semibold">${currentMission.title}</p>
                <div class="mt-2 h-2 bg-gray-200 rounded-full">
                  <div class="h-full bg-[var(--primary-green)] rounded-full" style="width: ${Math.min(100, (currentMission.current / currentMission.target) * 100)}%;"></div>
                </div>
                <p class="text-sm text-[var(--gray-text)] mt-2">
                  ${currentMission.current} / ${currentMission.target} ${currentMission.unit} de ${currentMission.material}
                </p>
                <p class="text-[var(--primary-blue)] font-bold mt-1">Recompensa: +${currentMission.points} Milhas!</p>
              </div>
            ` : `
              <p class="text-[var(--gray-text)]">Todas as missões concluídas! Verifique em 'Missões' para novas.</p>
            `}
          </div>

          <!-- Histórico Recente -->
          <div class="bg-white p-6 rounded-xl shadow-xl">
            <h2 class="text-xl font-bold text-[var(--dark-text)] mb-4">Últimos Descartes</h2>
            <div class="space-y-3">
              ${history.slice(0, 3).map(item => `
                <div class="flex justify-between items-center border-b pb-2 last:border-b-0">
                  <div class="flex items-center">
                    <i data-lucide="recycle" class="w-5 h-5 text-[var(--primary-green)] mr-3"></i>
                    <div>
                      <p class="font-semibold text-[var(--dark-text)]">${item.type} (${item.weight} Kg)</p>
                      <p class="text-xs text-[var(--gray-text)]">${item.date} - ${item.event}</p>
                    </div>
                  </div>
                  <span class="font-bold text-lg ${item.points > 0 ? 'text-[var(--primary-blue)]' : 'text-red-500'}">
                    ${item.points > 0 ? '+' : ''}${item.points}
                  </span>
                </div>
              `).join('')}
            </div>
          </div>
        </div>
      `;
    }

    function renderDeposit() {
      const { material, weight, eventBonus, status } = state.deposit;
      const points = getCalculatedPoints();
      
      mainContent.innerHTML = `
        <div class="p-4 space-y-6">
          <h1 class="text-3xl font-extrabold text-[var(--dark-text)] flex items-center">
            <i data-lucide="scan" class="w-8 h-8 text-[var(--primary-blue)] mr-2"></i>
            Lixeira Inteligente RECicle
          </h1>
          <div class="bg-white p-6 rounded-xl shadow-xl space-y-4">
            
            <h2 class="text-xl font-bold text-[var(--dark-text)] border-b pb-2">1. Selecione o Material</h2>
            <div id="material-selector" class="grid grid-cols-2 gap-4">
              ${Object.keys(PONTOS_BASE).map(mat => `
                <button
                  onclick="handleMaterialSelect('${mat}')"
                  class="p-4 rounded-lg font-semibold transition-all duration-200 shadow-md ${
                    material === mat
                      ? 'bg-[var(--primary-blue)] text-white ring-4 ring-[var(--light-blue)]'
                      : 'bg-gray-100 text-[var(--dark-text)] hover:bg-[var(--light-blue)] hover:text-white'
                  }"
                >
                  ${mat}
                </button>
              `).join('')}
            </div>

            <h2 class="text-xl font-bold text-[var(--dark-text)] border-b pb-2 pt-4">2. Defina o Peso e Evento</h2>
            <div>
              <label class="block text-sm font-medium text-[var(--gray-text)]">Peso Estimado (Kg)</label>
              <input
                type="range"
                min="0.1"
                max="5"
                step="0.1"
                value="${weight}"
                oninput="handleWeightChange(this.value)"
                class="w-full h-2 bg-gray-200 rounded-lg appearance-none cursor-pointer mt-2"
              />
              <p id="weight-display" class="text-center font-semibold text-lg mt-1">${parseFloat(weight).toFixed(1)} Kg</p>
            </div>

            <div class='flex space-x-4'>
              <div class="flex-1">
                <label class="block text-sm font-medium text-[var(--gray-text)]">Bônus de Evento</label>
                <select
                  value="${eventBonus}"
                  onchange="handleBonusChange(this.value)"
                  class="mt-1 block w-full py-2 px-3 border border-gray-300 bg-white rounded-md shadow-sm focus:outline-none focus:ring-[var(--primary-green)] focus:border-[var(--primary-green)] sm:text-sm"
                >
                  <option value="1.0">Normal (x1.0)</option>
                  <option value="1.5">São João/Carnaval (x1.5)</option>
                </select>
              </div>
              <div class="flex-1 bg-[var(--light-green)] p-3 rounded-lg flex flex-col justify-center items-center">
                <p class="text-sm font-medium text-[var(--dark-text)]">Pontuação Estimada</p>
                <p id="points-display" class="text-2xl font-bold text-[var(--primary-blue)]">+${points}</p>
              </div>
            </div>

            <div class="pt-4">
              <div id="deposit-button-container">
                <!-- Botão de depósito será renderizado aqui -->
              </div>
              <div id="status-message" class='text-center h-8'>
                <!-- Mensagem de status será renderizada aqui -->
              </div>
            </div>
          </div>
        </div>
      `;
      // Renderiza os botões e status dinâmicos
      renderDepositStatus();
    }
    
    function renderMissions() {
      const referralLink = `https://recicle.app/indique/${state.userId}`;
      const activeMissions = mockMissions.filter(m => !m.completed);
      
      mainContent.innerHTML = `
        <div class="p-4 space-y-6">
          <h1 class="text-3xl font-extrabold text-[var(--dark-text)] flex items-center">
            <i data-lucide="award" class="w-8 h-8 text-[var(--primary-orange)] mr-2"></i>
            Missões e Indicação
          </h1>
          
          <!-- Missões Ativas -->
          <div class="bg-white p-6 rounded-xl shadow-xl border-t-4 border-[var(--primary-orange)]">
            <h2 class="text-xl font-bold text-[var(--dark-text)] mb-4">Missões Ativas (${activeMissions.length})</h2>
            <div class="space-y-4">
              ${activeMissions.map(mission => `
                <div class="p-3 border rounded-lg bg-[var(--primary-orange)]/[0.05]">
                  <p class="font-bold text-lg text-[var(--dark-text)]">${mission.title}</p>
                  <p class="text-sm text-[var(--gray-text)] mt-1">Acumule ${mission.target} ${mission.unit} de ${mission.material} para ganhar <span class="text-[var(--primary-orange)] font-extrabold">+${mission.points} Milhas</span>.</p>
                  <div class="mt-2 h-2 bg-gray-300 rounded-full">
                    <div class="h-full bg-[var(--primary-orange)] rounded-full" style="width: ${Math.min(100, (mission.current / mission.target) * 100)}%;"></div>
                  </div>
                  <p class="text-right text-xs text-[var(--gray-text)] mt-1">${mission.current} / ${mission.target} ${mission.unit}</p>
                </div>
              `).join('')}
            </div>
          </div>

          <!-- Indicação -->
          <div class="bg-white p-6 rounded-xl shadow-xl border-t-4 border-[var(--primary-blue)]">
            <h2 class="text-xl font-bold text-[var(--dark-text)] mb-4 flex items-center">
              <i data-lucide="users" class="w-6 h-6 mr-2 text-[var(--primary-blue)]"></i>
              Indique e Ganhe!
            </h2>
            <p class="text-[var(--gray-text)] mb-3">
              Convide seus amigos...
            </p>
            <div class="flex flex-col sm:flex-row space-y-2 sm:space-y-0 sm:space-x-2">
              <input type="text" readonly value="${referralLink}" class="flex-grow p-3 border border-gray-300 rounded-lg bg-gray-50 text-sm overflow-x-auto" />
              <button onclick="copyReferral()" class="py-3 px-6 bg-[var(--primary-blue)] text-white font-semibold rounded-lg hover:bg-[var(--light-blue)] transition-colors duration-200">
                Copiar Link
              </button>
            </div>
          </div>
        </div>
      `;
    }
    
    function renderRanking() {
      const sortedRanking = [...mockRanking].sort((a, b) => b.points - a.points);
      
      mainContent.innerHTML = `
        <div class="p-4 space-y-6">
          <h1 class="text-3xl font-extrabold text-[var(--dark-text)] flex items-center">
            <i data-lucide="trophy" class="w-8 h-8 text-[var(--primary-orange)] mr-2"></i>
            Ranking de Campeões
          </h1>
          <p class="text-[var(--gray-text)]">Os 10 primeiros que se mantiverem por 10 semanas garantem prêmios especiais da PCR!</p>
          
          <div class="overflow-x-auto bg-white rounded-xl shadow-xl">
            <table class="min-w-full divide-y divide-gray-200">
              <thead class="bg-[var(--light-green)]/[0.2]">
                <tr>
                  <th class="px-6 py-3 text-left text-xs font-bold text-[var(--dark-text)] uppercase tracking-wider">Posição</th>
                  <th class="px-6 py-3 text-left text-xs font-bold text-[var(--dark-text)] uppercase tracking-wider">Usuário / ID</th>
                  <th class="px-6 py-3 text-left text-xs font-bold text-[var(--dark-text)] uppercase tracking-wider">Milhas</th>
                  <th class="px-6 py-3 text-center text-xs font-bold text-[var(--dark-text)] uppercase tracking-wider">Semanas no Top 10</th>
                </tr>
              </thead>
              <tbody class="divide-y divide-gray-200">
                ${sortedRanking.map((user, index) => {
                  const isCurrentUser = user.userId === state.userId;
                  return `
                    <tr class="transition-colors duration-150 ${isCurrentUser ? 'bg-[var(--primary-orange)]/[0.1] font-bold' : 'hover:bg-gray-50'}">
                      <td class="px-6 py-4 whitespace-nowrap">
                        ${index + 1 === 1 ? '<i data-lucide="trophy" class="w-6 h-6 text-[var(--primary-orange)]"></i>' : index + 1}
                      </td>
                      <td class="px-6 py-4 whitespace-nowrap">
                        ${isCurrentUser ? 'Você' : user.name}
                        <p class="text-xs text-[var(--gray-text)] font-mono">${user.userId}</p>
                      </td>
                      <td class="px-6 py-4 whitespace-nowrap text-lg text-[var(--primary-blue)] font-extrabold">
                        ${user.points.toLocaleString('pt-BR')}
                      </td>
                      <td class="px-6 py-4 whitespace-nowrap text-center">
                        <span class="px-2 inline-flex text-xs leading-5 font-semibold rounded-full ${user.weeks >= 10 ? 'bg-[var(--primary-green)]/[0.2] text-[var(--primary-green)]' : 'bg-[var(--primary-blue)]/[0.2] text-[var(--primary-blue)]'}">
                          ${user.weeks} / 10
                        </span>
                      </td>
                    </tr>
                  `;
                }).join('')}
              </tbody>
            </table>
          </div>
        </div>
      `;
    }
    
    function renderSettings() {
      mainContent.innerHTML = `
        <div class="p-4">
          <h1 class="text-3xl font-extrabold text-[var(--dark-text)] flex items-center">
            <i data-lucide="settings" class="w-8 h-8 text-[var(--gray-text)] mr-2"></i>
            Resgate de Pontos
          </h1>
          <p class='text-[var(--gray-text)] mt-4'>
            Aqui o usuário poderia resgatar suas milhas por vouchers de eventos, ingressos, ou benefícios com parceiros da Prefeitura do Recife.
          </p>
        </div>
      `;
    }
    
    // --- LÓGICA DE DEPÓSITO ---

    function getCalculatedPoints() {
      const { material, weight, eventBonus } = state.deposit;
      if (!material || weight <= 0) return 0;
      const basePoints = PONTOS_BASE[material] || 0;
      const totalPoints = basePoints * weight * eventBonus;
      return Math.round(totalPoints);
    }
    
    function updatePointsDisplay() {
        const pointsDisplay = document.getElementById('points-display');
        if (pointsDisplay) {
            pointsDisplay.textContent = `+${getCalculatedPoints()}`;
        }
    }

    function handleMaterialSelect(material) {
      state.deposit.material = material;
      // Re-renderiza apenas o seletor e o botão (otimização)
      const selectorContainer = document.getElementById('material-selector');
      selectorContainer.innerHTML = Object.keys(PONTOS_BASE).map(mat => `
        <button
          onclick="handleMaterialSelect('${mat}')"
          class="p-4 rounded-lg font-semibold transition-all duration-200 shadow-md ${
            state.deposit.material === mat
              ? 'bg-[var(--primary-blue)] text-white ring-4 ring-[var(--light-blue)]'
              : 'bg-gray-100 text-[var(--dark-text)] hover:bg-[var(--light-blue)] hover:text-white'
          }"
        >
          ${mat}
        </button>
      `).join('');
      renderDepositStatus();
      updatePointsDisplay();
    }

    function handleWeightChange(value) {
      state.deposit.weight = parseFloat(value);
      document.getElementById('weight-display').textContent = `${state.deposit.weight.toFixed(1)} Kg`;
      updatePointsDisplay();
    }

    function handleBonusChange(value) {
      state.deposit.eventBonus = parseFloat(value);
      updatePointsDisplay();
    }

    function handleStartScan() {
      state.deposit.status = 'escaneando';
      renderDepositStatus();
      setTimeout(() => {
        state.deposit.status = 'depositando';
        renderDepositStatus();
      }, 1500);
    }

    function handleDeposit() {
      const isCorrect = Math.random() < 0.9;
      const points = getCalculatedPoints();
      
      state.deposit.status = 'aguardando';
      renderDepositStatus();

      setTimeout(() => {
        if (isCorrect && points > 0) {
          state.deposit.status = 'concluido';
          // Chama o handler principal
          onDeposit(points, state.deposit.material);
        } else {
          state.deposit.status = 'erro';
          const penalty = state.deposit.material ? PONTOS_BASE[state.deposit.material] * 5 : 1000;
          onDeposit(-penalty, 'incorreto');
        }
        
        // Atualiza a UI de depósito
        renderDepositStatus();
        
        // Reseta o formulário
        setTimeout(() => {
            state.deposit = { ...state.deposit, status: 'pronto', material: '', weight: 0.5 };
            // Re-renderiza a aba de depósito para resetar
            if(state.selectedTab === 'deposit') {
                renderDeposit();
                lucide.createIcons();
            }
        }, 3000);
      }, 2000);
    }
    
    // Função principal de atualização de estado (simulando Redux/Context)
    function onDeposit(newPoints, type) {
        state.points += newPoints;
        state.history.unshift({
            id: Date.now(),
            type: type === 'incorreto' ? 'Descarte Incorreto' : type,
            weight: type === 'incorreto' ? 0 : state.deposit.weight,
            points: newPoints,
            date: new Date().toLocaleDateString('pt-BR'),
            event: newPoints < 0 ? 'Penalidade' : 'Normal',
        });

        if (newPoints > 0) {
            state.rankingPosition = Math.max(1, state.rankingPosition - 1);
        } else {
            state.rankingPosition = Math.min(10, state.rankingPosition + 1);
        }
    }
    
    // Atualiza apenas os botões e mensagens de status
    function renderDepositStatus() {
        const { material, status } = state.deposit;
        const buttonContainer = document.getElementById('deposit-button-container');
        const statusMessage = document.getElementById('status-message');
        
        if (!buttonContainer || !statusMessage) return;

        let buttonHtml = '';
        let messageHtml = '';

        switch (status) {
            case 'pronto':
                buttonHtml = `
                    <button
                        onclick="handleStartScan()"
                        ${!material ? 'disabled' : ''}
                        class="w-full py-3 rounded-xl font-bold text-lg text-white transition-colors duration-200 ${
                            material ? 'bg-[var(--primary-blue)] hover:bg-[var(--light-blue)] shadow-md' : 'bg-gray-400 cursor-not-allowed'
                        }"
                    >
                        <i data-lucide="scan" class="inline w-5 h-5 mr-2"></i>
                        1. Escanear QR & Iniciar Descarte
                    </button>`;
                break;
            case 'depositando':
                buttonHtml = `
                    <button
                        onclick="handleDeposit()"
                        class="w-full py-3 rounded-xl font-bold text-lg text-white bg-[var(--primary-orange)] hover:bg-[var(--primary-orange)]/90 shadow-md animate-pulse"
                    >
                        2. Depositar e Confirmar!
                    </button>`;
                messageHtml = `<p class="text-[var(--primary-orange)] font-semibold mt-4">Deposite o material agora. Câmera e peso em análise...</p>`;
                break;
            case 'escaneando':
                messageHtml = `<p class="text-[var(--primary-blue)] font-semibold mt-4">Escaneando QR Code... Lixeira liberada!</p>`;
                // Fall-through para botão desabilitado
            case 'aguardando':
                if(status === 'aguardando') messageHtml = `<p class="text-[var(--primary-blue)] font-semibold mt-4">Analisando o descarte...</p>`;
                buttonHtml = `
                    <button disabled class="w-full py-3 rounded-xl font-bold text-lg text-white bg-gray-400 cursor-not-allowed">
                        Aguardando...
                    </button>`;
                break;
            case 'concluido':
                messageHtml = `<p class="text-[var(--primary-green)] font-bold mt-4 text-xl flex items-center justify-center"><i data-lucide="check-circle" class="mr-2"></i> Descarte OK! Pontos adicionados.</p>`;
                buttonHtml = buttonHtml = `<button disabled class="w-full py-3 rounded-xl font-bold text-lg text-white bg-gray-400 cursor-not-allowed">Concluído</button>`;
                break;
            case 'erro':
                messageHtml = `<p class="text-red-600 font-bold mt-4 text-xl flex items-center justify-center"><i data-lucide="x-circle" class="mr-2"></i> Material incorreto! Penalidade aplicada.</p>`;
                buttonHtml = buttonHtml = `<button disabled class="w-full py-3 rounded-xl font-bold text-lg text-white bg-gray-400 cursor-not-allowed">Erro</button>`;
                break;
        }
        
        buttonContainer.innerHTML = buttonHtml;
        statusMessage.innerHTML = messageHtml;
        
        // Atualiza os ícones dentro dos elementos recém-criados
        lucide.createIcons();
    }
    
    function copyReferral() {
        const referralLink = `https://recicle.app/indique/${state.userId}`;
        navigator.clipboard.writeText(referralLink).then(() => {
            // Não podemos usar alert(), então usamos um feedback visual (mudando o texto do botão)
            const copyButton = document.querySelector('button[onclick="copyReferral()"]');
            if(copyButton) {
                copyButton.textContent = 'Copiado!';
                setTimeout(() => { copyButton.textContent = 'Copiar Link'; }, 2000);
            }
        });
    }

    // --- FUNÇÃO DE RENDERIZAÇÃO PRINCIPAL ---
    function renderApp() {
      // 1. Renderiza a navegação (destaca o item ativo)
      renderNav();

      // 2. Renderiza o conteúdo da aba selecionada
      switch (state.selectedTab) {
        case 'dashboard':
          renderDashboard();
          break;
        case 'deposit':
          renderDeposit();
          break;
        case 'missions':
          renderMissions();
          break;
        case 'ranking':
          renderRanking();
          break;
        case 'settings':
          renderSettings();
          break;
      }

      // 3. (MUITO IMPORTANTE) Renderiza os ícones do Lucide
      // Isso é necessário toda vez que o DOM é alterado.
      lucide.createIcons();
    }

    // --- INICIALIZAÇÃO ---
    document.addEventListener('DOMContentLoaded', renderApp);
  </script>
</body>
</html>

