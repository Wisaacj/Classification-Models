# Experimenting with a Single-Layered Perceptron, Logistic Regression, and Naive Bayes on the training dataset

Perceptron:
- Accuracy: 0.9137243515292297
- Precision: 0.9172770149049306
- Recall: 0.9137091162143354
- f1 0.9105836764783534

Logistic Regression (Note that max_iter had to be increased to 10000):
- Accuracy: 0.9652076074332172
- Precision: 0.9651532812510705
- Recall: 0.965205288796103
- f1: 0.9650950193365827

Naive Bayes:
- Accuracy: 0.8273954703832752
- Precision: 0.871126229005243
- Recall: 0.8274182324286709
- f1: 0.8294072137190873

---

## Exploring Data Scaling

### Standard Scaler

Perceptron:
- Accuracy: 0.9255420054200542
- Precision: 0.9262478773976279
- Recall: 0.9255393180236604
- f1 0.9248536758304478

Logistic Regression:
- Accuracy: 0.9707655826558266
- Precision: 0.9708119661268255
- Recall: 0.9707724425887265
- f1: 0.9707333414497087

Naive Bayes:
- Accuracy: 0.7752080913666279
- Precision: 0.8454705956684332
- Recall: 0.7752261656228253
- f1: 0.7729268940948638

### Min-Max Scaler

Perceptron:
- Accuracy: 0.9157931668602401
- Precision: 0.9187769809824365
- Recall: 0.9157967988865693
- f1: 0.9142578100529275

Logistic Regression:
- Accuracy: 0.9624201509872241
- Precision: 0.9627621969870734
- Recall: 0.9624217118997912
- f1: 0.9624533105223941

Naive Bayes:
- Accuracy: 0.8079002129307007
- Precision: 0.8607267600823755
- Recall: 0.8079331941544885
- f1: 0.8090112293247175

---

## Exploring Kernel Trick Data Transformations

Note each data transformation and evaluation is on the training dataset.

### Radial Basis Function - n_components=100

Perceptron:
- Accuracy: 0.09045925280681377
- Precision: 0.08783835735210568
- Recall: 0.09046624913013222
- f1: 0.07621883619563921

Logistic Regression:
- Accuracy: 0.10228174603174603
- Precision: 0.10076963460103518
- Recall: 0.1022964509394572
- f1: 0.10130897591468428

Naive Bayes:
- Accuracy: 0.09880468447541618
- Precision: 0.09799803952051815
- Recall: 0.09881697981906751
- f1: 0.0983185443552926

### Radial Basis Function = n_components=200

Perceptron:
- Accuracy: 0.11343641114982579
- Precision: 0.09996459109668651
- Recall: 0.11343075852470424
- f1: 0.09827560131532995

Logistic Regression:
- Accuracy: 0.10439653503677895
- Precision: 0.10272539896901828
- Recall: 0.10438413361169102
- f1: 0.10323979673834853

Naive Bayes:
- Accuracy: 0.10857288037166087
- Precision: 0.11004682739435077
- Recall: 0.10855949895615867
- f1: 0.10890950313549391

### Nystroem

Perceptron:
- Accuracy: 0.1453953735965931
- Precision: 0.09508524063011023
- Recall: 0.1454418928322895
- f1: 0.09681467071602395

Logistic Regression:
- Accuracy: 0.10090495547812621
- Precision: 0.020487935007073008
- Recall: 0.10090466249130133
- f1: 0.0317797531616644

Naive Bayes:
- Accuracy: 0.10020567169957414
- Precision: 0.020169234342959107
- Recall: 0.10020876826722339
- f1: 0.033360066490774096

# Evaluating the best models on the test dataset

_Note no kernel-trick data transformed models will be evaluated as their performance on the training dataset proved to be worse
than that of a random classifer_

Perceptron:
- Accuracy: 0.9472222222222222
- Precision: 0.9506739556477815
- Recall: 0.9472222222222222
- f1: 0.9472461128819086

Logistic Regression:
- Accuracy: 0.9611111111111111
- Precision: 0.9612873277824259
- Recall: 0.9611111111111111
- f1: 0.960983585160728

Naive Bayes:
- Accuracy: 0.8111111111111111
- Precision: 0.8479871939298477
- Recall: 0.8111111111111111
- f1: 0.8150828576150382

## Models with StandardScaler

Perceptron:
- Accuracy: 0.9111111111111111
- Precision: 0.9159277343550444
- Recall: 0.9111111111111111
- f1: 0.910154859794178

Logistic Regression:
- Accuracy: 0.9722222222222222
- Precision: 0.972658266035459
- Recall: 0.9722222222222222
- f1: 0.9722571303698064

Naive Bayes:
- Accuracy: 0.7416666666666667
- Precision: 0.8115651949207483
- Recall: 0.7416666666666667
- f1: 0.7418508070783839

# Conclusion

From the experiments and evaluations of the models, we can see that data transformations using kernel-trick had an overwhelmingly negative effect on the performance of the models. This is almost certainly because the kernel-trick will distort the image and create a completely different one as a result.

Furthermore, we can see that the pure models (ones without any scaling or kernel-trick data transformations) performed very well, with similar results when evaluated on the training and test datasets.

The best model was Logistic Regression (note the number of iterations had to be increased to 10000 for its training) with a StandardScaler scaling applied to the dataset. This model scored a consistent 97% across all the model performance metrics. I was worried that because Logistic Regression requried so many iterations for its training, it would overfit the training dataset; however, it is clear my worries were misplaced.