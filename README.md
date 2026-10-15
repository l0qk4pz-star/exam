<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<title>奶蛙换装游戏</title>
<style>
  * { margin:0; padding:0; box-sizing:border-box; font-family:-apple-system,"PingFang SC","Microsoft YaHei",sans-serif; }
  html, body { height:100%; overflow:hidden; }
  .page { position:absolute; inset:0; background-size:cover; background-position:center; background-repeat:no-repeat; display:none; flex-direction:column; align-items:center; justify-content:center; }
  .page.active { display:flex; }
  .blur { filter:blur(8px); }
  #home { background-image:url('1.png'); }
  #selection { background-image:url('2.png'); }
  #display { background-color:#fff; }
  .title { font-size:36px; font-weight:bold; color:#fff; text-shadow:2px 2px 8px rgba(0,0,0,0.5),0 0 20px rgba(255,255,0,0.8); margin-bottom:30px; }
  .btn { padding:14px 50px; font-size:22px; font-weight:bold; color:#fff; background:linear-gradient(135deg,#ffb347,#ff7b00); border:none; border-radius:50px; box-shadow:0 6px 0 #b35200; cursor:pointer; }
  .btn:active { transform:translateY(4px); box-shadow:0 0 0 #b35200; }
  .modal { position:absolute; inset:0; background:rgba(0,0,0,0.3); display:none; align-items:center; justify-content:center; z-index:10; }
  .modal.active { display:flex; }
  .modal-box { background:#fff; padding:30px 24px; border-radius:24px; width:80%; max-width:320px; text-align:center; box-shadow:0 10px 30px rgba(0,0,0,0.3); }
  .modal-box h3 { margin-bottom:20px; color:#333; font-size:20px; }
  .modal-box input { width:100%; padding:12px; font-size:18px; border:2px solid #ddd; border-radius:12px; margin-bottom:20px; text-align:center; outline:none; }
  .modal-box .btn { width:100%; padding:12px 0; font-size:18px; }
  .name { position:absolute; top:40px; font-size:26px; font-weight:bold; color:#fff; text-shadow:2px 2px 6px rgba(0,0,0,0.6); background:rgba(0,0,0,0.3); padding:6px 20px; border-radius:20px; }
  .grid { display:grid; grid-template-columns:1fr 1fr; gap:20px; width:80%; max-width:320px; position:absolute; bottom:80px; }
  .clothes { padding:16px 0; font-size:18px; font-weight:bold; color:#fff; border:none; border-radius:16px; box-shadow:0 4px 0 rgba(0,0,0,0.2); cursor:pointer; }
  .clothes:active { transform:translateY(4px); box-shadow:0 0 0 rgba(0,0,0,0.2); }
  .c1 { background:linear-gradient(135deg,#a8e063,#56ab2f); }
  .c2 { background:linear-gradient(135deg,#4facfe,#00f2fe); }
  .c3 { background:linear-gradient(135deg,#f093fb,#f5576c); }
  .c4 { background:linear-gradient(135deg,#ffecd2,#fcb69f); color:#7a3d2e; }
  #outfitImage { width:90%; height:90%; object-fit:contain; }
  .back { position:absolute; top:20px; left:20px; width:44px; height:44px; background:rgba(0,0,0,0.4); border-radius:50%; display:flex; align-items:center; justify-content:center; font-size:24px; color:#fff; cursor:pointer; z-index:20; }
</style>
</head>
<body>

<div id="home" class="page active">
  <div class="title">奶蛙换装游戏</div>
  <button class="btn" id="btnStart">开始</button>
</div>

<div id="modal" class="modal">
  <div class="modal-box">
    <h3>给奶蛙起个名字吧</h3>
    <input type="text" id="nameInput" placeholder="输入名字..." maxlength="10">
    <button class="btn" id="btnConfirm">确定</button>
  </div>
</div>

<div id="selection" class="page">
  <div class="name" id="nameShow"></div>
  <div class="grid">
    <button class="clothes c1" data-img="3.png">吉利服</button>
    <button class="clothes c2" data-img="4.png">校服</button>
    <button class="clothes c3" data-img="5.png">旗袍</button>
    <button class="clothes c4" data-img="6.png">裙子</button>
  </div>
</div>

<div id="display" class="page">
  <div class="back" id="btnBack">←</div>
  <img id="outfitImage" src="" alt="">
</div>

<script>
  var home = document.getElementById('home');
  var modal = document.getElementById('modal');
  var selection = document.getElementById('selection');
  var display = document.getElementById('display');
  var nameShow = document.getElementById('nameShow');
  var outfitImage = document.getElementById('outfitImage');
  var nameInput = document.getElementById('nameInput');

  function hideAll() {
    home.classList.remove('active');
    modal.classList.remove('active');
    selection.classList.remove('active');
    display.classList.remove('active');
  }

  document.getElementById('btnStart').onclick = function() {
    modal.classList.add('active');
    home.classList.add('blur');
  };

  document.getElementById('btnConfirm').onclick = function() {
    var v = nameInput.value.trim();
    if (v === '') { alert('请输入名字哦'); return; }
    nameShow.textContent = v;
    modal.classList.remove('active');
    home.classList.remove('blur');
    hideAll();
    selection.classList.add('active');
  };

  var btns = document.querySelectorAll('.clothes');
  for (var i = 0; i < btns.length; i++) {
    btns[i].onclick = function() {
      outfitImage.src = this.getAttribute('data-img');
      hid
