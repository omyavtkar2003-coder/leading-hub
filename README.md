<!DOCTYPE html>
<html lang="mr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Learning Hub - AI Viral Reel Studio</title>
  <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-slate-950 text-white flex h-screen overflow-hidden font-sans">

  <!-- डावीकडचा मेनू (Sidebar) -->
  <aside class="w-64 bg-slate-900 border-r border-slate-800 flex flex-col justify-between p-4">
    <div>
      <div class="flex items-center gap-2 mb-6 px-2">
        <span class="text-2xl">🚀</span>
        <h1 class="text-xl font-bold bg-gradient-to-r from-indigo-400 to-cyan-400 bg-clip-text text-transparent">
          Learning Hub
        </h1>
      </div>

      <p class="text-xs text-slate-400 uppercase font-semibold px-2 mb-2">All-In-One Workspace</p>
      <nav id="menu-list" class="space-y-1"></nav>
    </div>

    <div class="space-y-2 border-t border-slate-800 pt-4">
      <button onclick="openSettings()" class="w-full py-2 px-3 bg-indigo-600 hover:bg-indigo-500 rounded-lg text-sm font-medium transition">
        ⚙️ Tools Links सेट करा
      </button>
      <p class="text-[11px] text-center text-slate-500">100% Free Edition</p>
    </div>
  </aside>

  <!-- मुख्य स्क्रीन (Main Workspace) -->
  <main class="flex-1 flex flex-col bg-slate-950">
    <header class="h-14 bg-slate-900/60 border-b border-slate-800 px-6 flex items-center justify-between">
      <div class="flex items-center gap-3">
        <span id="current-icon" class="text-xl">🎙️</span>
        <h2 id="current-title" class="font-semibold text-lg">Voice Studio (Inbuilt Free)</h2>
        <span id="current-url-badge" class="text-xs bg-emerald-900/50 text-emerald-300 border border-emerald-700/50 px-2.5 py-0.5 rounded-full">
          100% Free Browser Engine
        </span>
      </div>
      <a id="open-new-tab" href="#" target="_blank" class="hidden text-xs bg-slate-800 hover:bg-slate-700 px-3 py-1.5 rounded-lg transition">
        नवीन टॅबमध्ये उघडा ↗
      </a>
    </header>

    <!-- १. इनबिल्ट मोफत Voice & Script Studio -->
    <div id="inbuilt-voice-studio" class="flex-1 p-6 overflow-y-auto">
      <div class="max-w-3xl mx-auto bg-slate-900 border border-slate-800 rounded-2xl p-6 space-y-5">
        <div>
          <h3 class="text-xl font-bold text-indigo-400">🎙️ मोफत AI व्हॉइस आणि स्क्रिप्ट स्टुडिओ</h3>
          <p class="text-xs text-slate-400 mt-1">कोणतेही जड सॉफ्टवेअर डाउनलोड न करता मराठी, हिंदी किंवा इंग्रजीमध्ये रीलचा आवाज तयार करा.</p>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
          <div>
            <label class="block text-xs text-slate-300 mb-1">आवाज निवडा (Voice / Language)</label>
            <select id="voice-select" class="w-full bg-slate-950 border border-slate-700 rounded-lg px-3 py-2 text-sm text-white"></select>
          </div>
          <div>
            <label class="block text-xs text-slate-300 mb-1">बोलण्याचा वेग (Speed): <span id="rate-val">1.0</span>x</label>
            <input id="voice-rate" type="range" min="0.7" max="1.4" step="0.1" value="1.0" oninput="document.getElementById('rate-val').textContent=this.value" class="w-full mt-2 accent-indigo-500" />
          </div>
        </div>

        <div>
          <label class="block text-xs text-slate-300 mb-1">तुमची रीलची स्क्रिप्ट इथे लिहा किंवा पेस्ट करा:</label>
          <textarea id="script-text" rows="5" placeholder="उदा. नमस्कार मित्रांनो! आज आपण जाणून घेणार आहोत एआयच्या जगातील ३ आश्चर्यकारक गोष्टी..." class="w-full bg-slate-950 border border-slate-700 rounded-xl p-3 text-sm text-white focus:outline-none focus:border-indigo-500"></textarea>
        </div>

        <div class="flex flex-wrap gap-3">
          <button onclick="speakScript()" class="px-5 py-2.5 bg-emerald-600 hover:bg-emerald-500 rounded-xl text-sm font-semibold transition flex items-center gap-2">
            ▶️ आवाज ऐका (Play Voice)
          </button>
          <button onclick="stopSpeech()" class="px-4 py-2.5 bg-rose-600/80 hover:bg-rose-600 rounded-xl text-sm font-medium transition">
            ⏹️ थांबवा (Stop)
          </button>
          <button onclick="copyScript()" class="px-4 py-2.5 bg-slate-800 hover:bg-slate-700 rounded-xl text-sm font-medium transition">
            📋 स्क्रिप्ट कॉपी करा
          </button>
        </div>

        <div class="bg-slate-950/70 border border-slate-800 rounded-xl p-4 text-xs text-slate-400 space-y-1">
          <p class="font-semibold text-slate-300">💡 मोफत टिप (आवाज सेव्ह करण्यासाठी):</p>
          <p>तुम्ही <b>Play Voice</b> दाबल्यावर तुमच्या PC वरील मोफत <b>Audacity</b> किंवा <b>OBS Studio</b> मधून हा आवाज थेट MP3 मध्ये रेकॉर्ड करू शकता, किंवा नंतर Pinokio मध्ये F5-TTS इन्स्टॉल झाल्यावर त्याची लिंक वरच्या Settings मधून जोडू शकता.</p>
        </div>
      </div>
    </div>

    <!-- २. इतर टूल्ससाठी Iframe स्क्रीन -->
    <div id="iframe-container" class="hidden flex-1 relative">
      <iframe id="tool-frame" src="" class="w-full h-full border-0 bg-white"></iframe>
    </div>
  </main>

  <!-- सेटिंग्ज पॉपअप -->
  <div id="settings-modal" class="hidden fixed inset-0 bg-black/70 flex items-center justify-center p-4 z-50">
    <div class="bg-slate-900 border border-slate-700 rounded-xl w-full max-w-lg p-6 max-h-[85vh] overflow-y-auto">
      <h3 class="text-lg font-bold mb-1">⚙️ तुमच्या टूल्सच्या लिंक्स (URLs) सेट करा</h3>
      <p class="text-xs text-slate-400 mb-4">तुमच्या PC किंवा ऑनलाइन टूल्सच्या लिंक्स इथे सेव्ह करा:</p>
      <div id="settings-inputs" class="space-y-3"></div>
      <div class="flex justify-end gap-2 mt-6">
        <button onclick="closeSettings()" class="px-4 py-2 bg-slate-800 rounded-lg text-sm">रद्द करा</button>
        <button onclick="saveSettings()" class="px-4 py-2 bg-indigo-600 hover:bg-indigo-500 rounded-lg text-sm font-semibold">सेव्ह करा</button>
      </div>
    </div>
  </div>

  <script>
    const defaultTools = [
      { id: "voicestudio", name: "Voice Studio", icon: "🎙️", url: "inbuilt" },
      { id: "comfyui", name: "ComfyUI", icon: "🎨", url: "http://127.0.0.1:8188" },
      { id: "openseo", name: "OpenSEO", icon: "📈", url: "https://trends.google.com" },
      { id: "appflowy", name: "AppFlowy", icon: "📝", url: "http://127.0.0.1:3000" },
      { id: "openwhisper", name: "OpenWhisper", icon: "💬", url: "http://127.0.0.1:9000" },
      { id: "openproject", name: "OpenProject", icon: "📊", url: "http://127.0.0.1:8080" },
      { id: "calcom", name: "Cal.com", icon: "📅", url: "https://app.cal.com" },
      { id: "chatwoot", name: "Chatwoot", icon: "💭", url: "http://127.0.0.1:3001" },
      { id: "capcut", name: "CapCut", icon: "✂️", url: "https://www.capcut.com" }
    ];

    let tools = JSON.parse(localStorage.getItem("learning_hub_tools_v2")) || defaultTools;

    function renderMenu() {
      const menu = document.getElementById("menu-list");
      menu.innerHTML = "";
      tools.forEach((tool) => {
        const btn = document.createElement("button");
        btn.className = "w-full flex items-center gap-3 px-3 py-2.5 rounded-lg text-sm text-slate-300 hover:bg-slate-800 hover:text-white transition text-left";
        btn.innerHTML = `<span>${tool.icon}</span><span>${tool.name}</span>`;
        btn.onclick = () => selectTool(tool);
        menu.appendChild(btn);
      });
    }

    function selectTool(tool) {
      document.getElementById("current-icon").textContent = tool.icon;
      document.getElementById("current-title").textContent = tool.name;

      if (tool.url === "inbuilt") {
        document.getElementById("inbuilt-voice-studio").classList.remove("hidden");
        document.getElementById("iframe-container").classList.add("hidden");
        document.getElementById("open-new-tab").classList.add("hidden");
        document.getElementById("current-url-badge").textContent = "100% Free Browser Engine";
      } else {
        document.getElementById("inbuilt-voice-studio").classList.add("hidden");
        document.getElementById("iframe-container").classList.remove("hidden");
        document.getElementById("open-new-tab").classList.remove("hidden");
        document.getElementById("open-new-tab").href = tool.url;
        document.getElementById("current-url-badge").textContent = tool.url;
        document.getElementById("tool-frame").src = tool.url;
      }
    }

    // ब्राउझरमधील सर्व मराठी/हिंदी/इंग्रजी आवाज लोड करणे
    function loadVoices() {
      const voiceSelect = document.getElementById("voice-select");
      const voices = speechSynthesis.getVoices();
      voiceSelect.innerHTML = "";
      voices.forEach((v, i) => {
        const option = document.createElement("option");
        option.value = i;
        option.textContent = `${v.name} (${v.lang})`;
        if (v.lang.includes("hi") || v.lang.includes("mr") || v.lang.includes("IN")) {
          option.selected = true;
        }
        voiceSelect.appendChild(option);
      });
    }
    speechSynthesis.onvoiceschanged = loadVoices;
    loadVoices();

    function speakScript() {
      const text = document.getElementById("script-text").value;
      if (!text.trim()) return alert("आधी काहीतरी स्क्रिप्ट टाइप करा!");
      speechSynthesis.cancel();
      const utterance = new SpeechSynthesisUtterance(text);
      const voices = speechSynthesis.getVoices();
      const selectedIdx = document.getElementById("voice-select").value;
      if (voices[selectedIdx]) utterance.voice = voices[selectedIdx];
      utterance.rate = parseFloat(document.getElementById("voice-rate").value);
      speechSynthesis.speak(utterance);
    }

    function stopSpeech() {
      speechSynthesis.cancel();
    }

    function copyScript() {
      const text = document.getElementById("script-text").value;
      navigator.clipboard.writeText(text);
      alert("स्क्रिप्ट कॉपी झाली!");
    }

    function openSettings() {
      const container = document.getElementById("settings-inputs");
      container.innerHTML = "";
      tools.forEach((tool, index) => {
        container.innerHTML += `
          <div>
            <label class="block text-xs text-slate-300 mb-1">${tool.icon} ${tool.name}</label>
            <input id="input-${index}" type="text" value="${tool.url}" class="w-full bg-slate-950 border border-slate-700 rounded-lg px-3 py-1.5 text-sm text-white" />
          </div>
        `;
      });
      document.getElementById("settings-modal").classList.remove("hidden");
    }

    function closeSettings() {
      document.getElementById("settings-modal").classList.add("hidden");
    }

    function saveSettings() {
      tools.forEach((tool, index) => {
        tool.url = document.getElementById(`input-${index}`).value;
      });
      localStorage.setItem("learning_hub_tools_v2", JSON.stringify(tools));
      renderMenu();
      closeSettings();
      alert("सेटिंग्ज सेव्ह झाल्या!");
    }

    renderMenu();
  </script>
</body>
</html>3
