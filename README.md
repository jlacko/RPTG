# A simple report template for R
Geared towards corporate (i.e. not academic) use.

My work is unlikely to appear in any reputable journals, and so I have little need for Elsevier or PeerJ templates, but I felt the need to address several issues specific to the corporate environment.  

I have therefore compiled a simple r markdown template, together with an accompanying *Report.tex* file to create simple yet (I hope) elegant pdf reports.

## A few features I found advantageous:  
* I like even my intermediate reports to be read only, hence my output is by choice *\*.pdf*, not the more common MS Word.  
* I have struggled with finding a sans serif font that would be easily available in both Linux and Windows environment, after a while I settled on [Roboto](https://fonts.google.com/specimen/Roboto). The usual suspects Arial and Helvetica turned out to be unreliable in this regard.
* I have included LaTeX macros for the more common table operations, so that the report does not fail on the dreaded *Environment XYZ not defined* error.

```r  
\usepackage{longtable}
\usepackage{booktabs}
\usepackage{array}
\usepackage{multirow}
\usepackage[table]{xcolor}
\usepackage{wrapfig}
\usepackage{float}
\usepackage{colortbl}
\usepackage{pdflscape}
\usepackage{tabu}
\usepackage{threeparttable}
```
* My reports often take a life of their own once out of my hands; to improve version control I have created 'project', 'version' and 'date' fields in the front matter of my report, together with corresponding code in my *Report.tex* template which places the project name, short form SHA of the last commit and system date in the left hand footer of each page (on the right hand side is page number).  
This way I can be certain at which iteration of my analysis a report was generated. I found this information valuable for intermediary reports, for final version it is easily removed.


```r
project: "`r basename(system('git rev-parse --show-toplevel', intern=TRUE))`"
version: "`r system('git rev-parse --short=7 HEAD', intern=TRUE)`"
date:    "`r format(Sys.time(), '%d-%m-%Y')`"
```  
![](footer.png)

As I needed a text with Czech accents the placeholer "report" is not the usual *Lorem ipsum*, but a Czech translation of Cicero's first [Catiline Oration](https://en.wikipedia.org/wiki/Catiline_Orations#Oratio_in_Catilinam_Prima_in_Senatu_Habita) (by the way: the original *Lorem Ipsum* also comes from Cicero - [*De finibus bonorum et malorum*](https://en.wikipedia.org/wiki/De_finibus_bonorum_et_malorum)).
