# CSC3026 Artificial Intelligence Examination Review (March 2017)

## Details

- Date and time: 12th July 2017, 9.00am
- Duration: 2 hours
- Part A: ONE question (30 marks)
- Part B: Choose TWO out of FOUR questions (2 x 10 marks)

## Coverage

## Chapter 1 - Fundamental issues of AI

### Typical characteristics and problem-solving approaches of an AI problem

- **Typical Problem Characteristics**
  - Tend to be large
  - Computationally complex, cannot be solved by straightforward algorithms
  - The problem domain requires a large amount of human expertise
- **Problem-solving approaches of an AI problem**
  - Heuristic is a rule of thumb for solving a problem. It is a set of guidelines that often  works to solve a problem. Can do things out of order.
  - Algorithm has to execute them in a specific way. If no input, it is not going to work. Order and inputs are important.


### Problem formulation – five attributes to consider

1. Initial State
    - Described by an initial state and the set of possible actions available (operators)
    - A path is any sequence of states connected by a sequence of actions
2. Action Function
    - A description of the possible actions available to the agent
    - Given a particular state s, ACTIONS(s) returns the set of actions that can be executed in s
3. Transition Model
    - A.K.A. Result Function
    - Description of what each action does
    - Specified by a function RESULT(s,a) that returns the state that results from doing action a in state s
4. Goal Test
    - Determines whether a given state is a goal state
5. Path Cost
    - Assigns a numeric cost to each path
    - Problem-solving agent chooses a cost function that reflects its own performance measure
    - Relevant if more than one path leads to the goal, and we want the shortest path

---

## Chapter 2 - Search

- **Differentiate among the search algorithms**
  - Tree Search Algorithms
  - Graph Search Algorithms
  - Uninformed Search / brute force / blind search strategies
    - Breadth First search
      - Completeness: Yes
      - Time complexity: O(b ^ d)
      - Space complexity: O(b ^ d)
      - Optimality: Yes
      - Cannot be used to solve any but the smallest problems owing to exponential complexity
    - Uniform-Cost search
      - Completeness: Yes
      - Time complexity: O(b ^ 1 + (C*/e))
      - Space complexity: O(b ^ 1 + (C*/e))
      - Optimality: Yes
    - Depth First search
      - Completeness: No (unless search space is finite and no loops are possible)
      - Time complexity: O(b ^ m)
      - Space complexity: O(bm)
      - Optimality: No (unless search space is finite and no loops are possible)
    - Depth-limited search
      - Completeness: Yes (No if l < d)
      - Time complexity: O(b ^ l)
      - Space complexity: O(bl)
      - Optimality: Yes (No if l > d)
    - Iterative Deepening search
      - Completeness: Yes (like BFS)
      - Time complexity: O (b ^ d) (like DFS)
      - Space complexity: O (b ^ d) (like DFS)
      - Optimality: Yes (like BFS)
  - Informed Search
    - Hill climbing search
    - Best-first search
      - Greedy best-first search
        - Completeness: No
        - Time complexity: O (b ^ m)
        - Space complexity: O(b ^ m)
        - Optimality: No
      - A* search

- **Informed vs uninformed search**
  - Informed search such as A* search uses heuristic function but uninformed search doesn't use heuristic function
  - Uninformed search just brute force which means searching without information but informed search searches with information

- **Evaluation function**
  - Informed search such as best-first search uses an evaluation function f(n) for each node
    - f(n) is seens as cost estimate
    - Expand node with the lowest evaluation

- Game tree
- **pruning operations and conditions**
- **justify search/pruning recommendation**
  - Alpha-beta pruning is a simple algorithm that identifies moves that are not beneficial, and then removes them from the game tree
  - The higher in the game tree that branches are pruned, the greater the effect in minimizing the search space
  - During DFS, maintain two variables called alpha and beta
    - alpha variable defines the best move that can be made to maximize
    - beta variable defines the best move that can be made to minimize
  - When traversing the game tree, if alpha >= beta
    - Opponent's move forces Player into a worse position than the current best move
    - Stop evaluating this branch any further
    - Prune

---

## Chapter 3 - Logic and Knowledge Representation

- **Logic**
  - A formal language that consists of syntax and semantic.

- **Discuss the limitations of propositional logic**
  - Operates with constant object only
  - No domain context and no domain variable
  - Cannot say "all", "there exist" etc
  - Propositional logic only limited to facts
  - Some knowledge are hard or impossible to encode in the propositional logic
    - Statements referring to groups of objects requires exhaustive enumeration of group
    - Statements about similar objects and relations need to be enumerated

- **Primary goal of knowledge representation**
  - To enable an intelligent entity (program) with a knowledge base to allow it to make intelligent decisions about its environment.

### Logic – PL vs FOL, translation of English statement to FOL statement

- PL assumes the world contains facts, FOL assumes the world contains objects, relationships or properties, and function.
- FOL has more elements than PL which are variables, functions, and quantifiers.
- FOL provides increased expressive power in comparison with PL

- **PEAS**
  - Performance
  - Environment
  - Actuators
  - Sensors

- **Wumpus World Problem Foundation**
  - Transition model not known
    - Does not know which Forward actions are fatal
    - Discovering the locations of pits and wumpus completes the agent's knowledge of the transition model
  - Main challenge is its initial ignorance of the configuration of the environment
  - Overcoming this ignorance seems to require logical reasoning

- **Basic element of FOL**
  - Constant symbols -> Objects
  - Predicate symbols -> Relations
  - Function symbols -> Functional relations
  - Variables
  - Connectives
  - Equalities
  - Quantifiers

- **Diagnostic rule**
  - Infer cause from effect
- **Causal rule**
  - Infer effect from cause (model based reasoning)

### Knowledge Representation – Logic, ontology, agents

- **Logic**
  - Provides the formal structure and rules of inferences, without logic knowledge representation is vague and statement could be contradictory.

- **Ontology**
  - The study of existence, of all kinds of entities that make up the world
  - A representation of a shared domain of interest that utilizes a common vocabulary to describe the classes, relations, functions and other similar objects of interest
  - Ideal for sharing knowledge over the Internet
  - **Why Develop an Ontology**
    - To share common understanding of the structure of information among people or software agents
      - Agents can extract and aggregate information from different Web sites. The agents can use this aggregated information to answer user queries or as input data to other applications.
    - To enable reuse of domain knowledge
      - For example, models for many different domains need to represent the notion of time
    - To make domain assumptions explicit
      - Makes it possible to change these assumptions easily if our knowledge about the domain changes
    - To separate domain knowledge from the operational knowledge
    - To analyze domain knowledge
  - Development process
    - Define classes in the ontology
    - Arrange the classes in a taxonomic (subclass-superclass) hierarchy
    - Define properties / slots / roles by describing their allowed values (facets / role restrictions)
    - Fill in the values for the properties / slots / roles of individual instances

  - **Knowledge Engineering Methodology**
    1. Determine the domain and scope of the ontology
    1. Consider re-using existing ontologies
    1. Enumerate important terms in the ontology
    1. Define the classes and class hierarchy
    1. Define the properties / slots /roles of the classes
    1. Define the facets / role restrictions
    1. Create instances

- **Agents**
  - Environment
    - Fully observable vs Partially observable
    - Deterministic vs Stochastic
    - Episodic vs Sequencial
    - Static vs Dynamic
    - Discrete vs Continuous
    - Single-agent vs Multi-agent
  - Agent program's difference with agent function
    - Agent function takes the entire percept sequence
    - Agent program takes just the current percept as its input since nothing more is available from the environment

  - An agent is anything that can be viewed as perceiving its environment through sensors and acting upon that environment through actuators.
  - Four agent structures
    - Simple reflex (Not coming out) agents
    - Model-based reflex agents
      - Ideal for tackling partially observable environments
      - Current percept is combined with the old internal state to generate the updated description of the current state, based on the agent's model of how the world works.
    - Goal-based agents
      - Goal information
      - The agent program can combine goal information with information about the results of possible actions (the same information as was used in the model-based agent) in order to choose actions that achieve the goal
    - Utility-based agents
      - Performance measure of how happy
      - If one world state is preferred to another, then it has higher utility for the agent.
  - **Describe the qualities an ideal agent should possess**
    - A rational agent chooses whichever action that is expected to maximize the value of performance measure given the percept sequence to date and prior knowledge of the environment. The definition requires information gathering to maximim future rewards. It also requires the agent to learn from percepts hence extending prior knowledge. The agent must be autonomy to compensate for incorrect prior knowledge through updating from environment.

---

### Chapter 3 & 4 Production and Expert Systems

- **Features of production systems that are considered advantages**
  - Ease of expression
    - Nature way for domain-specialists or expert to express themselves, to represent great amount of knowledge.
  - Intuitive in nature
    - IF-THEN nature is very intuitive way for humans to express themselves.
  - Simplicity
    - Production rules are very easy to develop and modify easy to understand and consistent with English language forms of expression

- **What is conflict resolution and why is it necessary**
  - Conflict resolution is a method for choosing a rule when more than one rule can be fired. When several rules are candidate for matching the antecedent / IF condition of a production rule, there must be a strategy to choose the most appropriate rule among them. There are 6 types which are:
    - Fire the first rule that matches the contents of the memory
    - Fire the rule with the highest priority
    - Fire the most specific rule
    - Fire the most recently used rule
    - Fire the most recently added rule
    - Don't fire a rule that has already fired
  - Why? To maintain good functioning of the system, it is important to resolve conflicts. As such, system will be able to provide an answer.

- **Discuss the problems of conflicts resolutions strategy "fire all rules"**
  - Conflict resolution is a method to define the strategy to choose the most appropriate rule. However, "fire all rule" will give rise to more conflicts because rules will contradict with each other. It is like having no strategy. Therefore, by using "fire all rule", it might possible looping at rules for those contradicting rules, and have low efficiency because big amount of rules needed to fire.

- Compare between forward chaining and backward chaining

| Forward Chaining | Backward Chaining |
|------------------|-------------------|
| Data driven | Goal Driven |
| Reasoning from facts to conclusion | Reasoning in reverse from a hypothesis, from a potential conclusion to the proven, to the facts that support the hypothesis.|
| May do work that is irrelevant to goal | More efficient |
| Good for planning, design and process monitoring | Suitable for diagnosis |
| Find possible conclusions supported by given facts.| Find facts that supports a hypothesis |

- **Give an example of a typical type of production system that would utilise Forward Chaining and explain why this is so.**
  - Website's search engine. A website search engine prompts user for input and search for any relevant website related to the keyword. It then returns the list of related website for the user to pick. When we search for something, we still do not have a goal in mind but based on the search result, we would pick one that is closest to what we think is the goal. Hence, there are irrevant work that is done (websites that are not chosen).

- **Do the same with Backward Chaining.**
  - Medical diagnostic system. Medical staffs specify the illness on the system which then system reutnrs a list of symptoms on the illness and possible solutions, which then the staff can take action based on the list. It first asks for the illness, which is the goal. The system is asked to prove "Is the patient 125 having a fever?". It will work backwards to prove the illness. Once proven, it will provide a list of possible solutions.

- **Major components in an expert system**
  - Knowledge base
  - Inference Engine
  - Explanation Facility

- **Typical design elements that constitute the expert system structure**
  - Agenda
  - Knowledge acquistion facility
  - Knowledge base
  - Inference engine
  - User interface
  - Explanation facility
  - Working memory

- **Differentiate the various responsibilities of each design element**
  - Agenda
    - A prioritized list of rules created by the inference engine, whose patterns are satisfied by facts / objects in working memory
  - Knowledge acquisition facility
    - An automatic way for the user to enter knowledge in system rather than by having the knowledge engineer explicitly code the knowledge
  - Knowledge base
    - Also called production memory in a rule-based expert system
    - Production rules
  - Inference engine
    - Makes inferences by deciding which rules are satisfied by facts / objects, prioritizes the satisfied rules and executes the rule with the highest priority
    - Two general methods of inferencing used as problem-solving strategies of expert systems
      - Forward chaining
      - Backward chaining
  - User interface
    - Mechanism by which the user and the expert system communicate
    - May be a simple text-oriented display or a sophisticated high-resolution bit-mapped display
  - Explanation facility
    - Key feature of an expert system
    - Explains the reasoning of the system to the user
    - A history of the activated rules and contents of working memory can be maintained in a stack
  - Working Memory
    - A global database of FACTS, used by the rules

- **Explain how these design elements interact**
  - **Working Memory and Knowledge Base**
    - Facts do not interact with one another
    - "the light is green" FACT has no effect on "the light is red" FACT
    - Knowledge of traffic lights says that if both facts are simultaneously present, then there is a malfunction in the traffic lights
  - **Working Memory and Inference Engine**
    - If “the light is green” FACT is in working memory, the inference engine will notice that this fact satisfies the IF / conditional / LHS part of the “green light” rule and put this rule on the Agenda
    - If a rule has multiple patterns, then all of its patterns must be simultaneously satisfied for the rule to be placed on the agenda
    - Certain patterns may even be satisfied by specifying the absence of certain facts in working memory
    - The THEN / consequent / RHS part of the rule is a list of actions to be executed when the rule fires
    - When the “red light” rule fires, its action “stop” is executed
    - When the “green light” rule fires, its action is “go”
    Specific actions usually include the 
    - Addition / removal of facts from working memory 
    Printing of results
    - Format of these actions depends on the syntax of the expert system language

- **Analyze and apply the appropriate inference mechanism in a problem scenario**
  - Can the problem be solved effectively by conventional programming
  - Is the domain well bounded?
  - Is there a need and a desire for an ES?
  - Is there at least one human expert willing to co-operate?
  - Can the expert explain the knowledge so that it is understandable?
  - Is the problem-solving knowledge mainly heuristic and uncertain?
- **justify design/inference decision/recommendation**

- **How are ES different with conventional programs**

- Conventional programs are procedural and expert system is determined by correct matching with data for forward chaining and correct matching with goals for backward chaining.
- Es input are flexible as opposed to the rigid design of conventional programs.
- Es utilize pattern matching to decipher the meaning of input while conventional program rely on specific input format. There is usually no explaination for conventional program on how it obtains the result but ES will have explanation facility to explain the reasoning for the result.

- **What is meta-rule?**

  - A meta rule is a rule that governs other rule
  - Meta tell when to use, why used and how to use that certain rule.
  - Why they were included in the KB?
    - Meta knowledge can take if or then part of meta-rule to justify conclusion

- **Knowledge engineering process**
  1. KE established dialogue with human expert in order to elicit expert's knowledge
  1. KE then codes the knowledge explicitly into KB
  1. Expert then evaluates the ES and gives feedback to KE
  1. Process is repeated until system's performance is judged to be satisfactory by the expert.

- **What is knowledge acquisition and why is it considered a "bottleneck in AI"**

  - Knowledge acquistion refers to the acquistion of knowledge from a human expert and other sources. It is carried out by knowledge engineer who extracts expertise by conducting extensive interviews with human experts. The KE process is time consumming and labour intensive. The KE may have to interview the expert several times. The process is step by step and sequential, if no interview is done, the prototype cannot be constructed. Hence, every stage needs to be completed before the next stage begins. Therefore, this process is slow and often described as fluid flow from a bottle.

- **Advantages of Expert System**
  - Increased availability
    - Mass production of expertise since it can be made available on a computer
  - Reduced cost
    - Average cost of providing expertise is greatly lowered
  - Reduced danger
    - ESs can be deployed in hazardous environments

- **Disadvantages of expert system**
  - Common sense
    - In addition to a great deal of technical knowledge, human experts have common sense. It is not yet known how to give ESs common sense
  - Creativity
    - Human experts can respond creatively to unusual situations, ESs cannot
  - Learning
    - Human experts automatically adapt to changing environments; ESs must be explicitly updated. Case-based reasoning and neural networks are methods that can incorporate learning

- **Characteristic of ES**
  - High performance
    - Expert system must be capable of responding at a level at least equal to, or better than a human expert
    - Quality of advice must have high degree of integrity
  - Adequate response time
    - Expert system must perform in a reasonable time, comparable to or better than the time required by an expert to reach a decision
    - Time constraints especially critical in the case of real-time systems
  - Good reliability
    - Expert system must be reliable and not be prone to crashes

## Chapter 6 - Uncertainty

- **Differentiate between conjunctive and disjunctive rules**
  - Conjunctive rule will only fire when both of the facts are true or both of the condition are satisfied. However, disjunctive rule will fire when either of the facts or either of the condition is true.
  - In order to calculate certainty factor for conjunctive rule, minimum value of certainty factor among the facts is used. While for disjunctive rule, maximum value of certainty factor among the facts is used.
- **Compute the certainty factor of a hypothesis given several rules with individual certainty factors**
- **Interpret the resulting numerical answer in regular English**

  | <p align="center">Term</p> | <p align="center">Certainty Factor</p> |
  -----|----------------
  |<p align="center">Definitely not</p> | <p align="center">-1.0</p> |
  |<p align="center">Almost certainly not</p> | <p align="center">-0.8</p> |
  |<p align="center">Probably not</p> | <p align="center">-0.6</p> |
  |<p align="center">Maybe not</p> | <p align="center">-0.4</p> |
  |<p align="center">Unknown</p> | <p align="center">-0.2 to +0.2</p> |
  |<p align="center">Maybe</p> | <p align="center">+0.4</p> |
  |<p align="center">Probably</p> | <p align="center">+0.6</p> |
  |<p align="center">Almost certainly</p> | <p align="center">+0.8</p> |
  |<p align="center">Definitely</p> | <p align="center">+1.0</p> |