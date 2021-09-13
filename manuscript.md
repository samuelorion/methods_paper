---
title: A simple method for automating neuron counts in vitro
keywords:
- markdown
- publishing
- manubot
lang: en-US
date-meta: '2021-09-13'
author-meta:
- Samuel Burke
header-includes: |-
  <!--
  Manubot generated metadata rendered from header-includes-template.html.
  Suggest improvements at https://github.com/manubot/manubot/blob/main/manubot/process/header-includes-template.html
  -->
  <meta name="dc.format" content="text/html" />
  <meta name="dc.title" content="A simple method for automating neuron counts in vitro" />
  <meta name="citation_title" content="A simple method for automating neuron counts in vitro" />
  <meta property="og:title" content="A simple method for automating neuron counts in vitro" />
  <meta property="twitter:title" content="A simple method for automating neuron counts in vitro" />
  <meta name="dc.date" content="2021-09-13" />
  <meta name="citation_publication_date" content="2021-09-13" />
  <meta name="dc.language" content="en-US" />
  <meta name="citation_language" content="en-US" />
  <meta name="dc.relation.ispartof" content="Manubot" />
  <meta name="dc.publisher" content="Manubot" />
  <meta name="citation_journal_title" content="Manubot" />
  <meta name="citation_technical_report_institution" content="Manubot" />
  <meta name="citation_author" content="Samuel Burke" />
  <meta name="citation_author_institution" content="Department of Neuroscience, Univerisité de Montréal" />
  <meta name="citation_author_orcid" content="0000-0002-7363-5133" />
  <meta name="twitter:creator" content="@kernow_qc" />
  <link rel="canonical" href="https://samuelorion.github.io/methods_paper/" />
  <meta property="og:url" content="https://samuelorion.github.io/methods_paper/" />
  <meta property="twitter:url" content="https://samuelorion.github.io/methods_paper/" />
  <meta name="citation_fulltext_html_url" content="https://samuelorion.github.io/methods_paper/" />
  <meta name="citation_pdf_url" content="https://samuelorion.github.io/methods_paper/manuscript.pdf" />
  <link rel="alternate" type="application/pdf" href="https://samuelorion.github.io/methods_paper/manuscript.pdf" />
  <link rel="alternate" type="text/html" href="https://samuelorion.github.io/methods_paper/v/30182bfde8b2c6c52ac1cb085ee7ef8e97cf4909/" />
  <meta name="manubot_html_url_versioned" content="https://samuelorion.github.io/methods_paper/v/30182bfde8b2c6c52ac1cb085ee7ef8e97cf4909/" />
  <meta name="manubot_pdf_url_versioned" content="https://samuelorion.github.io/methods_paper/v/30182bfde8b2c6c52ac1cb085ee7ef8e97cf4909/manuscript.pdf" />
  <meta property="og:type" content="article" />
  <meta property="twitter:card" content="summary_large_image" />
  <link rel="icon" type="image/png" sizes="192x192" href="https://manubot.org/favicon-192x192.png" />
  <link rel="mask-icon" href="https://manubot.org/safari-pinned-tab.svg" color="#ad1457" />
  <meta name="theme-color" content="#ad1457" />
  <!-- end Manubot generated metadata -->
bibliography:
- content/manual-references.json
manubot-output-bibliography: output/references.json
manubot-output-citekeys: output/citations.tsv
manubot-requests-cache-path: ci/cache/requests-cache
manubot-clear-requests-cache: false
...






<small><em>
This manuscript
([permalink](https://samuelorion.github.io/methods_paper/v/30182bfde8b2c6c52ac1cb085ee7ef8e97cf4909/))
was automatically generated
from [samuelorion/methods_paper@30182bf](https://github.com/samuelorion/methods_paper/tree/30182bfde8b2c6c52ac1cb085ee7ef8e97cf4909)
on September 13, 2021.
</em></small>

## Authors



+ **Samuel Burke**<br>
    ![ORCID icon](images/orcid.svg){.inline_icon}
    [0000-0002-7363-5133](https://orcid.org/0000-0002-7363-5133)
    · ![GitHub icon](images/github.svg){.inline_icon}
    [samuelorion](https://github.com/samuelorion)
    · ![Twitter icon](images/twitter.svg){.inline_icon}
    [kernow_qc](https://twitter.com/kernow_qc)<br>
  <small>
     Department of Neuroscience, Univerisité de Montréal
     · Funded by FRQS
  </small>



## Abstract {.page_break_before}




## Introduction
The quantification of cell numbers in *in vitro* and *in vivo* samples is a foundational variable in experimental biology.
However, manually counting cells is a massively laborious and insipid task, often tasked to junior scientists. 
Furthermore, manually counting cells is a massively laborious and insipid task, often tasked to junior scientists. Classically, the task will be achieved either by sitting at the microscope, or computer – with a counting-clicker (or equivalent) – for days, if not weeks and months.
With the advent of user-friendly automated imaging systems, relatively high throughput experiments can be imaged for cell number quantification by most wet-lab scientists.
With relatively little computational nous, most biologists can use software such as ImageJ [@doi:10.1038/nmeth.2089], CellProfiller [@doi:10.1371/journal.pbio.2005970] (and other similar projects) to achieve accurate quantifications of cells that have simple morphological features (such as stained nuclei). 
However, for neurons – and especially projecting neurons – this becomes a significant challenge. Not only do these types of cells have more complex morphologies, but these types of cells have received less attention from developers.

## The problem 

The current literature and documentation for methods for quantifying cell numbers are either limited to imaging segmentation tasks that are too simple, or describing methods that require one to be computationally-literate (and unperturbed by extensive mathematical formula within publications).
In the context of *in vitro* experiments, the quantification of number of nuclei can be achieved with very simple segmentation techniques.
However, when working with tissue samples, the task becomes significantly more complex.
Open competitons have allowed machine learning and data science practitioners to apply their methods to these tasks, and have achieved very high accuracy in nuclei segmentation challenges[@doi:10.1038/s41592-019-0612-7].
However, wet-lab biologist struggle to use these specialized methods (one reason being, perhaps, due to an undervaluation of computational skills in most biological curricula).  

For the more difficult task of automating the counting of neurons, multiple authors have described the application of state-of-the-art methods to achieve accurate quantifications [@doi:10.1038/s41598-019-50137-9, @doi:10.1101/2020.10.21.348771]. 
Indeed, authors have also attempted to create deep learning solutions to the problem of counting neurons, that can be used as a plug-in in ImageJ. 
Albeit a valiant effort to “... present an ImageJ plugin that enables non-machine-learning experts to analyze their data with U-Net on either a local computer or a remote server/cloud service” [@doi:10.1038/s41592-018-0261-2], the implementation of such methods is still challenging for many biologists, and for in vitro contexts, unnecessarily performant.   

## A solution

Many of these more advanced methods lack a substantial pedagogical component. 
To implement many of the methods – which a junior scientists will likely find themselves doing on multiple occasions for their own use-case – specific domain expertise is required in the computational realm (this is especially significant when one considers that most biologists / neuroscientists will be unfamiliar (as was this author) of the simple term iterator [@{https://en.wikipedia.org/w/index.php?title=Iterator&oldid=1022023119}]. 
One solution is for these methods and protocols to be contained within notebook interfaces such as Project Jupyter [@{https://www.jupyter.org}]. Not only can documentation be included with examples, but the methods can also be executed within a browser, and in systems where there is zero configuration required. 
In addition, using these formats for the sharing of methods may help instil a culture of open documentation and analysis. In this work we describe unground-breaking, simple to use and apply methods, that allow wet-lab biologist / neuroscientists to quantify the number of projecting neurons cultured in multi-well plates. 


## References {.page_break_before}

<!-- Explicitly insert bibliography here -->
<div id="refs"></div>
