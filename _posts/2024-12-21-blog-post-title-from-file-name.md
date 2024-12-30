## ML Notes for Quantitative Finance Interviews

### Linear Models

For details, you may refer to ESL Chapter3 or PRML.

#### Classification with Linear Models

Logistic regression is one of the generalized linear models to perform classification tasks. For ease of discussion, we will focus on the binary response case. We call logistic regression linear models that it assumes the log-odds of an observation $y$ can be expressed as a linear function of the $K$ input variables $\mathbf{x}:=(x_1, x_2, ..., x_K)$:

$$
\log{\frac{p(x)}{1-p(x)}} = \sum_{j=0}^K b_j x_j \tag{1}
$$

Here $p(x)$ represents the probability of $y=1$ and we call $\frac{p(x)}{1-p(x)}$ the "odds" of the response being true, here the function which links the *log(odds)* to probability function p(x) is called "link function" in GLM, in the case of logistic regression, link function is the ****logit**** function. We assumes the coefficients of features are "mutliplicative in odds", which means they contribute independently to the *log(odds)*.

From (1), we have

$$
p(z) = \frac{exp(z)}{1-exp(z)},
$$

$$
z=\sum_{j=0}^K b_j x_j.
$$

Therefore we have

$$
p'(z) = p(z)(1-p(z)).
$$

Logistic regression does not has an analytical solution, to solve the problem, we need to find out the set of parameter $b_0, b_1,...,b_K$ which maximizes the log-likelihood of the observations, which is expressed as the product of the predicted probabilities of the N individual observations:

$$
\mathcal{L}(\beta|\mathbf{X}, \mathbf{Y})=\sum_{i=0}^N \log{P(X_i)}
$$

From what discussed above, we have reached the most important conclusion about logistic regression that it is coordinate-free.

---

### This is a header

#### Some T-SQL Code

```tsql
SELECT This, [Is], A, Code, Block -- Using SSMS style syntax highlighting
    , REVERSE('abc')
FROM dbo.SomeTable s
    CROSS JOIN dbo.OtherTable o;
```

#### Some PowerShell Code

```powershell
Write-Host "This is a powershell Code block";

# There are many other languages you can use, but the style has to be loaded first

ForEach ($thing in $things) {
    Write-Output "It highlights it using the GitHub style"
}
```

#### Reference

+ https://win-vector.com/2011/09/14/the-simpler-derivation-of-logistic-regression/
