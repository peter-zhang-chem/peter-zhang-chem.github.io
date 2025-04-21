<!-- Dynamic Vanta Background Container -->
<div id="vanta-bg" style="position: fixed; width: 100%; height: 100%; z-index: -1; top: 0; left: 0;"></div>

<!-- Bio Section on Top of Background -->
<div style="position: relative; z-index: 1; padding: 3rem; max-width: 900px; margin: auto; color: #ffffff;">

  <div style="display: flex; align-items: flex-start; flex-wrap: wrap;">
    <img src="headshot.JPEG" alt="Photo" width="200" style="margin-right: 20px; border-radius: 10px; box-shadow: 0 0 10px rgba(0,0,0,0.3);"/>
    <div>
      <p><strong>Thank you for visiting my page!</strong> I hope this page provides you with a comprehensive view of my journey as a <strong>computational chemist</strong>.</p>
      <p>I am currently a <strong>4th-year PhD candidate in computational chemistry</strong> at the <strong>State University of New York at Buffalo</strong>. My research focuses on <strong>developing molecular dynamics simulation models to study ribonucleic acids (RNA)</strong> and their structural and phase separation properties.</p>
      <p>This summer, I will be joining the <strong>Platform Chemistry team at Enveda Biosciences</strong>, where I will contribute to advancing the <strong>computational pipeline for natural product hit-to-lead discovery</strong>. I am excited to apply my expertise in molecular modeling to accelerate drug discovery efforts.</p>
      <p>Feel free to connect with me on <a href="https://www.linkedin.com/in/hepzh/" style="color: #ffecb3;">LinkedIn</a> or explore my projects on <a href="https://github.com/peter-zhang-chem" style="color: #ffecb3;">GitHub</a>.</p>
    </div>
  </div>
</div>

<!-- Scripts for Vanta Background -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r121/three.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/vanta@latest/dist/vanta.waves.min.js"></script>

<script>
  VANTA.WAVES({
    el: "#vanta-bg",
    mouseControls: true,
    touchControls: true,
    minHeight: 200.00,
    minWidth: 200.00,
    scale: 1.0,
    scaleMobile: 1.0,
    color: 0x2196f3,
    shininess: 30.0,
    waveHeight: 20.0,
    waveSpeed: 1.2,
    zoom: 0.85
  });
</script>
