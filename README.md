<script>
  const home = document.getElementById('home');
  const selection = document.getElementById('selection');
  const display = document.getElementById('display');
  const namingModal = document.getElementById('namingModal');
  const startBtn = document.getElementById('startBtn');
  const nameInput = document.getElementById('nameInput');
  const confirmNameBtn = document.getElementById('confirmNameBtn');
  const displayName = document.getElementById('displayName');
  const outfitImage = document.getElementById('outfitImage');
  const backBtn = document.getElementById('backBtn');

  const outfitImages = {
    guerrilla: '3.png',
    school: '4.png',
    qipao: '5.png',
    dress: '6.png'
  };

  startBtn.addEventListener('click', () => {
    namingModal.classList.remove('hidden');
    home.classList.add('blurred');
  });

  confirmNameBtn.addEventListener('click', () => {
    const inputVal = nameInput.value.trim();
    if (inputVal === '') { alert('请输入名字哦~'); return; }
    displayName.textContent = inputVal;
    namingModal.classList.add('hidden');
    home.classList.remove('blurred');
    home.classList.add('hidden');
    selection.classList.remove('hidden');
  });

  document.querySelectorAll('.clothes-btn').forEach(btn => {
    btn.addEventListener('click', (e) => {
      const outfitKey = e.target.getAttribute('data-outfit');
      outfitImage.src = outfitImages[outfitKey];
      selection.classList.add('hidden');
      display.classList.remove('hidden');
    });
  });

  backBtn.addEventListener('click', () => {
    display.classList.add('hidden');
    selection.classList.remove('hidden');
  });

  window.addEventListener('load', () => {
    home.classList.remove('hidden');
    selection.classList.add('hidden');
    display.classList.add('hidden');
    namingModal.classList.add('hidden');
  });
</script># exam
