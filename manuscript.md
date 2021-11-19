---
title: A simple method for automating neuron counts in vitro
keywords:
- markdown
- publishing
- manubot
lang: en-US
date-meta: '2021-11-19'
author-meta:
- Samuel Burke
- Alex Tchung
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
  <meta name="dc.date" content="2021-11-19" />
  <meta name="citation_publication_date" content="2021-11-19" />
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
  <meta name="citation_author" content="Alex Tchung" />
  <meta name="citation_author_institution" content="Department of Pharmacology and Physiology, Université de Montréal" />
  <meta name="citation_author_orcid" content="0000-0001-7000-7046" />
  <link rel="canonical" href="https://samuelorion.github.io/methods_paper/" />
  <meta property="og:url" content="https://samuelorion.github.io/methods_paper/" />
  <meta property="twitter:url" content="https://samuelorion.github.io/methods_paper/" />
  <meta name="citation_fulltext_html_url" content="https://samuelorion.github.io/methods_paper/" />
  <meta name="citation_pdf_url" content="https://samuelorion.github.io/methods_paper/manuscript.pdf" />
  <link rel="alternate" type="application/pdf" href="https://samuelorion.github.io/methods_paper/manuscript.pdf" />
  <link rel="alternate" type="text/html" href="https://samuelorion.github.io/methods_paper/v/613368b9213ce23f5ef3f7d2bf7cca19aa72f08f/" />
  <meta name="manubot_html_url_versioned" content="https://samuelorion.github.io/methods_paper/v/613368b9213ce23f5ef3f7d2bf7cca19aa72f08f/" />
  <meta name="manubot_pdf_url_versioned" content="https://samuelorion.github.io/methods_paper/v/613368b9213ce23f5ef3f7d2bf7cca19aa72f08f/manuscript.pdf" />
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
([permalink](https://samuelorion.github.io/methods_paper/v/613368b9213ce23f5ef3f7d2bf7cca19aa72f08f/))
was automatically generated
from [samuelorion/methods_paper@613368b](https://github.com/samuelorion/methods_paper/tree/613368b9213ce23f5ef3f7d2bf7cca19aa72f08f)
on November 19, 2021.
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

+ **Alex Tchung**<br>
    ![ORCID icon](images/orcid.svg){.inline_icon}
    [0000-0001-7000-7046](https://orcid.org/0000-0001-7000-7046)
    · ![GitHub icon](images/github.svg){.inline_icon}
    [solvabl](https://github.com/solvabl)<br>
  <small>
     Department of Pharmacology and Physiology, Université de Montréal
     · Funded by CRSNG, Brain Canada & Krembil Foundations
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


## list of pubs for meta-analysis

[@PMID:10435500]
[@PMID:10448425]
[@PMID:10466894]
[@PMID:10690993]
[@PMID:11972798]
[@PMID:1353337]
[@PMID:1449247]
[@PMID:1725760]
[@PMID:1726030]
[@PMID:1748881]
[@PMID:17491094]
[@PMID:18297291]
[@PMID:1849779]
[@PMID:1933245]
[@PMID:2010756]
[@PMID:20817536]
[@PMID:20856865]
[@PMID:22941241]
[@PMID:23884810]
[@PMID:2570794]
[@PMID:2730377]
[@PMID:2747841]
[@PMID:2817827]
[@PMID:2950715]
[@PMID:2996284]
[@PMID:33479244]
[@PMID:3604586]
[@PMID:3753274]
[@PMID:3883886]
[@PMID:4022359]
[@PMID:4073850]
[@PMID:6089493]
[@PMID:6198483]
[@PMID:6247458]
[@PMID:6732189]
[@PMID:6830170]
[@PMID:6865505]
[@PMID:7651444]
[@PMID:7770115]
[@PMID:7804831]
[@PMID:7894999]
[@PMID:7904735]
[@PMID:7916375]
[@PMID:8093581]
[@PMID:8358501]
[@PMID:8489206]
[@PMID:8610103]
[@PMID:8649572]
[@PMID:8731382]
[@PMID:9126172]
[@PMID:8543951]
[@PMID:9444566]
[@PMID:143504126]
[@PMID:14090529]
[@PMID:17470494]
[@PMID:4050345]
[@PMID:5886206]
[@PMID:6637393]
[@PMID:9627747]
[@PMID:6695594]
[@PMID:NID]
[@PMID:10208589]
[@PMID:10459912]
[@PMID:10599772]
[@PMID:10688892]
[@PMID:10716254]
[@PMID:10722997]
[@PMID:10869053]
[@PMID:10892768]
[@PMID:11031089]
[@PMID:11114264]
[@PMID:11194939]
[@PMID:11445255]
[@PMID:11476292]
[@PMID:11697191]
[@PMID:11782993]
[@PMID:12390970]
[@PMID:12419530]
[@PMID:12465053]
[@PMID:12633144]
[@PMID:12902309]
[@PMID:1320531]
[@PMID:1494900]
[@PMID:14991820]
[@PMID:15197709]
[@PMID:15389895]
[@PMID:15468109]
[@PMID:15634729]
[@PMID:15912496]
[@PMID:16014651]
[@PMID:16320253]
[@PMID:16407544]
[@PMID:16421740]
[@PMID:16476936]
[@PMID:16753180]
[@PMID:16896314]
[@PMID:1691042]
[@PMID:16941622]
[@PMID:1694418]
[@PMID:17029264]
[@PMID:17052351]
[@PMID:17142832]
[@PMID:1718530]
[@PMID:17639427]
[@PMID:17894336]
[@PMID:18163454]
[@PMID:18227417]
[@PMID:18264713]
[@PMID:18329941]
[@PMID:18581481]
[@PMID:18804518]
[@PMID:1892359]
[@PMID:1895529]
[@PMID:19022934]
[@PMID:19519642]
[@PMID:19597132]
[@PMID:1972319]
[@PMID:19735086]
[@PMID:1978260]
[@PMID:20176003]
[@PMID:2065255]
[@PMID:21147074]
[@PMID:21553300]
[@PMID:21664855]
[@PMID:21696423]
[@PMID:22306459]
[@PMID:2257487]
[@PMID:23152586]
[@PMID:2357341]
[@PMID:23891794]
[@PMID:23996276]
[@PMID:24099985]
[@PMID:24226265]
[@PMID:24501436]
[@PMID:2456487]
[@PMID:2463283]
[@PMID:24704327]
[@PMID:24996051]
[@PMID:25062696]
[@PMID:2521057]
[@PMID:2542825]
[@PMID:2549846]
[@PMID:2557795]
[@PMID:25649148]
[@PMID:2575832]
[@PMID:2602422]
[@PMID:26095065]
[@PMID:26251824]
[@PMID:26295830]
[@PMID:26468408]
[@PMID:27003787]
[@PMID:27061071]
[@PMID:2709038]
[@PMID:27357212]
[@PMID:27891695]
[@PMID:28059471]
[@PMID:28190674]
[@PMID:28626918]
[@PMID:28725697]
[@PMID:2899295]
[@PMID:29420861]
[@PMID:29917054]
[@PMID:30201049]
[@PMID:30485555]
[@PMID:30590599]
[@PMID:31454423]
[@PMID:31769073]
[@PMID:3239957]
[@PMID:32881029]
[@PMID:33684514]
[@PMID:3379428]
[@PMID:33899954]
[@PMID:34092653]
[@PMID:3998751]
[@PMID:6475484]
[@PMID:6533352]
[@PMID:6847136]
[@PMID:7398694]
[@PMID:7494602]
[@PMID:7536004]
[@PMID:7700528]
[@PMID:7985492]
[@PMID:8199342]
[@PMID:8285597]
[@PMID:8433802]
[@PMID:8437705]
[@PMID:8628464]
[@PMID:8737406]
[@PMID:8809817]
[@PMID:8866425]
[@PMID:8990048]
[@PMID:9039456]
[@PMID:9106122]
[@PMID:9270609]
[@PMID:9335015]
[@PMID:9335016]
[@PMID:9387796]
[@PMID:9798081]
[@PMID:4661701968]
[@PMID:16606773]
[@PMID:20628197]
[@PMID:3475716]
[@PMID:7704619]


## References {.page_break_before}

<!-- Explicitly insert bibliography here -->
<div id="refs"></div>
