# eliiforainumber1.github.io
[Dice Roller V11.html](https://github.com/user-attachments/files/32536471/Dice.Roller.V11.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Roll Tracker</title>
<style>
  :root{
    --bg:#e9e4d4;
    --bg-card:#f5f1e5;
    --ink:#2c2a20;
    --ink-soft:#66624f;
    --moss:#4b6142;
    --moss-dark:#354730;
    --ochre:#a56f2b;
    --berry:#7c3030;
    --border:#c9c1a4;
    --border-soft:#dcd5bd;
  }
  @media (prefers-color-scheme: dark){
    :root{
      --bg:#1d2019;
      --bg-card:#262a20;
      --ink:#e9e4d4;
      --ink-soft:#a9a58f;
      --moss:#7fa06f;
      --moss-dark:#5c7a4f;
      --ochre:#c99457;
      --berry:#d17a7a;
      --border:#3a3f30;
      --border-soft:#2e321f;
    }
  }
  *{box-sizing:border-box;}
  body{
    margin:0;
    background:var(--bg);
    color:var(--ink);
    font-family:Georgia,"Iowan Old Style","Palatino Linotype",serif;
    padding:28px 16px 60px;
  }
  .wrap{max-width:920px;margin:0 auto;}
  header{
    display:flex;
    flex-wrap:wrap;
    align-items:baseline;
    justify-content:space-between;
    gap:12px;
    border-bottom:2px solid var(--border);
    padding-bottom:14px;
    margin-bottom:22px;
  }
  h1{
    font-size:1.7rem;
    margin:0;
    font-weight:600;
    letter-spacing:0.01em;
  }
  header p{
    margin:2px 0 0;
    color:var(--ink-soft);
    font-size:0.85rem;
    font-family:-apple-system,"Segoe UI",sans-serif;
  }
  .quickroll{display:flex;gap:6px;flex-wrap:wrap;}
  .die-btn{
    font-family:-apple-system,"Segoe UI",sans-serif;
    font-size:0.85rem;
    padding:7px 11px;
    background:var(--bg-card);
    border:1px solid var(--border);
    border-radius:5px;
    color:var(--ink);
    cursor:pointer;
  }
  .die-btn:hover{border-color:var(--moss);}
  .dice-count{
    width:48px;padding:7px 6px;border:1px solid var(--border);border-radius:5px;
    background:var(--bg-card);color:var(--ink);font-size:0.85rem;
    font-family:-apple-system,"Segoe UI",sans-serif;text-align:center;
  }
  .dice-count-x{
    font-family:-apple-system,"Segoe UI",sans-serif;
    color:var(--ink-soft);font-size:0.85rem;align-self:center;
  }
  .settings-bar{
    display:flex;
    flex-wrap:wrap;
    gap:20px;
    align-items:center;
    background:var(--bg-card);
    border:1px solid var(--border-soft);
    border-radius:8px;
    padding:12px 16px;
    margin-bottom:22px;
    font-family:-apple-system,"Segoe UI",sans-serif;
    font-size:0.88rem;
  }
  .settings-bar label{display:flex;align-items:center;gap:6px;color:var(--ink-soft);}
  .settings-bar input[type=number]{
    width:52px;padding:5px 6px;border:1px solid var(--border);border-radius:4px;
    background:var(--bg);color:var(--ink);font-size:0.9rem;
  }
  .mode-group{display:flex;gap:2px;background:var(--bg);border:1px solid var(--border);border-radius:6px;padding:2px;}
  .mode-group button{
    font-family:-apple-system,"Segoe UI",sans-serif;
    font-size:0.8rem;padding:5px 10px;border:none;background:transparent;color:var(--ink-soft);
    border-radius:4px;cursor:pointer;
  }
  .mode-group button.active{background:var(--moss);color:#fff;}
  .grid{display:grid;grid-template-columns:1.1fr 1fr;gap:20px;align-items:start;}
  @media (max-width:760px){.grid{grid-template-columns:1fr;}}
  section.panel{
    background:var(--bg-card);
    border:1px solid var(--border-soft);
    border-radius:10px;
    padding:16px 18px 20px;
  }
  section.panel h2{
    font-size:1.05rem;margin:0 0 12px;font-weight:600;
    border-bottom:1px solid var(--border-soft);padding-bottom:8px;
  }
  .ability-row{
    display:grid;
    grid-template-columns:44px 60px 1fr auto auto;
    align-items:center;
    gap:8px;
    padding:7px 0;
    border-bottom:1px solid var(--border-soft);
    font-family:-apple-system,"Segoe UI",sans-serif;
  }
  .ability-row:last-child{border-bottom:none;}
  .ability-group{margin-bottom:2px;}
  .skills-wrap{margin-bottom:6px;}
  .skill-row{
    display:flex;align-items:center;gap:8px;flex-wrap:wrap;
    padding:5px 0 5px 20px;
    margin-left:8px;
    border-left:2px solid var(--border-soft);
    border-bottom:1px solid var(--border-soft);
    font-family:-apple-system,"Segoe UI",sans-serif;
  }
  .skill-row:last-child{border-bottom:none;}
  .skill-row .skill-name{flex:1 1 100px;font-size:0.8rem;color:var(--ink-soft);}
  .skill-row label.prof{display:flex;align-items:center;gap:4px;font-size:0.72rem;color:var(--ink-soft);}
  .skill-row .roll-btn{font-size:0.72rem;padding:4px 8px;}
  .ability-name{font-weight:700;font-size:0.85rem;letter-spacing:0.02em;color:var(--ink);}
  .ability-row input[type=number]{
    width:52px;padding:5px 6px;border:1px solid var(--border);border-radius:4px;
    background:var(--bg);color:var(--ink);font-size:0.85rem;
  }
  .ability-row label.prof{
    display:flex;align-items:center;gap:4px;font-size:0.75rem;color:var(--ink-soft);
  }
  .roll-btn{
    font-family:-apple-system,"Segoe UI",sans-serif;
    font-size:0.78rem;padding:6px 9px;border-radius:5px;border:1px solid var(--moss);
    background:transparent;color:var(--moss-dark);cursor:pointer;white-space:nowrap;
  }
  .roll-btn:hover{background:var(--moss);color:#fff;}
  .roll-btn.save{border-color:var(--ochre);color:var(--ochre);}
  .roll-btn.save:hover{background:var(--ochre);color:#fff;}
  .attack{
    border:1px solid var(--border-soft);border-radius:8px;padding:10px 12px;margin-bottom:10px;
    font-family:-apple-system,"Segoe UI",sans-serif;
  }
  .attack-top{display:flex;gap:8px;align-items:center;margin-bottom:8px;}
  .attack-top input[type=text]{
    flex:1;padding:6px 8px;border:1px solid var(--border);border-radius:4px;
    background:var(--bg);color:var(--ink);font-size:0.88rem;font-weight:600;
  }
  .attack-top button.del{
    background:none;border:none;color:var(--berry);font-size:1rem;cursor:pointer;padding:2px 6px;
  }
  .attack-preset{
    font-family:-apple-system,"Segoe UI",sans-serif;
    padding:6px 7px;border:1px solid var(--border);border-radius:4px;
    background:var(--bg);color:var(--ink);font-size:0.8rem;
  }
  .attack-note{
    font-family:-apple-system,"Segoe UI",sans-serif;
    font-size:0.75rem;font-style:italic;color:var(--ink-soft);margin:-4px 0 8px;
  }
  .roll-btn[disabled]{
    opacity:0.45;cursor:not-allowed;
  }
  .roll-btn[disabled]:hover{background:transparent;color:var(--moss-dark);}
  .attack-fields{display:flex;flex-wrap:wrap;gap:8px;align-items:center;font-size:0.8rem;color:var(--ink-soft);}
  .attack-fields input{
    padding:5px 6px;border:1px solid var(--border);border-radius:4px;
    background:var(--bg);color:var(--ink);font-size:0.82rem;
  }
  .attack-fields input[type=number]{width:48px;}
  .attack-fields input.atk-bonus{width:48px;text-align:center;}
  .attack-fields input:disabled{
    opacity:0.6;
    color:var(--ink-soft);
    border-style:dashed;
    background-image:repeating-linear-gradient(45deg, var(--border-soft), var(--border-soft) 4px, var(--bg-card) 4px, var(--bg-card) 8px);
    cursor:not-allowed;
  }
  .attack-fields input.auto-value{
    background:var(--bg-card);
    border-color:var(--moss);
    color:var(--moss-dark);
    font-weight:700;
    cursor:default;
  }
  .attack-fields label.disabled-field{opacity:0.55;}
  .attack-fields input[type=text].dice{width:64px;}
  .attack-fields label{display:flex;align-items:center;gap:4px;}
  #add-attack{
    font-family:-apple-system,"Segoe UI",sans-serif;
    width:100%;padding:9px;border:1px dashed var(--border);border-radius:6px;
    background:transparent;color:var(--ink-soft);cursor:pointer;font-size:0.85rem;margin-top:4px;
  }
  #add-attack:hover{border-color:var(--moss);color:var(--moss-dark);}
  .prof-panel{margin-top:22px;}
  .prof-list{display:flex;flex-direction:column;}
  .prof-row{
    display:flex;align-items:center;gap:8px;padding:6px 0;
    border-bottom:1px solid var(--border-soft);
    font-family:-apple-system,"Segoe UI",sans-serif;
  }
  .prof-row:last-child{border-bottom:none;}
  .prof-row input[type=text]{
    flex:1;padding:6px 8px;border:1px solid var(--border);border-radius:4px;
    background:var(--bg);color:var(--ink);font-size:0.88rem;
  }
  .prof-row button.del{
    background:none;border:none;color:var(--berry);font-size:1rem;cursor:pointer;padding:2px 6px;
  }
  #add-prof{
    font-family:-apple-system,"Segoe UI",sans-serif;
    width:100%;padding:9px;border:1px dashed var(--border);border-radius:6px;
    background:transparent;color:var(--ink-soft);cursor:pointer;font-size:0.85rem;margin-top:8px;
  }
  #add-prof:hover{border-color:var(--moss);color:var(--moss-dark);}
  #log{
    margin-top:22px;background:var(--bg-card);border:1px solid var(--border-soft);
    border-radius:10px;padding:14px 18px;
  }
  #log h2{font-size:1.05rem;margin:0 0 10px;font-weight:600;}
  #log-list{max-height:260px;overflow-y:auto;display:flex;flex-direction:column-reverse;gap:0;}
  .log-entry{
    display:flex;justify-content:space-between;gap:10px;
    padding:7px 0;border-bottom:1px solid var(--border-soft);
    font-family:-apple-system,"Segoe UI",sans-serif;font-size:0.85rem;
  }
  .log-entry:first-child{border-bottom:none;}
  .log-entry .label{color:var(--ink-soft);}
  .log-entry .total{font-weight:700;}
  .log-entry .total.crit{color:var(--moss);}
  .log-entry .total.fumble{color:var(--berry);}
  .log-empty{color:var(--ink-soft);font-size:0.85rem;font-family:-apple-system,"Segoe UI",sans-serif;}
  #clear-log{
    font-family:-apple-system,"Segoe UI",sans-serif;
    font-size:0.75rem;background:none;border:none;color:var(--ink-soft);
    cursor:pointer;text-decoration:underline;margin-top:8px;
  }
</style>
</head>
<body>
<div class="wrap">

  <header>
    <div>
      <h1>Roll Tracker</h1>
      <p>Ability checks, saving throws, and attacks — works fully offline.</p>
    </div>
    <div class="quickroll" id="quickroll"></div>
  </header>

  <div class="settings-bar">
    <label>Proficiency Bonus
      <input type="number" id="prof-bonus" value="2">
    </label>
    <div class="mode-group" id="mode-group">
      <button data-mode="dis">Disadvantage</button>
      <button data-mode="normal" class="active">Normal</button>
      <button data-mode="adv">Advantage</button>
    </div>
  </div>

  <div class="grid">
    <section class="panel">
      <h2>Ability Checks &amp; Saves</h2>
      <div id="abilities"></div>
    </section>

    <section class="panel">
      <h2>Attacks</h2>
      <div id="attacks"></div>
      <button id="add-attack">+ Add Attack</button>
    </section>
  </div>

  <div id="log">
    <h2>Roll Log</h2>
    <div id="log-list"></div>
    <button id="clear-log">Clear log</button>
  </div>

  <section class="panel prof-panel">
    <h2>Proficiencies</h2>
    <div id="proficiencies" class="prof-list"></div>
    <button id="add-prof">+ Add Proficiency</button>
  </section>

</div>

<script>
(function(){
  "use strict";

  var STORAGE_KEY = "roll-tracker-state-v1";

  var PRESETS = {
    custom: {label:"Custom", name:"New Attack", dice:"1d6", note:"", noAttackRoll:false, ability:null},
    crossbow: {label:"Light Crossbow", name:"Light Crossbow", dice:"1d8", note:"Ranged Weapon Attack — piercing", noAttackRoll:false, ability:"DEX"},
    scimitar: {label:"Scimitar", name:"Scimitar", dice:"1d6", note:"Melee Weapon Attack (Finesse) — slashing", noAttackRoll:false, ability:"finesse"},
    thornwhip: {label:"Thorn Whip", name:"Thorn Whip", dice:"1d6", note:"Melee Spell Attack — piercing, pulls target 10 ft", noAttackRoll:false, ability:"WIS"},
    poisonspray: {label:"Poison Spray", name:"Poison Spray", dice:"1d12", note:"Con Save (no attack roll) — poison", noAttackRoll:true, ability:null},
    dagger: {label:"Dagger", name:"Dagger", dice:"1d4", note:"Melee/Thrown Weapon Attack (Finesse) — piercing", noAttackRoll:false, ability:"finesse"}
  };
  var PRESET_ORDER = ["custom","crossbow","scimitar","thornwhip","poisonspray","dagger"];

  var defaultState = {
    profBonus: 2,
    mode: "normal",
    abilities: [
      {name:"STR", mod:0, save:false},
      {name:"DEX", mod:0, save:false},
      {name:"CON", mod:0, save:false},
      {name:"INT", mod:0, save:false},
      {name:"WIS", mod:0, save:false},
      {name:"CHA", mod:0, save:false}
    ],
    skills: [
      {name:"Athletics", ability:"STR", prof:false, expertise:false},
      {name:"Acrobatics", ability:"DEX", prof:false, expertise:false},
      {name:"Sleight of Hand", ability:"DEX", prof:false, expertise:false},
      {name:"Stealth", ability:"DEX", prof:false, expertise:false},
      {name:"Arcana", ability:"INT", prof:false, expertise:false},
      {name:"History", ability:"INT", prof:true, expertise:false},
      {name:"Investigation", ability:"INT", prof:false, expertise:false},
      {name:"Nature", ability:"INT", prof:false, expertise:false},
      {name:"Religion", ability:"INT", prof:false, expertise:false},
      {name:"Animal Handling", ability:"WIS", prof:false, expertise:false},
      {name:"Insight", ability:"WIS", prof:false, expertise:false},
      {name:"Medicine", ability:"WIS", prof:false, expertise:false},
      {name:"Perception", ability:"WIS", prof:false, expertise:false},
      {name:"Survival", ability:"WIS", prof:false, expertise:false},
      {name:"Deception", ability:"CHA", prof:false, expertise:false},
      {name:"Intimidation", ability:"CHA", prof:false, expertise:false},
      {name:"Performance", ability:"CHA", prof:false, expertise:false},
      {name:"Persuasion", ability:"CHA", prof:true, expertise:false}
    ],
    attacks: [
      {preset:"scimitar", name:"Scimitar", atk:4, dice:"1d6", dmgBonus:0}
    ],
    proficiencies: [
      "Clubs (Druid)",
      "Daggers (Druid)",
      "Darts (Druid)",
      "Javelins (Druid)",
      "Maces (Druid)",
      "Quarterstaffs (Druid)",
      "Scimitars (Druid)",
      "Sickles (Druid)",
      "Slings (Druid)",
      "Spears (Druid)",
      "Longsword (High Elf — Elf Weapon Training)",
      "Shortsword (High Elf — Elf Weapon Training)",
      "Shortbow (High Elf — Elf Weapon Training)",
      "Longbow (High Elf — Elf Weapon Training)"
    ],
    log: []
  };

  var state = loadState();
  if(!state.proficiencies) state.proficiencies = defaultState.proficiencies.slice();
  if(!state.skills) state.skills = JSON.parse(JSON.stringify(defaultState.skills));
  state.skills.forEach(function(sk){ if(typeof sk.expertise === "undefined") sk.expertise = false; });

  function loadState(){
    try{
      var raw = localStorage.getItem(STORAGE_KEY);
      if(raw){
        var parsed = JSON.parse(raw);
        if(parsed && parsed.abilities && parsed.attacks) return parsed;
      }
    }catch(e){ /* offline/local file storage may be unavailable; fall back to defaults */ }
    return JSON.parse(JSON.stringify(defaultState));
  }

  function saveState(){
    try{
      localStorage.setItem(STORAGE_KEY, JSON.stringify(state));
    }catch(e){ /* ignore — rolling still works without persistence */ }
  }

  function rollDie(sides){
    return Math.floor(Math.random()*sides)+1;
  }

  function rollD20(){
    if(state.mode === "normal"){
      var r = rollDie(20);
      return {value:r, rolls:[r]};
    }
    var a = rollDie(20), b = rollDie(20);
    var value = state.mode === "adv" ? Math.max(a,b) : Math.min(a,b);
    return {value:value, rolls:[a,b]};
  }

  function parseDice(str){
    var m = /^\s*(\d+)\s*d\s*(\d+)\s*$/i.exec(str || "");
    if(!m) return null;
    return {count: parseInt(m[1],10), sides: parseInt(m[2],10)};
  }

  function getAbilityMod(name){
    var found = null;
    for(var i=0;i<state.abilities.length;i++){
      if(state.abilities[i].name === name){ found = state.abilities[i]; break; }
    }
    return found ? (found.mod || 0) : 0;
  }

  function signStr(n){
    return (n >= 0 ? "+" : "") + n;
  }

  // Returns null if this preset's bonus isn't auto-calculated (custom, or no attack roll at all).
  function computeAutoAttackBonus(presetKey){
    var preset = PRESETS[presetKey];
    if(!preset || !preset.ability) return null;
    var mod = preset.ability === "finesse"
      ? Math.max(getAbilityMod("STR"), getAbilityMod("DEX"))
      : getAbilityMod(preset.ability);
    return (state.profBonus || 0) + mod;
  }

  function addLog(label, parts, total, isD20, critOverride){
    var crit = false, fumble = false;
    if(isD20){
      if(critOverride === "crit") crit = true;
      else if(critOverride === "fumble") fumble = true;
    }
    state.log.push({label:label, parts:parts, total:total, crit:crit, fumble:fumble, t:Date.now()});
    if(state.log.length > 60) state.log.shift();
    saveState();
    renderLog();
  }

  function renderLog(){
    var list = document.getElementById("log-list");
    list.innerHTML = "";
    if(state.log.length === 0){
      list.innerHTML = '<div class="log-empty">No rolls yet.</div>';
      return;
    }
    state.log.forEach(function(entry){
      var row = document.createElement("div");
      row.className = "log-entry";
      var totalClass = "total" + (entry.crit ? " crit" : entry.fumble ? " fumble" : "");
      row.innerHTML =
        '<span class="label">' + escapeHtml(entry.label) + ' — ' + escapeHtml(entry.parts) + '</span>' +
        '<span class="' + totalClass + '">' + entry.total + (entry.crit ? " ★" : entry.fumble ? " ✕" : "") + '</span>';
      list.appendChild(row);
    });
  }

  function escapeHtml(s){
    return String(s).replace(/[&<>"']/g, function(c){
      return {"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c];
    });
  }

  // ---------- Quick roll (raw dice, with optional bulk count) ----------
  var diceSizes = [4,6,8,10,12,20,100];
  var qr = document.getElementById("quickroll");

  var countInput = document.createElement("input");
  countInput.type = "number";
  countInput.className = "dice-count";
  countInput.min = "1";
  countInput.value = "1";
  countInput.title = "Number of dice to roll at once — e.g. set to 8 and click d6 for Fireball's 8d6.";
  qr.appendChild(countInput);

  var xLabel = document.createElement("span");
  xLabel.className = "dice-count-x";
  xLabel.textContent = "×";
  qr.appendChild(xLabel);

  diceSizes.forEach(function(sides){
    var btn = document.createElement("button");
    btn.className = "die-btn";
    btn.textContent = "d" + sides;
    btn.addEventListener("click", function(){
      var count = Math.max(1, parseInt(countInput.value,10) || 1);
      var rolls = [];
      for(var i=0;i<count;i++) rolls.push(rollDie(sides));
      var sum = rolls.reduce(function(a,b){return a+b;},0);
      var label = count > 1 ? (count + "d" + sides) : ("d" + sides);
      var partsStr = count > 1 ? ("rolled [" + rolls.join(",") + "]") : ("rolled " + rolls[0]);
      var singleD20 = (sides === 20 && count === 1);
      addLog(label, partsStr, sum, singleD20, singleD20 ? (rolls[0]===20?"crit":rolls[0]===1?"fumble":null) : null);
    });
    qr.appendChild(btn);
  });

  // ---------- Settings ----------
  var profInput = document.getElementById("prof-bonus");
  profInput.value = state.profBonus;
  profInput.addEventListener("input", function(){
    state.profBonus = parseInt(profInput.value,10) || 0;
    saveState();
    renderAttacks();
  });

  var modeGroup = document.getElementById("mode-group");
  Array.prototype.forEach.call(modeGroup.querySelectorAll("button"), function(btn){
    if(btn.getAttribute("data-mode") === state.mode) setActiveMode(btn);
    btn.addEventListener("click", function(){
      state.mode = btn.getAttribute("data-mode");
      saveState();
      Array.prototype.forEach.call(modeGroup.querySelectorAll("button"), function(b){b.classList.remove("active");});
      setActiveMode(btn);
    });
  });
  function setActiveMode(btn){btn.classList.add("active");}

  // ---------- Abilities ----------
  var abilitiesEl = document.getElementById("abilities");

  function renderAbilities(){
    abilitiesEl.innerHTML = "";
    state.abilities.forEach(function(ab, idx){
      var group = document.createElement("div");
      group.className = "ability-group";

      var row = document.createElement("div");
      row.className = "ability-row";

      var name = document.createElement("div");
      name.className = "ability-name";
      name.textContent = ab.name;

      var modInput = document.createElement("input");
      modInput.type = "number";
      modInput.value = ab.mod;
      modInput.addEventListener("input", function(){
        state.abilities[idx].mod = parseInt(modInput.value,10) || 0;
        saveState();
        renderAttacks();
      });

      var profLabel = document.createElement("label");
      profLabel.className = "prof";
      var profCheck = document.createElement("input");
      profCheck.type = "checkbox";
      profCheck.checked = ab.save;
      profCheck.addEventListener("change", function(){
        state.abilities[idx].save = profCheck.checked;
        saveState();
      });
      profLabel.appendChild(profCheck);
      profLabel.appendChild(document.createTextNode("save prof"));

      var checkBtn = document.createElement("button");
      checkBtn.className = "roll-btn";
      checkBtn.textContent = "Check";
      checkBtn.addEventListener("click", function(){
        var d = rollD20();
        var total = d.value + (state.abilities[idx].mod || 0);
        var partsStr = "d20(" + d.rolls.join("/") + ") + " + (state.abilities[idx].mod||0);
        addLog(ab.name + " Check", partsStr, total, true, d.value===20?"crit":d.value===1?"fumble":null);
      });

      var saveBtn = document.createElement("button");
      saveBtn.className = "roll-btn save";
      saveBtn.textContent = "Save";
      saveBtn.addEventListener("click", function(){
        var d = rollD20();
        var bonus = (state.abilities[idx].mod || 0) + (state.abilities[idx].save ? (state.profBonus||0) : 0);
        var total = d.value + bonus;
        var partsStr = "d20(" + d.rolls.join("/") + ") + " + bonus;
        addLog(ab.name + " Save", partsStr, total, true, d.value===20?"crit":d.value===1?"fumble":null);
      });

      row.appendChild(name);
      row.appendChild(modInput);
      row.appendChild(profLabel);
      row.appendChild(checkBtn);
      row.appendChild(saveBtn);
      group.appendChild(row);

      var relatedSkills = state.skills.filter(function(s){ return s.ability === ab.name; });
      if(relatedSkills.length){
        var skillsWrap = document.createElement("div");
        skillsWrap.className = "skills-wrap";
        relatedSkills.forEach(function(skill){
          var skillIdx = state.skills.indexOf(skill);
          var srow = document.createElement("div");
          srow.className = "skill-row";

          var sName = document.createElement("div");
          sName.className = "skill-name";
          sName.textContent = skill.name;

          var sProfLabel = document.createElement("label");
          sProfLabel.className = "prof";
          var sProfCheck = document.createElement("input");
          sProfCheck.type = "checkbox";
          sProfCheck.checked = skill.prof;
          sProfCheck.addEventListener("change", function(){
            state.skills[skillIdx].prof = sProfCheck.checked;
            if(!sProfCheck.checked && state.skills[skillIdx].expertise){
              state.skills[skillIdx].expertise = false;
              saveState();
              renderAbilities();
              return;
            }
            saveState();
          });
          sProfLabel.appendChild(sProfCheck);
          sProfLabel.appendChild(document.createTextNode("prof"));

          var sExpLabel = document.createElement("label");
          sExpLabel.className = "prof";
          var sExpCheck = document.createElement("input");
          sExpCheck.type = "checkbox";
          sExpCheck.checked = skill.expertise;
          sExpCheck.addEventListener("change", function(){
            state.skills[skillIdx].expertise = sExpCheck.checked;
            if(sExpCheck.checked && !state.skills[skillIdx].prof){
              state.skills[skillIdx].prof = true;
              saveState();
              renderAbilities();
              return;
            }
            saveState();
          });
          sExpLabel.appendChild(sExpCheck);
          sExpLabel.appendChild(document.createTextNode("exp"));

          var sRollBtn = document.createElement("button");
          sRollBtn.className = "roll-btn";
          sRollBtn.textContent = "Roll";
          sRollBtn.addEventListener("click", function(){
            var d = rollD20();
            var sk = state.skills[skillIdx];
            var profPart = sk.prof ? (state.profBonus||0) * (sk.expertise ? 2 : 1) : 0;
            var bonus = (state.abilities[idx].mod || 0) + profPart;
            var total = d.value + bonus;
            var partsStr = "d20(" + d.rolls.join("/") + ") + " + bonus;
            addLog(skill.name, partsStr, total, true, d.value===20?"crit":d.value===1?"fumble":null);
          });

          srow.appendChild(sName);
          srow.appendChild(sProfLabel);
          srow.appendChild(sExpLabel);
          srow.appendChild(sRollBtn);
          skillsWrap.appendChild(srow);
        });
        group.appendChild(skillsWrap);
      }

      abilitiesEl.appendChild(group);
    });
  }

  // ---------- Attacks ----------
  var attacksEl = document.getElementById("attacks");

  function renderAttacks(){
    attacksEl.innerHTML = "";
    state.attacks.forEach(function(atk, idx){
      var box = document.createElement("div");
      box.className = "attack";

      var presetSelect = document.createElement("select");
      presetSelect.className = "attack-preset";
      PRESET_ORDER.forEach(function(key){
        var opt = document.createElement("option");
        opt.value = key;
        opt.textContent = PRESETS[key].label;
        if((atk.preset || "custom") === key) opt.selected = true;
        presetSelect.appendChild(opt);
      });
      presetSelect.addEventListener("change", function(){
        var key = presetSelect.value;
        var preset = PRESETS[key];
        state.attacks[idx].preset = key;
        if(key !== "custom"){
          state.attacks[idx].name = preset.name;
          state.attacks[idx].dice = preset.dice;
        }
        saveState();
        renderAttacks();
      });

      var top = document.createElement("div");
      top.className = "attack-top";
      var nameInput = document.createElement("input");
      nameInput.type = "text";
      nameInput.value = atk.name;
      nameInput.addEventListener("input", function(){
        state.attacks[idx].name = nameInput.value;
        saveState();
      });
      var delBtn = document.createElement("button");
      delBtn.className = "del";
      delBtn.textContent = "✕";
      delBtn.title = "Remove attack";
      delBtn.addEventListener("click", function(){
        state.attacks.splice(idx,1);
        saveState();
        renderAttacks();
      });
      top.appendChild(presetSelect);
      top.appendChild(nameInput);
      top.appendChild(delBtn);

      var currentPreset = PRESETS[atk.preset || "custom"];
      if(currentPreset && currentPreset.note){
        var noteEl = document.createElement("div");
        noteEl.className = "attack-note";
        noteEl.textContent = currentPreset.note;
        box.appendChild(top);
        box.appendChild(noteEl);
      } else {
        box.appendChild(top);
      }

      var fields = document.createElement("div");
      fields.className = "attack-fields";

      var atkLabel = document.createElement("label");
      var noAttackRollField = currentPreset && currentPreset.noAttackRoll;
      var autoBonus = computeAutoAttackBonus(atk.preset || "custom");
      var isAuto = autoBonus !== null && !noAttackRollField;

      atkLabel.textContent = "Atk bonus" + (isAuto ? " (auto)" : "");

      var atkInput = document.createElement("input");
      atkInput.type = "text";
      atkInput.className = "atk-bonus" + (isAuto ? " auto-value" : "");

      if(noAttackRollField){
        atkInput.value = "N/A";
        atkInput.disabled = true;
        atkInput.title = "This uses a saving throw, not an attack roll — there's no attack bonus to add.";
      } else if(isAuto){
        atkInput.value = signStr(autoBonus);
        atkInput.readOnly = true;
        var abilityUsed = currentPreset.ability === "finesse"
          ? (getAbilityMod("STR") >= getAbilityMod("DEX") ? "STR" : "DEX") + " (Finesse: best of STR/DEX)"
          : currentPreset.ability;
        atkInput.title = "Auto-calculated: Proficiency (" + signStr(state.profBonus||0) + ") + " + abilityUsed + " modifier. Switch to Custom to enter this manually.";
      } else {
        atkInput.value = String(atk.atk);
      }

      if(noAttackRollField) atkLabel.classList.add("disabled-field");
      atkInput.addEventListener("input", function(){
        if(atkInput.readOnly || atkInput.disabled) return;
        state.attacks[idx].atk = parseInt(atkInput.value,10) || 0;
        saveState();
      });
      atkLabel.appendChild(atkInput);

      var diceLabel = document.createElement("label");
      diceLabel.textContent = "Damage";
      var diceInput = document.createElement("input");
      diceInput.type = "text";
      diceInput.className = "dice";
      diceInput.value = atk.dice;
      diceInput.placeholder = "1d6";
      diceInput.addEventListener("input", function(){
        state.attacks[idx].dice = diceInput.value;
        saveState();
      });
      diceLabel.appendChild(diceInput);

      var dmgBonusLabel = document.createElement("label");
      dmgBonusLabel.textContent = "+";
      var dmgBonusInput = document.createElement("input");
      dmgBonusInput.type = "number";
      dmgBonusInput.value = atk.dmgBonus;
      dmgBonusInput.addEventListener("input", function(){
        state.attacks[idx].dmgBonus = parseInt(dmgBonusInput.value,10) || 0;
        saveState();
      });
      dmgBonusLabel.appendChild(dmgBonusInput);

      var atkBtn = document.createElement("button");
      atkBtn.className = "roll-btn";
      var noAttackRoll = currentPreset && currentPreset.noAttackRoll;
      atkBtn.textContent = noAttackRoll ? "No attack roll" : "Attack Roll";
      if(noAttackRoll){
        atkBtn.disabled = true;
        atkBtn.title = "This uses a saving throw, not an attack roll — the target rolls, not you.";
      }
      atkBtn.addEventListener("click", function(){
        if(noAttackRoll) return;
        var d = rollD20();
        var liveBonus = isAuto ? computeAutoAttackBonus(state.attacks[idx].preset || "custom") : (state.attacks[idx].atk || 0);
        var total = d.value + liveBonus;
        var partsStr = "d20(" + d.rolls.join("/") + ") + " + liveBonus;
        addLog(state.attacks[idx].name + " Attack", partsStr, total, true, d.value===20?"crit":d.value===1?"fumble":null);
      });

      var dmgBtn = document.createElement("button");
      dmgBtn.className = "roll-btn save";
      dmgBtn.textContent = "Damage";
      dmgBtn.addEventListener("click", function(){
        var parsed = parseDice(state.attacks[idx].dice);
        if(!parsed){
          addLog(state.attacks[idx].name + " Damage", "invalid dice — use format like 1d6", 0, false, null);
          return;
        }
        var rolls = [];
        for(var i=0;i<parsed.count;i++) rolls.push(rollDie(parsed.sides));
        var sum = rolls.reduce(function(a,b){return a+b;},0);
        var total = sum + (state.attacks[idx].dmgBonus || 0);
        var partsStr = parsed.count+"d"+parsed.sides+"(" + rolls.join(",") + ") + " + (state.attacks[idx].dmgBonus||0);
        addLog(state.attacks[idx].name + " Damage", partsStr, total, false, null);
      });

      fields.appendChild(atkLabel);
      fields.appendChild(diceLabel);
      fields.appendChild(dmgBonusLabel);
      fields.appendChild(atkBtn);
      fields.appendChild(dmgBtn);

      box.appendChild(fields);
      attacksEl.appendChild(box);
    });
  }

  document.getElementById("add-attack").addEventListener("click", function(){
    state.attacks.push({preset:"custom", name:"New Attack", atk:0, dice:"1d6", dmgBonus:0});
    saveState();
    renderAttacks();
  });

  document.getElementById("clear-log").addEventListener("click", function(){
    state.log = [];
    saveState();
    renderLog();
  });

  // ---------- Proficiencies ----------
  var profListEl = document.getElementById("proficiencies");

  function renderProficiencies(){
    profListEl.innerHTML = "";
    state.proficiencies.forEach(function(text, idx){
      var row = document.createElement("div");
      row.className = "prof-row";

      var input = document.createElement("input");
      input.type = "text";
      input.value = text;
      input.addEventListener("input", function(){
        state.proficiencies[idx] = input.value;
        saveState();
      });

      var delBtn = document.createElement("button");
      delBtn.className = "del";
      delBtn.textContent = "✕";
      delBtn.title = "Remove proficiency";
      delBtn.addEventListener("click", function(){
        state.proficiencies.splice(idx,1);
        saveState();
        renderProficiencies();
      });

      row.appendChild(input);
      row.appendChild(delBtn);
      profListEl.appendChild(row);
    });
  }

  document.getElementById("add-prof").addEventListener("click", function(){
    state.proficiencies.push("");
    saveState();
    renderProficiencies();
    var inputs = profListEl.querySelectorAll("input[type=text]");
    if(inputs.length) inputs[inputs.length-1].focus();
  });

  renderAbilities();
  renderAttacks();
  renderLog();
  renderProficiencies();
})();
</script>
</body>
</html>
