<!-- Dynamic Background -->
<div id="vanta-bg" style="position: fixed; width: 100%; height: 100%; z-index: -1;"></div>

<!-- Headshot + Intro Section -->
<div style="display: flex; align-items: flex-start; max-width: 900px; margin: auto; padding-top: 40px;">
  <img src="headshot.JPEG" alt="Photo 1" width="200" style="margin-right: 20px; border-radius: 10px;" />
  <div style="background-color: #B5D4EB; padding: 20px; border-radius: 10px;">
    <p><strong>Thank you for visiting my page!</strong> I hope this page provides you with a comprehensive view of my journey as a <strong>computational chemist</strong>.</p>
    <p>I am currently a <strong>4th-year PhD candidate in computational chemistry</strong> at the <strong>State University of New York at Buffalo</strong>. My research focuses on <strong>developing molecular dynamics simulation models to study ribonucleic acids (RNA)</strong> and their structural and phase separation properties.</p>
    <p>This summer, I will be joining the <strong>Platform Chemistry team at Enveda Biosciences</strong>, where I will contribute to advancing the <strong>computational pipeline for natural product hit-to-lead discovery</strong>. I am excited to apply my expertise in molecular modeling to accelerate drug discovery efforts.</p>
    <p>Feel free to connect with me on <a href="https://www.linkedin.com/in/hepzh/">Linkedin</a> or explore my projects on <a href="https://github.com/peter-zhang-chem">Github</a>.</p>
  </div>
</div>

<!-- Vanta.js Background Script -->
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
    color: 0x1e88e5,
    shininess: 50.0,
    waveHeight: 20.0,
    waveSpeed: 0.8,
    zoom: 0.85
  });
</script>