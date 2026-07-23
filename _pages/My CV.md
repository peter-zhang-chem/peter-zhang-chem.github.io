---
title: Curriculum vitae
author: Peter Zhang
date: 2026-06-30
category: Jekyll
layout: post
---

<button
  type="button"
  id="cv-download-button"
  class="cv-download-button">
  ↓ Download CV
</button>

<p id="cv-download-status" class="cv-download-status" aria-live="polite"></p>

<script>
document
  .getElementById("cv-download-button")
  .addEventListener("click", async function () {
    const button = this;
    const status = document.getElementById("cv-download-status");
    const pdfUrl = "{{ '/assets/Peter_CV_2026.pdf' | relative_url }}";

    button.disabled = true;
    button.textContent = "Preparing download…";
    status.textContent = "";

    try {
      const response = await fetch(pdfUrl);

      if (!response.ok) {
        throw new Error(`PDF request failed: ${response.status}`);
      }

      const pdfBlob = await response.blob();
      const blobUrl = URL.createObjectURL(pdfBlob);

      const temporaryLink = document.createElement("a");
      temporaryLink.href = blobUrl;
      temporaryLink.download = "Peter_Zhang_CV.pdf";

      document.body.appendChild(temporaryLink);
      temporaryLink.click();
      temporaryLink.remove();

      status.textContent = "Download started.";

      setTimeout(function () {
        URL.revokeObjectURL(blobUrl);
      }, 1000);
    } catch (error) {
      console.error(error);
      status.textContent = "Opening the PDF instead…";
      // window.location.href = pdfUrl;
    } finally {
      button.disabled = false;
      button.textContent = "↓ Download CV";
    }
  });
</script>

### Academic Research Experience
- **Visiting Research Fellow**, Rockefeller University (Host: [Steve Bonilla](https://www.rockefeller.edu/our-scientists/heads-of-laboratories/12052-steve-l-bonilla/)) – May 2026 to Present
- **Doctoral Candidate**, University at Buffalo – September 2023 to Present
- **Research Fellow**, [XSig](https://www.gettysburg.edu/offices/cross-disciplinary-science-institute/) – Summer 2018, 2019  
- **Undergraduate Research**, Gettysburg College – January 2018 to May 2021  

### Industry Research Experience
- **Platform Chemistry Intern**, [Enveda](https://enveda.com/) – May 2025 to August 2025  

### Education
* __State University of New York at Buffalo__, Buffalo, NY.
    - Ph.D. Computational Chemistry, [Bio Simulation Lab](https://biosimlabub.github.io/)
    - Advisor: [Hung T. Nguyen](https://arts-sciences.buffalo.edu/chemistry/faculty/faculty-directory/hung-t--nguyen.html)

* __Gettysburg College__, Gettysburg, PA.
    - B.S. Biochemistry and Molecular Biology
    - Advisor: [Tim Funk](https://www.gettysburg.edu/academic-programs/chemistry/faculty/employee_detail.dot?empId=02000253620013285&pageTitle=Tim+Funk)
    - Thesis: "Synthesis of cyanuric chloride-based synthetic lipids"

### Certificates
* Schrödinger - Virtual Screening and Machine Learning. Nov 2025.
* Schrödinger - Free Energy Calculations for Drug Design with FEP+. Oct 2025.

### Publications
**_Research Articles:_**

(6) **Zhang, H.**; Baidya, L.; Nguyen, H. T. Temperature-dependent ion partitioning remodels RNA structure and internal organization in condensate. _Submitted_.

(5) Mohanta, D.; **Zhang, H.**; Thirumalai, D.; Nguyen, H. T. Molecular origins of heterogeneous aging and spatial organization of RNA condensate. _Under Review_.

(4) **Zhang, H.**; Maity, H.; Nguyen T. H. Temperature-Dependent Ion Migration Underlies Sequence-Specific RNA Collapse. _Biophys. J._. **2026**, _125_, 3456–3470. [pdf](https://drive.google.com/file/d/1lj2rA4PI9TI1EFEWOaDB21HaICu4SG9c/view?usp=sharing) 
 
(3) Baidya, L.; **Zhang, H.**; Nguyen, H. T. Poly(ADP-Ribose) (PAR) Exhibits Ion-Dependent Structural Properties Distinct from RNA. _Nucleic Acids Res_ **2026**, _54 (6)_, gkag265. [pdf](https://drive.google.com/file/d/1XnAWzWrhvC-rKS__8QTFXUL4xpimZcSt/view?usp=sharing)

(2) Maity, H.; **Zhang, H.**; Thirumalai, D.; Nguyen, H. T. RNA Structural Complexity Dictates Its Ion Atmosphere. _J. Phys. Chem. Lett._ **2025**, 8393–8402. [pdf](https://drive.google.com/file/d/17H6vTtfJtpK7yu5TmXCpsvv7cPRlby3J/view?usp=sharing)

(1) Fang, M.; Kumar, G. S.; Racioppi, S.; **Zhang, H.**; Rabb, J. D.; Zurek, E.; Lin, Q. Hydrazonyl Sultones as Stable Tautomers of Highly Reactive Nitrile Imines for Fast Bioorthogonal Ligation Reaction. _J. Am. Chem. Soc._ **2023**, _145 (18)_, 9959–9964. [pdf](https://drive.google.com/file/d/1qe-B7CSS1OjKJw6gRGrmKajED_MZ5fLJ/view?usp=sharing)

**_Review Articles:_**
(2) **Zhang, H.**; Nguyen, H. T. Multiscale Models of Nucleic Acid–Driven Assembly and Biomolecular
Condensation. _In Preparation_

(1) **Zhang, H.**; Abidakun, O.; Nguyen, H. T. Molecular Insights into the Regulation of RNA Conformational Transitions : Ensembles, Dynamics, and Cellular Heterogeneity. _In Preparation_

**_Book Chapters:_**

(1) **Zhang, H.**, Fang, M., Lin, Q. (2025). Photo‑activatable Reagents for Bioorthogonal Ligation Reactions. In: Vrábel, M., Mikula, H. (eds) Bioorthogonal Reactions. Topics in Current Chemistry Collections. Springer, Cham. https://doi.org/10.1007/978-3-032-09821-4_5. [pdf](https://drive.google.com/file/d/1e9xyhD1HEe5vk2GPWd3ROBTLpXKtTDXz/view?usp=sharing)


### Presentations
* **Zhang, H.**; Nguyen, H.T. *RNA Collapse and Condensate Formation Tuned by Temperature and Counterions.* **Poster Presentation.** Biophysical Society Meeting, San Francisco, CA, Feb 2026.

* **Zhang, H.**; Nguyen, H.T. *Coarse-grained Simulation of ssRNA.* **Oral Presentation.** MDAnalysis UGM, Tucson, AZ, Nov 2025.

* **Zhang, H.**; Nguyen, H.T. *Temperature-Dependent Ion Migration Underlies Sequence-Specific RNA Collapse.* **Poster Presentation.** Rustbelt RNA Conference, Huron, Ohio, Oct 2025.

* **Zhang, H.**; Nguyen, H.T. *Ion-dependent Structural Ensemble and Phase Separation Propensity of Single-stranded RNA.* **Poster Presentation.** Computational Medicinal Chemistry School, Novartis Institutes for BioMedical Research, Cambridge, MA, September 2025.

* **Zhang, H.**; Nguyen, H.T. *Ion-dependent Structural Ensemble and Phase Separation Propensity of Single-stranded RNA.* **Poster Presentation.** Academic Excellence Celebration, Buffalo, NY, May 2025.

* **Zhang, H.**; Nguyen, H.T. *Coarse-grained Simulation of RNA.* **Invited Lecture.** Molecular Dynamics Simulations (Prof. Viviana Monje), Buffalo, NY, April 2025.

* **Zhang, H.**; Nguyen, H.T. *Ion-dependent Structural Ensembles and Phase Separation of Single-stranded RNA.* **Oral Presentation.** Buffalo RNA Group, Buffalo, NY, March 2025.

* **Zhang, H.**; Nguyen, H.T. *Ion-dependent Structural Ensembles and Phase Separation of Single-stranded RNA.* **Poster Presentation.** Biophysical Society Meeting, Los Angeles, CA, Feb 2025.

* **Zhang, H.**; Nguyen, H.T. *Ion-driven RNA Condensate Simulation.* **Poster Presentation.** Biophysical Society Meeting, Los Angeles, CA, Feb 2025.

* **Zhang, H.**; Nguyen, H.T. *Ion-dependent Structural Ensemble of Single-stranded RNA.* **Poster Presentation.** New York State RNA Conference, Canandaigua, NY, Oct 2024. **(Best Poster Award.)** 🏆

* **Zhang, H.**; Nguyen, H.T. *Parameterization of Coarse-grained ssRNA Force Field.* **Poster Presentation.** Buffalo Graduate Student Symposium, Buffalo, NY, May 2024.

### Teaching
* Computational Chemistry - Spring 2025
* Organic Chemistry - Spring 2024
* Physical Chemistry for Life Sciences - Spring 2022, Spring 2023, Fall 2024
* Honors Organic Chemistry - Fall 2022
* General Chemistry - Fall 2021, Fall 2025

### Honors & Awards
- **John Rys Fellowship**, University at Buffalo - Summer 2026  
  Awarded; declined in favor of research appointment at Rockefeller University  
- **Employee of the Month**, Enveda Biosciences - Summer 2025  
- **First Place, Summer Hackathon** *(Customized Bruker timsTOF Scheduler)*, Enveda Biosciences - Summer 2025  
- **Academic Excellence Award**, State University of New York - Spring 2025  
- **John B. Zinn Chemistry Research Award**, Gettysburg College - Spring 2021  