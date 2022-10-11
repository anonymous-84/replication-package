# Replication Package Comparison Defects and Code Smells

## Usage

To use the replication package, we recommend applying the dependencies included on the [requirements](requirements.txt) file. We strongly recommend using Python 3 Virtual Environment as follows.

```bash
python3 -m venv .venv
source .venv/bin/activate
pip3 install -r requirements.txt
```

From there, you can run the notebooks in the [notebooks](notebooks/) folder.

## Summary

This replication package allows the research community to replicate the results of a study comparing the defect model with several class-level code smells models.

### Code Smells Definitions

| Code Smell                   | Definition                                                                                  | Reference |
|------------------------------|---------------------------------------------------------------------------------------------|-----------|
| God Class                    | A large class that have too many responsibilities and centralizes the module functionality. | [3]       |
| Refused Bequest              | A class that does not want to use its parent behavior.                                      | [2]       |
| Spaghetti Code               | A class that has methods with large and unique multistage process flow.                     | [1]       |
| Class Data Should be Private | A class with too many public fields.                                                        | [4]       |
| Data Class                   | Classes that have only fields, getters and setters.                                         | [2]       |
| Lazy Class                   | Classes that have little behavior, with few methods and fields.                             | [2]       |
| Speculative Generality       | Classes that support future behavior, usually interacting with test classes only.           | [2]       |



### Open-Source Java Projects

- Ant 1.7
- Broadleaf 3.0
- Camel 1.6
- Elasticsearch 0.9
- Hazelcast 3.3
- JDT 3.4
- Jedit 4.3
- Lucene 4.3
- Neo4J 1.9
- OrientDB 1.6
- PDE 3.4
- POI 3.0
- Titan 0.5
- Xalan 2.7

## Folders

### Correlations

There is a folder called [correlations](correlations/) with the respective correlation analysis divided by each quality attribute. The blue value indicates low correlation, while red represents high correlation.
### Data

All data is available under the [data](data/) folder. Below, we present folder's working tree.

| Folder                        | Content                                            |
|-------------------------------|----------------------------------------------------|
| [**final**](data/final)       | Contains the final dataset with defects and smells |
| [**projects**](data/projects) | Contains the projects used in the study            |
| [**raw**](data/raw)           | Contains the raw dataset with defects              |
| [**unseen**](data/unseen)     | Contains the unseen dataset to test the models     |

Each project folder has all `csv` files with the information about the code smells. The files follow this naming pattern: `organic<code_smell>.csv`

> **Note**
> if you want to run the Organic tool, for instance, for the project `ant`, you need to execute the following command:

```bash
java -jar organic-OPT.jar -sf ../projects/ant/organic/ant.json -src "../bad-smells-defects/projects/ant"
```

You can execute the `organic-OPT.jar` included inside the [scripts](scripts/) folder.

#### Explanations

Inside the [explanations](explanations/) folder, we have all SHAP explanations for each target.

### Features

The complete list of features is available in the [features](folder here) folder. There two files in this folder:

- [features.md](features/features.md): contains the list of features used in the study with the considered correlation.
- [OpenStaticAnalyzer-1.0-Metrics.html](features/OpenStaticAnalyzer-1.0-Metrics.html): contains the list of features with a brief description.

### Models

The models created in the study are available in the [models](models/) folder. Each target has its own `pickle` file. Note that some files are too large for GitHub storage, and you have to unzip the `zip` files to use the models (defect, gc, lc, and sc).

### Notebooks

The notebooks are organized as follows:

- [01-setup.ipynb](notebooks/01-setup.ipynb): prepares, trains and executes the data for the study.
- [02-predict.ipynb](notebooks/02-predict.ipynb): loads the models and predicts with unseen data.

### Results

The results are available in the [results](results/) folder. There, we have the performance of each model and the results of the statistical tests.

### Scripts

Inside the [scripts](scripts/) folder, we stored the [Organic](https://github.com/opus-research/organic) jar.

### Validation

Inside the [validation](validation/) folder, we have the results of the validation of the Organic tool with developers.

##### References

- [1] Brown, W.H., Malveau, R.C., McCormick, H.W.S., Mowbray, T.J.: AntiPatterns: refactoring software, architectures, and projects in crisis. John Wiley & Sons, Inc. (1998)
- [2] Fowler, M.: Refactoring: Improving the Design of Existing Code. Addison-Wesley (1999)
- [3] Riel, A.: Object Oriented Design Heuristics. Addison-Wesley Professional (1996)
- [4] Santana, A., Cruz, D., Figueiredo, E.: An exploratory study on the identification and evaluation of bad smell agglomerations. In: Proceedings of the 36th Annual ACM Symposium on Applied Computing (2021)

