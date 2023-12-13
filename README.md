\documentclass[11pt]{article}

    \usepackage[breakable]{tcolorbox}
    \usepackage{parskip} % Stop auto-indenting (to mimic markdown behaviour)
    

    % Basic figure setup, for now with no caption control since it's done
    % automatically by Pandoc (which extracts ![](path) syntax from Markdown).
    \usepackage{graphicx}
    % Maintain compatibility with old templates. Remove in nbconvert 6.0
    \let\Oldincludegraphics\includegraphics
    % Ensure that by default, figures have no caption (until we provide a
    % proper Figure object with a Caption API and a way to capture that
    % in the conversion process - todo).
    \usepackage{caption}
    \DeclareCaptionFormat{nocaption}{}
    \captionsetup{format=nocaption,aboveskip=0pt,belowskip=0pt}

    \usepackage{float}
    \floatplacement{figure}{H} % forces figures to be placed at the correct location
    \usepackage{xcolor} % Allow colors to be defined
    \usepackage{enumerate} % Needed for markdown enumerations to work
    \usepackage{geometry} % Used to adjust the document margins
    \usepackage{amsmath} % Equations
    \usepackage{amssymb} % Equations
    \usepackage{textcomp} % defines textquotesingle
    % Hack from http://tex.stackexchange.com/a/47451/13684:
    \AtBeginDocument{%
        \def\PYZsq{\textquotesingle}% Upright quotes in Pygmentized code
    }
    \usepackage{upquote} % Upright quotes for verbatim code
    \usepackage{eurosym} % defines \euro

    \usepackage{iftex}
    \ifPDFTeX
        \usepackage[T1]{fontenc}
        \IfFileExists{alphabeta.sty}{
              \usepackage{alphabeta}
          }{
              \usepackage[mathletters]{ucs}
              \usepackage[utf8x]{inputenc}
          }
    \else
        \usepackage{fontspec}
        \usepackage{unicode-math}
    \fi

    \usepackage{fancyvrb} % verbatim replacement that allows latex
    \usepackage{grffile} % extends the file name processing of package graphics
                         % to support a larger range
    \makeatletter % fix for old versions of grffile with XeLaTeX
    \@ifpackagelater{grffile}{2019/11/01}
    {
      % Do nothing on new versions
    }
    {
      \def\Gread@@xetex#1{%
        \IfFileExists{"\Gin@base".bb}%
        {\Gread@eps{\Gin@base.bb}}%
        {\Gread@@xetex@aux#1}%
      }
    }
    \makeatother
    \usepackage[Export]{adjustbox} % Used to constrain images to a maximum size
    \adjustboxset{max size={0.9\linewidth}{0.9\paperheight}}

    % The hyperref package gives us a pdf with properly built
    % internal navigation ('pdf bookmarks' for the table of contents,
    % internal cross-reference links, web links for URLs, etc.)
    \usepackage{hyperref}
    % The default LaTeX title has an obnoxious amount of whitespace. By default,
    % titling removes some of it. It also provides customization options.
    \usepackage{titling}
    \usepackage{longtable} % longtable support required by pandoc >1.10
    \usepackage{booktabs}  % table support for pandoc > 1.12.2
    \usepackage{array}     % table support for pandoc >= 2.11.3
    \usepackage{calc}      % table minipage width calculation for pandoc >= 2.11.1
    \usepackage[inline]{enumitem} % IRkernel/repr support (it uses the enumerate* environment)
    \usepackage[normalem]{ulem} % ulem is needed to support strikethroughs (\sout)
                                % normalem makes italics be italics, not underlines
    \usepackage{mathrsfs}
    

    
    % Colors for the hyperref package
    \definecolor{urlcolor}{rgb}{0,.145,.698}
    \definecolor{linkcolor}{rgb}{.71,0.21,0.01}
    \definecolor{citecolor}{rgb}{.12,.54,.11}

    % ANSI colors
    \definecolor{ansi-black}{HTML}{3E424D}
    \definecolor{ansi-black-intense}{HTML}{282C36}
    \definecolor{ansi-red}{HTML}{E75C58}
    \definecolor{ansi-red-intense}{HTML}{B22B31}
    \definecolor{ansi-green}{HTML}{00A250}
    \definecolor{ansi-green-intense}{HTML}{007427}
    \definecolor{ansi-yellow}{HTML}{DDB62B}
    \definecolor{ansi-yellow-intense}{HTML}{B27D12}
    \definecolor{ansi-blue}{HTML}{208FFB}
    \definecolor{ansi-blue-intense}{HTML}{0065CA}
    \definecolor{ansi-magenta}{HTML}{D160C4}
    \definecolor{ansi-magenta-intense}{HTML}{A03196}
    \definecolor{ansi-cyan}{HTML}{60C6C8}
    \definecolor{ansi-cyan-intense}{HTML}{258F8F}
    \definecolor{ansi-white}{HTML}{C5C1B4}
    \definecolor{ansi-white-intense}{HTML}{A1A6B2}
    \definecolor{ansi-default-inverse-fg}{HTML}{FFFFFF}
    \definecolor{ansi-default-inverse-bg}{HTML}{000000}

    % common color for the border for error outputs.
    \definecolor{outerrorbackground}{HTML}{FFDFDF}

    % commands and environments needed by pandoc snippets
    % extracted from the output of `pandoc -s`
    \providecommand{\tightlist}{%
      \setlength{\itemsep}{0pt}\setlength{\parskip}{0pt}}
    \DefineVerbatimEnvironment{Highlighting}{Verbatim}{commandchars=\\\{\}}
    % Add ',fontsize=\small' for more characters per line
    \newenvironment{Shaded}{}{}
    \newcommand{\KeywordTok}[1]{\textcolor[rgb]{0.00,0.44,0.13}{\textbf{{#1}}}}
    \newcommand{\DataTypeTok}[1]{\textcolor[rgb]{0.56,0.13,0.00}{{#1}}}
    \newcommand{\DecValTok}[1]{\textcolor[rgb]{0.25,0.63,0.44}{{#1}}}
    \newcommand{\BaseNTok}[1]{\textcolor[rgb]{0.25,0.63,0.44}{{#1}}}
    \newcommand{\FloatTok}[1]{\textcolor[rgb]{0.25,0.63,0.44}{{#1}}}
    \newcommand{\CharTok}[1]{\textcolor[rgb]{0.25,0.44,0.63}{{#1}}}
    \newcommand{\StringTok}[1]{\textcolor[rgb]{0.25,0.44,0.63}{{#1}}}
    \newcommand{\CommentTok}[1]{\textcolor[rgb]{0.38,0.63,0.69}{\textit{{#1}}}}
    \newcommand{\OtherTok}[1]{\textcolor[rgb]{0.00,0.44,0.13}{{#1}}}
    \newcommand{\AlertTok}[1]{\textcolor[rgb]{1.00,0.00,0.00}{\textbf{{#1}}}}
    \newcommand{\FunctionTok}[1]{\textcolor[rgb]{0.02,0.16,0.49}{{#1}}}
    \newcommand{\RegionMarkerTok}[1]{{#1}}
    \newcommand{\ErrorTok}[1]{\textcolor[rgb]{1.00,0.00,0.00}{\textbf{{#1}}}}
    \newcommand{\NormalTok}[1]{{#1}}

    % Additional commands for more recent versions of Pandoc
    \newcommand{\ConstantTok}[1]{\textcolor[rgb]{0.53,0.00,0.00}{{#1}}}
    \newcommand{\SpecialCharTok}[1]{\textcolor[rgb]{0.25,0.44,0.63}{{#1}}}
    \newcommand{\VerbatimStringTok}[1]{\textcolor[rgb]{0.25,0.44,0.63}{{#1}}}
    \newcommand{\SpecialStringTok}[1]{\textcolor[rgb]{0.73,0.40,0.53}{{#1}}}
    \newcommand{\ImportTok}[1]{{#1}}
    \newcommand{\DocumentationTok}[1]{\textcolor[rgb]{0.73,0.13,0.13}{\textit{{#1}}}}
    \newcommand{\AnnotationTok}[1]{\textcolor[rgb]{0.38,0.63,0.69}{\textbf{\textit{{#1}}}}}
    \newcommand{\CommentVarTok}[1]{\textcolor[rgb]{0.38,0.63,0.69}{\textbf{\textit{{#1}}}}}
    \newcommand{\VariableTok}[1]{\textcolor[rgb]{0.10,0.09,0.49}{{#1}}}
    \newcommand{\ControlFlowTok}[1]{\textcolor[rgb]{0.00,0.44,0.13}{\textbf{{#1}}}}
    \newcommand{\OperatorTok}[1]{\textcolor[rgb]{0.40,0.40,0.40}{{#1}}}
    \newcommand{\BuiltInTok}[1]{{#1}}
    \newcommand{\ExtensionTok}[1]{{#1}}
    \newcommand{\PreprocessorTok}[1]{\textcolor[rgb]{0.74,0.48,0.00}{{#1}}}
    \newcommand{\AttributeTok}[1]{\textcolor[rgb]{0.49,0.56,0.16}{{#1}}}
    \newcommand{\InformationTok}[1]{\textcolor[rgb]{0.38,0.63,0.69}{\textbf{\textit{{#1}}}}}
    \newcommand{\WarningTok}[1]{\textcolor[rgb]{0.38,0.63,0.69}{\textbf{\textit{{#1}}}}}


    % Define a nice break command that doesn't care if a line doesn't already
    % exist.
    \def\br{\hspace*{\fill} \\* }
    % Math Jax compatibility definitions
    \def\gt{>}
    \def\lt{<}
    \let\Oldtex\TeX
    \let\Oldlatex\LaTeX
    \renewcommand{\TeX}{\textrm{\Oldtex}}
    \renewcommand{\LaTeX}{\textrm{\Oldlatex}}
    % Document parameters
    % Document title
    \title{Dimensionality\_Reduction\_Technique\_Principal\_Component\_Analysis}
    
    
    
    
    
% Pygments definitions
\makeatletter
\def\PY@reset{\let\PY@it=\relax \let\PY@bf=\relax%
    \let\PY@ul=\relax \let\PY@tc=\relax%
    \let\PY@bc=\relax \let\PY@ff=\relax}
\def\PY@tok#1{\csname PY@tok@#1\endcsname}
\def\PY@toks#1+{\ifx\relax#1\empty\else%
    \PY@tok{#1}\expandafter\PY@toks\fi}
\def\PY@do#1{\PY@bc{\PY@tc{\PY@ul{%
    \PY@it{\PY@bf{\PY@ff{#1}}}}}}}
\def\PY#1#2{\PY@reset\PY@toks#1+\relax+\PY@do{#2}}

\@namedef{PY@tok@w}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.73,0.73}{##1}}}
\@namedef{PY@tok@c}{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.24,0.48,0.48}{##1}}}
\@namedef{PY@tok@cp}{\def\PY@tc##1{\textcolor[rgb]{0.61,0.40,0.00}{##1}}}
\@namedef{PY@tok@k}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@kp}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@kt}{\def\PY@tc##1{\textcolor[rgb]{0.69,0.00,0.25}{##1}}}
\@namedef{PY@tok@o}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@ow}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.67,0.13,1.00}{##1}}}
\@namedef{PY@tok@nb}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@nf}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,1.00}{##1}}}
\@namedef{PY@tok@nc}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,1.00}{##1}}}
\@namedef{PY@tok@nn}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,1.00}{##1}}}
\@namedef{PY@tok@ne}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.80,0.25,0.22}{##1}}}
\@namedef{PY@tok@nv}{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\@namedef{PY@tok@no}{\def\PY@tc##1{\textcolor[rgb]{0.53,0.00,0.00}{##1}}}
\@namedef{PY@tok@nl}{\def\PY@tc##1{\textcolor[rgb]{0.46,0.46,0.00}{##1}}}
\@namedef{PY@tok@ni}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.44,0.44,0.44}{##1}}}
\@namedef{PY@tok@na}{\def\PY@tc##1{\textcolor[rgb]{0.41,0.47,0.13}{##1}}}
\@namedef{PY@tok@nt}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@nd}{\def\PY@tc##1{\textcolor[rgb]{0.67,0.13,1.00}{##1}}}
\@namedef{PY@tok@s}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@sd}{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@si}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.64,0.35,0.47}{##1}}}
\@namedef{PY@tok@se}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.67,0.36,0.12}{##1}}}
\@namedef{PY@tok@sr}{\def\PY@tc##1{\textcolor[rgb]{0.64,0.35,0.47}{##1}}}
\@namedef{PY@tok@ss}{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\@namedef{PY@tok@sx}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@m}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@gh}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,0.50}{##1}}}
\@namedef{PY@tok@gu}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.50,0.00,0.50}{##1}}}
\@namedef{PY@tok@gd}{\def\PY@tc##1{\textcolor[rgb]{0.63,0.00,0.00}{##1}}}
\@namedef{PY@tok@gi}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.52,0.00}{##1}}}
\@namedef{PY@tok@gr}{\def\PY@tc##1{\textcolor[rgb]{0.89,0.00,0.00}{##1}}}
\@namedef{PY@tok@ge}{\let\PY@it=\textit}
\@namedef{PY@tok@gs}{\let\PY@bf=\textbf}
\@namedef{PY@tok@ges}{\let\PY@bf=\textbf\let\PY@it=\textit}
\@namedef{PY@tok@gp}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,0.50}{##1}}}
\@namedef{PY@tok@go}{\def\PY@tc##1{\textcolor[rgb]{0.44,0.44,0.44}{##1}}}
\@namedef{PY@tok@gt}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.27,0.87}{##1}}}
\@namedef{PY@tok@err}{\def\PY@bc##1{{\setlength{\fboxsep}{\string -\fboxrule}\fcolorbox[rgb]{1.00,0.00,0.00}{1,1,1}{\strut ##1}}}}
\@namedef{PY@tok@kc}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@kd}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@kn}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@kr}{\let\PY@bf=\textbf\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@bp}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.50,0.00}{##1}}}
\@namedef{PY@tok@fm}{\def\PY@tc##1{\textcolor[rgb]{0.00,0.00,1.00}{##1}}}
\@namedef{PY@tok@vc}{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\@namedef{PY@tok@vg}{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\@namedef{PY@tok@vi}{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\@namedef{PY@tok@vm}{\def\PY@tc##1{\textcolor[rgb]{0.10,0.09,0.49}{##1}}}
\@namedef{PY@tok@sa}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@sb}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@sc}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@dl}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@s2}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@sh}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@s1}{\def\PY@tc##1{\textcolor[rgb]{0.73,0.13,0.13}{##1}}}
\@namedef{PY@tok@mb}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@mf}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@mh}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@mi}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@il}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@mo}{\def\PY@tc##1{\textcolor[rgb]{0.40,0.40,0.40}{##1}}}
\@namedef{PY@tok@ch}{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.24,0.48,0.48}{##1}}}
\@namedef{PY@tok@cm}{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.24,0.48,0.48}{##1}}}
\@namedef{PY@tok@cpf}{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.24,0.48,0.48}{##1}}}
\@namedef{PY@tok@c1}{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.24,0.48,0.48}{##1}}}
\@namedef{PY@tok@cs}{\let\PY@it=\textit\def\PY@tc##1{\textcolor[rgb]{0.24,0.48,0.48}{##1}}}

\def\PYZbs{\char`\\}
\def\PYZus{\char`\_}
\def\PYZob{\char`\{}
\def\PYZcb{\char`\}}
\def\PYZca{\char`\^}
\def\PYZam{\char`\&}
\def\PYZlt{\char`\<}
\def\PYZgt{\char`\>}
\def\PYZsh{\char`\#}
\def\PYZpc{\char`\%}
\def\PYZdl{\char`\$}
\def\PYZhy{\char`\-}
\def\PYZsq{\char`\'}
\def\PYZdq{\char`\"}
\def\PYZti{\char`\~}
% for compatibility with earlier versions
\def\PYZat{@}
\def\PYZlb{[}
\def\PYZrb{]}
\makeatother


    % For linebreaks inside Verbatim environment from package fancyvrb.
    \makeatletter
        \newbox\Wrappedcontinuationbox
        \newbox\Wrappedvisiblespacebox
        \newcommand*\Wrappedvisiblespace {\textcolor{red}{\textvisiblespace}}
        \newcommand*\Wrappedcontinuationsymbol {\textcolor{red}{\llap{\tiny$\m@th\hookrightarrow$}}}
        \newcommand*\Wrappedcontinuationindent {3ex }
        \newcommand*\Wrappedafterbreak {\kern\Wrappedcontinuationindent\copy\Wrappedcontinuationbox}
        % Take advantage of the already applied Pygments mark-up to insert
        % potential linebreaks for TeX processing.
        %        {, <, #, %, $, ' and ": go to next line.
        %        _, }, ^, &, >, - and ~: stay at end of broken line.
        % Use of \textquotesingle for straight quote.
        \newcommand*\Wrappedbreaksatspecials {%
            \def\PYGZus{\discretionary{\char`\_}{\Wrappedafterbreak}{\char`\_}}%
            \def\PYGZob{\discretionary{}{\Wrappedafterbreak\char`\{}{\char`\{}}%
            \def\PYGZcb{\discretionary{\char`\}}{\Wrappedafterbreak}{\char`\}}}%
            \def\PYGZca{\discretionary{\char`\^}{\Wrappedafterbreak}{\char`\^}}%
            \def\PYGZam{\discretionary{\char`\&}{\Wrappedafterbreak}{\char`\&}}%
            \def\PYGZlt{\discretionary{}{\Wrappedafterbreak\char`\<}{\char`\<}}%
            \def\PYGZgt{\discretionary{\char`\>}{\Wrappedafterbreak}{\char`\>}}%
            \def\PYGZsh{\discretionary{}{\Wrappedafterbreak\char`\#}{\char`\#}}%
            \def\PYGZpc{\discretionary{}{\Wrappedafterbreak\char`\%}{\char`\%}}%
            \def\PYGZdl{\discretionary{}{\Wrappedafterbreak\char`\$}{\char`\$}}%
            \def\PYGZhy{\discretionary{\char`\-}{\Wrappedafterbreak}{\char`\-}}%
            \def\PYGZsq{\discretionary{}{\Wrappedafterbreak\textquotesingle}{\textquotesingle}}%
            \def\PYGZdq{\discretionary{}{\Wrappedafterbreak\char`\"}{\char`\"}}%
            \def\PYGZti{\discretionary{\char`\~}{\Wrappedafterbreak}{\char`\~}}%
        }
        % Some characters . , ; ? ! / are not pygmentized.
        % This macro makes them "active" and they will insert potential linebreaks
        \newcommand*\Wrappedbreaksatpunct {%
            \lccode`\~`\.\lowercase{\def~}{\discretionary{\hbox{\char`\.}}{\Wrappedafterbreak}{\hbox{\char`\.}}}%
            \lccode`\~`\,\lowercase{\def~}{\discretionary{\hbox{\char`\,}}{\Wrappedafterbreak}{\hbox{\char`\,}}}%
            \lccode`\~`\;\lowercase{\def~}{\discretionary{\hbox{\char`\;}}{\Wrappedafterbreak}{\hbox{\char`\;}}}%
            \lccode`\~`\:\lowercase{\def~}{\discretionary{\hbox{\char`\:}}{\Wrappedafterbreak}{\hbox{\char`\:}}}%
            \lccode`\~`\?\lowercase{\def~}{\discretionary{\hbox{\char`\?}}{\Wrappedafterbreak}{\hbox{\char`\?}}}%
            \lccode`\~`\!\lowercase{\def~}{\discretionary{\hbox{\char`\!}}{\Wrappedafterbreak}{\hbox{\char`\!}}}%
            \lccode`\~`\/\lowercase{\def~}{\discretionary{\hbox{\char`\/}}{\Wrappedafterbreak}{\hbox{\char`\/}}}%
            \catcode`\.\active
            \catcode`\,\active
            \catcode`\;\active
            \catcode`\:\active
            \catcode`\?\active
            \catcode`\!\active
            \catcode`\/\active
            \lccode`\~`\~
        }
    \makeatother

    \let\OriginalVerbatim=\Verbatim
    \makeatletter
    \renewcommand{\Verbatim}[1][1]{%
        %\parskip\z@skip
        \sbox\Wrappedcontinuationbox {\Wrappedcontinuationsymbol}%
        \sbox\Wrappedvisiblespacebox {\FV@SetupFont\Wrappedvisiblespace}%
        \def\FancyVerbFormatLine ##1{\hsize\linewidth
            \vtop{\raggedright\hyphenpenalty\z@\exhyphenpenalty\z@
                \doublehyphendemerits\z@\finalhyphendemerits\z@
                \strut ##1\strut}%
        }%
        % If the linebreak is at a space, the latter will be displayed as visible
        % space at end of first line, and a continuation symbol starts next line.
        % Stretch/shrink are however usually zero for typewriter font.
        \def\FV@Space {%
            \nobreak\hskip\z@ plus\fontdimen3\font minus\fontdimen4\font
            \discretionary{\copy\Wrappedvisiblespacebox}{\Wrappedafterbreak}
            {\kern\fontdimen2\font}%
        }%

        % Allow breaks at special characters using \PYG... macros.
        \Wrappedbreaksatspecials
        % Breaks at punctuation characters . , ; ? ! and / need catcode=\active
        \OriginalVerbatim[#1,codes*=\Wrappedbreaksatpunct]%
    }
    \makeatother

    % Exact colors from NB
    \definecolor{incolor}{HTML}{303F9F}
    \definecolor{outcolor}{HTML}{D84315}
    \definecolor{cellborder}{HTML}{CFCFCF}
    \definecolor{cellbackground}{HTML}{F7F7F7}

    % prompt
    \makeatletter
    \newcommand{\boxspacing}{\kern\kvtcb@left@rule\kern\kvtcb@boxsep}
    \makeatother
    \newcommand{\prompt}[4]{
        {\ttfamily\llap{{\color{#2}[#3]:\hspace{3pt}#4}}\vspace{-\baselineskip}}
    }
    

    
    % Prevent overflowing lines due to hard-to-break entities
    \sloppy
    % Setup hyperref package
    \hypersetup{
      breaklinks=true,  % so long urls are correctly broken across lines
      colorlinks=true,
      urlcolor=urlcolor,
      linkcolor=linkcolor,
      citecolor=citecolor,
      }
    % Slightly bigger margins than the latex defaults
    
    \geometry{verbose,tmargin=1in,bmargin=1in,lmargin=1in,rmargin=1in}
    
    

\begin{document}
    
    \maketitle
    
    

    
    \hypertarget{dimensionality-reduction-technique-principal-component-analysis-pca}{%


Jasmine Sellers\(^1\)

\(^1\)University of Washington undergraduate

\textbf{Abstract}: This paper provides a comprehensive overview of a
dimensionality reduction technique called principal component analysis
(PCA). The investigation begins with the mathematical underpinnings of
PCA, discussing eigenvalues, eigenvectors, and data transformation into
a lower-dimensional space. The work is structured with an introduction
to the main steps of PCA supplemented with a toy example.

The paper then introduces a data visualization code utilizing PCA. This
drafting code connects theory and practice to explore datasets, applying
PCA to observe visualizations in reduced-dimensional spaces and gain
insights into data trends and relationships.

\textbf{Keywords}: dimensionality reduction, principal component
analysis (PCA), covariance, variance, eigenvector, eigenvalue, feature
vector 

\textbf{Introduction}
Dimensionality reduction
techniques are methods that reduce the dimensions in a dataset while
retaining key characteristics of the data. These techniques are applied
in domains such as machine learning, data analysis, and data
visualization. It tackles several key issues including
higher-dimensional data, noise, and complexity. Some dimensionality
reduction techniques include neural networks, matrix factorization, and
non-metric multidimensional scaling. This paper will concentrate on
principal component analysis (PCA), a commonly used method which
utilizes linear algebra in the computation of the covariance matrix and
principal components.

    \textbf{Principal Component Analysis} Principal component analysis (PCA)
is a standard tool used in data analysis due to its non-parametric
method for emphasizing the most significant information from
high-dimensional datasets. The primary goal of PCA is to transform the
data to lower dimensions while preserving its variability. This paper
will use an example alongside the main formulas to explain principal
component analysis.

I will use the following generic example to walk through the main steps
of PCA where X, Y, Z represent variables and \(x_1\), \(x_2\), \ldots{}
represent values of the corresponding variables.


\begin{longtable}[]{@{}lll@{}}
\toprule
X & Y & Z\tabularnewline
\midrule
\endhead
\(x_1\) & \(y_1\) & \(z_1\)\tabularnewline
\(x_2\) & \(y_2\) & \(z_2\)\tabularnewline
\(x_3\) & \(y_3\) & \(z_3\)\tabularnewline
\bottomrule
\end{longtable}

\newpage
\begin{enumerate}
\def\labelenumi{\arabic{enumi}.}
\tightlist
\item
  \textbf{Standardization} 
  \newline The standardization of data in PCA uses the
  following formulas:
\end{enumerate}

\begin{itemize}
\tightlist
\item
  \(\text{mean} = \frac{\text{sum of the terms}}{\text{total number of terms}}\)
\item
  \(\text{standard deviation (SD)} = \sqrt{\sum_{i=1}^n \frac{(x_i-mean)^2}{n}}\)
\item
  \(\text{z} = \frac{\text{value - mean}}{\text{standard deviation}}\)
\end{itemize}

The standardization process calculates the mean of each column/variable
which is used to calculate the standard deviation of each
column/variable. Then the z-score of each value is computed and place
its corresponding component. This can be illustrated as such:

\begin{longtable}[]{@{}lll@{}}
\toprule
X's corresponding mean & Y's corresponding mean & Z's corresponding
mean\tabularnewline
\midrule
\endhead
\(\frac{x_1+x_2+x_3}{n}\) & \(\frac{y_1+y_2+y_3}{n}\) &
\(\frac{z_1+z_2+z_3}{n}\)\tabularnewline
\bottomrule
\end{longtable}

\begin{longtable}[]{@{}lll@{}}
\toprule
\begin{minipage}[b]{0.31\columnwidth}\raggedright
X's corresponding SD\strut
\end{minipage} & \begin{minipage}[b]{0.31\columnwidth}\raggedright
Y's corresponding SD\strut
\end{minipage} & \begin{minipage}[b]{0.29\columnwidth}\raggedright
Z's corresponding SD\strut
\end{minipage}\tabularnewline
\midrule
\endhead
\begin{minipage}[t]{0.31\columnwidth}\raggedright
\(\sqrt{\sum_{i=1}^n \frac{(x_i-\bar{x})^2}{n}}\)\strut
\end{minipage} & \begin{minipage}[t]{0.31\columnwidth}\raggedright
\(\sqrt{\sum_{i=1}^n \frac{(y_i-\bar{y})^2}{n}}\)\strut
\end{minipage} & \begin{minipage}[t]{0.29\columnwidth}\raggedright
\(\sqrt{\sum_{i=1}^n \frac{(z_i-\bar{z})^2}{n}}\)\strut
\end{minipage}\tabularnewline
\bottomrule
\end{longtable}

Standardize data set calculated by taking each value and subtracting by
the column's mean and dividing by the column's standard deviation.

\begin{longtable}[]{@{}lll@{}}
\toprule
\begin{minipage}[b]{0.30\columnwidth}\raggedright
Standardized values of X\strut
\end{minipage} & \begin{minipage}[b]{0.30\columnwidth}\raggedright
Standardized values of Y\strut
\end{minipage} & \begin{minipage}[b]{0.30\columnwidth}\raggedright
Standardized values of Z\strut
\end{minipage}\tabularnewline
\midrule
\endhead
\begin{minipage}[t]{0.30\columnwidth}\raggedright
\(\frac{x_1-\bar{x}}{\text{SD of x}}\)\strut
\end{minipage} & \begin{minipage}[t]{0.30\columnwidth}\raggedright
\(\frac{y_1-\bar{y}}{\text{SD of y}}\)\strut
\end{minipage} & \begin{minipage}[t]{0.30\columnwidth}\raggedright
\(\frac{z_1-\bar{z}}{\text{SD of z}}\)\strut
\end{minipage}\tabularnewline
\begin{minipage}[t]{0.30\columnwidth}\raggedright
\(\frac{x_2-\bar{x}}{\text{SD of x}}\)\strut
\end{minipage} & \begin{minipage}[t]{0.30\columnwidth}\raggedright
\(\frac{y_2-\bar{y}}{\text{SD of y}}\)\strut
\end{minipage} & \begin{minipage}[t]{0.30\columnwidth}\raggedright
\(\frac{z_2-\bar{z}}{\text{SD of z}}\)\strut
\end{minipage}\tabularnewline
\begin{minipage}[t]{0.30\columnwidth}\raggedright
\(\frac{x_3-\bar{x}}{\text{SD of x}}\)\strut
\end{minipage} & \begin{minipage}[t]{0.30\columnwidth}\raggedright
\(\frac{y_3-\bar{y}}{\text{SD of y}}\)\strut
\end{minipage} & \begin{minipage}[t]{0.30\columnwidth}\raggedright
\(\frac{z_3-\bar{z}}{\text{SD of z}}\)\strut
\end{minipage}\tabularnewline
\bottomrule
\end{longtable}

\begin{enumerate}
\def\labelenumi{\arabic{enumi}.}
\setcounter{enumi}{1}
\tightlist
\item
  \textbf{Covariance Matrix Computation} 
  \newline Covariance is a measure of the
  relationship between two variables and calculated using the following
  formula where x and y are two random variables:
\end{enumerate}

\begin{itemize}
\tightlist
\item
  \(Cov(X, Y) = \sum_{i=1}^n \frac{(x_i-\bar{x})(y_i-\bar{y})}{\text{n}}\)
  where n is the number of data points There are two important
  properties of covariance:
\end{itemize}

\begin{enumerate}
\def\labelenumi{\arabic{enumi}.}
\item
  \(Cov(X, X) = Var(X)\)
\item
  \(Cov(X, Y) = Cov(Y, X)\) The covariance matrix is defined as
  \(C_x = \frac{1}{n}AA^T\) where A is an mxn matrix in which the rows
  of A represent the variables measured (e.g.~\(X\)) and the columns
  represent individual observations (e.g.~\(x_1, y_1, z_1\)). Continuing
  from the example, in this case,
  \(A = \begin{pmatrix} x_1 & x_2 &x_3 \\ y_1 & y_2 & y_3 \\ z_1 & z_2 & z_3 \end{pmatrix} = \begin{pmatrix} a_1 \\ a_2 \\ a_3 \end{pmatrix}\)
  thus the covariance matrix,
  \(C_x = \frac{1}{3}\begin{pmatrix} a_1 \\ a_2 \\ a_3 \end{pmatrix}\begin{pmatrix} a_{1} & a_{2} & a_{3} \end{pmatrix} = \begin{pmatrix} Var(X) & Cov(X, Y) & Cov(X, Z) \\ Cov(Y, X) & Var(Y) & Cov(Y, Z) \\ Cov(Z, X) & Cov(Z, Y) & Var(Z)\end{pmatrix}\)

  \begin{itemize}
  \tightlist
  \item
    This is an example of a covariance calculation:
    \(Cov(X, Y) = \frac{(x_1-\bar{x})(y_1-\bar{y})+(x_2-\bar{x})(y_2-\bar{y})+(x_3-\bar{x})(y_3-\bar{y})}{3}\)
    If the covariance is positive, then this indicates positive
    correlation between the two variables and vice versa.
  \end{itemize}
\item
  \textbf{Eigenvector Decomposition: Determining the Principal
  Components} 
  \newline The next step in solving for the principal components of
  the data set is to find the eigenvalue and eigenvector of the
  covariance matrix, \(C_x\). Eigenvector in linear algebra refers to a
  non-zero vector when multiplied by a square matrix, A, results in a
  scaled version of the vector. This can be represented as Av = λv in
  which v is the eigenvector of A and λ is the eigenvalue. The
  eigenvectors should then be ordered descending, based on their
  corresponding eigenvalues to organize the variables based on order of
  significance. The eigenvector with the largest eigenvalue is the
  principal component. Following this, the user can choose the n number
  of variables to focus on, transforming the data set to n dimensions.
  The chosen eigenvectors are called the feature vector. The final data
  set is formed by matrix multiplication of the standardized data set by
  the featured vector.
\item
  \textbf{Proportion of Total Variance} 
  \newline Recall that the eigenvalues are
  represented with λ, the proportion of total variance which we can
  represent with V can be represented as such:
  \(V_i = \frac{λ_i}{\sum_{i=1}^nλ_j}\) Where n is the number of
  principal components and \(V_i\) is the proportion of total variance
  for the ith principal component.
\item
  \textbf{Interpretation of Principal Components and Proportion of Total
  Variance} 
  \newline As mentioned previously the principal components are those
  with the highest eigenvalues as it captures the most significant
  relationships between the data. A high principal component value
  indicates that the corresponding variables contribute significantly to
  the underlying pattern/trend of the data. The opposite holds if the
  principal component is a low value.\\
  The proportion of total variance characterizes the importance of that
  principal component in explaining patterns and relationships within
  the data. The higher the proportion for a specific principal
  component, the more variability that is captured by this principal
  component from the original dataset. In other words, a larger value
  indicates the corresponding component explains a larger portion of the
  variability in the data set. In practical application, this means the
  corresponding principal component has more significance in representing
  primary relationships in the data.
\end{enumerate}

    \textbf{Python Script for Dimensionality Reduction with PCA} 
\newline 
\newline
\textbf{1. Principal Component Analysis (PCA) Code Example}
\newline Suppose you
want to interpret the following data set of six variables of interest
(i.e., six dimensions). The following code will walk through an example
of how to perform PCA to interpret the trends in the dataset focusing on
six variables: age, sleep duration (hrs), quality of sleep (1-10,
subjective rating), physical activity (min/day), stress level (1-10,
subjective rating), and heart rate (bpm):
https://www.kaggle.com/datasets/uom190346a/sleep-health-and-lifestyle-dataset/data.
The following dataset can be downloaded, and the code can be run through
GoogleColab to show the computations that can be done on a
six-dimensional dataset. The challenge of observing trends in a data set
of more than two to three variables becomes apparent. Thus, this example
walks through how we can utilize Python to perform the calculations
described above to give us the principal components and portion of total
variance, which we can use for analysis. The main functions to note from
the code below are np.cov()and np.linalg.eig()

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{4}{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{k+kn}{import} \PY{n+nn}{numpy} \PY{k}{as} \PY{n+nn}{np}
\PY{k+kn}{import} \PY{n+nn}{pandas} \PY{k}{as} \PY{n+nn}{pd}
\PY{k+kn}{from} \PY{n+nn}{google}\PY{n+nn}{.}\PY{n+nn}{colab} \PY{k+kn}{import} \PY{n}{files}
\PY{k+kn}{import} \PY{n+nn}{matplotlib}\PY{n+nn}{.}\PY{n+nn}{pyplot} \PY{k}{as} \PY{n+nn}{plt}
\PY{k+kn}{import} \PY{n+nn}{seaborn} \PY{k}{as} \PY{n+nn}{sns}

\PY{c+c1}{\PYZsh{} Upload a file from your device}
\PY{n}{uploaded} \PY{o}{=} \PY{n}{files}\PY{o}{.}\PY{n}{upload}\PY{p}{(}\PY{p}{)}
\PY{c+c1}{\PYZsh{} Get the file path from chosen csv file}
\PY{n}{file\PYZus{}path} \PY{o}{=} \PY{n+nb}{list}\PY{p}{(}\PY{n}{uploaded}\PY{o}{.}\PY{n}{keys}\PY{p}{(}\PY{p}{)}\PY{p}{)}\PY{p}{[}\PY{l+m+mi}{0}\PY{p}{]}

\PY{c+c1}{\PYZsh{} Getting sample data from the uploaded csv file}
\PY{n}{excel\PYZus{}data} \PY{o}{=} \PY{n}{file\PYZus{}path}
\PY{n}{columns\PYZus{}to\PYZus{}read} \PY{o}{=} \PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Age}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Sleep Duration}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Quality of Sleep}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}
\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Physical Activity Level}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Stress Level}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Heart Rate}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}
\PY{n}{myData} \PY{o}{=} \PY{n}{pd}\PY{o}{.}\PY{n}{read\PYZus{}csv}\PY{p}{(}\PY{n}{excel\PYZus{}data}\PY{p}{,} \PY{n}{usecols} \PY{o}{=} \PY{n}{columns\PYZus{}to\PYZus{}read}\PY{p}{)}
\PY{n}{myOccupations} \PY{o}{=} \PY{n}{pd}\PY{o}{.}\PY{n}{read\PYZus{}csv}\PY{p}{(}\PY{n}{excel\PYZus{}data}\PY{p}{,} \PY{n}{usecols} \PY{o}{=} \PY{p}{[}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Occupation}\PY{l+s+s1}{\PYZsq{}}\PY{p}{]}\PY{p}{)}

\PY{c+c1}{\PYZsh{} Step 1: Standardization}
\PY{n}{ex\PYZus{}variable\PYZus{}means} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{mean}\PY{p}{(}\PY{n}{myData}\PY{p}{,} \PY{n}{axis}\PY{o}{=}\PY{l+m+mi}{0}\PY{p}{)}
\PY{n}{ex\PYZus{}variable\PYZus{}sd} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{std}\PY{p}{(}\PY{n}{myData}\PY{p}{,} \PY{n}{axis}\PY{o}{=}\PY{l+m+mi}{0}\PY{p}{)}
\PY{n}{ex\PYZus{}standardized\PYZus{}data} \PY{o}{=} \PY{p}{(}\PY{n}{myData} \PY{o}{\PYZhy{}} \PY{n}{ex\PYZus{}variable\PYZus{}means}\PY{p}{)} \PY{o}{/} \PY{n}{ex\PYZus{}variable\PYZus{}sd}

\PY{c+c1}{\PYZsh{} Step 2: Covariance Matrix Computation}
\PY{n}{ex\PYZus{}cov\PYZus{}matrix} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{cov}\PY{p}{(}\PY{n}{ex\PYZus{}standardized\PYZus{}data}\PY{p}{,} \PY{n}{rowvar}\PY{o}{=}\PY{k+kc}{False}\PY{p}{)}

\PY{c+c1}{\PYZsh{} Step 3: Eigenvector Decomposition}
\PY{n}{ex\PYZus{}eigenvalues}\PY{p}{,} \PY{n}{ex\PYZus{}principal\PYZus{}components} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{linalg}\PY{o}{.}\PY{n}{eig}\PY{p}{(}\PY{n}{ex\PYZus{}cov\PYZus{}matrix}\PY{p}{)}

\PY{c+c1}{\PYZsh{} Step 4: Proportion of Total Variance}
\PY{n}{ex\PYZus{}proportion\PYZus{}of\PYZus{}total\PYZus{}variance} \PY{o}{=} \PY{n}{ex\PYZus{}eigenvalues} \PY{o}{/} \PY{n}{np}\PY{o}{.}\PY{n}{sum}\PY{p}{(}\PY{n}{ex\PYZus{}eigenvalues}\PY{p}{)}

\PY{n+nb}{print}\PY{p}{(}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{Covariance Matrix:}\PY{l+s+s2}{\PYZdq{}}\PY{p}{)}
\PY{n+nb}{print}\PY{p}{(}\PY{n}{ex\PYZus{}cov\PYZus{}matrix}\PY{p}{)}
\PY{n+nb}{print}\PY{p}{(}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+se}{\PYZbs{}n}\PY{l+s+s2}{Principal Component:}\PY{l+s+s2}{\PYZdq{}}\PY{p}{)}
\PY{n+nb}{print}\PY{p}{(}\PY{n}{ex\PYZus{}principal\PYZus{}components}\PY{p}{)}
\PY{n+nb}{print}\PY{p}{(}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+se}{\PYZbs{}n}\PY{l+s+s2}{Eigenvalues: }\PY{l+s+s2}{\PYZdq{}}\PY{p}{)}
\PY{n+nb}{print}\PY{p}{(}\PY{n}{ex\PYZus{}eigenvalues}\PY{p}{)}
\PY{n+nb}{print}\PY{p}{(}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+se}{\PYZbs{}n}\PY{l+s+s2}{Proportion of Total Variance:}\PY{l+s+s2}{\PYZdq{}}\PY{p}{)}
\PY{n+nb}{print}\PY{p}{(}\PY{n}{ex\PYZus{}proportion\PYZus{}of\PYZus{}total\PYZus{}variance}\PY{p}{)}

\PY{c+c1}{\PYZsh{} Stores the two largest eigenvalues from step 3}
\PY{k}{def} \PY{n+nf}{two\PYZus{}largest\PYZus{}indices}\PY{p}{(}\PY{n}{arr}\PY{p}{)}\PY{p}{:}
    \PY{k}{if} \PY{n+nb}{len}\PY{p}{(}\PY{n}{arr}\PY{p}{)} \PY{o}{\PYZlt{}} \PY{l+m+mi}{2}\PY{p}{:}
        \PY{k}{raise} \PY{n+ne}{ValueError}\PY{p}{(}\PY{l+s+s2}{\PYZdq{}}\PY{l+s+s2}{Array must have at least two elements}\PY{l+s+s2}{\PYZdq{}}\PY{p}{)}
    \PY{n}{sorted\PYZus{}indices} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{argsort}\PY{p}{(}\PY{n}{arr}\PY{p}{)}
    \PY{n}{largest\PYZus{}index} \PY{o}{=} \PY{n}{sorted\PYZus{}indices}\PY{p}{[}\PY{o}{\PYZhy{}}\PY{l+m+mi}{1}\PY{p}{]}
    \PY{n}{second\PYZus{}largest\PYZus{}index} \PY{o}{=} \PY{n}{sorted\PYZus{}indices}\PY{p}{[}\PY{o}{\PYZhy{}}\PY{l+m+mi}{2}\PY{p}{]}
    \PY{k}{return} \PY{n}{largest\PYZus{}index}\PY{p}{,} \PY{n}{second\PYZus{}largest\PYZus{}index}

\PY{n}{ex\PYZus{}indicies\PYZus{}of\PYZus{}largest} \PY{o}{=} \PY{n}{two\PYZus{}largest\PYZus{}indices}\PY{p}{(}\PY{n}{ex\PYZus{}eigenvalues}\PY{p}{)}

\PY{c+c1}{\PYZsh{} Get the corresponding principal components of the two largest eigenvalues}
\PY{n}{ex\PYZus{}two\PYZus{}principal\PYZus{}components} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{column\PYZus{}stack}\PY{p}{(}\PY{p}{(}\PY{n}{ex\PYZus{}principal\PYZus{}components}\PY{p}{[}\PY{p}{:}\PY{p}{,}\PY{n}{ex\PYZus{}indicies\PYZus{}of\PYZus{}largest}\PY{p}{[}\PY{l+m+mi}{0}\PY{p}{]}\PY{p}{]}\PY{p}{,}
                                               \PY{n}{ex\PYZus{}principal\PYZus{}components}\PY{p}{[}\PY{p}{:}\PY{p}{,}\PY{n}{ex\PYZus{}indicies\PYZus{}of\PYZus{}largest}\PY{p}{[}\PY{l+m+mi}{1}\PY{p}{]}\PY{p}{]}\PY{p}{)}\PY{p}{)}
\PY{n+nb}{print}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+se}{\PYZbs{}n}\PY{l+s+s1}{Transformed Data}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\PY{n+nb}{print}\PY{p}{(}\PY{n}{ex\PYZus{}two\PYZus{}principal\PYZus{}components}\PY{p}{)}

\PY{c+c1}{\PYZsh{} Reduction of Dimensions (higher dimension \PYZhy{}\PYZgt{} 2D)}
\PY{n}{transformed\PYZus{}data} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{dot}\PY{p}{(}\PY{n}{ex\PYZus{}standardized\PYZus{}data}\PY{p}{,} \PY{n}{ex\PYZus{}two\PYZus{}principal\PYZus{}components}\PY{p}{)}
\PY{n}{np\PYZus{}occupations} \PY{o}{=} \PY{n}{myOccupations}\PY{o}{.}\PY{n}{to\PYZus{}numpy}\PY{p}{(}\PY{p}{)}\PY{o}{.}\PY{n}{flatten}\PY{p}{(}\PY{p}{)}

\PY{n}{data\PYZus{}and\PYZus{}occupation} \PY{o}{=} \PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{PC1}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:} \PY{n}{transformed\PYZus{}data}\PY{p}{[}\PY{p}{:}\PY{p}{,}\PY{l+m+mi}{0}\PY{p}{]}\PY{p}{,}
                       \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{PC2}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:} \PY{n}{transformed\PYZus{}data}\PY{p}{[}\PY{p}{:}\PY{p}{,}\PY{l+m+mi}{1}\PY{p}{]}\PY{p}{,}
                       \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Occupation}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:} \PY{n}{np\PYZus{}occupations}\PY{p}{\PYZcb{}}

\PY{n}{df\PYZus{}PC1\PYZus{}PC2\PYZus{}Occupation} \PY{o}{=} \PY{n}{pd}\PY{o}{.}\PY{n}{DataFrame}\PY{p}{(}\PY{n}{data\PYZus{}and\PYZus{}occupation}\PY{p}{)}

\PY{c+c1}{\PYZsh{} Visualization of the data}
\PY{c+c1}{\PYZsh{} creates color codes for the possible occupations in the dataset}
\PY{n}{occupation\PYZus{}palette} \PY{o}{=} \PY{p}{\PYZob{}}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Software Engineer}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{red}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Doctor}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{blue}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Nurse}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{purple}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Engineer}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{yellow}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}
                      \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Teacher}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{orange}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Sales Representative}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{green}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Lawyer}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{brown}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}
                      \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Accountant}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{turquoise}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Scientist}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{gray}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Manager}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{pink}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Salesperson}\PY{l+s+s1}{\PYZsq{}}\PY{p}{:} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{lightgreen}\PY{l+s+s1}{\PYZsq{}}\PY{p}{\PYZcb{}}
\PY{c+c1}{\PYZsh{} creates a scatter plot with x as the first principal components and y as the second principal components.}
\PY{n}{sns}\PY{o}{.}\PY{n}{scatterplot}\PY{p}{(}\PY{n}{x} \PY{o}{=} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{PC1}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}
                \PY{n}{y} \PY{o}{=} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{PC2}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}
                \PY{n}{hue} \PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Occupation}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,}
                \PY{n}{data} \PY{o}{=} \PY{n}{df\PYZus{}PC1\PYZus{}PC2\PYZus{}Occupation}\PY{p}{,}
                \PY{n}{palette} \PY{o}{=} \PY{n}{occupation\PYZus{}palette}\PY{p}{)}

\PY{n}{plt}\PY{o}{.}\PY{n}{title}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{PCA \PYZhy{} Biplot}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{xlabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{PC1 (}\PY{l+s+s1}{\PYZsq{}} \PY{o}{+} \PY{n+nb}{str}\PY{p}{(}\PY{n+nb}{round}\PY{p}{(}\PY{n}{ex\PYZus{}proportion\PYZus{}of\PYZus{}total\PYZus{}variance}\PY{p}{[}\PY{l+m+mi}{0}\PY{p}{]} \PY{o}{*} \PY{l+m+mi}{100}\PY{p}{,} \PY{l+m+mi}{2}\PY{p}{)}\PY{p}{)} \PY{o}{+} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{)}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{ylabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{PC2 (}\PY{l+s+s1}{\PYZsq{}} \PY{o}{+} \PY{n+nb}{str}\PY{p}{(}\PY{n+nb}{round}\PY{p}{(}\PY{n}{ex\PYZus{}proportion\PYZus{}of\PYZus{}total\PYZus{}variance}\PY{p}{[}\PY{l+m+mi}{1}\PY{p}{]} \PY{o}{*} \PY{l+m+mi}{100}\PY{p}{,} \PY{l+m+mi}{2}\PY{p}{)}\PY{p}{)} \PY{o}{+} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{)}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{legend}\PY{p}{(}\PY{n}{loc}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{upper left}\PY{l+s+s1}{\PYZsq{}}\PY{p}{,} \PY{n}{bbox\PYZus{}to\PYZus{}anchor}\PY{o}{=}\PY{p}{(}\PY{l+m+mi}{1}\PY{p}{,}\PY{l+m+mi}{1}\PY{p}{)}\PY{p}{,} \PY{n}{title}\PY{o}{=}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{Occupations}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}

\PY{n+nb}{print}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+se}{\PYZbs{}n}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{show}\PY{p}{(}\PY{p}{)}

\PY{c+c1}{\PYZsh{} sources: https://colab.research.google.com/notebooks/io.ipynb, https://pythonbasics.org/read\PYZhy{}csv\PYZhy{}with\PYZhy{}pandas/,  https://www.geeksforgeeks.org/python\PYZhy{}read\PYZhy{}csv\PYZhy{}using\PYZhy{}pandas\PYZhy{}read\PYZus{}csv/,  https://numpy.org/doc/stable/reference/routines.linalg.html, https://www.tutorialspoint.com/how\PYZhy{}to\PYZhy{}plot\PYZhy{}a\PYZhy{}graph\PYZhy{}in\PYZhy{}python, https://seaborn.pydata.org/generated/seaborn.scatterplot.html}
\end{Verbatim}
\end{tcolorbox}

    
    \begin{Verbatim}[commandchars=\\\{\}]
<IPython.core.display.HTML object>
    \end{Verbatim}

    
    \begin{Verbatim}[commandchars=\\\{\}]
Saving Sleep\_health\_and\_lifestyle\_dataset.csv to
Sleep\_health\_and\_lifestyle\_dataset (2).csv
Covariance Matrix:
[[ 1.00268097  0.34563351  0.47500394  0.17947259 -0.42347677 -0.22621103]
 [ 0.34563351  1.00268097  0.88558086  0.21292965 -0.81319735 -0.51783949]
 [ 0.47500394  0.88558086  1.00268097  0.1934136  -0.90116155 -0.66163381]
 [ 0.17947259  0.21292965  0.1934136   1.00268097 -0.03422598  0.1373382 ]
 [-0.42347677 -0.81319735 -0.90116155 -0.03422598  1.00268097  0.67182278]
 [-0.22621103 -0.51783949 -0.66163381  0.1373382   0.67182278  1.00268097]]

Principal Component:
[[ 0.2929922   0.32080985 -0.88702029 -0.06758719 -0.11525077 -0.08112241]
 [ 0.47875506  0.07451706  0.26325654  0.44265275 -0.61248009 -0.35336026]
 [ 0.51936269  0.03237107  0.09197523  0.11185927  0.04546088  0.84034272]
 [ 0.08751607  0.84322811  0.3560927  -0.37018261  0.10375667 -0.08188207]
 [-0.50177136  0.11927532 -0.04595293 -0.18341171 -0.74656532  0.37534995]
 [-0.39468721  0.40647278 -0.08073337  0.78504968  0.20345387  0.12160401]]

Eigenvalues:
[3.49302358 1.15856571 0.73627157 0.41417762 0.14670846 0.06733885]

Proportion of Total Variance:
[0.58061399 0.19257799 0.12238382 0.06884503 0.02438603 0.01119313]

Transformed Data
[[ 0.2929922   0.32080985]
 [ 0.47875506  0.07451706]
 [ 0.51936269  0.03237107]
 [ 0.08751607  0.84322811]
 [-0.50177136  0.11927532]
 [-0.39468721  0.40647278]]


    \end{Verbatim}

    \begin{figure}
      \centering
      \includegraphics[width=0.8\linewidth]{Dimensionality_Reduction_Technique_Principal_Component_Analysis_4_2.png}
      \label{fig:Example 1 PCA - Biplot}
    \end{figure}
    
    The scatterplot above plots the values of the PC1 and PC2 against each
other. PC1 represents the standardized data matrix multiplied by the
corresponding eigenvector of the largest eigenvalue. PC2 represents the
standardized data matrix multiplied by the corresponding eigenvector of
the second-largest eigenvalue. One method in which the graph may be
interpreted is by observing any separation or clustering of the
scatterplot. Cluster points may have some relationship in the original
high-dimensional data space. Outliers in the PCA plot can also indicate
deviation from the general pattern of the data. 
\newline For instance, examining
the visual representation above reveals intriguing clusters among the
sampled individuals. When categorizing individuals by their respective
occupations, distinctive groups emerge, encompassing nurses, doctors,
teachers, salespersons, engineers, and accountants. While this
observation may not serve as conclusive evidence for shared
characteristics in variables such as age, sleep duration (in hours),
sleep quality (rated on a subjective scale of 1-10), daily physical
activity (in minutes), stress levels (rated on a subjective scale of
1-10), and heart rate (in beats per minute) among specific occupations,
it does provide valuable insights into discernible patterns within this
sample. Moreover, analyzing the proportion of total variance for each
variable provides valuable insights into their respective contributions
to the overall variability of the data. For example, the calculations
conducted in step 4 reveal that age and sleep duration significantly
contribute to the dataset's variability, accounting for 58.06\% and
19.26\%, respectively, according to covariance calculations. This
observation becomes particularly relevant when assessing the consistency
of variables within the sample, shedding light on which factors maintain
consistant values and which exhibit greater variability.In conclusion,
the exploration of principal component analysis not only reveals
patterns and relationships within the data but also highlights variables
that significantly influence its variance.

    \begin{enumerate}
\def\labelenumi{\arabic{enumi}.}
\setcounter{enumi}{1}
\tightlist
\item
  \textbf{Comprehensive PCA Analyzer: Adaptive Dimensionality Reduction
  Tool}
\end{enumerate}

The following code allows for the user to upload their .csv file with
the data to which principal component analysis will be performed on
(without the data/sample IDs). The inputed higher dimension data will
then be reduced to two dimensions using the first and second largest
principal components. The code will output the principal components with
their corresponding eigenvalues, proportion of total variance, and a
visualization of the data.

    \begin{tcolorbox}[breakable, size=fbox, boxrule=1pt, pad at break*=1mm,colback=cellbackground, colframe=cellborder]
\prompt{In}{incolor}{ }{\boxspacing}
\begin{Verbatim}[commandchars=\\\{\}]
\PY{c+c1}{\PYZsh{} Upload a file from your device}
\PY{n}{uploaded} \PY{o}{=} \PY{n}{files}\PY{o}{.}\PY{n}{upload}\PY{p}{(}\PY{p}{)}
\PY{c+c1}{\PYZsh{} Get the file path from chosen csv file}
\PY{n}{file\PYZus{}path} \PY{o}{=} \PY{n+nb}{list}\PY{p}{(}\PY{n}{uploaded}\PY{o}{.}\PY{n}{keys}\PY{p}{(}\PY{p}{)}\PY{p}{)}\PY{p}{[}\PY{l+m+mi}{0}\PY{p}{]}

\PY{c+c1}{\PYZsh{} Getting sample data from the uploaded csv file}
\PY{n}{excel\PYZus{}data} \PY{o}{=} \PY{n}{file\PYZus{}path}
\PY{n}{inputData} \PY{o}{=} \PY{n}{pd}\PY{o}{.}\PY{n}{read\PYZus{}csv}\PY{p}{(}\PY{n}{excel\PYZus{}data}\PY{p}{)}

\PY{c+c1}{\PYZsh{} Step 1: Standardization}
\PY{n}{variable\PYZus{}means} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{mean}\PY{p}{(}\PY{n}{inputData}\PY{p}{,} \PY{n}{axis}\PY{o}{=}\PY{l+m+mi}{0}\PY{p}{)}
\PY{n}{variable\PYZus{}sd} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{std}\PY{p}{(}\PY{n}{inputData}\PY{p}{,} \PY{n}{axis}\PY{o}{=}\PY{l+m+mi}{0}\PY{p}{)}
\PY{n}{standardized\PYZus{}data} \PY{o}{=} \PY{p}{(}\PY{n}{inputData} \PY{o}{\PYZhy{}} \PY{n}{variable\PYZus{}means}\PY{p}{)} \PY{o}{/} \PY{n}{variable\PYZus{}sd}

\PY{c+c1}{\PYZsh{} Step 2: Covariance Matrix Computation}
\PY{n}{cov\PYZus{}matrix} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{cov} \PY{p}{(}\PY{n}{standardized\PYZus{}data}\PY{p}{,} \PY{n}{rowvar}\PY{o}{=}\PY{k+kc}{False}\PY{p}{)}

\PY{c+c1}{\PYZsh{} Step 3: Eigenvector Decomposition}
\PY{n}{eigenvalues}\PY{p}{,} \PY{n}{principal\PYZus{}components} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{linalg}\PY{o}{.}\PY{n}{eig}\PY{p}{(}\PY{n}{cov\PYZus{}matrix}\PY{p}{)}

\PY{c+c1}{\PYZsh{} Proportion of Total Variance}
\PY{n}{proportion\PYZus{}of\PYZus{}total\PYZus{}variance} \PY{o}{=} \PY{n}{eigenvalues} \PY{o}{/} \PY{n}{np}\PY{o}{.}\PY{n}{sum}\PY{p}{(}\PY{n}{eigenvalues}\PY{p}{)}

\PY{c+c1}{\PYZsh{} Get the two largest numbers}
\PY{n}{two\PYZus{}principal\PYZus{}components} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{column\PYZus{}stack}\PY{p}{(}\PY{p}{(}\PY{n}{principal\PYZus{}components}\PY{p}{[}\PY{p}{:}\PY{p}{,}\PY{n}{indicies\PYZus{}of\PYZus{}largest}\PY{p}{[}\PY{l+m+mi}{0}\PY{p}{]}\PY{p}{]}\PY{p}{,} \PY{n}{principal\PYZus{}components}\PY{p}{[}\PY{p}{:}\PY{p}{,}\PY{n}{indicies\PYZus{}of\PYZus{}largest}\PY{p}{[}\PY{l+m+mi}{1}\PY{p}{]}\PY{p}{]}\PY{p}{)}\PY{p}{)}
\PY{n+nb}{print}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+se}{\PYZbs{}n}\PY{l+s+s1}{Transformed Data}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\PY{n+nb}{print}\PY{p}{(}\PY{n}{two\PYZus{}principal\PYZus{}components}\PY{p}{)}

\PY{c+c1}{\PYZsh{} Reduction of Dimensions (higher dimension \PYZhy{}\PYZgt{} 2D)}
\PY{n}{transformed\PYZus{}data} \PY{o}{=} \PY{n}{np}\PY{o}{.}\PY{n}{dot}\PY{p}{(}\PY{n}{standardized\PYZus{}data}\PY{p}{,} \PY{n}{two\PYZus{}principal\PYZus{}components}\PY{p}{)}

\PY{c+c1}{\PYZsh{} Visualization of the data}
\PY{n}{plt}\PY{o}{.}\PY{n}{scatter}\PY{p}{(}\PY{n}{transformed\PYZus{}data}\PY{p}{[}\PY{p}{:}\PY{p}{,}\PY{l+m+mi}{0}\PY{p}{]}\PY{p}{,} \PY{n}{transformed\PYZus{}data}\PY{p}{[}\PY{p}{:}\PY{p}{,}\PY{l+m+mi}{1}\PY{p}{]}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{title}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{PCA \PYZhy{} Biplot}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{xlabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{PC1 (}\PY{l+s+s1}{\PYZsq{}} \PY{o}{+} \PY{n+nb}{str}\PY{p}{(}\PY{n+nb}{round}\PY{p}{(}\PY{n}{proportion\PYZus{}of\PYZus{}total\PYZus{}variance}\PY{p}{[}\PY{l+m+mi}{0}\PY{p}{]} \PY{o}{*} \PY{l+m+mi}{100}\PY{p}{,} \PY{l+m+mi}{2}\PY{p}{)}\PY{p}{)} \PY{o}{+} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{)}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{ylabel}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{PC2 (}\PY{l+s+s1}{\PYZsq{}} \PY{o}{+} \PY{n+nb}{str}\PY{p}{(}\PY{n+nb}{round}\PY{p}{(}\PY{n}{proportion\PYZus{}of\PYZus{}total\PYZus{}variance}\PY{p}{[}\PY{l+m+mi}{1}\PY{p}{]} \PY{o}{*} \PY{l+m+mi}{100}\PY{p}{,} \PY{l+m+mi}{2}\PY{p}{)}\PY{p}{)} \PY{o}{+} \PY{l+s+s1}{\PYZsq{}}\PY{l+s+s1}{\PYZpc{}}\PY{l+s+s1}{)}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}

\PY{n+nb}{print}\PY{p}{(}\PY{l+s+s1}{\PYZsq{}}\PY{l+s+se}{\PYZbs{}n}\PY{l+s+s1}{\PYZsq{}}\PY{p}{)}
\PY{n}{plt}\PY{o}{.}\PY{n}{show}\PY{p}{(}\PY{p}{)}
\end{Verbatim}
\end{tcolorbox}

    
    \begin{Verbatim}[commandchars=\\\{\}]
<IPython.core.display.HTML object>
    \end{Verbatim}

    
    \textbf{Discussion} Notably, PCA is a dimensionality reduction
technique; thus, the interpretation of the graphs commonly involves a
combination of different statistical analyses. Other statistical
analyses may include linear regression, cluster analysis, and time
series analysis. Additionally, while PCA can be a powerful reduction
technique, not all patterns will have clear and meaningful
interpretations.

    \textbf{Conclusions} Dimensionality reduction techniques allow for the
reduction of dimensions in a dataset while retaining key characteristics
of the data. As evidenced by the sample data set, it tackles several
issues, including higher-dimensional data, noise, and complexity.
Principal component analysis (PCA), the reduction technique focused upon
in this paper, facilitates the exploration of high-dimensional datasets
by identifying principal components and their contributions to variance.
PCA not only simplifies data representation but also uncovers patterns
and relationships of the dataset, thus making it a robust supplemental
tool in data analysis.

    \textbf{References} 
    \begin{enumerate}
      \item Google. (n.d.). Google Colaboratory. Retrieved from \url{https://colab.research.google.com/notebooks/io.ipynb}
    
      \item Hastie, T., Tibshirani, R., \& Friedman, J. H. (2009). \textit{The Elements of Statistical Learning: Data Mining, Inference, and Prediction (2nd ed.)}. New York: Springer.
    
      \item Kruskal, J.B. (1964). Nonmetric multidimensional scaling: A numerical method. \textit{Psychometrika, 29}, 115--129. \url{https://doi.org/10.1007/BF02289694}
    
      \item Jolliffe, I.T. (1986). \textit{Principal Component Analysis}. Springer Series in Statistics. New York, NY: Springer. \url{https://doi.org/10.1007/978-1-4757-1904-8\_1}
    
      \item Jolliffe, I. T., \& Cadima, J. (2016). Principal component analysis: A review and recent developments. \textit{Philosophical Transactions. Series A, Mathematical, Physical, and Engineering Sciences, 374}(2065), 20150202. \url{https://doi.org/10.1098/rsta.2015.0202}
    
      \item \textit{Linear Algebra (numpy.linalg)}. (n.d.). NumPy v1.26 Manual. Retrieved from \url{https://numpy.org/doc/stable/reference/routines.linalg.html}
    
      \item Read CSV with Pandas. (n.d.). Python Tutorial. Retrieved from \url{https://pythonbasics.org/read-csv-with-pandas/}
    
      \item Shlens, J. (2014). A tutorial on principal component analysis. arXiv preprint arXiv:1404.1100.
    
      \item Smith, L. I. (2002). A tutorial on principal components analysis.
    
      \item Poole, D. (2015). Section 4.1 Introduction to Eigenvalues and Eigenvectors. In \textit{Linear Algebra: A Modern Introduction} (pp.~254--260). Cengage Learning.
    \end{enumerate}



    % Add a bibliography block to the postdoc
    
    
    
\end{document}
