# Interdependency in AI Decision Making: Comprehensive Summary

**Authors:** Ellie F. Baker and Munther Dahleh  
**Institution:** MIT Institute for Data Systems and Society

## 1. A Model of AI Decision Making

### Core Components Architecture

```mermaid
graph TB
    subgraph "Algorithm Development"
        CSW1[Current State<br/>of the World] --> PCS[Perception of<br/>Current State]
        CSW1 --> D1[Data]
        CSW1 --> OBJ1[Objective]
        
        PCS --> MS[Model Selection]
        D1 --> MS
        OBJ1 --> MS
        
        MS --> ALG[Algorithm]
    end
    
    subgraph "Algorithm Use"
        CSW2[Current State<br/>of the World] --> PCS2[Perception of<br/>Current State]
        PCS2 --> D2[Data]
        D2 --> ALG2[Algorithm]
        
        CSW2 --> OBJ2[Objective]
        OBJ2 --> PF[Person or Firm]
        
        ALG2 --> REC[Recommendation]
        REC --> PF
        PF --> ACT[Action]
        
        ACT -.->|Feedback| CSW2
    end
    
    style CSW1 fill:#2c3e50,stroke:#ecf0f1,stroke-width:2px,color:#ecf0f1
    style CSW2 fill:#2c3e50,stroke:#ecf0f1,stroke-width:2px,color:#ecf0f1
    style ALG fill:#27ae60,stroke:#ecf0f1,stroke-width:2px,color:#ecf0f1
    style ALG2 fill:#27ae60,stroke:#ecf0f1,stroke-width:2px,color:#ecf0f1
    style ACT fill:#e74c3c,stroke:#ecf0f1,stroke-width:2px,color:#ecf0f1
```

### Key Definitions

#### **Objectives**
- Quantified goals to be optimized
- May be unconscious and imperfectly optimized when used by agents

#### **Model Selection**
- Selection of architecture for ML algorithm class
- Entails assumptions often ignored at deployment
- Examples: OLS regression (linear, structural assumptions) vs Neural Networks (nonlinear, fewer assumptions)

#### **Perception of the World**
- Information available to or inferred by an agent
- No agent has complete understanding
- Different agents have different perceptions

#### **Control Theory for AI Decision Making Systems**

```mermaid
graph LR
    subgraph "Control Theory Concepts"
        F[Feedback Loop] --> DS[System Destabilization Risk]
        CF[Cascading Failure] --> SR[System Robustness]
        CRF[Correlated Failure] --> LR[Limited Robustness]
    end
    
    style F fill:#34495e,stroke:#ecf0f1,color:#ecf0f1
    style CF fill:#34495e,stroke:#ecf0f1,color:#ecf0f1
    style CRF fill:#34495e,stroke:#ecf0f1,color:#ecf0f1
```

**Key Control Theory Insights:**
- **Feedback**: Actions shape future system states - can compound harm
- **Cascading Failure**: Component failure triggers chain reaction
- **Correlated Failure**: Similar structures lead to widespread impact from single failure type

## 2. Challenges and Interventions - Detailed Analysis

### 2.1 Integrating Experts and Algorithms

**Challenge:** Correlation neglect leads to suboptimal human-AI collaboration

```mermaid
flowchart TD
    Start[Radiology Diagnosis Case] --> AI[AI Prediction:<br/>75% accuracy rate]
    AI --> Human[Radiologist Decision]
    Human --> CN{Correlation<br/>Neglect?}
    
    CN -->|Yes| Poor[Decreased Decision Quality]
    CN -->|No| Good[Improved Decision Quality]
    
    Poor --> Sol[Solution: Conditional<br/>AI Recommendations]
    Sol --> Thresh[Only show AI predictions<br/>when certainty threshold met]
    
    style Start fill:#2c3e50,stroke:#ecf0f1,color:#ecf0f1
    style AI fill:#3498db,stroke:#ecf0f1,color:#ecf0f1
    style CN fill:#e74c3c,stroke:#ecf0f1,color:#ecf0f1
    style Sol fill:#27ae60,stroke:#ecf0f1,color:#ecf0f1
```

**Example:** Agarwal et al. Radiology Study
- AI more accurate than 75% of radiologists
- BUT: Providing AI predictions had no average effect on accuracy
- **Root Cause:** Radiologists treat AI info as completely new when it's largely repackaged

### 2.2 Algorithmic Monoculture

**Challenge:** Mass adoption of identical algorithms creates systemic risks

```mermaid
flowchart TD
    MA[Mass Algorithm Adoption] --> Three{Three Major<br/>Consequences}
    
    Three --> CF[Correlated Failure<br/>Single vulnerability affects all]
    Three --> IC[Increased Competition<br/>All firms chase same candidates]
    Three --> SE[Systematic Exclusion<br/>Some individuals have no opportunities]
    
    CF --> Risk[System-wide vulnerability]
    IC --> Inefficiency[Resource waste]
    SE --> Inequality[Social harm]
    
    Risk --> Solution[Solution: Stochastic Algorithms]
    Inefficiency --> Solution
    Inequality --> Solution
    
    Solution --> RL[Reinforcement Learning<br/>with Exploration]
    RL --> Diversity[Diverse Rankings<br/>Reduced Risk]
    
    style MA fill:#e74c3c,stroke:#ecf0f1,color:#ecf0f1
    style Solution fill:#27ae60,stroke:#ecf0f1,color:#ecf0f1
    style RL fill:#3498db,stroke:#ecf0f1,color:#ecf0f1
```

**Example:** Hiring Algorithm Scenario
- 5 firms adopt same algorithm → All compete for same top candidate
- Solution: Add "good noise" through exploration/exploitation balance

### 2.3 Anticompetitive Behavior

**Challenge:** Platform control enables algorithmic manipulation

```mermaid
flowchart TD
    Amazon[Amazon Platform Control] --> Three{Three Anticompetitive<br/>Practices}
    
    Three --> Data[1 Information Asymmetry<br/>Access to all platform data]
    Three --> Search[2 Self-Preferencing<br/>Prioritize own products]
    Three --> Nessie[3 Project Nessie<br/>Price manipulation algorithm]
    
    Data --> Copy[Copy successful<br/>competitor products]
    Search --> Bias[Biased search results]
    Nessie --> Price[Industry-wide<br/>price increases<br/>$1B+ profit]
    
    Copy --> Solution[Khan's Structural<br/>Separatism]
    Bias --> Solution
    Price --> Solution
    
    Solution --> Sep[Separate Platforms<br/>from Commerce]
    Sep --> Fair[Fair Competition]
    
    style Amazon fill:#e74c3c,stroke:#ecf0f1,color:#ecf0f1
    style Solution fill:#27ae60,stroke:#ecf0f1,color:#ecf0f1
    style Sep fill:#3498db,stroke:#ecf0f1,color:#ecf0f1
```

### 2.4 Algorithmic (Mis)alignment

**Challenge:** Proxy objectives create harmful bias

```mermaid
flowchart TD
    Health[Healthcare Risk Assessment] --> Proxy{Current Proxy:<br/>Healthcare Spending}
    
    Proxy --> Bias[Racial Bias Created]
    Bias --> Harm[Black patients excluded<br/>from programs]
    
    Harm --> Root[Root Cause Analysis]
    Root --> SR[Systemic Racism affects<br/>spending patterns]
    
    SR --> Solution[Change Objective Function]
    Solution --> Direct[Predict Health Directly<br/>Not Spending]
    Direct --> Reduced[Significantly Reduced<br/>Racial Bias]
    
    style Health fill:#2c3e50,stroke:#ecf0f1,color:#ecf0f1
    style Bias fill:#e74c3c,stroke:#ecf0f1,color:#ecf0f1
    style Solution fill:#27ae60,stroke:#ecf0f1,color:#ecf0f1
```

### 2.5 Designing More Effective Objective Functions

**Challenge:** Algorithms replicate human judgment errors

```mermaid
flowchart TD
    Problem[Inversion Problem] --> Def[We lack direct data<br/>on mental states]
    
    Def --> Example{Example:<br/>User Satisfaction}
    Example --> Current[Current: Time Engaged<br/>as Proxy]
    Example --> Issue[Issue: Anger engagement ≠<br/>Satisfaction]
    
    Issue --> Solution[Behavioral Science<br/>Integration]
    Solution --> Model[Model Human<br/>Judgment Errors]
    Model --> Better[Better Objective<br/>Functions]
    
    Better --> Collab[ML + Behavioral Science<br/>Collaboration]
    
    style Problem fill:#e74c3c,stroke:#ecf0f1,color:#ecf0f1
    style Solution fill:#27ae60,stroke:#ecf0f1,color:#ecf0f1
    style Collab fill:#3498db,stroke:#ecf0f1,color:#ecf0f1
```

### 2.6 Examining Model Selection

**Challenge:** Limited perception leads to suboptimal outcomes

```mermaid
flowchart TD
    Resume[Resume Screening Task] --> Compare{Compare Two<br/>Approaches}
    
    Compare --> SL[Supervised Learning<br/>Exploitation only]
    Compare --> RL[Reinforcement Learning<br/>Exploration + Exploitation]
    
    SL --> Homogen[Homogeneous<br/>Candidate Pool]
    RL --> Diverse[Diverse Pool<br/>Gender, Race, Income, Academic]
    
    Homogen --> LowAccept[Lower Acceptance Rate<br/>More competition]
    Diverse --> HighAccept[Higher Acceptance Rate<br/>Less competition]
    
    HighAccept --> Success[Better Business<br/>Outcomes]
    
    style Resume fill:#2c3e50,stroke:#ecf0f1,color:#ecf0f1
    style RL fill:#27ae60,stroke:#ecf0f1,color:#ecf0f1
    style Success fill:#3498db,stroke:#ecf0f1,color:#ecf0f1
```

**Example:** Li et al. US Bank Study
- RL algorithm achieved comparable success
- More diverse candidate pool
- Higher offer acceptance rate

### 2.7 Evaluating Models Along Multiple Dimensions

**Challenge:** Single metric evaluation misses improvement opportunities

```mermaid
flowchart TD
    Rashomon[Rashomon Effect:<br/>Multiple good models exist] --> Eval{Evaluation<br/>Approach}
    
    Eval --> Single[Single Metric:<br/>Accuracy only]
    Eval --> Multi[Multiple Metrics:<br/>Accuracy + Fairness]
    
    Single --> Miss[Miss Pareto<br/>Improvements]
    Multi --> Find[Find Better<br/>Alternatives]
    
    Find --> Tool[Coston et al. Tool]
    Tool --> Compare[Compare fairness<br/>across model set]
    Compare --> Replace[Replace unfair with<br/>fair models]
    
    Replace --> Legal[Meets Legal<br/>Requirements]
    Legal --> NoDisp[No disparate impact<br/>without justification]
    
    style Rashomon fill:#3498db,stroke:#ecf0f1,color:#ecf0f1
    style Multi fill:#27ae60,stroke:#ecf0f1,color:#ecf0f1
    style Legal fill:#2c3e50,stroke:#ecf0f1,color:#ecf0f1
```

### 2.8 Surprising Results from Out-of-Sample Evaluations

**Challenge:** Debiasing methods fail in deployment

```mermaid
flowchart TD
    Medical[Medical AI Diagnostics] --> Shortcut{AI Uses<br/>Shortcuts}
    
    Shortcut --> Demo[Infers Demographics<br/>for Diagnosis]
    Demo --> Bias[Creates Harmful<br/>Disparities]
    
    Bias --> Debias{Debiasing<br/>Approaches}
    
    Debias --> InSample[In-Sample:<br/>Appears successful]
    Debias --> OutSample[Out-of-Sample:<br/>Often fails]
    
    OutSample --> Shift[Data Distribution<br/>Shift]
    
    Shift --> Solution[Minimize Demographic<br/>Encoding]
    Solution --> MAPA[Minimum Attribute<br/>Prediction Accuracy]
    MAPA --> Robust[Robust Debiasing]
    
    style Medical fill:#2c3e50,stroke:#ecf0f1,color:#ecf0f1
    style Bias fill:#e74c3c,stroke:#ecf0f1,color:#ecf0f1
    style Solution fill:#27ae60,stroke:#ecf0f1,color:#ecf0f1
```

**Example:** Yang et al. Study
- AI uses hospital location as disease predictor
- Debiasing works in training but fails in deployment
- Solution: Remove demographic information from embeddings

### 2.9 Mitigating Bias from Current State of World

**Challenge:** Systemic inequalities perpetuated through "neutral" algorithms

```mermaid
flowchart TD
    STEM[STEM Job Advertising] --> Auction[Ad Auction System]
    
    Auction --> Competition{Gender Competition<br/>Imbalance}
    Competition --> Women[Women ads:<br/>Higher competition]
    Competition --> Men[Men ads:<br/>Lower competition]
    
    Women --> Expensive[More expensive<br/>to reach women]
    Men --> Cheap[Cheaper to<br/>reach men]
    
    Expensive --> Result[Fewer ads shown<br/>to women]
    
    Result --> Policy{Policy<br/>Response}
    Policy --> Current[Current: Can't bid<br/>differently by gender]
    Policy --> Proposed[Proposed: Allow equality<br/>targeting exceptions]
    
    Proposed --> Equal[Equal ad<br/>distribution]
    
    style STEM fill:#2c3e50,stroke:#ecf0f1,color:#ecf0f1
    style Result fill:#e74c3c,stroke:#ecf0f1,color:#ecf0f1
    style Proposed fill:#27ae60,stroke:#ecf0f1,color:#ecf0f1
```

### 2.10 The Importance of Data Selection

**Challenge:** Data choices determine fairness outcomes

```mermaid
flowchart TD
    Data[Training Data Selection] --> Choice{Include Protected<br/>Attributes?}
    
    Choice --> Exclude[Exclude Race/Gender]
    Choice --> Include[Include Race/Gender]
    
    Exclude --> Blind[Color-blind Algorithm]
    Blind --> Perpetuate[Perpetuates Systemic<br/>Bias]
    
    Include --> Context[Provides Context]
    Context --> Correct[Can Correct for<br/>Systemic Factors]
    
    Correct --> Example[Example: Income differences<br/>affect success indicators]
    Example --> Better[More Fair and<br/>Accurate Predictions]
    
    style Data fill:#2c3e50,stroke:#ecf0f1,color:#ecf0f1
    style Include fill:#27ae60,stroke:#ecf0f1,color:#ecf0f1
    style Better fill:#3498db,stroke:#ecf0f1,color:#ecf0f1
```

### 2.11 Individual Overrides of Algorithmic Recommendations

**Challenge:** Human override decisions often decrease accuracy

```mermaid
flowchart TD
    Bail[Bail Decisions] --> Algo[Algorithm<br/>Recommendation]
    
    Algo --> Judge{Judge<br/>Override?}
    
    Judge --> No[Follow Algorithm]
    Judge --> Yes[Override Decision]
    
    Yes --> Skill{Judge Skill<br/>Level}
    
    Skill --> High[High Skill: 10%<br/>Better outcomes]
    Skill --> Low[Low Skill: 90%<br/>Worse outcomes]
    
    High --> Private[Uses Private<br/>Information Well]
    Low --> Poor[Poor Use of<br/>Context]
    
    Private --> Design[Implication: Design for<br/>selective overrides]
    
    style Bail fill:#2c3e50,stroke:#ecf0f1,color:#ecf0f1
    style High fill:#27ae60,stroke:#ecf0f1,color:#ecf0f1
    style Low fill:#e74c3c,stroke:#ecf0f1,color:#ecf0f1
```

**Example:** Dobbie & Yang Study
- 90% of judge overrides worsen outcomes
- 10% improve outcomes using private information
- High-skill judges use contextual info effectively

## 3. Conclusion

### Key Takeaways

```mermaid
mindmap
  root((AI Interdependency))
    Regulation
      Consider full system
      Not just algorithms
      Include feedback loops
    Research
      Study component interactions
      Identify cascade risks
      Develop interventions
    Practice
      Design for interdependency
      Monitor system outcomes
      Enable selective human input
    Solutions
      Structural separation
      Stochastic algorithms
      Multi-metric evaluation
      Behavioral science integration
```

### Core Message

The paper demonstrates that **effective AI governance requires understanding interdependencies** between:
- Algorithm development and deployment
- Human and algorithmic decision-making
- Market dynamics and individual algorithms
- Current world state and future outcomes

**Critical Insight:** Problems in AI systems often arise not from single components but from their interactions. Solutions must therefore address the full system, not isolated parts.

### Regulatory Implications

1. **Move beyond algorithm audits** to system-level assessments
2. **Consider feedback loops** and long-term equilibrium effects
3. **Address market dynamics** not just individual deployments
4. **Enable context-appropriate human oversight**
5. **Recognize that "neutral" algorithms can perpetuate bias**

---

*This comprehensive model empowers stakeholders to identify and address AI problems through understanding system interdependencies rather than focusing on isolated components.*