# likeapj.cls v1.1 January 18, 2019
LaTex style file for AAS journals 

The purpose of this file is to reproduce most faithfully the current look of all AAS journals. As such, it should be used together with the **likeapj.bst** companion bibliography style file and bibtex. 

## Brief instructions and suggestions
Items 1 and 2 take you a long way towards the desired result, so are pretty essential. The remaining items can provide some impressive improvements but you may feel you don't want to bother.

### 1. Note:
This file should be used together with **likeapj.bst** bibliography style file and **bibtex**, or references will not be properly hyperlinked.
### 2. Items to place before \begin{document}

  - (a) \documentclass[twocolumn, apj]{likeapj}       
                                              
(replace apj with one of                      
 apjs, aj, pasp, apjl as needed).             
                                              
option noj gives no journal in running head,  
only authors.
**WARNING: Options other than twocolumn have not been tested and may produce unexpected results.**

  - (b) 

% This is a hack found on the web to link only year in citations, per AAS look
\usepackage{etoolbox}
\makeatletter

% Patch case where name and year are separated by aysep
\patchcmd{\NAT@citex}

  {\@citea\NAT@hyper@{%
  
     \NAT@nmfmt{\NAT@nm}%
     
     \hyper@natlinkbreak{\NAT@aysep\NAT@spacechar}{\@citeb\@extra@b@citeb}%
     
     \NAT@date}}
     
  {\@citea\NAT@nmfmt{\NAT@nm}%
  
   \NAT@aysep\NAT@spacechar\NAT@hyper@{\NAT@date}}{}{}

% Patch case where name and year are separated by opening bracket

\patchcmd{\NAT@citex}

  {\@citea\NAT@hyper@{%
  
     \NAT@nmfmt{\NAT@nm}%
     
     \hyper@natlinkbreak{\NAT@spacechar\NAT@@open\if*#1*\else#1\NAT@spacechar\fi}%
     
       {\@citeb\@extra@b@citeb}%
     \NAT@date}}
     
  {\@citea\NAT@nmfmt{\NAT@nm}%
  
   \NAT@spacechar\NAT@@open\if*#1*\else#1\NAT@spacechar\fi\NAT@hyper@{\NAT@date}}
   
  {}{}

  \makeatother


  - (c) \usepackage{mathptmx}                         
This gets consistent AAS-looking Times fonts both for text and math. 
  - (d) [some or no dates]                         
\received{\today}                              
\revised{2019 Jan 32}                                    
\accepted{}                                   
\published{}                                  
                                              
### 3.Tables 

  - (a) Style maintains full functionality for AASTEX6.1 tables, including longtable. Default row spacing is probably too large; you may want to consider using something like
                                              
\renewcommand{\arraystretch}{0.85}            
                                              
right before the table LaTex code to control this.                                            

  - (b) Table comments                                        
If the table comments use a different font size compared to the actual table values, include a new declaration right before the command
\tablecomments, e.g.                          
                                              
\tabletypesize{\small}                        
\tablecomments{                                   

### 4. Appendix                                   
Style has two-column as default. To get the Appendix section heading correct, put **\\** right before the appendix section title text.           

### 5. References to AstL - AN
Astronomy Letters (AstL) and Astronomische Nachrichten (AN) need \anl and \anach in the journal entry of the bib file.


## Fix/modification list - Summary January 18, 2019
63 *individual* items; condensed summary in 28 items.
1. New options for running head for four AAS journals.
2. Two column appendix.
3. Appendix section titles ``Appendix A'' etc.
4. Page number at center & bottom.
5. Running head font styles for four journals and short authors.
6. Front page title lower case, bold.
7. Eliminate forced white space after abstract.
8. Front page authors font.
9. Abstract: no indentation, centered, smaller width; lower case title.
10. Keywords → Key words; width matched to abstract; adjust space to Introduction below.
11. Footnote with hrule.
12. Decrease footnote separation from main text.
13. Footnote number not indented.
14. Section title & number bold, lower case.
15. Subsection title & number in italics; lower case.
16. References: font fix, two-column, continue from end of text.
17. References title, centered over first column.
18. Footnote font.
19. Facilities font and no skip.
20. Bookmarked sections.
21. Table title centered; no italics; skip adjusted.
22. Table ''Note'' bold.
23. No big skip before ''Received etc.''
24. ''Received..., revised'', font/case adjusted.
25. Frontpage email not footnote, blue link in author list.
26. Several skips/spaces adjusted.
27. Readjust text width, columnsep, text height, title width
28. References to Astronomy Letters (AstL) and Astronomische Nachrichten (AN) will be correctly hyperlinked and shown if \anach and \anl are used in bib file.
