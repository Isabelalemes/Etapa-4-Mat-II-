# Etapa-4-Mat-II-
Projeto do site 
<!DOCTYPE html>
<html lang="pt-BR" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>EduCentral - Portal Unificado do Estudante</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        primary: {
                            50: '#eef2ff',
                            100: '#e0e7ff',
                            500: '#6366f1',
                            600: '#4f46e5',
                            700: '#4338ca',
                        },
                        emerald: {
                            500: '#10b981',
                            600: '#059669',
                        }
                    },
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    }
                }
            }
        }
    </script>
    <!-- FontAwesome for Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts Inter -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
        }
        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
            height: 8px;
        }
        ::-webkit-scrollbar-track {
            background: rgba(0, 0, 0, 0.05);
        }
        ::-webkit-scrollbar-thumb {
            background: rgba(100, 116, 139, 0.3);
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: rgba(100, 116, 139, 0.5);
        }
    </style>
</head>
<body class="bg-slate-50 dark:bg-slate-900 text-slate-800 dark:text-slate-100 min-h-screen transition-colors duration-300 flex flex-col">

    <!-- HEADER / NAVIGATION -->
    <header class="sticky top-0 z-40 bg-white/80 dark:bg-slate-800/80 backdrop-blur-md border-b border-slate-200 dark:border-slate-700 transition-colors">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-16 flex items-center justify-between gap-4">
            
            <!-- Logo & Brand -->
            <div class="flex items-center gap-3">
                <div class="w-10 h-10 rounded-xl bg-indigo-600 flex items-center justify-center text-white shadow-lg shadow-indigo-500/30">
                    <i class="fa-solid fa-graduation-cap text-xl"></i>
                </div>
                <div>
                    <span class="text-xl font-bold bg-clip-text text-transparent bg-gradient-to-r from-indigo-600 to-violet-600 dark:from-indigo-400 dark:to-violet-400">EduCentral</span>
                    <span class="hidden sm:inline-block text-xs text-slate-500 dark:text-slate-400 font-medium ml-2 border-l border-slate-300 dark:border-slate-600 pl-2">Hub do Estudante</span>
                </div>
            </div>

            <!-- Search Bar -->
            <div class="hidden md:flex items-center flex-1 max-w-md mx-4">
                <div class="relative w-full">
                    <i class="fa-solid fa-magnifying-glass absolute left-3.5 top-1/2 -translate-y-1/2 text-slate-400 text-sm"></i>
                    <input type="text" id="searchInput" onkeyup="filterExamsBySearch()" placeholder="Buscar vestibulares, concursos, matérias..." class="w-full pl-10 pr-4 py-2 text-sm bg-slate-100 dark:bg-slate-700/60 text-slate-900 dark:text-slate-100 rounded-xl border-0 focus:ring-2 focus:ring-indigo-500 outline-none transition-all">
                </div>
            </div>

            <!-- Navigation Links & Actions -->
            <div class="flex items-center gap-3">
                <nav class="hidden lg:flex items-center gap-1 text-sm font-medium text-slate-600 dark:text-slate-300">
                    <a href="#provas" class="px-3 py-2 rounded-lg hover:text-indigo-600 dark:hover:text-indigo-400 hover:bg-slate-100 dark:hover:bg-slate-700/50 transition">Provas</a>
                    <a href="#cronograma" class="px-3 py-2 rounded-lg hover:text-indigo-600 dark:hover:text-indigo-400 hover:bg-slate-100 dark:hover:bg-slate-700/50 transition">Cronograma</a>
                    <a href="#materiais" class="px-3 py-2 rounded-lg hover:text-indigo-600 dark:hover:text-indigo-400 hover:bg-slate-100 dark:hover:bg-slate-700/50 transition">Materiais</a>
                    <a href="#noticias" class="px-3 py-2 rounded-lg hover:text-indigo-600 dark:hover:text-indigo-400 hover:bg-slate-100 dark:hover:bg-slate-700/50 transition">Notícias</a>
                </nav>

                <div class="h-5 w-px bg-slate-200 dark:bg-slate-700 hidden lg:block"></div>

                <!-- Theme Toggle Button -->
                <button id="themeToggle" onclick="toggleDarkMode()" class="p-2.5 text-slate-500 hover:text-indigo-600 dark:text-slate-400 dark:hover:text-indigo-400 rounded-xl bg-slate-100 dark:bg-slate-700/50 hover:bg-slate-200 dark:hover:bg-slate-700 transition" title="Alternar Modo Escuro">
                    <i class="fa-solid fa-moon dark:hidden"></i>
                    <i class="fa-solid fa-sun hidden dark:block text-amber-400"></i>
                </button>

                <!-- User Profile Dropdown / Badge -->
                <div class="flex items-center gap-2 pl-2 border-l border-slate-200 dark:border-slate-700">
                    <img src="https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&q=80&w=150" alt="Avatar do Usuário" class="w-9 h-9 rounded-full object-cover ring-2 ring-indigo-500/30">
                    <div class="hidden sm:block text-left text-xs">
                        <p class="font-semibold text-slate-800 dark:text-slate-100 leading-tight">Mariana Silva</p>
                        <p class="text-slate-500 dark:text-slate-400">Foco: ENEM / FUVEST</p>
                    </div>
                </div>
            </div>
        </div>
    </header>

    <!-- MAIN CONTENT CONTAINER -->
    <main class="flex-1 max-w-7xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-8 space-y-8">

        <!-- WELCOME BANNER & FEATURED COUNTDOWN WIDGET -->
        <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
            <!-- Welcome Info -->
            <div class="lg:col-span-2 bg-gradient-to-r from-indigo-600 to-indigo-800 rounded-2xl p-6 sm:p-8 text-white shadow-xl shadow-indigo-500/10 relative overflow-hidden flex flex-col justify-between">
                <div class="absolute -right-10 -bottom-10 w-60 h-60 bg-white/10 rounded-full blur-2xl pointer-events-none"></div>
                <div class="relative z-10">
                    <span class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-white/20 text-xs font-semibold uppercase tracking-wider backdrop-blur-md mb-4">
                        <i class="fa-solid fa-bolt text-amber-300"></i> Painel do Aluno
                    </span>
                    <h1 class="text-2xl sm:text-3xl font-bold tracking-tight mb-2">Bem-vinda de volta, Mariana! 👋</h1>
                    <p class="text-indigo-100 text-sm sm:text-base max-w-xl">
                        Você tem <strong class="text-white underline">3 inscrições ativas</strong> e <strong>1 simulado agendado</strong> para este fim de semana. Mantenha o foco nos seus objetivos!
                    </p>
                </div>

                <div class="mt-6 pt-6 border-t border-white/20 flex flex-wrap gap-4 items-center justify-between text-xs sm:text-sm text-indigo-100 relative z-10">
                    <div class="flex items-center gap-2">
                        <i class="fa-solid fa-fire text-amber-400 text-base"></i>
                        <span>Sequência de estudos: <strong class="text-white">14 Dias</strong></span>
                    </div>
                    <a href="#cronograma" class="inline-flex items-center gap-2 px-4 py-2 rounded-xl bg-white text-indigo-700 font-semibold text-xs hover:bg-indigo-50 transition shadow">
                        Ir para meu Cronograma <i class="fa-solid fa-arrow-right"></i>
                    </a>
                </div>
            </div>

            <!-- Featured Countdown Card (ENEM 2026) -->
            <div class="bg-white dark:bg-slate-800 rounded-2xl p-6 border border-slate-200 dark:border-slate-700 shadow-sm flex flex-col justify-between">
                <div>
                    <div class="flex justify-between items-start mb-3">
                        <span class="px-2.5 py-1 rounded-md text-xs font-bold bg-amber-100 text-amber-800 dark:bg-amber-900/40 dark:text-amber-300">
                            <i class="fa-solid fa-star mr-1"></i> Destaque Nacional
                        </span>
                        <span class="text-xs text-slate-500 dark:text-slate-400">1º Dia de Prova</span>
                    </div>
                    <h3 class="text-lg font-bold text-slate-900 dark:text-slate-100">ENEM 2026</h3>
                    <p class="text-xs text-slate-500 dark:text-slate-400 mt-0.5">Exame Nacional do Ensino Médio</p>
                </div>

                <!-- Timer Grid -->
                <div class="my-4 grid grid-cols-4 gap-2 text-center">
                    <div class="bg-slate-50 dark:bg-slate-700/50 p-2 rounded-xl border border-slate-100 dark:border-slate-700">
                        <span id="timer-days" class="block text-xl font-black text-indigo-600 dark:text-indigo-400">12</span>
                        <span class="text-[10px] uppercase font-semibold text-slate-400">Dias</span>
                    </div>
                    <div class="bg-slate-50 dark:bg-slate-700/50 p-2 rounded-xl border border-slate-100 dark:border-slate-700">
                        <span id="timer-hours" class="block text-xl font-black text-indigo-600 dark:text-indigo-400">18</span>
                        <span class="text-[10px] uppercase font-semibold text-slate-400">Horas</span>
                    </div>
                    <div class="bg-slate-50 dark:bg-slate-700/50 p-2 rounded-xl border border-slate-100 dark:border-slate-700">
                        <span id="timer-mins" class="block text-xl font-black text-indigo-600 dark:text-indigo-400">42</span>
                        <span class="text-[10px] uppercase font-semibold text-slate-400">Min</span>
                    </div>
                    <div class="bg-slate-50 dark:bg-slate-700/50 p-2 rounded-xl border border-slate-100 dark:border-slate-700">
                        <span id="timer-secs" class="block text-xl font-black text-indigo-600 dark:text-indigo-400">09</span>
                        <span class="text-[10px] uppercase font-semibold text-slate-400">Seg</span>
                    </div>
                </div>

                <button onclick="openExamModal('enem')" class="w-full py-2.5 px-4 rounded-xl bg-slate-100 dark:bg-slate-700 hover:bg-indigo-600 hover:text-white dark:hover:bg-indigo-600 text-slate-700 dark:text-slate-200 text-xs font-semibold transition flex items-center justify-center gap-2">
                    <i class="fa-regular fa-file-lines"></i> Ver Edital e Informações
                </button>
            </div>
        </div>

        <!-- METRICS / SUMMARY CARDS -->
        <section class="grid grid-cols-2 md:grid-cols-4 gap-4">
            <div class="bg-white dark:bg-slate-800 p-4 rounded-2xl border border-slate-200 dark:border-slate-700 shadow-sm flex items-center gap-4">
                <div class="w-12 h-12 rounded-xl bg-emerald-100 dark:bg-emerald-900/30 text-emerald-600 dark:text-emerald-400 flex items-center justify-center text-xl shrink-0">
                    <i class="fa-solid fa-file-circle-check"></i>
                </div>
                <div>
                    <span class="text-2xl font-bold text-slate-900 dark:text-slate-100">08</span>
                    <p class="text-xs text-slate-500 dark:text-slate-400 font-medium">Inscrições Abertas</p>
                </div>
            </div>

            <div class="bg-white dark:bg-slate-800 p-4 rounded-2xl border border-slate-200 dark:border-slate-700 shadow-sm flex items-center gap-4">
                <div class="w-12 h-12 rounded-xl bg-indigo-100 dark:bg-indigo-900/30 text-indigo-600 dark:text-indigo-400 flex items-center justify-center text-xl shrink-0">
                    <i class="fa-solid fa-clock"></i>
                </div>
                <div>
                    <span class="text-2xl font-bold text-slate-900 dark:text-slate-100">12d</span>
                    <p class="text-xs text-slate-500 dark:text-slate-400 font-medium">Próxima Prova</p>
                </div>
            </div>

            <div class="bg-white dark:bg-slate-800 p-4 rounded-2xl border border-slate-200 dark:border-slate-700 shadow-sm flex items-center gap-4">
                <div class="w-12 h-12 rounded-xl bg-violet-100 dark:bg-violet-900/30 text-violet-600 dark:text-violet-400 flex items-center justify-center text-xl shrink-0">
                    <i class="fa-solid fa-pen-ruler"></i>
                </div>
                <div>
                    <span class="text-2xl font-bold text-slate-900 dark:text-slate-100">24</span>
                    <p class="text-xs text-slate-500 dark:text-slate-400 font-medium">Simulados Feitos</p>
                </div>
            </div>

            <div class="bg-white dark:bg-slate-800 p-4 rounded-2xl border border-slate-200 dark:border-slate-700 shadow-sm flex items-center gap-4">
                <div class="w-12 h-12 rounded-xl bg-amber-100 dark:bg-amber-900/30 text-amber-600 dark:text-amber-400 flex items-center justify-center text-xl shrink-0">
                    <i class="fa-solid fa-hourglass-half"></i>
                </div>
                <div>
                    <span class="text-2xl font-bold text-slate-900 dark:text-slate-100">142h</span>
                    <p class="text-xs text-slate-500 dark:text-slate-400 font-medium">Horas Estudadas</p>
                </div>
            </div>
        </section>

        <!-- EXAM LISTINGS & FILTERS SECTION -->
        <section id="provas" class="space-y-6">
            <div class="flex flex-col md:flex-row md:items-center justify-between gap-4">
                <div>
                    <h2 class="text-xl font-bold text-slate-900 dark:text-slate-100 flex items-center gap-2">
                        <i class="fa-solid fa-calendar-days text-indigo-600 dark:text-indigo-400"></i>
                        Calendário de Vestibulares & Concursos
                    </h2>
                    <p class="text-xs text-slate-500 dark:text-slate-400 mt-1">Acompanhe editais, datas de inscrição e provas atualizados em tempo real.</p>
                </div>

                <!-- Filter Tabs -->
                <div class="flex items-center gap-1 bg-slate-200/60 dark:bg-slate-800 p-1 rounded-xl overflow-x-auto">
                    <button onclick="filterCategory('todos')" class="filter-tab active px-3.5 py-1.5 rounded-lg text-xs font-semibold text-slate-700 dark:text-slate-300 transition whitespace-nowrap" data-tab="todos">Todos</button>
                    <button onclick="filterCategory('vestibular')" class="filter-tab px-3.5 py-1.5 rounded-lg text-xs font-semibold text-slate-600 dark:text-slate-400 transition whitespace-nowrap" data-tab="vestibular">Vestibulares</button>
                    <button onclick="filterCategory('concurso')" class="filter-tab px-3.5 py-1.5 rounded-lg text-xs font-semibold text-slate-600 dark:text-slate-400 transition whitespace-nowrap" data-tab="concurso">Concursos Públicos</button>
                    <button onclick="filterCategory('processo')" class="filter-tab px-3.5 py-1.5 rounded-lg text-xs font-semibold text-slate-600 dark:text-slate-400 transition whitespace-nowrap" data-tab="processo">Processos Seletivos</button>
                </div>
            </div>

            <!-- Exam Cards Grid -->
            <div id="examGrid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                <!-- Cards will be populated by JavaScript -->
            </div>
        </section>

        <!-- STUDY PLANNER & EDUCATIONAL RESOURCES (2-COLUMN LAYOUT) -->
        <div class="grid grid-cols-1 lg:grid-cols-3 gap-8">
            
            <!-- STUDY PLANNER & CHECKLIST (2 COLUMNS) -->
            <section id="cronograma" class="lg:col-span-2 bg-white dark:bg-slate-800 rounded-2xl p-6 border border-slate-200 dark:border-slate-700 shadow-sm flex flex-col justify-between">
                <div>
                    <div class="flex items-center justify-between mb-4">
                        <div>
                            <h3 class="text-lg font-bold text-slate-900 dark:text-slate-100 flex items-center gap-2">
                                <i class="fa-solid fa-list-check text-indigo-600 dark:text-indigo-400"></i>
                                Planner de Estudos Diário
                            </h3>
                            <p class="text-xs text-slate-500 dark:text-slate-400">Organize suas metas e acompanhe seu progresso de hoje.</p>
                        </div>
                        <span id="taskCounter" class="text-xs font-bold px-2.5 py-1 rounded-full bg-indigo-50 dark:bg-indigo-900/40 text-indigo-600 dark:text-indigo-300">
                            0/0 Concluídas
                        </span>
                    </div>

                    <!-- Progress Bar -->
                    <div class="w-full bg-slate-100 dark:bg-slate-700 rounded-full h-2 mb-6 overflow-hidden">
                        <div id="taskProgressBar" class="bg-indigo-600 h-2 rounded-full transition-all duration-300" style="width: 0%"></div>
                    </div>

                    <!-- Add New Task Input -->
                    <form onsubmit="addNewTask(event)" class="flex gap-2 mb-6">
                        <input type="text" id="newTaskInput" placeholder="Ex: Resolver 20 questões de Física sobre Mecânica..." required class="flex-1 text-sm bg-slate-50 dark:bg-slate-700/50 border border-slate-200 dark:border-slate-600 rounded-xl px-4 py-2.5 text-slate-800 dark:text-slate-100 focus:ring-2 focus:ring-indigo-500 outline-none">
                        <button type="submit" class="bg-indigo-600 hover:bg-indigo-700 text-white font-semibold px-4 py-2.5 rounded-xl text-sm transition flex items-center gap-2 shrink-0">
                            <i class="fa-solid fa-plus"></i> <span class="hidden sm:inline">Adicionar</span>
                        </button>
                    </form>

                    <!-- Checklist Items List -->
                    <div id="taskList" class="space-y-2 max-h-[320px] overflow-y-auto pr-1">
                        <!-- Populated by JS -->
                    </div>
                </div>

                <div class="mt-6 pt-4 border-t border-slate-100 dark:border-slate-700/60 flex justify-between items-center text-xs text-slate-500">
                    <span><i class="fa-solid fa-lightbulb text-amber-500 mr-1"></i> Dica: Tente focar em sessões de Pomodoro de 25 min.</span>
                    <button onclick="clearCompletedTasks()" class="hover:text-red-500 transition">Limpar concluídas</button>
                </div>
            </section>

            <!-- MATERIALS & RESOURCES (1 COLUMN) -->
            <section id="materiais" class="bg-white dark:bg-slate-800 rounded-2xl p-6 border border-slate-200 dark:border-slate-700 shadow-sm">
                <h3 class="text-lg font-bold text-slate-900 dark:text-slate-100 mb-1 flex items-center gap-2">
                    <i class="fa-solid fa-folder-open text-indigo-600 dark:text-indigo-400"></i>
                    Materiais Gratuitos
                </h3>
                <p class="text-xs text-slate-500 dark:text-slate-400 mb-6">Downloads rápidos de provas, guiadas e apostilas.</p>

                <div class="space-y-3">
                    <a href="#" onclick="alert('Download da Apostila de Redação iniciado!')" class="group flex items-center p-3 rounded-xl border border-slate-100 dark:border-slate-700/60 hover:border-indigo-200 dark:hover:border-indigo-800 hover:bg-indigo-50/40 dark:hover:bg-slate-700/40 transition">
                        <div class="w-10 h-10 rounded-lg bg-red-100 dark:bg-red-900/30 text-red-600 dark:text-red-400 flex items-center justify-center text-lg mr-3 shrink-0">
                            <i class="fa-solid fa-file-pdf"></i>
                        </div>
                        <div class="flex-1 min-w-0">
                            <h4 class="text-xs font-semibold text-slate-800 dark:text-slate-200 truncate group-hover:text-indigo-600 dark:group-hover:text-indigo-400">Guia de Redação Nota 1000</h4>
                            <p class="text-[11px] text-slate-400">PDF • 4.2 MB • Estruturas coringa</p>
                        </div>
                        <i class="fa-solid fa-download text-slate-400 group-hover:text-indigo-600 ml-2 text-xs"></i>
                    </a>

                    <a href="#" onclick="alert('Download das Provas do ENEM iniciado!')" class="group flex items-center p-3 rounded-xl border border-slate-100 dark:border-slate-700/60 hover:border-indigo-200 dark:hover:border-indigo-800 hover:bg-indigo-50/40 dark:hover:bg-slate-700/40 transition">
                        <div class="w-10 h-10 rounded-lg bg-blue-100 dark:bg-blue-900/30 text-blue-600 dark:text-blue-400 flex items-center justify-center text-lg mr-3 shrink-0">
                            <i class="fa-solid fa-box-archive"></i>
                        </div>
                        <div class="flex-1 min-w-0">
                            <h4 class="text-xs font-semibold text-slate-800 dark:text-slate-200 truncate group-hover:text-indigo-600 dark:group-hover:text-indigo-400">Combo Provas ENEM (2018-2025)</h4>
                            <p class="text-[11px] text-slate-400">ZIP • 28.5 MB • Provas e Gabaritos</p>
                        </div>
                        <i class="fa-solid fa-download text-slate-400 group-hover:text-indigo-600 ml-2 text-xs"></i>
                    </a>

                    <a href="#" onclick="alert('Acessando videoaulas gratuitas!')" class="group flex items-center p-3 rounded-xl border border-slate-100 dark:border-slate-700/60 hover:border-indigo-200 dark:hover:border-indigo-800 hover:bg-indigo-50/40 dark:hover:bg-slate-700/40 transition">
                        <div class="w-10 h-10 rounded-lg bg-purple-100 dark:bg-purple-900/30 text-purple-600 dark:text-purple-400 flex items-center justify-center text-lg mr-3 shrink-0">
                            <i class="fa-solid fa-circle-play"></i>
                        </div>
                        <div class="flex-1 min-w-0">
                            <h4 class="text-xs font-semibold text-slate-800 dark:text-slate-200 truncate group-hover:text-indigo-600 dark:group-hover:text-indigo-400">Aulas de Revisão de Matemática</h4>
                            <p class="text-[11px] text-slate-400">Vídeos • Módulos FUVEST / Unicamp</p>
                        </div>
                        <i class="fa-solid fa-arrow-up-right-from-square text-slate-400 group-hover:text-indigo-600 ml-2 text-xs"></i>
                    </a>

                    <a href="#" onclick="alert('Download da Tabela Periódica Interativa!')" class="group flex items-center p-3 rounded-xl border border-slate-100 dark:border-slate-700/60 hover:border-indigo-200 dark:hover:border-indigo-800 hover:bg-indigo-50/40 dark:hover:bg-slate-700/40 transition">
                        <div class="w-10 h-10 rounded-lg bg-emerald-100 dark:bg-emerald-900/30 text-emerald-600 dark:text-emerald-400 flex items-center justify-center text-lg mr-3 shrink-0">
                            <i class="fa-solid fa-flask"></i>
                        </div>
                        <div class="flex-1 min-w-0">
                            <h4 class="text-xs font-semibold text-slate-800 dark:text-slate-200 truncate group-hover:text-indigo-600 dark:group-hover:text-indigo-400">Tabela Periódica Completa & Fórmulas</h4>
                            <p class="text-[11px] text-slate-400">PDF • Resumo ilustrado de Química</p>
                        </div>
                        <i class="fa-solid fa-download text-slate-400 group-hover:text-indigo-600 ml-2 text-xs"></i>
                    </a>
                </div>
            </section>
        </div>

        <!-- NEWS & ANNOUNCEMENTS FEED -->
        <section id="noticias" class="space-y-4">
            <div class="flex items-center justify-between">
                <div>
                    <h2 class="text-xl font-bold text-slate-900 dark:text-slate-100 flex items-center gap-2">
                        <i class="fa-solid fa-newspaper text-indigo-600 dark:text-indigo-400"></i>
                        Notícias e Atualizações de Editais
                    </h2>
                    <p class="text-xs text-slate-500 dark:text-slate-400 mt-1">Fique por dentro das alterações de cronograma, prorrogativas e dicas de estudo.</p>
                </div>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                <!-- News Card 1 -->
                <article class="bg-white dark:bg-slate-800 rounded-2xl border border-slate-200 dark:border-slate-700 overflow-hidden shadow-sm flex flex-col justify-between hover:shadow-md transition">
                    <div class="p-5">
                        <div class="flex items-center gap-2 text-xs text-indigo-600 dark:text-indigo-400 font-medium mb-2">
                            <span>MEC</span> • <span>Há 2 horas</span>
                        </div>
                        <h3 class="font-bold text-slate-900 dark:text-slate-100 text-sm mb-2 hover:text-indigo-600 cursor-pointer">
                            MEC confirma isenção da taxa do ENEM para alunos da rede pública
                        </h3>
                        <p class="text-slate-500 dark:text-slate-400 text-xs line-clamp-3">
                            Estudantes do 3º ano do ensino médio público terão isenção garantida automaticamente. Confira os prazos para confirmação do cadastro no sistema.
                        </p>
                    </div>
                    <div class="px-5 py-3 bg-slate-50 dark:bg-slate-700/30 border-t border-slate-100 dark:border-slate-700 flex justify-between items-center text-xs">
                        <span class="text-slate-400">Leitura de 3 min</span>
                        <a href="#" onclick="alert('Abrindo notícia completa...')" class="font-semibold text-indigo-600 dark:text-indigo-400 hover:underline">Ler mais <i class="fa-solid fa-angle-right"></i></a>
                    </div>
                </article>

                <!-- News Card 2 -->
                <article class="bg-white dark:bg-slate-800 rounded-2xl border border-slate-200 dark:border-slate-700 overflow-hidden shadow-sm flex flex-col justify-between hover:shadow-md transition">
                    <div class="p-5">
                        <div class="flex items-center gap-2 text-xs text-emerald-600 dark:text-emerald-400 font-medium mb-2">
                            <span>Concursos</span> • <span>Há 5 horas</span>
                        </div>
                        <h3 class="font-bold text-slate-900 dark:text-slate-100 text-sm mb-2 hover:text-indigo-600 cursor-pointer">
                            Caixa Econômica divulga edital com mais de 4.000 vagas presenciais
                        </h3>
                        <p class="text-slate-500 dark:text-slate-400 text-xs line-clamp-3">
                            Oportunidades para Técnico Bancário e área de TI com remuneração inicial que pode ultrapassar R$ 6.000 mais benefícios.
                        </p>
                    </div>
                    <div class="px-5 py-3 bg-slate-50 dark:bg-slate-700/30 border-t border-slate-100 dark:border-slate-700 flex justify-between items-center text-xs">
                        <span class="text-slate-400">Leitura de 5 min</span>
                        <a href="#" onclick="alert('Abrindo notícia completa...')" class="font-semibold text-indigo-600 dark:text-indigo-400 hover:underline">Ler mais <i class="fa-solid fa-angle-right"></i></a>
                    </div>
                </article>

                <!-- News Card 3 -->
                <article class="bg-white dark:bg-slate-800 rounded-2xl border border-slate-200 dark:border-slate-700 overflow-hidden shadow-sm flex flex-col justify-between hover:shadow-md transition">
                    <div class="p-5">
                        <div class="flex items-center gap-2 text-xs text-purple-600 dark:text-purple-400 font-medium mb-2">
                            <span>Dicas de Estudo</span> • <span>Ontem</span>
                        </div>
                        <h3 class="font-bold text-slate-900 dark:text-slate-100 text-sm mb-2 hover:text-indigo-600 cursor-pointer">
                            Como organizar as revisões espaçadas no reta final da FUVEST
                        </h3>
                        <p class="text-slate-500 dark:text-slate-400 text-xs line-clamp-3">
                            Professores explicam a técnica das flashcards e revisões periódicas de 24h, 7 dias e 30 dias para evitar o 'curva do esquecimento'.
                        </p>
                    </div>
                    <div class="px-5 py-3 bg-slate-50 dark:bg-slate-700/30 border-t border-slate-100 dark:border-slate-700 flex justify-between items-center text-xs">
                        <span class="text-slate-400">Leitura de 4 min</span>
                        <a href="#" onclick="alert('Abrindo notícia completa...')" class="font-semibold text-indigo-600 dark:text-indigo-400 hover:underline">Ler mais <i class="fa-solid fa-angle-right"></i></a>
                    </div>
                </article>
            </div>
        </section>

    </main>

    <!-- FOOTER -->
    <footer class="mt-12 bg-white dark:bg-slate-800 border-t border-slate-200 dark:border-slate-700 py-8 transition-colors">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex flex-col md:flex-row items-center justify-between gap-4">
            <div class="flex items-center gap-2">
                <div class="w-7 h-7 rounded-lg bg-indigo-600 flex items-center justify-center text-white text-xs font-bold">
                    <i class="fa-solid fa-graduation-cap"></i>
                </div>
                <span class="font-bold text-slate-800 dark:text-slate-100 text-sm">EduCentral Brasil</span>
                <span class="text-xs text-slate-400">© 2026 Todos os direitos reservados.</span>
            </div>
            <div class="flex items-center gap-6 text-xs text-slate-500 dark:text-slate-400">
                <a href="#" class="hover:text-indigo-600 transition">Termos de Uso</a>
                <a href="#" class="hover:text-indigo-600 transition">Privacidade</a>
                <a href="#" class="hover:text-indigo-600 transition">Central de Ajuda</a>
                <a href="#" class="hover:text-indigo-600 transition">Contato</a>
            </div>
        </div>
    </footer>

    <!-- INTERACTIVE MODAL FOR EXAM DETAILS -->
    <div id="examModal" class="fixed inset-0 z-50 bg-slate-900/60 backdrop-blur-sm hidden flex items-center justify-center p-4 transition-opacity duration-300">
        <div class="bg-white dark:bg-slate-800 rounded-2xl max-w-2xl w-full p-6 shadow-2xl border border-slate-200 dark:border-slate-700 relative max-h-[90vh] overflow-y-auto">
            <!-- Close Button -->
            <button onclick="closeExamModal()" class="absolute top-4 right-4 text-slate-400 hover:text-slate-600 dark:hover:text-slate-200 p-2 rounded-lg transition">
                <i class="fa-solid fa-xmark text-lg"></i>
            </button>

            <!-- Dynamic Modal Content -->
            <div id="modalContent">
                <!-- Loaded via JS -->
            </div>
        </div>
    </div>

    <!-- JAVASCRIPT LOGIC -->
    <script>
        // --- DATA STORE ---
        const examsData = [
            {
                id: 'enem',
                title: 'ENEM 2026',
                subtitle: 'Exame Nacional do Ensino Médio',
                type: 'vestibular',
                status: 'Inscrições Abertas',
                statusColor: 'bg-emerald-100 text-emerald-800 dark:bg-emerald-900/40 dark:text-emerald-300',
                deadline: '28 de Outubro, 2026',
                examDate: '08 e 15 de Novembro, 2026',
                fee: 'R$ 85,00 (Isenção disponível)',
                slots: 'Nacional (Sisu/ProUni/ FIES)',
                organizer: 'INEP',
                description: 'A principal porta de entrada para universidades públicas e privadas em todo o Brasil. Avaliação dividida em dois domingos com Linguagens, Ciências Humanas, Exatas, Natureza e Redação.'
            },
            {
                id: 'fuvest',
                title: 'FUVEST 2027',
                subtitle: 'Universidade de São Paulo (USP)',
                type: 'vestibular',
                status: 'Edital Publicado',
                statusColor: 'bg-blue-100 text-blue-800 dark:bg-blue-900/40 dark:text-blue-300',
                deadline: '15 de Novembro, 2026',
                examDate: '1ª Fase: 10/12/2026',
                fee: 'R$ 191,00',
                slots: '8.147 vagas',
                organizer: 'Fundação FUVEST',
                description: 'Vestibular tradicional para ingresso na Universidade de São Paulo (USP). Prova de 1ª fase com 90 questões de múltipla escolha e 2ª fase com questões dissertativas + Redação.'
            },
            {
                id: 'caixa',
                title: 'Concurso Caixa Econômica',
                subtitle: 'Técnico Bancário & TI',
                type: 'concurso',
                status: 'Inscrições Abertas',
                statusColor: 'bg-emerald-100 text-emerald-800 dark:bg-emerald-900/40 dark:text-emerald-300',
                deadline: '05 de Novembro, 2026',
                examDate: '14 de Dezembro, 2026',
                fee: 'R$ 50,00',
                slots: '4.000 Vagas (Nível Médio)',
                salary: 'R$ 3.762,00 + Benefícios',
                organizer: 'Cesgranrio',
                description: 'Concurso público de âmbito nacional para cargos de nível médio. Excelente oportunidade com benefícios de vale-alimentação, plano de saúde e previdência.'
            },
            {
                id: 'unicamp',
                title: 'UNICAMP 2027',
                subtitle: 'Universidade Estadual de Campinas',
                type: 'vestibular',
                status: 'Em Breve',
                statusColor: 'bg-amber-100 text-amber-800 dark:bg-amber-900/40 dark:text-amber-300',
                deadline: 'A definir',
                examDate: '22 de Novembro, 2026',
                fee: 'R$ 192,00',
                slots: '2.540 vagas',
                organizer: 'COMVEST',
                description: 'Processo seletivo reconhecido pela inovação e interdisciplinaridade de suas questões. Avaliação em duas fases presenciais.'
            },
            {
                id: 'prmg',
                title: 'Processo Seletivo PRF (Estágio)',
                subtitle: 'Polícia Rodoviária Federal',
                type: 'processo',
                status: 'Inscrições Abertas',
                statusColor: 'bg-emerald-100 text-emerald-800 dark:bg-emerald-900/40 dark:text-emerald-300',
                deadline: '12 de Novembro, 2026',
                examDate: 'Avaliação Curricular / Prova On-line',
                fee: 'Gratuito',
                slots: '150 Vagas',
                salary: 'Bolsa de R$ 1.125,69',
                organizer: 'CIEE',
                description: 'Seleção simplificada para estudantes do ensino superior das áreas de Direito, Administração, TI e Comunicação.'
            },
            {
                id: 'unesp',
                title: 'UNESP 2027',
                subtitle: 'Universidade Estadual Paulista',
                type: 'vestibular',
                status: 'Edital Publicado',
                statusColor: 'bg-blue-100 text-blue-800 dark:bg-blue-900/40 dark:text-blue-300',
                deadline: '20 de Novembro, 2026',
                examDate: '15 de Dezembro, 2026',
                fee: 'R$ 192,00',
                slots: '6.596 vagas',
                organizer: 'Vunesp',
                description: 'Vestibular unificado para os diversos campi da UNESP espalhados pelo estado de São Paulo. Prova objetiva e dissertativa.'
            }
        ];

        let initialTasks = [
            { id: 1, text: 'Revisar Redação - Modelo ENEM (Introdução e Proposta de Intervenção)', completed: true },
            { id: 2, text: 'Resolver 30 questões de Matemática (Funções de 2º Grau)', completed: false },
            { id: 3, text: 'Assistir videoaula de História do Brasil: Era Vargas', completed: false },
            { id: 4, text: 'Simulado de Física - FUVEST 1ª Fase', completed: false }
        ];

        let currentFilter = 'todos';

        // --- DOM RENDER FUNCTIONS ---

        // Render Exam Listings
        function renderExams(data) {
            const grid = document.getElementById('examGrid');
            grid.innerHTML = '';

            if (data.length === 0) {
                grid.innerHTML = `
                    <div class="col-span-full py-12 text-center text-slate-400">
                        <i class="fa-solid fa-magnifying-glass text-3xl mb-2"></i>
                        <p>Nenhuma prova ou concurso encontrado com os critérios digitados.</p>
                    </div>
                `;
                return;
            }

            data.forEach(exam => {
                const card = document.createElement('div');
                card.className = "bg-white dark:bg-slate-800 rounded-2xl border border-slate-200 dark:border-slate-700 p-5 shadow-sm hover:shadow-md transition flex flex-col justify-between";
                
                card.innerHTML = `
                    <div>
                        <div class="flex items-center justify-between gap-2 mb-3">
                            <span class="px-2.5 py-1 rounded-full text-[11px] font-bold ${exam.statusColor}">
                                ${exam.status}
                            </span>
                            <span class="text-[11px] text-slate-400 font-medium uppercase tracking-wider">${exam.organizer}</span>
                        </div>

                        <h3 class="text-base font-bold text-slate-900 dark:text-slate-100">${exam.title}</h3>
                        <p class="text-xs text-slate-500 dark:text-slate-400 mt-0.5 mb-4">${exam.subtitle}</p>

                        <div class="space-y-2 text-xs text-slate-600 dark:text-slate-300">
                            <div class="flex items-center gap-2">
                                <i class="fa-regular fa-clock w-4 text-indigo-500"></i>
                                <span>Inscrições até: <strong>${exam.deadline}</strong></span>
                            </div>
                            <div class="flex items-center gap-2">
                                <i class="fa-regular fa-calendar-check w-4 text-emerald-500"></i>
                                <span>Data da Prova: <strong>${exam.examDate}</strong></span>
                            </div>
                            ${exam.salary ? `
                            <div class="flex items-center gap-2">
                                <i class="fa-solid fa-sack-dollar w-4 text-amber-500"></i>
                                <span>Remuneração: <strong class="text-emerald-600 dark:text-emerald-400">${exam.salary}</strong></span>
                            </div>` : ''}
                        </div>
                    </div>

                    <div class="mt-5 pt-4 border-t border-slate-100 dark:border-slate-700/60 flex items-center justify-between">
                        <span class="text-[11px] text-slate-400 font-medium">${exam.slots}</span>
                        <button onclick="openExamModal('${exam.id}')" class="px-3 py-1.5 rounded-lg bg-indigo-50 dark:bg-indigo-900/30 hover:bg-indigo-600 hover:text-white dark:hover:bg-indigo-600 text-indigo-600 dark:text-indigo-300 text-xs font-semibold transition">
                            Ver Detalhes
                        </button>
                    </div>
                `;
                grid.appendChild(card);
            });
        }

        // Filter Categories
        function filterCategory(category) {
            currentFilter = category;
            
            // Update active tab visual
            document.querySelectorAll('.filter-tab').forEach(tab => {
                if (tab.dataset.tab === category) {
                    tab.classList.add('bg-white', 'dark:bg-slate-700', 'shadow-sm', 'text-indigo-600', 'dark:text-indigo-400');
                    tab.classList.remove('text-slate-600', 'dark:text-slate-400');
                } else {
                    tab.classList.remove('bg-white', 'dark:bg-slate-700', 'shadow-sm', 'text-indigo-600', 'dark:text-indigo-400');
                    tab.classList.add('text-slate-600', 'dark:text-slate-400');
                }
            });

            const filtered = category === 'todos' 
                ? examsData 
                : examsData.filter(item => item.type === category);

            renderExams(filtered);
        }

        // Live Search Filter
        function filterExamsBySearch() {
            const query = document.getElementById('searchInput').value.toLowerCase();
            const filtered = examsData.filter(item => {
                const matchesCategory = currentFilter === 'todos' || item.type === currentFilter;
                const matchesSearch = item.title.toLowerCase().includes(query) ||
                                      item.subtitle.toLowerCase().includes(query) ||
                                      item.organizer.toLowerCase().includes(query);
                return matchesCategory && matchesSearch;
            });
            renderExams(filtered);
        }

        // --- TASK LIST / CHECKLIST LOGIC ---

        function renderTasks() {
            const listContainer = document.getElementById('taskList');
            listContainer.innerHTML = '';

            let completedCount = 0;

            initialTasks.forEach(task => {
                if (task.completed) completedCount++;

                const item = document.createElement('div');
                item.className = `flex items-center justify-between p-3 rounded-xl border transition ${
                    task.completed 
                        ? 'bg-slate-50 dark:bg-slate-700/20 border-slate-100 dark:border-slate-800 text-slate-400 dark:text-slate-500' 
                        : 'bg-white dark:bg-slate-700/50 border-slate-200 dark:border-slate-600 text-slate-800 dark:text-slate-100'
                }`;

                item.innerHTML = `
                    <label class="flex items-center gap-3 flex-1 cursor-pointer select-none">
                        <input type="checkbox" ${task.completed ? 'checked' : ''} onchange="toggleTask(${task.id})" class="w-4 h-4 rounded text-indigo-600 focus:ring-indigo-500 accent-indigo-600 cursor-pointer">
                        <span class="text-xs font-medium ${task.completed ? 'line-through' : ''}">${task.text}</span>
                    </label>
                    <button onclick="deleteTask(${task.id})" class="text-slate-400 hover:text-red-500 p-1 text-xs transition">
                        <i class="fa-solid fa-trash-can"></i>
                    </button>
                `;
                listContainer.appendChild(item);
            });

            // Update Progress UI
            const total = initialTasks.length;
            const percentage = total === 0 ? 0 : Math.round((completedCount / total) * 100);
            
            document.getElementById('taskCounter').innerText = `${completedCount}/${total} Concluídas`;
            document.getElementById('taskProgressBar').style.width = `${percentage}%`;
        }

        function addNewTask(e) {
            e.preventDefault();
            const input = document.getElementById('newTaskInput');
            const text = input.value.trim();
            
            if (text) {
                initialTasks.push({
                    id: Date.now(),
                    text: text,
                    completed: false
                });
                input.value = '';
                renderTasks();
            }
        }

        function toggleTask(id) {
            initialTasks = initialTasks.map(t => t.id === id ? { ...t, completed: !t.completed } : t);
            renderTasks();
        }

        function deleteTask(id) {
            initialTasks = initialTasks.filter(t => t.id !== id);
            renderTasks();
        }

        function clearCompletedTasks() {
            initialTasks = initialTasks.filter(t => !t.completed);
            renderTasks();
        }

        // --- MODAL HANDLERS ---

        function openExamModal(id) {
            const exam = examsData.find(e => e.id === id);
            if (!exam) return;

            const modalContent = document.getElementById('modalContent');
            modalContent.innerHTML = `
                <div class="space-y-4">
                    <div class="flex items-center gap-2">
                        <span class="px-2.5 py-1 rounded-full text-xs font-bold ${exam.statusColor}">${exam.status}</span>
                        <span class="text-xs text-slate-400 font-medium">Banca: ${exam.organizer}</span>
                    </div>

                    <div>
                        <h2 class="text-xl font-bold text-slate-900 dark:text-slate-100">${exam.title}</h2>
                        <p class="text-sm text-slate-500 dark:text-slate-400">${exam.subtitle}</p>
                    </div>

                    <p class="text-xs sm:text-sm text-slate-600 dark:text-slate-300 leading-relaxed bg-slate-50 dark:bg-slate-700/40 p-4 rounded-xl border border-slate-100 dark:border-slate-700">
                        ${exam.description}
                    </p>

                    <!-- Details Grid -->
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-3 text-xs">
                        <div class="p-3 bg-slate-50 dark:bg-slate-700/30 rounded-xl border border-slate-100 dark:border-slate-700">
                            <span class="text-slate-400 block font-medium">Inscrições</span>
                            <strong class="text-slate-800 dark:text-slate-200 text-sm">${exam.deadline}</strong>
                        </div>
                        <div class="p-3 bg-slate-50 dark:bg-slate-700/30 rounded-xl border border-slate-100 dark:border-slate-700">
                            <span class="text-slate-400 block font-medium">Data das Provas</span>
                            <strong class="text-slate-800 dark:text-slate-200 text-sm">${exam.examDate}</strong>
                        </div>
                        <div class="p-3 bg-slate-50 dark:bg-slate-700/30 rounded-xl border border-slate-100 dark:border-slate-700">
                            <span class="text-slate-400 block font-medium">Taxa de Inscrição</span>
                            <strong class="text-slate-800 dark:text-slate-200 text-sm">${exam.fee}</strong>
                        </div>
                        <div class="p-3 bg-slate-50 dark:bg-slate-700/30 rounded-xl border border-slate-100 dark:border-slate-700">
                            <span class="text-slate-400 block font-medium">Vagas / Abrangência</span>
                            <strong class="text-slate-800 dark:text-slate-200 text-sm">${exam.slots}</strong>
                        </div>
                    </div>

                    <!-- CTA Actions -->
                    <div class="pt-4 flex flex-col sm:flex-row gap-2 justify-end">
                        <button onclick="closeExamModal()" class="px-4 py-2.5 rounded-xl border border-slate-200 dark:border-slate-600 text-xs font-semibold text-slate-600 dark:text-slate-300 hover:bg-slate-100 dark:hover:bg-slate-700 transition">
                            Fechar
                        </button>
                        <a href="#" onclick="alert('Redirecionando para a página oficial do edital...')" class="px-5 py-2.5 rounded-xl bg-indigo-600 hover:bg-indigo-700 text-white text-xs font-semibold transition text-center shadow-md shadow-indigo-500/20">
                            Acessar Página do Edital <i class="fa-solid fa-arrow-up-right-from-square ml-1"></i>
                        </a>
                    </div>
                </div>
            `;

            const modal = document.getElementById('examModal');
            modal.classList.remove('hidden');
        }

        function closeExamModal() {
            document.getElementById('examModal').classList.add('hidden');
        }

        // Close Modal on Outside Click
        document.getElementById('examModal').addEventListener('click', function(e) {
            if (e.target === this) {
                closeExamModal();
            }
        });

        // --- DARK MODE TOGGLE ---
        function toggleDarkMode() {
            const html = document.documentElement;
            if (html.classList.contains('dark')) {
                html.classList.remove('dark');
                localStorage.setItem('theme', 'light');
            } else {
                html.classList.add('dark');
                localStorage.setItem('theme', 'dark');
            }
        }

        // --- INITIALIZATION & TIMER ---
        window.onload = function() {
            // Check system preference or stored theme
            if (localStorage.getItem('theme') === 'dark' || (!('theme' in localStorage) && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
                document.documentElement.classList.add('dark');
            } else {
                document.documentElement.classList.remove('dark');
            }

            // Render components
            filterCategory('todos');
            renderTasks();

            // Simple Countdown Mock Decrement
            setInterval(() => {
                const secs = document.getElementById('timer-secs');
                if (secs) {
                    let current = parseInt(secs.innerText);
                    if (current > 0) {
                        secs.innerText = (current - 1).toString().padStart(2, '0');
                    } else {
                        secs.innerText = '59';
                    }
                }
            }, 1000);
        };
    </script>
</body>
</html>
