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
  - Heuristic
    - A rule of thumb for solving a problem
    - It is a set of guidelines that often works to solve a problem
  - Algorithm

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

- Logic – PL vs FOL, translation of English statement to FOL statement
  - PL assumes the world contains facts, FOL assumes the world contains objects, relationships, and function.
  - FOL has more elements than PL which are variables, functions, and quantifiers.
  - FOL provides increased expressive power in comparison with PL

- Knowledge Representation – Logic, ontology, agents
  - Ontology
    - The study of existence, of all kinds of entities that make up the world
    - A representation of a shared domain of interest that utilizes a common vocabulary to describe the classes, relations, functions and other similar objects of interest
    - Why Develop an Ontology
      - To share common understanding of the structure of information among people or software agents
      - To enable reuse of domain knowledge
      - To make domain assumptions explicit
      - To separate domain knowledge from the operational knowledge
      - To analyze domain knowledge
    - Knowledge Engineering Methodology
      1. Determine the domain and scope of the ontology
      1. Consider re-using existing ontologies
      1. Enumerate important terms in the ontology
      1. Define the classes and class hierarchy
      1. Define the properties / slots /roles of the classes
      1. Define the facets / role restrictions
      1. Create instances
  - Agents
    - An agent is anything that can be viewed as perceiving its environment through sensors and acting upon that environment through actuators.
    - Four agent structures
      - Simple reflex (Not coming out) agents
      - Model-based reflex agents
      - Goal-based agents
      - Utility-based agents

---

### Chapter 3 & 4 Production and Expert Systems

- Major components in an expert system
  - Knowledge base
  - Inference Engine
  - Explanation Facility
- Typical design elements that constitute the expert system structure
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

## Chapter 6 - Uncertainty

- **Differentiate between conjunctive and disjunctive rules**
  - Conjunctive rule will only fire when both of the facts are true or both of the condition are satisfied. However, disjunctive rule will fire when either of the facts or either of the condition is true.
  - In order to calculate certainty factor for conjunctive rule, minimum value of certainty factor among the facts is used. While for disjunctive rule, maximum value of certainty factor among the facts is used.
- **Compute the certainty factor of a hypothesis given several rules with individual certainty factors**
- **Interpret the resulting numerical answer in regular English**

  Name | Certainty Value
  -----|----------------
  <p align="center">Definitely not</p> | -1.0
  <p align="center">Almost certainly not</p> | -0.8
  <p align="center">Probably not</p> | -0.6
  <p align="center">Maybe not</p> | -0.4
  <p align="center">Unknown</p> | -0.2 to +0.2
  <p align="center">Maybe</p> | +0.4
  <p align="center">Probably</p> | +0.6
  <p align="center">Almost certainly</p> | +0.8
  <p align="center">Definitely</p> | +1.0