[index.html.html](https://github.com/user-attachments/files/33922857/index.html.html)
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>迎接旅客登机英语 · 实训系统</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" />
    <style>
        * { margin:0; padding:0; box-sizing:border-box; }
        body { font-family:'Segoe UI','PingFang SC',Roboto,sans-serif; background:#f0f4fa; color:#1a2a3a; padding-top:68px; line-height:1.6; }
        .navbar { position:fixed; top:0; left:0; right:0; z-index:1000; background:linear-gradient(145deg,#1a2a5e,#2c448e); padding:0 14px; height:64px; display:flex; align-items:center; justify-content:space-between; box-shadow:0 4px 20px rgba(26,42,94,0.35); gap:4px; flex-wrap:nowrap; }
        .navbar .brand { display:flex; align-items:center; gap:8px; color:#fff; font-weight:700; font-size:0.85rem; white-space:nowrap; }
        .navbar .brand i { color:#f5d98f; font-size:1.1rem; }
        .navbar .brand span { font-size:0.6rem; font-weight:400; opacity:0.6; }
        .navbar .nav-links { display:flex; gap:2px; flex-wrap:nowrap; overflow-x:auto; }
        .navbar .nav-links a { color:rgba(255,255,255,0.6); text-decoration:none; padding:4px 10px; border-radius:30px; font-size:0.65rem; font-weight:600; transition:all 0.25s; white-space:nowrap; cursor:pointer; }
        .navbar .nav-links a:hover { color:#fff; background:rgba(255,255,255,0.08); }
        .navbar .nav-links a.active { color:#1a2a5e; background:#f5d98f; }
        .navbar .right-actions { display:flex; align-items:center; gap:6px; flex-shrink:0; }
        .navbar .print-btn { background:rgba(255,255,255,0.1); border:1px solid rgba(255,255,255,0.15); color:#fff; padding:3px 12px; border-radius:30px; font-size:0.6rem; font-weight:600; cursor:pointer; display:flex; align-items:center; gap:4px; }
        .navbar .print-btn:hover { background:rgba(255,255,255,0.2); }
        .container { max-width:1100px; margin:0 auto; padding:12px 14px 30px; }
        .page { display:none; animation:fadeUp 0.3s ease; }
        .page.active { display:block; }
        @keyframes fadeUp { from { opacity:0; transform:translateY(10px); } to { opacity:1; transform:translateY(0); } }
        .card { background:#fff; border-radius:16px; padding:18px 20px; box-shadow:0 2px 12px rgba(0,0,0,0.04); margin-bottom:18px; border:1px solid rgba(0,0,0,0.02); }
        .card-title { font-size:1.05rem; font-weight:700; color:#1a2a5e; margin-bottom:12px; display:flex; align-items:center; gap:10px; }
        .card-title i { color:#c99f4a; font-size:1rem; }
        .card-title .sub { font-weight:400; font-size:0.7rem; color:#8a9eb0; margin-left:auto; }
        .section-desc { color:#4a5a6e; font-size:0.9rem; margin-bottom:12px; }
        .form-row { display:grid; grid-template-columns:repeat(auto-fit,minmax(180px,1fr)); gap:12px; }
        .form-group { display:flex; flex-direction:column; gap:3px; }
        .form-group label { font-weight:600; font-size:0.78rem; color:#1a2a5e; }
        .form-group input, .form-group textarea, .form-group select { padding:6px 12px; border-radius:8px; border:1px solid #dce4ec; font-size:0.85rem; background:#fafcff; transition:0.2s; font-family:inherit; }
        .form-group input:focus, .form-group textarea:focus, .form-group select:focus { border-color:#c99f4a; outline:none; box-shadow:0 0 0 3px rgba(201,159,74,0.08); }
        .btn { padding:5px 16px; border-radius:30px; border:none; font-weight:600; font-size:0.75rem; cursor:pointer; transition:all 0.2s; display:inline-flex; align-items:center; gap:5px; }
        .btn-primary { background:#f5d98f; color:#1a2a5e; }
        .btn-primary:hover { background:#ffe8b5; }
        .btn-success { background:#2d7d5a; color:#fff; }
        .btn-success:hover { background:#3a9d72; }
        .btn-outline { background:transparent; border:1.5px solid #dce4ec; color:#5a6e82; }
        .btn-outline:hover { border-color:#b6cce0; background:#f7faff; }
        .btn-sm { padding:3px 12px; font-size:0.65rem; }
        .text-muted { color:#8a9eb0; font-size:0.78rem; }
        .text-gold { color:#c99f4a; }

        .vocab-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(250px,1fr)); gap:12px; }
        .vocab-card { background:#f7faff; border-radius:12px; padding:14px 16px; border:1px solid #e6edf6; transition:0.2s; }
        .vocab-card:hover { border-color:#b6cce0; background:#f0f6fe; }
        .vocab-card .word { font-weight:700; font-size:1.05rem; color:#1a2a5e; }
        .vocab-card .phonetic { font-size:0.8rem; color:#8a9eb0; margin-left:6px; font-weight:400; }
        .vocab-card .meaning { font-size:0.85rem; color:#4a5a6e; margin:2px 0 6px; }
        .vocab-card .actions { display:flex; align-items:center; gap:6px; flex-wrap:wrap; margin-top:6px; }
        .vocab-card .actions .speak-btn { background:rgba(201,159,74,0.12); border:none; color:#c99f4a; width:30px; height:30px; border-radius:50%; cursor:pointer; font-size:0.8rem; }
        .vocab-card .actions .speak-btn:hover { background:#c99f4a; color:#fff; }
        .vocab-card .actions .record-btn { background:rgba(52,152,219,0.12); border:none; color:#2980b9; width:30px; height:30px; border-radius:50%; cursor:pointer; font-size:0.8rem; }
        .vocab-card .actions .record-btn:hover { background:#2980b9; color:#fff; }
        .vocab-card .actions .record-btn.recording { background:#c0392b; color:#fff; animation:pulse-icon 0.6s infinite; }
        .vocab-card .score-display { margin-top:6px; font-size:0.8rem; font-weight:600; display:flex; align-items:center; gap:6px; }
        .vocab-card .score-display .score-value { padding:2px 10px; border-radius:20px; font-size:0.85rem; }
        .score-excellent { background:#d4edda; color:#1a6e4a; }
        .score-good { background:#d6eaf8; color:#1a5276; }
        .score-fair { background:#fdebd0; color:#935e38; }
        .score-poor { background:#fadbd8; color:#922b21; }
        .score-none { background:#e6edf6; color:#8a9eb0; }
        @keyframes pulse-icon { 0%,100% { transform:scale(1); opacity:1; } 50% { transform:scale(0.85); opacity:0.6; } }
        .recognition-status { font-size:0.75rem; color:#5a6e82; padding:4px 10px; border-radius:20px; background:#f0f4f9; display:inline-block; margin-top:4px; }
        .recognition-status.active { background:#d6eaf8; color:#1a5276; }
        .recognition-status.success { background:#d4edda; color:#1a6e4a; }
        .recognition-status.error { background:#fadbd8; color:#922b21; }

        .phrase-section { margin-bottom:20px; }
        .phrase-section-title { font-weight:700; font-size:0.95rem; color:#1a2a5e; padding:8px 14px; background:#f0f4f9; border-radius:10px; margin-bottom:8px; display:flex; align-items:center; gap:10px; }
        .phrase-section-title .badge { font-size:0.65rem; font-weight:600; background:#c99f4a; color:#fff; padding:0 12px; border-radius:20px; line-height:1.8; }
        .phrase-item { padding:10px 14px; background:#f7faff; border-radius:10px; border-left:4px solid #c99f4a; margin-bottom:8px; transition:0.2s; }
        .phrase-item:hover { background:#f0f6fe; }
        .phrase-item .en-line { display:flex; flex-wrap:wrap; align-items:center; gap:3px; margin-bottom:6px; }
        .phrase-item .en-line .word-chip { display:inline-block; padding:2px 7px; border-radius:6px; font-weight:600; font-size:0.92rem; color:#1a2a5e; cursor:pointer; user-select:none; transition:0.15s; }
        .phrase-item .en-line .word-chip:hover { background:rgba(201,159,74,0.15); color:#c99f4a; }
        .phrase-item .en-line .word-chip.speaking { background:#c99f4a; color:#fff; animation:pulse-icon 0.8s infinite; }
        .phrase-item .zh-line { color:#4a5a6e; font-size:0.85rem; padding-left:2px; margin-bottom:6px; }
        .phrase-item .sentence-actions { display:flex; align-items:center; gap:8px; flex-wrap:wrap; padding-top:6px; border-top:1px dashed #e6edf6; }
        .btn-sentence { background:linear-gradient(135deg,#c99f4a,#e0b96a); border:none; color:#fff; padding:5px 14px; border-radius:20px; font-size:0.72rem; font-weight:600; cursor:pointer; display:inline-flex; align-items:center; gap:5px; transition:0.2s; box-shadow:0 2px 6px rgba(201,159,74,0.25); }
        .btn-sentence:hover { background:linear-gradient(135deg,#b88f3a,#c99f4a); transform:translateY(-1px); }
        .btn-sentence.playing { background:linear-gradient(135deg,#2d7d5a,#3a9d72); animation:pulse-icon 0.8s infinite; }

        .dialogue-grid { display:grid; grid-template-columns:repeat(auto-fill,minmax(460px,1fr)); gap:20px; }
        .dialogue-card { background:#ffffff; border-radius:16px; padding:20px 22px; border:1px solid #e6edf6; transition:0.25s; display:flex; flex-direction:column; box-shadow:0 2px 6px rgba(0,0,0,0.02); }
        .dialogue-card:hover { border-color:#b6cce0; box-shadow:0 4px 16px rgba(0,0,0,0.06); }
        .dialogue-card .d-header { display:flex; align-items:center; gap:12px; margin-bottom:14px; flex-wrap:wrap; border-bottom:1px solid #f0f4f9; padding-bottom:10px; }
        .dialogue-card .d-num { font-size:0.65rem; font-weight:700; color:#c99f4a; background:rgba(201,159,74,0.12); padding:3px 14px; border-radius:30px; }
        .dialogue-card .d-title { font-weight:700; font-size:1.05rem; color:#1a2a5e; }
        .dialogue-card .d-scene-label { font-size:0.7rem; color:#8a9eb0; margin-left:auto; background:#e6edf6; padding:2px 14px; border-radius:30px; }
        .dialogue-card .d-body { display:flex; flex-direction:column; gap:8px; margin:6px 0 12px; max-height:620px; overflow-y:auto; padding-right:4px; }
        .dialogue-card .d-body::-webkit-scrollbar { width:4px; }
        .dialogue-card .d-body::-webkit-scrollbar-thumb { background:#c99f4a; border-radius:10px; }
        .dialogue-card .d-line { padding:10px 14px; border-radius:12px; background:#fafcff; border-left:4px solid #c99f4a; }
        .dialogue-card .d-line.crew { background:#f2f6fc; border-left-color:#2c448e; }
        .dialogue-card .d-line.passenger { background:#f7faff; border-left-color:#2980b9; }
        .dialogue-card .d-line .d-speaker { font-weight:700; font-size:0.8rem; color:#4a5a6e; display:flex; align-items:center; gap:6px; margin-bottom:4px; }
        .dialogue-card .d-line .d-en-line { display:flex; flex-wrap:wrap; align-items:center; gap:3px; margin-bottom:4px; }
        .dialogue-card .d-line .d-en-line .word-chip { display:inline-block; padding:2px 7px; border-radius:6px; font-weight:600; font-size:0.98rem; color:#1a2a3a; cursor:pointer; user-select:none; transition:0.15s; }
        .dialogue-card .d-line .d-en-line .word-chip:hover { background:rgba(201,159,74,0.15); color:#c99f4a; }
        .dialogue-card .d-line .d-en-line .word-chip.speaking { background:#c99f4a; color:#fff; animation:pulse-icon 0.8s infinite; }
        .dialogue-card .d-line .d-trans { font-size:0.88rem; color:#5a6e82; line-height:1.5; padding-top:4px; border-top:1px dashed rgba(0,0,0,0.05); margin-bottom:6px; }
        .dialogue-card .d-line .d-actions { display:flex; align-items:center; gap:8px; flex-wrap:wrap; }
        .dialogue-card .d-audio-bar { display:flex; align-items:center; gap:8px; margin-top:12px; padding-top:12px; border-top:1px solid #e6edf6; flex-wrap:wrap; }
        .dialogue-card .d-audio-bar .btn-audio-sm { background:rgba(201,159,74,0.1); border:none; color:#c99f4a; padding:5px 14px; border-radius:30px; font-size:0.7rem; font-weight:600; cursor:pointer; display:inline-flex; align-items:center; gap:6px; }
        .dialogue-card .d-audio-bar .btn-audio-sm:hover { background:#c99f4a; color:#fff; }
        .dialogue-card .d-audio-bar .btn-audio-sm.playing { background:#2d7d5a; color:#fff; animation:pulse-icon 0.8s infinite; }
        .dialogue-card .d-audio-bar .btn-recording-sm { background:rgba(41,128,185,0.1); border:none; color:#2980b9; padding:5px 14px; border-radius:30px; font-size:0.7rem; font-weight:600; cursor:pointer; display:inline-flex; align-items:center; gap:6px; }
        .dialogue-card .d-audio-bar .btn-recording-sm:hover { background:#2980b9; color:#fff; }
        .dialogue-card .d-audio-bar .btn-recording-sm.recording { background:#c0392b; color:#fff; animation:pulse-icon 0.6s infinite; }
        .dialogue-card .d-audio-bar .d-status { font-size:0.7rem; color:#8a9eb0; }
        .dialogue-card .d-audio-bar .d-status.done { color:#2d7d5a; font-weight:600; }

        .case-card { display:grid; grid-template-columns:1fr 1fr; gap:16px; }
        .case-card .info-item { background:#f7faff; border-radius:10px; padding:12px 16px; border:1px solid #e6edf6; }
        .case-card .info-item .label { font-weight:600; font-size:0.75rem; color:#8a9eb0; text-transform:uppercase; letter-spacing:0.5px; }
        .case-card .info-item .value { font-weight:700; font-size:1rem; color:#1a2a5e; margin-top:2px; }
        .case-card .info-item .value.en { color:#2980b9; font-weight:600; font-size:0.9rem; }
        .case-card .info-item .value.zh { color:#4a5a6e; font-size:0.85rem; }
        @media (max-width:600px) { .case-card { grid-template-columns:1fr; } }

        .role-grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(180px,1fr)); gap:12px; }
        .role-card { background:#f7faff; border-radius:12px; padding:12px 14px; border:1px solid #e6edf6; }
        .role-card .r-title { font-weight:700; font-size:0.85rem; color:#1a2a5e; display:flex; align-items:center; gap:6px; }
        .role-card .r-title .icon { color:#c99f4a; }
        .role-card .r-name input { width:100%; padding:4px 10px; border-radius:6px; border:1px solid #dce4ec; font-size:0.8rem; background:#fff; margin-top:4px; }

        .script-step { display:flex; align-items:center; gap:10px; padding:8px 12px; background:#fafcff; border-radius:8px; border:1px solid #e6edf6; margin-bottom:6px; flex-wrap:wrap; }
        .script-step .step-num { font-weight:700; font-size:0.75rem; color:#8a9eb0; min-width:30px; }
        .script-step select, .script-step input { padding:4px 8px; border-radius:6px; border:1px solid #dce4ec; font-size:0.8rem; background:#fff; flex:1 1 140px; min-width:100px; }
        .script-step .custom-input { flex:2 1 180px; }
        .script-step .btn-remove-step { background:transparent; border:none; color:#c0392b; cursor:pointer; font-size:0.8rem; padding:2px 6px; }
        .script-preview { background:#f7faff; border-radius:10px; padding:12px 16px; border:1px solid #e6edf6; margin-top:10px; white-space:pre-wrap; font-family:'Consolas',monospace; font-size:0.85rem; line-height:1.8; max-height:300px; overflow-y:auto; }

        .eval-item { display:flex; align-items:center; gap:12px; padding:8px 14px; background:#f7faff; border-radius:10px; border:1px solid #e6edf6; flex-wrap:wrap; }
        .eval-item .e-label { font-weight:600; font-size:0.82rem; color:#1a2a5e; min-width:100px; }
        .eval-item .e-desc { font-size:0.75rem; color:#5a6e82; flex:1; min-width:80px; }
        .eval-item .e-score-input select { padding:3px 8px; border-radius:6px; border:1px solid #dce4ec; font-size:0.8rem; background:#fff; font-weight:600; width:70px; }
        .score-summary { display:grid; grid-template-columns:repeat(auto-fit,minmax(160px,1fr)); gap:14px; margin-bottom:16px; }
        .score-box { background:#f7faff; border-radius:12px; padding:14px 16px; text-align:center; border:1px solid #e6edf6; }
        .score-box .label { font-size:0.72rem; color:#5a6e82; }
        .score-box .value { font-size:1.8rem; font-weight:700; color:#1a2a5e; }
        .score-box .value.gold { color:#c99f4a; }
        .score-box .value.green { color:#2d7d5a; }
        .score-box .weight { font-size:0.65rem; color:#8a9eb0; }
        .score-detail table { width:100%; border-collapse:collapse; font-size:0.82rem; }
        .score-detail th { background:#f0f4f9; padding:6px 10px; text-align:left; font-weight:700; color:#1a2a5e; border-bottom:2px solid #dce4ec; }
        .score-detail td { padding:5px 10px; border-bottom:1px solid #e6edf6; }

        .toast { position:fixed; bottom:24px; right:24px; background:#1a2a5e; color:#fff; padding:8px 20px; border-radius:12px; box-shadow:0 8px 24px rgba(0,0,0,0.2); font-weight:600; transform:translateY(100px); opacity:0; transition:all 0.4s ease; z-index:999; max-width:400px; font-size:0.8rem; }
        .toast.show { transform:translateY(0); opacity:1; }
        .toast.success { background:#2d7d5a; }
        .toast.error { background:#c0392b; }
        .toast.info { background:#2980b9; }
        .footer { text-align:center; padding:14px 0 4px; color:#8a9eb0; font-size:0.65rem; border-top:1px solid #e6edf6; margin-top:4px; }
        .footer i { color:#c99f4a; }

        @media print {
            body { padding-top:0; background:#fff; }
            .navbar { display:none !important; }
            .page { display:block !important; animation:none !important; }
            .card { box-shadow:none !important; border:1px solid #ddd; }
            .btn { display:none !important; }
            .btn-sentence { display:none !important; }
            .dialogue-grid { grid-template-columns:repeat(2,1fr); }
            .vocab-grid { grid-template-columns:repeat(2,1fr); }
            .word-chip { background:none !important; color:#000 !important; }
        }
        @media (max-width:820px) {
            .navbar { padding:0 10px; height:56px; }
            .navbar .brand { font-size:0.7rem; }
            .navbar .brand span { display:none; }
            .navbar .nav-links a { font-size:0.55rem; padding:3px 8px; }
            body { padding-top:60px; }
            .container { padding:10px; }
            .vocab-grid { grid-template-columns:repeat(auto-fill,minmax(180px,1fr)); }
            .dialogue-grid { grid-template-columns:1fr; }
            .role-grid { grid-template-columns:1fr 1fr; }
            .form-row { grid-template-columns:1fr; }
            .score-summary { grid-template-columns:1fr 1fr; }
        }
        @media (max-width:480px) {
            .navbar .nav-links a { font-size:0.5rem; padding:2px 6px; }
            .navbar .brand { font-size:0.6rem; }
            .navbar .right-actions .print-btn span { display:none; }
            .vocab-grid { grid-template-columns:1fr; }
            .role-grid { grid-template-columns:1fr; }
            .score-summary { grid-template-columns:1fr; }
            .dialogue-grid { grid-template-columns:1fr; }
            .case-card { grid-template-columns:1fr; }
        }
    </style>
</head>
<body>

    <nav class="navbar" id="navbar">
        <div class="brand">
            <i class="fas fa-plane-departure"></i>
            迎接登机 <span>· 英语实训</span>
        </div>
        <div class="nav-links">
            <a class="active" data-page="page-info"><i class="fas fa-info-circle"></i> 小组</a>
            <a data-page="page-case"><i class="fas fa-clipboard-list"></i> 案例信息</a>
            <a data-page="page-vocab"><i class="fas fa-book-open"></i> 词汇</a>
            <a data-page="page-phrases"><i class="fas fa-comment-dots"></i> 句型</a>
            <a data-page="page-dialogue"><i class="fas fa-comments"></i> 对话卡片</a>
            <a data-page="page-performance"><i class="fas fa-user-tag"></i> 模拟展演</a>
            <a data-page="page-eval"><i class="fas fa-chalkboard-teacher"></i> 师评成绩</a>
        </div>
        <div class="right-actions">
            <button class="print-btn" onclick="window.print()"><i class="fas fa-print"></i> <span>打印</span></button>
        </div>
    </nav>

    <div class="container">

        <!-- 小组信息 -->
        <div class="page active" id="page-info">
            <div class="card">
                <div class="card-title"><i class="fas fa-info-circle"></i> 小组基本信息</div>
                <div class="form-row">
                    <div class="form-group"><label><i class="fas fa-school"></i> 班级</label><input type="text" id="className" placeholder="请输入班级" /></div>
                    <div class="form-group"><label><i class="fas fa-tag"></i> 小组名称</label><input type="text" id="groupName" placeholder="如：第1组 / Boarding Team" /></div>
                    <div class="form-group"><label><i class="fas fa-hashtag"></i> 小组编号</label><input type="text" id="groupId" placeholder="如：G01" /></div>
                    <div class="form-group"><label><i class="fas fa-tasks"></i> 实训任务</label><input type="text" id="taskName" value="迎接旅客登机英语实训" /></div>
                    <div class="form-group"><label><i class="fas fa-user-tie"></i> 指导教师</label><input type="text" id="teacherName" placeholder="请输入姓名" /></div>
                </div>
                <div style="margin-top:10px;">
                    <button class="btn btn-success" id="saveInfoBtn"><i class="fas fa-save"></i> 保存信息</button>
                    <span class="text-muted" style="margin-left:10px;">数据自动保存在浏览器</span>
                </div>
            </div>
            <div class="card">
                <div class="card-title"><i class="fas fa-clipboard-list"></i> 任务说明</div>
                <p style="color:#4a5a6e;font-size:0.92rem;">
                    本实训系统基于 <strong>HU7480 三亚→北京 航班登机阶段服务</strong> 真实案例设计。
                    通过 <strong>词汇跟读评分</strong>、<strong>句型逐词发音</strong>、<strong>对话卡片学习</strong>、<strong>模拟展演对话编排</strong> 四个环节，
                    掌握 <strong>6大情境、55+核心句型</strong>，实现“会认、会说、会用”的学习目标。
                </p>
                <div style="background:#fcf9f0;border-radius:10px;padding:12px 16px;border-left:4px solid #c99f4a;margin-top:10px;">
                    <strong style="color:#1a2a5e;">💡 特色功能：</strong>
                    <span style="color:#4a5a6e;font-size:0.88rem;">① 点击任意单词听发音并显示中文释义；② 每句提供"整句朗读"按钮；③ 支持跟读评分与对话录音。</span>
                </div>
            </div>
        </div>

        <!-- 案例信息 -->
        <div class="page" id="page-case">
            <div class="card">
                <div class="card-title"><i class="fas fa-clipboard-list"></i> HU7480 迎接旅客登机案例 <span class="sub">案例详情</span></div>
                <p class="section-desc">以下为本次迎接旅客登机英语实训所使用的完整案例信息。</p>
                <div style="background:#f7faff;border-radius:10px;padding:14px 16px;border-left:4px solid #c99f4a;margin-bottom:14px;">
                    <p style="color:#1a2a5e;font-size:0.92rem;line-height:1.8;">
                        <strong>✈️ 航班：</strong> HU7480 三亚（SYX）→ 北京（PEK）<br>
                        <strong>📅 日期：</strong> 2025年1月20日 &nbsp;|&nbsp; <strong>机型：</strong> 空客 A330-300<br>
                        <strong>⏰ 阶段：</strong> 旅客登机阶段（离港时间 22:10）
                    </p>
                </div>
                <div style="background:#fcf9f0;border-radius:10px;padding:12px 16px;border-left:4px solid #c99f4a;margin-bottom:14px;">
                    <p style="color:#1a2a5e;font-size:0.9rem;line-height:1.8;">
                        <strong>📋 案例描述：</strong><br>
                        在一趟三亚飞往北京的航班上，旅客正在陆续登机。乘务员在客舱门口迎接旅客，查验登机牌，指引旅客前往指定座位，并解答关于起飞和降落时间的询问。在登机过程中，乘务员会遇到各种情况：旅客想与家人坐在一起而请求换座；旅客坐错座位需引导回原座；旅客询问航班信息；以及旅客提出机上升舱的需求。乘务员需用英语专业、礼貌地与旅客沟通，提供合理的解决方案，确保登机过程顺畅有序。
                    </p>
                </div>
                <div class="case-card">
                    <div class="info-item"><div class="label">服务场景 / Scenarios</div><div class="value en">Greeting / Seat / Upgrade</div><div class="value zh">问候 / 座位 / 升舱</div></div>
                    <div class="info-item"><div class="label">核心证件 / Documents</div><div class="value en">Boarding Pass / Seat Number</div><div class="value zh">登机牌 / 座位号</div></div>
                    <div class="info-item"><div class="label">座位服务 / Seat Service</div><div class="value en">Change Seats / Assigned Seat</div><div class="value zh">调换座位 / 指定座位</div></div>
                    <div class="info-item"><div class="label">航班信息 / Flight Info</div><div class="value en">Take off / Land / Flight Time</div><div class="value zh">起飞 / 降落 / 飞行时间</div></div>
                </div>
                <div style="margin-top:14px;background:#fcf9f0;border-radius:10px;padding:10px 16px;border-left:4px solid #c99f4a;">
                    <strong style="color:#1a2a5e;">📌 案例要点：</strong>
                    <span style="color:#4a5a6e;font-size:0.9rem;">登机阶段覆盖6大情境：问候与查验登机牌、指引座位、换座（与家人同行）、换座（坐错座位）、旅客询问航班信息、机上升舱。所有补充句型已归入这6类情境中。</span>
                </div>
            </div>
        </div>

        <!-- 词汇 -->
        <div class="page" id="page-vocab">
            <div class="card">
                <div class="card-title"><i class="fas fa-book-open"></i> 迎接旅客登机核心词汇 <span class="sub">点击 <i class="fas fa-volume-up"></i> 听发音 · 点击 <i class="fas fa-microphone"></i> 跟读评分</span></div>
                <p class="section-desc">共25个迎接旅客登机专属词汇，点击喇叭听标准发音，点击麦克风跟读评分。</p>
                <div class="vocab-grid" id="vocabGrid"></div>
                <div style="margin-top:12px;display:flex;gap:10px;flex-wrap:wrap;align-items:center;">
                    <button class="btn btn-outline btn-sm" id="resetVocabScoresBtn"><i class="fas fa-redo-alt"></i> 重置所有评分</button>
                    <span class="text-muted" id="vocabProgress">已学 0/25 个词汇</span>
                </div>
            </div>
        </div>

        <!-- 句型 -->
        <div class="page" id="page-phrases">
            <div class="card">
                <div class="card-title"><i class="fas fa-comment-dots"></i> 迎接旅客登机常用句型 <span class="sub">6大情境 · 55+核心句型 · 点击单词发音 · 点击按钮听整句</span></div>
                <p class="section-desc">
                    <strong>①</strong> 点击句中任意单词 → 听该单词发音并显示中文释义；
                    <strong>②</strong> 点击 <i class="fas fa-volume-up text-gold"></i> <strong>整句朗读</strong>按钮 → 听整句标准发音。
                </p>
                <div id="phraseContainer"></div>
            </div>
        </div>

        <!-- 对话卡片 -->
        <div class="page" id="page-dialogue">
            <div class="card">
                <div class="card-title"><i class="fas fa-comments"></i> 迎接旅客登机对话卡片 <span class="sub">点击单词发音 · 点击按钮听整句 · 支持录音</span></div>
                <p class="section-desc">
                    <strong>点击台词中任意单词</strong>可听该单词发音并显示中文释义；<strong>点击台词下方的"整句朗读"按钮</strong>可听整句发音。
                </p>
                <div class="dialogue-grid" id="dialogueGrid"></div>
                <div style="margin-top:12px;display:flex;gap:10px;flex-wrap:wrap;align-items:center;">
                    <button class="btn btn-outline btn-sm" id="clearDialogueRecordingsBtn"><i class="fas fa-trash-alt"></i> 清除所有录音</button>
                    <span class="text-muted" id="dialogueProgress">已录音 0/6 个对话</span>
                </div>
            </div>
        </div>

        <!-- 模拟展演 -->
        <div class="page" id="page-performance">
            <div class="card">
                <div class="card-title"><i class="fas fa-user-tag"></i> 1. 角色分工（6人一组）</div>
                <div class="role-grid" id="roleGrid"></div>
                <div style="margin-top:12px;">
                    <button class="btn btn-success" id="saveRolesBtn"><i class="fas fa-save"></i> 保存角色分配</button>
                </div>
            </div>
            <div class="card">
                <div class="card-title"><i class="fas fa-pen-fancy"></i> 2. 对话文本编写</div>
                <div id="scriptEditor">
                    <div id="scriptStepsContainer"></div>
                    <div style="margin-top:8px;display:flex;gap:8px;flex-wrap:wrap;">
                        <button class="btn btn-primary btn-sm" id="addStepBtn"><i class="fas fa-plus"></i> 添加步骤</button>
                        <button class="btn btn-outline btn-sm" id="resetScriptBtn"><i class="fas fa-redo-alt"></i> 重置为默认流程</button>
                        <span class="text-muted" style="font-size:0.7rem;">共 <span id="stepCount">0</span> 个步骤</span>
                    </div>
                </div>
                <div style="margin-top:14px;">
                    <button class="btn btn-success" id="previewScriptBtn"><i class="fas fa-eye"></i> 预览对话</button>
                    <button class="btn btn-primary" id="downloadScriptBtn"><i class="fas fa-download"></i> 下载对话文本</button>
                </div>
                <div id="scriptPreviewContainer" style="margin-top:12px;display:none;">
                    <div class="card" style="background:#f7faff;border:1px solid #e6edf6;border-radius:10px;padding:12px 16px;">
                        <div class="card-title" style="font-size:0.95rem;margin-bottom:6px;"><i class="fas fa-file-alt text-gold"></i> 对话预览</div>
                        <div class="script-preview" id="scriptPreviewText"></div>
                    </div>
                </div>
            </div>
            <div class="card">
                <div class="card-title"><i class="fas fa-clipboard-check"></i> 3. 模拟展演评分（教师用）</div>
                <div id="roleplayEvalContainer"></div>
                <div style="margin-top:10px;">
                    <button class="btn btn-success" id="saveRoleplayEvalBtn"><i class="fas fa-save"></i> 保存评分</button>
                </div>
            </div>
        </div>

        <!-- 师评成绩 -->
        <div class="page" id="page-eval">
            <div class="card">
                <div class="card-title"><i class="fas fa-chalkboard-teacher"></i> 教师综合评价</div>
                <div id="teacherEvalContainer"></div>
                <div style="margin-top:10px;">
                    <button class="btn btn-success" id="saveTeacherEvalBtn"><i class="fas fa-save"></i> 保存师评</button>
                </div>
            </div>
            <div class="card">
                <div class="card-title"><i class="fas fa-chart-bar"></i> 成绩总览</div>
                <p class="text-muted" style="margin-bottom:10px;">最终成绩 = 词汇掌握 × 20% + 对话理解 × 30% + 模拟展演 × 50%</p>
                <div id="scoreSummary"></div>
                <div id="scoreDetail" class="score-detail"></div>
            </div>
        </div>

        <div class="footer">
            <i class="fas fa-plane-departure"></i> 迎接旅客登机英语 · 实训系统 &nbsp;|&nbsp; 数据本地存储
            <br><span style="font-size:0.6rem;">"微笑迎客，专业服务" —— 以专业态度，学好登机服务英语</span>
        </div>
    </div>

    <div class="toast" id="toast"></div>

    <script>
        const STORAGE_KEY = 'boarding_service_system_v3';

        // ===== 25个迎接旅客登机核心词汇 =====
        const VOCAB_DATA = [
            { word: 'boarding pass', phonetic: '/ˈbɔːrdɪŋ pæs/', meaning: 'n. 登机牌' },
            { word: 'seat number', phonetic: '/siːt ˈnʌmbər/', meaning: 'n. 座位号' },
            { word: 'assigned seat', phonetic: '/əˈsaɪnd siːt/', meaning: 'n. 指定座位' },
            { word: 'aisle seat', phonetic: '/aɪl siːt/', meaning: 'n. 靠走道座位' },
            { word: 'window seat', phonetic: '/ˈwɪndoʊ siːt/', meaning: 'n. 靠窗座位' },
            { word: 'overhead compartment', phonetic: '/ˌoʊvərˈhed kəmˈpɑːrtmənt/', meaning: 'n. 头顶行李架' },
            { word: 'cabin', phonetic: '/ˈkæbɪn/', meaning: 'n. 客舱' },
            { word: 'take off', phonetic: '/teɪk ɔːf/', meaning: 'phr. 起飞' },
            { word: 'land', phonetic: '/lænd/', meaning: 'v. 降落' },
            { word: 'scheduled', phonetic: '/ˈskedʒuːld/', meaning: 'adj. 计划的，预计的' },
            { word: 'flight time', phonetic: '/flaɪt taɪm/', meaning: 'n. 飞行时间' },
            { word: 'upgrade', phonetic: '/ˈʌpɡreɪd/', meaning: 'v. 升舱' },
            { word: 'business class', phonetic: '/ˈbɪznəs klæs/', meaning: 'n. 公务舱 / 商务舱' },
            { word: 'economy class', phonetic: '/ɪˈkɑːnəmi klæs/', meaning: 'n. 经济舱' },
            { word: 'legroom', phonetic: '/ˈleɡruːm/', meaning: 'n. 腿部空间' },
            { word: 'luggage allowance', phonetic: '/ˈlʌɡɪdʒ əˈlaʊəns/', meaning: 'n. 免费行李额' },
            { word: 'shuttle bus service', phonetic: '/ˈʃʌtl bʌs ˈsɜːrvɪs/', meaning: 'n. 摆渡车服务' },
            { word: 'Frequent Flyer', phonetic: '/ˈfriːkwənt ˈflaɪər/', meaning: 'n. 常旅客' },
            { word: 'mileage', phonetic: '/ˈmaɪlɪdʒ/', meaning: 'n. 里程积分' },
            { word: 'original cabin class', phonetic: '/əˈrɪdʒənl ˈkæbɪn klæs/', meaning: 'n. 原舱位' },
            { word: 'balance', phonetic: '/ˈbæləns/', meaning: 'n. 平衡（配载平衡）' },
            { word: 'safety reason', phonetic: '/ˈseɪfti ˈriːzn/', meaning: 'n. 安全原因' },
            { word: 'change seats', phonetic: '/tʃeɪndʒ siːts/', meaning: 'phr. 调换座位' },
            { word: 'purser', phonetic: '/ˈpɜːrsər/', meaning: 'n. 乘务长' },
            { word: 'welcome aboard', phonetic: '/ˈwelkəm əˈbɔːrd/', meaning: 'phr. 欢迎登机' }
        ];

        // ===== 单词中文释义词典 =====
        const WORD_DICT = {
            'good':'好的','morning':'早上','afternoon':'下午','evening':'晚上','welcome':'欢迎','aboard':'登机',
            'sir':'先生','madam':'女士','miss':'女士','excuse':'打扰','me':'我','please':'请','thank':'感谢',
            'thanks':'谢谢','you':'您','your':'您的','sorry':'抱歉','yes':'是的','no':'不','may':'可以',
            'i':'我','see':'看','boarding':'登机','pass':'牌/通行证','here':'这里','are':'是','where':'哪里',
            'is':'是','my':'我的','seat':'座位','number':'号码','could':'能','show':'展示','this':'这个',
            'that':'那个','the':'这个','a':'一个','an':'一个','and':'和','in':'在……里','on':'在……上',
            'at':'在','to':'到','of':'……的','for':'为了','with':'和','from':'从','we':'我们','our':'我们的',
            'it':'它','help':'帮助','put':'放','place':'放置','bag':'包','baggage':'行李','luggage':'行李',
            'suitcase':'手提箱','overhead':'头顶的','bin':'行李架','compartment':'行李架','under':'在……下面',
            'front':'前面','behind':'后面','aisle':'过道','window':'窗户','row':'排','rear':'后部','across':'穿过',
            'turn':'转','right':'右','left':'左','edge':'边缘','when':'什么时候','going':'将要','to':'去',
            'take':'拿/带','off':'离开','take off':'起飞','land':'降落','landing':'降落','flight':'航班',
            'time':'时间','hours':'小时','hour':'小时','around':'大约','o\'clock':'点钟','scheduled':'计划的',
            'would':'会','like':'喜欢','change':'换','gentleman':'先生','family':'家人','sit':'坐',
            'together':'一起','because':'因为','his':'他的','three':'三','rows':'排','back':'后面','also':'也',
            'problem':'问题','want':'想要','too':'也','great':'太好了','many':'许多','thanks':'谢谢',
            'legroom':'腿部空间','narrow':'狭窄的','certainly':'当然','till':'直到','try':'尝试','arrange':'安排',
            'later':'稍后','pleasure':'荣幸','could':'能','comfortable':'舒适的','keep':'保持','balance':'平衡',
            'passengers':'旅客','allowed':'被允许','before':'在……之前','or':'或者','understanding':'理解',
            'anything':'任何事','can':'可以','let':'让','us':'我们','know':'知道',
            'upgrade':'升舱','just':'只是','information':'信息','business':'商务','class':'舱位','meal':'餐食',
            'allowance':'额度','service':'服务','shuttle':'摆渡','bus':'巴士','if':'如果','frequent':'常',
            'flyer':'旅客','fortune':'财富','wings':'翅膀','club':'俱乐部','mileage':'里程','accumulated':'累积',
            'based':'基于','original':'原来的','still':'仍然','second':'一会儿','attend':'处理','short':'短的',
            'while':'一会儿','nice':'高兴','mr':'先生','green':'格林','charge':'收费','yuan':'元',
            'how':'怎么样','pay':'支付','by':'通过','alipay':'支付宝','wechat':'微信','cash':'现金',
            'prefer':'更喜欢','scan':'扫描','qr':'二维码','code':'代码','colleague':'同事',
            'enjoy':'享受','have':'有','goodbye':'再见','middle':'中间','section':'区域','follow':'跟随',
            'ahead':'向前','straight':'直的','last':'最后的','third':'第三','vacant':'空的','empty':'空的',
            'available':'可用的','confirm':'确认','wrong':'错误的','afraid':'恐怕','return':'返回','assigned':'指定的',
            'ground':'地面','staff':'工作人员','soon':'很快','next':'旁边的','lady':'女士','child':'孩子',
            'mind':'介意','talked':'谈过','prefers':'更喜欢','anymore':'再','extra':'额外的','step':'走',
            'aside':'旁边','through':'通过','recline':'放倒','right now':'立刻','first class':'头等舱',
            'no more':'没有更多','moment':'一会儿','shortly':'很快','note':'注意','include':'包含'
        };

        // ===== 核心句型（6大情境，优化后55+句型） =====
        const PHRASE_DATA = [
            // ===== 情境一：问候与查验登机牌 =====
            { en: 'Good morning, sir. Welcome aboard!', zh: '早上好，先生。欢迎登机！', tag: '问候与查验' },
            { en: 'Welcome aboard.', zh: '欢迎登机。', tag: '问候与查验' },
            { en: 'May I see your boarding pass, please?', zh: '我能看一下您的登机牌吗？', tag: '问候与查验' },
            { en: 'May I see your boarding pass? We need to confirm your seat number.', zh: '我能看一下您的登机牌吗？我们需要确认您的座位号。', tag: '问候与查验' },
            { en: 'Here you are.', zh: '给您。', tag: '问候与查验' },
            { en: 'Your seat number is 54K, at the rear of the cabin.', zh: '您的座位号是54K，在后舱。', tag: '问候与查验' },
            { en: 'Enjoy your flight!', zh: '祝您旅途愉快！', tag: '问候与查验' },

            // ===== 情境二：指引座位 =====
            { en: 'Your seat number is on the edge of the overhead compartment.', zh: '座位号在行李架的边缘。', tag: '指引座位' },
            { en: 'Please go straight ahead and turn right.', zh: '请直走，然后右转。', tag: '指引座位' },
            { en: 'It\'s at the front of the cabin.', zh: '在客舱前部。', tag: '指引座位' },
            { en: 'Let me help you find your seat.', zh: '我来帮您找座位。', tag: '指引座位' },
            { en: 'If you need anything, please press the call button.', zh: '如果需要帮助，请按呼唤铃。', tag: '指引座位' },
            { en: 'Your seat is in the middle section. Please follow me.', zh: '您的座位在中间区域，请跟我来。', tag: '指引座位' },
            { en: 'Please take this aisle to your seat.', zh: '请走这条过道到您的座位。', tag: '指引座位' },
            { en: 'Your seat is in the back of the plane. Right this way, please.', zh: '您的座位在飞机后部，请这边走。', tag: '指引座位' },
            { en: 'It\'s in the front row. Just go straight ahead and you\'ll see it.', zh: '在前排，请直走就能看到。', tag: '指引座位' },
            { en: 'Please take this aisle. Your seat is in the third row from the last.', zh: '请走这条过道，您的座位在倒数第三排。', tag: '指引座位' },
            { en: 'Would you like me to help you with your baggage?', zh: '需要我帮您拿行李吗？', tag: '指引座位' },
            { en: 'Excuse me, sir/madam. Could you please step aside so the passengers behind can pass?', zh: '打扰一下，先生/女士，请您侧身让后面的旅客通过好吗？', tag: '指引座位' },

            // ===== 情境三：换座位——与家人同行 =====
            { en: 'Excuse me, sir. May I ask you something?', zh: '打扰一下，先生。能问您一件事吗？', tag: '换座-与家人' },
            { en: 'Would you mind changing seats with this gentleman?', zh: '您介意和这位先生换一下座位吗？', tag: '换座-与家人' },
            { en: 'He would like to sit with his family.', zh: '他想和家人坐在一起。', tag: '换座-与家人' },
            { en: 'It\'s three rows back and it\'s also an aisle seat.', zh: '就在三排后面，也是一个靠走道座位。', tag: '换座-与家人' },
            { en: 'Great. Thank you very much.', zh: '太好了，非常感谢。', tag: '换座-与家人' },
            { en: 'The lady next to you would like to sit with her child. Would you mind changing seats with her?', zh: '您旁边的女士想和她的孩子坐在一起。您介意和她换一下座位吗？', tag: '换座-与家人' },
            { en: 'I\'m sorry. I\'ve talked with the passenger, but she still prefers the window seat.', zh: '抱歉，我已和那位旅客沟通过，但她还是更喜欢靠窗座位。', tag: '换座-与家人' },
            { en: 'I\'m sorry. Please take a seat for the time being. I\'ll check with the ground staff and be back soon.', zh: '抱歉，请您先坐下。我去和地面工作人员确认一下，马上回来。', tag: '换座-与家人' },
            { en: 'I\'ll check if there are any empty seats in the first row after boarding.', zh: '登机结束后我帮您看看第一排有没有空座位。', tag: '换座-与家人' },
            { en: '23C is vacant. You can move there after take-off.', zh: '23C是空的，您可以在起飞后换到那里坐。', tag: '换座-与家人' },
            { en: '32K is available. You can move there after take-off.', zh: '32K空着，您可以在起飞后过去坐。', tag: '换座-与家人' },
            { en: 'I\'m sorry, there are no empty seats on board.', zh: '抱歉，机上没有空座位了。', tag: '换座-与家人' },

            // ===== 情境四：换座位——坐错座位 =====
            { en: 'May I see your boarding pass, please?', zh: '我能看一下您的登机牌吗？', tag: '换座-坐错' },
            { en: 'Your seat number is 32A, in the front of the cabin.', zh: '您的座位号是32A，在客舱前部。', tag: '换座-坐错' },
            { en: 'I\'m afraid you need to return to your seat for safety reasons.', zh: '为了您的安全，恐怕您需要回到自己的座位。', tag: '换座-坐错' },
            { en: 'For weight and balance, passengers cannot change seats before take-off or landing.', zh: '为了配载平衡，旅客在起飞前和落地前不能调换座位。', tag: '换座-坐错' },
            { en: 'When we reach cruising altitude, you can change seats.', zh: '到达巡航高度后，您可以换座位。', tag: '换座-坐错' },
            { en: 'I\'m afraid you\'ve taken a wrong seat.', zh: '恐怕您坐错座位了。', tag: '换座-坐错' },
            { en: 'Please return to your assigned seat now. You can change seats after take-off.', zh: '请立即回到您的指定座位。起飞后您可以换座位。', tag: '换座-坐错' },

            // ===== 情境五：旅客询问航班信息 =====
            { en: 'When will we take off?', zh: '我们什么时候起飞？', tag: '航班信息' },
            { en: 'At what time will we land?', zh: '我们什么时候降落？', tag: '航班信息' },
            { en: 'We are scheduled to take off at 9 o\'clock.', zh: '我们预计9点起飞。', tag: '航班信息' },
            { en: 'The flight time today is about 2 hours.', zh: '今天的飞行时间大约是2小时。', tag: '航班信息' },
            { en: 'We will be landing around 11 o\'clock.', zh: '我们将在11点左右降落。', tag: '航班信息' },
            { en: 'We will take off at 9 am and land at 11:30 am.', zh: '我们将于上午9点起飞，上午11:30降落。', tag: '航班信息' },

            // ===== 情境六：机上升舱 =====
            { en: 'I\'d like to upgrade, please.', zh: '我想升舱。', tag: '机上升舱' },
            { en: 'If you upgrade on board, you will not get the business class meal, extra luggage allowance, or shuttle bus service.', zh: '机上升舱将无法享受公务舱餐食、额外行李额和摆渡车服务。', tag: '机上升舱' },
            { en: 'Mileage will be based on your original cabin class.', zh: '里程积分仍按原舱位标准累积。', tag: '机上升舱' },
            { en: 'The purser will be with you shortly.', zh: '乘务长马上过来为您办理。', tag: '机上升舱' },
            { en: 'Please scan this QR code. Enjoy your flight!', zh: '请扫描这里的二维码。祝您旅途愉快！', tag: '机上升舱' },
            { en: 'Sorry, Madam. There are no seats available in first class.', zh: '抱歉，女士。头等舱没有空位了。', tag: '机上升舱' },
            { en: 'You can upgrade, but there is an extra charge.', zh: '您可以升舱，但需要支付额外费用。', tag: '机上升舱' }
        ];

        // ===== 6个完整对话（已优化语法与情境适配） =====
        const DIALOGUE_DATA = [{
            id: 1,
            title: '问候与查验登机牌',
            scene: '旅客登机，乘务员问候并查验登机牌',
            lines: [
                { speaker: 'Crew', text: 'Good morning, sir. Welcome aboard!', trans: '早上好，先生。欢迎登机！' },
                { speaker: 'Passenger', text: 'Good morning. Could you help me find my seat?', trans: '早上好。您能帮我找一下座位吗？' },
                { speaker: 'Crew', text: 'May I see your boarding pass, please?', trans: '我能看一下您的登机牌吗？' },
                { speaker: 'Passenger', text: 'Here you are.', trans: '给您。' },
                { speaker: 'Crew', text: 'Thank you. Your seat is 54K, at the rear of the cabin. Please go straight and turn right.', trans: '谢谢。您的座位是54K，在后舱。请直走然后右转。' },
                { speaker: 'Passenger', text: 'Thank you. When will we take off?', trans: '谢谢。我们什么时候起飞？' },
                { speaker: 'Crew', text: 'We are scheduled to take off at 9 o\'clock. The flight time is about 2 hours, so we will land around 11.', trans: '我们预计9点起飞。飞行时间大约2小时，所以大约11点降落。' }
            ]
        }, {
            id: 2,
            title: '指引座位',
            scene: '旅客寻找座位，乘务员指引并告知座位号位置',
            lines: [
                { speaker: 'Passenger', text: 'Excuse me, I can\'t find my seat. Could you help me?', trans: '打扰一下，我找不到我的座位。能帮我一下吗？' },
                { speaker: 'Crew', text: 'Of course. May I see your boarding pass?', trans: '当然，可以看一下您的登机牌吗？' },
                { speaker: 'Passenger', text: 'Here you are.', trans: '给您。' },
                { speaker: 'Crew', text: 'Your seat is 32A, at the front of the cabin. Please go straight ahead and turn left. The seat number is on the edge of the overhead compartment.', trans: '您的座位是32A，在客舱前部。请往前走然后左转。座位号在行李架边缘。' },
                { speaker: 'Passenger', text: 'Thank you so much!', trans: '非常感谢！' },
                { speaker: 'Crew', text: 'You\'re welcome. If you need anything, just press the call button.', trans: '不客气。如果需要帮助，请按呼唤铃。' }
            ]
        }, {
            id: 3,
            title: '换座位——与家人同行',
            scene: '旅客家人座位被分散，乘务员协助询问其他旅客是否愿意换座',
            lines: [
                { speaker: 'Crew', text: 'Excuse me, sir. May I ask you something?', trans: '打扰一下，先生。能问您一件事吗？' },
                { speaker: 'Passenger', text: 'Sure. What is it?', trans: '当然，什么事？' },
                { speaker: 'Crew', text: 'Would you mind changing seats with this gentleman? He would like to sit with his family.', trans: '您介意和这位先生换一下座位吗？他想和家人坐在一起。' },
                { speaker: 'Passenger', text: 'That depends. Where is his seat?', trans: '看情况。他的座位在哪里？' },
                { speaker: 'Crew', text: 'It\'s three rows back, and it\'s also an aisle seat.', trans: '在三排之后，也是靠走道的座位。' },
                { speaker: 'Passenger', text: 'Oh, that\'s fine. I\'d like an aisle seat too.', trans: '哦，那可以。我也喜欢靠走道。' },
                { speaker: 'Crew', text: 'Great. Thank you very much.', trans: '太好了，非常感谢。' }
            ]
        }, {
            id: 4,
            title: '换座位——坐错座位',
            scene: '旅客坐错座位，乘务员解释配载平衡与安全规定，引导回原座',
            lines: [
                { speaker: 'Crew', text: 'Good afternoon, sir. May I see your boarding pass, please?', trans: '下午好，先生。能看一下您的登机牌吗？' },
                { speaker: 'Passenger', text: 'Here you are.', trans: '给您。' },
                { speaker: 'Crew', text: 'Sir, your seat is 32A, at the front of the cabin. I\'m afraid you need to return to your seat for safety reasons.', trans: '先生，您的座位是32A，在客舱前部。为了安全起见，恐怕您需要回到自己的座位。' },
                { speaker: 'Passenger', text: 'Could I sit here instead? It\'s more comfortable.', trans: '我可以坐这里吗？这里更舒服一些。' },
                { speaker: 'Crew', text: 'I\'m sorry, sir. For weight and balance, passengers cannot change seats before take-off or landing.', trans: '抱歉，先生。为了配载平衡，旅客在起飞和降落前不能换座位。' },
                { speaker: 'Passenger', text: 'I see. I\'ll go back to my seat.', trans: '好的，我回我的座位。' },
                { speaker: 'Crew', text: 'Thank you for your understanding. After we reach cruising altitude, you can change seats.', trans: '感谢您的理解。到达巡航高度后，您可以换座位。' },
                { speaker: 'Passenger', text: 'Got it. Thanks.', trans: '明白了，谢谢。' },
                { speaker: 'Crew', text: 'If there\'s anything else, please let us know.', trans: '如果还有其他需要，请告诉我们。' }
            ]
        }, {
            id: 5,
            title: '旅客询问航班信息',
            scene: '登机后，旅客询问航班起飞、降落时间及飞行时长，乘务员耐心解答',
            lines: [
                { speaker: 'Passenger', text: 'Excuse me, Miss. When will we take off?', trans: '打扰一下，乘务员。我们什么时候起飞？' },
                { speaker: 'Crew', text: 'We are scheduled to take off at 9 o\'clock, sir.', trans: '先生，我们预计9点起飞。' },
                { speaker: 'Passenger', text: 'And when will we land?', trans: '那什么时候降落呢？' },
                { speaker: 'Crew', text: 'The flight time is about 2 hours, so we will land around 11.', trans: '飞行时间大约2小时，所以我们大约11点降落。' },
                { speaker: 'Passenger', text: 'Thank you. That\'s very helpful.', trans: '谢谢，这很有帮助。' },
                { speaker: 'Crew', text: 'You\'re welcome. Enjoy your flight!', trans: '不客气。祝您旅途愉快！' }
            ]
        }, {
            id: 6,
            title: '机上升舱',
            scene: '旅客提出机上升舱需求，乘务员说明升舱限制并协助办理',
            lines: [
                { speaker: 'Passenger', text: 'Miss, I\'d like to upgrade, please.', trans: '乘务员，我想升舱。' },
                { speaker: 'Crew', text: 'Certainly, sir. Please note: upgrading on board does not include the business class meal, extra luggage allowance, or shuttle bus service. If you are a Frequent Flyer, mileage will be based on your original class. Would you still like to upgrade?', trans: '好的，先生。请注意：机上升舱不包含公务舱餐食、额外行李额和摆渡车服务。如果您是常旅客，里程积分仍按原舱位累积。您还需要升舱吗？' },
                { speaker: 'Passenger', text: 'Yes, please.', trans: '是的，需要。' },
                { speaker: 'Crew', text: 'All right, sir. Please give me a moment. The purser will be with you shortly.', trans: '好的，先生。请稍等，乘务长马上过来。' },
                { speaker: 'Purser', text: 'Good morning, sir. I\'m Purser Lucy. May I have your boarding pass, please? Nice to see you, Mr. Green. Upgrading to business class costs XX yuan. How would you like to pay? Alipay, WeChat, or cash?', trans: '先生您好，我是乘务长露西。能看一下您的登机牌吗？格林先生，升到公务舱需要XX元。您想怎么支付？支付宝、微信还是现金？' },
                { speaker: 'Passenger', text: 'Alipay, please.', trans: '支付宝。' },
                { speaker: 'Purser', text: 'Certainly. Please scan this QR code. My colleague will help you with your baggage to seat 17C. Enjoy your flight!', trans: '好的。请扫描这个二维码。我的同事会帮您把行李拿到17C座位。祝您旅途愉快！' }
            ]
        }];

        const ROLE_DATA = [
            { id: 'r1', title: '乘务员1 (CA1)', icon: 'fa-user-tie' },
            { id: 'r2', title: '乘务员2 (CA2)', icon: 'fa-user' },
            { id: 'r3', title: '乘务员3 (CA3)', icon: 'fa-user' },
            { id: 'r4', title: '乘务员4 (CA4)', icon: 'fa-user' },
            { id: 'r5', title: '乘务员5 (CA5)', icon: 'fa-user' },
            { id: 'r6', title: '乘务长 (Purser)', icon: 'fa-user-shield' }
        ];

        const TEACHER_EVAL_ITEMS = [
            { id: 't1', label: '词汇掌握度', desc: '25个核心词汇的认读与发音准确度', weight: 20 },
            { id: 't2', label: '对话理解与应答', desc: '6个对话卡片的理解与跟读熟练度', weight: 30 },
            { id: 't3', label: '模拟展演表现', desc: '角色投入度、语言流畅度、服务礼仪', weight: 50 }
        ];

        const ROLEPLAY_DIMENSIONS = [
            { id: 'rp1', label: '语言流畅度', desc: '英语表达自然、连贯，无明显卡顿' },
            { id: 'rp2', label: '角色投入度', desc: '情感投入、服务态度亲切、有职业感' },
            { id: 'rp3', label: '服务礼仪', desc: '站姿、手势、微笑、眼神交流规范' }
        ];

        function getDefaultData() {
            return {
                groupInfo: { className: '', groupName: '', groupId: '', taskName: '迎接旅客登机英语实训', teacher: '' },
                vocabScores: {},
                roles: ROLE_DATA.map(r => ({ ...r, member: '' })),
                scriptSteps: [
                    { roleId: 'r1', phraseIdx: 0, customText: '' },
                    { roleId: 'r2', phraseIdx: 5, customText: '' },
                    { roleId: 'r3', phraseIdx: 10, customText: '' },
                    { roleId: 'r4', phraseIdx: 15, customText: '' },
                    { roleId: 'r5', phraseIdx: 20, customText: '' },
                    { roleId: 'r6', phraseIdx: 25, customText: '' }
                ],
                dialogueRecordings: {},
                roleplayEval: {},
                teacherEval: {},
                teacherComment: '',
                updatedAt: ''
            };
        }

        function loadData() {
            try {
                const raw = localStorage.getItem(STORAGE_KEY);
                if (raw) {
                    const parsed = JSON.parse(raw);
                    if (!parsed.groupInfo) parsed.groupInfo = getDefaultData().groupInfo;
                    if (!parsed.vocabScores) parsed.vocabScores = {};
                    if (!parsed.roles || parsed.roles.length !== 6) {
                        parsed.roles = ROLE_DATA.map(r => ({ ...r, member: '' }));
                    } else {
                        parsed.roles = parsed.roles.map((r, idx) => ({ ...ROLE_DATA[idx], member: r.member || '' }));
                    }
                    if (!parsed.scriptSteps || !Array.isArray(parsed.scriptSteps) || parsed.scriptSteps.length === 0) {
                        parsed.scriptSteps = getDefaultData().scriptSteps;
                    }
                    if (!parsed.dialogueRecordings) parsed.dialogueRecordings = {};
                    if (!parsed.roleplayEval) parsed.roleplayEval = {};
                    if (!parsed.teacherEval) parsed.teacherEval = {};
                    if (parsed.teacherComment === undefined) parsed.teacherComment = '';
                    return parsed;
                }
            } catch (e) { console.warn('加载数据失败', e); }
            return getDefaultData();
        }

        function saveData(data) {
            data.updatedAt = new Date().toLocaleString();
            localStorage.setItem(STORAGE_KEY, JSON.stringify(data));
            return data;
        }

        let appData = loadData();

        function showToast(msg, type = 'success', duration = 2800) {
            const el = document.getElementById('toast');
            el.textContent = msg;
            el.className = 'toast ' + type + ' show';
            clearTimeout(el._timer);
            el._timer = setTimeout(() => el.classList.remove('show'), duration);
        }

        function speakText(text, lang = 'en-US', rate = 0.8, callback) {
            if (!window.speechSynthesis) { showToast('浏览器不支持语音合成', 'error'); return; }
            window.speechSynthesis.cancel();
            const utterance = new SpeechSynthesisUtterance(text);
            utterance.lang = lang;
            utterance.rate = rate;
            utterance.pitch = 1.0;
            utterance.volume = 1;
            utterance.onend = () => {
                document.querySelectorAll('.speaking, .playing').forEach(el => el.classList.remove('speaking', 'playing'));
                if (callback) callback();
            };
            utterance.onerror = () => {
                document.querySelectorAll('.speaking, .playing').forEach(el => el.classList.remove('speaking', 'playing'));
                if (callback) callback();
            };
            window.speechSynthesis.speak(utterance);
        }

        function buildClickableWords(sentence) {
            const parts = sentence.split(/(\s+)/);
            let html = '';
            parts.forEach(part => {
                if (/^\s+$/.test(part)) {
                    html += ' ';
                } else if (part.trim() === '') {
                    // skip
                } else {
                    const cleanWord = part.replace(/[.,!?;:'"]/g, '').trim();
                    if (cleanWord) {
                        html += `<span class="word-chip" data-word="${cleanWord.replace(/"/g, '&quot;').replace(/'/g, '&#39;')}">${part}</span>`;
                    } else {
                        html += `<span>${part}</span>`;
                    }
                }
            });
            return html;
        }

        function bindWordClicks(container) {
            container.querySelectorAll('.word-chip').forEach(chip => {
                chip.addEventListener('click', function(e) {
                    e.stopPropagation();
                    const word = this.dataset.word;
                    if (!word) return;
                    const lowerWord = word.toLowerCase();
                    const meaning = WORD_DICT[lowerWord] || WORD_DICT[word] || '';
                    document.querySelectorAll('.word-chip.speaking').forEach(el => el.classList.remove('speaking'));
                    this.classList.add('speaking');
                    speakText(word, 'en-US', 0.75, () => { this.classList.remove('speaking'); });
                    const displayMsg = meaning ? `🔊 ${word} — ${meaning}` : `🔊 ${word}`;
                    showToast(displayMsg, 'info', 2000);
                });
            });
        }

        document.querySelectorAll('.nav-links a').forEach(link => {
            link.addEventListener('click', function(e) {
                e.preventDefault();
                const pageId = this.dataset.page;
                document.querySelectorAll('.nav-links a').forEach(l => l.classList.remove('active'));
                this.classList.add('active');
                document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
                document.getElementById(pageId).classList.add('active');
                if (pageId === 'page-info') loadInfoToForm();
                if (pageId === 'page-vocab') renderVocab();
                if (pageId === 'page-phrases') renderPhrases();
                if (pageId === 'page-dialogue') renderDialogues();
                if (pageId === 'page-performance') { renderRoles(); renderScriptEditor(); renderRoleplayEval(); }
                if (pageId === 'page-eval') { renderTeacherEval(); renderScore(); }
            });
        });

        function loadInfoToForm() {
            const info = appData.groupInfo;
            document.getElementById('className').value = info.className || '';
            document.getElementById('groupName').value = info.groupName || '';
            document.getElementById('groupId').value = info.groupId || '';
            document.getElementById('taskName').value = info.taskName || '迎接旅客登机英语实训';
            document.getElementById('teacherName').value = info.teacher || '';
        }
        document.getElementById('saveInfoBtn').addEventListener('click', function() {
            appData.groupInfo.className = document.getElementById('className').value.trim();
            appData.groupInfo.groupName = document.getElementById('groupName').value.trim();
            appData.groupInfo.groupId = document.getElementById('groupId').value.trim();
            appData.groupInfo.taskName = document.getElementById('taskName').value.trim();
            appData.groupInfo.teacher = document.getElementById('teacherName').value.trim();
            saveData(appData);
            showToast('小组信息已保存');
        });

        let recognition = null;

        function initSpeechRecognition() {
            if (!('webkitSpeechRecognition' in window) && !('SpeechRecognition' in window)) return null;
            const SR = window.SpeechRecognition || window.webkitSpeechRecognition;
            const rec = new SR();
            rec.lang = 'en-US';
            rec.continuous = false;
            rec.interimResults = false;
            rec.maxAlternatives = 1;
            return rec;
        }

        function calculateScore(recognized, target) {
            recognized = recognized.toLowerCase().trim();
            target = target.toLowerCase().trim();
            if (!recognized || !target) return 0;
            if (recognized === target) return 100;
            if (recognized.includes(target)) return 92;
            if (target.includes(recognized)) return 88;
            const recWords = recognized.split(/\s+/);
            const tarWords = target.split(/\s+/);
            let matchCount = 0;
            tarWords.forEach(tw => { if (recWords.some(rw => rw === tw)) matchCount++; });
            if (tarWords.length > 0) {
                const ratio = matchCount / tarWords.length;
                if (ratio >= 0.8) return 85;
                if (ratio >= 0.6) return 70;
                if (ratio >= 0.4) return 55;
            }
            const dist = levenshteinDistance(recognized, target);
            const maxLen = Math.max(recognized.length, target.length);
            if (maxLen === 0) return 0;
            return Math.round((1 - dist / maxLen) * 60);
        }

        function levenshteinDistance(a, b) {
            const matrix = [];
            for (let i = 0; i <= b.length; i++) matrix[i] = [i];
            for (let j = 0; j <= a.length; j++) matrix[0][j] = j;
            for (let i = 1; i <= b.length; i++) {
                for (let j = 1; j <= a.length; j++) {
                    if (b[i - 1] === a[j - 1]) { matrix[i][j] = matrix[i - 1][j - 1]; } else {
                        matrix[i][j] = Math.min(matrix[i - 1][j - 1] + 1, matrix[i][j - 1] + 1, matrix[i - 1][j] + 1);
                    }
                }
            }
            return matrix[b.length][a.length];
        }

        function getScoreClass(score) {
            if (score >= 80) return 'score-excellent';
            if (score >= 60) return 'score-good';
            if (score >= 40) return 'score-fair';
            if (score > 0) return 'score-poor';
            return 'score-none';
        }

        function getScoreLabel(score) {
            if (score >= 80) return '🌟 优秀';
            if (score >= 60) return '👍 良好';
            if (score >= 40) return '📖 一般';
            if (score > 0) return '💪 需练习';
            return '⏳ 待跟读';
        }

        function renderVocab() {
            const grid = document.getElementById('vocabGrid');
            grid.innerHTML = '';
            VOCAB_DATA.forEach((item, idx) => {
                const scoreData = appData.vocabScores[item.word] || { score: 0, attempts: 0 };
                const div = document.createElement('div');
                div.className = 'vocab-card';
                div.innerHTML = `
                    <div><span class="word">${item.word}</span><span class="phonetic">${item.phonetic}</span></div>
                    <div class="meaning">${item.meaning}</div>
                    <div class="actions">
                        <button class="speak-btn" data-word="${item.word}"><i class="fas fa-volume-up"></i></button>
                        <button class="record-btn" data-word="${item.word}" data-idx="${idx}"><i class="fas fa-microphone"></i></button>
                        <span class="recognition-status" id="status-${idx}">点击🎤开始跟读</span>
                    </div>
                    <div class="score-display">
                        评分：<span class="score-value ${getScoreClass(scoreData.score)}" id="score-${idx}">${scoreData.score > 0 ? scoreData.score : '—'}</span>
                        <span style="font-size:0.7rem;color:#8a9eb0;">${getScoreLabel(scoreData.score)}</span>
                    </div>`;
                grid.appendChild(div);
                div.querySelector('.speak-btn').addEventListener('click', function(e) {
                    e.stopPropagation();
                    const word = this.dataset.word;
                    document.querySelectorAll('.speak-btn.speaking').forEach(b => b.classList.remove('speaking'));
                    this.classList.add('speaking');
                    speakText(word, 'en-US', 0.7, () => { this.classList.remove('speaking'); });
                });
                const recordBtn = div.querySelector('.record-btn');
                const statusEl = document.getElementById(`status-${idx}`);
                const scoreEl = document.getElementById(`score-${idx}`);
                recordBtn.addEventListener('click', function(e) {
                    e.stopPropagation();
                    const word = this.dataset.word;
                    if (this.classList.contains('recording')) {
                        if (recognition) { try { recognition.stop(); } catch (e) {} }
                        this.classList.remove('recording');
                        return;
                    }
                    if (!('webkitSpeechRecognition' in window) && !('SpeechRecognition' in window)) {
                        showToast('当前浏览器不支持语音识别', 'error'); return;
                    }
                    if (!recognition) { recognition = initSpeechRecognition(); if (!recognition) return; }
                    recognition.lang = 'en-US';
                    recognition.continuous = false;
                    recognition.interimResults = false;
                    recognition.onstart = function() {
                        recordBtn.classList.add('recording');
                        statusEl.textContent = '🎤 正在听...';
                        statusEl.className = 'recognition-status active';
                    };
                    recognition.onresult = function(event) {
                        const result = event.results[0];
                        const transcript = result[0].transcript.toLowerCase().trim();
                        const confidence = result[0].confidence || 0;
                        const score = calculateScore(transcript, word);
                        const finalScore = Math.min(100, Math.round(score * 0.85 + confidence * 15));
                        if (!appData.vocabScores[word]) appData.vocabScores[word] = { score: 0, attempts: 0 };
                        appData.vocabScores[word].score = Math.max(appData.vocabScores[word].score, finalScore);
                        appData.vocabScores[word].attempts += 1;
                        saveData(appData);
                        statusEl.textContent = `✅ ${finalScore}分`;
                        statusEl.className = 'recognition-status success';
                        scoreEl.textContent = finalScore;
                        scoreEl.className = `score-value ${getScoreClass(finalScore)}`;
                        recordBtn.classList.remove('recording');
                        updateVocabProgress();
                    };
                    recognition.onerror = function(event) {
                        recordBtn.classList.remove('recording');
                        statusEl.textContent = '❌ 错误';
                        statusEl.className = 'recognition-status error';
                    };
                    recognition.onend = function() { recordBtn.classList.remove('recording'); };
                    try { recognition.start(); } catch (e) { recordBtn.classList.remove('recording'); }
                });
            });
            updateVocabProgress();
        }

        function updateVocabProgress() {
            let learned = 0;
            VOCAB_DATA.forEach(item => {
                const data = appData.vocabScores[item.word];
                if (data && data.score > 0) learned++;
            });
            document.getElementById('vocabProgress').textContent = `已学 ${learned}/${VOCAB_DATA.length} 个词汇`;
        }

        document.getElementById('resetVocabScoresBtn').addEventListener('click', function() {
            if (!confirm('重置所有词汇评分数据？')) return;
            appData.vocabScores = {};
            saveData(appData);
            renderVocab();
            showToast('所有评分已重置');
        });

        function renderPhrases() {
            const container = document.getElementById('phraseContainer');
            container.innerHTML = '';
            const categoryMap = {
                '问候与查验': '👋 情境一：问候与查验登机牌',
                '指引座位': '🪑 情境二：指引座位',
                '换座-与家人': '👨‍👩‍👧 情境三：换座位（与家人同行）',
                '换座-坐错': '⚠️ 情境四：换座位（坐错座位）',
                '航班信息': '✈️ 情境五：旅客询问航班信息',
                '机上升舱': '💺 情境六：机上升舱'
            };
            const groups = {};
            PHRASE_DATA.forEach(p => {
                if (!groups[p.tag]) groups[p.tag] = [];
                groups[p.tag].push(p);
            });
            const order = ['问候与查验', '指引座位', '换座-与家人', '换座-坐错', '航班信息', '机上升舱'];
            order.forEach(tag => {
                if (!groups[tag]) return;
                const items = groups[tag];
                const section = document.createElement('div');
                section.className = 'phrase-section';
                let itemsHtml = '';
                items.forEach(item => {
                    itemsHtml += `
                        <div class="phrase-item">
                            <div class="en-line">${buildClickableWords(item.en)}</div>
                            <div class="zh-line">${item.zh}</div>
                            <div class="sentence-actions">
                                <button class="btn-sentence" data-sentence="${item.en.replace(/"/g, '&quot;')}"><i class="fas fa-volume-up"></i> 整句朗读</button>
                            </div>
                        </div>
                    `;
                });
                section.innerHTML = `
                    <div class="phrase-section-title">
                        <span>${categoryMap[tag] || tag}</span>
                        <span class="badge">${items.length} 句</span>
                    </div>
                    ${itemsHtml}
                `;
                container.appendChild(section);
                bindWordClicks(section);
                section.querySelectorAll('.btn-sentence').forEach(btn => {
                    btn.addEventListener('click', function(e) {
                        e.stopPropagation();
                        const sentence = this.dataset.sentence;
                        document.querySelectorAll('.btn-sentence.playing').forEach(b => b.classList.remove('playing'));
                        this.classList.add('playing');
                        speakText(sentence, 'en-US', 0.8, () => { this.classList.remove('playing'); });
                        showToast('🔊 正在朗读整句...', 'info', 2000);
                    });
                });
            });
        }

        function renderDialogues() {
            const grid = document.getElementById('dialogueGrid');
            grid.innerHTML = '';
            DIALOGUE_DATA.forEach(dial => {
                const rec = appData.dialogueRecordings[dial.id] || null;
                const card = document.createElement('div');
                card.className = 'dialogue-card';

                let linesHtml = '';
                dial.lines.forEach(line => {
                    const cls = line.speaker === 'Crew' || line.speaker === 'Purser' ? 'crew' : 'passenger';
                    const icon = line.speaker === 'Purser' ? 'user-shield' : (line.speaker === 'Crew' ? 'user-tie' : 'user');
                    const speakerLabel = line.speaker === 'Purser' ? '👨‍✈️ 乘务长' : (line.speaker === 'Crew' ? '👩‍✈️ 乘务员' : '🧑 旅客');
                    linesHtml += `
                        <div class="d-line ${cls}">
                            <div class="d-speaker"><i class="fas fa-${icon}"></i> ${speakerLabel}</div>
                            <div class="d-en-line">${buildClickableWords(line.text)}</div>
                            <div class="d-trans">${line.trans}</div>
                            <div class="d-actions">
                                <button class="btn-sentence" data-sentence="${line.text.replace(/"/g, '&quot;').replace(/'/g, '&#39;')}"><i class="fas fa-volume-up"></i> 整句朗读</button>
                            </div>
                        </div>
                    `;
                });

                const fullText = dial.lines.map(l => l.text).join(' ');

                card.innerHTML = `
                    <div class="d-header">
                        <span class="d-num">情境 ${dial.id}</span>
                        <span class="d-title">${dial.title}</span>
                        <span class="d-scene-label">${dial.scene}</span>
                    </div>
                    <div class="d-body">${linesHtml}</div>
                    <div class="d-audio-bar">
                        <button class="btn-audio-sm play-full" data-text="${fullText.replace(/"/g, '&quot;').replace(/'/g, '&#39;')}" title="播放整段对话"><i class="fas fa-play"></i> 整段播放</button>
                        <button class="btn-recording-sm start-rec" data-id="${dial.id}" title="开始录音"><i class="fas fa-circle" style="color:#c0392b;"></i> 录音</button>
                        <button class="btn-recording-sm stop-rec" data-id="${dial.id}" style="display:none;" title="停止录音"><i class="fas fa-stop"></i> 停止</button>
                        <button class="btn-recording-sm play-rec" data-id="${dial.id}" title="播放录音" ${!rec ? 'disabled' : ''}><i class="fas fa-play"></i> 播放</button>
                        <button class="btn-recording-sm delete-rec" data-id="${dial.id}" title="删除录音" ${!rec ? 'disabled' : ''}><i class="fas fa-trash-alt"></i> 删除</button>
                        <span class="d-status" id="dial-status-${dial.id}">${rec ? '✅ 已录音 ' + (rec.duration || 0) + 's' : '⏳ 未录音'}</span>
                    </div>
                `;
                grid.appendChild(card);
                bindWordClicks(card);

                card.querySelectorAll('.btn-sentence').forEach(btn => {
                    btn.addEventListener('click', function(e) {
                        e.stopPropagation();
                        const sentence = this.dataset.sentence;
                        document.querySelectorAll('.btn-sentence.playing').forEach(b => b.classList.remove('playing'));
                        this.classList.add('playing');
                        speakText(sentence, 'en-US', 0.8, () => { this.classList.remove('playing'); });
                        showToast('🔊 正在朗读整句...', 'info', 2000);
                    });
                });

                card.querySelector('.play-full').addEventListener('click', function(e) {
                    e.stopPropagation();
                    this.classList.add('playing');
                    speakText(this.dataset.text, 'en-US', 0.78, () => { this.classList.remove('playing'); });
                    showToast(`🔊 播放完整对话`, 'info', 2000);
                });

                const startBtn = card.querySelector('.start-rec');
                const stopBtn = card.querySelector('.stop-rec');
                const playBtn = card.querySelector('.play-rec');
                const deleteBtn = card.querySelector('.delete-rec');
                const statusEl = document.getElementById(`dial-status-${dial.id}`);
                let mediaRecorder = null;
                let audioChunks = [];
                let recordingStartTime = 0;

                startBtn.addEventListener('click', async function(e) {
                    e.stopPropagation();
                    if (appData.dialogueRecordings[dial.id] && appData.dialogueRecordings[dial.id].audioData) {
                        if (!confirm('已有录音，重新录音将覆盖之前的内容？')) return;
                    }
                    try {
                        const stream = await navigator.mediaDevices.getUserMedia({ audio: true });
                        mediaRecorder = new MediaRecorder(stream, { mimeType: 'audio/webm' });
                        audioChunks = [];
                        mediaRecorder.ondataavailable = (event) => { if (event.data.size > 0) audioChunks.push(event.data); };
                        mediaRecorder.onstop = () => {
                            const blob = new Blob(audioChunks, { type: 'audio/webm' });
                            const reader = new FileReader();
                            reader.onload = () => {
                                const base64 = reader.result.split(',')[1];
                                const duration = Math.round((Date.now() - recordingStartTime) / 1000);
                                appData.dialogueRecordings[dial.id] = { audioData: base64, duration, timestamp: new Date().toISOString() };
                                saveData(appData);
                                statusEl.textContent = `✅ 已录音 ${duration}s`;
                                statusEl.className = 'd-status done';
                                playBtn.disabled = false;
                                deleteBtn.disabled = false;
                                updateDialogueProgress();
                            };
                            reader.readAsDataURL(blob);
                            stream.getTracks().forEach(track => track.stop());
                            startBtn.style.display = 'inline-flex';
                            stopBtn.style.display = 'none';
                        };
                        mediaRecorder.start();
                        recordingStartTime = Date.now();
                        startBtn.style.display = 'none';
                        stopBtn.style.display = 'inline-flex';
                        showToast('🎤 录音中...', 'info', 2000);
                    } catch (err) { showToast('无法访问麦克风', 'error'); }
                });

                stopBtn.addEventListener('click', function(e) {
                    e.stopPropagation();
                    if (mediaRecorder && mediaRecorder.state === 'recording') mediaRecorder.stop();
                });

                playBtn.addEventListener('click', function(e) {
                    e.stopPropagation();
                    const data = appData.dialogueRecordings[dial.id];
                    if (!data || !data.audioData) return;
                    new Audio(`data:audio/webm;base64,${data.audioData}`).play();
                });

                deleteBtn.addEventListener('click', function(e) {
                    e.stopPropagation();
                    if (!confirm('确定删除此对话的录音吗？')) return;
                    delete appData.dialogueRecordings[dial.id];
                    saveData(appData);
                    statusEl.textContent = '⏳ 未录音';
                    statusEl.className = 'd-status';
                    playBtn.disabled = true;
                    deleteBtn.disabled = true;
                    updateDialogueProgress();
                });
            });
            updateDialogueProgress();
        }

        function updateDialogueProgress() {
            let count = 0;
            DIALOGUE_DATA.forEach(d => {
                if (appData.dialogueRecordings[d.id] && appData.dialogueRecordings[d.id].audioData) count++;
            });
            document.getElementById('dialogueProgress').textContent = `已录音 ${count}/${DIALOGUE_DATA.length} 个对话`;
        }

        document.getElementById('clearDialogueRecordingsBtn').addEventListener('click', function() {
            if (!confirm('确定清除所有对话的录音数据吗？')) return;
            appData.dialogueRecordings = {};
            saveData(appData);
            renderDialogues();
            showToast('所有录音已清除');
        });

        function renderRoles() {
            const grid = document.getElementById('roleGrid');
            grid.innerHTML = '';
            appData.roles.forEach((role, idx) => {
                const div = document.createElement('div');
                div.className = 'role-card';
                div.innerHTML = `
                    <div class="r-title"><span class="icon"><i class="fas ${role.icon}"></i></span> ${role.title}</div>
                    <div class="r-name"><input type="text" class="role-member-input" data-idx="${idx}" value="${role.member}" placeholder="姓名..." /></div>`;
                grid.appendChild(div);
                div.querySelector('.role-member-input').addEventListener('change', function() {
                    appData.roles[parseInt(this.dataset.idx)].member = this.value.trim();
                    saveData(appData);
                    renderScriptEditor();
                });
            });
        }

        document.getElementById('saveRolesBtn').addEventListener('click', function() {
            document.querySelectorAll('.role-member-input').forEach(inp => {
                appData.roles[parseInt(inp.dataset.idx)].member = inp.value.trim();
            });
            saveData(appData);
            renderScriptEditor();
            showToast('角色分配已保存');
        });

        function renderScriptEditor() {
            const container = document.getElementById('scriptStepsContainer');
            const steps = appData.scriptSteps || [];
            container.innerHTML = '';
            steps.forEach((step, idx) => {
                const div = document.createElement('div');
                div.className = 'script-step';
                const roleSelect = document.createElement('select');
                appData.roles.forEach(r => {
                    const opt = document.createElement('option');
                    opt.value = r.id;
                    opt.textContent = r.member ? `${r.title} (${r.member})` : r.title;
                    if (r.id === step.roleId) opt.selected = true;
                    roleSelect.appendChild(opt);
                });
                const phraseSelect = document.createElement('select');
                const defaultOpt = document.createElement('option');
                defaultOpt.value = '-1';
                defaultOpt.textContent = '✏️ 自定义';
                phraseSelect.appendChild(defaultOpt);
                PHRASE_DATA.forEach((p, pi) => {
                    const opt = document.createElement('option');
                    opt.value = pi;
                    opt.textContent = p.en.substring(0, 40) + '...';
                    if (pi === step.phraseIdx) opt.selected = true;
                    phraseSelect.appendChild(opt);
                });
                const customInput = document.createElement('input');
                customInput.type = 'text';
                customInput.placeholder = '自定义台词...';
                customInput.value = step.customText || '';
                const numSpan = document.createElement('span');
                numSpan.className = 'step-num';
                numSpan.textContent = `#${idx+1}`;
                const delBtn = document.createElement('button');
                delBtn.className = 'btn-remove-step';
                delBtn.innerHTML = '<i class="fas fa-trash-alt"></i>';
                delBtn.addEventListener('click', function() {
                    if (steps.length <= 1) return;
                    steps.splice(idx, 1);
                    saveData(appData);
                    renderScriptEditor();
                });
                div.appendChild(numSpan);
                div.appendChild(roleSelect);
                div.appendChild(phraseSelect);
                div.appendChild(customInput);
                div.appendChild(delBtn);
                container.appendChild(div);
                const saveStep = () => {
                    appData.scriptSteps[idx].roleId = roleSelect.value;
                    appData.scriptSteps[idx].phraseIdx = parseInt(phraseSelect.value);
                    appData.scriptSteps[idx].customText = customInput.value.trim();
                    saveData(appData);
                };
                roleSelect.addEventListener('change', saveStep);
                phraseSelect.addEventListener('change', saveStep);
                customInput.addEventListener('input', saveStep);
            });
            document.getElementById('stepCount').textContent = steps.length;
        }

        document.getElementById('addStepBtn').addEventListener('click', function() {
            appData.scriptSteps.push({ roleId: 'r1', phraseIdx: -1, customText: '' });
            saveData(appData);
            renderScriptEditor();
            showToast('已添加新步骤');
        });

        document.getElementById('resetScriptBtn').addEventListener('click', function() {
            if (!confirm('重置为默认对话流程？')) return;
            appData.scriptSteps = getDefaultData().scriptSteps;
            saveData(appData);
            renderScriptEditor();
        });

        function generatePreview() {
            const steps = appData.scriptSteps || [];
            const previewContainer = document.getElementById('scriptPreviewContainer');
            const previewText = document.getElementById('scriptPreviewText');
            if (steps.length === 0) { previewText.textContent = '暂无步骤。'; previewContainer.style.display = 'block'; return; }
            const groupInfo = appData.groupInfo;
            let lines = `迎接旅客登机英语对话脚本\n小组：${groupInfo.groupName || '未命名'} (${groupInfo.groupId || ''})\n${'='.repeat(40)}\n\n`;
            steps.forEach((step) => {
                const role = appData.roles.find(r => r.id === step.roleId);
                const roleName = role ? `${role.title} (${role.member || '未分配'})` : '未知角色';
                let phrase = '';
                if (step.phraseIdx >= 0 && step.phraseIdx < PHRASE_DATA.length) phrase = PHRASE_DATA[step.phraseIdx].en;
                else phrase = step.customText || '（未填写）';
                lines += `【${roleName}】${phrase}\n`;
            });
            previewText.textContent = lines;
            previewContainer.style.display = 'block';
            return lines;
        }

        document.getElementById('previewScriptBtn').addEventListener('click', function() {
            generatePreview();
            showToast('对话预览已更新');
        });

        document.getElementById('downloadScriptBtn').addEventListener('click', function() {
            const fullText = generatePreview();
            if (!fullText) return;
            const blob = new Blob([fullText], { type: 'text/plain;charset=utf-8' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = `迎接登机对话_${appData.groupInfo.groupId || '小组'}.txt`;
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            URL.revokeObjectURL(url);
            showToast('✅ 已下载');
        });

        function renderRoleplayEval() {
            const container = document.getElementById('roleplayEvalContainer');
            let html = '';
            ROLEPLAY_DIMENSIONS.forEach(item => {
                const score = appData.roleplayEval[item.id] || 0;
                html += `<div class="eval-item">
                    <span class="e-label">${item.label}</span>
                    <span class="e-desc">${item.desc}</span>
                    <div class="e-score-input">
                        <select class="roleplay-score" data-id="${item.id}">
                            ${[0,10,20,30,40,50,60,70,80,90,100].map(v => `<option value="${v}" ${score===v?'selected':''}>${v}</option>`).join('')}
                        </select><span>/ 100</span>
                    </div>
                </div>`;
            });
            const total = ROLEPLAY_DIMENSIONS.reduce((sum, item) => sum + (appData.roleplayEval[item.id] || 0), 0);
            const avg = Math.round(total / ROLEPLAY_DIMENSIONS.length);
            html += `<div style="margin-top:8px;padding:8px 14px;background:#f7faff;border-radius:8px;font-weight:700;color:#1a2a5e;">模拟展演平均分：<span id="roleplayAvg">${avg}</span> / 100</div>`;
            container.innerHTML = html;
            container.querySelectorAll('.roleplay-score').forEach(sel => {
                sel.addEventListener('change', function() {
                    appData.roleplayEval[this.dataset.id] = parseInt(this.value);
                    saveData(appData);
                    const newAvg = Math.round(ROLEPLAY_DIMENSIONS.reduce((s, item) => s + (appData.roleplayEval[item.id] || 0), 0) / ROLEPLAY_DIMENSIONS.length);
                    document.getElementById('roleplayAvg').textContent = newAvg;
                    renderScore();
                });
            });
        }

        document.getElementById('saveRoleplayEvalBtn').addEventListener('click', function() {
            saveData(appData);
            showToast('模拟展演评分已保存');
            renderScore();
        });

        function renderTeacherEval() {
            const container = document.getElementById('teacherEvalContainer');
            let html = '';
            TEACHER_EVAL_ITEMS.forEach(item => {
                const score = appData.teacherEval[item.id] || 0;
                html += `<div class="eval-item">
                    <span class="e-label">${item.label}</span>
                    <span class="e-desc">${item.desc}（权重 ${item.weight}%）</span>
                    <div class="e-score-input">
                        <select class="teacher-score" data-id="${item.id}">
                            ${[0,10,20,30,40,50,60,70,80,90,100].map(v => `<option value="${v}" ${score===v?'selected':''}>${v}</option>`).join('')}
                        </select><span>/ 100</span>
                    </div>
                </div>`;
            });
            const weightedTotal = TEACHER_EVAL_ITEMS.reduce((sum, item) => sum + (appData.teacherEval[item.id] || 0) * (item.weight / 100), 0);
            html += `<div style="margin-top:10px;padding:8px 14px;background:#f7faff;border-radius:8px;font-weight:700;color:#1a2a5e;">师评加权总分：<span id="teacherWeightedTotal">${Math.round(weightedTotal)}</span> / 100</div>`;
            html += `<div style="margin-top:10px;"><label style="font-weight:600;font-size:0.8rem;color:#1a2a5e;display:block;margin-bottom:3px;"><i class="fas fa-comment"></i> 教师评语</label><textarea id="teacherComment" rows="3" style="width:100%;padding:8px 12px;border-radius:8px;border:1px solid #dce4ec;font-size:0.85rem;font-family:inherit;resize:vertical;">${appData.teacherComment || ''}</textarea></div>`;
            container.innerHTML = html;
            container.querySelectorAll('.teacher-score').forEach(sel => {
                sel.addEventListener('change', function() {
                    appData.teacherEval[this.dataset.id] = parseInt(this.value);
                    saveData(appData);
                    const newWeighted = TEACHER_EVAL_ITEMS.reduce((sum, item) => sum + (appData.teacherEval[item.id] || 0) * (item.weight / 100), 0);
                    document.getElementById('teacherWeightedTotal').textContent = Math.round(newWeighted);
                    renderScore();
                });
            });
            const commentArea = document.getElementById('teacherComment');
            if (commentArea) commentArea.addEventListener('input', function() { appData.teacherComment = this.value; saveData(appData); });
        }

        document.getElementById('saveTeacherEvalBtn').addEventListener('click', function() {
            const comment = document.getElementById('teacherComment');
            if (comment) appData.teacherComment = comment.value;
            saveData(appData);
            showToast('师评已保存');
            renderScore();
        });

        function renderScore() {
            const container = document.getElementById('scoreSummary');
            const detailContainer = document.getElementById('scoreDetail');
            let vocabTotal = 0, vocabCount = 0;
            VOCAB_DATA.forEach(item => {
                const data = appData.vocabScores[item.word];
                if (data && data.score > 0) { vocabTotal += data.score; vocabCount++; }
            });
            const vocabAvg = vocabCount > 0 ? Math.round(vocabTotal / vocabCount) : 0;
            const dialogueScore = appData.teacherEval['t2'] || 0;
            const rpTotal = ROLEPLAY_DIMENSIONS.reduce((sum, item) => sum + (appData.roleplayEval[item.id] || 0), 0);
            const rpAvg = ROLEPLAY_DIMENSIONS.length > 0 ? Math.round(rpTotal / ROLEPLAY_DIMENSIONS.length) : 0;
            const teacherWeighted = TEACHER_EVAL_ITEMS.reduce((sum, item) => sum + (appData.teacherEval[item.id] || 0) * (item.weight / 100), 0);
            const finalScore = Math.round(teacherWeighted);
            let grade = '待评定', gradeColor = '#8a9eb0';
            if (finalScore >= 90) { grade = '优秀'; gradeColor = '#2d7d5a'; }
            else if (finalScore >= 80) { grade = '良好'; gradeColor = '#2d7d5a'; }
            else if (finalScore >= 70) { grade = '中等'; gradeColor = '#c99f4a'; }
            else if (finalScore >= 60) { grade = '及格'; gradeColor = '#c99f4a'; }
            else if (finalScore > 0) { grade = '待提高'; gradeColor = '#c0392b'; }

            container.innerHTML = `
                <div class="score-box"><div class="label">词汇掌握</div><div class="value">${vocabAvg}</div><div class="weight">${vocabCount}/${VOCAB_DATA.length} 个已评分</div></div>
                <div class="score-box"><div class="label">对话理解</div><div class="value gold">${dialogueScore}</div><div class="weight">权重 30%</div></div>
                <div class="score-box"><div class="label">模拟展演</div><div class="value gold">${rpAvg}</div><div class="weight">权重 50%</div></div>
                <div class="score-box" style="background:#fdf8ee;border-color:#c99f4a;"><div class="label">最终成绩</div><div class="value green" style="font-size:2rem;">${finalScore}</div><div class="weight" style="color:${gradeColor};font-weight:700;font-size:0.85rem;">${grade}</div></div>`;
            let detailHtml = `<h4 style="color:#1a2a5e;margin:10px 0 6px;">📋 评分明细</h4>
                <table><thead><tr><th>评价维度</th><th>得分</th><th>权重</th><th>加权得分</th></tr></thead><tbody>
                    <tr><td>词汇掌握度</td><td>${vocabAvg}</td><td>—</td><td>—</td></tr>
                    <tr><td>对话理解与应答</td><td>${dialogueScore}</td><td>30%</td><td>${Math.round(dialogueScore * 0.3)}</td></tr>
                    <tr><td>模拟展演表现</td><td>${rpAvg}</td><td>50%</td><td>${Math.round(rpAvg * 0.5)}</td></tr>
                    <tr style="font-weight:700;background:#f7faff;"><td><strong>师评加权总分</strong></td><td colspan="3"><strong>${Math.round(teacherWeighted)}</strong> 分（${grade}）</td></tr>
                </tbody></table>`;
            detailContainer.innerHTML = detailHtml;
        }

        function init() {
            loadInfoToForm();
            renderVocab();
            renderPhrases();
            renderDialogues();
            renderRoles();
            renderScriptEditor();
            renderRoleplayEval();
            renderTeacherEval();
            renderScore();
            showToast('✈ 迎接旅客登机英语实训系统 v3 已加载（6大情境）', 'success');
        }

        setInterval(() => { saveData(appData); }, 30000);
        window.addEventListener('beforeunload', () => { saveData(appData); });

        if (document.readyState === 'complete') init();
        else window.addEventListener('load', init);
    </script>
</body>
</html>
