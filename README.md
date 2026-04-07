<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tailere — Appartement Raspail</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;1,9..40,300&family=DM+Serif+Display:ital@0;1&display=swap" rel="stylesheet">
<style>
:root{--cream:#F7F5F0;--cream-dark:#EDE9E0;--cream-border:#D8D2C6;--green-900:#0D3D22;--green-700:#1C6B3A;--green-500:#2D8A50;--green-200:#A8D4B8;--green-50:#E8F5EE;--amber-700:#7A4A00;--amber-50:#FFF8E0;--amber-border:#E8C88A;--blue-700:#185FA5;--blue-50:#E6F1FB;--gray-800:#1A1A1A;--gray-600:#444;--gray-400:#888;--white:#fff;--red-700:#A32D2D;--red-50:#FFEAEA;--font-sans:'DM Sans',sans-serif;--font-serif:'DM Serif Display',serif;--radius-sm:6px;--radius-md:10px;--radius-lg:14px;}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0;}
body{font-family:var(--font-sans);background:var(--cream);color:var(--gray-800);font-size:14px;line-height:1.5;min-height:100vh;}
.app{display:flex;flex-direction:column;min-height:100vh;}
.topbar{background:var(--white);border-bottom:0.5px solid var(--cream-border);padding:0 24px;height:52px;display:flex;align-items:center;gap:16px;position:sticky;top:0;z-index:100;}
.topbar-logo{font-family:var(--font-serif);font-size:18px;color:var(--green-700);letter-spacing:-0.02em;}
.topbar-sep{color:var(--cream-border);font-size:18px;}
.breadcrumb{display:flex;align-items:center;gap:6px;font-size:13px;}
.breadcrumb a{color:var(--gray-400);cursor:pointer;}
.breadcrumb a:hover{color:var(--gray-600);}
.breadcrumb span{color:var(--gray-800);font-weight:500;}
.topbar-actions{margin-left:auto;display:flex;gap:8px;}
.btn-sm{font-family:var(--font-sans);font-size:12px;font-weight:500;padding:6px 14px;border-radius:var(--radius-sm);cursor:pointer;border:0.5px solid var(--cream-border);background:var(--white);color:var(--gray-600);transition:background .15s;}
.btn-sm:hover{background:var(--cream);}
.btn-sm.primary{background:var(--green-700);color:var(--white);border-color:var(--green-700);}
.btn-sm.primary:hover{background:var(--green-900);}
.project-header{background:var(--white);border-bottom:0.5px solid var(--cream-border);padding:20px 24px 0;}
.project-header-top{display:flex;align-items:flex-start;justify-content:space-between;margin-bottom:16px;}
.project-tag{font-size:11px;font-weight:500;color:var(--gray-400);text-transform:uppercase;letter-spacing:.08em;margin-bottom:4px;}
.project-name{font-family:var(--font-serif);font-size:26px;color:var(--gray-800);letter-spacing:-0.02em;line-height:1.2;}
.project-sub{font-size:13px;color:var(--gray-400);margin-top:3px;}
.phase-badge{font-size:11px;font-weight:500;padding:4px 12px;border-radius:20px;background:var(--amber-50);color:var(--amber-700);border:0.5px solid var(--amber-border);white-space:nowrap;}
.metrics-row{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;margin-bottom:20px;}
.metric{padding:10px 14px;background:var(--cream);border-radius:var(--radius-md);border:0.5px solid var(--cream-border);}
.metric-label{font-size:11px;color:var(--gray-400);margin-bottom:3px;}
.metric-value{font-size:18px;font-weight:500;color:var(--gray-800);letter-spacing:-0.02em;}
.metric-sub{font-size:11px;color:var(--green-500);margin-top:1px;}
.metric-sub.warn{color:var(--amber-700);}
.tabs{display:flex;gap:0;overflow-x:auto;}
.tab{font-size:13px;padding:10px 18px;cursor:pointer;color:var(--gray-400);border-bottom:2px solid transparent;white-space:nowrap;transition:color .15s,border-color .15s;display:flex;align-items:center;gap:6px;}
.tab:hover{color:var(--gray-600);}
.tab.active{color:var(--green-700);border-bottom-color:var(--green-700);font-weight:500;}
.tab-pill{font-size:10px;padding:1px 6px;border-radius:10px;font-weight:500;}
.tab-pill.green{background:var(--green-50);color:var(--green-700);}
.tab-pill.red{background:var(--red-50);color:var(--red-700);}
.main{padding:20px 24px;}
.tab-panel{display:none;}
.tab-panel.active{display:block;animation:fadeUp .2s ease;}
@keyframes fadeUp{from{opacity:0;transform:translateY(6px);}to{opacity:1;transform:translateY(0);}}
.section-label{font-size:11px;font-weight:500;text-transform:uppercase;letter-spacing:.07em;color:var(--gray-400);margin:20px 0 10px;}
.section-label:first-child{margin-top:0;}
.badge{font-size:10px;font-weight:500;padding:2px 8px;border-radius:10px;}
.badge-valide{background:var(--green-50);color:var(--green-700);border:0.5px solid var(--green-200);}
.badge-partage{background:var(--blue-50);color:var(--blue-700);border:0.5px solid #B5D4F4;}
.badge-prive{background:var(--cream);color:var(--gray-400);border:0.5px solid var(--cream-border);}
.badge-ia{background:var(--amber-50);color:var(--amber-700);border:0.5px solid var(--amber-border);}
/* OVERVIEW */
.phases-strip{display:flex;gap:8px;overflow-x:auto;padding-bottom:2px;margin-bottom:20px;}
.phase-card{background:var(--white);border:0.5px solid var(--cream-border);border-radius:var(--radius-md);padding:12px 16px;min-width:140px;flex-shrink:0;position:relative;overflow:hidden;}
.phase-card.active{border-color:var(--green-500);border-width:1px;}
.phase-card.active::before{content:'';position:absolute;top:0;left:0;right:0;height:3px;background:var(--green-500);}
.phase-dot{width:7px;height:7px;border-radius:50%;display:inline-block;margin-right:5px;}
.dot-done{background:var(--green-700);}
.dot-active{background:var(--green-500);}
.dot-pending{background:var(--cream-border);}
.phase-card-name{font-size:13px;font-weight:500;color:var(--gray-800);margin-bottom:3px;}
.phase-card-dates{font-size:11px;color:var(--gray-400);}
.phase-card-pct{font-size:20px;font-weight:500;margin-top:8px;}
.pct-done{color:var(--green-700);}
.pct-active{color:var(--green-500);}
.pct-pending{color:var(--cream-border);}
.progress-bar-wrap{height:3px;background:var(--cream-dark);border-radius:2px;margin-top:8px;overflow:hidden;}
.progress-bar-fill{height:100%;background:var(--green-500);border-radius:2px;}
.info-grid{display:grid;grid-template-columns:1fr 1fr;gap:8px;}
.info-row{background:var(--white);border:0.5px solid var(--cream-border);border-radius:var(--radius-md);padding:10px 14px;}
.info-key{font-size:11px;color:var(--gray-400);margin-bottom:2px;}
.info-val{font-size:13px;font-weight:500;color:var(--gray-800);}
.info-val.green{color:var(--green-700);}
/* DOCUMENTS */
.doc-section{background:var(--white);border:0.5px solid var(--cream-border);border-radius:var(--radius-md);margin-bottom:8px;overflow:hidden;}
.doc-section-hdr{padding:12px 16px;display:flex;align-items:center;gap:10px;cursor:pointer;user-select:none;transition:background .1s;}
.doc-section-hdr:hover{background:var(--cream);}
.doc-num{font-size:12px;color:var(--gray-400);min-width:22px;}
.doc-sec-name{font-size:13px;font-weight:500;color:var(--gray-800);flex:1;}
.doc-count{font-size:11px;color:var(--gray-400);}
.chevron{font-size:11px;color:var(--gray-400);transition:transform .2s;}
.chevron.open{transform:rotate(180deg);}
.doc-files{border-top:0.5px solid var(--cream-border);}
.doc-files.collapsed{display:none;}
.doc-file{padding:9px 16px 9px 28px;display:flex;align-items:center;gap:8px;border-bottom:0.5px solid #F5F0E8;cursor:pointer;transition:background .1s;}
.doc-file:last-child{border-bottom:none;}
.doc-file:hover{background:var(--cream);}
.doc-file-icon{width:14px;height:17px;background:var(--blue-50);border-radius:2px;border:0.5px solid #B5D4F4;flex-shrink:0;}
.doc-file-icon.green{background:var(--green-50);border-color:var(--green-200);}
.doc-file-name{flex:1;font-size:12px;color:var(--gray-800);}
.doc-file-date{font-size:11px;color:var(--gray-400);white-space:nowrap;}
.new-dot{width:6px;height:6px;border-radius:50%;background:var(--green-500);flex-shrink:0;}
/* CR */
.cr-generate-bar{display:flex;align-items:center;justify-content:space-between;background:var(--green-50);border:0.5px solid var(--green-200);border-radius:var(--radius-md);padding:12px 16px;cursor:pointer;transition:background .15s;}
.cr-generate-bar:hover{background:#DCF0E5;}
.cr-generate-label{font-size:13px;font-weight:500;color:var(--green-700);}
.cr-generate-sub{font-size:11px;color:var(--green-500);margin-top:1px;}
.cr-generate-btn{font-family:var(--font-sans);font-size:12px;font-weight:500;background:var(--green-700);color:var(--white);border:none;padding:7px 14px;border-radius:var(--radius-sm);cursor:pointer;}
.cr-list{display:flex;flex-direction:column;gap:10px;}
.cr-card{background:var(--white);border:0.5px solid var(--cream-border);border-radius:var(--radius-md);padding:14px 16px;cursor:pointer;transition:box-shadow .15s;}
.cr-card:hover{box-shadow:0 2px 8px rgba(0,0,0,.07);}
.cr-card.new{border-color:var(--green-200);border-width:1px;}
.cr-top{display:flex;align-items:flex-start;gap:12px;margin-bottom:8px;}
.cr-icon{width:34px;height:34px;background:var(--cream);border:0.5px solid var(--cream-border);border-radius:var(--radius-sm);display:flex;align-items:center;justify-content:center;flex-shrink:0;font-size:15px;}
.cr-title-block{flex:1;}
.cr-title{font-size:13px;font-weight:500;color:var(--gray-800);margin-bottom:2px;}
.cr-date{font-size:11px;color:var(--gray-400);}
.cr-preview{font-size:12px;color:var(--gray-400);line-height:1.5;margin-bottom:10px;padding-left:46px;}
.cr-footer{display:flex;align-items:center;gap:8px;padding-left:46px;}
.cr-read{font-size:11px;color:var(--green-500);}
.cr-gen{font-size:11px;color:var(--gray-400);}
/* GANTT */
.gantt-wrap{background:var(--white);border:0.5px solid var(--cream-border);border-radius:var(--radius-lg);overflow:hidden;}
.gantt-head{display:grid;grid-template-columns:120px 1fr;border-bottom:0.5px solid var(--cream-border);background:var(--cream);}
.gantt-head-label{padding:8px 12px;font-size:11px;color:var(--gray-400);border-right:0.5px solid var(--cream-border);}
.gantt-months{display:flex;flex:1;}
.gantt-month{flex:1;text-align:center;font-size:10px;color:var(--gray-400);padding:8px 0;border-right:0.5px solid var(--cream-border);font-weight:500;text-transform:uppercase;letter-spacing:.05em;}
.gantt-month:last-child{border-right:none;}
.gantt-month.current{color:var(--green-700);background:var(--green-50);}
.gantt-row{display:grid;grid-template-columns:120px 1fr;border-bottom:0.5px solid #F5F0E8;min-height:36px;}
.gantt-row.sub-row{background:#FDFCFA;min-height:28px;}
.gantt-row:last-child{border-bottom:none;}
.gantt-row-label{padding:0 12px;display:flex;align-items:center;gap:6px;font-size:12px;color:var(--gray-800);border-right:0.5px solid var(--cream-border);font-weight:500;}
.gantt-row-label.sub{font-size:11px;color:var(--gray-400);font-weight:400;padding-left:20px;}
.gantt-track{position:relative;display:flex;align-items:center;}
.gantt-bar{position:absolute;height:16px;border-radius:3px;display:flex;align-items:center;padding:0 7px;overflow:hidden;}
.gantt-bar.sub{height:8px;}
.bar-done{background:var(--green-700);}
.bar-active{background:var(--green-500);}
.bar-upcoming{background:var(--cream-dark);border:0.5px solid var(--cream-border);}
.bar-lot{background:var(--green-200);}
.gantt-bar-text{font-size:10px;color:var(--white);font-weight:500;white-space:nowrap;}
.bar-upcoming .gantt-bar-text{color:var(--gray-400);}
.bar-lot .gantt-bar-text{color:var(--green-700);}
.gantt-pct{font-size:10px;color:var(--white);font-weight:500;}
.today-line{position:absolute;top:0;bottom:0;width:1px;background:var(--gray-800);opacity:.2;border-right:1px dashed var(--gray-800);}
.milestone{position:absolute;width:9px;height:9px;background:var(--green-900);transform:rotate(45deg);z-index:2;}
.gantt-legend{display:flex;gap:16px;flex-wrap:wrap;margin-top:12px;}
.legend-item{display:flex;align-items:center;gap:6px;font-size:11px;color:var(--gray-400);}
.legend-dot{width:12px;height:8px;border-radius:2px;flex-shrink:0;}
/* INTERVENANTS */
.portal-info-banner{background:var(--green-50);border:0.5px solid var(--green-200);border-radius:var(--radius-md);padding:10px 14px;font-size:12px;color:var(--green-700);margin-bottom:16px;display:flex;align-items:center;gap:8px;}
.portal-dot{width:7px;height:7px;border-radius:50%;background:var(--green-500);flex-shrink:0;}
.art-card{background:var(--white);border:0.5px solid var(--cream-border);border-radius:var(--radius-lg);margin-bottom:10px;overflow:hidden;}
.art-card-top{padding:14px 16px;display:flex;align-items:center;gap:12px;}
.avatar{width:38px;height:38px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:12px;font-weight:500;flex-shrink:0;}
.av-blue{background:var(--blue-50);color:var(--blue-700);border:0.5px solid #B5D4F4;}
.av-amber{background:var(--amber-50);color:var(--amber-700);border:0.5px solid var(--amber-border);}
.av-gray{background:var(--cream);color:var(--gray-400);border:0.5px solid var(--cream-border);}
.av-green{background:var(--green-50);color:var(--green-700);border:0.5px solid var(--green-200);}
.art-info{flex:1;}
.art-name{font-size:13px;font-weight:500;color:var(--gray-800);margin-bottom:2px;}
.art-lot{font-size:11px;color:var(--gray-400);}
.status-pill{font-size:11px;font-weight:500;padding:3px 10px;border-radius:20px;}
.sp-actif{background:var(--green-50);color:var(--green-700);border:0.5px solid var(--green-200);}
.sp-attente{background:var(--amber-50);color:var(--amber-700);border:0.5px solid var(--amber-border);}
.sp-invite{background:var(--cream);color:var(--gray-400);border:0.5px solid var(--cream-border);}
.art-stats{display:grid;grid-template-columns:repeat(3,1fr);border-top:0.5px solid var(--cream-border);}
.art-stat{padding:10px 14px;border-right:0.5px solid var(--cream-border);text-align:center;}
.art-stat:last-child{border-right:none;}
.art-stat-val{font-size:16px;font-weight:500;color:var(--gray-800);letter-spacing:-0.02em;}
.art-stat-key{font-size:10px;color:var(--gray-400);margin-top:2px;}
.art-footer{padding:10px 16px;border-top:0.5px solid var(--cream-border);display:flex;align-items:center;justify-content:space-between;background:var(--cream);}
.art-link{font-size:12px;color:var(--blue-700);cursor:pointer;}
.art-link:hover{text-decoration:underline;}
.art-note{font-size:11px;color:var(--gray-400);}
.art-note.warn{color:var(--amber-700);}
.add-intervenant{display:flex;align-items:center;justify-content:center;gap:8px;border:1px dashed var(--cream-border);border-radius:var(--radius-lg);padding:14px;cursor:pointer;color:var(--gray-400);font-size:13px;transition:border-color .15s,color .15s;margin-top:4px;}
.add-intervenant:hover{border-color:var(--green-200);color:var(--green-700);}
</style>
</head>
<body>
<div class="app">
  <div class="topbar">
    <div class="topbar-logo">tailere</div>
    <div class="topbar-sep">·</div>
    <div class="breadcrumb">
      <a>Projets</a>
      <span style="color:var(--cream-border)">›</span>
      <span>Appartement Raspail</span>
    </div>
    <div class="topbar-actions">
      <button class="btn-sm">Exporter PDF</button>
      <button class="btn-sm">Inviter client</button>
      <button class="btn-sm primary">+ Nouveau document</button>
    </div>
  </div>

  <div class="project-header">
    <div class="project-header-top">
      <div>
        <div class="project-tag">Paris 14e · Résidentiel</div>
        <div class="project-name">Appartement Raspail</div>
        <div class="project-sub">87 m² · Rénovation complète · M. &amp; Mme Lefèvre · Démarré jan. 2026</div>
      </div>
      <span class="phase-badge">Phase DCE</span>
    </div>
    <div class="metrics-row">
      <div class="metric"><div class="metric-label">Budget total</div><div class="metric-value">142 000 €</div><div class="metric-sub warn">+3% vs estimatif</div></div>
      <div class="metric"><div class="metric-label">Engagé</div><div class="metric-value">61 400 €</div><div class="metric-sub">43% du budget</div></div>
      <div class="metric"><div class="metric-label">Avancement global</div><div class="metric-value">38%</div><div class="metric-sub">Phase 3 sur 5</div></div>
      <div class="metric"><div class="metric-label">Livraison estimée</div><div class="metric-value">oct. 2026</div><div class="metric-sub">Dans 27 semaines</div></div>
    </div>
    <div class="tabs">
      <div class="tab active" data-tab="overview">Vue d'ensemble</div>
      <div class="tab" data-tab="docs">Documents <span class="tab-pill green">12</span></div>
      <div class="tab" data-tab="cr">Comptes-rendus <span class="tab-pill red">1 nouveau</span></div>
      <div class="tab" data-tab="gantt">Planning</div>
      <div class="tab" data-tab="art">Intervenants <span class="tab-pill green">5</span></div>
    </div>
  </div>

  <div class="main">

    <!-- VUE D'ENSEMBLE -->
    <div class="tab-panel active" id="panel-overview">
      <div class="section-label">Phases du projet</div>
      <div class="phases-strip">
        <div class="phase-card"><div style="display:flex;align-items:center;margin-bottom:4px"><span class="phase-dot dot-done"></span><span class="phase-card-name">ESQ</span></div><div class="phase-card-dates">jan. → fév. 2026</div><div class="phase-card-pct pct-done">100%</div><div class="progress-bar-wrap"><div class="progress-bar-fill" style="width:100%;background:var(--green-700)"></div></div></div>
        <div class="phase-card"><div style="display:flex;align-items:center;margin-bottom:4px"><span class="phase-dot dot-done"></span><span class="phase-card-name">APS / APD</span></div><div class="phase-card-dates">fév. → mars 2026</div><div class="phase-card-pct pct-done">100%</div><div class="progress-bar-wrap"><div class="progress-bar-fill" style="width:100%;background:var(--green-700)"></div></div></div>
        <div class="phase-card active"><div style="display:flex;align-items:center;margin-bottom:4px"><span class="phase-dot dot-active"></span><span class="phase-card-name">DCE</span></div><div class="phase-card-dates">avr. → mai 2026</div><div class="phase-card-pct pct-active">65%</div><div class="progress-bar-wrap"><div class="progress-bar-fill" style="width:65%"></div></div></div>
        <div class="phase-card"><div style="display:flex;align-items:center;margin-bottom:4px"><span class="phase-dot dot-pending"></span><span class="phase-card-name">DET / Chantier</span></div><div class="phase-card-dates">juin → sept. 2026</div><div class="phase-card-pct pct-pending">—</div><div class="progress-bar-wrap"><div class="progress-bar-fill" style="width:0%"></div></div></div>
        <div class="phase-card"><div style="display:flex;align-items:center;margin-bottom:4px"><span class="phase-dot dot-pending"></span><span class="phase-card-name">OPR / Livraison</span></div><div class="phase-card-dates">oct. 2026</div><div class="phase-card-pct pct-pending">—</div><div class="progress-bar-wrap"><div class="progress-bar-fill" style="width:0%"></div></div></div>
      </div>
      <div class="section-label">Informations projet</div>
      <div class="info-grid">
        <div class="info-row"><div class="info-key">Client</div><div class="info-val">M. &amp; Mme Lefèvre</div></div>
        <div class="info-row"><div class="info-key">Chef de projet</div><div class="info-val">Sophie Marchand</div></div>
        <div class="info-row"><div class="info-key">Surface</div><div class="info-val">87 m²</div></div>
        <div class="info-row"><div class="info-key">Type de projet</div><div class="info-val">Rénovation complète</div></div>
        <div class="info-row"><div class="info-key">Contrat signé</div><div class="info-val green">12 jan. 2026 ✓</div></div>
        <div class="info-row"><div class="info-key">Prochaine échéance</div><div class="info-val">CCTP Plomberie — 14 avr.</div></div>
        <div class="info-row"><div class="info-key">Assurance DO</div><div class="info-val green">Ouverte ✓</div></div>
        <div class="info-row"><div class="info-key">Dossier administratif</div><div class="info-val">DP déposée — en instruction</div></div>
      </div>
    </div>

    <!-- DOCUMENTS -->
    <div class="tab-panel" id="panel-docs">
      <div class="doc-section" id="sec1">
        <div class="doc-section-hdr" onclick="toggleSection('sec1')"><span class="doc-num">01</span><span class="doc-sec-name">Contrat &amp; Honoraires</span><span class="badge badge-valide">Validé ✓</span><span class="doc-count">2 docs</span><span class="chevron open" id="chev-sec1">▾</span></div>
        <div class="doc-files" id="files-sec1">
          <div class="doc-file"><div class="doc-file-icon green"></div><span class="doc-file-name">Contrat MOE — Raspail v1.pdf</span><span class="badge badge-valide">Validé</span><span class="doc-file-date">12 jan. 2026</span></div>
          <div class="doc-file"><div class="doc-file-icon green"></div><span class="doc-file-name">Annexe honoraires.pdf</span><span class="badge badge-valide">Validé</span><span class="doc-file-date">12 jan. 2026</span></div>
        </div>
      </div>
      <div class="doc-section" id="sec2">
        <div class="doc-section-hdr" onclick="toggleSection('sec2')"><span class="doc-num">02</span><span class="doc-sec-name">APS — Avant-Projet Sommaire</span><span class="badge badge-valide">Validé ✓</span><span class="doc-count">3 docs</span><span class="chevron" id="chev-sec2">▾</span></div>
        <div class="doc-files collapsed" id="files-sec2">
          <div class="doc-file"><div class="doc-file-icon green"></div><span class="doc-file-name">Plans APS v2.pdf</span><span class="badge badge-valide">Validé</span><span class="doc-file-date">28 fév. 2026</span></div>
          <div class="doc-file"><div class="doc-file-icon"></div><span class="doc-file-name">Moodboard directions créatives.pdf</span><span class="badge badge-valide">Validé</span><span class="doc-file-date">20 fév. 2026</span></div>
          <div class="doc-file"><div class="doc-file-icon"></div><span class="doc-file-name">Estimatif APS.xlsx</span><span class="badge badge-valide">Validé</span><span class="doc-file-date">28 fév. 2026</span></div>
        </div>
      </div>
      <div class="doc-section" id="sec3">
        <div class="doc-section-hdr" onclick="toggleSection('sec3')"><span class="doc-num">03</span><span class="doc-sec-name">DCE — Dossiers de Consultation</span><span class="badge badge-partage">Partagé</span><span class="doc-count">4 docs</span><span class="chevron open" id="chev-sec3">▾</span></div>
        <div class="doc-files" id="files-sec3">
          <div class="doc-file"><div class="doc-file-icon green"></div><span class="doc-file-name">CCTP Électricité.pdf</span><span class="badge badge-ia" style="margin-right:2px">IA</span><span class="badge badge-valide">Validé</span><span class="doc-file-date">2 avr. 2026</span></div>
          <div class="doc-file"><div class="doc-file-icon"></div><span class="doc-file-name">CCTP Plomberie.pdf</span><span class="badge badge-ia" style="margin-right:2px">IA</span><span class="badge badge-prive">Privé</span><span class="new-dot" style="margin:0 4px"></span><span class="doc-file-date">6 avr. 2026</span></div>
          <div class="doc-file"><div class="doc-file-icon"></div><span class="doc-file-name">CCTP Peinture.pdf</span><span class="badge badge-ia" style="margin-right:2px">IA</span><span class="badge badge-prive">Privé</span><span class="new-dot" style="margin:0 4px"></span><span class="doc-file-date">7 avr. 2026</span></div>
          <div class="doc-file"><div class="doc-file-icon"></div><span class="doc-file-name">Plans techniques APD v3.pdf</span><span class="badge badge-partage">Partagé</span><span class="doc-file-date">15 mars 2026</span></div>
        </div>
      </div>
      <div class="doc-section" id="sec4">
        <div class="doc-section-hdr" onclick="toggleSection('sec4')"><span class="doc-num">04</span><span class="doc-sec-name">Administratif</span><span class="badge badge-prive">Privé</span><span class="doc-count">3 docs</span><span class="chevron" id="chev-sec4">▾</span></div>
        <div class="doc-files collapsed" id="files-sec4">
          <div class="doc-file"><div class="doc-file-icon"></div><span class="doc-file-name">Déclaration Préalable — dépôt mairie.pdf</span><span class="badge badge-prive">Privé</span><span class="doc-file-date">10 mars 2026</span></div>
          <div class="doc-file"><div class="doc-file-icon"></div><span class="doc-file-name">Attestation assurance DO.pdf</span><span class="badge badge-valide">Validé</span><span class="doc-file-date">8 jan. 2026</span></div>
          <div class="doc-file"><div class="doc-file-icon"></div><span class="doc-file-name">CCAP — Cahier des Clauses Admin.pdf</span><span class="badge badge-ia" style="margin-right:2px">IA</span><span class="badge badge-prive">Privé</span><span class="doc-file-date">3 avr. 2026</span></div>
        </div>
      </div>
    </div>

    <!-- COMPTES-RENDUS -->
    <div class="tab-panel" id="panel-cr">
      <div class="cr-generate-bar">
        <div><div class="cr-generate-label">Générer un compte-rendu par IA</div><div class="cr-generate-sub">Basé sur les données de la semaine · ~25 secondes</div></div>
        <button class="cr-generate-btn" onclick="alert('Génération IA en cours...')">+ Générer CR IA</button>
      </div>
      <div class="section-label" style="margin-top:16px">Historique</div>
      <div class="cr-list">
        <div class="cr-card new">
          <div class="cr-top">
            <div class="cr-icon">📋</div>
            <div class="cr-title-block"><div class="cr-title">CR n°3 — Réunion DCE — Lot Électricité</div><div class="cr-date">7 avr. 2026 · <span style="color:var(--amber-700)">Non diffusé</span></div></div>
            <span class="badge badge-ia">IA</span>
          </div>
          <div class="cr-preview">"Présence : S. Marchand (architecte), J. Durand (élec.), M. Lefèvre (client). Avancement lot électricité 70%. Réserve tableau central levée. Prochaine réunion 14 avr."</div>
          <div class="cr-footer"><span class="badge badge-ia">IA</span><span class="cr-gen">Généré en 22s</span><span style="flex:1"></span><button class="btn-sm primary" style="font-size:11px;padding:5px 10px">Diffuser</button></div>
        </div>
        <div class="cr-card">
          <div class="cr-top">
            <div class="cr-icon">📋</div>
            <div class="cr-title-block"><div class="cr-title">CR n°2 — Réunion APD — Validation plans</div><div class="cr-date">18 mars 2026</div></div>
            <span class="badge badge-ia">IA</span>
          </div>
          <div class="cr-preview">"Validation plans APD v3 par clients. Modifications cloison cuisine intégrées. Estimatif travaux confirmé à 142 000 €. Prochaine étape : lancement DCE."</div>
          <div class="cr-footer"><span class="badge badge-ia">IA</span><span class="cr-gen">Généré en 31s</span><span style="flex:1"></span><span class="cr-read">✓✓ Lu le 19 mars</span></div>
        </div>
        <div class="cr-card">
          <div class="cr-top">
            <div class="cr-icon">📋</div>
            <div class="cr-title-block"><div class="cr-title">CR n°1 — Réunion de lancement ESQ</div><div class="cr-date">15 jan. 2026</div></div>
            <span class="badge badge-ia">IA</span>
          </div>
          <div class="cr-preview">"Première réunion client. Programme validé. Surface : 87 m². Budget validé : 140–145k€. Délai livraison souhaité : oct. 2026. Prochaine réunion : présentation esquisses."</div>
          <div class="cr-footer"><span class="badge badge-ia">IA</span><span class="cr-gen">Généré en 28s</span><span style="flex:1"></span><span class="cr-read">✓✓ Lu le 16 jan.</span></div>
        </div>
      </div>
    </div>

    <!-- PLANNING -->
    <div class="tab-panel" id="panel-gantt">
      <div class="gantt-wrap">
        <div class="gantt-head">
          <div class="gantt-head-label">Phase</div>
          <div class="gantt-months">
            <div class="gantt-month">Jan</div><div class="gantt-month">Fév</div><div class="gantt-month">Mars</div><div class="gantt-month current">Avr</div><div class="gantt-month">Mai</div><div class="gantt-month">Juin</div><div class="gantt-month">Juil</div><div class="gantt-month">Août</div><div class="gantt-month">Sept</div><div class="gantt-month">Oct</div>
          </div>
        </div>
        <div class="gantt-row"><div class="gantt-row-label"><span class="phase-dot dot-done"></span>ESQ</div><div class="gantt-track"><div class="gantt-bar bar-done" style="left:0%;width:19%"><span class="gantt-pct">100%</span></div><div class="milestone" style="left:19%;top:50%;margin-top:-4px"></div></div></div>
        <div class="gantt-row"><div class="gantt-row-label"><span class="phase-dot dot-done"></span>APS / APD</div><div class="gantt-track"><div class="gantt-bar bar-done" style="left:19%;width:23%"><span class="gantt-pct">100%</span></div><div class="milestone" style="left:42%;top:50%;margin-top:-4px"></div></div></div>
        <div class="gantt-row"><div class="gantt-row-label"><span class="phase-dot dot-active"></span>DCE</div><div class="gantt-track"><div class="gantt-bar bar-active" style="left:32%;width:18%"><span class="gantt-pct">65%</span></div><div class="today-line" style="left:38%"></div></div></div>
        <div class="gantt-row"><div class="gantt-row-label"><span class="phase-dot dot-pending"></span>DET / Chantier</div><div class="gantt-track"><div class="gantt-bar bar-upcoming" style="left:50%;width:37%"><span class="gantt-bar-text">Chantier</span></div></div></div>
        <div class="gantt-row sub-row"><div class="gantt-row-label sub">↳ Élec.</div><div class="gantt-track"><div class="gantt-bar bar-lot sub" style="left:50%;width:18%"><span class="gantt-bar-text">Durand</span></div></div></div>
        <div class="gantt-row sub-row"><div class="gantt-row-label sub">↳ Plomberie</div><div class="gantt-track"><div class="gantt-bar bar-lot sub" style="left:55%;width:20%"><span class="gantt-bar-text">Martin</span></div></div></div>
        <div class="gantt-row sub-row"><div class="gantt-row-label sub">↳ Peinture</div><div class="gantt-track"><div class="gantt-bar bar-lot sub" style="left:68%;width:14%"><span class="gantt-bar-text">Azur</span></div></div></div>
        <div class="gantt-row"><div class="gantt-row-label"><span class="phase-dot dot-pending"></span>OPR / Liv.</div><div class="gantt-track"><div class="gantt-bar bar-upcoming" style="left:87%;width:12%"><span class="gantt-bar-text">OPR</span></div><div class="milestone" style="left:99%;top:50%;margin-top:-4px;background:var(--green-700)"></div></div></div>
      </div>
      <div class="gantt-legend">
        <div class="legend-item"><div class="legend-dot" style="background:var(--green-700)"></div>Phase validée</div>
        <div class="legend-item"><div class="legend-dot" style="background:var(--green-500)"></div>En cours</div>
        <div class="legend-item"><div class="legend-dot" style="background:var(--cream-dark);border:0.5px solid var(--cream-border)"></div>À venir</div>
        <div class="legend-item"><div class="legend-dot" style="background:var(--green-200)"></div>Lots artisans</div>
        <div class="legend-item"><div style="width:9px;height:9px;background:var(--green-900);transform:rotate(45deg);flex-shrink:0"></div>Jalon</div>
        <div class="legend-item"><div style="width:1px;height:12px;border-right:1px dashed var(--gray-400);opacity:.6;flex-shrink:0"></div>Aujourd'hui</div>
      </div>
    </div>

    <!-- INTERVENANTS -->
    <div class="tab-panel" id="panel-art">
      <div class="portal-info-banner"><div class="portal-dot"></div>Portail artisan cloisonné — chaque intervenant accède uniquement à son lot. Ils ne voient pas le budget global ni les autres intervenants.</div>
      <div class="section-label">Lot 01 · Électricité CFO/CFA</div>
      <div class="art-card">
        <div class="art-card-top"><div class="avatar av-blue">JD</div><div class="art-info"><div class="art-name">Jean Durand — Durand Électricité SARL</div><div class="art-lot">Lot 01 · Électricité CFO/CFA · Paris 75</div></div><span class="status-pill sp-actif">Actif</span></div>
        <div class="art-stats"><div class="art-stat"><div class="art-stat-val">38 400 €</div><div class="art-stat-key">Marché signé</div></div><div class="art-stat"><div class="art-stat-val">2 / 3</div><div class="art-stat-key">Situations</div></div><div class="art-stat"><div class="art-stat-val" style="color:var(--amber-700)">1</div><div class="art-stat-key">Réserve ouverte</div></div></div>
        <div class="art-footer"><span class="art-link">→ Ouvrir le portail artisan</span><span class="art-note warn">Situation n°3 attendue le 15 avr.</span></div>
      </div>
      <div class="section-label">Lot 02 · Plomberie &amp; Sanitaires</div>
      <div class="art-card">
        <div class="art-card-top"><div class="avatar av-amber">PM</div><div class="art-info"><div class="art-name">Pierre Martin — Martin Plomberie</div><div class="art-lot">Lot 02 · Plomberie &amp; Sanitaires · Paris 92</div></div><span class="status-pill sp-attente">OS en attente</span></div>
        <div class="art-stats"><div class="art-stat"><div class="art-stat-val">12 800 €</div><div class="art-stat-key">Devis accepté</div></div><div class="art-stat"><div class="art-stat-val">0 / 0</div><div class="art-stat-key">Situations</div></div><div class="art-stat"><div class="art-stat-val">—</div><div class="art-stat-key">Réserves</div></div></div>
        <div class="art-footer"><span class="art-link">→ Émettre l'Ordre de Service</span><span class="art-note warn">OS non encore émis — démarrage bloqué</span></div>
      </div>
      <div class="section-label">Lot 03 · Peinture &amp; Revêtements</div>
      <div class="art-card">
        <div class="art-card-top"><div class="avatar av-gray">AZ</div><div class="art-info"><div class="art-name">Azur Peinture SARL</div><div class="art-lot">Lot 03 · Peinture &amp; Revêtements · Paris 75</div></div><span class="status-pill sp-invite">Invité</span></div>
        <div class="art-stats"><div class="art-stat"><div class="art-stat-val" style="font-size:12px;color:var(--gray-400)">En attente</div><div class="art-stat-key">Devis</div></div><div class="art-stat"><div class="art-stat-val">—</div><div class="art-stat-key">Marché</div></div><div class="art-stat"><div class="art-stat-val">—</div><div class="art-stat-key">Situations</div></div></div>
        <div class="art-footer"><span class="art-link">→ Relancer l'artisan</span><span class="art-note">Devis demandé le 3 avr. 2026</span></div>
      </div>
      <div class="section-label">Client</div>
      <div class="art-card">
        <div class="art-card-top"><div class="avatar av-green">LL</div><div class="art-info"><div class="art-name">M. &amp; Mme Lefèvre</div><div class="art-lot">Portail client · Accès limité aux documents partagés</div></div><span class="status-pill sp-actif">Actif</span></div>
        <div class="art-stats"><div class="art-stat"><div class="art-stat-val" style="color:var(--green-700)">3</div><div class="art-stat-key">Docs validés</div></div><div class="art-stat"><div class="art-stat-val">2</div><div class="art-stat-key">Docs lus</div></div><div class="art-stat"><div class="art-stat-val">0</div><div class="art-stat-key">En attente</div></div></div>
        <div class="art-footer"><span class="art-link">→ Ouvrir le portail client</span><span class="art-note">Dernière connexion il y a 2 jours</span></div>
      </div>
      <div class="add-intervenant" onclick="alert('Inviter un intervenant...')"><span style="font-size:16px;color:var(--green-500)">+</span>Inviter un intervenant (artisan, BE, co-traitant)</div>
    </div>

  </div>
</div>

<script>
document.querySelectorAll('.tab').forEach(function(tab){
  tab.addEventListener('click',function(){
    var name=this.dataset.tab;
    document.querySelectorAll('.tab').forEach(function(t){t.classList.remove('active');});
    document.querySelectorAll('.tab-panel').forEach(function(p){p.classList.remove('active');p.style.display='none';});
    this.classList.add('active');
    var panel=document.getElementById('panel-'+name);
    panel.style.display='block';
    panel.classList.add('active');
  });
});
document.querySelectorAll('.tab-panel').forEach(function(p){
  if(!p.classList.contains('active')) p.style.display='none';
});
function toggleSection(id){
  var files=document.getElementById('files-'+id);
  var chev=document.getElementById('chev-'+id);
  if(files.classList.contains('collapsed')){files.classList.remove('collapsed');chev.classList.add('open');}
  else{files.classList.add('collapsed');chev.classList.remove('open');}
}
</script>
</body>
</html>
