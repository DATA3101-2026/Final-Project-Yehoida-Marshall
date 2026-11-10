# Data Audit for a Comparative Study of Norris and Piastri
Yehoida Marshall
2026-11-10

# 1: Project Overview

This project aims to investigate how much a driver’s individual
technique influences race performance in Formula 1, rather than
performance being determined by the machinery alone. By comparing Lando
Norris and Oscar Piastri throughout the 2025 season, I hope to better
understand these differences since both drivers compete for the same
team and have access to similar machinery, resources, and team
strategies. I will be examining telemetry data, particularly speed,
throttle application and braking behaviour, alongside tyre compound and
tyre age, to explore how driving techniques and tyre-related decisions
affect race pace across straight, high-speed corners, and low-speed
corners, where the data is available.

------------------------------------------------------------------------

# 2: Data Sources

## 2.1 Summary of sources

| Source | Producer | Format | Coverage | Using |
|:---|:---|:---|:---|:---|
| OpenF1 | OpenF1 project | API (JSON/CSV) | Formula 1 sessions, 2023-present; 2025 tested | Yes |
| FastF1 | Philipp Schaefer and contributors | Python package | Historical F1 session and telemetry data | No |
| Jolpica-F1 | Jolpica and 18 contirbutors | REST API | Historical F1 session and telemetry | No |

## 2.2.1: OpenF1

**Producer and authority.** OpenF1 is an open-source project maintained
by nine contributors(br-g, adrielfrederick, keerth 1gowda, JesusGranizo,
Ragha02, MukulS07, aksharbhagwandin, NiklEVer26 and FestinBiju). Its
mission is to make Formula 1 data accessible to everyone.It is an
unofficial data service, it is not an official FIA or Formula 1
provider.

**Original Dataset Purpose.** The purpose of the original dataset during
the race is for teams to use timing and telemetry information to monitor
car performance, driver behaviour and race strategy and after the race
the teams can analyse that information to understand what happened and
inform decisions for future races.

**Collection method.** The original data comes from sensors installed in
the cars and from race timing and tracking systems.However, the exact
process OpenF1 uses to obtain and process all of its data has not been
fully verified.

**Coverage and resolution.** The scope of my research focuses on the
2025 formula 1 season, specifically Lando Norris and Oscar Piastri
across 24 races. In the data source, I was looking for variables such as
speed, throttle application, tyre age, tyre compound, braking, lap
times, and car location, and I found records containing these variables.
The data source has lap data recorded per lap, tyre information per
stint, and telemetry data recorded multiple times per second. For my
data audit, I examined one track, the Bahrain Grand Prix, to investigate
the available variables. I also checked whether records were available
for both drivers across all 24 tracks, which they were. I just, however
did not fully verify the completeness and accuracy of every variable
across the entire season.

**Licence.** The OpenF1 GitHub repository contains a licence called
Attribution-NonCommercial-ShareAlike 4.0 International Licence. The
licence allows noncommercial sharing and adaptation of the material it
covers.Users must give appropriate credit and follow ShareAlike
requirements when sharing adaptations. It is unclear whether this
licence covers the original Formula 1 telemetry data, so redistribution
rights are still not clarified.

**Access.** I found OpenF1 while searching for Formula 1 data online.I
retrieved it on on 9/11/26.After investigating three possible sources, I
selected OpenF1 because I encountered problems accessing the other data
source FastF1. I then checked whether OpenF1 contained the variables
needed for my research. With the help of AI, I retrieved the data
directly from OpenF1 API into R using jsonlite::fromJSON() function
(which we learnt in class after I had use AI). I was able to access
historical data without creating an account or paying a fee because I
was using 2025 data and from 2023 the data was free. The only problem I
encountered was HTTP 429 errors when making multiple request,to see if
the data I needed was available, which temporarily limited my access to
the data.

**Known problems.** While testing OpenF1, I noticed some limitations in
the data. One 2025 race session returned only one lap record for Oscar
Piastri, so I would need to determine whether this was due to an early
retirement or missing data. I also noticed unusual telemetry values,
where throttle and braking measurements reached 104, even though
throttle is generally measured on a 0–100 scale and braking is
represented using binary values. Another limitation is that OpenF1
provides car location data but does not directly identify whether each
measurement was recorded on a straight, high-speed corner, or low-speed
corner.

    Rows: 1,129
    Columns: 16
    $ meeting_key       <int> 1257, 1257, 1257, 1257, 1257, 1257, 1257, 1257, 1257…
    $ session_key       <int> 10014, 10014, 10014, 10014, 10014, 10014, 10014, 100…
    $ driver_number     <int> 81, 16, 63, 55, 10, 12, 22, 7, 6, 4, 31, 1, 14, 23, …
    $ lap_number        <int> 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1…
    $ date_start        <chr> "2025-04-13T15:03:49.173000+00:00", "2025-04-13T15:0…
    $ duration_sector_1 <dbl> 33.127, 34.565, 33.821, 35.564, 35.235, 35.266, 36.8…
    $ duration_sector_2 <dbl> 42.130, 43.164, 42.305, 43.370, 42.900, 44.112, 43.8…
    $ duration_sector_3 <dbl> 23.956, 24.036, 23.820, 24.064, 24.192, 24.317, 24.6…
    $ i1_speed          <int> 233, 233, 232, 228, 230, 230, 236, 230, 235, 230, 22…
    $ i2_speed          <int> 244, 250, 249, 245, 239, 248, 250, 240, 252, 244, 24…
    $ is_pit_out_lap    <lgl> FALSE, FALSE, FALSE, FALSE, FALSE, FALSE, FALSE, FAL…
    $ lap_duration      <dbl> 99.213, 101.765, 99.946, 102.998, 102.327, 103.695, …
    $ segments_sector_1 <list> <NA, 0, 2049, 2049, 2051, 2051, 2049, 2049, 2051, 2…
    $ segments_sector_2 <list> <2051, 2051, 2051, 2049, 2051, 2049, 2049, 2049, 20…
    $ segments_sector_3 <list> <2049, 2049, 2049, 2049, 2049, 2049, 2051>, <2049, …
    $ st_speed          <int> 250, 256, 251, 257, 256, 253, 210, 243, 243, 257, 24…

      meeting_key session_key driver_number lap_number
    1        1257       10014            81          1
    2        1257       10014            16          1
    3        1257       10014            63          1
    4        1257       10014            55          1
    5        1257       10014            10          1
    6        1257       10014            12          1
                            date_start duration_sector_1 duration_sector_2
    1 2025-04-13T15:03:49.173000+00:00            33.127            42.130
    2 2025-04-13T15:03:49.173000+00:00            34.565            43.164
    3 2025-04-13T15:03:49.173000+00:00            33.821            42.305
    4 2025-04-13T15:03:49.173000+00:00            35.564            43.370
    5 2025-04-13T15:03:49.173000+00:00            35.235            42.900
    6 2025-04-13T15:03:49.173000+00:00            35.266            44.112
      duration_sector_3 i1_speed i2_speed is_pit_out_lap lap_duration
    1            23.956      233      244          FALSE       99.213
    2            24.036      233      250          FALSE      101.765
    3            23.820      232      249          FALSE       99.946
    4            24.064      228      245          FALSE      102.998
    5            24.192      230      239          FALSE      102.327
    6            24.317      230      248          FALSE      103.695
                                               segments_sector_1
    1      NA, 0, 2049, 2049, 2051, 2051, 2049, 2049, 2051, 2049
    2      NA, 0, 2049, 2049, 2049, 2049, 2049, 2049, 2049, 2049
    3      NA, 0, 2049, 2051, 2049, 2049, 2049, 2049, 2049, 2049
    4 2048, 2049, 2049, 2049, 2049, 2049, 2049, 2049, 2049, 2049
    5      NA, 0, 2049, 2049, 2049, 2049, 2049, 2049, 2049, 2049
    6      NA, 0, 2049, 2049, 2049, 2049, 2049, 2049, 2049, 2049
                                                     segments_sector_2
    1 2051, 2051, 2051, 2049, 2051, 2049, 2049, 2049, 2051, 2049, 2049
    2 2049, 2049, 2049, 2049, 2049, 2049, 2049, 2049, 2049, 2049, 2049
    3 2049, 2049, 2049, 2049, 2049, 2049, 2049, 2051, 2049, 2049, 2049
    4 2049, 2049, 2049, 2049, 2049, 2049, 2049, 2049, 2049, 2049, 2049
    5 2049, 2049, 2049, 2049, 2049, 2049, 2049, 2049, 2049, 2049, 2049
    6       0, 0, 2049, 2049, 2049, 2049, 2049, 2049, 2049, 2049, 2049
                             segments_sector_3 st_speed
    1 2049, 2049, 2049, 2049, 2049, 2049, 2051      250
    2 2049, 2049, 2049, 2049, 2049, 2049, 2051      256
    3 2051, 2049, 2049, 2051, 2049, 2051, 2051      251
    4 2049, 2049, 2049, 2049, 2049, 2049, 2048      257
    5    2049, 2049, 2049, 2049, 2049, 2049, 0      256
    6 2049, 2049, 2049, 2049, 2049, 2049, 2051      253

The output contains 1129 observations and 16 variables from the 2025
Bahrain Grand Prix. Some of the variables include lap number, lap
duration, driver number, sector timing, etc. This information will help
me filter the data to find the 2 driver numbers I am studying and
compare how long it took them to finish a lap and a sector, etc

## 2.3: Investigated and rejected sources

Jolipca-F1: I discovered it through F1DataStop, the same website where I
found the other data providers,I rejected it because I first audited
OpenF1 and it had everything I needed so I didn’t see the point. FastF1:
I tried to investigate it, because its README on GitHub seemed very
convincing but when I tried to retrieve data it was giving me so many
errors and so i moved on with OpenF1.

## 2.4: What I could not find

OpenF1 did not directly provide classifications for different sections
of the circuit, such as straight, high-speed, and low-speed corners.
However, when I plotted the location data for the Bahrain Grand Prix, I
was able to identify the general shape of the circuit and observe
changes in speed. Although I could visually identify corners, I could
not yet distinguish between the high-speed and low-speed corners. I do
not currently see this as a reason to change my research question, but
if I cannot reliably classify the corners, I may narrow my research
question and generalize some of the detailed variables.

------------------------------------------------------------------------

# 3: Licensing and permissions

## 3.1: Licence by source

| Source | Licence                      | Attribution_required | Attribution_given |
|:-------|:-----------------------------|:---------------------|:------------------|
| OpenF1 | CC BY-NC-SA 4.0 (repository) | Yes                  | Yes, see below    |

**Attribution statements.** The date for my project was obtained byt
OpenF1(https://openf1.org), an open source Formula 1 data API. The
GitHub repository(https://github.com/br-g/openf1) cantains the Creative
Commons Attribution-NonCommercial-ShareAlike 4.0 International
licence(https://github.com/br-g/openf1/blob/main/LICENSE). I can’t say
for certian whether this lincence also applies to the underlying Formula
1 telemetry data.

## 3.2: Unresolved licensing

I was unable to confirm whether OpenF1’s repository licence covers the
original Formula 1 telemetry data and because of lack of time,I could
not contact OpenF1 for clarification. However, I spoke to you about this
in class and you said it was okay to proceed. I will make sure that I do
not redistribute the raw data until I know for certain that I have
permission to .

## 3.3: Downstream permissions

Since I am only using OpenF1, I do not have to worry about combining
data from sources with different license.However, because I am still
unsure whether OpenF1’s licence covers the original telemetry data, I
cannot offer an open licence for the raw data or give others permission
to redistribute it. I can make my own analysis and findings available
for people to read and reference, but for now, I will keep my original
work under copyright with all rights reserved.

------------------------------------------------------------------------

# 4: Consent and identifiability

**Consent.** I did not collect the data myself, as it was already
available through OpenF1. The data describes the performance of Formula
1 drivers during official races, and I am using it for academic
research. From what I found, the collection and use of telemetry data
are governed by contracts and the Formula 1 regulations rather than
separate consent from drivers but I can’t say for sure what the exact
agreements are and if the cover the public sharing of this data in
particular.

**Identifiability.** My research focuses on 1 team (McLaren), and its 2
drivers (Lando Norris and Oscar Piastri). The smallest group is one
diver. Both are identifiable and their racing performance data is
publicly available.

**How sensitive data will be used.** The data I am using is about the
drivers’ racing performance and doesn’t include private or sensitive
information. I will keep their names and drivers numbers because they
are important for my comparison but i won’t publish the raw telemetry
data un till I confirm that I have permission to do so.

------------------------------------------------------------------------

# 5: Exclusions and harms

## 5.1: Excluded data from the audit

I did not permanently remove any data, I just filtered the dataset to
Bahrain , that was after I made sure all 24 races where there ,then I
filtered again to check for Lando and Piastri and looked through that
filtered data set to see if I have the things I needed but that was just
testing to see if i had the important things I have not decided which or
if I will be excluding any data for my final analysis. Even if I do it
would be at most the other drivers I don’t need but i would delete them
ill just filter

## 5.2: Who could be harmed

This could negatively affect the drivers in question since my research
isn’t considering every single detail and is taking out weird laps so
people could ignore that the research doesn’t account for every little
things and could be misused by fans or the media to make one driver look
worse than the other

## 5.3: Unreleased working data

I will not publish the raw telemetry data because I am still unsure if I
have the permission to redistribute it but i plan on sharing my R code.

------------------------------------------------------------------------

# 6: Data Stewardship

**Where it lives.** It is currently stored on my GitHub in my
Final-Project-Yehoida-Marshall and on my computer

**Who maintains it.** I will maintain the project , since i plan to
include it in my portfolio when/ if I apply for jobs in Formula 1, I
tend to keep it accessible and update it when necessary

**Formats and dependencies.** My project is using R and Markdown files
so it should still be readable in the future but the code does depend on
the R packages and the OpenF1 API so, the changes could affect whether
the code would still work in 2036

**Lifespan.** I plan to keep this project beyond the course becasue I
want to include it in my portfolio for future job applications in
Formula 1. Since it focuses on the 2025 season, the research will remain
a historical comparison, so may be only the code will need some updating
and dependencies to keep it working.

------------------------------------------------------------------------

# 7: Use of AI

**AI log:** [AI-log.md](log/AI-log.md)

I used AI, specifically CHATGPT (GPT-6). I used it to breakdown the
questions (basically makes a checklist for me for everything i have to
do). I used it to audit my data sources because I had started before we
learnt about API sourcing in class so i used it to help me retrieve the
data. It helped me with code eg. one of my data sets was a repo that
worked with fully python so used AI to help me know how to get it in R,
way too many errors so I did not use that source. I also used it as a
thinking ahead tool so not just looking at the variables I had but also
what are things i have to consider before full committing to just this
one data source. I also used it to summarize the licence text from the
data source.

------------------------------------------------------------------------

# 8: Session information

    R version 4.6.1 (2026-06-24)
    Platform: aarch64-apple-darwin23
    Running under: macOS Tahoe 26.6.2

    Matrix products: default
    BLAS:   /Library/Frameworks/R.framework/Versions/4.6/Resources/lib/libRblas.0.dylib 
    LAPACK: /Library/Frameworks/R.framework/Versions/4.6/Resources/lib/libRlapack.dylib;  LAPACK version 3.12.1

    locale:
    [1] en_US.UTF-8/en_US.UTF-8/en_US.UTF-8/C/en_US.UTF-8/en_US.UTF-8

    time zone: America/Moncton
    tzcode source: internal

    attached base packages:
    [1] stats     graphics  grDevices utils     datasets  methods   base     

    other attached packages:
     [1] jsonlite_2.0.0  lubridate_1.9.5 forcats_1.0.1   stringr_1.6.0  
     [5] dplyr_1.2.1     purrr_1.2.2     readr_2.2.0     tidyr_1.3.2    
     [9] tibble_3.3.1    ggplot2_4.0.3   tidyverse_2.0.0

    loaded via a namespace (and not attached):
     [1] gtable_0.3.6       compiler_4.6.1     tidyselect_1.2.1   scales_1.4.0      
     [5] yaml_2.3.12        fastmap_1.2.0      R6_2.6.1           generics_0.1.4    
     [9] knitr_1.52         pillar_1.11.1      RColorBrewer_1.1-3 tzdb_0.5.0        
    [13] rlang_1.3.0        stringi_1.8.9      xfun_0.61          S7_0.2.2          
    [17] otel_0.2.0         timechange_0.4.0   cli_3.6.6          withr_3.0.3       
    [21] magrittr_2.0.5     digest_0.6.39      grid_4.6.1         rstudioapi_0.19.0 
    [25] hms_1.1.4          lifecycle_1.0.5    vctrs_0.7.3        evaluate_1.0.5    
    [29] glue_1.8.1         farver_2.1.2       rmarkdown_2.32     tools_4.6.1       
    [33] pkgconfig_2.0.3    htmltools_0.5.9   
