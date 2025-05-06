<style>
  .profile-container {
    display: flex;
    flex-direction: row;
    align-items: flex-start;
    max-width: 900px;
    margin: auto;
    padding: 40px 20px;
    flex-wrap: wrap;
  }

  .profile-img {
    width: 200px;
    border-radius: 10px;
    margin-right: 20px;
    flex-shrink: 0;
  }

  .profile-text {
    flex: 1;
    min-width: 250px;
    padding-top: 10px;
  }

  @media (max-width: 600px) {
    .profile-container {
      flex-direction: column;
      align-items: center;
    }

    .profile-img {
      margin-right: 0;
      margin-bottom: 20px;
      width: 60%;
      max-width: 200px;
    }

    .profile-text {
      text-align: center;
      padding: 0;
    }
  }
</style>

<div class="profile-container">
  <img src="headshot.JPEG" alt="Headshot of Peter Zhang" class="profile-img" />
  <div class="profile-text">
    <p><strong>Thank you for visiting my page!</strong> I hope this page provides you with a comprehensive view of my journey as a <strong>computational chemist</strong>.</p>
    <p>I am currently a <strong>4th-year PhD candidate in computational chemistry</strong> at the <strong>State University of New York at Buffalo</strong>. My research focuses on <strong>developing molecular dynamics simulation models to study ribonucleic acids (RNA)</strong> and their structural and phase separation properties.</p>
    <p>This summer, I will be joining the <strong>Platform Chemistry team at Enveda Biosciences</strong>, where I will contribute to advancing the <strong>computational pipeline for natural product hit-to-lead discovery</strong>. I am excited to apply my expertise in molecular modeling to accelerate drug discovery efforts.</p>
    <p>Feel free to connect with me on <a href="https://www.linkedin.com/in/hepzh/">LinkedIn</a> or explore my projects on <a href="https://github.com/peter-zhang-chem">GitHub</a> and <a href="https://scholar.google.com/citations?user=HaxobcoAAAAJ&hl=en">Google Scholar</a>.</p>
  </div>
</div>