# Principles-of-Synthetic-Biology

## Jump to...

- [Glossary](#glossary)
- [Week 1](#week1)
- [Week 2](#week2)
- [Week 3](#week3)
- [Week 4](#week4)
- [Week 5](#week5)
- [Week 6](#week6)


## Glossary



## Week 1: Introduction & Top-down design

We might be able to program cells in the same way we program computers.
The computer might be able to translate these high-level biological programs into say biological regulatory networks.

Abstract regulatory network -> DNA sequence -> into the cell.

#### Possible real-life Applications
- Detect (and kill) HeLa cancer cells (Cancer)
- Vaccination using regulated antigen/adjuvant production (infectious diseases)
- Self-timed, multi-step hiPs to B-cell differentiation (Programmable Organoids)
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

How do we go from wanting a cell to do X to having the cell do X? We need to apply principles of design to engineer the circuit that lets the cell do X. We need computational tools to analyze the circuit, get intuition about it or confirm our expectations. We can then have the DNA encoding the circuit synthesized and test it in cells. Since these circuits are likely to be complex, we will need several iterations of design, debugging, analysis, etc. This cannot happen in an ad hoc way, we need principles to follow for this to be efficient!

Exposing cells to various factors for them to mutate.

#### What is synthetic biology?
- An emerging engineering discipline that seeks to make implementation of new biological function vastly more efficient, reliable, transparent and safe.
- A field dedicated to biologically engineered solutions to world problems in health, energy, environment, and security.

#### What is different between SB and GE?
>My understanding is that synthetic biology is genetic engineering 2.0. The difference is in the approach. Whereas genetic engineering projects are usually ad hoc, synthetic biology aims to apply proper engineering principles such as standardisation, modularisation and reusability. Synthetic biologists create and use libraries of standard parts that are characterised, so they can be easily reused in projects. A part could be a gene, a terminator, a promoter, etc.

>Synthetic biology also has greater ambitions. The focus is on creating whole systems/circuits of genetic regulation. This means there is a need for computational modelling and understanding of how biological systems work. In this aspect synthetic biology is a sister of systems biology a bit like synthetic chemistry (engineering) is a sister of chemistry (science).

>You could of course argue that it's just a marketing ploy to invent a new name for something that is just the next step in genetic engineering, but the differences in the approach are quite large and a new name signifies it.

>With regards to synthesised vs. PCRed DNA: It doesn't really matter what you use in synthetic biology. However, cheap synthesis is one of the technologies that enable easier synthetic biology. The idea for the future is that you will be able to synthesise whole plasmids and chromosomes instead of having to "cut and paste" DNA. When that happens, physical parts repositories will be obsolete, but they will remain crucial in silico. Cheap synthesis is nice, but doesn't make or brake synthetic biology.

#### Top-down design

In order to deal with challenges arising from complexity of systems, engineers break down the systems into smaller, more manageable pieces hierarchically.

Biology is not necessarily Boolean (digital) as we hope. The cell uses electrical, chemical, and mechanical currencies in non-digital ways. Perhaps we need different paradigms for different components and layers.

**Registry of Standard Biological Parts - iGEM registry.**

**See Images in Week 1.** 

## Week 2: Top-down design & decomposition

Top-down design: specifying the overall function of a system at a high level, then filling in details through various levels of abstraction, down to the physical implementation of the system.

A system is made of modules, implementing individual functions such as toggles or oscillators. Each module is composed of devices that perform even simple operations such as repression or activation. At the very lowest level, we have the physical components such as DNA and proteins. We can model a system at various levels of granularity: the molecular or even atomic level, or at the level of devices.

The process of top down decomposition helps you get at the various levels of abstraction and find a suitable implementation for the system. Again, we start at a high-level description. We then think of a slightly more formal description of the system, for example using Boolean algebra, where signals are either on or off (molecules are either present or not.) This lets you map the behaviour to an abstract genetic regulatory network (GRN), where genetic components regulate each other through processes like repression and activation. Once you have an abstract GRN, you have to choose the actual genes to fill in the nodes in this regulatory network — the actual repressors and activators. These genes have DNA sequences that you can then assemble together into a physical implementation of the circuit and finally test them in cells.

### The BioCompiler

A line is a piece of DNA.
Bent arrow - a region of DNA to which polymerase can bind.

The BioCompiler is able to optimize combinatorial logic circuits (circuits without any state or memory), stateful logic circuits (like the SR latch, which has memory), and even systems with various spatial properties, such as pattern generators.

#### CAD for biology

What should we characterize? What can we characterize? For enzyme engineering, we would want to know the rates of enzymes. For synthetic biologists, measuring binding rates for transcription factors and DNA in vivo (in cells) is hard in high throughput. However, people have developed good methods for characterizing promoters, to measure the **rate of production from promoters.** We could do it with quantitative PCR (qPCR), for example, though it is medium throughput. RNA sequencing (RNAseq), could be used to see how whole pathways are affected by a circuit.

#### Top-down design B cells

In this example of top-down design we look at a system where we want to engineer stem cells to produce β cells in Type I diabetes patients. In Type I diabetes, β cells are killed by the immune system. At a high level, we want a system that maintains a population of β cells using auto-regulated differentiation of stem cells (homeostasis of the β cell population).

To achieve this, we can have stem cells that auto-regulate their own division. If there are too many, the division is inhibited. At the same time, these stem cells can differentiate through various stages into β cells, which are then removed by the immune system. We add auto-regulation to the differentiation stage to control its rate: too many β cells will cause there to be less differentiation.

#### Challenges to design

As a new engineering discipline, we need to create new rules and standards! This should happen in a cycle of designing, building, testing and learning. 
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

## Week 3: Parts and composition

What are the elements and parts in synthetic biology? Cells are made of protein, DNA, metabolites and other molecules, so at a first pass, these could be the parts of synbio. However, the conceptual meaning of a protein is not really in its structure, but rather in its function. This suggests that a good, practical definition for a part is likely not going to involve the structure of a protein.

This concept of parts and interfaces (connections) between them is key to successful engineering principles. In software engineering, a great programming platform is one that easily lets you create small reusable units of code (parts) that can be as easily composed together using well-specified interfaces.

#### Parts in gene expression

We often depict a piece of DNA as a horizontal line with some annotations. In a public database of genomes, you will often see annotations for the coding sequence (CDS) of a gene — that's one candidate for a part in a genome, since it's useful for biologists. But there's more to a gene than just the coding sequence!

For a promoter to wholly encapsulate its function, it must be true that it can be removed from the context it is in and put in a new one, and still function.

#### Desirables for parts

Ideally, we would have things like expression cassettes, which can be insulated from each other and are comprised of all the things we need to regulate a gene and the gene itself. Each component would be chosen from a library of characterized elements to suit our needs, regardless of the context.

- Completenesss: I can make any function.
- Scalability: I can make complex circuits.
- Homogeneity: I can measure once, and it applies to the whole family.
- Composability: There are standards for part connection such that unit function is maintained or predictable modified upon attachment.
- Invariance: And it holds in different contexts.

#### What is a part?

- Parts should encapsulate a function. How each functional unit is physically implemented is initially less important than its overall behaviour.
- Encapsulation should preserve function when connected to other parts. Functions, when properly defined, have formal specifications of the input and output dependencies of the
device. So that there are formal device boundaries.
- Parts may be made up of other parts. The definition of parts as functions allows a hierarchical view of design in which complex functions are compositions of more
elementary functions with the formal inputs and outputs made explicit.
- Parts are physical elements that can be assembled in standard ways?

Why can we make abstractions when modeling biochemical systems? When we think about gene expression in bacteria in detail, there are a lot of interactions polymerase can go through: it could bump into random molecules before it binds the σ -factor and forms the holoenzyme; this holoenzyme might interact with various other molecules in the cell before it binds DNA and finds the promoter; the promoter can bump into other enzymes, etc. We don't always really need to capture all of this "noise", similar to how we don't need to model the silicon physics of a transistor when designing chips.

To define what a part means, let's look at what a designed system — which we will want to use parts in — does. Any design moves the system through a programmed series of states. This progression is the result of many elementary processes and functions working together. Hence, it is useful to define a part as being one of these processes (functions), instead of some physical element such as a molecule or piece of DNA.

**The state of a system can be described chemically,** for example how many molecules of something there are, and where they are; what the temperature at some particular location is; what the volume of some cell compartment is. The state of a whole system could thus be described as a vector containing these numbers. **Processes — our parts — change this state by converting molecules, creating new ones, destroying them or transporting them.**

**See Images in Week 3.** 

## Week 4: Gene expression and regulation & Autoregulatory feedback

To remind you, for ease of design, we define parts as processes. While we manufacture with DNA, it is not a good substrate for designing. We want to design with abstractions that allow us to separate functions and compose modules with ease — something we can do with processes but not physical pieces of DNA.

We want to design with functions and not model details of the processes underlying those functions unless we have to. 

The essential function of an enzyme is its activity: it converts one molecule to some other molecule.

Parts are processes. Processes are what we want to design with. These processes take state variables — say, the concentration of something — and turn them into a rate of change of the state variable. An enzyme might carry out this process, but it is not often useful for designing with; an enzyme won't "work" if the substrate is not present! Designing with processes in mind helps us capture this dependency with ease.

Compositors aggregate the effects of parts. These are the total rates of change of some state variable, across the whole system in the framework of ordinary differential equations (ODEs). We use ODEs to describe the dynamics of well-mixed biochemical systems mathematically. There is one compositor for each state variable, for example the concentration of each distinguishable chemical species. Pyruvate (the anion of pyruvic acid, an important metabolite) in the cytosol is separated from pyruvate in the mitochondrion and we can essentially distinguish them!

#### Positive and Negative feedbacks - Autoregulatory feedback

Positive feedback — when the protein promotes its own production — might sound like a good thing, but turns out this is not what we are looking for; we'll see later that positive feedback can actually decrease the response time!

Negative feedback — when the protein represses its own production — is what we need! We'll see how this works in the next section.

Negative autoregulation is one of the most common motifs one can find in nature. In negative autoregulation (NAR) the production of output of a system is inhibited by the output itself, a form of negative feedback.

In positive feedback, the protein promotes its own production.

**See Images in Week 4.** 

## Week 5: Simple digital devices & Cascades

Combinational logic refers to digital logic that carries out a function for which the output depends only on the current inputs (that is, it has no state). The digital abstraction simplifies our thinking of system design and enables us to create sophisticated devices by using simple digital elements with properties such as signal restoration, which enable them to be easily composed together.

#### The NOT gate

Let's consider the NOT gate, also known as an inverter. The inverter turns an input of 0 to an output of 1 and an input of 1 to an output of 0.

To implement this genetically, we first need to define our signals. One convenient way to define a signal is to say that a signal is the concentration of a chemical species, for example a protein. If the concentration of a protein in a cell is low, it represents the signal 0 and if the concentration is high it represents the signal 1. This is similar to electronics, where a low voltage typically represents a 0 and a high voltage a 1. Note how in both examples we are converting a continuous value to a discrete one.

There are other signals that synthetic biologists use, for example PoPS ([RNA] polymerases per second) or RiPS (ribosomes per second) could be defined as input and output signals. These signals show the rate at which these enzymes move along the DNA or RNA, as appropriate. A strong promoter causes a high PoPS along the gene. A repressor reduces the PoPS of the gene it regulates.

#### The IMPLIES gate

The NOT gate can be enhanced with functionality by introducing an inducer to the repressor. A common example of an inducer is a small molecule that inhibits the repressor by binding it; this binding causes the repressor to no longer function as an inhibitor of gene expression. For example, a repressor protein bound by an inducer might lose its ability to bind DNA.

### Cascades

In order for a digital abstraction of transcriptional regulation to hold, it must be true that activators and repressors are expressed either at high ("ON") or low ("OFF") levels. But this notion begs the question of what concentration threshold each regulatory protein must be above/below to ensure that we actually get digital behavior. Such thresholds often depend on the activity of the output protein, whether it is a transcription factor, an enzyme, or involved in some other process.

#### Functional Cascade

It would be ideal to start with individual parts, predict their behavior when composed together, build a cascade and have it work right off the bat. Unfortunately, as we have seen in the previous sections, this goal is still very difficult to realize. Taking the opposite approach, a team in Ron's laboratory managed to build the functional cascade with parts on hand, then decided to go back and analyze its properties with regards to sensitivity, signal restoration, noise propagation/attenuation, and timing delay. First, they started with a simple system in which the Tet repressor (TetR) binds and represses transcription of EYFP. TetR is sensitive to the small molecule aTc, a homolog of tetracycline. In the presence of aTc, TetR's DNA binding domain is destabilized, and TetR can no longer bind the Tet operator (TetO) sequence in the pL(tet) promoter.

One pervasive issue in synthetic biology is that we don't know how every single element of our circuits interacts with every other element (or with the cell for that matter). When building electronic circuits, electrical engineers can use wires to direct current where it needs to go. Such wires are not present in biology - and while we like to assume that we have some aspect of modularity/orthogonality with our parts, that's not actually the case. Thus, we need to do better analysis of parts to predict how they may interact with each other in order to better model higher-order circuits.

One important question when analyzing our functional cascade is how the noise propagates. By looking at just the mean behavior of cells expressing the cascade, we miss some of the underlying reasons why the cascade might fail. One of the most common measures of noise is the **coefficient of variation** ( CV ), which is given by the ratio of a sample's standard deviation ( s2 ) to its mean ( X¯¯¯¯ ):

The effect of the noise on our function can depend on the design specification. For example, if all we care about is getting cells to express highly or lowly, then the noise in the transition region may not matter so much. However, there may be cases when we do care about the transition region - for instance if we would like to have some aspect of tunability or analog behavior in our circuits. If we care about the synchronization of cells as they pass through some transition region from low to high output (eg during embryogenesis/development), then the noise during this transit will be a major problem.

**See Images in Week 5.** 

## Week 6: Hazards & Feed-forward motifs

### The Cancer classifier

We desire to make abstract representations of parts, and to be able to use these abstractions to define modules that can be reliably composed to make any system. As an example, we considered a simple cascade of transcriptional repressors. We discussed how we could make models for the individual repressor parts, then parameterize these models in order to find some mathematical description of the system. This could then be used to try to simulate the effect of adding multiple parts together in a cascade. In terms of models, we discussed the benefits/drawbacks of having a detailed, physical, **mechanistic model** vs a high-level **phenotypic model** where mechanisms are not used.

Another major topic we discussed was how to characterize modules. First, we must consider the chassis organism being used - is it prokaryotic or eukaryotic?, what species?, etc. A powerful way to analyze modules is in terms of their **input-output behavior**. We accomplished this by varying inducer given to cells and measuring the output of the circuit, represented by a fluorescent protein. Ideally, we could use input-output matching to predict the behavior of several composed parts, but unfortunately we aren't quite there yet.

One promising application of synthetic biology is in precision medicine. Here, we discuss a circuit that is designed to classify cells as cancerous or not. This was actually implemented in a collaboration between Ron's and Yakovi Benenson's laboratories, in which a circuit was made to classify cells as HeLa (the most widely used cancer cell line) or human embryonic kidney (HEK) cells (a poplar and well-studied cell line used in cell biology research).

As Adam put it, many common cancers have been "profiled to death" in recent years. For example, check out The Cancer Genome Atlas (TCGA - link to their data portal). For each cancer studied, researchers have analyzed samples from hundreds of real patients. They have collected data on the genome sequences, single nucleotide polymorphisms (SNPs), DNA methylation patterns, and mRNA/miRNA transcription profiles of tumor samples from all these patients and have even provided matched clinical data. This provides a wealth of **biomarkers** that a synthetic biologist could use in the design of sensors for classifying cancer.

Perhaps the easiest mammalian cell property to measure is RNA-related and protein-related. This is because RNA and proteins typically make up the physical parts of our synthetic circuits. We can build sensors that interact with these molecules and then use the resulting state change from binding to issue a signal that indicates that a biomarker has been detected. Combining the outputs of these sensors allows us to detect a pattern of gene expression that denotes a cancerous cell. One important question is how many genes should we have to detect? It has been estimated by some studies that there are upwards of 30,000 genes in the human genome - even using just 1% of the genome means we would have to build hundreds of sensors and link all of their outputs together into one massive logic function!

In reality, we only need about 3-5 genes differentially expressed in cancer and healthy cells to tell the difference.

One important question to ask is what does high vs low mean, especially in the context of differential gene expression in a disease such as cancer? There is absurd heterogeneity in cancer. Between two people with the same type of cancer, the profiles of gene expression between their cancers can be wildly different for many proteins. Even cells that are both a part of the **same tumor** can have wildly different expression levels! This presents a problem when attempting to detect cancer biomarkers, and is something that we have to consider when designing circuits to do multi-input sensing.

Typically, we can take a 10-fold change from normal is a good metric for minimum difference between a "normal" and transformed gene state. While this is generally a large enough difference, we really need to consider the **mean and variance** of expression in as many cells as possible in tumors from different people. If a 10-fold increase in expression is within the normal range of gene expression for a healthy adult, then we will need our biomarker threshold to, say, 100-fold above normal.

#### Comparison of cascades

In this segment, we discuss the strategy of using a cascade of activators to delay circuit output. In the previous segment, we discussed a problem of speed mismatches between different signalling pathways feeding into a logic gate with multiple inputs. In particular, we discussed a situation in which the expression of an activator branch signal was much more rapid than the repressing branch signal.

If a certain branch is too fast, we can add more activators in series to delay the signal, allowing time for the other branch to propagate its signal. In the video above, we consider a modified activator branch that creates a delay. Note: the input into the branch (formerly B ) is now represented by R2 to emphasize that the input into the cascade is a repressor rather than an activator.

#### Cascades wrap-up

In this paper, the researchers built a classifier circuit to determine if cells are HeLa or not. The core functionality of this circuit is RNA interference, a phenomenon seen in most eukaryotic cells. This circuit will be discussed more in depth later in the course when we talk about RNA circuits.

The classifier works by using microRNA (miRNA) as biomarkers to directly repress circuit elements. If any marker miRNAs are high in the cell, they will bind target mRNA in the circuit, repressing translation and facilitating mRNA degradation. The researchers identified two sets of miRNAs: "low" and "high".

"Low" miRNAs were identified as being expressed lowly in HeLa cells but not other cell types.
Conversely, "high" miRNAs are high in HeLa cells but not in others.

First, Ron discussed how the HeLa classifier had adapted for a breast cancer model and is being used to drive replication of the oncolytic herpes simplex virus (HSV)-1.

What we alluded to in the previous segment was a hazard in the HeLa classifier. In mismatched cells, the high miRNAs will not be high, and thus the repressor will be expressed and repress the output. However, as we have seen before, repression cascades can lead to a hazard because the initial levels of the repressor are low. Thus, to improve the circuit, the researchers added an activation element to the circuit and a hybrid promoter for the output, similar to what we did in the previous section with our generic classifier.

### Feed-forward motifs

**Feed-forward** circuits have a network structure in which some starting node initiates a signal through multiple branches that later converge. This allows for the generation of pulses as well as other interesting behavior. This will be the main topic of Lecture 12.

**Toggles** are systems that can switch between two or more states. Toggles allow us to store memory of the last input that the system was given. An important aspect of toggle switches is the stability of their switchable states, particularly with respect to biological noise. This will be the topic of Lecture 13.

**Oscillators** are important circuits that have a periodic nature. The output of these devices increases and decreases over time, leading to interesting sinusoidal-like behavior. Oscillators are particularly important for timing and creating clocks. This will be the topic of Lectures 14 and 15.

#### Engineering Pulse Characteristics

In this segment, Ron discussed the experimental data for the pulse generator system and a model for the pulse characteristics. The experimental data (presented in the left panel) is the result of testing several different pulse generator constructs. High-throughput genetic assembly methods allow the creation of many circuit variants, which - due to the current uncertainty in biological system design -- is one of the best ways to get functional genetic circuits.

Two aspects of the pulse response were emphasized: the amplitude (or gain) and duration. The initial design that was attempted showed no pulse response at all. In order to understand why, the researchers built a mathematical model to describe the system and ultimately used it to identify the key parameters affecting the pulse gain. The pulse gain is the amplitude of the pulse response relative to the background levels of GFP (averaged for all cells).

### Nature's devices

In the "development" of regulatory networks in cells, the designer is evolution. We know that due to the driver of natural selection/survival of the fittest, organisms are not composed of completely random networks; the constant pressure to survive and be efficient means that only certain network structures are selected for or **enriched**. We seek to identify these common patterns of network connections (topologies) because they are likely to have useful functionalities.

So far, there have been two major approaches to studying regulatory networks in cells. In the **bottom-up** or reductionist approach, knockout or overexpression of particular elements is performed to study the relative increase/decrease in expression of downstream elements in a pathway or interaction network. So if we wanted to understand the interaction between X and Y, we could knockout X and observe the expression of Y. If Y increased in its expression, then we could hypothesize that X⊣Y.

#### Coherent feed-forward loops (cFFLs)

Let us define a feed-forward loop as a network motif where one node regulates two or more branches that later converge at a downstream node. Simply put, feed-forward loops are defined by multiple edges or unique paths connecting two nodes. In their work, Shmoolik and Uri classified all different types of FFLs with three elements (the simplest possible FFLs).

Coherent feed-forward loops (cFFLs) are FFLs with consistent logic from one branching node to the other. That is: if one branch is outputting a "HIGH" signal, the other branch should also ultimately produce a "HIGH" signal (or both branches produce a "LOW" signal.) Let's examine a couple of the coherent FFLs in the segment video above to cement this notion. 

#### Incoherent feed-forward loops (iFFLs)

In this segment, we discuss incoherent feed-forward loops (iFFLs). In these circuits, the signal through different arms have opposing effects on the output. For iFFLs, we will only look at AND logic at the convergence point, but note that using an OR gate will have the interesting effect of making the steady-state always be on instead of off.

### Modeling a cFFL

As we have seen in the examples above, the biggest uses of cFFLs are noise rejection and delay. But what do we need for these functions? First, we need sigmoid in transfer functions for all activation and repression relationships. This makes the response of C to B be ~zero for low expression values of B . Small variation in A will then not cause C to be expressed, because it will not sufficiently activate B .

In this segment, Adam wraps up the discussion of FFLs with some thoughts about motifs, which will lead us into the next exciting topic — the toggle switch!

### Segue: motifs

Why do certain motifs appear more often than random? There may be some functional reason evolution has selected for FFLs, such as useful functionality. In addition, it is possible that FFLs are "easily findable" in evolution's methods to solve a problem, such as energy consumption optimization. We must remember that there is always an element of bias in the randomness of biology that is difficult to predict. It is possible that FFLs are not particularly noteworthy in biology, and just by chance cells happen to make these motifs more than what we think is random.
