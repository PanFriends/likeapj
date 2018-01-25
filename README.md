# likeapj
 LaTeX class and bibliography style files for AAS journals.
 
 - likeapj.cls v1.0, 25 January 2018
 - likeapj.bst v1.0, 25 January 2018
 
 
 The latest version is available here.

 Use together with likeapj.bst to get reference list
 correctly color-coded and hyperlinked.

 **Copyright 2017-1018 Panayiotis Tzanavaris**

 This work may be distributed and/or modified under the
 conditions of the LaTeX Project Public License, either version 1.3
 of this license or (at your option) any later version.
 The latest version of this license is in
   http://www.latex-project.org/lppl.txt
 and version 1.3 or later is part of all distributions of LaTeX
 version 2005/12/01 or later.

 This work has the LPPL maintenance status `maintained'.
 
 The Current Maintainer of this work is Panayiotis Tzanavaris.

 This work consists of the files likeapj.cls, likeapj.bst.
 
 
 ## likeapj.cls
 This builds upon:

 AASTeX61.cls                                  
 October 5, 2016                               
 December 28, 2016 (bug fix on .bib file)      
 Copyright 2016 American Astronomical Society  
 

 Jan. 25, 2018:                                                  
 Includes 57 fixes/modifications to match AAS journals published look as of Jan. 2018 by                                           
 Panayiotis Tzanavaris                                           
 panayiotis.tzanavaris-1@nasa.gov                                
 anax93@yahoo.com                                                

 ## List of modifications/fixes:
  (PT) 01/24/2018: 57 *individual* items; overall summary
 in 26 items:

1. New options for running head for four AAS journals.
2. Two column appendix.
3. Appendix section titles ``Appendix A'' etc.
4. Page number at center & bottom.
5. Running head font styles for four journals and short authors.
6. Front page title lower case, bold.
7. Eliminate forced white space after abstract.
8. Front page authors font.
9. Abstract: no indentation, centered, smaller width; lower case title.
10. Keywords → Key words; width matched to abstract.
11. Footnote with hrule.
12. Decrease footnote separation from main text.
13. Footnote number not indented.
14. Section title & number bold, lower case.
15. Subsection title & number italics, lower case.
16. References: font, two-column, continue from end of text.
17. References title, centered over first column.
18. Footnote font.
19. Facilities font and no skip.
20. Bookmarked sections.
21. Table title centered; no italics; skip adjusted.
22. Table ``Note'' bold.
23. No big skip before ``Received etc.''
24. ``Received..., revised'', font/case adjusted.
25. Frontpage email not footnote, blue link in author list.
26. Several skips/spaces adjusted.

                                              
## INSTRUCTIONS FOR USE
In your LaTex source file:

## 1:
At top:                                             
**\documentclass[twocolumn, apj]{likeapj}**      
                                              
(replace apj with one of                      
 **apjs, aj, pasp, apjl** as needed).             
                                              
option **noj** gives no journal in running head,  
only authors 

## 2:
**\usepackage{mathptmx}**                        
This gets times fonts both for text and math. 

## 3:  
[some or no dates]

**\received{\today}                              
\revised{}                                    
\accepted{}                  
\published{}**  

## 4: Table comments 
If the table comments use a different font   
size compared to the actual table values,     
a new declaration is needed right before the  
\tablecomments, e.g.                          
                                              
\tabletypesize{\small}                        
\tablecomments{ 

## 5: Appendix
Style has two-column as default.             
To get the Appendix section heading correct, 
put **\\\\** right before the appendix section     
title text.

## 6: 
In order to link only the year in          
citations, uncomment and put the following    
in the package declaration area of the        
LaTex source:

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



                                             
                                             








