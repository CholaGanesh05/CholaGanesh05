<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Chola Chetan Chukkala — AI Researcher</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;600;700&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0d1117;
    --bg2: #111820;
    --surface: #161b22;
    --border: #21262d;
    --accent: #D4732A;
    --accent2: #C4621A;
    --text: #e6edf3;
    --muted: #8b949e;
    --glow: rgba(212, 115, 42, 0.15);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'JetBrains Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* Ambient background */
  body::before {
    content: '';
    position: fixed;
    top: -50%;
    left: -50%;
    width: 200%;
    height: 200%;
    background: radial-gradient(ellipse 60% 40% at 60% 20%, rgba(212,115,42,0.07) 0%, transparent 60%),
                radial-gradient(ellipse 40% 60% at 20% 80%, rgba(196,98,26,0.05) 0%, transparent 50%);
    pointer-events: none;
    z-index: 0;
  }

  .container {
    max-width: 900px;
    margin: 0 auto;
    padding: 40px 24px;
    position: relative;
    z-index: 1;
  }

  /* Header */
  .header {
    text-align: center;
    margin-bottom: 48px;
    animation: fadeDown 0.6s ease both;
  }

  .typing-banner {
    display: inline-block;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 14px 28px;
    margin-bottom: 8px;
    font-size: 15px;
    font-weight: 600;
    color: var(--accent);
    letter-spacing: 0.02em;
    position: relative;
    overflow: hidden;
  }
  .typing-banner::after {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(90deg, transparent 0%, rgba(212,115,42,0.06) 50%, transparent 100%);
    animation: shimmer 3s infinite;
  }

  /* Divider */
  .divider {
    border: none;
    border-top: 1px solid var(--border);
    margin: 36px 0;
    position: relative;
  }
  .divider::after {
    content: '◈';
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background: var(--bg);
    padding: 0 8px;
    color: var(--accent);
    font-size: 12px;
  }

  /* Section */
  .section-title {
    font-family: 'Syne', sans-serif;
    font-size: 18px;
    font-weight: 700;
    color: var(--text);
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 10px;
    letter-spacing: 0.01em;
  }
  .section-title span { opacity: 0.9; }
  .section-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--border), transparent);
  }

  /* About card */
  .about-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 24px;
    animation: fadeUp 0.5s ease 0.1s both;
  }
  .code-block {
    font-size: 13px;
    line-height: 1.8;
    color: var(--text);
  }
  .code-class { color: #79c0ff; }
  .code-key { color: #d2a8ff; }
  .code-str { color: #a5d6ff; }
  .code-list { color: #7ee787; }
  .code-bracket { color: var(--muted); }
  .about-bullets {
    margin-top: 16px;
    display: flex;
    flex-direction: column;
    gap: 6px;
    font-size: 13px;
    color: var(--muted);
  }
  .about-bullets p { display: flex; align-items: baseline; gap: 8px; }
  .about-bullets .icon { font-size: 14px; }
  .about-bullets strong { color: var(--text); }
  .resume-link {
    display: inline-block;
    margin-top: 14px;
    padding: 8px 18px;
    background: linear-gradient(135deg, var(--accent2), var(--accent));
    color: white;
    text-decoration: none;
    border-radius: 6px;
    font-size: 12px;
    font-weight: 600;
    letter-spacing: 0.05em;
    transition: opacity 0.2s, transform 0.2s;
  }
  .resume-link:hover { opacity: 0.88; transform: translateY(-1px); }

  /* Connect */
  .connect-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    animation: fadeUp 0.5s ease 0.15s both;
  }
  .social-badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    padding: 9px 16px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    text-decoration: none;
    color: var(--text);
    font-size: 12px;
    font-weight: 600;
    transition: border-color 0.2s, transform 0.2s, box-shadow 0.2s;
  }
  .social-badge:hover {
    border-color: var(--accent);
    transform: translateY(-2px);
    box-shadow: 0 4px 16px rgba(212,115,42,0.2);
  }
  .social-badge svg { width: 16px; height: 16px; flex-shrink: 0; }

  /* Research Interests */
  .research-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 12px;
    animation: fadeUp 0.5s ease 0.2s both;
  }
  @media (max-width: 600px) { .research-grid { grid-template-columns: 1fr 1fr; } }
  .research-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 16px;
    transition: border-color 0.2s, transform 0.2s, box-shadow 0.2s;
    cursor: default;
  }
  .research-card:hover {
    border-color: var(--accent);
    transform: translateY(-2px);
    box-shadow: 0 4px 20px var(--glow);
  }
  .research-card .icon { font-size: 20px; margin-bottom: 8px; }
  .research-card h4 {
    font-family: 'Syne', sans-serif;
    font-size: 13px;
    font-weight: 700;
    color: var(--text);
    margin-bottom: 6px;
  }
  .research-card p { font-size: 11px; color: var(--muted); line-height: 1.6; }

  /* Tech Stack */
  .stack-section { margin-bottom: 28px; animation: fadeUp 0.5s ease 0.25s both; }
  .stack-section-title {
    font-size: 12px;
    font-weight: 600;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 0.1em;
    margin-bottom: 12px;
    padding-bottom: 8px;
    border-bottom: 1px solid var(--border);
  }
  .badges-row {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  /* Badge with tooltip */
  .badge-wrap {
    position: relative;
    display: inline-block;
  }
  .badge-wrap .badge {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 7px 13px;
    border-radius: 6px;
    font-size: 12px;
    font-weight: 600;
    cursor: default;
    border: 1px solid transparent;
    transition: transform 0.18s, box-shadow 0.18s, border-color 0.18s;
    user-select: none;
  }
  .badge-wrap:hover .badge {
    transform: translateY(-2px);
    border-color: rgba(255,255,255,0.15);
    box-shadow: 0 6px 20px rgba(0,0,0,0.4);
  }
  .badge svg { width: 14px; height: 14px; flex-shrink: 0; }
  .badge span { white-space: nowrap; }

  /* Tooltip */
  .tooltip {
    position: absolute;
    bottom: calc(100% + 8px);
    left: 50%;
    transform: translateX(-50%) translateY(4px);
    background: #1c2128;
    border: 1px solid var(--accent);
    color: var(--text);
    font-size: 11px;
    padding: 6px 12px;
    border-radius: 6px;
    white-space: nowrap;
    pointer-events: none;
    opacity: 0;
    transition: opacity 0.18s, transform 0.18s;
    z-index: 100;
    box-shadow: 0 4px 16px rgba(0,0,0,0.5);
  }
  .tooltip::after {
    content: '';
    position: absolute;
    top: 100%;
    left: 50%;
    transform: translateX(-50%);
    border: 5px solid transparent;
    border-top-color: var(--accent);
  }
  .badge-wrap:hover .tooltip {
    opacity: 1;
    transform: translateX(-50%) translateY(0);
  }

  /* GitHub Analytics */
  .analytics-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
    animation: fadeUp 0.5s ease 0.3s both;
  }
  @media (max-width: 600px) { .analytics-grid { grid-template-columns: 1fr; } }
  .analytics-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    overflow: hidden;
  }
  .analytics-card img { width: 100%; display: block; }

  /* Quote footer */
  .footer {
    text-align: center;
    margin-top: 48px;
    padding: 24px;
    border-top: 1px solid var(--border);
    color: var(--muted);
    font-size: 12px;
    line-height: 1.8;
    animation: fadeUp 0.5s ease 0.4s both;
  }
  .footer blockquote {
    font-style: italic;
    color: var(--text);
    margin-bottom: 16px;
    font-size: 13px;
  }

  /* Animations */
  @keyframes fadeDown { from { opacity: 0; transform: translateY(-16px); } to { opacity: 1; transform: translateY(0); } }
  @keyframes fadeUp { from { opacity: 0; transform: translateY(16px); } to { opacity: 1; transform: translateY(0); } }
  @keyframes shimmer { 0%,100% { transform: translateX(-100%); } 50% { transform: translateX(100%); } }
</style>
</head>
<body>
<div class="container">

  <!-- Capsule Render Header -->
  <div style="margin:-40px -24px 0;overflow:hidden;line-height:0;">
    <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=12,20,27&height=250&section=header&text=Chola%20Chetan%20Chukkala&fontSize=50&animation=fadeIn&fontAlignY=38&fontColor=ffffff&desc=AI%20Researcher%20%E2%80%A2%20AI%20Engineer%20%E2%80%A2%20Software%20Developer&descSize=20&descAlignY=58&descColor=F5C48A" alt="Header Banner — Chola Chetan Chukkala | AI Researcher • AI Engineer • Software Developer" style="width:100%;display:block;"/>
  </div>

  <!-- Header -->
  <div class="header" style="margin-top:32px;">
    <div class="typing-banner">Researching the Frontiers of AI 🧠 · Building Intelligent Systems from Scratch 🔬 · Fine-tuning LLMs | Multimodal AI | Agents 🤖</div>
  </div>

  <hr class="divider">

  <!-- About Me -->
  <div class="section-title"><span>🧑‍💻 About Me</span></div>
  <div class="about-card">
    <div class="code-block">
      <span class="code-class">class</span> <span style="color:#e3b341">CholaChetan</span>:<br>
      &nbsp;&nbsp;<span class="code-key">name</span> = <span class="code-str">"Chola Chetan Chukkala"</span><br>
      &nbsp;&nbsp;<span class="code-key">roles</span> = <span class="code-bracket">[</span><span class="code-list">"AI Researcher", "AI Engineer", "Software Developer"</span><span class="code-bracket">]</span><br>
      &nbsp;&nbsp;<span class="code-key">focus</span> = <span class="code-bracket">[</span><span class="code-list">"LLM Fine-tuning", "Multimodal AI", "Agentic Systems", "NLP"</span><span class="code-bracket">]</span><br>
      &nbsp;&nbsp;<span class="code-key">philosophy</span> = <span class="code-str">"I learn fastest when I build things."</span><br>
      &nbsp;&nbsp;<span class="code-key">goal</span> = <span class="code-str">"Contribute to frontier AI research"</span>
    </div>
    <div class="about-bullets">
      <p><span class="icon">🔭</span> Researching <strong>Multimodal AI & Agentic Systems</strong></p>
      <p><span class="icon">🧪</span> Building at the intersection of <strong>research & engineering</strong></p>
      <p><span class="icon">📖</span> Reading papers daily — translating theory into working systems</p>
      <p><span class="icon">⚡</span> Mindset: <strong>Research-first. Engineer-second. Ship always.</strong></p>
    </div>
    <a class="resume-link" href="https://drive.google.com/drive/folders/13t6xZRkvtisErOi2_hUqZElSHGn38yPP?usp=drive_link" target="_blank">📄 View My Resume →</a>
  </div>

  <hr class="divider">

  <!-- Connect -->
  <div class="section-title"><span>🌐 Connect With Me</span></div>
  <div class="connect-grid">
    <a class="social-badge" href="https://github.com/CholaGanesh05" target="_blank">
      <svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 2C6.477 2 2 6.477 2 12c0 4.418 2.865 8.167 6.839 9.49.5.092.682-.217.682-.483 0-.237-.009-.866-.013-1.7-2.782.604-3.369-1.34-3.369-1.34-.454-1.155-1.11-1.463-1.11-1.463-.908-.62.069-.608.069-.608 1.003.07 1.531 1.03 1.531 1.03.892 1.529 2.341 1.088 2.91.832.092-.647.35-1.088.636-1.338-2.22-.253-4.555-1.11-4.555-4.943 0-1.091.39-1.984 1.029-2.683-.103-.253-.446-1.27.098-2.647 0 0 .84-.269 2.75 1.025A9.578 9.578 0 0112 6.836c.85.004 1.705.115 2.504.337 1.909-1.294 2.747-1.025 2.747-1.025.546 1.377.202 2.394.1 2.647.64.699 1.028 1.592 1.028 2.683 0 3.842-2.339 4.687-4.566 4.935.359.309.678.919.678 1.852 0 1.336-.012 2.415-.012 2.743 0 .267.18.578.688.48C19.138 20.163 22 16.418 22 12c0-5.523-4.477-10-10-10z"/></svg>
      CholaGanesh05
    </a>
    <a class="social-badge" href="https://www.linkedin.com/in/cholachetan24" target="_blank">
      <svg viewBox="0 0 24 24" fill="#0A66C2"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
      cholachetan24
    </a>
    <a class="social-badge" href="mailto:vpscholachetan24@gmail.com">
      <svg viewBox="0 0 24 24" fill="#EA4335"><path d="M24 5.457v13.909c0 .904-.732 1.636-1.636 1.636h-3.819V11.73L12 16.64l-6.545-4.91v9.273H1.636A1.636 1.636 0 010 19.366V5.457c0-2.023 2.309-3.178 3.927-1.964L5.455 4.64 12 9.548l6.545-4.909 1.528-1.145C21.69 2.28 24 3.434 24 5.457z"/></svg>
      vpscholachetan24
    </a>
    <a class="social-badge" href="https://www.kaggle.com/cholachetanchukkala" target="_blank">
      <svg viewBox="0 0 24 24" fill="#20BEFF"><path d="M18.825 23.859c-.022.092-.117.141-.281.141h-3.139c-.187 0-.351-.082-.492-.248l-5.178-6.589-1.448 1.374v5.111c0 .235-.117.352-.351.352H5.505c-.236 0-.354-.117-.354-.352V.353c0-.233.118-.353.354-.353h2.431c.234 0 .351.12.351.353v14.343l6.203-6.272c.165-.165.33-.246.495-.246h3.239c.144 0 .236.06.285.18.046.149.034.255-.036.315l-6.555 6.344 6.836 8.507c.095.104.117.208.07.336z"/></svg>
      cholachetanchukkala
    </a>
  </div>

  <hr class="divider">

  <!-- Research Interests -->
  <div class="section-title"><span>🔬 Research Interests</span></div>
  <div class="research-grid">
    <div class="research-card"><div class="icon">🧠</div><h4>Large Language Models</h4><p>Fine-tuning, RLHF, alignment, RAG, efficient inference</p></div>
    <div class="research-card"><div class="icon">📦</div><h4>Small Language Models</h4><p>Phi, Gemma, TinyLlama — on-device & edge deployment</p></div>
    <div class="research-card"><div class="icon">🤖</div><h4>Agentic AI</h4><p>Tool-use, planning, memory, multi-agent orchestration</p></div>
    <div class="research-card"><div class="icon">👁️</div><h4>Multimodal AI</h4><p>Vision-Language Models, audio-text, cross-modal grounding</p></div>
    <div class="research-card"><div class="icon">🌊</div><h4>State Space Models</h4><p>Mamba, S4 — efficient long-context sequence modelling</p></div>
    <div class="research-card"><div class="icon">🔀</div><h4>Hybrid Architectures</h4><p>Transformer + SSM hybrids, MoE, sparse attention</p></div>
    <div class="research-card"><div class="icon">🌐</div><h4>Social Networks & AI</h4><p>Graph neural networks, community detection, misinformation</p></div>
    <div class="research-card"><div class="icon">💚</div><h4>Social Wellbeing & AI</h4><p>Mental health AI, assistive tech, human-centered design</p></div>
    <div class="research-card"><div class="icon">🔐</div><h4>AI Safety & Alignment</h4><p>Robustness, interpretability, responsible deployment</p></div>
    <div class="research-card"><div class="icon">📐</div><h4>NLP & Representation</h4><p>Transformers, embeddings, semantic understanding</p></div>
    <div class="research-card"><div class="icon">⚡</div><h4>Efficient ML</h4><p>Quantization, LoRA/QLoRA, knowledge distillation</p></div>
  </div>

  <hr class="divider">

  <!-- AI / ML Stack -->
  <div class="section-title"><span>🧠 AI Research & Core ML Stack</span></div>

  <div class="stack-section">
    <div class="stack-section-title">🔬 Deep Learning Frameworks</div>
    <div class="badges-row">
      <div class="badge-wrap"><div class="badge" style="background:#1a0f0a;color:#EE4C2C"><svg viewBox="0 0 24 24" fill="#EE4C2C"><path d="M12.005 0L4.952 12.013 12.005 24l7.043-11.987z"/></svg><span>PyTorch</span></div><div class="tooltip">Primary DL Framework for Research</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#1a1100;color:#FF6F00"><svg viewBox="0 0 24 24" fill="#FF6F00"><path d="M1.292 5.856L11.54 0v24L1.292 18.144A1.24 1.24 0 010 17.024V6.976c0-.48.28-.904.684-1.12z"/></svg><span>TensorFlow</span></div><div class="tooltip">Production ML & Model Serving</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#1a0000;color:#D00000"><svg viewBox="0 0 24 24" fill="#D00000"><path d="M0 0h24v24H0z" fill="none"/><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"/></svg><span>Keras</span></div><div class="tooltip">High-Level Neural Network API</div></div>
    </div>
  </div>

  <div class="stack-section">
    <div class="stack-section-title">🤗 LLM & Foundation Models</div>
    <div class="badges-row">
      <div class="badge-wrap"><div class="badge" style="background:#1a1600;color:#FFCC33"><svg viewBox="0 0 24 24" fill="#FFCC33"><circle cx="12" cy="12" r="10"/></svg><span>Hugging Face</span></div><div class="tooltip">Transformers | Datasets | Model Hub</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#0a1212;color:#2ecc71"><svg viewBox="0 0 24 24" fill="#1C3C3C"><circle cx="12" cy="12" r="10" fill="#1C3C3C" stroke="#2ecc71" stroke-width="1.5"/></svg><span>LangChain</span></div><div class="tooltip">LLM Orchestration & Agent Pipelines</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#111;color:#e6edf3"><svg viewBox="0 0 24 24" fill="currentColor"><circle cx="12" cy="12" r="10"/></svg><span>Ollama</span></div><div class="tooltip">Local LLM Inference & Deployment</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#1a0e06;color:#FF6B35"><svg viewBox="0 0 24 24" fill="#FF6B35"><path d="M12 2L2 7l10 5 10-5-10-5zM2 17l10 5 10-5M2 12l10 5 10-5"/></svg><span>Unsloth</span></div><div class="tooltip">Efficient LLM Fine-tuning (LoRA/QLoRA)</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#110d1a;color:#8A2BE2"><svg viewBox="0 0 24 24" fill="#8A2BE2"><path d="M12 2L2 7l10 5 10-5-10-5z"/></svg><span>PEFT</span></div><div class="tooltip">Parameter-Efficient Fine-Tuning Methods</div></div>
    </div>
  </div>

  <div class="stack-section">
    <div class="stack-section-title">📊 Data Science & ML Engineering</div>
    <div class="badges-row">
      <div class="badge-wrap"><div class="badge" style="background:#1a0f00;color:#F7931E"><svg viewBox="0 0 24 24" fill="#F7931E"><circle cx="12" cy="12" r="10"/></svg><span>Scikit-learn</span></div><div class="tooltip">Classical ML Algorithms & Evaluation Pipelines</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#08061a;color:#a78bfa"><svg viewBox="0 0 24 24" fill="#150458"><rect width="24" height="24" rx="2" fill="#150458"/><text x="2" y="18" font-size="14" fill="#e6edf3" font-weight="bold">pd</text></svg><span>Pandas</span></div><div class="tooltip">Data Wrangling & Tabular Analysis</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#090f1a;color:#4D77CF"><svg viewBox="0 0 24 24" fill="#4D77CF"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2z"/></svg><span>NumPy</span></div><div class="tooltip">Numerical Computing & Matrix Operations</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#0e0a1a;color:#5C3EE8"><svg viewBox="0 0 24 24" fill="#5C3EE8"><circle cx="12" cy="12" r="10"/></svg><span>OpenCV</span></div><div class="tooltip">Computer Vision & Image Processing</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#001a2e;color:#0194E2"><svg viewBox="0 0 24 24" fill="#0194E2"><path d="M12 2L2 7l10 5 10-5z"/></svg><span>MLflow</span></div><div class="tooltip">Experiment Tracking & Model Registry</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#0a1a0a;color:#44A833"><svg viewBox="0 0 24 24" fill="#44A833"><circle cx="12" cy="12" r="10"/></svg><span>Anaconda</span></div><div class="tooltip">Python Environment & Package Management</div></div>
    </div>
  </div>

  <hr class="divider">

  <!-- Software Engineering Stack -->
  <div class="section-title"><span>⚙️ Software Engineering Stack</span></div>

  <div class="stack-section">
    <div class="stack-section-title">🧩 Programming Languages</div>
    <div class="badges-row">
      <div class="badge-wrap"><div class="badge" style="background:#091526;color:#3776AB"><svg viewBox="0 0 24 24" fill="#3776AB"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2z"/></svg><span>Python</span></div><div class="tooltip">Primary Language for AI/ML Research</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#1a1800;color:#F7DF1E"><svg viewBox="0 0 24 24" fill="#F7DF1E"><rect width="24" height="24"/><text x="3" y="18" font-size="13" fill="#000" font-weight="bold">JS</text></svg><span>JavaScript</span></div><div class="tooltip">Full-Stack Web & AI Tool Interfaces</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#1a0e00;color:#ED8B00"><svg viewBox="0 0 24 24" fill="#ED8B00"><path d="M8.851 18.56s-.917.534.653.714c1.902.218 2.874.187 4.969-.211 0 0 .552.346 1.321.646-4.699 2.013-10.633-.118-6.943-1.149M8.276 15.933s-1.028.761.542.924c2.032.209 3.636.227 6.413-.308 0 0 .384.389.987.602-5.679 1.661-12.007.13-7.942-1.218"/></svg><span>Java</span></div><div class="tooltip">Object-Oriented & Backend Systems</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#00091a;color:#00599C"><svg viewBox="0 0 24 24" fill="#00599C"><path d="M12 2L2 7v10l10 5 10-5V7z"/></svg><span>C</span></div><div class="tooltip">Systems & Performance-Critical Code</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#000f1a;color:#0175C2"><svg viewBox="0 0 24 24" fill="#0175C2"><circle cx="12" cy="12" r="10"/></svg><span>Dart</span></div><div class="tooltip">Cross-Platform Mobile App Development</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#100e1a;color:#9b8ec4"><svg viewBox="0 0 24 24" fill="#5E5086"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2z"/></svg><span>Haskell</span></div><div class="tooltip">Functional & Type-Theoretic Reasoning</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#1a0e00;color:#E16737"><svg viewBox="0 0 24 24" fill="#E16737"><path d="M12 2L2 7v10l10 5 10-5V7z"/></svg><span>MATLAB</span></div><div class="tooltip">Scientific Computing & Mathematical Modelling</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#1a0b00;color:#E34F26"><svg viewBox="0 0 24 24" fill="#E34F26"><path d="M1.5 0h21l-1.91 21.563L11.977 24l-8.565-2.438L1.5 0zm17.09 4.413L5.41 4.41l.213 2.622 10.125.002-.255 2.716h-6.64l.24 2.573h6.182l-.366 3.523-2.91.804-2.956-.81-.188-2.11h-2.61l.29 3.855L12 19.288l5.373-1.53L18.59 4.414z"/></svg><span>HTML5</span></div><div class="tooltip">Semantic Web Structure & Markup</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#00091a;color:#1572B6"><svg viewBox="0 0 24 24" fill="#1572B6"><path d="M1.5 0h21l-1.91 21.563L11.977 24l-8.565-2.438z"/></svg><span>CSS3</span></div><div class="tooltip">Styling, Animations & Responsive Design</div></div>
    </div>
  </div>

  <div class="stack-section">
    <div class="stack-section-title">🚀 Frameworks & Interfaces</div>
    <div class="badges-row">
      <div class="badge-wrap"><div class="badge" style="background:#001a18;color:#009688"><svg viewBox="0 0 24 24" fill="#009688"><path d="M12 2L2 7v10l10 5 10-5V7z"/></svg><span>FastAPI</span></div><div class="tooltip">High-Performance Async REST APIs</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#111;color:#e6edf3"><svg viewBox="0 0 24 24" fill="white"><circle cx="12" cy="12" r="10" fill="#000"/></svg><span>Flask</span></div><div class="tooltip">Lightweight Python Web Microframework</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#001a07;color:#44b574"><svg viewBox="0 0 24 24" fill="#092E20"><circle cx="12" cy="12" r="10" fill="#092E20" stroke="#44b574" stroke-width="1"/></svg><span>Django</span></div><div class="tooltip">Full-Stack Python Web Framework</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#1a0d00;color:#FF7C00"><svg viewBox="0 0 24 24" fill="#FF7C00"><circle cx="12" cy="12" r="10"/></svg><span>Gradio</span></div><div class="tooltip">Rapid AI/ML Demo & Interactive UI Builder</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#1a0b0b;color:#FF4B4B"><svg viewBox="0 0 24 24" fill="#FF4B4B"><path d="M12 2L2 7l10 5 10-5z"/></svg><span>Streamlit</span></div><div class="tooltip">Data Apps & ML Model Dashboards</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#001a1a;color:#61DAFB"><svg viewBox="0 0 24 24" fill="#61DAFB"><circle cx="12" cy="12" r="2.5"/><ellipse cx="12" cy="12" rx="10" ry="4.5" fill="none" stroke="#61DAFB" stroke-width="1.5"/><ellipse cx="12" cy="12" rx="10" ry="4.5" fill="none" stroke="#61DAFB" stroke-width="1.5" transform="rotate(60 12 12)"/><ellipse cx="12" cy="12" rx="10" ry="4.5" fill="none" stroke="#61DAFB" stroke-width="1.5" transform="rotate(120 12 12)"/></svg><span>React</span></div><div class="tooltip">Component-Based Modern Frontend</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#001a00;color:#339933"><svg viewBox="0 0 24 24" fill="#339933"><circle cx="12" cy="12" r="10"/></svg><span>Node.js</span></div><div class="tooltip">JavaScript Runtime for Backend Services</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#00091a;color:#02569B"><svg viewBox="0 0 24 24" fill="#02569B"><path d="M14.314 0L2.3 12 6 15.7 21.684.013h-7.357zm.014 11.072L6.857 18.53l3.7 3.7 3.371-3.371-3.857-3.857L21.7 3.143 14.328 11.07z"/></svg><span>Flutter</span></div><div class="tooltip">Cross-Platform Mobile Apps with Dart</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#001a1a;color:#06B6D4"><svg viewBox="0 0 24 24" fill="#06B6D4"><path d="M12 6L0 18h4l8-8 8 8h4L12 6z"/></svg><span>Tailwind CSS</span></div><div class="tooltip">Utility-First Framework for Rapid UI</div></div>
    </div>
  </div>

  <div class="stack-section">
    <div class="stack-section-title">🗄️ Databases</div>
    <div class="badges-row">
      <div class="badge-wrap"><div class="badge" style="background:#000d1a;color:#4169E1"><svg viewBox="0 0 24 24" fill="#4169E1"><path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2z"/></svg><span>PostgreSQL</span></div><div class="tooltip">Advanced Relational Database</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#001a00;color:#47A248"><svg viewBox="0 0 24 24" fill="#47A248"><path d="M17.193 9.555c-1.264-5.58-4.252-7.414-4.573-8.115-.28-.394-.53-.954-.735-1.44-.036.495-.055.685-.523 1.184-.723.566-4.438 3.682-4.74 10.02-.282 5.912 4.27 9.435 4.888 9.884l.07.05A73.49 73.49 0 0111.91 24h.481c.114-1.032.284-2.056.51-3.07.417-.296.604-.463.85-.693a11.342 11.342 0 003.639-8.464c.01-.814-.103-1.662-.197-2.218zm-5.336 8.195s0-8.51 3.504-9.498c-1.327 2.807-1.474 5.65-.832 7.625-.854.745-1.752 1.303-2.672 1.873z"/></svg><span>MongoDB</span></div><div class="tooltip">Flexible NoSQL Document Database</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#00091a;color:#4479A1"><svg viewBox="0 0 24 24" fill="#4479A1"><path d="M16.405 5.501c-.115 0-.193.014-.274.033v.013h.014c.054.104.146.18.214.274.054.107.1.214.154.32l.014-.015c.094-.066.14-.172.14-.333-.04-.047-.046-.094-.068-.133-.026-.045-.094-.1-.194-.159z"/></svg><span>MySQL</span></div><div class="tooltip">Open-Source Relational DBMS</div></div>
    </div>
  </div>

  <div class="stack-section">
    <div class="stack-section-title">🛠️ DevOps, Cloud & Tooling</div>
    <div class="badges-row">
      <div class="badge-wrap"><div class="badge" style="background:#1a0600;color:#F05032"><svg viewBox="0 0 24 24" fill="#F05032"><path d="M23.546 10.93L13.067.452a1.55 1.55 0 00-2.188 0L8.708 2.627l2.76 2.76a1.838 1.838 0 012.326 2.34l2.659 2.66a1.838 1.838 0 11-1.103 1.076l-2.48-2.48v6.511a1.84 1.84 0 11-1.51-.018V9.160a1.841 1.841 0 01-.999-2.42L7.917 4.003.454 11.468a1.55 1.55 0 000 2.187l10.48 10.478a1.55 1.55 0 002.186 0l10.424-10.424a1.55 1.55 0 000-2.779z"/></svg><span>Git</span></div><div class="tooltip">Version Control & Collaboration Workflows</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#1a1400;color:#FCC624"><svg viewBox="0 0 24 24" fill="#FCC624"><path d="M12 0C5.374 0 0 5.373 0 12c0 6.628 5.374 12 12 12 6.629 0 12-5.372 12-12C24 5.373 18.629 0 12 0zm0 2a10 10 0 110 20A10 10 0 0112 2z"/></svg><span>Linux</span></div><div class="tooltip">Primary Dev & Server OS</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#00091a;color:#2496ED"><svg viewBox="0 0 24 24" fill="#2496ED"><path d="M13.983 11.078h2.119a.186.186 0 00.186-.185V9.006a.186.186 0 00-.186-.186h-2.119a.185.185 0 00-.185.185v1.888c0 .102.083.185.185.185m-2.954-5.43h2.118a.186.186 0 00.186-.186V3.574a.186.186 0 00-.186-.185h-2.118a.185.185 0 00-.185.185v1.888c0 .102.082.185.185.185"/></svg><span>Docker</span></div><div class="tooltip">Containerization & Reproducible Deployments</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#1a0e00;color:#FF9900"><svg viewBox="0 0 24 24" fill="#FF9900"><path d="M6.763 10.036c0 .296.032.535.088.71.064.176.144.368.256.576.04.063.056.127.056.183 0 .08-.048.16-.152.24l-.503.335a.383.383 0 01-.208.072c-.08 0-.16-.04-.239-.112a2.47 2.47 0 01-.287-.375 6.18 6.18 0 01-.248-.471c-.622.734-1.405 1.101-2.347 1.101-.67 0-1.205-.191-1.596-.574-.391-.384-.59-.894-.59-1.533 0-.678.239-1.23.726-1.644.487-.415 1.133-.623 1.955-.623.272 0 .551.024.846.064.296.04.6.104.918.176v-.583c0-.607-.127-1.03-.375-1.277-.255-.248-.686-.367-1.3-.367-.28 0-.568.031-.863.103-.295.072-.583.16-.862.272a2.287 2.287 0 01-.28.104.488.488 0 01-.127.023c-.112 0-.168-.08-.168-.247v-.391c0-.128.016-.224.056-.28a.597.597 0 01.224-.167c.279-.144.614-.264 1.005-.36a4.84 4.84 0 011.246-.151c.95 0 1.644.216 2.091.647.439.43.662 1.085.662 1.963v2.586zm-3.24 1.214c.263 0 .534-.048.822-.144.287-.096.543-.271.758-.51.128-.152.224-.32.272-.512.047-.191.08-.423.08-.694v-.335a6.66 6.66 0 00-.735-.136 6.02 6.02 0 00-.75-.048c-.535 0-.926.104-1.19.32-.263.215-.39.518-.39.917 0 .375.095.655.295.846.191.2.47.296.838.296z"/></svg><span>AWS</span></div><div class="tooltip">Cloud Infrastructure & ML Deployment</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#1a0600;color:#D24939"><svg viewBox="0 0 24 24" fill="#D24939"><circle cx="12" cy="12" r="10"/></svg><span>Jenkins</span></div><div class="tooltip">CI/CD Pipeline Automation</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#1a1100;color:#FFCA28"><svg viewBox="0 0 24 24" fill="#FFCA28"><path d="M3.89 15.673L6.255.461A.542.542 0 017.27.288l2.543 4.771zm16.794 3.692l-2.25-14a.54.54 0 00-.919-.295L3.316 19.365l7.17 4.045a1.486 1.486 0 001.442 0zM14.3 7.148l-1.82-3.482a.542.542 0 00-.96 0L3.53 17.984z"/></svg><span>Firebase</span></div><div class="tooltip">BaaS & Real-Time Data Sync</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#1a0800;color:#F24E1E"><svg viewBox="0 0 24 24" fill="#F24E1E"><path d="M15.852 8.981h-4.588V0h4.588c2.476 0 4.49 2.014 4.49 4.49s-2.014 4.491-4.49 4.491zM12.735 7.51h3.117c1.665 0 3.019-1.355 3.019-3.019s-1.354-3.019-3.019-3.019h-3.117V7.51z"/></svg><span>Figma</span></div><div class="tooltip">UI/UX Design & Prototyping</div></div>
      <div class="badge-wrap"><div class="badge" style="background:#001a2e;color:#31A8FF"><svg viewBox="0 0 24 24" fill="#31A8FF"><path d="M13.035 0C6.088 0 .357 5.731.357 12.678c0 3.498 1.422 6.664 3.716 8.944l-.003-.003c2.308 2.298 5.48 3.72 8.965 3.72C19.982 25.34 25.714 19.61 25.714 12.66 25.713 5.73 19.982.001 13.035.001z"/></svg><span>Photoshop</span></div><div class="tooltip">Digital Image Editing & Visual Design</div></div>
    </div>
  </div>

  <hr class="divider">

  <!-- GitHub Analytics -->
  <div class="section-title"><span>📊 GitHub Analytics</span></div>
  <div class="analytics-grid">
    <div class="analytics-card">
      <img src="https://github-readme-stats.vercel.app/api?username=CholaGanesh05&show_icons=true&theme=github_dark&bg_color=161b22&title_color=D4732A&icon_color=C4621A&border_color=21262d&hide_border=false" alt="GitHub Stats" loading="lazy">
    </div>
    <div class="analytics-card">
      <img src="https://github-readme-streak-stats.herokuapp.com/?user=CholaGanesh05&theme=github-dark-blue&background=161b22&ring=D4732A&fire=C4621A&currStreakLabel=D4732A&border=21262d" alt="GitHub Streak" loading="lazy">
    </div>
  </div>

  <hr class="divider">

  <div class="footer">
    <blockquote>"The goal of AI research is not to build systems that think like humans —<br>it's to build systems that help humans think better."</blockquote>
    <p style="color:var(--muted);font-size:11px">MIT License — feel free to use, adapt, and build upon this work with attribution.</p>
  </div>

  <!-- Capsule Render Footer -->
  <div style="margin:0 -24px -40px;overflow:hidden;line-height:0;">
    <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=12,20,27&height=120&section=footer" alt="Footer Wave" style="width:100%;display:block;"/>
  </div>

</div>
</body>
</html>
