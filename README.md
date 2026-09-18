<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>สื่อการสอนสังคมศึกษา 5 สาระ - Rainbow Neon Edition</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Prompt & Sarabun -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Prompt:wght@300;400;500;600;700;800;900&family=Sarabun:wght@400;500;600;700&display=swap" rel="stylesheet">
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Prompt', 'Sarabun', 'sans-serif'],
                    },
                    colors: {
                        'neon-pink': '#FF2A85',
                        'neon-purple': '#9B51E0',
                        'neon-blue': '#00F0FF',
                        'neon-green': '#10B981',
                        'neon-lime': '#76E000',
                        'neon-yellow': '#FFD600',
                        'neon-orange': '#FF6B00',
                        'neon-red': '#FF2E55',
                        'pop-bg': '#FFFDF0',
                    },
                    boxShadow: {
                        'pop': '4px 4px 0px 0px #000000',
                        'pop-lg': '8px 8px 0px 0px #000000',
                        'pop-xl': '12px 12px 0px 0px #000000',
                        'neon-pink': '0px 0px 20px rgba(255, 42, 133, 0.6)',
                        'neon-blue': '0px 0px 20px rgba(0, 240, 255, 0.6)',
                        'neon-yellow': '0px 0px 20px rgba(255, 214, 0, 0.6)',
                    }
                }
            }
        }
    </script>
    
    <style>
        body {
            font-family: 'Prompt', sans-serif;
            background-color: #FFFDF0;
            background-image: radial-gradient(#FFD600 1.5px, transparent 1.5px), radial-gradient(#FF2A85 1.5px, #FFFDF0 1.5px);
            background-size: 60px 60px;
            background-position: 0 0, 30px 30px;
        }

        .brutal-border {
            border: 3.5px solid #000000;
        }

        .brutal-btn {
            border: 3.5px solid #000000;
            box-shadow: 4px 4px 0px 0px #000000;
            transition: all 0.15s ease-in-out;
        }

        .brutal-btn:hover {
            transform: translate(-2px, -2px);
            box-shadow: 6px 6px 0px 0px #000000;
        }

        .brutal-btn:active {
            transform: translate(2px, 2px);
            box-shadow: 2px 2px 0px 0px #000000;
        }

        .brutal-card {
            border: 4px solid #000000;
            box-shadow: 6px 6px 0px 0px #000000;
            transition: all 0.2s ease;
        }

        .brutal-card:hover {
            transform: translateY(-4px);
            box-shadow: 10px 10px 0px 0px #000000;
        }

        #drawingCanvas {
            touch-action: none;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-8px) rotate(1deg); }
        }

        .animate-float {
            animation: float 4s ease-in-out infinite;
        }

        ::-webkit-scrollbar {
            width: 12px;
            height: 12px;
        }
        ::-webkit-scrollbar-track {
            background: #FFE082;
            border-left: 3px solid #000;
        }
        ::-webkit-scrollbar-thumb {
            background: #FF2A85;
            border: 3px solid #000;
            border-radius: 6px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #9B51E0;
        }
    </style>
</head>
<body class="min-h-screen text-slate-900 pb-12 flex flex-col">

    <!-- Header Navbar -->
    <header class="sticky top-0 z-30 bg-yellow-300 brutal-border border-t-0 border-x-0 py-4 px-4 sm:px-8 mb-8 shadow-md">
        <div class="max-w-7xl mx-auto flex flex-col md:flex-row items-center justify-between gap-4">
            
            <!-- Logo & Title -->
            <div class="flex items-center gap-3">
                <div class="w-14 h-14 bg-neon-pink brutal-border rounded-2xl flex items-center justify-center text-white text-2xl font-black shadow-pop animate-float rotate-3">
                    <i class="fa-solid fa-graduation-cap text-yellow-300 text-3xl"></i>
                </div>
                <div>
                    <h1 class="text-2xl sm:text-3xl font-black tracking-tight text-slate-900 drop-shadow-sm">
                        SOCIAL<span class="bg-neon-pink text-white px-2 py-0.5 rounded-lg ml-1 rotate-1 inline-block border-2 border-black shadow-pop">HUB</span>
                    </h1>
                    <p class="text-xs sm:text-sm font-bold text-slate-800">คลังสื่อการสอนสังคมศึกษา 5 สาระ (Rainbow Neon Edition)</p>
                </div>
            </div>

            <!-- Action Controls -->
            <div class="flex flex-wrap items-center justify-center gap-3 w-full md:w-auto">
                <button onclick="openModal()" class="brutal-btn bg-neon-lime hover:bg-lime-400 text-black font-extrabold px-4 py-2.5 rounded-2xl flex items-center gap-2 text-sm sm:text-base">
                    <i class="fa-solid fa-circle-plus text-lg"></i>
                    <span>สร้างสไลด์ใหม่</span>
                </button>

                <button onclick="openImportModal()" class="brutal-btn bg-neon-blue hover:bg-cyan-300 text-black font-extrabold px-4 py-2.5 rounded-2xl flex items-center gap-2 text-sm sm:text-base">
                    <i class="fa-solid fa-file-import text-lg"></i>
                    <span>นำเข้าสไลด์ภายนอก</span>
                </button>

                <button onclick="resetToDefaultData()" class="brutal-btn bg-white hover:bg-slate-100 text-black font-bold px-3 py-2.5 rounded-2xl flex items-center gap-1.5 text-sm" title="รีเซ็ตข้อมูลตัวอย่าง">
                    <i class="fa-solid fa-rotate-left"></i>
                    <span class="hidden sm:inline">รีเซ็ตข้อมูล</span>
                </button>
            </div>
        </div>
    </header>

    <!-- Main Content Container -->
    <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 flex-grow w-full">

        <!-- Top Controls: Search Bar & Subject Badges -->
        <div class="bg-white brutal-card p-6 rounded-3xl mb-8 bg-gradient-to-r from-purple-100 via-pink-100 to-yellow-100">
            <div class="flex flex-col md:flex-row gap-4 justify-between items-center mb-6">
                <!-- Search Input -->
                <div class="relative w-full md:w-96">
                    <i class="fa-solid fa-magnifying-glass absolute left-4 top-1/2 -translate-y-1/2 text-slate-500 text-lg"></i>
                    <input type="text" id="searchInput" oninput="filterDecks()" placeholder="ค้นหาชื่อบทเรียน หรือคำสำคัญ..." 
                        class="w-full pl-12 pr-4 py-3 bg-white brutal-border rounded-2xl font-semibold text-slate-800 focus:outline-none focus:ring-4 focus:ring-neon-pink/50 placeholder-slate-400">
                </div>

                <!-- Category Counters Info -->
                <div class="text-sm font-extrabold bg-black text-white px-4 py-2 rounded-xl shadow-pop flex items-center gap-2">
                    <i class="fa-solid fa-layer-group text-neon-yellow"></i>
                    <span>ทั้งหมด <span id="deckCount" class="text-neon-lime text-base mx-1">0</span> ชุดบทเรียน</span>
                </div>
            </div>

            <!-- Category Filter Tabs -->
            <div class="flex flex-wrap gap-2.5 justify-center md:justify-start" id="filterTabs">
                <!-- Tabs rendered dynamically -->
            </div>
        </div>

        <!-- Grid Display of Slide Decks -->
        <div id="deckGrid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
            <!-- Dynamic Content loaded via JS -->
        </div>

        <!-- Empty State Message -->
        <div id="emptyState" class="hidden text-center py-16 bg-white brutal-card rounded-3xl my-8">
            <div class="w-24 h-24 bg-neon-yellow brutal-border rounded-full flex items-center justify-center mx-auto mb-4 text-4xl shadow-pop">
                <i class="fa-solid fa-ghost"></i>
            </div>
            <h3 class="text-2xl font-black text-slate-800 mb-2">ไม่พบชุดสไลด์สอนที่คุณค้นหา</h3>
            <p class="text-slate-600 font-semibold mb-6">ลองเปลี่ยนคำค้นหา หรือนำเข้าชุดสไลด์ภายนอกมาใช้งานได้!</p>
            <div class="flex justify-center gap-3">
                <button onclick="openModal()" class="brutal-btn bg-neon-pink text-white font-extrabold px-6 py-3 rounded-2xl">
                    <i class="fa-solid fa-plus mr-2"></i>สร้างชุดสไลด์ใหม่
                </button>
                <button onclick="openImportModal()" class="brutal-btn bg-neon-blue text-black font-extrabold px-6 py-3 rounded-2xl">
                    <i class="fa-solid fa-file-import mr-2"></i>นำเข้าสไลด์ภายนอก
                </button>
            </div>
        </div>

    </main>

    <!-- Presentation Mode Fullscreen Modal -->
    <div id="presentationModal" class="fixed inset-0 bg-slate-950/90 backdrop-blur-md z-50 hidden flex-col transition-all duration-300">
        
        <!-- Presentation Navbar Header -->
        <div class="bg-black text-white px-4 py-3 brutal-border border-x-0 border-t-0 flex items-center justify-between z-20">
            <div class="flex items-center gap-3">
                <span id="presSubjectBadge" class="px-3 py-1 rounded-xl text-xs font-black brutal-border">สาระ</span>
                <h2 id="presDeckTitle" class="font-extrabold text-lg sm:text-xl text-white truncate max-w-xs sm:max-w-md">ชื่อบทเรียน</h2>
            </div>
            
            <!-- Controls Toolbar -->
            <div class="flex items-center gap-2">
                <!-- Theme Selector -->
                <div class="hidden sm:flex items-center gap-1.5 bg-slate-800 p-1.5 rounded-xl border border-slate-700">
                    <span class="text-xs font-bold text-slate-300 px-1"><i class="fa-solid fa-palette text-neon-yellow"></i> Theme:</span>
                    <button onclick="changePresBg('bg-white text-slate-900')" class="w-6 h-6 rounded-lg bg-white border border-black hover:scale-110 transition" title="Light"></button>
                    <button onclick="changePresBg('bg-slate-900 text-white')" class="w-6 h-6 rounded-lg bg-slate-900 border border-white hover:scale-110 transition" title="Dark"></button>
                    <button onclick="changePresBg('bg-amber-100 text-amber-950')" class="w-6 h-6 rounded-lg bg-amber-100 border border-amber-900 hover:scale-110 transition" title="Warm Papyrus"></button>
                    <button onclick="changePresBg('bg-pink-100 text-pink-950')" class="w-6 h-6 rounded-lg bg-pink-100 border border-pink-800 hover:scale-110 transition" title="Neon Pink"></button>
                    <button onclick="changePresBg('bg-cyan-100 text-cyan-950')" class="w-6 h-6 rounded-lg bg-cyan-100 border border-cyan-800 hover:scale-110 transition" title="Cyber Cyan"></button>
                </div>

                <!-- Pen Tool Toggle -->
                <button id="penBtn" onclick="togglePenTool()" class="brutal-btn bg-slate-800 text-white hover:bg-neon-pink px-3 py-1.5 rounded-xl text-sm font-bold flex items-center gap-1.5">
                    <i class="fa-solid fa-pen-nib"></i>
                    <span class="hidden md:inline">ปากกาขีดเขียน</span>
                </button>
                
                <button onclick="clearCanvas()" class="brutal-btn bg-slate-800 text-white hover:bg-red-500 p-2 rounded-xl text-sm" title="ลบรอยปากกา">
                    <i class="fa-solid fa-eraser"></i>
                </button>

                <!-- Speaker Notes Toggle -->
                <button id="notesBtn" onclick="toggleSpeakerNotes()" class="brutal-btn bg-slate-800 text-slate-200 hover:bg-neon-yellow hover:text-black px-3 py-1.5 rounded-xl text-sm font-bold flex items-center gap-1.5">
                    <i class="fa-solid fa-note-sticky"></i>
                    <span class="hidden md:inline">บันทึกผู้สอน</span>
                </button>

                <!-- Export Current Deck -->
                <button onclick="exportCurrentActiveDeck()" class="brutal-btn bg-slate-800 text-white hover:bg-neon-blue hover:text-black p-2 rounded-xl text-sm" title="ส่งออกชุดสไลด์นี้เป็น JSON">
                    <i class="fa-solid fa-download"></i>
                </button>

                <button onclick="deleteCurrentDeckFromPres()" class="brutal-btn bg-red-600 hover:bg-red-700 text-white px-3 py-1.5 rounded-xl text-sm font-bold flex items-center gap-1.5" title="ลบชุดสไลด์นี้">
                    <i class="fa-solid fa-trash"></i>
                </button>

                <button onclick="closePresentation()" class="brutal-btn bg-neon-pink text-white hover:bg-pink-600 px-3.5 py-1.5 rounded-xl text-sm font-black ml-2">
                    <i class="fa-solid fa-xmark text-lg"></i>
                </button>
            </div>
        </div>

        <!-- Pen Palette -->
        <div id="penPalette" class="hidden bg-slate-900 border-b border-slate-700 py-2 px-4 flex items-center justify-center gap-3 z-20">
            <span class="text-xs font-bold text-slate-300">สีปากกา:</span>
            <button onclick="setPenColor('#FF2A85')" class="w-6 h-6 rounded-full bg-neon-pink border-2 border-white focus:ring-2 ring-white"></button>
            <button onclick="setPenColor('#00F0FF')" class="w-6 h-6 rounded-full bg-neon-blue border-2 border-white focus:ring-2 ring-white"></button>
            <button onclick="setPenColor('#FFD600')" class="w-6 h-6 rounded-full bg-neon-yellow border-2 border-white focus:ring-2 ring-white"></button>
            <button onclick="setPenColor('#10B981')" class="w-6 h-6 rounded-full bg-emerald-500 border-2 border-white focus:ring-2 ring-white"></button>
            <button onclick="setPenColor('#000000')" class="w-6 h-6 rounded-full bg-black border-2 border-white focus:ring-2 ring-white"></button>
            <div class="h-4 w-px bg-slate-700 mx-1"></div>
            <span class="text-xs font-bold text-slate-300">ขนาด:</span>
            <button onclick="setPenWidth(3)" class="text-xs text-white font-bold bg-slate-700 px-2 py-0.5 rounded">เล็ก</button>
            <button onclick="setPenWidth(6)" class="text-xs text-white font-bold bg-slate-700 px-2 py-0.5 rounded">กลาง</button>
            <button onclick="setPenWidth(12)" class="text-xs text-white font-bold bg-slate-700 px-2 py-0.5 rounded">ใหญ่</button>
        </div>

        <!-- Workspace -->
        <div class="flex-grow relative flex items-center justify-center p-4 sm:p-8 overflow-hidden">
            <div id="presSlideFrame" class="relative w-full max-w-5xl aspect-[16/9] brutal-card rounded-3xl p-6 sm:p-12 flex flex-col justify-between transition-all bg-white text-slate-900 overflow-y-auto shadow-neon-pink">
                <div class="flex justify-between items-center border-b-4 border-black pb-4 mb-4">
                    <span id="presSubtopic" class="text-sm sm:text-base font-black uppercase tracking-wider px-3 py-1 rounded-xl bg-neon-yellow brutal-border">
                        หัวข้อย่อย
                    </span>
                    <span id="presSlideCounter" class="text-sm sm:text-base font-black bg-black text-white px-3 py-1 rounded-xl">
                        1 / 5
                    </span>
                </div>

                <div class="my-auto py-4">
                    <h2 id="presSlideTitle" class="text-2xl sm:text-4xl lg:text-5xl font-black mb-6 leading-tight tracking-tight text-slate-900">
                        หัวข้อสไลด์
                    </h2>
                    <div id="presSlideBody" class="text-base sm:text-xl lg:text-2xl font-medium leading-relaxed text-slate-800 whitespace-pre-line">
                        เนื้อหาบทเรียน...
                    </div>
                </div>

                <div class="pt-4 border-t-2 border-slate-200 flex justify-between items-center text-xs sm:text-sm font-bold text-slate-500">
                    <span id="presDeckFooter"><i class="fa-solid fa-book-open mr-1"></i> สื่อการสอนสังคมศึกษา</span>
                    <span>กด <kbd class="px-2 py-1 bg-slate-200 border border-slate-400 rounded text-black font-black">←</kbd> <kbd class="px-2 py-1 bg-slate-200 border border-slate-400 rounded text-black font-black">→</kbd> เพื่อเปลี่ยนสไลด์</span>
                </div>

                <canvas id="drawingCanvas" class="absolute inset-0 w-full h-full pointer-events-none rounded-3xl z-10"></canvas>
            </div>

            <button onclick="prevSlide()" class="absolute left-2 sm:left-6 top-1/2 -translate-y-1/2 brutal-btn bg-neon-yellow hover:bg-yellow-400 text-black w-12 h-12 sm:w-16 sm:h-16 rounded-full flex items-center justify-center text-2xl z-20">
                <i class="fa-solid fa-chevron-left"></i>
            </button>
            <button onclick="nextSlide()" class="absolute right-2 sm:right-6 top-1/2 -translate-y-1/2 brutal-btn bg-neon-yellow hover:bg-yellow-400 text-black w-12 h-12 sm:w-16 sm:h-16 rounded-full flex items-center justify-center text-2xl z-20">
                <i class="fa-solid fa-chevron-right"></i>
            </button>

            <div id="speakerNotesPanel" class="hidden absolute bottom-4 left-1/2 -translate-x-1/2 w-11/12 max-w-3xl bg-black text-white brutal-border p-4 rounded-2xl z-30 shadow-2xl">
                <div class="flex items-center justify-between mb-2 pb-2 border-b border-slate-700">
                    <span class="text-sm font-black text-neon-yellow flex items-center gap-2">
                        <i class="fa-solid fa-user-tie"></i> บันทึกสำหรับผู้สอน (Teacher Notes)
                    </span>
                    <button onclick="toggleSpeakerNotes()" class="text-slate-400 hover:text-white">
                        <i class="fa-solid fa-xmark"></i>
                    </button>
                </div>
                <p id="presSpeakerNotes" class="text-sm sm:text-base font-medium text-slate-200">
                    ไม่มีบันทึกเพิ่มเติมสำหรับสไลด์นี้
                </p>
            </div>

        </div>

        <div class="w-full bg-slate-900 h-3 brutal-border border-x-0 border-b-0 relative">
            <div id="slideProgressBar" class="bg-neon-pink h-full transition-all duration-300 w-0"></div>
        </div>

    </div>

    <!-- External Slide Import Modal -->
    <div id="importModal" class="fixed inset-0 bg-black/80 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4 overflow-y-auto">
        <div class="bg-white brutal-card rounded-3xl w-full max-w-2xl my-8 p-6 sm:p-8">
            <div class="flex justify-between items-center pb-4 mb-6 border-b-4 border-black">
                <h3 class="text-2xl font-black text-slate-900 flex items-center gap-2">
                    <i class="fa-solid fa-file-import text-neon-blue"></i> นำเข้าสไลด์จากภายนอก
                </h3>
                <button onclick="closeImportModal()" class="w-10 h-10 bg-slate-100 hover:bg-slate-200 brutal-border rounded-xl flex items-center justify-center text-slate-700">
                    <i class="fa-solid fa-xmark text-xl"></i>
                </button>
            </div>

            <!-- Import Tabs -->
            <div class="flex gap-2 mb-6 border-b-2 border-black pb-3">
                <button id="importTabFileBtn" onclick="switchImportTab('file')" class="brutal-btn bg-black text-white px-4 py-2 rounded-xl font-black text-xs sm:text-sm">
                    <i class="fa-solid fa-file-arrow-up mr-1.5"></i> เลือกไฟล์ (JSON / TXT)
                </button>
                <button id="importTabTextBtn" onclick="switchImportTab('text')" class="brutal-btn bg-white text-black px-4 py-2 rounded-xl font-black text-xs sm:text-sm">
                    <i class="fa-solid fa-paste mr-1.5"></i> วางเค้าโครงข้อความ
                </button>
            </div>

            <!-- Tab 1: File Upload -->
            <div id="importTabFile" class="space-y-4">
                <div class="border-4 border-dashed border-black rounded-3xl p-8 text-center bg-yellow-50 hover:bg-yellow-100 transition cursor-pointer" onclick="document.getElementById('fileInput').click()">
                    <div class="w-16 h-16 bg-neon-blue brutal-border rounded-full flex items-center justify-center mx-auto mb-3 text-2xl shadow-pop">
                        <i class="fa-solid fa-cloud-arrow-up text-black"></i>
                    </div>
                    <h4 class="text-lg font-black text-slate-900">คลิกเพื่อเลือกไฟล์ หรือลากไฟล์มาวางที่นี่</h4>
                    <p class="text-xs font-bold text-slate-600 mt-1">รองรับไฟล์ `.json` (ไฟล์ชุดสไลด์) และไฟล์ `.txt` (ข้อความเค้าโครง)</p>
                    <input type="file" id="fileInput" accept=".json,.txt" onchange="handleFileSelect(event)" class="hidden">
                </div>

                <div class="bg-blue-50 brutal-border p-4 rounded-2xl text-xs font-bold text-slate-800">
                    <i class="fa-solid fa-circle-info text-neon-blue text-sm mr-1"></i>
                    ท่านสามารถส่งออก (Export) สไลด์จากเครื่องเดิมเพื่อนำไฟล์ JSON มานำเข้าใช้งานต่อที่เครื่องนี้ได้ทันที!
                </div>
            </div>

            <!-- Tab 2: Text / Outline Paste -->
            <div id="importTabText" class="hidden space-y-4">
                <div>
                    <label class="block text-sm font-black text-slate-800 mb-2">เลือกสาระการเรียนรู้เป้าหมาย *</label>
                    <select id="importSubjectSelect" class="w-full px-4 py-2.5 bg-slate-50 brutal-border rounded-xl font-bold">
                        <option value="history">1. ประวัติศาสตร์</option>
                        <option value="geography">2. ภูมิศาสตร์</option>
                        <option value="economics">3. เศรษฐศาสตร์</option>
                        <option value="civics">4. หน้าที่พลเมือง</option>
                        <option value="religion">5. ศาสนาและวัฒนธรรม</option>
                    </select>
                </div>

                <div>
                    <label class="block text-sm font-black text-slate-800 mb-2">วางเค้าโครงข้อความบทเรียน</label>
                    <textarea id="importTextOutline" class="w-full h-48 px-4 py-3 bg-slate-50 brutal-border rounded-xl font-medium text-xs leading-relaxed" placeholder="ตัวอย่างรูปแบบข้อความ:
# ชื่อบทเรียน: ประวัติศาสตร์ไทยน่ารู้
[หัวข้อย่อย] การสถาปนากรุงธนบุรี
- หัวข้อสไลด์: พระเจ้าตากสินมหาราช
- เนื้อหา: ทรงกอบกู้เอกราชพ.ศ. 2310 และสถาปนากรุงธนบุรีเป็นราชธานี
[Notes: เน้นย้ำยุทธศาสตร์ค่ายโพธิ์สามต้น]

--- (แบ่งสไลด์)
[หัวข้อย่อย] ภูมิปัญญาธนบุรี
- หัวข้อสไลด์: การทำมาหากินของชาวธนบุรี
- เนื้อหา: การทำสวนผลไม้ และการค้าทางเรือ"></textarea>
                </div>

                <button onclick="processTextImport()" class="w-full brutal-btn bg-neon-lime hover:bg-lime-400 text-black font-black py-3 rounded-2xl text-sm flex items-center justify-center gap-2">
                    <i class="fa-solid fa-wand-magic-sparkles"></i> แปลงข้อความและสร้างชุดสไลด์
                </button>
            </div>

            <div class="flex justify-end pt-4 border-t-2 border-slate-200 mt-6">
                <button onclick="closeImportModal()" class="brutal-btn bg-slate-200 hover:bg-slate-300 text-slate-800 font-bold px-5 py-2.5 rounded-xl text-sm">
                    ยกเลิก
                </button>
            </div>
        </div>
    </div>

    <!-- Quick Text Import Modal inside Slide Creation -->
    <div id="quickTextImportModal" class="fixed inset-0 bg-black/80 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4">
        <div class="bg-white brutal-card rounded-3xl w-full max-w-xl p-6">
            <h3 class="text-xl font-black mb-3 text-slate-900 flex items-center gap-2">
                <i class="fa-solid fa-bolt text-neon-yellow"></i> นำเข้าข้อความสไลด์แบบรวดเร็ว
            </h3>
            <p class="text-xs font-bold text-slate-600 mb-4">วางข้อความของคุณโดยเว้นบรรทัด บรรทัดแรกจะเป็นชื่อหัวข้อ บรรทัดต่อๆ ไปจะเป็นเนื้อหา</p>
            
            <textarea id="quickImportText" class="w-full h-40 px-3 py-2 bg-slate-50 brutal-border rounded-xl text-xs font-medium mb-4" placeholder="ชื่อหัวข้อสไลด์ที่ 1
• เนื้อหาบรรทัดที่ 1
• เนื้อหาบรรทัดที่ 2

---

ชื่อหัวข้อสไลด์ที่ 2
• เนื้อหาบรรทัดที่ 1"></textarea>

            <div class="flex justify-end gap-2">
                <button onclick="closeQuickTextImport()" class="brutal-btn bg-slate-200 px-4 py-2 rounded-xl text-xs font-bold">ยกเลิก</button>
                <button onclick="applyQuickTextImport()" class="brutal-btn bg-neon-lime px-4 py-2 rounded-xl text-xs font-black">แทรกสไลด์เหล่านี้</button>
            </div>
        </div>
    </div>

    <!-- Add / Edit Slide Deck Modal -->
    <div id="deckModal" class="fixed inset-0 bg-black/70 backdrop-blur-sm z-50 hidden flex items-center justify-center p-4 overflow-y-auto">
        <div class="bg-white brutal-card rounded-3xl w-full max-w-3xl my-8 p-6 sm:p-8 max-h-[90vh] overflow-y-auto">
            
            <div class="flex justify-between items-center pb-4 mb-6 border-b-4 border-black">
                <h3 id="modalTitle" class="text-2xl font-black text-slate-900 flex items-center gap-2">
                    <i class="fa-solid fa-folder-plus text-neon-pink"></i> สร้างชุดสไลด์สอนใหม่
                </h3>
                <button onclick="closeModal()" class="w-10 h-10 bg-slate-100 hover:bg-slate-200 brutal-border rounded-xl flex items-center justify-center text-slate-700">
                    <i class="fa-solid fa-xmark text-xl"></i>
                </button>
            </div>

            <form id="deckForm" onsubmit="handleDeckFormSubmit(event)" class="space-y-6">
                <input type="hidden" id="editDeckId" value="">

                <!-- Title & Subject Row -->
                <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                    <div class="md:col-span-2">
                        <label class="block text-sm font-black text-slate-800 mb-2">ชื่อชุดสไลด์ / บทเรียน *</label>
                        <input type="text" id="deckTitleInput" required placeholder="เช่น ประวัติศาสตร์สุโขทัยน่ารู้" 
                            class="w-full px-4 py-3 bg-slate-50 brutal-border rounded-xl font-semibold focus:outline-none focus:bg-yellow-50">
                    </div>

                    <div>
                        <label class="block text-sm font-black text-slate-800 mb-2">สาระการเรียนรู้ *</label>
                        <select id="deckSubjectSelect" required onchange="updateCardColorPreview()"
                            class="w-full px-4 py-3 bg-slate-50 brutal-border rounded-xl font-bold focus:outline-none focus:bg-yellow-50">
                            <option value="history">1. ประวัติศาสตร์</option>
                            <option value="geography">2. ภูมิศาสตร์</option>
                            <option value="economics">3. เศรษฐศาสตร์</option>
                            <option value="civics">4. หน้าที่พลเมือง</option>
                            <option value="religion">5. ศาสนาและวัฒนธรรม</option>
                        </select>
                    </div>
                </div>

                <!-- Author & Subtopic -->
                <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                    <div>
                        <label class="block text-sm font-black text-slate-800 mb-2">ชื่อผู้สอน / ผู้แต่ง</label>
                        <input type="text" id="deckAuthorInput" placeholder="ครูผู้สอน..." 
                            class="w-full px-4 py-3 bg-slate-50 brutal-border rounded-xl font-semibold">
                    </div>
                    <div>
                        <label class="block text-sm font-black text-slate-800 mb-2">ระดับชั้น / คำโปรย</label>
                        <input type="text" id="deckTagInput" placeholder="เช่น ชั้นมัธยมศึกษาปีที่ 1" 
                            class="w-full px-4 py-3 bg-slate-50 brutal-border rounded-xl font-semibold">
                    </div>
                </div>

                <!-- Color Style Preview Badge -->
                <div class="p-4 rounded-2xl brutal-border bg-slate-100 flex items-center justify-between">
                    <span class="text-sm font-black text-slate-700">โทนสีประจำสาระ (อัตโนมัติ):</span>
                    <span id="subjectThemeBadge" class="px-4 py-1.5 rounded-xl font-black text-sm brutal-border shadow-pop">
                        ตัวอย่างสีการ์ด
                    </span>
                </div>

                <!-- Dynamic Slides Builder Section -->
                <div>
                    <div class="flex flex-wrap justify-between items-center mb-3 gap-2">
                        <label class="text-base font-black text-slate-900">รายการหน้าสไลด์ (<span id="slideCountLabel">0</span> หน้า)</label>
                        <div class="flex gap-2">
                            <button type="button" onclick="openQuickTextImport()" class="brutal-btn bg-neon-blue hover:bg-cyan-300 text-black font-extrabold px-3 py-1.5 rounded-xl text-xs flex items-center gap-1">
                                <i class="fa-solid fa-paste"></i> นำเข้าข้อความด่วน
                            </button>
                            <button type="button" onclick="addSlideInputRow()" class="brutal-btn bg-neon-yellow hover:bg-yellow-400 text-black font-extrabold px-3 py-1.5 rounded-xl text-xs flex items-center gap-1">
                                <i class="fa-solid fa-plus"></i> เพิ่มหน้าสไลด์
                            </button>
                        </div>
                    </div>

                    <div id="slidesContainer" class="space-y-4 max-h-80 overflow-y-auto pr-2">
                        <!-- Slide Rows Generated via JS -->
                    </div>
                </div>

                <!-- Form Submit Actions -->
                <div class="flex justify-end gap-3 pt-4 border-t-2 border-slate-200">
                    <button type="button" onclick="closeModal()" class="brutal-btn bg-slate-200 hover:bg-slate-300 text-slate-800 font-bold px-5 py-2.5 rounded-xl text-sm">
                        ยกเลิก
                    </button>
                    <button type="submit" class="brutal-btn bg-neon-lime hover:bg-lime-400 text-black font-black px-6 py-2.5 rounded-xl text-sm">
                        <i class="fa-solid fa-floppy-disk mr-1"></i> บันทึกชุดสไลด์
                    </button>
                </div>
            </form>

        </div>
    </div>

    <script>
        /* ==========================================================================
           1. DATA STRUCTURES & CONFIGURATION
           ========================================================================== */

        const SUBJECTS = {
            history: {
                id: 'history',
                name: 'ประวัติศาสตร์',
                icon: 'fa-landmark-dome',
                cardBg: 'bg-gradient-to-br from-amber-400 via-orange-500 to-red-500',
                badgeBg: 'bg-orange-500 text-white',
                btnBg: 'bg-orange-400 hover:bg-orange-500',
                accentColor: '#FF6B00',
                desc: 'สีส้มสดอมทอง (Ultra Sunburst Orange & Coral)'
            },
            geography: {
                id: 'geography',
                name: 'ภูมิศาสตร์',
                icon: 'fa-earth-asia',
                cardBg: 'bg-gradient-to-br from-lime-300 via-emerald-400 to-teal-500',
                badgeBg: 'bg-lime-400 text-black',
                btnBg: 'bg-lime-400 hover:bg-lime-500',
                accentColor: '#76E000',
                desc: 'สีเขียวมะนาว/ฟ้าสด (Lime Neon Green & Ocean Turquoise)'
            },
            economics: {
                id: 'economics',
                name: 'เศรษฐศาสตร์',
                icon: 'fa-coins',
                cardBg: 'bg-gradient-to-br from-yellow-300 via-amber-400 to-rose-500',
                badgeBg: 'bg-yellow-400 text-black',
                btnBg: 'bg-yellow-400 hover:bg-yellow-500',
                accentColor: '#FFD600',
                desc: 'สีเหลืองสว่าง/ส้มอมแดง (Bright Electric Yellow & Crimson Flame)'
            },
            civics: {
                id: 'civics',
                name: 'หน้าที่พลเมือง',
                icon: 'fa-scale-balanced',
                cardBg: 'bg-gradient-to-br from-cyan-300 via-blue-500 to-indigo-600',
                badgeBg: 'bg-cyan-400 text-black',
                btnBg: 'bg-cyan-400 hover:bg-cyan-500',
                accentColor: '#00F0FF',
                desc: 'สีฟ้าสด/น้ำเงินนีออน (Electric Sky Blue & Royal Neon)'
            },
            religion: {
                id: 'religion',
                name: 'ศาสนาและวัฒนธรรม',
                icon: 'fa-hands-praying',
                cardBg: 'bg-gradient-to-br from-pink-400 via-fuchsia-500 to-purple-600',
                badgeBg: 'bg-neon-pink text-white',
                btnBg: 'bg-neon-pink hover:bg-pink-600',
                accentColor: '#FF2A85',
                desc: 'สีชมพูนีออน/ม่วงพาสเทล (Ultra Magenta Pink & Violet Glow)'
            }
        };

        const DEFAULT_DECKS = [
            {
                id: 'deck-hist-01',
                subjectKey: 'history',
                title: 'อาณาจักรสุโขทัย: ยุคทองแห่งอารยธรรม',
                author: 'คุณครูสังคมน่ารัก',
                tag: 'ระดับชั้น ม.1',
                slides: [
                    {
                        subtopic: 'การสถาปนาสุโขทัย',
                        title: 'กำเนิดอาณาจักรสุโขทัย',
                        content: '• พ่อขุนบางกลางหาว และ พ่อขุนผาเมือง ร่วมกันขับไล่ "ขอมสบาดโขลญลำพง"\n• พ่อขุนบางกลางหาว ขึ้นครองราชย์เป็น "พ่อขุนศรีอินทราทิตย์" กษัตริย์องค์แรกแห่งราชวงศ์พระร่วง\n• สุโขทัยมีความเจริญรุ่งเรืองสูงสุดในสมัย "พ่อขุนรามคำแหงมหาราช"',
                        notes: 'เน้นย้ำเรื่องความกล้าหาญและความร่วมมือของสองผู้นำไทยในการกอบกู้บ้านเมือง'
                    },
                    {
                        subtopic: 'การเมืองการปกครอง',
                        title: 'รูปแบบการปกครอง "พ่อขุนปกครองลูก"',
                        content: '• ความสัมพันธ์ระหว่างกษัตริย์กับราษฎรเหมือน "พ่อ กับ ลูก"\n• กษัตริย์ทรงใกล้ชิดประชาชน มีการสั่นกระดิ่งร้องเรียนทุกข์หน้าประตูวัง\n• ต่อมาในสมัยธรรมราชา ปรับเปลี่ยนเป็นแบบ "ธรรมราชา" โดยนำหลักธรรมทางพุทธศาสนามาใช้',
                        notes: 'ให้นักเรียนเปรียบเทียบความแตกต่างระหว่างระบบพ่อขุนปกครองลูก กับเทวราชา'
                    },
                    {
                        subtopic: 'ศิลาจารึก & อักษรไทย',
                        title: 'การกำเนิดลายสือไทย (พ.ศ. 1826)',
                        content: '• พ่อขุนรามคำแหงมหาราชทรงประดิษฐ์ "ลายสือไทย"\n• บันทึกเรื่องราวลงในศิลาจารึกหลักที่ 1\n• สะท้อนภาพความสมบูรณ์: "ในน้ำมีปลา ในนามีข้าว ผู้ใดใคร่ค้าช้างค้า ผู้ใดใคร่ค้าม้าค้า"',
                        notes: 'ชวนนักเรียนอ่านข้อความบนศิลาจารึกร่วมกัน และพูดคุยถึงเศรษฐกิจแบบเสรีในยุคนั้น'
                    }
                ]
            },
            {
                id: 'deck-geo-01',
                subjectKey: 'geography',
                title: 'เครื่องมือทางภูมิศาสตร์ & โลกของเรา',
                author: 'ครูภูมิศาสตร์สุดซ่า',
                tag: 'ระดับชั้น ม.2',
                slides: [
                    {
                        subtopic: 'เครื่องมือสำรวจ',
                        title: 'แผนที่ & เทคโนโลยีภูมิสารสนเทศ',
                        content: '1. แผนที่ภูมิประเทศ (Topographic Map) แสดงความสูงต่ำของพื้นที่\n2. GIS (ระบบสารสนเทศภูมิศาสตร์) จัดเก็บและวิเคราะห์ข้อมูลเชิงพื้นที่\n3. GPS (ระบบระบุตำแหน่งบนโลก) ใช้ดาวเทียมระบุพิกัดความแม่นยำสูง\n4. Remote Sensing (การรับรู้จากระยะไกล) ภาพถ่ายดาวเทียมและภาพถ่ายทางอากาศ',
                        notes: 'ให้นักเรียนเปิดแอป Google Maps หรือ Google Earth บนมือถือเพื่อทดลองระบุพิกัด'
                    },
                    {
                        subtopic: 'พิกัดภูมิศาสตร์',
                        title: 'ละติจูด (Latitude) & ลองจิจูด (Longitude)',
                        content: '• ละติจูด (เส้นรุ้ง): วัดขนานกับเส้นศูนย์สูตร บอก "เขตภูมิอากาศ" (ร้อน อบอุ่น หนาว)\n• ลองจิจูด (เส้นแวง): เส้นเมริเดียนเชื่อมขั้วโลก บอก "เวลาสากล" (ทุก 15 องศา = 1 ชั่วโมง)',
                        notes: 'เทคนิคท่องจำง่ายๆ: "รุ้งตะแคง (ละติจูด) แวงตั้ง (ลองจิจูด)"'
                    },
                    {
                        subtopic: 'ปรากฏการณ์ธรรมชาติ',
                        title: 'การเกิดฤดูกาล & แผ่นดินไหว',
                        content: '• แกนโลกเอียง 23.5 องศา โคจรรอบดวงอาทิตย์ ทำให้เกิด "ฤดูกาล"\n• การเคลื่อนที่ของแผ่นเปลือกโลก (Tectonic Plates) ก่อให้เกิดแผ่นดินไหวและภูเขาไฟระเบิด\n• วงแหวนแห่งไฟ (Ring of Fire) บริเวณรอบมหาสมุทรแปซิฟิกที่มีแผ่นดินไหวบ่อยที่สุด',
                        notes: 'ใช้ลูกโลกจำลอง หรือเปิดภาพแอนิเมชันการเอียงของแกนโลกให้นักเรียนดูประกอบ'
                    }
                ]
            },
            {
                id: 'deck-econ-01',
                subjectKey: 'economics',
                title: 'เศรษฐศาสตร์น่ารู้: กลไกราคา & อุปสงค์อุปทาน',
                author: 'ครูพี่ป๊อป',
                tag: 'ระดับชั้น ม.3',
                slides: [
                    {
                        subtopic: 'พื้นฐานเศรษฐศาสตร์',
                        title: 'ความต้องการที่ไม่จำกัด vs ทรัพยากรที่มีจำกัด',
                        content: '• เศรษฐศาสตร์ คือการจัดสรร "ทรัพยากรที่มีอยู่อย่างจำกัด" ให้เกิดประโยชน์สูงสุด ตอบสนองความต้องการที่ไม่จำกัดของมนุษย์\n• ก่อให้เกิด "ค่าเสียโอกาส" (Opportunity Cost) ทุกครั้งเมื่อตัดสินใจเลือกสิ่งใดสิ่งหนึ่ง',
                        notes: 'ยกตัวอย่างชีวิตประจำวัน: การเลือกซื้อชานมไข่มุกเทียบกับการเก็บเงินออม'
                    },
                    {
                        subtopic: 'กฎอุปสงค์และอุปทาน',
                        title: 'Demand (อุปสงค์) & Supply (อุปทาน)',
                        content: '• กฎของอุปสงค์ (Demand): ราคาแพงขึ้น ➔ ซื้อน้อยลง / ราคาถูกลง ➔ ซื้อมากขึ้น\n• กฎของอุปทาน (Supply): ราคาแพงขึ้น ➔ ขายมากขึ้น / ราคาถูกลง ➔ ขายน้อยลง\n• จุดดุลยภาพ (Equilibrium): จุดที่ความต้องการซื้อและความต้องการขายเท่ากันพอดี',
                        notes: 'ใช้นิ้วมือวาดกราฟเส้น Demand (ตัดลง) และ Supply (ตัดขึ้น) ให้ดูบนกระดาน'
                    },
                    {
                        subtopic: 'เศรษฐกิจพอเพียง',
                        title: 'ปรัชญาเศรษฐกิจพอเพียง 3 ห่วง 2 เงื่อนไข',
                        content: '• 3 ห่วง: พอประมาณ (ไม่มากไม่น้อยไป) + มีเหตุผล + มีภูมิคุ้มกันในตัวที่ดี\n• 2 เงื่อนไข: เงื่อนไขความรู้ + เงื่อนไขคุณธรรม\n• ประยุกต์ใช้ในการออมเงิน การเลือกซื้อสินค้า และการดำเนินชีวิตประจำวัน',
                        notes: 'ถามนักเรียนว่าในสัปดาห์นี้ ได้นำหลักความพอประมาณมาใช้ในเรื่องใดบ้าง'
                    }
                ]
            },
            {
                id: 'deck-civics-01',
                subjectKey: 'civics',
                title: 'พลเมืองดีตามวิถีประชาธิปไตย & กฎหมายใกล้ตัว',
                author: 'ครูสายประชาธิปไตย',
                tag: 'ระดับชั้น ม.2',
                slides: [
                    {
                        subtopic: 'พลเมืองดี',
                        title: 'คุณลักษณะของพลเมืองดีตามวิถีประชาธิปไตย',
                        content: '1. เคารพสิทธิและเสรีภาพของผู้อื่น\n2. มีคารวธรรม (เคารพผู้ใหญ่และกฎเกณฑ์), สามัคคีธรรม (ร่วมมือกัน), ปัญญาธรรม (ใช้เหตุผล)\n3. ปฏิบัติตามกฎหมายและหน้าที่ของปวงชนชาวไทย\n4. มีจิตสาธารณะ เสียสละเพื่อส่วนรวม',
                        notes: 'ให้นักเรียนช่วยกันยกตัวอย่างการทำกิจกรรมจิตสาธารณะในโรงเรียน'
                    },
                    {
                        subtopic: 'กฎหมายใกล้ตัว',
                        title: 'กฎหมายแพ่ง กฎหมายอาญา & กฎหมายจราจร',
                        content: '• กฎหมายแพ่ง: เรื่องสิทธิ ทรัพย์สิน สัญญา มรดก (โทษคือการชดใช้ค่าเสียหาย)\n• กฎหมายอาญา: ความผิดต่อส่วนรวม เช่น ลักทรัพย์ ทำร้ายร่างกาย (โทษมี 5 ระดับ: ริบทรัพย์สิน, ปรับ, กักขัง, จำคุก, ประหารชีวิต)\n• บัตรประจำตัวประชาชน: ต้องทำเมื่ออายุครบ 7 ปีบริบูรณ์',
                        notes: 'เน้นย้ำเรื่องความแตกต่างระหว่างโทษทางแพ่ง (จ่ายเงิน) และโทษทางอาญา (ติดคุก/รับโทษ)'
                    },
                    {
                        subtopic: 'ระบอบการปกครอง',
                        title: 'การปกครองระบอบประชาธิปไตยของไทย',
                        content: '• อำนาจอธิปไตยเป็นของปวงชนชาวไทย แบ่งเป็น 3 อำนาจหลัก:\n  1. อำนาจนิติบัญญัติ (รัฐสภา - ออกกฎหมาย)\n  2. อำนาจบริหาร (คณะรัฐมนตรี - บริหารประเทศ)\n  3. อำนาจตุลาการ (ศาล - ตัดสินคดีความ)\n• พระมหากษัตริย์ทรงเป็นประมุขภายใต้รัฐธรรมนูญ',
                        notes: 'ใช้วงกลมคานอำนาจ 3 ฝ่าย (Checks and Balances) อธิบายระบบตรวจสอบและถ่วงดุล'
                    }
                ]
            },
            {
                id: 'deck-religion-01',
                subjectKey: 'religion',
                title: 'ศาสนา วัฒนธรรม & หลักธรรมในการดำเนินชีวิต',
                author: 'ครูธรรมะสดใส',
                tag: 'ระดับชั้น ม.1',
                slides: [
                    {
                        subtopic: 'ศาสนาสำคัญ',
                        title: 'ศาสนาพุทธ ศาสนาอิสลาม & ศาสนาคริสต์',
                        content: '• ศาสนาพุทธ: คัมภีร์พระไตรปิฎก / ศาสดาคือพระพุทธเจ้า / มุ่งสู่การหลุดพ้น (นิพพาน)\n• ศาสนาอิสลาม: คัมภีร์อัลกุรอาน / ศาสดาคือพระมูฮัมหมัด / ศรัทธาในพระอัลเลาะห์\n• ศาสนาคริสต์: คัมภีร์ไบเบิล / ศาสดาคือพระเยซู / สอนเรื่องความรักและการให้อภัย\n• ทุกศาสนาล้วนสอนให้ทุกคนเป็นคนดีและอยู่ร่วมกันอย่างสันติสุข',
                        notes: 'เน้นย้ำความหลากหลายทางศาสนาและการยอมรับความแตกต่างในสังคมพหุวัฒนธรรม'
                    },
                    {
                        subtopic: 'หลักธรรมสำคัญ',
                        title: 'อริยสัจ 4 ความจริงอันประเสริฐ',
                        content: '1. ทุกข์: ความไม่สบายกาย ไม่สบายใจ (ปัญหาที่เกิดขึ้น)\n2. สมุทัย: สาเหตุแห่งทุกข์ (ตัณหา / ความอยาก)\n3. นิโรธ: ความดับทุกข์ (การแก้ปัญหาได้สำเร็จ)\n4. มรรค: ข้อปฏิบัติให้ถึงความดับทุกข์ (วิธีแก้ปัญหา เช่น มรรคมีองค์ 8)',
                        notes: 'เปรียบเทียบอริยสัจ 4 กับขั้นตอนการทำงานของหมอ (ตรวจโรค ➔ หาสาเหตุ ➔ วางเป้าหายรักษา ➔ ให้ยา/สั่งการรักษา)'
                    },
                    {
                        subtopic: 'วัฒนธรรมไทย',
                        title: 'มารยาทไทย & ประเพณีอันทรงคุณค่า',
                        content: '• มารยาทไทย: การไหว้ 3 ระดับ (พระสงฆ์, ผู้มีพระคุณ/ผู้สูงอายุ, บุคคลเสมอกัน)\n• ประเพณี 4 ภาค:\n  - ภาคเหนือ: ยี่เป็ง (โคมลอย)\n  - ภาคอีสาน: บุญบังไฟ, ผีตาโขน\n  - ภาคกลาง: แข่งเรือยาว, ลอยกระทง\n  - ภาคใต้: ชักพระ, บุญสารทเดือนสิบ',
                        notes: 'สาธิตวิธีการไหว้ทั้ง 3 ระดับให้นักเรียนปฏิบัติตามอย่างถูกต้อง'
                    }
                ]
            }
        ];

        let slideDecks = [];
        let currentFilter = 'all';
        let currentActiveDeck = null;
        let currentSlideIndex = 0;
        
        let isDrawing = false;
        let penActive = false;
        let penColor = '#FF2A85';
        let penWidth = 6;
        let ctx = null;

        /* ==========================================================================
           2. INITIALIZATION
           ========================================================================== */

        window.onload = function() {
            loadDecksFromStorage();
            renderFilterTabs();
            renderDecks();
            setupKeyboardNavigation();
            setupCanvasDrawing();
        };

        function loadDecksFromStorage() {
            const stored = localStorage.getItem('social_hub_decks_v2');
            if (stored) {
                try {
                    slideDecks = JSON.parse(stored);
                } catch (e) {
                    slideDecks = [...DEFAULT_DECKS];
                }
            } else {
                slideDecks = [...DEFAULT_DECKS];
                saveDecksToStorage();
            }
        }

        function saveDecksToStorage() {
            localStorage.setItem('social_hub_decks_v2', JSON.stringify(slideDecks));
        }

        function resetToDefaultData() {
            if (confirm("คุณต้องการรีเซ็ตข้อมูลสไลด์กลับเป็นค่าเริ่มต้นใช่หรือไม่?")) {
                slideDecks = [...DEFAULT_DECKS];
                saveDecksToStorage();
                renderDecks();
            }
        }

        /* ==========================================================================
           3. UI RENDER FUNCTIONS
           ========================================================================== */

        function renderFilterTabs() {
            const container = document.getElementById('filterTabs');
            let html = `
                <button onclick="setFilter('all')" class="brutal-btn px-4 py-2 rounded-2xl font-black text-sm flex items-center gap-2 ${currentFilter === 'all' ? 'bg-black text-white' : 'bg-white text-slate-800'}">
                    <i class="fa-solid fa-shapes"></i> ทั้งหมด 5 สาระ
                </button>
            `;

            Object.keys(SUBJECTS).forEach(key => {
                const subj = SUBJECTS[key];
                const active = currentFilter === key;
                html += `
                    <button onclick="setFilter('${key}')" class="brutal-btn px-4 py-2 rounded-2xl font-black text-sm flex items-center gap-2 ${active ? 'bg-black text-white ring-2 ring-yellow-400' : 'bg-white text-slate-800'}">
                        <i class="fa-solid ${subj.icon}" style="color:${subj.accentColor}"></i>
                        ${subj.name}
                    </button>
                `;
            });

            container.innerHTML = html;
        }

        function setFilter(subjectKey) {
            currentFilter = subjectKey;
            renderFilterTabs();
            renderDecks();
        }

        function filterDecks() {
            renderDecks();
        }

        function renderDecks() {
            const grid = document.getElementById('deckGrid');
            const emptyState = document.getElementById('emptyState');
            const searchVal = document.getElementById('searchInput').value.toLowerCase().trim();

            let filtered = slideDecks.filter(deck => {
                const matchCategory = (currentFilter === 'all') || (deck.subjectKey === currentFilter);
                const matchSearch = deck.title.toLowerCase().includes(searchVal) || 
                                    (deck.author && deck.author.toLowerCase().includes(searchVal)) ||
                                    (deck.tag && deck.tag.toLowerCase().includes(searchVal));
                return matchCategory && matchSearch;
            });

            document.getElementById('deckCount').textContent = filtered.length;

            if (filtered.length === 0) {
                grid.innerHTML = '';
                emptyState.classList.remove('hidden');
                return;
            }

            emptyState.classList.add('hidden');

            let html = '';
            filtered.forEach(deck => {
                const subj = SUBJECTS[deck.subjectKey] || SUBJECTS.history;
                const slideCount = deck.slides ? deck.slides.length : 0;

                html += `
                    <div class="brutal-card ${subj.cardBg} rounded-3xl p-6 flex flex-col justify-between relative overflow-hidden group">
                        
                        <div class="absolute -right-6 -bottom-6 text-black/10 text-9xl font-black pointer-events-none group-hover:scale-110 transition-transform">
                            <i class="fa-solid ${subj.icon}"></i>
                        </div>

                        <div>
                            <div class="flex items-center justify-between mb-4">
                                <span class="px-3 py-1.5 rounded-xl font-black text-xs border-2 border-black ${subj.badgeBg} shadow-pop flex items-center gap-1.5">
                                    <i class="fa-solid ${subj.icon}"></i> ${subj.name}
                                </span>
                                <span class="bg-black text-white text-xs font-extrabold px-3 py-1 rounded-xl shadow-pop">
                                    <i class="fa-solid fa-clone text-neon-yellow mr-1"></i> ${slideCount} หน้า
                                </span>
                            </div>

                            <h3 class="text-xl sm:text-2xl font-black text-black mb-3 leading-snug drop-shadow-sm">
                                ${deck.title}
                            </h3>

                            <div class="flex flex-wrap items-center gap-2 text-xs font-bold text-slate-900 mb-6">
                                ${deck.author ? `<span class="bg-white/80 brutal-border px-2.5 py-1 rounded-lg"><i class="fa-solid fa-user-tie mr-1 text-neon-pink"></i>${deck.author}</span>` : ''}
                                ${deck.tag ? `<span class="bg-white/80 brutal-border px-2.5 py-1 rounded-lg"><i class="fa-solid fa-graduation-cap mr-1 text-neon-blue"></i>${deck.tag}</span>` : ''}
                            </div>
                        </div>

                        <div class="pt-4 border-t-2 border-black/20 flex items-center justify-between gap-2 z-10">
                            <button onclick="startPresentation('${deck.id}')" class="brutal-btn bg-black text-white hover:bg-slate-900 font-extrabold px-3.5 py-2.5 rounded-2xl text-xs sm:text-sm flex-grow flex items-center justify-center gap-1.5 shadow-pop">
                                <i class="fa-solid fa-play text-neon-lime"></i> นำเสนอ
                            </button>
                            
                            <button onclick="exportDeckJson('${deck.id}')" class="brutal-btn bg-white hover:bg-cyan-200 text-black p-2.5 rounded-2xl" title="ส่งออกไฟล์ JSON">
                                <i class="fa-solid fa-download"></i>
                            </button>

                            <button onclick="openEditModal('${deck.id}')" class="brutal-btn bg-white hover:bg-yellow-200 text-black p-2.5 rounded-2xl" title="แก้ไข">
                                <i class="fa-solid fa-pen-to-square"></i>
                            </button>
                            
                            <button onclick="deleteDeck('${deck.id}')" class="brutal-btn bg-red-500 hover:bg-red-600 text-white p-2.5 rounded-2xl" title="ลบ">
                                <i class="fa-solid fa-trash"></i>
                            </button>
                        </div>

                    </div>
                `;
            });

            grid.innerHTML = html;
        }

        /* ==========================================================================
           4. PRESENTATION MODE
           ========================================================================== */

        function startPresentation(deckId) {
            const deck = slideDecks.find(d => d.id === deckId);
            if (!deck || !deck.slides || deck.slides.length === 0) {
                alert("ชุดสไลด์นี้ยังไม่มีเนื้อหา ให้กดปุ่มแก้ไขเพื่อเพิ่มเนื้อหาสไลด์!");
                return;
            }

            currentActiveDeck = deck;
            currentSlideIndex = 0;

            const modal = document.getElementById('presentationModal');
            modal.classList.remove('hidden');
            modal.classList.add('flex');

            const subj = SUBJECTS[deck.subjectKey] || SUBJECTS.history;
            const badge = document.getElementById('presSubjectBadge');
            badge.textContent = subj.name;
            badge.className = `px-3 py-1 rounded-xl text-xs font-black brutal-border ${subj.badgeBg}`;

            document.getElementById('presDeckTitle').textContent = deck.title;
            document.getElementById('presDeckFooter').innerHTML = `<i class="fa-solid fa-book-open mr-1"></i> ${deck.title} (${subj.name})`;

            renderCurrentSlide();
            resizeCanvas();
        }

        function renderCurrentSlide() {
            if (!currentActiveDeck || !currentActiveDeck.slides[currentSlideIndex]) return;

            const slide = currentActiveDeck.slides[currentSlideIndex];
            const total = currentActiveDeck.slides.length;

            document.getElementById('presSlideCounter').textContent = `${currentSlideIndex + 1} / ${total}`;
            document.getElementById('presSubtopic').textContent = slide.subtopic || 'หัวข้อย่อย';
            document.getElementById('presSlideTitle').textContent = slide.title || 'ไม่มีชื่อหัวข้อ';
            document.getElementById('presSlideBody').textContent = slide.content || '';

            document.getElementById('presSpeakerNotes').textContent = slide.notes || 'ไม่มีบันทึกเพิ่มเติมสำหรับสไลด์นี้';

            const progressPercent = ((currentSlideIndex + 1) / total) * 100;
            document.getElementById('slideProgressBar').style.width = `${progressPercent}%`;

            clearCanvas();
        }

        function nextSlide() {
            if (currentActiveDeck && currentSlideIndex < currentActiveDeck.slides.length - 1) {
                currentSlideIndex++;
                renderCurrentSlide();
            }
        }

        function prevSlide() {
            if (currentActiveDeck && currentSlideIndex > 0) {
                currentSlideIndex--;
                renderCurrentSlide();
            }
        }

        function closePresentation() {
            const modal = document.getElementById('presentationModal');
            modal.classList.add('hidden');
            modal.classList.remove('flex');
            currentActiveDeck = null;
        }

        function changePresBg(colorClasses) {
            const frame = document.getElementById('presSlideFrame');
            frame.className = `relative w-full max-w-5xl aspect-[16/9] brutal-card rounded-3xl p-6 sm:p-12 flex flex-col justify-between transition-all overflow-y-auto shadow-neon-pink ${colorClasses}`;
        }

        function toggleSpeakerNotes() {
            const panel = document.getElementById('speakerNotesPanel');
            panel.classList.toggle('hidden');
        }

        function exportCurrentActiveDeck() {
            if (currentActiveDeck) {
                exportDeckJson(currentActiveDeck.id);
            }
        }

        function deleteCurrentDeckFromPres() {
            if (currentActiveDeck) {
                if (confirm(`คุณแน่ใจหรือไม่ว่าต้องการลบชุดสไลด์ "${currentActiveDeck.title}" ออก?`)) {
                    const idToDelete = currentActiveDeck.id;
                    closePresentation();
                    deleteDeck(idToDelete);
                }
            }
        }

        function setupKeyboardNavigation() {
            document.addEventListener('keydown', (e) => {
                const presModal = document.getElementById('presentationModal');
                if (!presModal.classList.contains('hidden')) {
                    if (e.key === 'ArrowRight' || e.key === 'Space') {
                        nextSlide();
                    } else if (e.key === 'ArrowLeft') {
                        prevSlide();
                    } else if (e.key === 'Escape') {
                        closePresentation();
                    }
                }
            });
        }

        /* ==========================================================================
           5. DRAWING CANVAS TOOL
           ========================================================================== */

        function setupCanvasDrawing() {
            const canvas = document.getElementById('drawingCanvas');
            ctx = canvas.getContext('2d');

            window.addEventListener('resize', resizeCanvas);

            canvas.addEventListener('mousedown', startDrawing);
            canvas.addEventListener('mousemove', draw);
            canvas.addEventListener('mouseup', stopDrawing);
            canvas.addEventListener('mouseleave', stopDrawing);

            canvas.addEventListener('touchstart', (e) => {
                const touch = e.touches[0];
                const rect = canvas.getBoundingClientRect();
                startDrawing({ clientX: touch.clientX, clientY: touch.clientY });
            });
            canvas.addEventListener('touchmove', (e) => {
                const touch = e.touches[0];
                draw({ clientX: touch.clientX, clientY: touch.clientY });
            });
            canvas.addEventListener('touchend', stopDrawing);
        }

        function resizeCanvas() {
            const canvas = document.getElementById('drawingCanvas');
            const frame = document.getElementById('presSlideFrame');
            if (frame && canvas) {
                canvas.width = frame.clientWidth;
                canvas.height = frame.clientHeight;
            }
        }

        function togglePenTool() {
            penActive = !penActive;
            const btn = document.getElementById('penBtn');
            const palette = document.getElementById('penPalette');
            const canvas = document.getElementById('drawingCanvas');

            if (penActive) {
                btn.classList.remove('bg-slate-800');
                btn.classList.add('bg-neon-pink', 'text-white');
                palette.classList.remove('hidden');
                canvas.classList.remove('pointer-events-none');
                canvas.classList.add('cursor-crosshair');
            } else {
                btn.classList.remove('bg-neon-pink');
                btn.classList.add('bg-slate-800');
                palette.classList.add('hidden');
                canvas.classList.add('pointer-events-none');
                canvas.classList.remove('cursor-crosshair');
            }
        }

        function setPenColor(color) { penColor = color; }
        function setPenWidth(width) { penWidth = width; }

        function startDrawing(e) {
            if (!penActive) return;
            isDrawing = true;
            const canvas = document.getElementById('drawingCanvas');
            const rect = canvas.getBoundingClientRect();
            ctx.beginPath();
            ctx.moveTo(e.clientX - rect.left, e.clientY - rect.top);
        }

        function draw(e) {
            if (!isDrawing || !penActive) return;
            const canvas = document.getElementById('drawingCanvas');
            const rect = canvas.getBoundingClientRect();
            ctx.lineTo(e.clientX - rect.left, e.clientY - rect.top);
            ctx.strokeStyle = penColor;
            ctx.lineWidth = penWidth;
            ctx.lineCap = 'round';
            ctx.lineJoin = 'round';
            ctx.stroke();
        }

        function stopDrawing() { isDrawing = false; }

        function clearCanvas() {
            const canvas = document.getElementById('drawingCanvas');
            if (ctx && canvas) {
                ctx.clearRect(0, 0, canvas.width, canvas.height);
            }
        }

        /* ==========================================================================
           6. EXTERNAL SLIDE IMPORT / EXPORT SYSTEM
           ========================================================================== */

        function openImportModal() {
            document.getElementById('importModal').classList.remove('hidden');
        }

        function closeImportModal() {
            document.getElementById('importModal').classList.add('hidden');
        }

        function switchImportTab(tab) {
            const fileTab = document.getElementById('importTabFile');
            const textTab = document.getElementById('importTabText');
            const fileBtn = document.getElementById('importTabFileBtn');
            const textBtn = document.getElementById('importTabTextBtn');

            if (tab === 'file') {
                fileTab.classList.remove('hidden');
                textTab.classList.add('hidden');
                fileBtn.className = 'brutal-btn bg-black text-white px-4 py-2 rounded-xl font-black text-xs sm:text-sm';
                textBtn.className = 'brutal-btn bg-white text-black px-4 py-2 rounded-xl font-black text-xs sm:text-sm';
            } else {
                fileTab.classList.add('hidden');
                textTab.classList.remove('hidden');
                fileBtn.className = 'brutal-btn bg-white text-black px-4 py-2 rounded-xl font-black text-xs sm:text-sm';
                textBtn.className = 'brutal-btn bg-black text-white px-4 py-2 rounded-xl font-black text-xs sm:text-sm';
            }
        }

        function handleFileSelect(e) {
            const file = e.target.files[0];
            if (!file) return;

            const reader = new FileReader();
            reader.onload = function(event) {
                const content = event.target.result;
                if (file.name.endsWith('.json')) {
                    tryImportJson(content);
                } else {
                    tryImportTextOutline(content, file.name.replace('.txt', ''));
                }
            };
            reader.readAsText(file);
        }

        function tryImportJson(jsonStr) {
            try {
                const data = JSON.parse(jsonStr);
                const decksToImport = Array.isArray(data) ? data : [data];
                let count = 0;

                decksToImport.forEach(deck => {
                    if (deck.title && deck.slides) {
                        deck.id = 'deck-imported-' + Date.now() + '-' + Math.floor(Math.random()*1000);
                        if (!SUBJECTS[deck.subjectKey]) deck.subjectKey = 'history';
                        slideDecks.unshift(deck);
                        count++;
                    }
                });

                if (count > 0) {
                    saveDecksToStorage();
                    renderDecks();
                    closeImportModal();
                    alert(`นำเข้าชุดสไลด์เรียบร้อยจำนวน ${count} ชุด!`);
                } else {
                    alert("รูปแบบไฟล์ JSON ไม่ถูกต้อง กรุณาตรวจสอบไฟล์ใหม่อีกครั้ง");
                }
            } catch (err) {
                alert("เกิดข้อผิดพลาดในการอ่านไฟล์ JSON: " + err.message);
            }
        }

        function tryImportTextOutline(text, defaultTitle = 'บทเรียนนำเข้าภายนอก') {
            const lines = text.split('\n');
            let deckTitle = defaultTitle;
            let slides = [];
            let currentSlide = null;

            lines.forEach(line => {
                const trimmed = line.trim();
                if (!trimmed) return;

                if (trimmed.startsWith('# ')) {
                    deckTitle = trimmed.replace('# ', '').replace('ชื่อบทเรียน:', '').trim();
                } else if (trimmed.startsWith('---') || trimmed.startsWith('===')) {
                    if (currentSlide) slides.push(currentSlide);
                    currentSlide = null;
                } else if (trimmed.startsWith('[หัวข้อย่อย]')) {
                    if (!currentSlide) currentSlide = { subtopic: '', title: '', content: '', notes: '' };
                    currentSlide.subtopic = trimmed.replace('[หัวข้อย่อย]', '').trim();
                } else if (trimmed.startsWith('- หัวข้อสไลด์:') || trimmed.startsWith('## ')) {
                    if (!currentSlide) currentSlide = { subtopic: 'บทเรียน', title: '', content: '', notes: '' };
                    currentSlide.title = trimmed.replace('- หัวข้อสไลด์:', '').replace('## ', '').trim();
                } else if (trimmed.startsWith('[Notes:')) {
                    if (currentSlide) currentSlide.notes = trimmed.replace('[Notes:', '').replace(']', '').trim();
                } else {
                    if (!currentSlide) {
                        currentSlide = { subtopic: 'บทเรียน', title: trimmed, content: '', notes: '' };
                    } else {
                        currentSlide.content += (currentSlide.content ? '\n' : '') + trimmed;
                    }
                }
            });

            if (currentSlide) slides.push(currentSlide);

            if (slides.length > 0) {
                const subjectKey = document.getElementById('importSubjectSelect').value || 'history';
                const newDeck = {
                    id: 'deck-import-' + Date.now(),
                    subjectKey: subjectKey,
                    title: deckTitle,
                    author: 'นำเข้าจากไฟล์ภายนอก',
                    tag: 'สไลด์นำเข้า',
                    slides: slides
                };
                slideDecks.unshift(newDeck);
                saveDecksToStorage();
                renderDecks();
                closeImportModal();
                alert(`แปลงข้อความและสร้างชุดสไลด์ "${deckTitle}" สำเร็จ (${slides.length} หน้า)!`);
            } else {
                alert("ไม่สามารถแยกหน้าสไลด์จากข้อความได้ กรุณาตรวจสอบรูปแบบข้อความ");
            }
        }

        function processTextImport() {
            const text = document.getElementById('importTextOutline').value.trim();
            if (!text) {
                alert("กรุณาป้อนข้อความเค้าโครงบทเรียน!");
                return;
            }
            tryImportTextOutline(text);
        }

        function exportDeckJson(deckId) {
            const deck = slideDecks.find(d => d.id === deckId);
            if (!deck) return;

            const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(deck, null, 2));
            const downloadAnchor = document.createElement('a');
            downloadAnchor.setAttribute("href", dataStr);
            downloadAnchor.setAttribute("download", `${deck.title.replace(/[/\\?%*:|"<>]/g, '_')}.json`);
            document.body.appendChild(downloadAnchor);
            downloadAnchor.click();
            downloadAnchor.remove();
        }

        /* ==========================================================================
           7. QUICK TEXT IMPORT FOR SLIDE CREATION FORM
           ========================================================================== */

        function openQuickTextImport() {
            document.getElementById('quickTextImportModal').classList.remove('hidden');
        }

        function closeQuickTextImport() {
            document.getElementById('quickTextImportModal').classList.add('hidden');
        }

        function applyQuickTextImport() {
            const rawText = document.getElementById('quickImportText').value.trim();
            if (!rawText) return;

            const blocks = rawText.split(/---|\n\n\n/);
            blocks.forEach(block => {
                const lines = block.trim().split('\n');
                if (lines.length > 0) {
                    const title = lines[0].replace(/^[0-9#.-]+\s*/, '').trim();
                    const content = lines.slice(1).join('\n').trim();
                    if (title) {
                        addSlideInputRow('บทเรียน', title, content, '');
                    }
                }
            });

            closeQuickTextImport();
            document.getElementById('quickImportText').value = '';
        }

        /* ==========================================================================
           8. FORM MANAGEMENT (ADD / EDIT / DELETE)
           ========================================================================== */

        function openModal() {
            document.getElementById('editDeckId').value = '';
            document.getElementById('modalTitle').innerHTML = `<i class="fa-solid fa-folder-plus text-neon-pink"></i> สร้างชุดสไลด์สอนใหม่`;
            document.getElementById('deckForm').reset();
            
            document.getElementById('slidesContainer').innerHTML = '';
            addSlideInputRow();
            addSlideInputRow();

            updateCardColorPreview();
            document.getElementById('deckModal').classList.remove('hidden');
        }

        function closeModal() {
            document.getElementById('deckModal').classList.add('hidden');
        }

        function updateCardColorPreview() {
            const selectVal = document.getElementById('deckSubjectSelect').value;
            const subj = SUBJECTS[selectVal] || SUBJECTS.history;
            const badge = document.getElementById('subjectThemeBadge');
            
            badge.textContent = `${subj.name} (${subj.desc})`;
            badge.className = `px-4 py-1.5 rounded-xl font-black text-sm brutal-border shadow-pop ${subj.badgeBg}`;
        }

        function addSlideInputRow(subtopic = '', title = '', content = '', notes = '') {
            const container = document.getElementById('slidesContainer');
            const slideIndex = container.children.length + 1;

            const div = document.createElement('div');
            div.className = 'p-4 bg-slate-50 brutal-border rounded-2xl relative space-y-3';
            div.innerHTML = `
                <div class="flex items-center justify-between border-b border-slate-300 pb-2">
                    <span class="font-extrabold text-sm text-slate-800">
                        <i class="fa-solid fa-file-powerpoint text-neon-pink mr-1"></i> สไลด์หน้า <span class="slide-num">${slideIndex}</span>
                    </span>
                    <button type="button" onclick="removeSlideInputRow(this)" class="text-red-500 hover:text-red-700 font-bold text-xs bg-red-100 hover:bg-red-200 px-2 py-1 rounded-lg">
                        <i class="fa-solid fa-trash"></i> ลบหน้านี้
                    </button>
                </div>

                <div class="grid grid-cols-1 md:grid-cols-2 gap-3">
                    <input type="text" class="slide-subtopic w-full px-3 py-2 bg-white brutal-border rounded-xl text-xs font-bold" placeholder="หัวข้อย่อย (เช่น การเมือง)" value="${subtopic}">
                    <input type="text" class="slide-title w-full px-3 py-2 bg-white brutal-border rounded-xl text-xs font-bold" placeholder="ชื่อหัวข้อสไลด์ *" required value="${title}">
                </div>

                <textarea class="slide-content w-full px-3 py-2 bg-white brutal-border rounded-xl text-xs font-medium h-20" placeholder="เนื้อหาสไลด์ (ใส่เครื่องหมาย • หรือเว้นวรรคได้)...">${content}</textarea>

                <input type="text" class="slide-notes w-full px-3 py-2 bg-yellow-50 brutal-border rounded-xl text-xs font-medium" placeholder="บันทึกสำหรับผู้สอน (Teacher Notes)..." value="${notes}">
            `;

            container.appendChild(div);
            updateSlideNumbers();
        }

        function removeSlideInputRow(btn) {
            const container = document.getElementById('slidesContainer');
            if (container.children.length <= 1) {
                alert("ต้องมีสไลด์อย่างน้อย 1 หน้าขึ้นไป!");
                return;
            }
            btn.closest('.p-4').remove();
            updateSlideNumbers();
        }

        function updateSlideNumbers() {
            const rows = document.querySelectorAll('#slidesContainer > div');
            rows.forEach((row, idx) => {
                row.querySelector('.slide-num').textContent = idx + 1;
            });
            document.getElementById('slideCountLabel').textContent = rows.length;
        }

        function openEditModal(deckId) {
            const deck = slideDecks.find(d => d.id === deckId);
            if (!deck) return;

            document.getElementById('editDeckId').value = deck.id;
            document.getElementById('modalTitle').innerHTML = `<i class="fa-solid fa-pen-to-square text-neon-blue"></i> แก้ไขชุดสไลด์สอน`;
            
            document.getElementById('deckTitleInput').value = deck.title;
            document.getElementById('deckSubjectSelect').value = deck.subjectKey;
            document.getElementById('deckAuthorInput').value = deck.author || '';
            document.getElementById('deckTagInput').value = deck.tag || '';

            const container = document.getElementById('slidesContainer');
            container.innerHTML = '';

            if (deck.slides && deck.slides.length > 0) {
                deck.slides.forEach(s => {
                    addSlideInputRow(s.subtopic, s.title, s.content, s.notes);
                });
            } else {
                addSlideInputRow();
            }

            updateCardColorPreview();
            document.getElementById('deckModal').classList.remove('hidden');
        }

        function handleDeckFormSubmit(e) {
            e.preventDefault();
            
            const deckId = document.getElementById('editDeckId').value;
            const title = document.getElementById('deckTitleInput').value.trim();
            const subjectKey = document.getElementById('deckSubjectSelect').value;
            const author = document.getElementById('deckAuthorInput').value.trim();
            const tag = document.getElementById('deckTagInput').value.trim();

            const slideRows = document.querySelectorAll('#slidesContainer > div');
            const slides = [];

            slideRows.forEach(row => {
                const subtopic = row.querySelector('.slide-subtopic').value.trim();
                const slideTitle = row.querySelector('.slide-title').value.trim();
                const content = row.querySelector('.slide-content').value.trim();
                const notes = row.querySelector('.slide-notes').value.trim();

                slides.push({
                    subtopic: subtopic || 'บทเรียน',
                    title: slideTitle || 'ไม่มีชื่อหัวข้อ',
                    content: content,
                    notes: notes
                });
            });

            if (deckId) {
                const index = slideDecks.findIndex(d => d.id === deckId);
                if (index !== -1) {
                    slideDecks[index] = {
                        ...slideDecks[index],
                        title,
                        subjectKey,
                        author,
                        tag,
                        slides
                    };
                }
            } else {
                const newDeck = {
                    id: 'deck-' + Date.now(),
                    subjectKey,
                    title,
                    author,
                    tag,
                    slides
                };
                slideDecks.unshift(newDeck);
            }

            saveDecksToStorage();
            renderDecks();
            closeModal();
        }

        function deleteDeck(deckId) {
            const deck = slideDecks.find(d => d.id === deckId);
            if (!deck) return;

            if (confirm(`คุณแน่ใจหรือไม่ว่าต้องการลบชุดสไลด์ "${deck.title}"?`)) {
                slideDecks = slideDecks.filter(d => d.id !== deckId);
                saveDecksToStorage();
                renderDecks();
            }
        }
    </script>
</body>
</html>
