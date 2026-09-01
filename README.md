<style>
  .profile-container {
    max-width: 950px;
    margin: auto;
    padding: 40px 20px;
  }

  .hero-section {
    display: flex;
    align-items: center;
    gap: 40px;
    margin-bottom: 40px;
    flex-wrap: wrap;
  }

  .profile-img {
    width: 220px;
    border-radius: 12px;
    flex-shrink: 0;
  }

  .value-quote {
    flex: 1;
    font-style: italic;
    font-size: 1.5rem;
    line-height: 1.7;
    color: #555;
    border-left: 4px solid #999;
    padding-left: 24px;
    margin: 0;
  }

  .quote-author {
    display: block;
    margin-top: 15px;
    font-size: 1rem;
    font-style: normal;
    color: #777;
  }

  .profile-text {
    font-size: 1.5rem;
    line-height: 1.8;
  }

  @media (max-width: 700px) {
    .hero-section {
      flex-direction: column;
      text-align: center;
    }

    .value-quote {
      border-left: none;
      border-top: 4px solid #999;
      padding-left: 0;
      padding-top: 20px;
      font-size: 1.2rem;
    }

    .profile-img {
      width: 60%;
      max-width: 220px;
    }
  }
</style>

<div class="profile-container">

  <div class="hero-section">
    <img src="headshot.JPEG" 
         alt="Headshot of Peter Zhang" 
         class="profile-img" />

    <blockquote class="value-quote">
      “We should publish great science, but more importantly, we must translate it into therapeutics to benefit patients — after all, at the end of the day, we are all patients.”
      <span class="quote-author">— Atul Butte</span>
    </blockquote>
  </div>

  <div class="profile-text">

    <p><strong>Hi! Thanks for taking the time to learn a little more about me. I hope this page gives you a sense of what motivates me as a scientist, the work I've done, and where I hope to go next.</strong></p>

    <p>
      I am currently a Research Fellow at The Rockefeller University in the
      <a href="https://www.bonillalab.org/" target="_blank">Laboratory of RNA Structural Biology and Biophysics</a>.
      Here, I am developing cryo-EM image-processing and computational methods to move beyond describing biomolecules as single static structures and toward resolving the distributions of conformational states that make up RNA structural ensembles.
    </p>

    <p>
      At the same time, I am completing my Ph.D., where I develop and apply coarse-grained molecular dynamics simulations to understand RNA biophysics, including
      <a href="https://www.cell.com/biophysj/fulltext/S0006-3495(26)00366-8" target="_blank">single-stranded RNA</a>
      and its phase-separation behavior, as well as
      <a href="https://academic-oup-com.gate.lib.buffalo.edu/nar/article/54/6/gkag265/8550794" target="_blank">poly(ADP-ribose)</a>.
      Across these projects, I am especially interested in connecting molecular structure, dynamics, and function through simulation, structural biology, and data-driven approaches.
    </p>

    <p>
      My long-term goal is to help develop therapies that improve patients' outcomes and quality of life, a motivation shaped in part by seeing diseases such as cancer affect people close to me. In the near term, I hope to work at the intersection of cryo-EM, molecular modeling, and machine learning. I am particularly interested in using molecular dynamics simulations and computational inference to characterize heterogeneous structural ensembles rather than relying solely on a single static structure.
    </p>

    <p>
      Ultimately, I want to understand not only what biomolecules look like, but how they move, how those dynamics influence function, and how that knowledge can be leveraged to design better therapeutics.
    </p>

    <p>
      If you are looking for a scientist with expertise in computational molecular modeling and cryo-EM, I would love to connect and explore how I might contribute. I am always excited to learn, collaborate across disciplines, and help tackle challenging problems at the interface of computation, structural biology, and therapeutics.
    </p>

  </div>
</div>