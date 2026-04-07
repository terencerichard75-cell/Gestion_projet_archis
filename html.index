<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tailere — Gestion de projets</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;1,9..40,300&family=DM+Serif+Display:ital@0;1&display=swap" rel="stylesheet">
<style>
:root{--cream:#F7F5F0;--cream-dark:#EDE9E0;--cream-border:#D8D2C6;--green-900:#0D3D22;--green-700:#1C6B3A;--green-500:#2D8A50;--green-200:#A8D4B8;--green-50:#E8F5EE;--amber-700:#7A4A00;--amber-50:#FFF8E0;--amber-border:#E8C88A;--blue-700:#185FA5;--blue-50:#E6F1FB;--gray-800:#1A1A1A;--gray-600:#444;--gray-400:#888;--gray-200:#ccc;--white:#fff;--red-700:#A32D2D;--red-50:#FFEAEA;--font-sans:'DM Sans',sans-serif;--font-serif:'DM Serif Display',serif;--r-sm:6px;--r-md:10px;--r-lg:14px;}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0;}
body{font-family:var(--font-sans);background:var(--cream);color:var(--gray-800);font-size:14px;line-height:1.5;min-height:100vh;}

/* ── TOPBAR ── */
.topbar{background:var(--white);border-bottom:0.5px solid var(--cream-border);padding:0 24px;height:52px;display:flex;align-items:center;gap:16px;position:sticky;top:0;z-index:200;}
.topbar-logo{font-family:var(--font-serif);font-size:18px;color:var(--green-700);letter-spacing:-0.02em;cursor:pointer;}
.topbar-sep{color:var(--cream-border);font-size:18px;}
.breadcrumb{display:flex;align-items:center;gap:6px;font-size:13px;}
.breadcrumb a{color:var(--gray-400);cursor:pointer;transition:color .15s;}
.breadcrumb a:hover{color:var(--green-700);}
.breadcrumb span{color:var(--gray-800);font-weight:500;}
.topbar-actions{margin-left:auto;display:flex;gap:8px;align-items:center;}

/* ── BUTTONS ── */
.btn{font-family:var(--font-sans);font-size:12px;font-weight:500;padding:7px 14px;border-radius:var(--r-sm);cursor:pointer;border:0.5px solid var(--cream-border);background:var(--white);color:var(--gray-600);transition:background .15s,border-color .15s;position:relative;white-space:nowrap;}
.btn:hover{background:var(--cream);}
.btn.primary{background:var(--green-700);color:var(--white);border-color:var(--green-700);}
.btn.primary:hover{background:var(--green-900);}
.btn.danger{background:var(--red-50);color:var(--red-700);border-color:#F7C1C1;}
.btn.danger:hover{background:#FCEBEB;}

/* ── TOOLTIP ── */
[data-tip]{position:relative;}
[data-tip]::after{
  content:attr(data-tip);
  position:absolute;bottom:calc(100% + 8px);left:50%;transform:translateX(-50%);
  background:var(--gray-800);color:var(--white);font-size:11px;font-weight:400;
  padding:5px 10px;border-radius:var(--r-sm);white-space:nowrap;
  pointer-events:none;opacity:0;transition:opacity .15s;z-index:999;
  max-width:220px;white-space:normal;text-align:center;line-height:1.4;
}
[data-tip]::before{
  content:'';position:absolute;bottom:calc(100% + 3px);left:50%;transform:translateX(-50%);
  border:5px solid transparent;border-top-color:var(--gray-800);
  pointer-events:none;opacity:0;transition:opacity .15s;z-index:999;
}
[data-tip]:hover::after,[data-tip]:hover::before{opacity:1;}

/* ── VIEWS ── */
.view{display:none;}
.view.active{display:block;}

/* ═══════════════════════════════════
   LISTE DE PROJETS
═══════════════════════════════════ */
.projects-header{padding:28px 24px 20px;display:flex;align-items:flex-end;justify-content:space-between;}
.projects-title{font-family:var(--font-serif);font-size:28px;color:var(--gray-800);letter-spacing:-0.02em;}
.projects-sub{font-size:13px;color:var(--gray-400);margin-top:3px;}
.projects-toolbar{padding:0 24px 16px;display:flex;align-items:center;gap:10px;}
.search-input{font-family:var(--font-sans);font-size:13px;padding:7px 12px;border:0.5px solid var(--cream-border);border-radius:var(--r-md);background:var(--white);color:var(--gray-800);width:240px;outline:none;transition:border-color .15s;}
.search-input:focus{border-color:var(--green-500);}
.search-input::placeholder{color:var(--gray-400);}
.filter-btn{font-family:var(--font-sans);font-size:12px;padding:7px 12px;border:0.5px solid var(--cream-border);border-radius:var(--r-md);background:var(--white);color:var(--gray-600);cursor:pointer;transition:background .15s;}
.filter-btn:hover{background:var(--cream);}
.filter-btn.active{background:var(--green-50);color:var(--green-700);border-color:var(--green-200);}
.projects-stats{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;padding:0 24px 20px;}
.stat-card{background:var(--white);border:0.5px solid var(--cream-border);border-radius:var(--r-md);padding:12px 16px;}
.stat-card-val{font-size:22px;font-weight:500;color:var(--gray-800);letter-spacing:-0.02em;}
.stat-card-label{font-size:11px;color:var(--gray-400);margin-top:2px;}
.projects-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;padding:0 24px 32px;}
.project-card{background:var(--white);border:0.5px solid var(--cream-border);border-radius:var(--r-lg);overflow:hidden;cursor:pointer;transition:box-shadow .15s,transform .15s;}
.project-card:hover{box-shadow:0 4px 16px rgba(0,0,0,.08);transform:translateY(-1px);}
.project-card-header{padding:16px 18px 14px;border-bottom:0.5px solid var(--cream-border);}
.project-card-top{display:flex;align-items:flex-start;justify-content:space-between;margin-bottom:8px;}
.project-card-name{font-family:var(--font-serif);font-size:16px;color:var(--gray-800);letter-spacing:-0.01em;line-height:1.3;}
.project-card-meta{font-size:11px;color:var(--gray-400);margin-top:3px;}
.project-phase-pill{font-size:10px;font-weight:500;padding:3px 9px;border-radius:20px;white-space:nowrap;flex-shrink:0;margin-left:8px;}
.pill-conception{background:var(--blue-50);color:var(--blue-700);border:0.5px solid #B5D4F4;}
.pill-dce{background:var(--amber-50);color:var(--amber-700);border:0.5px solid var(--amber-border);}
.pill-chantier{background:#FEF0E0;color:#7A3800;border:0.5px solid #F5C88A;}
.pill-livre{background:var(--green-50);color:var(--green-700);border:0.5px solid var(--green-200);}
.pill-pause{background:var(--cream);color:var(--gray-400);border:0.5px solid var(--cream-border);}
.project-card-progress{height:3px;background:var(--cream-dark);border-radius:2px;overflow:hidden;margin-top:10px;}
.project-card-progress-fill{height:100%;background:var(--green-500);border-radius:2px;}
.project-card-body{padding:12px 18px;}
.project-card-stats{display:grid;grid-template-columns:1fr 1fr 1fr;gap:8px;}
.pcs{text-align:center;}
.pcs-val{font-size:14px;font-weight:500;color:var(--gray-800);}
.pcs-key{font-size:10px;color:var(--gray-400);margin-top:1px;}
.project-card-footer{padding:10px 18px;border-top:0.5px solid var(--cream-border);background:var(--cream);display:flex;align-items:center;justify-content:space-between;}
.project-card-client{font-size:11px;color:var(--gray-600);}
.project-card-date{font-size:11px;color:var(--gray-400);}
.new-project-card{background:transparent;border:1.5px dashed var(--cream-border);border-radius:var(--r-lg);display:flex;flex-direction:column;align-items:center;justify-content:center;gap:10px;padding:32px;cursor:pointer;transition:border-color .2s,background .2s;min-height:180px;}
.new-project-card:hover{border-color:var(--green-200);background:var(--green-50);}
.new-project-icon{width:40px;height:40px;border-radius:50%;background:var(--green-50);border:0.5px solid var(--green-200);display:flex;align-items:center;justify-content:center;font-size:20px;color:var(--green-500);transition:background .2s;}
.new-project-card:hover .new-project-icon{background:var(--white);}
.new-project-label{font-size:13px;font-weight:500;color:var(--gray-400);transition:color .2s;}
.new-project-card:hover .new-project-label{color:var(--green-700);}
.new-project-sub{font-size:11px;color:var(--gray-200);}
.new-project-card:hover .new-project-sub{color:var(--green-200);}

/* ═══════════════════════════════════
   MODAL CRÉATION PROJET
═══════════════════════════════════ */
.modal-overlay{position:fixed;inset:0;background:rgba(20,20,20,.45);z-index:500;display:flex;align-items:center;justify-content:center;opacity:0;pointer-events:none;transition:opacity .2s;}
.modal-overlay.open{opacity:1;pointer-events:all;}
.modal{background:var(--white);border-radius:var(--r-lg);width:580px;max-width:95vw;max-height:90vh;overflow-y:auto;box-shadow:0 20px 60px rgba(0,0,0,.15);}
.modal-header{padding:22px 24px 18px;border-bottom:0.5px solid var(--cream-border);display:flex;align-items:center;justify-content:space-between;}
.modal-title{font-family:var(--font-serif);font-size:20px;color:var(--gray-800);}
.modal-sub{font-size:12px;color:var(--gray-400);margin-top:2px;}
.modal-close{width:30px;height:30px;border-radius:50%;border:0.5px solid var(--cream-border);background:transparent;cursor:pointer;display:flex;align-items:center;justify-content:center;font-size:16px;color:var(--gray-400);transition:background .15s;}
.modal-close:hover{background:var(--cream);}
.modal-body{padding:20px 24px;}
.modal-footer{padding:16px 24px;border-top:0.5px solid var(--cream-border);display:flex;justify-content:flex-end;gap:8px;}
.form-row{margin-bottom:16px;}
.form-row-2{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:16px;}
label{display:block;font-size:11px;font-weight:500;color:var(--gray-600);text-transform:uppercase;letter-spacing:.06em;margin-bottom:6px;}
input[type=text],input[type=email],input[type=number],select,textarea{font-family:var(--font-sans);font-size:13px;width:100%;padding:8px 12px;border:0.5px solid var(--cream-border);border-radius:var(--r-sm);background:var(--white);color:var(--gray-800);outline:none;transition:border-color .15s;}
input:focus,select:focus,textarea:focus{border-color:var(--green-500);}
input::placeholder,textarea::placeholder{color:var(--gray-400);}
textarea{resize:vertical;min-height:80px;}
select{appearance:none;background-image:url("data:image/svg+xml,%3Csvg width='10' height='6' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M0 0l5 6 5-6z' fill='%23888'/%3E%3C/svg%3E");background-repeat:no-repeat;background-position:right 10px center;padding-right:28px;}
.form-section-title{font-size:12px;font-weight:500;color:var(--green-700);text-transform:uppercase;letter-spacing:.07em;margin:20px 0 12px;padding-bottom:8px;border-bottom:0.5px solid var(--green-50);}
.form-section-title:first-child{margin-top:0;}
.gabarit-grid{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-top:6px;}
.gabarit-card{border:0.5px solid var(--cream-border);border-radius:var(--r-md);padding:12px 14px;cursor:pointer;transition:border-color .15s,background .15s;position:relative;}
.gabarit-card:hover{border-color:var(--green-200);background:var(--green-50);}
.gabarit-card.selected{border-color:var(--green-500);border-width:1.5px;background:var(--green-50);}
.gabarit-card input[type=radio]{position:absolute;opacity:0;}
.gabarit-name{font-size:13px;font-weight:500;color:var(--gray-800);margin-bottom:2px;}
.gabarit-desc{font-size:11px;color:var(--gray-400);line-height:1.4;}
.gabarit-phases{font-size:10px;color:var(--green-700);margin-top:6px;font-weight:500;}
.field-hint{font-size:11px;color:var(--gray-400);margin-top:4px;}

/* ═══════════════════════════════════
   FICHE PROJET (5 onglets)
═══════════════════════════════════ */
.project-header{background:var(--white);border-bottom:0.5px solid var(--cream-border);padding:20px 24px 0;}
.project-header-top{display:flex;align-items:flex-start;justify-content:space-between;margin-bottom:16px;gap:16px;}
.project-tag{font-size:11px;font-weight:500;color:var(--gray-400);text-transform:uppercase;letter-spacing:.08em;margin-bottom:4px;}
.project-name{font-family:var(--font-serif);font-size:26px;color:var(--gray-800);letter-spacing:-0.02em;line-height:1.2;}
.project-sub{font-size:13px;color:var(--gray-400);margin-top:3px;}
.phase-badge{font-size:11px;font-weight:500;padding:4px 12px;border-radius:20px;background:var(--amber-50);color:var(--amber-700);border:0.5px solid var(--amber-border);white-space:nowrap;flex-shrink:0;}
.metrics-row{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;margin-bottom:20px;}
.metric{padding:10px 14px;background:var(--cream);border-radius:var(--r-md);border:0.5px solid var(--cream-border);}
.metric-label{font-size:11px;color:var(--gray-400);margin-bottom:3px;}
.metric-value{font-size:18px;font-weight:500;color:var(--gray-800);letter-spacing:-0.02em;}
.metric-sub{font-size:11px;color:var(--green-500);margin-top:1px;}
.metric-sub.warn{color:var(--amber-700);}
.tabs{display:flex;overflow-x:auto;}
.tab{font-size:13px;padding:10px 18px;cursor:pointer;color:var(--gray-400);border-bottom:2px solid transparent;white-space:nowrap;transition:color .15s,border-color .15s;display:flex;align-items:center;gap:6px;}
.tab:hover{color:var(--gray-600);}
.tab.active{color:var(--green-700);border-bottom-color:var(--green-700);font-weight:500;}
.tab-pill{font-size:10px;padding:1px 6px;border-radius:10px;font-weight:500;}
.tp-green{background:var(--green-50);color:var(--green-700);}
.tp-red{background:var(--red-50);color:var(--red-700);}
.main{padding:20px 24px;}
.tab-panel{display:none;}
.tab-panel.active{display:block;animation:fadeUp .2s ease;}
@keyframes fadeUp{from{opacity:0;transform:translateY(5px);}to{opacity:1;transform:translateY(0);}}
.section-label{font-size:11px;font-weight:500;text-transform:uppercase;letter-spacing:.07em;color:var(--gray-400);margin:20px 0 10px;}
.section-label:first-child{margin-top:0;}
.badge{font-size:10px;font-weight:500;padding:2px 8px;border-radius:10px;}
.badge-valide{background:var(--green-50);color:var(--green-700);border:0.5px solid var(--green-200);}
.badge-partage{background:var(--blue-50);color:var(--blue-700);border:0.5px solid #B5D4F4;}
.badge-prive{background:var(--cream);color:var(--gray-400);border:0.5px solid var(--cream-border);}
.badge-ia{background:var(--amber-50);color:var(--amber-700);border:0.5px solid var(--amber-border);}
/* OVERVIEW */
.phases-strip{display:flex;gap:8px;overflow-x:auto;padding-bottom:2px;margin-bottom:20px;}
.phase-card{background:var(--white);border:0.5px solid var(--cream-border);border-radius:var(--r-md);padding:12px 16px;min-width:140px;flex-shrink:0;position:relative;overflow:hidden;}
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
.info-row{background:var(--white);border:0.5px solid var(--cream-border);border-radius:var(--r-md);padding:10px 14px;}
.info-key{font-size:11px;color:var(--gray-400);margin-bottom:2px;}
.info-val{font-size:13px;font-weight:500;color:var(--gray-800);}
.info-val.green{color:var(--green-700);}
/* DOCUMENTS */
.doc-section{background:var(--white);border:0.5px solid var(--cream-border);border-radius:var(--r-md);margin-bottom:8px;overflow:hidden;}
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
.cr-generate-bar{display:flex;align-items:center;justify-content:space-between;background:var(--green-50);border:0.5px solid var(--green-200);border-radius:var(--r-md);padding:12px 16px;margin-bottom:4px;}
.cr-generate-label{font-size:13px;font-weight:500;color:var(--green-700);}
.cr-generate-sub{font-size:11px;color:var(--green-500);margin-top:1px;}
.cr-list{display:flex;flex-direction:column;gap:10px;margin-top:16px;}
.cr-card{background:var(--white);border:0.5px solid var(--cream-border);border-radius:var(--r-md);padding:14px 16px;}
.cr-card.new{border-color:var(--green-200);border-width:1px;}
.cr-top{display:flex;align-items:flex-start;gap:12px;margin-bottom:8px;}
.cr-icon{width:34px;height:34px;background:var(--cream);border:0.5px solid var(--cream-border);border-radius:var(--r-sm);display:flex;align-items:center;justify-content:center;flex-shrink:0;font-size:15px;}
.cr-title-block{flex:1;}
.cr-title{font-size:13px;font-weight:500;color:var(--gray-800);margin-bottom:2px;}
.cr-date{font-size:11px;color:var(--gray-400);}
.cr-preview{font-size:12px;color:var(--gray-400);line-height:1.5;margin-bottom:10px;padding-left:46px;}
.cr-footer{display:flex;align-items:center;gap:8px;padding-left:46px;}
.cr-read{font-size:11px;color:var(--green-500);}
.cr-gen{font-size:11px;color:var(--gray-400);}
/* GANTT */
.gantt-wrap{background:var(--white);border:0.5px solid var(--cream-border);border-radius:var(--r-lg);overflow:hidden;}
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
.portal-info-banner{background:var(--green-50);border:0.5px solid var(--green-200);border-radius:var(--r-md);padding:10px 14px;font-size:12px;color:var(--green-700);margin-bottom:16px;display:flex;align-items:center;gap:8px;}
.portal-dot{width:7px;height:7px;border-radius:50%;background:var(--green-500);flex-shrink:0;}
.art-card{background:var(--white);border:0.5px solid var(--cream-border);border-radius:var(--r-lg);margin-bottom:10px;overflow:hidden;}
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
.add-intervenant{display:flex;align-items:center;justify-content:center;gap:8px;border:1px dashed var(--cream-border);border-radius:var(--r-lg);padding:14px;cursor:pointer;color:var(--gray-400);font-size:13px;transition:border-color .15s,color .15s;margin-top:4px;}
.add-intervenant:hover{border-color:var(--green-200);color:var(--green-700);}
/* TOAST */
.toast{position:fixed;bottom:24px;right:24px;background:var(--gray-800);color:var(--white);font-size:13px;padding:10px 18px;border-radius:var(--r-md);z-index:1000;opacity:0;transform:translateY(8px);transition:opacity .25s,transform .25s;pointer-events:none;}
.toast.show{opacity:1;transform:translateY(0);}
/* ── NAV TABS (topbar) ── */
.topbar-nav{display:flex;gap:2px;margin-left:8px;}
.topbar-tab{font-size:13px;padding:6px 14px;border-radius:var(--r-sm);cursor:pointer;color:var(--gray-400);transition:background .15s,color .15s;border:none;background:transparent;font-family:var(--font-sans);}
.topbar-tab:hover{background:var(--cream);color:var(--gray-800);}
.topbar-tab.active{background:var(--green-50);color:var(--green-700);font-weight:500;}
/* ── VUE FINANCIÈRE GLOBALE ── */
.fin-section{padding:0 24px 32px;}
.fin-header{padding:28px 24px 20px;display:flex;align-items:flex-end;justify-content:space-between;}
.fin-kpis{display:grid;grid-template-columns:repeat(5,1fr);gap:12px;margin-bottom:24px;}
.fin-kpi{background:var(--white);border:0.5px solid var(--cream-border);border-radius:var(--r-md);padding:14px 16px;}
.fin-kpi-label{font-size:11px;color:var(--gray-400);margin-bottom:4px;}
.fin-kpi-val{font-size:22px;font-weight:500;letter-spacing:-0.03em;color:var(--gray-800);}
.fin-kpi-sub{font-size:11px;margin-top:3px;}
.fin-kpi-bar{height:4px;background:var(--cream-dark);border-radius:2px;margin-top:8px;overflow:hidden;}
.fin-kpi-bar-fill{height:100%;border-radius:2px;}
.fin-table-wrap{background:var(--white);border:0.5px solid var(--cream-border);border-radius:var(--r-lg);overflow:hidden;margin-bottom:20px;}
.fin-table-head{display:grid;grid-template-columns:1.8fr 1fr 1fr 1fr 1fr 1.2fr;padding:10px 18px;background:var(--cream);border-bottom:0.5px solid var(--cream-border);gap:8px;}
.fin-th{font-size:11px;font-weight:500;color:var(--gray-400);text-transform:uppercase;letter-spacing:.06em;}
.fin-row{display:grid;grid-template-columns:1.8fr 1fr 1fr 1fr 1fr 1.2fr;padding:13px 18px;border-bottom:0.5px solid #F5F0E8;align-items:center;gap:8px;cursor:pointer;transition:background .1s;}
.fin-row:last-child{border-bottom:none;}
.fin-row:hover{background:var(--cream);}
.fin-row.total-row{background:var(--cream);border-top:1px solid var(--cream-border);cursor:default;}
.fin-row.total-row:hover{background:var(--cream);}
.fin-proj-name{font-size:13px;font-weight:500;color:var(--gray-800);}
.fin-proj-client{font-size:11px;color:var(--gray-400);margin-top:1px;}
.fin-cell{font-size:13px;color:var(--gray-800);}
.fin-cell.green{color:var(--green-700);font-weight:500;}
.fin-cell.warn{color:var(--amber-700);font-weight:500;}
.fin-cell.muted{color:var(--gray-400);}
.fin-cell.bold{font-weight:500;}
.fin-mini-bar{height:4px;background:var(--cream-dark);border-radius:2px;margin-top:5px;overflow:hidden;width:80px;}
.fin-mini-bar-fill{height:100%;background:var(--green-500);border-radius:2px;}
.fin-alerts{display:flex;flex-direction:column;gap:8px;margin-bottom:20px;}
.fin-alert-row{background:var(--white);border:0.5px solid var(--cream-border);border-radius:var(--r-md);padding:12px 16px;display:flex;align-items:center;gap:12px;}
.fin-alert-row.urgent{border-color:var(--amber-border);background:var(--amber-50);}
.fin-alert-dot{width:8px;height:8px;border-radius:50%;flex-shrink:0;}
.fin-alert-dot.green{background:var(--green-500);}
.fin-alert-dot.amber{background:var(--amber-700);}
.fin-alert-dot.gray{background:var(--cream-border);}
.fin-alert-text{flex:1;font-size:12px;color:var(--gray-800);line-height:1.4;}
.fin-alert-amount{font-size:14px;font-weight:500;min-width:80px;text-align:right;}
.fin-alert-action{font-family:var(--font-sans);font-size:11px;font-weight:500;padding:5px 10px;border-radius:var(--r-sm);cursor:pointer;border:0.5px solid var(--cream-border);background:var(--white);color:var(--gray-600);white-space:nowrap;}
.fin-alert-action:hover{background:var(--cream);}
.fin-chart-wrap{background:var(--white);border:0.5px solid var(--cream-border);border-radius:var(--r-lg);padding:18px 20px;margin-bottom:20px;}
.fin-chart-title{font-size:12px;font-weight:500;color:var(--gray-400);text-transform:uppercase;letter-spacing:.06em;margin-bottom:16px;}
.fin-bar-chart{display:flex;align-items:flex-end;gap:10px;height:120px;border-bottom:0.5px solid var(--cream-border);padding-bottom:0;}
.fin-bar-group{display:flex;flex-direction:column;align-items:center;gap:4px;flex:1;}
.fin-bars{display:flex;gap:3px;align-items:flex-end;height:100px;}
.fin-bar{border-radius:3px 3px 0 0;min-width:18px;transition:opacity .15s;}
.fin-bar:hover{opacity:.8;}
.fin-bar-label{font-size:10px;color:var(--gray-400);margin-top:6px;white-space:nowrap;}
.fin-chart-legend{display:flex;gap:16px;margin-top:12px;}
.fin-legend-item{display:flex;align-items:center;gap:6px;font-size:11px;color:var(--gray-400);}
.fin-legend-dot{width:10px;height:10px;border-radius:2px;flex-shrink:0;}
/* ── HONORAIRES ── */
.hon-summary{display:grid;grid-template-columns:repeat(4,1fr);gap:12px;margin-bottom:20px;}
.hon-kpi{background:var(--white);border:0.5px solid var(--cream-border);border-radius:var(--r-md);padding:12px 16px;}
.hon-kpi-label{font-size:11px;color:var(--gray-400);margin-bottom:4px;}
.hon-kpi-val{font-size:20px;font-weight:500;letter-spacing:-0.02em;color:var(--gray-800);}
.hon-kpi-sub{font-size:11px;margin-top:2px;}
.hon-progress-wrap{height:6px;background:var(--cream-dark);border-radius:3px;margin-top:8px;overflow:hidden;}
.hon-progress-fill{height:100%;border-radius:3px;transition:width .4s;}
.hon-table-wrap{background:var(--white);border:0.5px solid var(--cream-border);border-radius:var(--r-lg);overflow:hidden;margin-bottom:16px;}
.hon-table-header{display:grid;grid-template-columns:2fr 1fr 1fr 1fr 1fr 1fr;padding:10px 16px;background:var(--cream);border-bottom:0.5px solid var(--cream-border);gap:8px;}
.hon-th{font-size:11px;font-weight:500;color:var(--gray-400);text-transform:uppercase;letter-spacing:.06em;}
.hon-row{display:grid;grid-template-columns:2fr 1fr 1fr 1fr 1fr 1fr;padding:12px 16px;border-bottom:0.5px solid #F5F0E8;align-items:center;gap:8px;transition:background .1s;}
.hon-row:last-child{border-bottom:none;}
.hon-row:hover{background:var(--cream);}
.hon-phase-name{font-size:13px;font-weight:500;color:var(--gray-800);}
.hon-phase-sub{font-size:11px;color:var(--gray-400);margin-top:1px;}
.hon-cell{font-size:13px;color:var(--gray-800);}
.hon-cell.muted{color:var(--gray-400);}
.hon-cell.green{color:var(--green-700);font-weight:500;}
.hon-cell.warn{color:var(--amber-700);font-weight:500;}
.hon-status-pill{font-size:10px;font-weight:500;padding:3px 9px;border-radius:20px;display:inline-block;}
.hsp-paye{background:var(--green-50);color:var(--green-700);border:0.5px solid var(--green-200);}
.hsp-envoye{background:var(--blue-50);color:var(--blue-700);border:0.5px solid #B5D4F4;}
.hsp-attente{background:var(--amber-50);color:var(--amber-700);border:0.5px solid var(--amber-border);}
.hsp-afacturer{background:var(--cream);color:var(--gray-400);border:0.5px solid var(--cream-border);}
.hon-action-btn{font-family:var(--font-sans);font-size:11px;font-weight:500;padding:4px 10px;border-radius:var(--r-sm);cursor:pointer;border:0.5px solid var(--cream-border);background:var(--white);color:var(--gray-600);transition:background .15s;}
.hon-action-btn:hover{background:var(--cream);}
.hon-action-btn.primary{background:var(--green-700);color:var(--white);border-color:var(--green-700);}
.hon-action-btn.primary:hover{background:var(--green-900);}
.hon-timeline{background:var(--white);border:0.5px solid var(--cream-border);border-radius:var(--r-lg);padding:16px 20px;margin-bottom:16px;}
.hon-timeline-title{font-size:12px;font-weight:500;color:var(--gray-400);text-transform:uppercase;letter-spacing:.06em;margin-bottom:14px;}
.hon-tl-row{display:flex;align-items:center;gap:12px;margin-bottom:10px;position:relative;}
.hon-tl-row:last-child{margin-bottom:0;}
.hon-tl-dot{width:10px;height:10px;border-radius:50%;flex-shrink:0;border:2px solid transparent;}
.hon-tl-dot.paid{background:var(--green-700);border-color:var(--green-700);}
.hon-tl-dot.sent{background:var(--blue-700);border-color:var(--blue-700);}
.hon-tl-dot.pending{background:var(--white);border-color:var(--cream-border);}
.hon-tl-line{position:absolute;left:4px;top:14px;width:2px;height:calc(100% + 6px);background:var(--cream-border);}
.hon-tl-row:last-child .hon-tl-line{display:none;}
.hon-tl-label{flex:1;font-size:13px;color:var(--gray-800);}
.hon-tl-date{font-size:11px;color:var(--gray-400);}
.hon-tl-amount{font-size:13px;font-weight:500;color:var(--gray-800);}
.hon-tl-status{font-size:10px;padding:2px 8px;border-radius:10px;}
.hon-alert-banner{background:var(--amber-50);border:0.5px solid var(--amber-border);border-radius:var(--r-md);padding:12px 16px;display:flex;align-items:center;gap:12px;margin-bottom:16px;}
.hon-alert-icon{font-size:16px;flex-shrink:0;}
.hon-alert-text{font-size:12px;color:var(--amber-700);flex:1;line-height:1.5;}
.hon-alert-action{font-family:var(--font-sans);font-size:12px;font-weight:500;padding:6px 12px;border-radius:var(--r-sm);cursor:pointer;background:var(--amber-700);color:var(--white);border:none;white-space:nowrap;}
</style>
</head>
<body>

<!-- ═══════════ TOPBAR ═══════════ -->
<div class="topbar" id="topbar">
  <div class="topbar-logo" onclick="goToList()">tailere</div>
  <div class="topbar-sep">·</div>
  <div class="breadcrumb" id="breadcrumb">
    <span>Projets</span>
  </div>
  <div class="topbar-nav">
    <button class="topbar-tab active" id="nav-projets" onclick="goToList()" data-tip="Liste de tous vos projets">Projets</button>
    <button class="topbar-tab" id="nav-finances" onclick="goToFinances()" data-tip="Vue globale des encaissements et honoraires sur tous les projets">Finances</button>
  </div>
  <div class="topbar-actions" id="topbar-actions">
    <button class="btn" data-tip="Rechercher parmi vos projets, clients, documents" onclick="document.querySelector('.search-input').focus()">Rechercher</button>
    <button class="btn primary" data-tip="Créer un nouveau projet depuis un gabarit (résidentiel, tertiaire, commercial…)" onclick="openModal()">+ Nouveau projet</button>
  </div>
</div>

<!-- ═══════════ VUE : LISTE PROJETS ═══════════ -->
<div class="view active" id="view-list">
  <div class="projects-header">
    <div>
      <div class="projects-title">Mes projets</div>
      <div class="projects-sub">6 projets actifs · mis à jour il y a 2 minutes</div>
    </div>
  </div>

  <div class="projects-toolbar">
    <input class="search-input" type="text" placeholder="Rechercher un projet, un client…" oninput="filterProjects(this.value)">
    <button class="filter-btn active" data-tip="Afficher tous les projets" onclick="setFilter('all',this)">Tous</button>
    <button class="filter-btn" data-tip="Projets en phase de conception (ESQ, APS, APD)" onclick="setFilter('conception',this)">Conception</button>
    <button class="filter-btn" data-tip="Projets en phase DCE — consultation des entreprises" onclick="setFilter('dce',this)">DCE</button>
    <button class="filter-btn" data-tip="Projets dont le chantier est en cours" onclick="setFilter('chantier',this)">Chantier</button>
    <button class="filter-btn" data-tip="Projets livrés et archivés" onclick="setFilter('livre',this)">Livrés</button>
  </div>

  <div class="projects-stats">
    <div class="stat-card"><div class="stat-card-val">6</div><div class="stat-card-label">Projets actifs</div></div>
    <div class="stat-card"><div class="stat-card-val">3</div><div class="stat-card-label">Chantiers en cours</div></div>
    <div class="stat-card"><div class="stat-card-val" style="color:var(--amber-700)">2</div><div class="stat-card-label">Actions requises</div></div>
    <div class="stat-card"><div class="stat-card-val">842k€</div><div class="stat-card-label">Budget total géré</div></div>
  </div>

  <div class="projects-grid" id="projects-grid">

    <!-- CARD 1 — Appartement Raspail -->
    <div class="project-card" data-phase="dce" onclick="goToProject()">
      <div class="project-card-header">
        <div class="project-card-top">
          <div>
            <div class="project-card-name">Appartement Raspail</div>
            <div class="project-card-meta">Paris 14e · 87 m² · Rénovation complète</div>
          </div>
          <span class="project-phase-pill pill-dce">DCE</span>
        </div>
        <div class="project-card-progress"><div class="project-card-progress-fill" style="width:38%"></div></div>
      </div>
      <div class="project-card-body">
        <div class="project-card-stats">
          <div class="pcs"><div class="pcs-val">142k€</div><div class="pcs-key">Budget</div></div>
          <div class="pcs"><div class="pcs-val">38%</div><div class="pcs-key">Avancement</div></div>
          <div class="pcs"><div class="pcs-val" style="color:var(--amber-700)">1</div><div class="pcs-key">Action requise</div></div>
        </div>
      </div>
      <div class="project-card-footer">
        <span class="project-card-client">M. &amp; Mme Lefèvre</span>
        <span class="project-card-date">Livraison oct. 2026</span>
      </div>
    </div>

    <!-- CARD 2 — Villa Saint-Cloud -->
    <div class="project-card" data-phase="chantier" onclick="goToProject()">
      <div class="project-card-header">
        <div class="project-card-top">
          <div>
            <div class="project-card-name">Villa Saint-Cloud</div>
            <div class="project-card-meta">Saint-Cloud · 210 m² · Réhabilitation</div>
          </div>
          <span class="project-phase-pill pill-chantier">Chantier</span>
        </div>
        <div class="project-card-progress"><div class="project-card-progress-fill" style="width:62%"></div></div>
      </div>
      <div class="project-card-body">
        <div class="project-card-stats">
          <div class="pcs"><div class="pcs-val">320k€</div><div class="pcs-key">Budget</div></div>
          <div class="pcs"><div class="pcs-val">62%</div><div class="pcs-key">Avancement</div></div>
          <div class="pcs"><div class="pcs-val" style="color:var(--red-700)">3</div><div class="pcs-key">Réserves ouv.</div></div>
        </div>
      </div>
      <div class="project-card-footer">
        <span class="project-card-client">Famille Dumont</span>
        <span class="project-card-date">Livraison juil. 2026</span>
      </div>
    </div>

    <!-- CARD 3 — Boutique Marais -->
    <div class="project-card" data-phase="conception" onclick="goToProject()">
      <div class="project-card-header">
        <div class="project-card-top">
          <div>
            <div class="project-card-name">Boutique Le Marais</div>
            <div class="project-card-meta">Paris 3e · 65 m² · Aménagement commercial</div>
          </div>
          <span class="project-phase-pill pill-conception">APS</span>
        </div>
        <div class="project-card-progress"><div class="project-card-progress-fill" style="width:20%"></div></div>
      </div>
      <div class="project-card-body">
        <div class="project-card-stats">
          <div class="pcs"><div class="pcs-val">85k€</div><div class="pcs-key">Budget</div></div>
          <div class="pcs"><div class="pcs-val">20%</div><div class="pcs-key">Avancement</div></div>
          <div class="pcs"><div class="pcs-val">0</div><div class="pcs-key">Actions</div></div>
        </div>
      </div>
      <div class="project-card-footer">
        <span class="project-card-client">Mme Fontaine</span>
        <span class="project-card-date">Livraison nov. 2026</span>
      </div>
    </div>

    <!-- CARD 4 — Penthouse Opéra -->
    <div class="project-card" data-phase="chantier" onclick="goToProject()">
      <div class="project-card-header">
        <div class="project-card-top">
          <div>
            <div class="project-card-name">Penthouse Opéra</div>
            <div class="project-card-meta">Paris 9e · 145 m² · Rénovation prestige</div>
          </div>
          <span class="project-phase-pill pill-chantier">Chantier</span>
        </div>
        <div class="project-card-progress"><div class="project-card-progress-fill" style="width:80%"></div></div>
      </div>
      <div class="project-card-body">
        <div class="project-card-stats">
          <div class="pcs"><div class="pcs-val">195k€</div><div class="pcs-key">Budget</div></div>
          <div class="pcs"><div class="pcs-val">80%</div><div class="pcs-key">Avancement</div></div>
          <div class="pcs"><div class="pcs-val">1</div><div class="pcs-key">Action requise</div></div>
        </div>
      </div>
      <div class="project-card-footer">
        <span class="project-card-client">M. Bertrand</span>
        <span class="project-card-date">Livraison mai 2026</span>
      </div>
    </div>

    <!-- CARD 5 — Maison Bordeaux (livré) -->
    <div class="project-card" data-phase="livre" onclick="goToProject()">
      <div class="project-card-header">
        <div class="project-card-top">
          <div>
            <div class="project-card-name">Maison Bordeaux</div>
            <div class="project-card-meta">Bordeaux · 180 m² · Rénovation complète</div>
          </div>
          <span class="project-phase-pill pill-livre">Livré</span>
        </div>
        <div class="project-card-progress"><div class="project-card-progress-fill" style="width:100%;background:var(--green-700)"></div></div>
      </div>
      <div class="project-card-body">
        <div class="project-card-stats">
          <div class="pcs"><div class="pcs-val">100k€</div><div class="pcs-key">Budget</div></div>
          <div class="pcs"><div class="pcs-val" style="color:var(--green-700)">100%</div><div class="pcs-key">Livré</div></div>
          <div class="pcs"><div class="pcs-val">0</div><div class="pcs-key">Réserves</div></div>
        </div>
      </div>
      <div class="project-card-footer">
        <span class="project-card-client">M. &amp; Mme Girard</span>
        <span class="project-card-date">Livré fév. 2026</span>
      </div>
    </div>

    <!-- CARD NOUVEAU PROJET -->
    <div class="new-project-card" onclick="openModal()" data-tip="Créer un projet depuis un gabarit — résidentiel, tertiaire, commercial, etc.">
      <div class="new-project-icon">+</div>
      <div class="new-project-label">Nouveau projet</div>
      <div class="new-project-sub">Depuis un gabarit ou de zéro</div>
    </div>

  </div>
</div>

<!-- ═══════════ VUE : FINANCES GLOBALES ═══════════ -->
<div class="view" id="view-finances">
  <div class="fin-header">
    <div>
      <div class="projects-title">Finances</div>
      <div class="projects-sub">Vue globale des honoraires &amp; encaissements — tous projets actifs</div>
    </div>
    <div style="display:flex;gap:8px;">
      <button class="btn" data-tip="Exporter le tableau de synthèse en Excel ou PDF" onclick="showToast('Export en cours…')">Exporter</button>
      <button class="btn primary" data-tip="Émettre une nouvelle facture sur l'un des projets" onclick="showToast('Sélectionnez un projet pour facturer')">+ Nouvelle facture</button>
    </div>
  </div>

  <div class="fin-section">

    <!-- KPIs globaux -->
    <div class="fin-kpis">
      <div class="fin-kpi">
        <div class="fin-kpi-label">Total honoraires HT</div>
        <div class="fin-kpi-val">68 400 €</div>
        <div class="fin-kpi-sub" style="color:var(--gray-400)">6 projets actifs</div>
      </div>
      <div class="fin-kpi">
        <div class="fin-kpi-label">Encaissé YTD</div>
        <div class="fin-kpi-val" style="color:var(--green-700)">31 200 €</div>
        <div class="fin-kpi-sub" style="color:var(--green-500)">46% du total</div>
        <div class="fin-kpi-bar"><div class="fin-kpi-bar-fill" style="width:46%;background:var(--green-500)"></div></div>
      </div>
      <div class="fin-kpi">
        <div class="fin-kpi-label">En attente de règlement</div>
        <div class="fin-kpi-val" style="color:var(--amber-700)">11 400 €</div>
        <div class="fin-kpi-sub" style="color:var(--amber-700)">3 factures envoyées</div>
      </div>
      <div class="fin-kpi">
        <div class="fin-kpi-label">Restant à facturer</div>
        <div class="fin-kpi-val">25 800 €</div>
        <div class="fin-kpi-sub" style="color:var(--gray-400)">Phases à venir</div>
      </div>
      <div class="fin-kpi">
        <div class="fin-kpi-label">En retard de paiement</div>
        <div class="fin-kpi-val" style="color:var(--red-700)">2</div>
        <div class="fin-kpi-sub" style="color:var(--red-700)">Relances à envoyer</div>
      </div>
    </div>

    <!-- Alertes -->
    <div class="section-label">Actions requises</div>
    <div class="fin-alerts">
      <div class="fin-alert-row urgent">
        <div class="fin-alert-dot amber"></div>
        <div class="fin-alert-text">
          <strong>Appartement Raspail</strong> — Acompte mi-projet · F2026-004 envoyée le 2 avr. · <span style="color:var(--amber-700)">J+5 dépassé</span>
        </div>
        <div class="fin-alert-amount" style="color:var(--amber-700)">5 112 € TTC</div>
        <button class="fin-alert-action" data-tip="Envoyer un email de relance à M. & Mme Lefèvre" onclick="showToast('Relance envoyée — Lefèvre')">Relancer</button>
      </div>
      <div class="fin-alert-row urgent">
        <div class="fin-alert-dot amber"></div>
        <div class="fin-alert-text">
          <strong>Penthouse Opéra</strong> — Solde chantier · F2026-009 envoyée le 28 mars · <span style="color:var(--amber-700)">J+10 dépassé</span>
        </div>
        <div class="fin-alert-amount" style="color:var(--amber-700)">6 288 € TTC</div>
        <button class="fin-alert-action" data-tip="Envoyer un email de relance à M. Bertrand" onclick="showToast('Relance envoyée — Bertrand')">Relancer</button>
      </div>
      <div class="fin-alert-row">
        <div class="fin-alert-dot green"></div>
        <div class="fin-alert-text">
          <strong>Villa Saint-Cloud</strong> — Acompte mi-projet facturable · Chantier à 62%
        </div>
        <div class="fin-alert-amount" style="color:var(--green-700)">9 600 € TTC</div>
        <button class="fin-alert-action" data-tip="Générer et envoyer la facture d'acompte mi-projet à la famille Dumont" onclick="showToast('Facture générée — Dumont')">Facturer</button>
      </div>
    </div>

    <!-- Tableau par projet -->
    <div class="section-label">Détail par projet</div>
    <div class="fin-table-wrap">
      <div class="fin-table-head">
        <div class="fin-th">Projet · Client</div>
        <div class="fin-th">Honoraires HT</div>
        <div class="fin-th">Encaissé</div>
        <div class="fin-th">En attente</div>
        <div class="fin-th">À facturer</div>
        <div class="fin-th">Avancement</div>
      </div>

      <!-- Raspail -->
      <div class="fin-row" onclick="goToProject()">
        <div>
          <div class="fin-proj-name">Appartement Raspail</div>
          <div class="fin-proj-client">M. &amp; Mme Lefèvre · DCE</div>
        </div>
        <div class="fin-cell bold">14 200 €</div>
        <div class="fin-cell green">5 680 €</div>
        <div class="fin-cell warn">4 260 € ⚠</div>
        <div class="fin-cell muted">4 260 €</div>
        <div>
          <div class="fin-cell" style="font-size:12px">40% encaissé</div>
          <div class="fin-mini-bar"><div class="fin-mini-bar-fill" style="width:40%"></div></div>
        </div>
      </div>

      <!-- Saint-Cloud -->
      <div class="fin-row" onclick="goToProject()">
        <div>
          <div class="fin-proj-name">Villa Saint-Cloud</div>
          <div class="fin-proj-client">Famille Dumont · Chantier</div>
        </div>
        <div class="fin-cell bold">24 000 €</div>
        <div class="fin-cell green">9 600 €</div>
        <div class="fin-cell muted">—</div>
        <div class="fin-cell" style="color:var(--green-700);font-weight:500">8 000 €</div>
        <div>
          <div class="fin-cell" style="font-size:12px">40% encaissé</div>
          <div class="fin-mini-bar"><div class="fin-mini-bar-fill" style="width:40%"></div></div>
        </div>
      </div>

      <!-- Boutique Marais -->
      <div class="fin-row" onclick="goToProject()">
        <div>
          <div class="fin-proj-name">Boutique Le Marais</div>
          <div class="fin-proj-client">Mme Fontaine · APS</div>
        </div>
        <div class="fin-cell bold">6 800 €</div>
        <div class="fin-cell green">2 720 €</div>
        <div class="fin-cell muted">—</div>
        <div class="fin-cell muted">4 080 €</div>
        <div>
          <div class="fin-cell" style="font-size:12px">40% encaissé</div>
          <div class="fin-mini-bar"><div class="fin-mini-bar-fill" style="width:40%"></div></div>
        </div>
      </div>

      <!-- Penthouse -->
      <div class="fin-row" onclick="goToProject()">
        <div>
          <div class="fin-proj-name">Penthouse Opéra</div>
          <div class="fin-proj-client">M. Bertrand · Chantier 80%</div>
        </div>
        <div class="fin-cell bold">14 600 €</div>
        <div class="fin-cell green">5 840 €</div>
        <div class="fin-cell warn">5 240 € ⚠</div>
        <div class="fin-cell muted">3 520 €</div>
        <div>
          <div class="fin-cell" style="font-size:12px">40% encaissé</div>
          <div class="fin-mini-bar"><div class="fin-mini-bar-fill" style="width:40%"></div></div>
        </div>
      </div>

      <!-- Maison Bordeaux -->
      <div class="fin-row" onclick="goToProject()">
        <div>
          <div class="fin-proj-name">Maison Bordeaux</div>
          <div class="fin-proj-client">M. &amp; Mme Girard · Livré</div>
        </div>
        <div class="fin-cell bold">8 000 €</div>
        <div class="fin-cell green" style="color:var(--green-700)">8 000 €</div>
        <div class="fin-cell muted">—</div>
        <div class="fin-cell muted">—</div>
        <div>
          <div class="fin-cell" style="font-size:12px;color:var(--green-700)">100% soldé ✓</div>
          <div class="fin-mini-bar"><div class="fin-mini-bar-fill" style="width:100%;background:var(--green-700)"></div></div>
        </div>
      </div>

      <!-- Ligne total -->
      <div class="fin-row total-row">
        <div><div class="fin-proj-name" style="color:var(--gray-400)">Total</div></div>
        <div class="fin-cell bold">68 400 €</div>
        <div class="fin-cell bold" style="color:var(--green-700)">31 840 €</div>
        <div class="fin-cell bold" style="color:var(--amber-700)">9 500 €</div>
        <div class="fin-cell bold">19 860 €</div>
        <div>
          <div class="fin-cell" style="font-size:12px">47% encaissé</div>
          <div class="fin-mini-bar"><div class="fin-mini-bar-fill" style="width:47%"></div></div>
        </div>
      </div>
    </div>

    <!-- Graphique mensuel -->
    <div class="section-label">Encaissements mensuels 2026</div>
    <div class="fin-chart-wrap">
      <div class="fin-bar-chart" id="fin-chart"></div>
      <div class="fin-chart-legend">
        <div class="fin-legend-item"><div class="fin-legend-dot" style="background:var(--green-700)"></div>Encaissé</div>
        <div class="fin-legend-item"><div class="fin-legend-dot" style="background:var(--green-200)"></div>Prévu</div>
      </div>
    </div>

  </div>
</div>

<!-- ═══════════ VUE : FICHE PROJET ═══════════ -->
<div class="view" id="view-project">
  <div class="project-header">
    <div class="project-header-top">
      <div>
        <div class="project-tag">Paris 14e · Résidentiel</div>
        <div class="project-name">Appartement Raspail</div>
        <div class="project-sub">87 m² · Rénovation complète · M. &amp; Mme Lefèvre · Démarré jan. 2026</div>
      </div>
      <div style="display:flex;gap:8px;align-items:center;flex-shrink:0">
        <button class="btn" data-tip="Exporter la fiche projet complète en PDF (documents, planning, budget)">Exporter PDF</button>
        <button class="btn" data-tip="Envoyer un lien d'invitation au client pour accéder à son portail sécurisé">Inviter client</button>
        <button class="btn primary" data-tip="Ajouter un document, générer un document par IA, ou importer un fichier existant">+ Nouveau document</button>
        <span class="phase-badge">Phase DCE</span>
      </div>
    </div>
    <div class="metrics-row">
      <div class="metric"><div class="metric-label">Budget total</div><div class="metric-value">142 000 €</div><div class="metric-sub warn">+3% vs estimatif</div></div>
      <div class="metric"><div class="metric-label">Engagé</div><div class="metric-value">61 400 €</div><div class="metric-sub">43% du budget</div></div>
      <div class="metric"><div class="metric-label">Avancement global</div><div class="metric-value">38%</div><div class="metric-sub">Phase 3 sur 5</div></div>
      <div class="metric"><div class="metric-label">Livraison estimée</div><div class="metric-value">oct. 2026</div><div class="metric-sub">Dans 27 semaines</div></div>
    </div>
    <div class="tabs">
      <div class="tab active" data-tab="overview" data-tip="Résumé du projet — phases, infos générales, avancement global">Vue d'ensemble</div>
      <div class="tab" data-tab="docs" data-tip="GED — tous les documents classés par phase avec statuts Privé / Partagé / Validé / IA">Documents <span class="tab-pill tp-green">12</span></div>
      <div class="tab" data-tab="cr" data-tip="Comptes-rendus de chantier — générés automatiquement par IA en 25 secondes">Comptes-rendus <span class="tab-pill tp-red">1 nouveau</span></div>
      <div class="tab" data-tab="gantt" data-tip="Planning Gantt — toutes les phases, les lots artisans, et la ligne du temps">Planning</div>
      <div class="tab" data-tab="art" data-tip="Portail artisan cloisonné — chaque intervenant accède uniquement à son lot">Intervenants <span class="tab-pill tp-green">5</span></div>
      <div class="tab" data-tab="honoraires" data-tip="Suivi des honoraires architecte — acomptes, factures, paiements reçus et à venir">Honoraires <span class="tab-pill tp-red">1 à encaisser</span></div>
    </div>
  </div>

  <div class="main">

    <!-- OVERVIEW -->
    <div class="tab-panel active" id="panel-overview">
      <div class="section-label">Phases du projet</div>
      <div class="phases-strip">
        <div class="phase-card" data-tip="Phase ESQ terminée — esquisses validées par le client le 15 fév. 2026"><div style="display:flex;align-items:center;margin-bottom:4px"><span class="phase-dot dot-done"></span><span class="phase-card-name">ESQ</span></div><div class="phase-card-dates">jan. → fév. 2026</div><div class="phase-card-pct pct-done">100%</div><div class="progress-bar-wrap"><div class="progress-bar-fill" style="width:100%;background:var(--green-700)"></div></div></div>
        <div class="phase-card" data-tip="Avant-projet validé — plans APD v3 approuvés le 18 mars 2026"><div style="display:flex;align-items:center;margin-bottom:4px"><span class="phase-dot dot-done"></span><span class="phase-card-name">APS / APD</span></div><div class="phase-card-dates">fév. → mars 2026</div><div class="phase-card-pct pct-done">100%</div><div class="progress-bar-wrap"><div class="progress-bar-fill" style="width:100%;background:var(--green-700)"></div></div></div>
        <div class="phase-card active" data-tip="DCE en cours — 3 CCTP générés par IA, 1 devis artisan en attente"><div style="display:flex;align-items:center;margin-bottom:4px"><span class="phase-dot dot-active"></span><span class="phase-card-name">DCE</span></div><div class="phase-card-dates">avr. → mai 2026</div><div class="phase-card-pct pct-active">65%</div><div class="progress-bar-wrap"><div class="progress-bar-fill" style="width:65%"></div></div></div>
        <div class="phase-card" data-tip="Direction de l'Exécution des Travaux — démarrage prévu juin 2026 après signature des OS"><div style="display:flex;align-items:center;margin-bottom:4px"><span class="phase-dot dot-pending"></span><span class="phase-card-name">DET / Chantier</span></div><div class="phase-card-dates">juin → sept. 2026</div><div class="phase-card-pct pct-pending">—</div><div class="progress-bar-wrap"><div class="progress-bar-fill" style="width:0%"></div></div></div>
        <div class="phase-card" data-tip="Opérations Préalables à la Réception — visite finale, levée des réserves, remise des clés"><div style="display:flex;align-items:center;margin-bottom:4px"><span class="phase-dot dot-pending"></span><span class="phase-card-name">OPR / Livraison</span></div><div class="phase-card-dates">oct. 2026</div><div class="phase-card-pct pct-pending">—</div><div class="progress-bar-wrap"><div class="progress-bar-fill" style="width:0%"></div></div></div>
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
          <div class="doc-file" data-tip="Contrat de maîtrise d'œuvre signé électroniquement par M. &amp; Mme Lefèvre le 12 jan. 2026"><div class="doc-file-icon green"></div><span class="doc-file-name">Contrat MOE — Raspail v1.pdf</span><span class="badge badge-valide">Validé</span><span class="doc-file-date">12 jan. 2026</span></div>
          <div class="doc-file" data-tip="Grille d'honoraires annexée au contrat — phases et montants par tranche"><div class="doc-file-icon green"></div><span class="doc-file-name">Annexe honoraires.pdf</span><span class="badge badge-valide">Validé</span><span class="doc-file-date">12 jan. 2026</span></div>
        </div>
      </div>
      <div class="doc-section" id="sec2">
        <div class="doc-section-hdr" onclick="toggleSection('sec2')"><span class="doc-num">02</span><span class="doc-sec-name">APS — Avant-Projet Sommaire</span><span class="badge badge-valide">Validé ✓</span><span class="doc-count">3 docs</span><span class="chevron" id="chev-sec2">▾</span></div>
        <div class="doc-files collapsed" id="files-sec2">
          <div class="doc-file" data-tip="Plans côtés version 2 — approuvés par les clients le 28 fév. 2026. Inclut les cotes de toutes les pièces."><div class="doc-file-icon green"></div><span class="doc-file-name">Plans APS v2.pdf</span><span class="badge badge-valide">Validé</span><span class="doc-file-date">28 fév. 2026</span></div>
          <div class="doc-file" data-tip="Planche tendances — palette matériaux, mobilier, ambiance. Approuvée par le client."><div class="doc-file-icon"></div><span class="doc-file-name">Moodboard directions créatives.pdf</span><span class="badge badge-valide">Validé</span><span class="doc-file-date">20 fév. 2026</span></div>
          <div class="doc-file" data-tip="Estimatif provisoire des travaux en phase APS — base de référence pour le budget."><div class="doc-file-icon"></div><span class="doc-file-name">Estimatif APS.xlsx</span><span class="badge badge-valide">Validé</span><span class="doc-file-date">28 fév. 2026</span></div>
        </div>
      </div>
      <div class="doc-section" id="sec3">
        <div class="doc-section-hdr" onclick="toggleSection('sec3')"><span class="doc-num">03</span><span class="doc-sec-name">DCE — Dossiers de Consultation</span><span class="badge badge-partage">Partagé</span><span class="doc-count">4 docs</span><span class="chevron open" id="chev-sec3">▾</span></div>
        <div class="doc-files" id="files-sec3">
          <div class="doc-file" data-tip="Cahier des Clauses Techniques Particulières — lot électricité. Généré par IA en 22s. Partagé aux entreprises le 2 avr."><div class="doc-file-icon green"></div><span class="doc-file-name">CCTP Électricité.pdf</span><span class="badge badge-ia" style="margin-right:2px">IA</span><span class="badge badge-valide">Validé</span><span class="doc-file-date">2 avr. 2026</span></div>
          <div class="doc-file" data-tip="CCTP Plomberie généré par IA — encore en mode Privé, pas encore envoyé aux artisans. Document nouveau."><div class="doc-file-icon"></div><span class="doc-file-name">CCTP Plomberie.pdf</span><span class="badge badge-ia" style="margin-right:2px">IA</span><span class="badge badge-prive">Privé</span><span class="new-dot" style="margin:0 4px"></span><span class="doc-file-date">6 avr. 2026</span></div>
          <div class="doc-file" data-tip="CCTP Peinture généré par IA — encore en mode Privé, pas encore envoyé aux artisans. Document nouveau."><div class="doc-file-icon"></div><span class="doc-file-name">CCTP Peinture.pdf</span><span class="badge badge-ia" style="margin-right:2px">IA</span><span class="badge badge-prive">Privé</span><span class="new-dot" style="margin:0 4px"></span><span class="doc-file-date">7 avr. 2026</span></div>
          <div class="doc-file" data-tip="Plans techniques APD version 3 — partagés avec les entreprises pour la consultation."><div class="doc-file-icon"></div><span class="doc-file-name">Plans techniques APD v3.pdf</span><span class="badge badge-partage">Partagé</span><span class="doc-file-date">15 mars 2026</span></div>
        </div>
      </div>
      <div class="doc-section" id="sec4">
        <div class="doc-section-hdr" onclick="toggleSection('sec4')"><span class="doc-num">04</span><span class="doc-sec-name">Administratif</span><span class="badge badge-prive">Privé</span><span class="doc-count">3 docs</span><span class="chevron" id="chev-sec4">▾</span></div>
        <div class="doc-files collapsed" id="files-sec4">
          <div class="doc-file" data-tip="Déclaration Préalable déposée en mairie le 10 mars 2026 — délai d'instruction : 1 mois."><div class="doc-file-icon"></div><span class="doc-file-name">Déclaration Préalable — dépôt mairie.pdf</span><span class="badge badge-prive">Privé</span><span class="doc-file-date">10 mars 2026</span></div>
          <div class="doc-file" data-tip="Attestation d'assurance Dommages-Ouvrage souscrite par le client — obligatoire avant ouverture du chantier."><div class="doc-file-icon"></div><span class="doc-file-name">Attestation assurance DO.pdf</span><span class="badge badge-valide">Validé</span><span class="doc-file-date">8 jan. 2026</span></div>
          <div class="doc-file" data-tip="Cahier des Clauses Administratives Particulières — généré par IA. Définit les conditions contractuelles avec les artisans."><div class="doc-file-icon"></div><span class="doc-file-name">CCAP — Cahier des Clauses Admin.pdf</span><span class="badge badge-ia" style="margin-right:2px">IA</span><span class="badge badge-prive">Privé</span><span class="doc-file-date">3 avr. 2026</span></div>
        </div>
      </div>
    </div>

    <!-- CR -->
    <div class="tab-panel" id="panel-cr">
      <div class="cr-generate-bar">
        <div><div class="cr-generate-label">Générer un compte-rendu par IA</div><div class="cr-generate-sub">L'IA analyse les données de la semaine — tâches, réserves, situations — et rédige le CR complet en ~25 secondes</div></div>
        <button class="btn primary" data-tip="Tailere génère automatiquement le CR depuis les données du projet : tâches accomplies, réserves ouvertes/levées, situations de travaux, présents à la réunion. Vous n'avez plus qu'à valider." onclick="showToast('Génération IA en cours… CR prêt dans 25s')">+ Générer CR IA</button>
      </div>
      <div class="cr-list">
        <div class="cr-card new">
          <div class="cr-top"><div class="cr-icon">📋</div><div class="cr-title-block"><div class="cr-title">CR n°3 — Réunion DCE — Lot Électricité</div><div class="cr-date">7 avr. 2026 · <span style="color:var(--amber-700)">Non diffusé</span></div></div><span class="badge badge-ia">IA</span></div>
          <div class="cr-preview">"Présence : S. Marchand (architecte), J. Durand (élec.), M. Lefèvre (client). Avancement lot électricité 70%. Réserve tableau central levée. Prochaine réunion 14 avr."</div>
          <div class="cr-footer"><span class="badge badge-ia">IA</span><span class="cr-gen">Généré en 22s</span><span style="flex:1"></span><button class="btn primary" style="font-size:11px;padding:5px 10px" data-tip="Envoyer ce CR par email au client et aux artisans concernés. Une fois diffusé, le document est archivé et non modifiable." onclick="showToast('CR diffusé au client et aux artisans')">Diffuser</button></div>
        </div>
        <div class="cr-card">
          <div class="cr-top"><div class="cr-icon">📋</div><div class="cr-title-block"><div class="cr-title">CR n°2 — Réunion APD — Validation plans</div><div class="cr-date">18 mars 2026</div></div><span class="badge badge-ia">IA</span></div>
          <div class="cr-preview">"Validation plans APD v3 par clients. Modifications cloison cuisine intégrées. Estimatif travaux confirmé à 142 000 €. Prochaine étape : lancement DCE."</div>
          <div class="cr-footer"><span class="badge badge-ia">IA</span><span class="cr-gen">Généré en 31s</span><span style="flex:1"></span><span class="cr-read">✓✓ Lu le 19 mars</span></div>
        </div>
        <div class="cr-card">
          <div class="cr-top"><div class="cr-icon">📋</div><div class="cr-title-block"><div class="cr-title">CR n°1 — Réunion de lancement ESQ</div><div class="cr-date">15 jan. 2026</div></div><span class="badge badge-ia">IA</span></div>
          <div class="cr-preview">"Première réunion client. Programme validé. Surface : 87 m². Budget validé : 140–145k€. Délai livraison souhaité : oct. 2026."</div>
          <div class="cr-footer"><span class="badge badge-ia">IA</span><span class="cr-gen">Généré en 28s</span><span style="flex:1"></span><span class="cr-read">✓✓ Lu le 16 jan.</span></div>
        </div>
      </div>
    </div>

    <!-- GANTT -->
    <div class="tab-panel" id="panel-gantt">
      <div class="gantt-wrap">
        <div class="gantt-head"><div class="gantt-head-label">Phase</div><div class="gantt-months"><div class="gantt-month">Jan</div><div class="gantt-month">Fév</div><div class="gantt-month">Mars</div><div class="gantt-month current">Avr</div><div class="gantt-month">Mai</div><div class="gantt-month">Juin</div><div class="gantt-month">Juil</div><div class="gantt-month">Août</div><div class="gantt-month">Sept</div><div class="gantt-month">Oct</div></div></div>
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
        <div class="legend-item"><div style="width:9px;height:9px;background:var(--green-900);transform:rotate(45deg);flex-shrink:0"></div>Jalon de validation</div>
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
        <div class="art-footer"><span class="art-link" data-tip="Ouvrir le portail sécurisé de Jean Durand — il voit uniquement son lot, ses situations, ses réserves" onclick="showToast('Ouverture du portail artisan Durand Électricité…')">→ Ouvrir le portail artisan</span><span class="art-note warn">Situation n°3 attendue le 15 avr.</span></div>
      </div>
      <div class="section-label">Lot 02 · Plomberie &amp; Sanitaires</div>
      <div class="art-card">
        <div class="art-card-top"><div class="avatar av-amber">PM</div><div class="art-info"><div class="art-name">Pierre Martin — Martin Plomberie</div><div class="art-lot">Lot 02 · Plomberie &amp; Sanitaires · Paris 92</div></div><span class="status-pill sp-attente">OS en attente</span></div>
        <div class="art-stats"><div class="art-stat"><div class="art-stat-val">12 800 €</div><div class="art-stat-key">Devis accepté</div></div><div class="art-stat"><div class="art-stat-val">0 / 0</div><div class="art-stat-key">Situations</div></div><div class="art-stat"><div class="art-stat-val">—</div><div class="art-stat-key">Réserves</div></div></div>
        <div class="art-footer"><span class="art-link" data-tip="Émettre l'Ordre de Service officiel — Pierre Martin reçoit un email avec accès à son portail et peut démarrer le chantier" onclick="showToast('Ordre de Service émis — notification envoyée à Martin Plomberie')">→ Émettre l'Ordre de Service</span><span class="art-note warn">OS non encore émis — démarrage bloqué</span></div>
      </div>
      <div class="section-label">Lot 03 · Peinture &amp; Revêtements</div>
      <div class="art-card">
        <div class="art-card-top"><div class="avatar av-gray">AZ</div><div class="art-info"><div class="art-name">Azur Peinture SARL</div><div class="art-lot">Lot 03 · Peinture &amp; Revêtements · Paris 75</div></div><span class="status-pill sp-invite">Invité</span></div>
        <div class="art-stats"><div class="art-stat"><div class="art-stat-val" style="font-size:12px;color:var(--gray-400)">En attente</div><div class="art-stat-key">Devis</div></div><div class="art-stat"><div class="art-stat-val">—</div><div class="art-stat-key">Marché</div></div><div class="art-stat"><div class="art-stat-val">—</div><div class="art-stat-key">Situations</div></div></div>
        <div class="art-footer"><span class="art-link" data-tip="Envoyer un email de relance à Azur Peinture avec rappel de la date limite de remise des devis" onclick="showToast('Email de relance envoyé à Azur Peinture')">→ Relancer l'artisan</span><span class="art-note">Devis demandé le 3 avr. 2026</span></div>
      </div>
      <div class="section-label">Client</div>
      <div class="art-card">
        <div class="art-card-top"><div class="avatar av-green">LL</div><div class="art-info"><div class="art-name">M. &amp; Mme Lefèvre</div><div class="art-lot">Portail client · Accès limité aux documents partagés</div></div><span class="status-pill sp-actif">Actif</span></div>
        <div class="art-stats"><div class="art-stat"><div class="art-stat-val" style="color:var(--green-700)">3</div><div class="art-stat-key">Docs validés</div></div><div class="art-stat"><div class="art-stat-val">2</div><div class="art-stat-key">Docs lus</div></div><div class="art-stat"><div class="art-stat-val">0</div><div class="art-stat-key">En attente</div></div></div>
        <div class="art-footer"><span class="art-link" data-tip="Ouvrir le portail client — ils voient uniquement les documents partagés, les plans approuvés, et les CR diffusés" onclick="showToast('Ouverture du portail client Lefèvre…')">→ Ouvrir le portail client</span><span class="art-note">Dernière connexion il y a 2 jours</span></div>
      </div>
      <div class="add-intervenant" data-tip="Ajouter un artisan, un bureau d'études, un co-traitant ou un sous-traitant à ce projet" onclick="showToast('Invitation d\'un nouvel intervenant…')"><span style="font-size:16px;color:var(--green-500)">+</span>Inviter un intervenant (artisan, BE, co-traitant)</div>
    </div>

    <!-- HONORAIRES -->
    <div class="tab-panel" id="panel-honoraires">

      <!-- KPIs -->
      <div class="hon-summary">
        <div class="hon-kpi">
          <div class="hon-kpi-label">Total honoraires HT</div>
          <div class="hon-kpi-val">14 200 €</div>
          <div class="hon-kpi-sub" style="color:var(--gray-400)">10% du budget travaux</div>
        </div>
        <div class="hon-kpi">
          <div class="hon-kpi-label">Encaissé</div>
          <div class="hon-kpi-val" style="color:var(--green-700)">5 680 €</div>
          <div class="hon-kpi-sub" style="color:var(--green-500)">40% du total HT</div>
          <div class="hon-progress-wrap"><div class="hon-progress-fill" style="width:40%;background:var(--green-500)"></div></div>
        </div>
        <div class="hon-kpi">
          <div class="hon-kpi-label">En attente de règlement</div>
          <div class="hon-kpi-val" style="color:var(--amber-700)">5 112 €</div>
          <div class="hon-kpi-sub" style="color:var(--amber-700)">Facture envoyée · J+5</div>
        </div>
        <div class="hon-kpi">
          <div class="hon-kpi-label">Solde à facturer</div>
          <div class="hon-kpi-val">5 680 €</div>
          <div class="hon-kpi-sub" style="color:var(--gray-400)">À la réception · oct. 2026</div>
        </div>
      </div>

      <!-- Alerte acompte en attente -->
      <div class="hon-alert-banner">
        <div class="hon-alert-icon">⚠</div>
        <div class="hon-alert-text"><strong>Acompte mi-projet en attente de paiement</strong> — Facture F2026-004 de 5 112 € TTC envoyée le 2 avr. 2026. Échéance dépassée de 5 jours. M. &amp; Mme Lefèvre n'ont pas encore réglé.</div>
        <button class="hon-alert-action" data-tip="Envoyer un email de relance au client avec rappel de la facture et lien de virement" onclick="showToast('Email de relance envoyé à M. & Mme Lefèvre')">Relancer le client</button>
      </div>

      <!-- Tableau des 3 acomptes -->
      <div class="section-label">Échéancier</div>
      <div class="hon-table-wrap">
        <div class="hon-table-header">
          <div class="hon-th">Appel de fonds</div>
          <div class="hon-th">Quote-part</div>
          <div class="hon-th">Montant HT</div>
          <div class="hon-th">TVA 20%</div>
          <div class="hon-th">TTC</div>
          <div class="hon-th">Statut &amp; action</div>
        </div>

        <!-- Acompte 1 — payé -->
        <div class="hon-row">
          <div>
            <div class="hon-phase-name">Acompte de départ</div>
            <div class="hon-phase-sub">À la signature du contrat · Facture F2026-001 · 14 jan. 2026</div>
          </div>
          <div class="hon-cell">40%</div>
          <div class="hon-cell">5 680 €</div>
          <div class="hon-cell muted">1 136 €</div>
          <div class="hon-cell green">6 816 €</div>
          <div style="display:flex;align-items:center;gap:6px;">
            <span class="hon-status-pill hsp-paye">Payé ✓</span>
            <button class="hon-action-btn" data-tip="Télécharger la facture F2026-001 en PDF" onclick="showToast('Téléchargement F2026-001…')">PDF</button>
          </div>
        </div>

        <!-- Acompte 2 — facturé, en attente -->
        <div class="hon-row" style="background:#FFFBF3;">
          <div>
            <div class="hon-phase-name">Acompte mi-projet</div>
            <div class="hon-phase-sub">À la validation APD / mi-chantier · Facture F2026-004 · 2 avr. 2026</div>
          </div>
          <div class="hon-cell">40%</div>
          <div class="hon-cell">5 680 €</div>
          <div class="hon-cell muted">1 136 €</div>
          <div class="hon-cell warn">5 112 € ⚠</div>
          <div style="display:flex;align-items:center;gap:6px;">
            <span class="hon-status-pill hsp-envoye">Envoyé</span>
            <button class="hon-action-btn" data-tip="Télécharger la facture F2026-004 en PDF" onclick="showToast('Téléchargement F2026-004…')">PDF</button>
            <button class="hon-action-btn primary" data-tip="Marquer cet acompte comme encaissé après réception du virement bancaire" onclick="showToast('Acompte mi-projet marqué encaissé ✓')">Encaissé</button>
          </div>
        </div>

        <!-- Solde — à facturer -->
        <div class="hon-row">
          <div>
            <div class="hon-phase-name">Solde final</div>
            <div class="hon-phase-sub">À la signature du PV de réception OPR · Prévu oct. 2026</div>
          </div>
          <div class="hon-cell">20%</div>
          <div class="hon-cell">2 840 €</div>
          <div class="hon-cell muted">568 €</div>
          <div class="hon-cell muted">3 408 €</div>
          <div style="display:flex;align-items:center;gap:6px;">
            <span class="hon-status-pill hsp-afacturer">À facturer</span>
            <button class="hon-action-btn" disabled style="opacity:.35;cursor:default" data-tip="Le solde sera facturable uniquement après signature du PV de réception — OPR prévue oct. 2026">Facturer</button>
          </div>
        </div>

        <!-- Ligne total -->
        <div class="hon-row" style="background:var(--cream);border-top:1px solid var(--cream-border);">
          <div><div class="hon-phase-name" style="color:var(--gray-400);font-weight:500">Total</div></div>
          <div class="hon-cell" style="font-weight:500">100%</div>
          <div class="hon-cell" style="font-weight:500">14 200 €</div>
          <div class="hon-cell" style="font-weight:500">2 840 €</div>
          <div class="hon-cell" style="font-weight:500">17 040 €</div>
          <div></div>
        </div>

      </div>

      <!-- Timeline -->
      <div class="section-label">Chronologie des paiements</div>
      <div class="hon-timeline">
        <div class="hon-tl-row">
          <div style="position:relative"><div class="hon-tl-dot paid"></div><div class="hon-tl-line"></div></div>
          <div class="hon-tl-label">Acompte de départ encaissé par virement — F2026-001</div>
          <div class="hon-tl-amount" style="color:var(--green-700)">+ 6 816 € TTC</div>
          <div class="hon-tl-date" style="margin-left:12px;min-width:90px;text-align:right">14 jan. 2026</div>
        </div>
        <div class="hon-tl-row">
          <div style="position:relative"><div class="hon-tl-dot sent"></div><div class="hon-tl-line"></div></div>
          <div class="hon-tl-label">Acompte mi-projet facturé — F2026-004 · en attente de règlement</div>
          <div class="hon-tl-amount" style="color:var(--amber-700)">5 112 € TTC</div>
          <div class="hon-tl-date" style="margin-left:12px;min-width:90px;text-align:right">2 avr. 2026</div>
        </div>
        <div class="hon-tl-row">
          <div style="position:relative"><div class="hon-tl-dot pending"></div></div>
          <div class="hon-tl-label" style="color:var(--gray-400)">Solde final — après réception OPR (prévu)</div>
          <div class="hon-tl-amount" style="color:var(--gray-400)">3 408 € TTC</div>
          <div class="hon-tl-date" style="margin-left:12px;min-width:90px;text-align:right;color:var(--gray-400)">oct. 2026</div>
        </div>
      </div>

      <div style="display:flex;justify-content:flex-end;gap:8px;margin-top:4px;">
        <button class="btn" data-tip="Modifier les pourcentages ou les déclencheurs de chaque appel de fonds" onclick="showToast('Modification de l\'échéancier…')">Modifier l'échéancier</button>
        <button class="btn primary" data-tip="Générer et envoyer une facture au client par email avec calcul TVA automatique" onclick="showToast('Nouvelle facture générée et envoyée')">+ Nouvelle facture</button>
      </div>

    </div>
  </div><!-- /main -->
</div><!-- /view-project -->

<!-- ═══════════ MODAL CRÉATION PROJET ═══════════ -->
<div class="modal-overlay" id="modal-overlay" onclick="closeModalIfOutside(event)">
  <div class="modal">
    <div class="modal-header">
      <div><div class="modal-title">Nouveau projet</div><div class="modal-sub">Choisissez un gabarit et renseignez les informations de base</div></div>
      <button class="modal-close" onclick="closeModal()">✕</button>
    </div>
    <div class="modal-body">
      <div class="form-section-title">Gabarit de projet</div>
      <div class="gabarit-grid">
        <label class="gabarit-card selected" onclick="selectGabarit(this,'residentiel')">
          <input type="radio" name="gabarit" value="residentiel" checked>
          <div class="gabarit-name">Résidentiel</div>
          <div class="gabarit-desc">Appartement, maison, villa — rénovation ou aménagement</div>
        </label>
        <label class="gabarit-card" onclick="selectGabarit(this,'commercial')">
          <input type="radio" name="gabarit" value="commercial">
          <div class="gabarit-name">Commercial / ERP</div>
          <div class="gabarit-desc">Boutique, restaurant, bureau, espace recevant du public</div>
        </label>
        <label class="gabarit-card" onclick="selectGabarit(this,'tertiaire')">
          <input type="radio" name="gabarit" value="tertiaire">
          <div class="gabarit-name">Tertiaire</div>
          <div class="gabarit-desc">Bureau, open space, coworking, siège social</div>
        </label>
        <label class="gabarit-card" onclick="selectGabarit(this,'sourcing')">
          <input type="radio" name="gabarit" value="sourcing">
          <div class="gabarit-name">Sourcing &amp; mobilier</div>
          <div class="gabarit-desc">Projet focalisé sur la sélection et commande de mobilier</div>
        </label>
      </div>

      <div class="form-section-title" style="margin-top:20px">
        Phases du projet
        <span style="font-size:11px;font-weight:400;color:var(--gray-400);text-transform:none;letter-spacing:0;margin-left:8px">Cochez uniquement les phases nécessaires à votre mission</span>
      </div>
      <div id="phases-selector" style="display:flex;flex-direction:column;gap:6px;"></div>
      <div style="margin-top:10px;padding:10px 14px;background:var(--cream);border-radius:var(--r-md);border:0.5px solid var(--cream-border);font-size:12px;color:var(--gray-400);">
        Séquence retenue : <strong id="phases-preview" style="color:var(--gray-800);font-weight:500;"></strong>
      </div>

      <div class="form-section-title">Informations générales</div>
      <div class="form-row">
        <label>Nom du projet *</label>
        <input type="text" placeholder="ex : Appartement Haussmann, Villa Les Pins…" id="input-name">
      </div>
      <div class="form-row-2">
        <div>
          <label>Ville / adresse</label>
          <input type="text" placeholder="Paris 16e, Lyon, Bordeaux…" id="input-city">
        </div>
        <div>
          <label>Surface (m²)</label>
          <input type="number" placeholder="ex : 120" id="input-surface">
        </div>
      </div>
      <div class="form-row-2">
        <div>
          <label>Budget travaux estimé (€)</label>
          <input type="number" placeholder="ex : 150000" id="input-budget">
        </div>
        <div>
          <label>Budget mobilier estimé (€)</label>
          <input type="number" placeholder="ex : 25000" id="input-budget-mobilier">
          <div class="field-hint">Sourcing catalogue Tailere — 157 marques premium</div>
        </div>
      </div>
      <div class="form-row">
        <label>Date de livraison souhaitée</label>
        <input type="text" placeholder="ex : jan. 2027" id="input-delivery">
      </div>

      <div class="form-section-title">Client</div>
      <div class="form-row-2">
        <div>
          <label>Nom du client *</label>
          <input type="text" placeholder="ex : M. &amp; Mme Lefèvre" id="input-client-name">
        </div>
        <div>
          <label>Email du client</label>
          <input type="email" placeholder="client@email.com" id="input-client-email">
          <div class="field-hint">Une invitation sera envoyée automatiquement pour accéder au portail client</div>
        </div>
      </div>

      <div class="form-section-title">Chef de projet</div>
      <div class="form-row">
        <label>Assigner à</label>
        <select id="input-pm">
          <option>Sophie Marchand (vous)</option>
          <option>Thomas Leblanc</option>
          <option>Marie Dupont</option>
        </select>
      </div>
      <div class="form-row">
        <label>Notes internes</label>
        <textarea placeholder="Contexte du projet, contraintes particulières, notes de premier contact…" id="input-notes"></textarea>
      </div>
    </div>
    <div class="modal-footer">
      <button class="btn" onclick="closeModal()">Annuler</button>
      <button class="btn primary" data-tip="Crée le projet avec les phases prédéfinies du gabarit, invite le client par email et ouvre la fiche projet" onclick="createProject()">Créer le projet →</button>
    </div>
  </div>
</div>

<!-- TOAST -->
<div class="toast" id="toast"></div>

<script>
// ── NAVIGATION ──
function goToList(){
  document.getElementById('view-list').classList.add('active');
  document.getElementById('view-project').classList.remove('active');
  document.getElementById('view-finances').classList.remove('active');
  document.getElementById('breadcrumb').innerHTML='<span>Projets</span>';
  document.getElementById('topbar-actions').innerHTML=`
    <button class="btn" data-tip="Rechercher parmi vos projets, clients, documents" onclick="document.querySelector('.search-input').focus()">Rechercher</button>
    <button class="btn primary" data-tip="Créer un nouveau projet depuis un gabarit (résidentiel, tertiaire, commercial…)" onclick="openModal()">+ Nouveau projet</button>`;
  document.getElementById('nav-projets').classList.add('active');
  document.getElementById('nav-finances').classList.remove('active');
}
function goToProject(){
  document.getElementById('view-list').classList.remove('active');
  document.getElementById('view-finances').classList.remove('active');
  document.getElementById('view-project').classList.add('active');
  document.getElementById('breadcrumb').innerHTML=`<a onclick="goToList()">Projets</a><span style="color:var(--cream-border);margin:0 4px">›</span><span>Appartement Raspail</span>`;
  document.getElementById('topbar-actions').innerHTML='';
  document.getElementById('nav-projets').classList.remove('active');
  document.getElementById('nav-finances').classList.remove('active');
}
function goToFinances(){
  document.getElementById('view-list').classList.remove('active');
  document.getElementById('view-project').classList.remove('active');
  document.getElementById('view-finances').classList.add('active');
  document.getElementById('breadcrumb').innerHTML='<span>Finances</span>';
  document.getElementById('topbar-actions').innerHTML='';
  document.getElementById('nav-projets').classList.remove('active');
  document.getElementById('nav-finances').classList.add('active');
  renderFinChart();
}
function renderFinChart(){
  var chart = document.getElementById('fin-chart');
  if(!chart || chart.dataset.rendered) return;
  chart.dataset.rendered = '1';
  var months = ['Jan','Fév','Mars','Avr','Mai','Juin','Juil','Août','Sept','Oct','Nov','Déc'];
  var encaisse = [6816, 3408, 3408, 0, 0, 9600, 0, 0, 0, 0, 0, 0];
  var prevu    = [0,    0,    0,    5112, 8000, 0, 7200, 4800, 0, 3408, 6000, 4200];
  var max = Math.max.apply(null, encaisse.concat(prevu));
  months.forEach(function(m, i){
    var g = document.createElement('div');
    g.className = 'fin-bar-group';
    var bars = document.createElement('div');
    bars.className = 'fin-bars';
    if(encaisse[i]){
      var b = document.createElement('div');
      b.className = 'fin-bar';
      b.style.cssText = 'background:var(--green-700);height:'+Math.round((encaisse[i]/max)*96)+'px;';
      b.title = encaisse[i].toLocaleString('fr-FR')+'€ encaissé';
      bars.appendChild(b);
    }
    if(prevu[i]){
      var b2 = document.createElement('div');
      b2.className = 'fin-bar';
      b2.style.cssText = 'background:var(--green-200);height:'+Math.round((prevu[i]/max)*96)+'px;';
      b2.title = prevu[i].toLocaleString('fr-FR')+'€ prévu';
      bars.appendChild(b2);
    }
    if(!encaisse[i] && !prevu[i]){
      var empty = document.createElement('div');
      empty.style.cssText = 'width:18px;height:4px;background:var(--cream-dark);border-radius:2px;';
      bars.appendChild(empty);
    }
    var lbl = document.createElement('div');
    lbl.className = 'fin-bar-label';
    lbl.textContent = m;
    g.appendChild(bars);
    g.appendChild(lbl);
    chart.appendChild(g);
  });
}

// ── TABS ──
document.querySelectorAll('.tab').forEach(function(tab){
  tab.addEventListener('click',function(){
    var name=this.dataset.tab;
    document.querySelectorAll('.tab').forEach(function(t){t.classList.remove('active');});
    document.querySelectorAll('.tab-panel').forEach(function(p){p.classList.remove('active');p.style.display='none';});
    this.classList.add('active');
    var panel=document.getElementById('panel-'+name);
    panel.style.display='block';
    setTimeout(function(){panel.classList.add('active');},10);
  });
});
document.querySelectorAll('.tab-panel').forEach(function(p){
  if(!p.classList.contains('active')) p.style.display='none';
});

// ── DOCUMENT SECTIONS ──
function toggleSection(id){
  var f=document.getElementById('files-'+id),c=document.getElementById('chev-'+id);
  if(f.classList.contains('collapsed')){f.classList.remove('collapsed');c.classList.add('open');}
  else{f.classList.add('collapsed');c.classList.remove('open');}
}

// ── MODAL ──
function openModal(){
  document.getElementById('modal-overlay').classList.add('open');
}
function closeModal(){
  document.getElementById('modal-overlay').classList.remove('open');
}
function closeModalIfOutside(e){
  if(e.target===document.getElementById('modal-overlay')) closeModal();
}
function selectGabarit(el, key){
  document.querySelectorAll('.gabarit-card').forEach(function(c){c.classList.remove('selected');});
  el.classList.add('selected');
  renderPhases(key);
}

// Phase definitions per gabarit
var GABARITS = {
  residentiel: [
    {id:'esq',   label:'ESQ',    desc:'Esquisse — premières intentions spatiales',         required:true,  checked:true},
    {id:'aps',   label:'APS',    desc:'Avant-Projet Sommaire — plans d\'ensemble',          required:false, checked:true},
    {id:'apd',   label:'APD',    desc:'Avant-Projet Définitif — plans cotés validés',       required:true,  checked:true},
    {id:'dce',   label:'DCE',    desc:'Consultation entreprises — CCTP, devis, OS',         required:false, checked:true},
    {id:'det',   label:'DET',    desc:'Direction d\'exécution — suivi chantier, CR, réserves', required:false, checked:true},
    {id:'opr',   label:'OPR',    desc:'Opérations préalables à la réception — levée réserves', required:false, checked:true},
    {id:'daact', label:'DAACT',  desc:'Déclaration d\'achèvement et de conformité des travaux', required:false, checked:true},
  ],
  commercial: [
    {id:'esq',   label:'ESQ',    desc:'Esquisse — premières intentions spatiales',          required:true,  checked:true},
    {id:'aps',   label:'APS',    desc:'Avant-Projet Sommaire',                               required:false, checked:true},
    {id:'apd',   label:'APD',    desc:'Avant-Projet Définitif — plans cotés validés',        required:true,  checked:true},
    {id:'dce',   label:'DCE',    desc:'Consultation entreprises — CCTP, devis, OS',          required:false, checked:true},
    {id:'det',   label:'DET',    desc:'Direction d\'exécution — suivi chantier',             required:false, checked:true},
    {id:'erp',   label:'ERP',    desc:'Dossier ERP — sécurité incendie, accessibilité',     required:false, checked:true},
    {id:'opr',   label:'OPR',    desc:'Réception des travaux — levée des réserves',          required:false, checked:true},
  ],
  tertiaire: [
    {id:'esq',   label:'ESQ',    desc:'Esquisse — premières intentions spatiales',          required:true,  checked:true},
    {id:'apd',   label:'APD',    desc:'Avant-Projet Définitif — plans cotés validés',        required:true,  checked:true},
    {id:'dce',   label:'DCE',    desc:'Consultation entreprises — CCTP, devis, OS',          required:false, checked:true},
    {id:'det',   label:'DET',    desc:'Direction d\'exécution — suivi chantier',             required:false, checked:true},
    {id:'opr',   label:'OPR',    desc:'Réception des travaux',                               required:false, checked:true},
  ],
  sourcing: [
    {id:'sel',   label:'Sélection',   desc:'Sourcing mobilier — catalogue des 157 marques', required:true,  checked:true},
    {id:'prop',  label:'Proposition', desc:'Proposition commerciale client — PDF automatique', required:true, checked:true},
    {id:'cmd',   label:'Commande',    desc:'Bon de commande après validation client',         required:true,  checked:true},
    {id:'liv',   label:'Livraison',   desc:'Suivi des livraisons et SAV',                    required:false, checked:true},
  ],
};

function renderPhases(key){
  var phases = GABARITS[key] || GABARITS['residentiel'];
  var container = document.getElementById('phases-selector');
  container.innerHTML = '';
  phases.forEach(function(p){
    var row = document.createElement('div');
    row.style.cssText = 'display:flex;align-items:flex-start;gap:12px;padding:10px 14px;background:var(--white);border:0.5px solid var(--cream-border);border-radius:8px;cursor:'+(p.required?'default':'pointer')+';transition:background .1s;';
    row.id = 'phase-row-'+p.id;
    if(!p.required) row.onclick = function(){ togglePhase(p.id); };

    var checkWrap = document.createElement('div');
    checkWrap.style.cssText = 'width:18px;height:18px;border-radius:4px;border:1.5px solid var(--cream-border);background:var(--white);display:flex;align-items:center;justify-content:center;flex-shrink:0;margin-top:1px;transition:background .15s,border-color .15s;';
    checkWrap.id = 'check-'+p.id;
    if(p.checked){
      checkWrap.style.background = 'var(--green-700)';
      checkWrap.style.borderColor = 'var(--green-700)';
      checkWrap.innerHTML = '<svg width="10" height="8" viewBox="0 0 10 8" fill="none"><path d="M1 4l3 3 5-6" stroke="white" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>';
    }

    var info = document.createElement('div');
    info.style.cssText = 'flex:1;';

    var badge = document.createElement('span');
    badge.style.cssText = 'font-size:12px;font-weight:500;color:var(--gray-800);margin-right:8px;';
    badge.textContent = p.label;

    var req = '';
    if(p.required){
      req = document.createElement('span');
      req.style.cssText = 'font-size:10px;background:var(--cream);color:var(--gray-400);border:0.5px solid var(--cream-border);padding:1px 6px;border-radius:10px;margin-right:6px;';
      req.textContent = 'Obligatoire';
    }

    var desc = document.createElement('div');
    desc.style.cssText = 'font-size:11px;color:var(--gray-400);margin-top:2px;';
    desc.textContent = p.desc;

    var labelLine = document.createElement('div');
    labelLine.style.cssText = 'display:flex;align-items:center;flex-wrap:wrap;gap:4px;';
    labelLine.appendChild(badge);
    if(req) labelLine.appendChild(req);

    info.appendChild(labelLine);
    info.appendChild(desc);
    row.appendChild(checkWrap);
    row.appendChild(info);

    // state tracking
    row._checked = p.checked;
    row._required = p.required;
    row._id = p.id;
    row._label = p.label;

    container.appendChild(row);
  });
  updatePreview();
}

function togglePhase(id){
  var row = document.getElementById('phase-row-'+id);
  var check = document.getElementById('check-'+id);
  if(!row || row._required) return;
  row._checked = !row._checked;
  if(row._checked){
    check.style.background = 'var(--green-700)';
    check.style.borderColor = 'var(--green-700)';
    check.innerHTML = '<svg width="10" height="8" viewBox="0 0 10 8" fill="none"><path d="M1 4l3 3 5-6" stroke="white" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>';
    row.style.background = 'var(--white)';
  } else {
    check.style.background = 'var(--white)';
    check.style.borderColor = 'var(--cream-border)';
    check.innerHTML = '';
    row.style.background = '#FDFCFA';
  }
  updatePreview();
}

function updatePreview(){
  var rows = document.querySelectorAll('#phases-selector > div');
  var active = [];
  rows.forEach(function(r){ if(r._checked) active.push(r._label); });
  document.getElementById('phases-preview').textContent = active.join(' → ') || '—';
}

function createProject(){
  var name=document.getElementById('input-name').value;
  if(!name){document.getElementById('input-name').focus();return;}
  var preview = document.getElementById('phases-preview').textContent;
  closeModal();
  goToProject();
  showToast('Projet "'+name+'" créé · ' + preview);
}

// Init phases on load
renderPhases('residentiel');

// ── FILTER ──
var currentFilter='all';
function setFilter(f,btn){
  currentFilter=f;
  document.querySelectorAll('.filter-btn').forEach(function(b){b.classList.remove('active');});
  btn.classList.add('active');
  filterProjects(document.querySelector('.search-input').value);
}
function filterProjects(q){
  document.querySelectorAll('.project-card[data-phase]').forEach(function(c){
    var nameMatch=c.innerText.toLowerCase().indexOf(q.toLowerCase())>-1||q==='';
    var phaseMatch=currentFilter==='all'||c.dataset.phase===currentFilter;
    c.style.display=(nameMatch&&phaseMatch)?'':'none';
  });
}

// ── TOAST ──
var toastTimer;
function showToast(msg){
  var t=document.getElementById('toast');
  t.textContent=msg;
  t.classList.add('show');
  clearTimeout(toastTimer);
  toastTimer=setTimeout(function(){t.classList.remove('show');},2800);
}
</script>
</body>
</html>
