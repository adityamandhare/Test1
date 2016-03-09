
<html>
  <head>
    <title>Se'16: Patterns and Anti-Patterns (a.k.a. "Bad Smells")</title>
    <link rel="stylesheet"
	  type="text/css"
	  href="http://fonts.googleapis.com/css?family='Roboto+Slab'"
	  >
    <link rel="shortcut icon"
	  href="/_img/se_favicon.ico" 
	  type="image/x-icon/" >
 
    <style>
      body {
      
        font-family: 'Roboto Slab' sans-serif;
      padding: 10px;
      background-color: #ccc;
      color: black;
      text-align:center;
      background-image: url(http://www.transparenttextures.com/patterns/3px-tile.png);
      
      
      
       }
      #right {
          text-align: right;
      }
      #topline {
         padding: 0px;
         margin:0px;
         margin-top: 2px;
         margin-bottom: 4px;
         font-style: italic;
      font-size: small;
      border-top: 0px;
      border-bottom:0px;
      xborder-top: 1px solid #11559c;
      background-color: #ccc;
      }
      #wrap {
         background-color: #fff;
         padding: 10px;
         padding-top:0px;
         border: 1px black solid;
         width: 800px;
         margin: 0 auto;
      text-align: left;
      
      padding-left: 20px;
      padding-right: 20px;
      }

		
#crumbs {
	height:2.3em;
	border:1px solid #dedede;
      }
      #crumbs ul {

       list-style-type:none;
	padding:0;
      margin:0;
      }
      #crumbs li {
      list-style-type:none;
	padding:0;
	margin:0;
	float:left;
	line-height:2.3em;
	color:#777;
	padding-left:.75em;
	}		
#crumbs li a {
	background:url(/_img/crumbs.gif) no-repeat right center;
	display:block;
	padding:0 15px 0 0;
	}							

/****************************
      #crumbs li a:link,
#crumbs li a:visited {
	color:#777;
	text-decoration:none;
	}	
a:link, a:visited,	
#crumbs li a:hover,
#crumbs li a:focus {
	color:#dd2c0d;
      }
***************************/
      
#wrap a:link, a:visited, a:hover, a:focus{
      text-decoration: none;
      color: #11559c;
}
      
.hll { background-color: #ffffcc }
.c { color: #888888 } /* Comment */
.err { color: #a61717; background-color: #e3d2d2 } /* Error */
.k { color: #008800; font-weight: bold } /* Keyword */
.cm { color: #888888 } /* Comment.Multiline */
.cp { color: #cc0000; font-weight: bold } /* Comment.Preproc */
.c1 { color: #888888 } /* Comment.Single */
.cs { color: #cc0000; font-weight: bold; background-color: #fff0f0 } /* Comment.Special */
.gd { color: #000000; background-color: #ffdddd } /* Generic.Deleted */
.ge { font-style: italic } /* Generic.Emph */
.gr { color: #aa0000 } /* Generic.Error */
.gh { color: #333333 } /* Generic.Heading */
.gi { color: #000000; background-color: #ddffdd } /* Generic.Inserted */
.go { color: #888888 } /* Generic.Output */
.gp { color: #555555 } /* Generic.Prompt */
.gs { font-weight: bold } /* Generic.Strong */
.gu { color: #666666 } /* Generic.Subheading */
.gt { color: #aa0000 } /* Generic.Traceback */
.kc { color: #008800; font-weight: bold } /* Keyword.Constant */
.kd { color: #008800; font-weight: bold } /* Keyword.Declaration */
.kn { color: #008800; font-weight: bold } /* Keyword.Namespace */
.kp { color: #008800 } /* Keyword.Pseudo */
.kr { color: #008800; font-weight: bold } /* Keyword.Reserved */
.kt { color: #888888; font-weight: bold } /* Keyword.Type */
.m { color: #0000DD; font-weight: bold } /* Literal.Number */
.s { color: #dd2200; background-color: #fff0f0 } /* Literal.String */
.na { color: #336699 } /* Name.Attribute */
.nb { color: #003388 } /* Name.Builtin */
.nc { color: #bb0066; font-weight: bold } /* Name.Class */
.no { color: #003366; font-weight: bold } /* Name.Constant */
.nd { color: #555555 } /* Name.Decorator */
.ne { color: #bb0066; font-weight: bold } /* Name.Exception */
.nf { color: #0066bb; font-weight: bold } /* Name.Function */
.nl { color: #336699; font-style: italic } /* Name.Label */
.nn { color: #bb0066; font-weight: bold } /* Name.Namespace */
.py { color: #336699; font-weight: bold } /* Name.Property */
.nt { color: #bb0066; font-weight: bold } /* Name.Tag */
.nv { color: #336699 } /* Name.Variable */
.ow { color: #008800 } /* Operator.Word */
.w { color: #bbbbbb } /* Text.Whitespace */
.mb { color: #0000DD; font-weight: bold } /* Literal.Number.Bin */
.mf { color: #0000DD; font-weight: bold } /* Literal.Number.Float */
.mh { color: #0000DD; font-weight: bold } /* Literal.Number.Hex */
.mi { color: #0000DD; font-weight: bold } /* Literal.Number.Integer */
.mo { color: #0000DD; font-weight: bold } /* Literal.Number.Oct */
.sb { color: #dd2200; background-color: #fff0f0 } /* Literal.String.Backtick */
.sc { color: #dd2200; background-color: #fff0f0 } /* Literal.String.Char */
.sd { color: #dd2200; background-color: #fff0f0 } /* Literal.String.Doc */
.s2 { color: #dd2200; background-color: #fff0f0 } /* Literal.String.Double */
.se { color: #0044dd; background-color: #fff0f0 } /* Literal.String.Escape */
.sh { color: #dd2200; background-color: #fff0f0 } /* Literal.String.Heredoc */
.si { color: #3333bb; background-color: #fff0f0 } /* Literal.String.Interpol */
.sx { color: #22bb22; background-color: #f0fff0 } /* Literal.String.Other */
.sr { color: #008800; background-color: #fff0ff } /* Literal.String.Regex */
.s1 { color: #dd2200; background-color: #fff0f0 } /* Literal.String.Single */
.ss { color: #aa6600; background-color: #fff0f0 } /* Literal.String.Symbol */
.bp { color: #003388 } /* Name.Builtin.Pseudo */
.vc { color: #336699 } /* Name.Variable.Class */
.vg { color: #dd7700 } /* Name.Variable.Global */
.vi { color: #3333bb } /* Name.Variable.Instance */
      .il { color: #0000DD; font-weight: bold } /* Literal.Number.Integer.Long */


    </style>
  </head>
  <body>
    <div id="wrap">     

      
      <p style="font-size: small; ccolor:white;
xbackground-color: #CCC;

">
        <a href="/">Home</a> |
	<a href="/lectures/">Lectures</a> |
	<a href="/project">Project</a> |
	<a href="/review">Review</a>  | 
	<a href="/resources">Resources</a> |
	<a href="https://groups.google.com/forum/#!forum/csc510">News</a><br>
      
      
      <a href="/"><img
		     src="/_img/banner.png"></a><br>
      
      <a href="http://unlicense.org/">&copy; 2016</a>,
	  <a href="http://menzies.us">Tim Menzies</a>,
	  <a href="https://www.csc.ncsu.edu">cs@ncstate</a>
      
      </p>

     
      </span>

      
      
<h1 id="patterns-and-anti-patterns-aka-bad-smells">Patterns and Anti-Patterns (a.k.a. "Bad Smells")</h1>
<div class="toc">
<ul>
<li><a href="#patterns-and-anti-patterns-aka-bad-smells">Patterns and Anti-Patterns (a.k.a. "Bad Smells")</a></li>
<li><a href="#before-we-begin-beware-generalization-itis">Before we Begin: beware generalization-itis</a></li>
<li><a href="#patterns">Patterns</a><ul>
<li><a href="#patterns-in-chess">Patterns in chess:</a></li>
<li><a href="#patterns-in-object-design">Patterns in Object Design</a></li>
</ul>
</li>
<li><a href="#patterns-in-function-programming">"Patterns" in function programming</a></li>
<li><a href="#maybe-not-patterns-but-anti-patterns">Maybe not Patterns, but Anti-Patterns</a><ul>
<li><a href="#eg-oo-bad-smells">e.g. OO Bad Smells</a></li>
<li><a href="#eg-test-smell-bad-smells">e.g. Test Smell Bad Smells</a></li>
<li><a href="#eg-arthur-riel-oo-design-heuristics">e.g. Arthur Riel: OO design heuristics</a></li>
</ul>
</li>
</ul>
</div>
<hr />
<p>Experts are experts since they've learned patterns of useful behavior (fyi: expert = 5 patterns per day * 10 years)</p>
<h1 id="before-we-begin-beware-generalization-itis">Before we Begin: beware generalization-itis</h1>
<p>YAGNI! (your aint gonna need it)</p>
<ul>
<li>but, sometimes,  YAGNI (you are gonna need it)</li>
<li>Remember the Rule of 3<ul>
<li>First time, just do it;</li>
<li>Second time, note you are doing it the second time;</li>
<li>Third time, now you are allowed to refactor to generalize.</li>
</ul>
</li>
</ul>
<h1 id="patterns">Patterns</h1>
<p>If we look at N concrete things,  and then abstract our thinking a little,
then we can find some repeated features that might even apply to future things.</p>
<p>For example...</p>
<h2 id="patterns-in-chess">Patterns in chess:</h2>
<ul>
<li>more space in the center</li>
<li>open lines</li>
<li>weak squares</li>
<li>pawn majority, pawn minority</li>
<li>two weak points to attack - the Principle of Two Weaknesses</li>
<li>weak kingside</li>
<li>weak queenside pawn structures</li>
<li>inactive knight at the corner</li>
<li>dead bishop</li>
<li>weak isolated d-pawn</li>
<li>insufficient piece coordination</li>
<li>attacking mark</li>
<li>free protected pawn</li>
<li>bishop pair</li>
<li>better minor piece in open position - bishop versus knight</li>
<li>better minor piece in blocked position - knight versus bishop</li>
<li>break through</li>
<li>and others etc. </li>
</ul>
<p>e.g forking:</p>
<p><img alt="" src="/_img/chessfork1.png" /></p>
<p><img alt="" src="/_img/chessfork2.png" /></p>
<p><img alt="" src="/_img/chessfork3.png" /></p>
<h2 id="patterns-in-object-design">Patterns in Object Design</h2>
<p><img width=500 src="/_img/chbrowser.png"></p>
<p><img width=500 src="/_img/filebrowser.png"></p>
<p><img width=500 src="/_img/compositebrowser.png"></p>
<p><img width=500 src="/_img/compositepattern.png"></p>
<p><a href="/_img/gofpattern.jpg"><img width=500
src="/_img/gofpattern.jpg"></a></p>
<p>Gang of Four (1994</p>
<p>Erich Gamma, Richard Helm, Ralph Johnson and John Vlissides </p>
<p>If you read this book, and you are not excited, then check your pulse. You're dead.</p>
<p><img width=400 src="/_img/gofbook.png"></p>
<p>Patterns are a religion</p>
<p><img width=400 src="/_img/onering.png"></p>
<h1 id="patterns-in-function-programming">"Patterns" in function programming</h1>
<p>Functional programmers (Haskell, Clojure, F#, Lisp, Skill, Racket,….) make up 10 patterns for breakfast.</p>
<p>Cause its so easy (say what? OO makes some easy things hard?)</p>
<p>In LISP, one (and only one) recursive data type, the list which contains either
atoms
or another list</p>
<p>e.g. visitor pattern in functional (5 lines)</p>
<table class="codehilitetable"><tr><td class="linenos"><div class="linenodiv"><pre> 1
 2
 3
 4
 5
 6
 7
 8
 9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35</pre></div></td><td class="code"><div class="codehilite"><pre><span class="p">(</span><span class="nb">defun</span> <span class="nv">visitr</span> <span class="p">(</span><span class="nv">things</span> <span class="nv">f</span><span class="p">)</span>
  <span class="s">&quot;visitor patterns in functional programming&quot;</span>
  <span class="p">(</span><span class="k">if</span> <span class="p">(</span><span class="nb">atom</span> <span class="nv">things</span><span class="p">)</span>
      <span class="p">(</span><span class="nb">funcall</span> <span class="nv">f</span> <span class="nv">things</span><span class="p">)</span>   <span class="c1">; then</span>
      <span class="p">(</span><span class="nb">dolist</span> <span class="p">(</span><span class="nv">one</span> <span class="nv">things</span><span class="p">)</span> <span class="c1">; else do for each</span>
         <span class="p">(</span><span class="nv">visitr</span> <span class="nv">one</span> <span class="nv">f</span><span class="p">))))</span>

<span class="p">(</span><span class="nb">defun</span> <span class="nv">demo</span> <span class="p">(</span><span class="k">&amp;aux</span> <span class="nv">all</span><span class="p">)</span>
  <span class="p">(</span><span class="k">let</span> <span class="p">((</span><span class="nv">nastyComplexThing</span>
     <span class="o">&#39;</span><span class="p">(</span><span class="nv">a</span> 
       <span class="p">(</span><span class="nv">b</span> <span class="mi">1</span><span class="p">)</span> 
       <span class="nv">c</span>
       <span class="p">(</span><span class="nv">d</span> <span class="nv">e</span> 
          <span class="p">(</span><span class="nv">f</span> <span class="nv">g</span> 
         <span class="p">(</span><span class="mi">2</span> <span class="mi">3</span> <span class="mi">4</span><span class="p">)</span>
         <span class="p">)</span>
          <span class="nv">h</span><span class="p">)</span>
       <span class="p">(</span><span class="nv">i</span> <span class="nv">j</span><span class="p">)</span>
       <span class="p">(</span><span class="nv">k</span>
        <span class="p">(</span><span class="nv">l</span>
         <span class="p">(</span><span class="nv">m</span>
          <span class="p">(</span><span class="nv">n</span> <span class="nv">o</span> <span class="nv">p</span> <span class="nv">q</span> <span class="nv">r</span> 
         <span class="p">(</span><span class="nv">s</span> <span class="mi">5</span> <span class="mi">6</span> <span class="mi">7</span><span class="p">)</span>
         <span class="p">(</span><span class="no">t</span> <span class="mi">8</span> <span class="mi">9</span> <span class="p">)</span>
         <span class="nv">u</span> <span class="nv">v</span> <span class="nv">w</span> <span class="nv">x</span> <span class="nv">y</span> <span class="nv">z</span><span class="p">)))))))</span>
    <span class="p">(</span><span class="nv">visitr</span> <span class="nv">nastyComplexThing</span>
        <span class="p">(</span><span class="k">lambda</span> <span class="p">(</span><span class="nv">x</span><span class="p">)</span>
          <span class="p">(</span><span class="k">if</span> <span class="p">(</span><span class="nb">numberp</span> <span class="nv">x</span><span class="p">)</span>
          <span class="p">(</span><span class="nb">push</span> <span class="nv">x</span> <span class="nv">all</span><span class="p">))))</span>
    <span class="nv">all</span><span class="p">))</span>

<span class="p">(</span><span class="nb">print</span><span class="p">(</span><span class="nv">demo</span><span class="p">))</span>

<span class="c1">; output</span>
<span class="c1">; (9 8 7 6 5 4 3 2 1)</span>
</pre></div>
</td></tr></table>

<h1 id="maybe-not-patterns-but-anti-patterns">Maybe not Patterns, but Anti-Patterns</h1>
<h2 id="eg-oo-bad-smells">e.g. OO Bad Smells</h2>
<p>Taken from the excellent notes found at the
<a href="https://refactoring.guru/catalog">Refactoring guru</a></p>
<ul>
<li>Bloated<ul>
<li>Bloaters are code, methods and classes that have increased to such gargantuan proportions that they are hard to work with. Usually these smells do not crop up right away, rather they accumulate over time as the program evolves (and especially when nobody makes an effort to eradicate them).</li>
<li>Long Method</li>
<li>Large Class</li>
<li>Primitive Obsession</li>
<li>Long Parameter List</li>
<li>Data Clumps</li>
</ul>
</li>
<li>OO abusers<ul>
<li>All these smells are incomplete or incorrect application of object-oriented programming principles.</li>
<li>Switch Statements</li>
<li>Temporary Field</li>
<li>Refused Bequest</li>
<li>Alternative Classes with Different Interfaces</li>
</ul>
</li>
<li>Change preventers<ul>
<li>These smells mean that if you need to change something in one place in your code, you have to make many changes in other places too. Program development becomes much more complicated and expensive as a result.</li>
<li>Divergent Change</li>
<li>Shotgun Surgery</li>
<li>Parallel Inheritance Hierarchies</li>
</ul>
</li>
<li>Dispensables<ul>
<li>A dispensable is something pointless and unneeded whose absence would make the code cleaner, more efficient and easier to understand.</li>
<li>Comments</li>
<li>Duplicate Code</li>
<li>Lazy Class</li>
<li>Data Class</li>
<li>Dead Code</li>
<li>Speculative Generality</li>
</ul>
</li>
<li>Couplers<ul>
<li>All the smells in this group contribute to excessive coupling between classes or show what happens if coupling is replaced by excessive delegation.</li>
<li>Feature Envy</li>
<li>Inappropriate Intimacy</li>
<li>Message Chains</li>
<li>Middle Man</li>
</ul>
</li>
</ul>
<p>Note:</p>
<ul>
<li>For every study, there is an anti-study</li>
<li>Some raise questions about whether the above are <strong>the</strong> bad smells that are useful to
  consider for <strong>all</strong> projects<sup id="fnref:hall12"><a class="footnote-ref" href="#fn:hall12" rel="footnote">1</a></sup>.</li>
<li>That said, there is some evidence that these bad smells predict for software change proneness<sup id="fnref:khomh"><a class="footnote-ref" href="#fn:khomh" rel="footnote">2</a></sup>.</li>
<li>But another approach is to reflect over your own error logs to learn the bad smells that are
  most important at your site,</li>
<li>So not general bad smells for all projects;</li>
<li>But general methods for finding local bad smells.</li>
<li>For example, see next section.</li>
</ul>
<h2 id="eg-test-smell-bad-smells">e.g. Test Smell Bad Smells</h2>
<p>From [Reichart et al. 2007]<sup id="fnref:reichhart"><a class="footnote-ref" href="#fn:reichhart" rel="footnote">3</a></sup>.</p>
<ol>
<li>Harvest the tests and collect a list of problems found in
the tests through manual inspection.<ul>
<li>Due the large number of tests we did
   not analyze all of them, but rather focused on a sample of approximately 500
   test-methods.</li>
</ul>
</li>
<li>Cluster the problems to identify commonalities and differences.</li>
<li>Distill the lessons in automatic queries in a tool called TestLint.<ul>
<li>Static analysis of the test code and dynamic
  analysis including code manipulation and
  instrumentation.</li>
</ul>
</li>
<li>Apply  queries on all the tests in our case study<ul>
<li>Manually inspected the detected Test Smells to identify false positives.</li>
</ul>
</li>
</ol>
<p><img alt="" src="/_img/badsmells1.gif" /></p>
<p><img alt="" src="/_img/badsmells2.png" /></p>
<h2 id="eg-arthur-riel-oo-design-heuristics">e.g. Arthur Riel: OO design heuristics</h2>
<p><strong>Chapter 2: Classes and Objects: The Building Blocks of the Object-Oriented Paradigm</strong></p>
<p>2.1: All data should be hidden within its class.</p>
<p>2.2: Users of a class must be dependent on its public interface, but a class should not be dependent on its users.</p>
<p>2.3: Minimize the number of messages in the protocol of a class.</p>
<p>2.4: Implement a minimal public interface which all classes understand. This interface should include operations such as copy (deep versus shallow), equality testing, pretty printing, parsing from a ASCII description, etc.</p>
<p>2.5: Do not put implementation details such as common-code private functions into the public interface of a class.</p>
<p>2.6: Do not clutter the public interface of a class with things that users of that class are not able to use or are not interested in using.</p>
<p>2.7: Classes should only exhibit nil or export coupling with other classes.</p>
<p>2.8: A class should capture one and only one key abstraction.</p>
<p>2.9: Keep related data and behavior in one place.</p>
<p>2.10: Spin off non-related information into another class (i.e. non-communicating behavior).</p>
<p>2.11: Be sure the abstraction that you model are classes and not simply the roles objects play.</p>
<p><strong>Chapter 3: Topologies of Action-Oriented Vs. Object-Oriented Applications</strong></p>
<p>3.1: Distribute system intelligence horizontally as uniformly as possible, i.e. the top level classes in a design should share the work uniformly.</p>
<p>3.2: Do not create god classes/objects in your system. Be very suspicious of an abstraction whose name contains Driver, Manager, System, or Subsystem.</p>
<p>3.3: Beware of classes that have many accessor methods defined in their public interface, many of them imply that related data and behavior are not being kept in one place.</p>
<p>3.4: Beware of classes which have too much non-communicating behavior, i.e. methods which operate on a proper subset of the data members of a class. God classes often exhibit lots of non-communicating behavior.</p>
<p>3.5: In applications which consist of an object-oriented model interacting with a user interface, the model should never be dependent on the interface. The interface should be dependent on the model.</p>
<p>3.6: Model the real world whenever possible. (This heuristic is often violated for reasons of system intelligence distribution, avoidance of god classes, and the keeping of related data and behavior in one place).</p>
<p>3.7: Eliminate irrelevant classes from your design.</p>
<p>3.8: Eliminate classes that are outside the system.</p>
<p>3.9: Do not turn an operation into a class.</p>
<p>3.10: Agent classes are often placed in the analysis model of an application.</p>
<p><strong>Chapter 4: The Relationships Between Classes and Objects</strong></p>
<p>4.1: Minimize the number of classes with which another class collaborates.</p>
<p>4.2: Minimize the number of message sends between a class and its collaborator.</p>
<p>4.3: Minimize the amount of collaboration between a class and its collaborator, i.e. the number of different messages sent.</p>
<p>4.4 : Minimize fanout in a class.</p>
<p>4.5: If a class contains objects of another class then the containing class should be sending messages to the contained objects.</p>
<p>4.6: Most of the methods defined on a class should be using most of the data members most of the time.</p>
<p>4.7: Classes should not contain more objects than a developer can fit in his or her short term memory. A favorite value for this number is six.</p>
<p>4.8: Distribute system intelligence vertically down narrow and deep containment hierarchies.</p>
<p>4.9: When implementing semantic constraints, it is best to implement them in terms of the class definition. Often this will lead to a proliferation of classes in which case the constraint must be implemented in the behavior of the class, usually, but not necessarily, in the constructor</p>
<p>4.10: When implementing semantic constraints in the constructor of a class, place the constraint test in the constructor as far down a containment hierarchy as the domain allows.</p>
<p>4.11: The semantic information on which a constraint is based is best placed in a central third-party object when that information is volatile.</p>
<p>4.12: The semantic information on which a constraint is based is best decentralized among the classes involved in the constraint when that information is stable.</p>
<p>4.13: A class must know what it contains, but it should never know who contains it.</p>
<p>4.14: Objects which share lexical scope -- those contained in the same containing class -- should not have uses relationships between them.</p>
<p><strong>Chapter 5: The Inheritance Relationship</strong></p>
<p>5.1: Inheritance should only be used to model a specialization hierarchy.</p>
<p>5.2: Derived classes must have knowledge of their base class by definition, but base classes should not know anything about their derived classes.</p>
<p>5.3: All data in a base class should be private, i.e. do not use protected data.</p>
<p>5.4: Theoretically, inheritance hierarchies should be deep, i.e. the deeper the better.</p>
<p>5.5: Pragmatically, inheritance hierarchies should be no deeper than an average person can keep in their short term memory. A popular value for this depth is six.</p>
<p>5.6: All abstract classes must be base classes.</p>
<p>5.7: All base classes should be abstract classes.</p>
<p>5.8: Factor the commonality of data, behavior, and/or interface as high as possible in the inheritance hierarchy.</p>
<p>5.9: If two or more classes only share common data (no common behavior) then that common data should be placed in a class which will be contained by each sharing class.</p>
<p>5.10: If two or more classes have common data and behavior (i.e. methods) then those classes should each inherit from a common base class which captures those data and methods.</p>
<p>5.11: If two or more classes only share common interface (i.e. messages, not methods) then they should inherit from a common base class only if they will be used polymorphically.</p>
<p>5.12: Explicit case analysis on the type of an object is usually an error, the designer should use polymorphism in most of these cases.</p>
<p>5.13: Explicit case analysis on the value of an attribute is often an error. The class should be decomposed into an inheritance hierarchy where each value of the attribute is transformed into a derived class.</p>
<p>5.14: Do not model the dynamic semantics of a class through the use of the inheritance relationship. An attempt to model dynamic semantics with a static semantic relationship will lead to a toggling of types at runtime.</p>
<p>5.15: Do not turn objects of a class into derived classes of the class. Be very suspicious of any derived class for which there is only one instance.</p>
<p>5.16: If you think you need to create new classes at runtime, take a step back and realize that what you are trying to create are objects. Now generalize these objects into a class.</p>
<p>5.17: It should be illegal for a derived class to override a base class method with a NOP method, i.e. a method which does nothing.</p>
<p>5.18: Do not confuse optional containment with the need for inheritance, modelling optional containment with inheritance will lead to a proliferation of classes.</p>
<p>5.19: When building an inheritance hierarchy try to construct reusable frameworks rather than reusable components.</p>
<p><strong>Chapter 6: Multiple Inheritance</strong></p>
<p>6.1: If you have an example of multiple inheritance
in your design, assume you have made a mistake and
prove otherwise.</p>
<p>6.2: Whenever there is inheritance in an
object-oriented design ask yourself two questions:
1) Am I a special type of the thing I'm inheriting
from? and 2) Is the thing I'm inheriting from part
of me?</p>
<p>6.3: Whenever you have found a multiple inheritance
relationship in a object-oriented design be sure
that no base class is actually a derived class of
another base class, i.e. accidental multiple
inheritance.</p>
<p><strong>Chapter 7: The Association Relationship</strong></p>
<p>7.1: When given a choice in an object-oriented
design between a containment relationship and an
association relationship, choose the containment
relationship.</p>
<p><strong>Chapter 8: Class-Specific Data and Behavior</strong></p>
<p>8.1: Do not use global data or functions to perform
bookkeeping information on the objects of a class,
class variables or methods should be used instead.</p>
<p><strong>Chapter 9: Physical Object-Oriented Design</strong></p>
<p>9.1: Object-oriented designers should never allow
physical design criteria to corrupt their logical
designs. However, very often physical design
criteria is used in the decision making process at
logical design time.</p>
<p>9.2: Do not change the state of an object without
going through its public interface.</p>
<div class="footnote">
<hr />
<ol>
<li id="fn:hall12">
<p>Tracy Hall, Min Zhang, David Bowes, and Yi Sun,
<a href="/resources/12badsmells.pdf">Some Code Smells Have a Significant but Small Effect on Faults</a>).
ACM Trans. Softw. Eng. Methodol. 23(4), Article 33 (September 2014),&#160;<a class="footnote-backref" href="#fnref:hall12" rev="footnote" title="Jump back to footnote 1 in the text">&#8617;</a></p>
</li>
<li id="fn:khomh">
<p>Foutse Khomh,
Massimiliano Di Penta, Yann-Gael Gueheneuc,
<a href="http://swat.polymtl.ca/~foutsekh/docs/TechReport.pdf">An Exploratory Study of the Impact of Code Smells on Software Change-proneness</a>
in Reverse Engineering, 2009. WCRE '09. 16th Working Conference on , vol., no., pp.75-84, 13-16 Oct. 2009&#160;<a class="footnote-backref" href="#fnref:khomh" rev="footnote" title="Jump back to footnote 2 in the text">&#8617;</a></p>
</li>
<li id="fn:reichhart">
<p>Stefan Reichhart and Tudor Girba, Stephane Ducasse,
<a href="http://www.jot.fm/issues/issue_2007_10/paper12/">Rule-based Assessment of Test Quality</a>,
Journal of Object Technology,
6(9), October 2007.&#160;<a class="footnote-backref" href="#fnref:reichhart" rev="footnote" title="Jump back to footnote 3 in the text">&#8617;</a></p>
</li>
</ol>
</div>