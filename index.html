<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Fourier Demo</title>
<style>

  body {
    background: #0d0d14;
    display: flex;
    align-items: center;
    justify-content: center;
    min-height: 100vh;
    font-family: 'DM Sans', sans-serif;
    color: var(--text-primary);
  }

  .card-title {
    font-family: 'Space Mono', monospace;
    font-size: 15px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: #7fefbd;
  }

  .canvas-wrapper {
    position: relative;
    border-radius: 12px;
    overflow: hidden;
    border: 1px solid var(--border);
    background: #0d0d14;
  }

  canvas {
    display: block;
    width: 100%;
  }
  
  
    .subwave-list {
    margin-top: 16px;
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  .subwave-row {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 8px 12px;
    background: rgba(255,255,255,0.02);
    border-radius: 8px;
    border: 1px solid rgba(255,255,255,0.04);
  }
    .subwave-color {
    width: 10px;
    height: 10px;
    border-radius: 50%;
    flex-shrink: 0;
  }

  .subwave-label {
    font-family: 'Space Mono', monospace;
    font-size: 25px;
    color: #ffffff;
    flex: 1;
  }
  
    .param-chips {
    display: flex;
    gap: 6px;
  }

  .chip {
    font-family: 'Space Mono', monospace;
    font-size: 18px;
    padding: 2px 7px;
    border-radius: 4px;
    background: rgba(255,255,255,0.05);
    color: #ffffff;
    border: 1px solid rgba(255,255,255,0.06);
  }

  .chip span {
    color: var(--text-primary);
    opacity: 0.7;
  }

label {
  color: white;
}

</style>
</head>
<body>

<div class="wave-card">
	
  <div class="card-header">
    <div class="card-title">Fourier Composition</div>
  </div>

  <div class="canvas-wrapper">
    <canvas id="waveCanvas" width="1240" height="420"></canvas>
  </div>

  <div class="subwave-list" id="subwaveList"></div>
  
  
  <label>
  <input type="checkbox" id="ampCheck" checked>
  Enable Amplitude
  </label>
  <br>
  <label>
  <input type="checkbox" id="freCheck">
  Enable Frequency
  </label>
  <br>
  <label>
  <input type="checkbox" id="phaCheck">
  Enable Phase
  </label>
  <br>
  <label>
  Number of Waves
  <input type="range" id="diffSlider" min="1" max="4" step="1" value="1">
	<span id="diffCount">1</span>
  </label>
<br>
<button id="rerollBtn">New Wave</button>

</div>



<script>
  
  let difficulty = 1;

  const diffSlider = document.getElementById("diffSlider");
  const diffLabel = document.getElementById("diffCount");

  diffSlider.addEventListener("input", function () {
    difficulty = parseFloat(diffSlider.value);
    diffLabel.textContent = difficulty;
    changeDifficulty();
    draw();
  });

  // Define sub-waves: { amplitude, frequency (Hz), phase (radians), color }
  let subwaves = [
    { amplitude: 0.5, frequency: 2.5,  phase: 0,           color: '#00ff2f',	enabled: 1 },
    { amplitude: 0.5, frequency: 2.5,  phase: 0,   color: '#fff200',	enabled: 0 },
    { amplitude: 0.5, frequency: 2.5,  phase: 0,   color: '#74c0fc',	enabled: 0 },
    { amplitude: 0.5, frequency: 2.5,  phase: 0,   color: '#da77f2',	enabled: 0 },
  ];
  
  let realwaves = [
    { amplitude: randomRounded(0, 1, 0.05), frequency: randomRounded(0.5, 5, 0.1),  phase: Math.PI*randomRounded(0, 2, 0.05),           color: '#ff6b9d',	enabled: 1 },
    { amplitude: randomRounded(0, 1, 0.05), frequency: randomRounded(0.5, 5, 0.1),  phase: Math.PI*randomRounded(0, 2, 0.05),   color: '#ffa94d',	enabled: 0 },
    { amplitude: randomRounded(0, 1, 0.05), frequency: randomRounded(0.5, 5, 0.1),  phase: Math.PI*randomRounded(0, 2, 0.05),   color: '#74c0fc',	enabled: 0 },
    { amplitude: randomRounded(0, 1, 0.05), frequency: randomRounded(0.5, 5, 0.1),  phase: Math.PI*randomRounded(0, 2, 0.05),   color: '#da77f2',	enabled: 0 },
  ];

	// gets the canvas and declares variables
  const canvas = document.getElementById('waveCanvas');
  const ctx = canvas.getContext('2d');
  const W = canvas.width;
  const H = canvas.height;

const list = document.getElementById('subwaveList');

  // Time window: show 2 full periods of the lowest frequency
  const tMin = 0;
  const tMax = 2.0;
  
  function randomRounded(min, max, rnd) {
    let value = Math.random() * (max - min) + min;
    let scalingFactor = 100/(rnd*100)
    return Math.round(value * scalingFactor) / scalingFactor;
	}

	//runs the code for a single wave
  function sampleWave(wave, t) {
    if(wave.enabled) {
    return wave.amplitude * Math.sin(2 * Math.PI * wave.frequency * t + wave.phase);
    } else {
    return 0;
    }
  }

	//creates the composite wave
    //TODO- Update to work with variable waves(currently always runs on subwaves
    	//aka change to accomodate real and user input waves
  function sampleComposite(t) {
    return subwaves.reduce((sum, w) => sum + sampleWave(w, t), 0);
  }
  
  function sampComposite(t) {
    return realwaves.reduce((sum, w) => sum + sampleWave(w, t), 0);
  }

  function draw() {
    ctx.clearRect(0, 0, W, H);

    const padX = 40;
    const padY = 40;
    const plotW = W - 2 * padX;
    const plotH = H - 2 * padY;
    const midY = H / 2;

    // Max possible amplitude for scaling
		//TODO- Update to work off real or input waves
        //or make it not do this shit idk
    const maxAmp = subwaves.reduce((s, w) => s + w.amplitude, 0);
    const scaleY = (plotH / 2) // (maxAmp * 1.1);

    // Grid lines
    ctx.strokeStyle = 'rgba(255,255,255,0.25)';
    ctx.lineWidth = 1;
    for (let i = 1; i <= 3; i++) {
      const y = midY - (plotH / 2) * (i / 4);
      ctx.beginPath(); ctx.moveTo(padX, y); ctx.lineTo(W - padX, y); ctx.stroke();
      const y2 = midY + (plotH / 2) * (i / 4);
      ctx.beginPath(); ctx.moveTo(padX, y2); ctx.lineTo(W - padX, y2); ctx.stroke();
    }
    // Vertical grid
    for (let i = 1; i <= 7; i++) {
      const x = padX + plotW * (i / 8);
      ctx.beginPath(); ctx.moveTo(x, padY); ctx.lineTo(x, H - padY); ctx.stroke();
    }

    // Zero line
    ctx.strokeStyle = 'rgba(255,255,255,0.4)';
    ctx.lineWidth = 1;
    ctx.beginPath(); ctx.moveTo(padX, midY); ctx.lineTo(W - padX, midY); ctx.stroke();

    const N = 1200;

    // Draw sub-waves
    	//TODO- Update to draw fakewaves and realwaves
        //maybe move to separate function?
    subwaves.forEach(wave => {
      if(wave.enabled) {
      ctx.beginPath();
      ctx.strokeStyle = wave.color;
      ctx.lineWidth = 1.5;
      ctx.globalAlpha = 0.45;
      ctx.setLineDash([15, 10]);

      for (let i = 0; i <= N; i++) {
        const t = tMin + (tMax - tMin) * (i / N);
        const y = sampleWave(wave, t);
        const px = padX + plotW * (i / N);
        const py = midY - y * scaleY;
        i === 0 ? ctx.moveTo(px, py) : ctx.lineTo(px, py);
      }
      ctx.stroke();
    }
    });

    ctx.setLineDash([]);
    ctx.globalAlpha = 1;

    // Draw composite wave
    ctx.beginPath();
    ctx.strokeStyle = '#7fefbd';
    ctx.lineWidth = 2.5;
    ctx.shadowColor = '#7fefbd';
    ctx.shadowBlur = 10;

    for (let i = 0; i <= N; i++) {
      const t = tMin + (tMax - tMin) * (i / N);
      const y = sampleComposite(t);
      const px = padX + plotW * (i / N);
      const py = midY - y * scaleY;
      i === 0 ? ctx.moveTo(px, py) : ctx.lineTo(px, py);
    }
    ctx.stroke();
    ctx.shadowBlur = 0;
    
    // Draw real composite wave
    ctx.beginPath();
    ctx.strokeStyle = '#ff0000';
    ctx.lineWidth = 2.5;
    ctx.shadowColor = '#ff0000';
    ctx.shadowBlur = 10;
      ctx.globalAlpha = 0.75;
    
      ctx.setLineDash([20, 3, 3, 3, 3, 3, 3, 3]);

    for (let i = 0; i <= N; i++) {
      const t = tMin + (tMax - tMin) * (i / N);
      const y = sampComposite(t);
      const px = padX + plotW * (i / N);
      const py = midY - y * scaleY;
      i === 0 ? ctx.moveTo(px, py) : ctx.lineTo(px, py);
    }
    ctx.stroke();
    ctx.shadowBlur = 0;
    
    ctx.setLineDash([]);

    // Axis labels
    ctx.fillStyle = 'rgba(255,255,255,0.2)';
    ctx.font = '18px Space Mono, monospace';
    ctx.textAlign = 'center';
    ctx.fillText('0s', padX, midY + 20);
    ctx.fillText('2s', W - padX, midY + 20);
  }

// ========================
// UI Controls -- below this is chat
// ========================

function updateSliders() {
  list.innerHTML = ""; // clear existing sliders

  subwaves.forEach((w, i) => {
    if (!w.enabled) return;

    const row = document.createElement('div');
    row.className = 'subwave-row';

    row.innerHTML = `
      <div class="subwave-color" style="background:${w.color}"></div>
      <div class="subwave-label">Wave ${i + 1}</div>
      <div class="param-chips">
        <div class="chip">
          A = <span id="ampVal${i}">${w.amplitude.toFixed(2)}</span>
          <input type="range"
            min="0"
            max="1"
            step="0.05"
            value="${w.amplitude}"
            data-index="${i}"
            data-param="amplitude">
        </div>
        <div class="chip">
          f = <span id="freqVal${i}">${w.frequency.toFixed(2)}</span>
          <input type="range"
            min="0.5"
            max="5"
            step="0.1"
            value="${w.frequency}"
            data-index="${i}"
            data-param="frequency">
        </div>
        <div class="chip">
          φ = <span id="phaseVal${i}">${(w.phase / Math.PI).toFixed(2)}π</span>
          <input type="range"
            min="0"
            max="${2 * Math.PI}"
            step="${0.05 * Math.PI}"
            value="${w.phase}"
            data-index="${i}"
            data-param="phase">
        </div>
      </div>
    `;

    list.appendChild(row);
  });

  // ✅ Add a **single delegated event listener** for all sliders
  list.querySelectorAll('input[type="range"]').forEach(input => {
    input.addEventListener('input', (e) => {
      const index = e.target.dataset.index;
      const param = e.target.dataset.param;
      const value = parseFloat(e.target.value);

      subwaves[index][param] = value;

      // update displayed value
      if (param === "phase") {
        document.getElementById(`phaseVal${index}`).textContent =
          (value / Math.PI).toFixed(2) + "π";
      } else if (param === "frequency") {
        document.getElementById(`freqVal${index}`).textContent =
          value.toFixed(2);
      } else {
        document.getElementById(`ampVal${index}`).textContent =
          value.toFixed(2);
      }

      draw(); // redraw canvas
    });
  });
}

const rerollBtn = document.getElementById("rerollBtn");
        rerollBtn.addEventListener("click", () => {
        	reroll();
        });

const ampCheck = document.getElementById("ampCheck");
const freCheck = document.getElementById("freCheck");
const phaCheck = document.getElementById("phaCheck");

// Variable to store the state
let ampEnabled = ampCheck.checked; // initial state
let freEnabled = freCheck.checked; // initial state
let phaEnabled = phaCheck.checked; // initial state

// Listen for changes
ampCheck.addEventListener("change", () => {
    ampEnabled = ampCheck.checked;
});
freCheck.addEventListener("change", () => {
    freEnabled = freCheck.checked;
});
phaCheck.addEventListener("change", () => {
    phaEnabled = phaCheck.checked;
});

function reroll() {
    realwaves.forEach(wave => {
		if(ampEnabled) {
        	wave.amplitude = randomRounded(0, 1, 0.05) * wave.enabled;
        } else {
        	wave.amplitude = 0.5 * wave.enabled;
        }
        
        if(freEnabled) {
        	wave.frequency = randomRounded(0.5, 5, 0.1) * wave.enabled;
        } else {
        	wave.frequency = 2.5 * wave.enabled;
        }
        
        if(phaEnabled) {
        	wave.phase = Math.PI*randomRounded(0, 2, 0.05) * wave.enabled;
        } else {
        	wave.phase = 0 * wave.enabled;
        }
        draw();
	})
}

function changeDifficulty() {
   realwaves.forEach(wave => {
	wave.enabled = 0;
	});
   subwaves.forEach(wave => {
	wave.enabled = 0;
	});
   for (let i = 0; i < difficulty; i++) {
      subwaves[i].enabled = 1;
      realwaves[i].enabled = 1;
   }
   reroll();
updateSliders();
   draw();
}

// Initial draw

updateSliders();
changeDifficulty();
draw();


</script>
</body>
</html>
