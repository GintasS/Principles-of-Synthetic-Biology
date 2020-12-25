# Principles-of-Synthetic-Biology

## Jump to...

  - [Week 1](#week1)
  - [Week 2](#week2)
  - [Week 3](#week3)
  - [Week 4](#week4)
  - [Week 5](#week5)
  - [Week 6](#week6)
  
## <a name="week1"></a>Week 1

We might be able to program cells in the same way we program computers.
Computer might be able to translate these high level biological programs into say biological regulatory networks.

Abstract regulatory network -> DNA sequence -> into the cell.

#### Possible real-life Applications
- Detect (and kill) HeLa cancer cells (Cancer)
- Vaccination using regulated antigen/adjuvant production (Infectious diseases)
- Self-timed, multi-step hiPs to B-cell differentation (Programmable Organoids)
- Rare diseases, DNA Vaccines
- Cell-based therapies, Beta cells
- Biomanufacturing
- Drug development
- Diagnostics
- Water supply crises
- Land and Waterway misuse
- Food Shortage Crises
- Rising Greenhouse Gas Emissions

 #### Course outline
 - Introduction to synthetic biology
 - DNA manipulation
 - Biological principles and modeling
 - Dynamics of biological circuits
 - Principles of design
 - Other modes of regulation:
   Rna, Protein-Protein, Metabolic
 - Multicellular systems
 - Synthetic biology applications & perspectives

#### Intro

How do we go from wanting a cell to do X to having the cell do X? We need to apply principles of design to engineer the circuit that lets the cell do X. We need computational tools to analyze the circuit, get intuition about it or confirm our expectations. We can then have the DNA encoding the circuit synthesized and test it in cells. Since these circuits are likely to be complex, we will need several iterations of design, debugging, analysis etc. This cannot happen in an ad hoc way, we need principles to follow for this to be efficient!

Exposing cells to various factors for them to mutate.

#### What is synthetic biology?
- An emerging engineering discipline that seeks to make implementation of new biological function vastly more efficient, reliable, transparent and safe.
- A field dedicated to biologically engineered solutions to world problems in health, energy, environment, and security.

#### What is different between SB and GE?
>My understanding is that synthetic biology is genetic engineering 2.0. The difference is in the approach. Whereas genetic engineering projects are usually ad hoc, synthetic biology aims to apply proper engineering principles such as standardisation, modularisation, and reusability. Synthetic biologists create and use libraries of standard parts that are characterised, so they can be easily reused in projects. A part could be a gene, a terminator, a promoter, etc.

>Synthetic biology also has greater ambitions. The focus is on creating whole systems/circuits of genetic regulation. This means there is a need for computational modelling and understanding of how biological systems work. In this aspect synthetic biology is a sister of systems biology a bit like synthetic chemistry (engineering) is a sister of chemistry (science).

>You could of course argue that it's just a marketing ploy to invent a new name for something that is just the next step in genetic engineering, but the differences in approach are quite large and a new name signifies it.

>With regards to synthesised vs. PCRed DNA: It doesn't really matter which you use in synthetic biology. However, cheap synthesis is one of the technologies that enable easier synthetic biology. The idea for the future is that you will be able to synthesise whole plasmids and chromosomes instead of having to "cut and paste" DNA. When that happens physical parts repositories will be obsolete, but they will remain crucial in silico. Cheap synthesis is nice, but doesn't make or brake synthetic biology.

#### Top-down design

In order to deal with challenges arising from complexity of systems, engineers break down the systems into smaller, more manageable pieces hierarchically.

Biology is not necessarily Boolean (digital) as we hope. The cell uses electrical, chemical, and mechanical currencies in non-digital ways. Perhaps we need different paradigms for different components and layers.

**Registry of Standard Biological Parts - iGEM registry.**

**See Images in Week 1.** 

## <a name="week2"></a>Week 2

Top-down design: specifying the overall function of a system at a high level, then filling in details through various levels of abstraction, down to the physical implementation of the system.

A system is made of modules, implementing individual functions such as toggles or oscillators. Each module is composed of devices that perform even simple operations such as repression or activation. At the very lowest level we have the physical components such as DNA and proteins. We can model a system at various levels of granularity: the molecular or even atomic level, or at the level of devices.

The process of top down decomposition helps you get at the various levels of abstraction and find a suitable implementation for the system. Again, we start at a high level description. We then think of a slightly more formal description of the system, for example using Boolean algebra, where signals are either on or off (molecules are either present or not). This lets you map the behaviour to an abstract genetic regulatory network (GRN), where genetic components regulate each other through processes like repression and activation. Once you have an abstract GRN, you have to choose the actual genes to fill in the nodes in this regulatory network — the actual repressors and activators. These genes have DNA sequences that you can then assemble together into a physical implementation of the circuit and finally test them in cells.

### The BioCompiler

A line is a piece of DNA.
Bent arrow - a region of DNA to which polymerase can bind.

aTc — a small molecule inducer, disables the TetR repressor protein from binding its operator.

IPTG — a small molecule inducer, disables the LacI repressor protein from binding its operator.

LISP-like language — LISP is a family of programming languages, famous for its heavy use of parentheses. A statement like (green (sr-latch (aTc) (IPTG))) reads something like "turn green if a function called sr-latch called with the values of aTc and IPTG returns true".

SR-latch — a bistable element that can be set (S) and reset (R). When the set signal is present, the latch is considered on and remains on until the reset input is seen, when the latch turns off. You can turn the latch on again by sending a set signal. Thus it functions as a 1-bit storage element by remembering whether the last input was S or R.

The BioCompiler is able to optimize combinatorial logic circuits (circuits without any state or memory), stateful logic circuits (like the SR latch, which has memory), and even systems with various spatial properties, such as pattern generators.

#### CAD for biology

What should we characterize? What can we characterize? For enzyme engineering, we would want to know the rates of enzymes. For synthetic biologists, measuring binding rates for transcription factors and DNA in vivo (in cells) is hard in high throughput. However, people have developed good methods for characterizing promoters, to measure the **rate of production from promoters.** We could do it with quantitative PCR (qPCR), for example, though it is medium throughput. RNA sequencing (RNAseq), could be used to see how whole pathways are affected by a circuit.

#### Top-down design B cells

In this example of top-down design we look at a system where we want to engineer stem cells to produce β cells in Type I diabetes patients. In Type I diabetes, β cells are killed by the immune system. At a high level, we want a system that maintains a population of β cells using auto-regulated differentiation of stem cells (homeostasis of the β cell population).

To achieve this, we can have stem cells that auto-regulate their own division. If there are too many, the division is inhibited. At the same time, these stem cells can differentiate through various stages into β cells, which are then removed by the immune system. We add auto-regulation to the differentiation stage to control its rate: too many β cells will cause there to be less differentiation.

#### Challenges to design

As a new engineering discipline we need to create new rules and standards! This should happen in a cycle of designing, building, testing and learning. 
We need to do this in a systematic and unified way across laboratories and institutions to progress as a field.

### DNA synthesis and assembly 

DNA synthesis and assembly is what lets us go from a concept of some behavior to an actual implementation, a genetic circuit.

DNA is made of nucleotides and can be built (assembled) from the bottom up. We can easily buy oligonucleotides, short (tens to a few hundred bases) single-stranded oligomers of DNA. These can be composed to make genes (typically 1-10 thousand basepairs, bp). Pathways can be created from sets of genes related to some function. Whole genomes comprise of many pathways and genes working together to give life to the cell.

Progress made in DNA synthesis and assembly leads to progress in synthetic biology, since much of synthetic biology is dependent on the ability to encode circuits and systems on DNA.

#### Ways of joining DNA
- Chemically adding nucleotides
- Ligase
- Polymerization
- Recombination

#### Traditional cloning

We typically use plasmids as a delivery vector of choice for our circuits. These are circular pieces of DNA that typically have a few useful features. An origin of replication allows us to propagate the plasmid in bacteria. An antibiotic resistance gene allows us to select for bacteria that have the plasmid, it acts as a marker for the presence of the plasmid.

### BioBricks

The BioBrick assembly standard is an extension of traditional cloning that allows you to do modular, hierarchical assembly: a BioBrick construct can be assembled with any other BioBrick construct to create a new BioBrick. It is based on restriction enzymes, but these restriction enzymes are always the same: you only need EcoRI, XbaI, SpeI, and PstI. This standardizes the process of cloning; rather than designing each restriction reaction for every construct, the set of reactions as well as the relevant DNA sequences are predefined.

Each sequence of interest in a BioBrick is flanked on the left by EcoRI (E) and XbaI (X) and on the right by SpeI (S) and PstI (P). If you have a BioBrick, you can append or prepend another BioBrick to it by choosing which enzymes you cut the BioBricks with. You then ligate these digested products, but the scar that forms from the ligation of the cut sites is no longer a recognition sequence for E/X/S/P.

#### Synthesis of long DNA

How can we make sequences that don't exist in nature as we want? In 1979 it was shown that you can create a completely new double-stranded sequence of DNA by starting from short oligonucleotides that have matching bases that can come together and anneal in a one-pot reaction. Ligation joins the oligonucleotide backbones to create a double-stranded sequence. Feel free to read Khorana's paper describing the total synthesis of a gene from oligos (1979) in which a 207 bp piece of DNA was created.

In 1986 it was shown that you can use PCR of partially overlapping oligos to create even longer sequences (374 bp). 

#### Misc

Having libraries of parts lets us reuse components! If we find a good promoter, we would likely want to re-use that promoter in various circuits that we build.

**See Images in Week 2.** 

## <a name="week3"></a>Week 3

What are the elements and parts in synthetic biology? Cells are made of protein, DNA, metabolites and other molecules, so at a first pass, these could be the parts of synbio. However, the conceptual meaning of a protein is not really in its structure, but rather in its function. This suggests that a good, practical definition for a part is likely not going to involve the structure of a protein.

This concept of parts and interfaces (connections) between them is key to successful engineering principles. In software engineering, a great programming platform is one that easily lets you create small reusable units of code (parts) that can be as easily composed together using well-specified interfaces.

#### Parts in gene expression

We often depict a piece of DNA as a horizontal line with some annotations. In a public database of genomes you will often see annotations for the coding sequence (CDS) of a gene — that's one candidate for a part in a genome, since it's useful for biologists. But there's more to a gene than just the coding sequence!

For a promoter to wholly encapsulate its function, it must be true that it can be removed from the context it is in and put in a new one, and still function.

#### Desirables for parts

Ideally, we would have things like expression cassettes, which can be insulated from each other and are comprised of all the things we need to regulate a gene and the gene itself. Each component would be chosen from a library of characterized elements to suit our needs, regardless of the context.

- Completenesss: I can make any function.
- Scalability: I can make complex circuits.
- Homogeneity: I can measure once and it applies to the whole family.
- Composability: There are standards for part connection such that unit function is maintained or predicatble modified upon attachment.
- Invariance: And it holds in different contexts.

#### What is a part?

- Parts should encapsulate a function. How each functional unit is physically implemented is initially less important than its overall behaviour.
- Encapsulation should preserve function when connected to other parts. Functions, when properly defined, have formal specifications of the input and output dependencies of the
device. So that there are formal device boundaries.
- Parts may be made up of other parts. The definition of parts as functions allows a hierarchical view of design in which complex functions are compositions of more
elementary functions with the formal inputs and outputs made explicit.
- Parts are physical elements that can be assembled in standard ways?

Why can we make abstractions when modeling biochemical systems? When we think about gene expression in bacteria in detail, there are a lot of interactions polymerase can go through: it could bump into random molecules before it binds the  σ -factor and forms the holoenzyme; this holoenzyme might interact with various other molecules in the cell before it binds DNA and finds the promoter; the promoter can bump into other enzymes etc. We don't always really need to capture all of this "noise", similar to how we don't need to model the silicon physics of a transistor when designing chips.

To define what a part means, let's look at what a designed system — which we will want to use parts in — does. Any design moves the system through a programmed series of states. This progression is the result of many elementary processes and functions working together. Hence, it is useful to define a part as being one of these processes (functions), instead of some physical element such as a molecule or piece of DNA.

**The state of a system can be described chemically,** for example how many molecules of something there are, and where they are; what the temperature at some particular location is; what the volume of some cell compartment is. The state of a whole system could thus be described as a vector containing these numbers. **Processes — our parts — change this state by converting molecules, creating new ones, destroying them, or transporting them.**