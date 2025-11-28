#ai 

# Classical Programming vs Machine Learning

Classical Programming:
- rules rely on human understanding and manual coding
- some problems not possible to identify so doesn't always work
- **programmer** learns rules from observing data
![[Screenshot 2025-10-10 at 14.44.25.png]]

Machine Learning:
- human provides data and anticipated answer
- computer outputs set of rules which then applied to new data
- **machine** learns rules from observing data
![[Screenshot 2025-10-10 at 14.44.59.png]]

### Supervised Learning 

Machine learns mappings input to output
- given input data, machine gives prediction of output

Examples:

| input             | method           | output              |
| ----------------- | ---------------- | ------------------- |
| savings           | credit scoring   | credit score        |
| tumour size       | cancer detection | malignant or benign |
| money transaction | fraud detection  | legitimate or not   |
- teacher knows correct answers (supervises)
- algorithm makes iterative predictions corrected by teacher
- learning stops at certain acceptable performance level

>[!info] Machine Learning
>**Machine Learning** is the process of using a training set to learn features, continue modelling, and finally producing an efficient model.


# Types of Machine Learning

>[!danger] Three Types of Machine Learning
>1. Supervised Learning
>2. Unsupervised Learning
>3. Reinforcement Learning

### Supervised Learning

To learn the mapping (rules) between inputs and outputs
- labelled data provided of past input/output pairs during learning process
- trains model how to behave for unseen data![[Screenshot 2025-10-10 at 14.52.48.png]]

### Unsupervised Learning

To learn hidden pattern (rules) from a set of inputs
- unlabelled data is provided of past input (not input/output pair) during learning process
- instances in same group more similar to each other than those in other groups
![[Screenshot 2025-10-10 at 14.54.47.png]]
### Reinforcement Learning

Occasional positive/negative feedback to reinforce behaviours
- good behaviours rewarded with treat = more common
- bad behaviours punished = less common
- balancing between exploring uncharted data and exploiting current knowledge
![[Screenshot 2025-10-10 at 14.57.55.png]]

>[!info] Machine Learning
>Machine learning is the study of algorithms that improve over task $T$ with respect to performance measure $P$ based on experience $E$.

