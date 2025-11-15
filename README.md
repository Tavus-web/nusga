<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Wedding Invitation</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=Inter:wght@300;400;600&display=swap" rel="stylesheet">
<style>
  :root{
    --bg1: #fff0f6;
    --bg2: #fff7fb;
    --accent: #ff6fa6;
    --accent-2: #ffd7ec;
    --text: #3b2a2a;
    --muted: #7a5b5b;
  }
  *{box-sizing:border-box}
  body{
    margin:0;
    font-family: "Inter", system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
    color:var(--text);
    background: linear-gradient(180deg,var(--bg1),var(--bg2));
    -webkit-font-smoothing:antialiased;
    -moz-osx-font-smoothing:grayscale;
    overflow-x:hidden;
  }

  /* Layout */
  .container{
    max-width:980px;
    margin:32px auto;
    padding:28px;
    background:rgba(255,255,255,0.75);
    border-radius:20px;
    box-shadow:0 8px 30px rgba(0,0,0,0.08);
    position:relative;
    overflow:hidden;
  }

  header{
    display:flex;
    gap:20px;
    align-items:center;
    justify-content:space-between;
    flex-wrap:wrap;
  }
  .title{
    font-family:"Playfair Display", serif;
    font-size: clamp(22px, 4vw, 36px);
    letter-spacing:0.6px;
    color:var(--accent);
  }
  .names{
    font-size: clamp(26px, 6vw, 48px);
    font-family:"Playfair Display";
    color:#b30f5e;
    margin:6px 0 0 0;
  }
  .subtitle{color:var(--muted); margin-top:6px; font-size:14px}

  .hero{
    display:grid;
    grid-template-columns: 1fr 360px;
    gap:24px;
    align-items:center;
    margin-top:20px;
  }

  .card{
    padding:20px;
    border-radius:14px;
    background: linear-gradient(180deg, rgba(255,255,255,0.9), rgba(255,255,255,0.8));
    box-shadow: 0 6px 18px rgba(203,84,139,0.08);
    backdrop-filter: blur(4px);
  }

  .details h3{
    margin:0 0 10px 0;
    font-family:"Playfair Display";
    color:#9f1e6a;
  }
  .details p{margin:6px 0; color:var(--muted)}

  .countdown{
    display:flex;
    gap:10px;
    margin-top:12px;
  }
  .countdown .unit{
    background:linear-gradient(180deg,#fff,#ffeaf6);
    border-radius:10px;
    padding:12px 16px;
    text-align:center;
    min-width:72px;
  }
  .unit .number{font-size:20px; font-weight:700; color:#8a114b}
  .unit .label{font-size:12px; color:var(--muted)}

  .cta{
    display:flex;
    gap:12px;
    margin-top:18px;
    flex-wrap:wrap;
  }
  .btn{
    background:linear-gradient(90deg,var(--accent), #ff8cba);
    color:white;
    border:none;
    padding:12px 18px;
    border-radius:10px;
    cursor:pointer;
    font-weight:600;
    box-shadow:0 6px 18px rgba(255,111,166,0.18);
  }
  .btn.secondary{
    background:transparent;
    border:1px solid rgba(155,75,115,0.12);
    color:var(--text);
  }

  /* Music control */
  .music-toggle{
    display:inline-flex;
    gap:10px;
    align-items:center;
    padding:8px 12px;
    border-radius:999px;
    border:1px solid rgba(155,75,115,0.06);
    background:linear-gradient(180deg,#fff,#fff9fb);
  }

  /* Footer */
  footer{margin-top:20px; text-align:center; color:var(--muted); font-size:13px}

  /* Floating decorations */
  .floating{
    position:absolute;
    pointer-events:none;
    inset:0;
  }
  .heart{
    position:absolute;
    width:56px;
    height:56px;
    transform:translate(-50%,-50%) rotate(15deg);
    opacity:0.14;
    filter:blur(0.2px);
  }

  /* Modal */
  .modal-backdrop{
    position:fixed; inset:0; background:rgba(20,10,20,0.45);
    display:none; align-items:center; justify-content:center; z-index:60;
  }
  .modal{
    width:min(900px,95%);
    height:min(85vh,800px);
    background:white; border-radius:12px; overflow:hidden; box-shadow:0 18px 60px rgba(0,0,0,0.3);
  }
  .modal .modal-header{
    display:flex; justify-content:space-between; align-items:center; padding:12px 16px; border-bottom:1px solid #f3e6ef;
  }
  .modal iframe{width:100%; height:calc(100% - 56px); border:0; display:block;}

  /* animations */
  @keyframes floatA { 0%{ transform: translateY(0) } 50%{ transform: translateY(-18px) } 100%{ transform: translateY(0) } }
  .float-slow{ animation: floatA 6s ease-in-out infinite; }
  .float-slower{ animation: floatA 9s ease-in-out infinite; }
  .fade-in{ animation: fadeIn .9s ease both; }
  @keyframes fadeIn { from{opacity:0; transform:translateY(10px)} to{opacity:1; transform:none} }
  .fade-in {
    opacity: 0;
    transform: translateY(20px);
    animation: fadeInAnim 5s ease forwards;
  }
  
  @keyframes fadeInAnim {
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }
  

  /* responsive */
  @media (max-width:880px){
    .hero { grid-template-columns: 1fr; }
    .floating{ display:none; }
  }

  /* small touches */
  .venue-link{ color:#9c1160; text-decoration:none; font-weight:600 }
  .muted-small{ font-size:13px; color:var(--muted) }

  .photo-frame {
    position: relative;
    width: 300px;
    height: 300px;
    border-radius: 20px;  /* keep your existing rounding */
    overflow: hidden;
    box-shadow: 0 0 20px rgba(255,111,166,0.4);
  }

  .photo-frame img {
    position: absolute;
    width: 100%;
    height: 100%;
    object-fit: cover;
    top: 0;
    left: 0;
    opacity: 0;
    transition: opacity 2s ease-in-out;
  }
  
  .photo-frame img.active {
    opacity: 1;
    z-index: 2;
  }
  /* RSVP Button */
#rsvpBtn.btn {
  background-color: #ff6fa6;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 25px;
  font-size: 1.1rem;
  cursor: pointer;
  transition: background 0.3s ease;
}
#rsvpBtn.btn:hover {
  background-color: #ff4f90;
}

/* Popup container */
.rsvp-popup {
  display: none;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: white;
  padding: 25px 30px;
  border-radius: 20px;
  box-shadow: 0 0 25px rgba(255,111,166,0.4);
  z-index: 1000;
  text-align: center;
  max-width: 320px;
  width: 90%;
  animation: fadeIn 0.4s ease-in-out;
}

/* Form elements */
.rsvp-form input,
.rsvp-form select {
  width: 100%;
  padding: 10px;
  margin: 8px 0 16px;
  border-radius: 10px;
  border: 1px solid #ffb6d3;
  font-size: 1rem;
  outline: none;
}

.rsvp-form input:focus,
.rsvp-form select:focus {
  border-color: #ff6fa6;
  box-shadow: 0 0 5px rgba(255,111,166,0.5);
}

/* Submit button */
.submit-btn {
  background-color: #ff6fa6;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 25px;
  cursor: pointer;
  transition: background 0.3s ease;
}
.submit-btn:hover {
  background-color: #ff4f90;
}

/* Fade animation */
@keyframes fadeIn {
  from { opacity: 0; transform: translate(-50%, -48%); }
  to { opacity: 1; transform: translate(-50%, -50%); }
}

/* Show popup */
.rsvp-popup.show {
  display: block;
}

  
   
</style>
</head>
<body>
<div class="container">
  <!-- CONFIG: Replace these values -->
  <!--
    EDIT HERE:
      coupleNames = "A & B"
      weddingDateISO = "2026-06-15T15:30:00"  (use yyyy-mm-ddThh:mm:ss in local time)
      venueName = "Sunset Gardens"
      venueAddress = "123 Blossom Lane, City"
      mapsURL = "https://maps.google.com/..."  (optional)
      googleFormURL = "https://docs.google.com/forms/d/e/..." (paste your form share URL here)
      musicURL = ""  (link to an MP3 file you host, or leave empty)
      For YouTube audio: you can paste an embed link below manually into the music iframe section if you prefer.
  -->
  <script>
    const coupleNames = "Süleýman we Şajahan";
    const weddingDateISO = "2026-06-15 18:00:00";
    const venueName = "Jennet restorany";
    const venueAddress = "Aşgabat şäheri";
    const mapsURL = "https://yandex.tm/maps/org/168050053290/?ll=58.159278%2C38.059505&z=15.17"; // replace with your google maps link
    const googleFormURL = ""; // paste your Google Form URL here
    const musicURL = "https://ulgamda.com.tm/tracks/turkmenskie-pesni/10232-mad-nazarov-amp-jeren-halnazarowa-seni-belledim.html"; // paste direct mp3 link here (or leave blank)
  </script>

  <header>
    <div>
      <div class="title">Biz toý edýaris!</div>
      <div class="names" id="namesJS">Loading…</div>
      <div class="subtitle" id="dateSubtitle">Save the date</div>
    </div>
    <div style="text-align:right">
      <div class="music-toggle" id="musicToggle" title="Play / pause music">
        <span id="musicIcon">♪</span>
        <small class="muted-small" id="musicLabel">Music: Seni belledim</small>
      </div>
    </div>
  </header>

  <div class="hero" style="margin-top:20px;">
    <div class="card details fade-in">
      <h3>Sizi toýumyzyň gadyrly myhmany bolmaga çagyrýarys</h3>
      <p id="invitationText">Biziň bagt toýuny tutýan günümiziň bir bölegi bolsaňyz dabaramyza şatlyk goşarsyňyz! </p>

      <div style="margin-top:16px;">
        <strong>Güni we wagty</strong>
        <div class="muted-small" id="dateTime">—</div>

        <strong style="margin-top:12px; display:block">Ýeri</strong>
        <div class="muted-small">
          <div id="venueName">—</div>
          <div id="venueAddress">—</div>
          <a id="mapsLink" class="venue-link" href="#" target="_blank">Kartada görkez</a>
        </div>
      </div>

      <div style="margin-top:14px;">
        <strong>Galan wagt</strong>
        <div class="countdown" id="countdown">
          <div class="unit">
            <div class="number" id="days">--</div>
            <div class="label">Gün</div>
          </div>
          <div class="unit">
            <div class="number" id="hours">--</div>
            <div class="label">Sagat</div>
          </div>
          <div class="unit">
            <div class="number" id="minutes">--</div>
            <div class="label">Minut</div>
          </div>
          <div class="unit">
            <div class="number" id="seconds">--</div>
            <div class="label">Sekunt</div>
          </div>
        </div>
      </div>

      <!-- RSVP Button -->
<button id="rsvpBtn" class="btn">💌 Myhmanyň anketasy</button>

<!-- RSVP Popup -->
<div id="rsvpPopup" class="rsvp-popup">
  <form id="rsvpForm" class="rsvp-form">
    <h3>Maglumatlary girizmegiňizi haýyş edýaris!</h3>

    <label for="guestName">Siziň adyňyz:</label>
    <input type="text" id="guestName" placeholder="Enter your name" required>

    <label for="attendance">Toýa gelip bilersiňizmi?</label>
    <select id="attendance" required>
      <option value="">Saýlaň...</option>
      <option value="yes">Hawa, uly höwes bilen bararyn 💕</option>
      <option value="no">Gynansakda, baryp bilmerin. Bagtly boluň! </option>
    </select>

    <button type="submit" class="submit-btn">Ugrat</button>
  </form>
</div>


      <div style="margin-top:12px; color:var(--muted); font-size:13px;">
        <strong>Lybas:</strong> Ýaşyl, gülgüne, gök we ş.m. reňklerde — esasy siziň ýylgyrşyňyz ✨
      </div>
    </div>

    <div class="card fade-in" style="display:flex;flex-direction:column;align-items:center;justify-content:center;min-height:260px;">
      <div style="text-align:center">
        <div class="photo-frame">
  <img src="couple_photo1.jpg" alt="Photo 1" class="active">
  <img src="couple_photo2.jpg" alt="Photo 2">
  <img src="couple_photo3.jpg" alt="Photo 3">
</div>
    </div>
      <div style="text-align:center; margin-top:14px;">
        <div style="font-weight:700; font-family:'Playfair Display'; font-size:20px;" id="sideNames">Mähribanlar</div>
        <div style="color:var(--muted); margin-top:6px; font-size:14px;">Size sabyrsyzlyk bilen garaşýarys</div>
      </div>
    </div>
  </div>

  <footer>
    <div class="muted-small">Jogabyňyzy ugratmak üçin "Myhmanyň anketasy" düwmä basyň</div>
  </footer>

  <!-- Floating decorations -->
  <div class="floating" aria-hidden="true">
    <svg class="heart float-slow" style="left:12%; top:20%; width:88px; opacity:0.12" viewBox="0 0 24 24" fill="none"><path d="M12 21s-8-5.3-8-10a5 5 0 0 1 9.9-1A5 5 0 0 1 20 11c0 4.7-8 10-8 10z" fill="#ff6fa6"/></svg>
    <svg class="heart float-slower" style="left:88%; top:10%; width:64px; opacity:0.12" viewBox="0 0 24 24" fill="none"><path d="M12 21s-8-5.3-8-10a5 5 0 0 1 9.9-1A5 5 0 0 1 20 11c0 4.7-8 10-8 10z" fill="#ff9ccf"/></svg>
    <svg class="heart" style="left:72%; top:74%; width:48px; opacity:0.08" viewBox="0 0 24 24" fill="none"><path d="M12 21s-8-5.3-8-10a5 5 0 0 1 9.9-1A5 5 0 0 1 20 11c0 4.7-8 10-8 10z" fill="#ffd7ec"/></svg>
  </div>

</div>

<!-- RSVP Modal (Google Form iframe) -->
<div class="modal-backdrop" id="modalBackdrop" role="dialog" aria-hidden="true">
  <div class="modal" role="document">
    <div class="modal-header">
      <div style="font-weight:700; color:#9c1160">RSVP</div>
      <button id="closeModal" class="btn secondary" style="height:36px; padding:6px 12px;">Close</button>
    </div>
    <!-- The iframe src will be set dynamically from googleFormURL variable -->
    <iframe id="rsvpIframe" src=""></iframe>
  </div>
</div>

<!-- Hidden audio element (user should set musicURL to a hosted mp3 file) -->
<audio id="bgAudio" loop src="https://ulgamda.com.tm/tracks/turkmenskie-pesni/10232-mad-nazarov-amp-jeren-halnazarowa-seni-belledim."></audio>


<script>
  // Populate content from config
  (function(){
    const namesEl = document.getElementById('namesJS');
    const sideNamesEl = document.getElementById('sideNames');
    const dateTimeEl = document.getElementById('dateTime');
    const dateSubtitleEl = document.getElementById('dateSubtitle');
    const venueNameEl = document.getElementById('venueName');
    const venueAddressEl = document.getElementById('venueAddress');
    const mapsLinkEl = document.getElementById('mapsLink');
    const invitationTextEl = document.getElementById('invitationText');
    const rsvpBtn = document.getElementById('rsvpBtn');
    const directionBtn = document.getElementById('directionBtn');
    const shareBtn = document.getElementById('shareBtn');
    const modal = document.getElementById('modalBackdrop');
    const iframe = document.getElementById('rsvpIframe');
    const closeModal = document.getElementById('closeModal');
    const audio = document.getElementById('bgAudio');
    const musicToggle = document.getElementById('musicToggle');
    const musicLabel = document.getElementById('musicLabel');
    const musicIcon = document.getElementById('musicIcon');

    // Load config variables defined in doc head
    // (If you edit values in the top script, they will be used)
    try{
      // show names
      namesEl.textContent = coupleNames;
      sideNamesEl.textContent = coupleNames;
      // Turkmen weekday and month names
const turkmenWeekdays = ["Ýekşenbe", "Duşenbe", "Sişenbe", "Çarşenbe", "Penşenbe", "Anna", "Şenbe"];
const turkmenMonths = ["Ýanwar", "Fewral", "Mart", "Aprel", "Maý", "Iýun", "Iýul", "Awgust", "Sentýabr", "Oktýabr", "Noýabr", "Dekabr"];

// Parse wedding date
const weddingDate = new Date(weddingDateISO);

// Get parts
const weekday = turkmenWeekdays[weddingDate.getDay()];
const day = weddingDate.getDate();
const month = turkmenMonths[weddingDate.getMonth()];
const year = weddingDate.getFullYear();
let hours = weddingDate.getHours();
let minutes = weddingDate.getMinutes();
if(minutes < 10) minutes = "0" + minutes;
if(hours < 10) hours = "0" + hours;

// Update elements
dateTimeEl.textContent = `${weekday}, ${day} ${month} ${year}, ${hours}:${minutes}`;
dateSubtitleEl.textContent = `${day} ${month} ${year}`;


      venueNameEl.textContent = venueName;
      venueAddressEl.textContent = venueAddress;
      mapsLinkEl.href = mapsURL || "#";
      directionBtn.href = mapsURL || "#";

      // RSVP modal
      if (googleFormURL && googleFormURL.trim() !== "") {
        rsvpBtn.addEventListener('click', ()=> {
          iframe.src = googleFormURL;
          modal.style.display = "flex";
        });
      } else {
        rsvpBtn.addEventListener('click', ()=> {
          alert("No Google Form URL set. To enable RSVP, open the HTML file and set the 'googleFormURL' variable near the top.");
        });
      }
      closeModal.addEventListener('click', ()=> {
        modal.style.display = "none";
        iframe.src = "";
      });
      modal.addEventListener('click', (e) => {
        if (e.target === modal) { modal.style.display = "none"; iframe.src = ""; }
      });

      // Share button (uses Web Share API if available)
      shareBtn.addEventListener('click', async ()=> {
        const shareData = {
          title: `Wedding — ${coupleNames}`,
          text: `Join us in celebrating ${coupleNames}!`,
          url: location.href
        };
        try {
          if (navigator.share) {
            await navigator.share(shareData);
          } else {
            // fallback: copy link
            await navigator.clipboard.writeText(location.href);
            alert("Link copied to clipboard. Share it with your guests!");
          }
        } catch (err) {
          alert("Couldn't share — please copy the page URL manually.");
        }
      });

      // Music control: if musicURL provided, set audio src
      if (musicURL && musicURL.trim() !== "") {
        audio.src = musicURL;
        musicToggle.addEventListener('click', ()=> {
          if (audio.paused) {
            audio.play().catch(()=>{ alert("Autoplay blocked — click play on the player controls if needed."); });
            musicIcon.textContent = "♫";
            musicLabel.textContent = "Playing: Seni belledim";
          } else {
            audio.pause();
            musicIcon.textContent = "♪";
            musicLabel.textContent = "Paused";
          }
        });
        // show a tiny control tip
        audio.addEventListener('play', ()=> { musicIcon.textContent="♫"; musicLabel.textContent="Playing: Seni belledim"; });
        audio.addEventListener('pause', ()=> { musicIcon.textContent="♪"; musicLabel.textContent="Paused"; });
      } else {
        // no audio; provide a message that user should add URL
        musicToggle.addEventListener('click', ()=> {
          alert("No music file configured. Edit the HTML: set the 'musicURL' variable to a direct MP3 file URL (hosted on your server).");
        });
        musicLabel.textContent = "Music: (add a URL in the code)";
      }

    } catch (err) {
      console.error(err);
    }

    // Countdown timer
    function updateCountdown(){
      const now = new Date();
      const wedding = new Date(weddingDateISO);
      let diff = Math.max(0, wedding - now);
      const days = Math.floor(diff / (1000*60*60*24));
      diff -= days * (1000*60*60*24);
      const hours = Math.floor(diff / (1000*60*60));
      diff -= hours * (1000*60*60);
      const minutes = Math.floor(diff / (1000*60));
      diff -= minutes * (1000*60);
      const seconds = Math.floor(diff / 1000);

      document.getElementById('days').textContent = String(days).padStart(2,'0');
      document.getElementById('hours').textContent = String(hours).padStart(2,'0');
      document.getElementById('minutes').textContent = String(minutes).padStart(2,'0');
      document.getElementById('seconds').textContent = String(seconds).padStart(2,'0');

      document.getElementById("sideNames").textContent = "Mähribanlar!";

      if (wedding - now <= 0) {
        document.getElementById('countdown').innerHTML = "<div style='font-weight:700; color:#9c1160'>The celebration has begun! 🎉</div>";
      }
    }
    updateCountdown();
    setInterval(updateCountdown, 1000);

  })();
  const photos = document.querySelectorAll('.photo-frame img');
let current = 0;

setInterval(() => {
  photos[current].classList.remove('active');
  current = (current + 1) % photos.length;
  photos[current].classList.add('active');
}, 4000);
const rsvpBtn = document.getElementById('rsvpBtn');
const rsvpPopup = document.getElementById('rsvpPopup');
const rsvpForm = document.getElementById('rsvpForm');

// Show popup
rsvpBtn.addEventListener('click', () => {
  rsvpPopup.classList.add('show');
});

// Handle form submission
rsvpForm.addEventListener('submit', (e) => {
  e.preventDefault();
  const name = document.getElementById('guestName').value;
  const attendance = document.getElementById('attendance').value;

  alert(`💖 Sagboluň, ${name}! Siziň jogabyňyz (${attendance === 'yes' ? 'Bararyn' : 'Baryp bilmerin'}) kabul edildi.`);
  rsvpPopup.classList.remove('show');
  rsvpForm.reset();
});

</script>

</body>
</html>
