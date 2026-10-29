# Data Audit & Overview Template
Your name here
2026-10-28

- [1: Project Overview](#1-project-overview)
- [2: Data Sources](#2-data-sources)
  - [2.1 Summary of sources](#21-summary-of-sources)
  - [2.2.1: \[name 1\]](#221-name-1)
  - [2.2.2 \[name 2\]](#222-name-2)
  - [2.3: Investigated and rejected
    sources](#23-investigated-and-rejected-sources)
  - [2.4: What I could not find](#24-what-i-could-not-find)
- [3: Licensing and permissions](#3-licensing-and-permissions)
  - [3.1: Licence by source](#31-licence-by-source)
  - [3.2: Unresolved licensing \[If you were able to find all licencing,
    delete
    this\]](#32-unresolved-licensing-if-you-were-able-to-find-all-licencing-delete-this)
  - [3.3: Downstream permissions](#33-downstream-permissions)
- [4: Consent and identifiability](#4-consent-and-identifiability)
- [5: Exclusions and harms](#5-exclusions-and-harms)
  - [5.1: Excluded data from the
    audit](#51-excluded-data-from-the-audit)
  - [5.2: Who could be harmed](#52-who-could-be-harmed)
  - [5.3: Unreleased working data](#53-unreleased-working-data)
- [6: Data Stewardship](#6-data-stewardship)
- [7: Use of AI](#7-use-of-ai)
- [8: Session information](#8-session-information)

<!--  another version of markdown elements, this works for html-style documents
&#10;[FP Part 2: HOW TO USE THIS TEMPLATE FOR YOUR SUBMISSION
&#10;Replace every bracketed prompt with your own writing (remove the brackets themselves, they're part of the placeholder here), and delete the prompt. 
&#10;Delete any sections that are not relevant for project, but note in commit message notes (not commit titles!) why you chose to delete them. That way I know that you've been thinking through what will be relevant as you begin the coding portion of this project.
&#10;Render, commit and push the markdown AND the .Rmd to your final project folder. 
&#10;This document will live in your final project folder in your repository alongside the AI-LOG.md, your code, and your raw data. Remember to commit it as you work on it, so that it doesn't get mixed up in your class or assignment commit messages.]
-->

# 1: Project Overview

\[Two or three sentences. What community, what question, what you are
building. Assume your reader has not seen your proposal.\]

------------------------------------------------------------------------

# 2: Data Sources

<!-- For the section numbers above, remember to update if needed for multiple sources or removing unneeded subsections -->

\[This section everything you went looking for in your data audit. If
you found sources that you chose not to use for the project itself, put
them in! That helps me understand all the options you were considering
as you worked through it\]

## 2.1 Summary of sources

\[Fill in one row per source you investigated. Include the ones you
rejected in the `Using?` column. This table is the quick reference your
reader checks before reading anything else. A clear table will give a
reader a good idea of what the focus is beyond the overview\]

| Source          | Producer         | Format  | Coverage         | Using        |
|:----------------|:-----------------|:--------|:-----------------|:-------------|
| \[source name\] | \[organization\] | \[CSV\] | \[place, years\] | Yes          |
| \[source name\] | \[organization\] | \[PDF\] | \[place, years\] | Yes          |
| \[source name\] | \[organization\] | \[API\] | \[place, years\] | No, see 2.4 |

## 2.2.1: \[name 1\]

**Producer and authority.** \[Who made this dataset, under what grant,
mandate, legal authority, initiative, etc. Ex: If a municipality
publishes it, which department, and are they required to? If a
researcher published it, what grant was it under? If it’s an open source
publication from an organization, do they describe why it is
published?\]

**Original Dataset Purpose.** \[Why was this collected? The original
author likely didn’t have the exact same research question as you.\]

**Collection method.** \[How did the values collected get into the file?
Sensor, survey, administrative by-product, manual entry, something
nobody can tell you? Remember that no answer found is still and
answer!\]

**Coverage and resolution.** \[Spatial extent, temporal range, reporting
frequency, unit of observation.\]

**Licence.** \[Find the licence declaration and put the shorthand here.
If you cannot find it, say here and complete section 3.2.\]

**Access.** \[How you got it, and whether a future user could get it the
same way. Include the date you retrieved it if it is from a website, as
sometimes web portals or search algorithms can change and make your
first search method difficult to replicate.\]

**Known problems.** \[What is wrong with it on a first look-through? Are
there any missing years, survey answers, changed definitions,
inconsistent identifiers, or NA values in the dataset?\]

\[One or two sentences on what the output above shows. Feel free to note
anything new or hard for you to initially understand in the structure,
types, source, or size.\]

## 2.2.2 \[name 2\]

\[Repeat the full structure above for every source you are using. Copy
the headings and the loaded source’s descriptive sentences below.\]

## 2.3: Investigated and rejected sources

\[One or two sentences per rejected source: what it was, why you went
looking. Some examples: licensing permissions, resolution mismatch,
paywall, abandoned since 2017, aggregated beyond its usefulness, changed
project idea, etc.

A rejected source documented properly saves the next person the time you
spent finding out the best source for your project. Negative results are
not bad news!\]

## 2.4: What I could not find

\[If you changed your project idea due to lack of data, explain what you
expected to find more easily but does not, or exists and is not
obtainable. Name who holds it, if you know the source. Absence is a
finding about how an organization or community’s data is managed.\]

------------------------------------------------------------------------

# 3: Licensing and permissions

## 3.1: Licence by source

| Source | Licence | Attribution_required | Attribution_given |
|:---|:---|:---|:---|
| \[source name 1\] | \[e.g. OGL Canada 2.0\] | Yes | Yes, see below |
| \[source name 2\] | \[licence\] | \[Yes/No\] | \[Yes/No\] |

**Attribution statements.** \[Reproduce the exact attribution each
licence requires, aka the wording the licence specifies.\]

## 3.2: Unresolved licensing \[If you were able to find all licencing, delete this\]

\[For any source where you could not determine the licence include: what
you tried, who you contacted or what you found, and what you concluded
about permissible use based on the project. “Unknown, this is my search
or web investigation trail” is worth full marks.\]

## 3.3: Downstream permissions

\[What can someone else do with your data project *output*? If you
combine sources under incompatible licences, your merged product may be
more restricted than either input was. Work out what licence you can
actually offer, and state it. If all open data, state it.\]

------------------------------------------------------------------------

# 4: Consent and identifiability

\[If your data does not describe people, say so explicitly and explain
why you are confident of that then move on.\]

**Consent.** \[If you collected it: what paticipants agreed to, and how
their data and consent was recorded. If someone else collected it: what
were people told at the time, and does your use fall inside that? If it
is your own data, what are you comfortable with people using it for in
the future if someone else downloaded it?\]

**Identifiability.** \[How many people are in the smallest reported
cell? How small is the population of the place or community you are
describing? If it does reference people’s data in a public manner
(sports stats like goals or time), that is public data. If it is a
conversation from a person who did not consent for their interview to be
shared, it’s not.\]

**What I will be doing with it.** \[Suppression of identifiable
information in your published dataset, aggregation to a coarser unit
(bigger groups etc), withholding identifying variables, or a decision
not to publish part of the dataset.\]

------------------------------------------------------------------------

# 5: Exclusions and harms

## 5.1: Excluded data from the audit

\[Every published dataset will demonstrate what an author aimed to
prioritize, and lack of data or missing data can show the same. If you
removed a column of the unprocessed dataset, describe what it was, and
why you decided to remove it. That could be things like sensitive
variables, time periods, places, categories. How could this exclusion
affect your data points in your analysis? \]

## 5.2: Who could be harmed

\[Name a plausible misuse and who would be on the receiving end. Think
about parties with an interest in the subject you chose, who are not
your intended audience.\]

## 5.3: Unreleased working data

\[If there is anything in your working data you would not publish, say
what it was and why. If there is nothing, describe why it is okay to
publish the working / raw dataset.\]

------------------------------------------------------------------------

# 6: Data Stewardship

**Where it lives.** \[Repository, platform, or institution. It’s okay to
be realisitic about the project after this course ends, as a GitHub
account you stop paying attention to in January is a real answer.\]

**Who maintains it.** \[If nobody, say nobody.\]

**Formats and dependencies.** \[Will your files open in ten years?
Consider what could break if someone tried it in 2036. The package
versions, data format, API, links to sources etc.\]

**Lifespan.** \[How long is this meaningfully usable before it needs
updating or should be retired?\]

------------------------------------------------------------------------

# 7: Use of AI

\[State plainly whether you have used AI tools on this project.

Your `AI-LOG.md` will live in this repository and is committed alongside
the work it describes. Do not reproduce it here, but use a link such as
`/log/AI-LOG.md` to point to it within your final project directory:\]

**AI log:** `AI-LOG.md` \[— maintained from \[starting date\] and
committed alongside each stage of work.\]

\[One short paragraph summarizing your pattern of AI use (if any) so
far: which stages, what for, etc. State the model you are using, such as
ChatGPT or Claude. If you are continuing to chat to a Gemeni search
agent after looking something up, that counts too! If you have not used
AI tools at all, say so here and make sure `AI-LOG.md` says the same.\]

\[**Reminder: the text in this document must be written in your own
words.**\]

------------------------------------------------------------------------

# 8: Session information

    R version 4.6.1 (2026-06-24)
    Platform: x86_64-apple-darwin20
    Running under: macOS Tahoe 26.6.2

    Matrix products: default
    BLAS:   /Library/Frameworks/R.framework/Versions/4.6-x86_64/Resources/lib/libRblas.0.dylib 
    LAPACK: /Library/Frameworks/R.framework/Versions/4.6-x86_64/Resources/lib/libRlapack.dylib;  LAPACK version 3.12.1

    locale:
    [1] en_US.UTF-8/en_US.UTF-8/en_US.UTF-8/C/en_US.UTF-8/en_US.UTF-8

    time zone: America/Halifax
    tzcode source: internal

    attached base packages:
    [1] stats     graphics  grDevices utils     datasets  methods   base     

    other attached packages:
     [1] lubridate_1.9.5 forcats_1.0.1   stringr_1.6.0   dplyr_1.2.1    
     [5] purrr_1.2.2     readr_2.2.0     tidyr_1.3.2     tibble_3.3.1   
     [9] ggplot2_4.0.3   tidyverse_2.0.0

    loaded via a namespace (and not attached):
     [1] gtable_0.3.6       jsonlite_2.0.0     compiler_4.6.1     tidyselect_1.2.1  
     [5] scales_1.4.0       yaml_2.3.12        fastmap_1.2.0      R6_2.6.1          
     [9] generics_0.1.4     knitr_1.52         pillar_1.11.1      RColorBrewer_1.1-3
    [13] tzdb_0.5.0         rlang_1.3.0        stringi_1.8.9      xfun_0.60         
    [17] S7_0.2.2           otel_0.2.0         timechange_0.4.0   cli_3.6.6         
    [21] withr_3.0.3        magrittr_2.0.5     digest_0.6.39      grid_4.6.1        
    [25] rstudioapi_0.19.0  hms_1.1.4          lifecycle_1.0.5    vctrs_0.7.3       
    [29] evaluate_1.0.5     glue_1.8.1         farver_2.1.2       rmarkdown_2.32    
    [33] tools_4.6.1        pkgconfig_2.0.3    htmltools_0.5.9   

<!--
BEFORE YOU SUBMIT
&#10;- Does your file render from a clean session (wiping the environment and history with no errors?
- Are all paths relative? No setwd(), no C:/Users/yourname/
- Is every package you used declared in the setup chunk?
- Is AI-LOG.md committed and current?
- Could a stranger read this and know what you are hoping to do in your project, what your data is, where it came
  from, and what others are allowed to do with it?
- Have you deleted every bracketed prompt including this comment block?
-->
