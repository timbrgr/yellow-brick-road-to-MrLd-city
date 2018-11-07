# Rules of Machine Learning: Best Practices for ML Engineering

All input provided from Google's "Best practices for ML Engineering". <br>
Souce: Martin, Zinkevich, https://developers.google.com/machine-learning/guides/rules-of-ml/

**Rule #1: Don’t be afraid to launch a product without machine learning.**
- ML requires a lot of data. If not available, **try heuristics**. They can already get you far.
--> **"If machine learning is not absolutely required for your product, don't use it until you have data."**

**Rule #2: First, design and implement metrics.**
- try to track as much as possible --> track changes, notice problems (+ track it)
- design with metric instrumentation in mind

**Rule #3: Choose machine learning over a _complex_ heuristic.**
- complex heuristics are unmaintainable
- when you have the data & understanding of what to do, move the ML (they are easier to update & maintain)

## ML Phase 1: First Pipeline

**Rule #4: Keep the first model simple and get the infrastructure right.**
- first model provides biggest boost to product, no need to be fancy
- determine
  - how to get examples to your learning algorithm
  - first idea what "good" and "bad" mean for system
  - how to integrate model into aplication (live, precompute)
- choose _simple features_ to ensure that
  - features reach algo correctly
  - model learns reasonable weights
  - features reach model in server correctly
--> Now: simple model provides baseline metrics and pipeline for more compled models (some teams aim for "neutral" first launch -> deprioritize ML gains as to not get distracted)

**Rule #5: Test the infrastructure indepently from the ML.**
- make infrastructure **testable** --> decouple learning part from system to
  - test getting data into the algo
  - test getting models out of the training algo (make sure getting same results as models in serving environment)
  
**Rule #6: Be careful about dropped data when copying pipelines.**
- careful when copying data pipelines, as old pipeline might drop data we need for the new one

**Rule #7: Turn heuristics into features, or handle them externally.**
- **heuristics can give you a lift when tweaked with ML** -> those rules often contain a lot of intuition about the system you don't want to throw away
- use existing heuristics by
  - preprocessing using the heuristic: pre-filter etc. don't try to relearn certain things that can be easily described by heuristic
  - creating a feature: e.g. compute relevance score
  - mine raw inputs of heuristic
  - modifying the label: heuristic might capture information not contained in label
- **be mindful about the added complexity** when using heuristic in ML system

**Monitoring**
- practice good alerting hygiene, such as making alerts actionable and having a dashboard page.

## ML Phase 2: Feature Engineering

## ML Phase 3: Slowed Growth, Optimization Refinement, and Complex Models

