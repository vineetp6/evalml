<p align="center">
<img width=50% src="https://github.com/featurelabs/evalml/blob/master/docs/source/images/evalml_logo.png?raw=true" alt="Featuretools" />
</p>

[![CircleCI](https://circleci.com/gh/FeatureLabs/evalml.svg?style=svg&circle-token=9e0ce5e5f2db05f96fe92238fcde6d13963188b6)](https://circleci.com/gh/FeatureLabs/evalml)

EvalML is an AutoML library to build optimized machine learning pipelines for domain-specific objective functions.

**Key Functionality**

* **Domain-specific** - Includes repository of domain-specific objective functions and interface to define your own
* **End-to-end** - Constructs and optimizes pipelines that include imputation, feature selection, and a variety of modeling techniques
* **Guardrails** - Carefully cross-validates to prevent overfitting and warns you if training and testing results diverge

## Install
```shell
pip install evalml --index-url https://install.featurelabs.com/<KEY>
```

## Quick Start

```
from evalml import AutoClassifer
from evalml.objectives import FraudDetection


fraud_objective = FraudDetection(
    retry_percentage=.5,
    interchange_fee=.02,
    fraud_payout_percentage=.75,
    amount_col=10
)

clf = AutoClassifier(objective=fraud_objective,
                     max_pipelines=3)

clf.fit(X_train, y_train)

# get best pipeline
clf.best_pipeline)

# predict on new data using best pipeline
clf.best_pipeline.score(X_test, y_test)

# see all pipeline ranks
clf.rankings
```

## Built at Feature Labs
<a href="https://www.featurelabs.com/">
    <img src="http://www.featurelabs.com/wp-content/uploads/2017/12/logo.png" alt="Featuretools" />
</a>
