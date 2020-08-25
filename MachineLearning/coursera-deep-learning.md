# Week 1

## 1.1 What is a neural network ? 

Housing price prediction:

* bedrooms + size ---> family siz 

* zip code ---> walkability 

* Zip code + wealth ----> school quality

* The stuff after arrows is what the first layer has inferred. 

  ![img](images/coursera-deep-learning/lFR5xLES6dIL8psoHiWjgb3Uqxiwh8oDXpuTSxQxAnM_dvLQ_j7yiH1Fkh3zgq7CbzwfInqwAEiYwit_XJdOa09NTCgHfJz-qgICpukJQTiIU8mRmWeBzlKzeRRde7A_b2OJ-Ltq)

  Combining these inferred feature we can infer price. We do not need to do the above feature engineering. We pass all inputs to all nodes and given sufficient data the nodes will assign weights correctly.

  ![image-20200816145814331](images/coursera-deep-learning/image-20200816145814331.png)

  

## 1.2 Supervised learning with Neural Networks:
Examples:

- House price - std nn 

* Ad clicks - std nn

* Photo tagging - convolutional CNN

* Speech recognition -  temporal component -1d sequence data - RNN

* Language translation - alphabets one at a time - RNN

* Autonomous driving - complexity : image, text, radar - Hybrid archi
  ![img](images/coursera-deep-learning/MMw5klVgOx56vXmJJL-tjK6qFeJpLm8PGhSdhzKr2nlaS2Ct_jtXsCrLa1vASrv04AFTwYoANV98itKkng1U119uHEgvrAbrm8AZxS6XslVhcogoeSiPwU7HdabW5sDHQ2rIhkPu)

  Structured data :  records of data wherein each feature is well defined. Ex size, bedrooms etc

  Unstructured: Audio, Image, Text . Features might be pixel value [humans are good, tougher for machines]

  

###  1.3 Why is DL taking off 

Scale drives deep learning process. 

* Traditional ML algo, performance improves with amt of data and then stabilizes/plateaus.  

* Over the past 10 years, we have generates a lot of data (arrows in the pic ) -> digitization. Traditional algos cant take adv of it.

* Traditional ML -> small NN -> medium NN -> large NN. NN's can take adv of large data sets. 

* Scale = more data + more units 

  ![img](images/coursera-deep-learning/OrkkS64wOxKyCyE4L-Hj9ANDLObSleavSAe4uNdZNI5EcE_cvFTUeQow_XffD0SYoc0H48mejDUKHODI4BZIaT1sW5lBaqxPyOabCbyXqQbVqNJgSethIb51Yg5RAL-qr1j3N7lQ)

* Best best at improving NN : through more data, make model larger.

* For smaller training data : the difference in performance between ML, small, medium, large is nearly the same. Not well defined. Performance will depend on features selected etc. 

* Switching from sigmoid (s shape) to relu (flat and positive). Former has regions where the gradient is nearly zero so learning stops. By using relu for activation , gradient is always greater than 0 so GD is faster. ![img](images/coursera-deep-learning/j44427jWd3-rdLpS3yCVCb63ReugCjyAu1NI5mIwmHS8VjJAs2IhdzYnVEA64m6oZXxQbXGgjW0MmPte0yTrN1CPs5c3unLXwoP-NBuHv1vf87QNOKvyoMkGZptHTavzMFBW94vb)

  

# Week 2 

## 2.1 Logistic Regression as a Neural Network

### 2.1.1 Binary Classification 

Logistic regression = algo for binary classification. 

![image-20200816152405164](images/coursera-deep-learning/image-20200816152405164.png)

* Eg cat(1), not cat(0), Image = three separate matrices for Red, Blue, Green. 
* So 1 picture of 64*64 pixels will have 3 matrices of 64*64. 
* How convert to feature vector ? unroll all to 1d matrix X. Total dimensions will 64 * 64*3 = --- 12288 X 1Matrix X - will have m columns where there are m training samples. And n rows wherein the dimensionality of features. 
* The former makes the implementation easier.
  *  X.shape (n x m ). Training samples are stacked as columns not rows. m = no of training samples
  *  Y.shape = (1,m). [ y1, y2, … ym]. 

### 2.1.2 Logistic Regression 

When to use ? Output label in supervised learning is zero or one. 

* Given X, want y^ = P( y = 1| x) , Parameters w , b 

* Linear regression y = wT * x + b 

  * this can be greater than 1 or negative. doesnt make sense for prob. 

  * so we use sigmoid (s shaped curve). Sigmoid(z) = 1 / (1+ e^-z)

  * If z large then sigmoid = 1 / 1+0 = 1 If z large neg then sigmoid = 1/ 1+ big_num = 0 

  * Not using the notation shown on the right wherein b,w are in the same matrix.

    ![img](images/coursera-deep-learning/rElVU48hcOMpAaVIvug4aTXa-wQGKwQj6ZOmSDo7rmyEW4KLQIF-fEnp0CZbAgals-NNInj0Todj_lp4xp6AhOCCPpkt5uygzfVhtqk6lJy5AVu0XNNp7wVxmHZmPZeZ9fyy9HwH

### 2.1.3 Logistic Regression cost function 

* To train the parameters (w, b) you need a cost function st y^ is nearly same as y. 

* L(y^, y) = ½ ( y^ - y) ^2 -> this is not generally used in log reg because the optimization problem (to find the parameters) is **non-convex** so it has **multiple local optima**. Gradient descent does not work well. 

* ![image-20200816153745071](images/coursera-deep-learning/image-20200816153745071.png)We need a convex optimization problem

  *  If y ==1 

    * L = - logy^ 
    * We want loss to be as small as possible ...  so we want log y ^ to be large .... want y^ large 
    * So we want y^  = 1

  * If y==0 

    * L = - log(1-y^) 
    * want L to be small
    * want log (1-y^) to be large 
    * want y^ to small 
    * sigmoid so that means y^ =0 

    Above loss was for one sample. Cost function is over all samples. 1/m summation (L (y, y^)	![img](images/coursera-deep-learning/RVav3tz6No9ydVQ5QBAspZAS5kTCukH6up0rySfJz4LktkecTvfHE543Hz_RYaZVznM1jCg7zzM7Nyn_vH0STiRTJge12eiRdIhVG1UJvDPv_Zg93XRGDworzHLEAg1Tiq3fXrDm)

    

### 2.1.4 Gradient Descent 

Goal find (w, b) that minimizes the cost function J over all training samples. 

If w is a single row number and b is a single row number then J(w,b) is a surface in 2D space above the two axis and the distance between any point on the surface to w,b is J(w,b) …. We want to find J(w,b) with min distance. **J is a convex function**. U (bowl shaped) . Non convex means many minimas. 

At start, init w,b at an initial point and go in the steepest descent direction![img](images/coursera-deep-learning/1gpOxlpT1xdE242DRoC4Cu7pB9N3Z7okJRbq18I50oyXuRUahfaL2F_7ilL7rdj4s53SRovt2AD527uOO16tP58yTGJ_oTAubdX72ZnQ0_sU-Cro5RYjsZ4Z6GrOMBxRB6kU4eSX)
Algo: (considering only w for simplicity in 2d)![img](images/coursera-deep-learning/hppIMWmw8ibMYjR0l7ZbAqaseGURYWoyrD6XFpQQF_pfdEuiGSQMbSZuxwuBCWW0AJmpbJVBB1AceFYG_yfqHWb_ftDa2bu_MGvxGAyhuD9wOERQ6yZupA7OJ6Do5pR_pl0PE20y) 

* On the left dw is negative so we will land up adding to the weights and moving to the right on the x axis
* On the right dw is positive so we will subtract and go to the left

![image-20200816155949578](images/coursera-deep-learning/image-20200816155949578.png)Derivative is the slope at a point. We want to know the slope given the current w,b values.  Formal def of the update to w,b ![img](images/coursera-deep-learning/L9nOvL9R_65mjc7CCstoao_uCcZ6CedesVMwH0xnAR4B_Ex2eElwbJLXrHJXOvIoISww6dmcn-9v9u2Jar5x7avCOO-jeJ-qhwBMEBxNnfRkY8TYvl4HUIIOG0EHPKYA1vzTnDwW)
“ d” is used when J is function of only w. squigle "d" Partial derivative is used when J is a function of w,b ![img](images/coursera-deep-learning/T8bvzMCL79AeF0m-WxlIk3WdOcT5Gd1DfAYkifRYmG2vSfM2JRB10jcpintpBG3D30YP77_YKzYy1eLmdzwGDzkZGqmDqHxxi2FY9cFBwz0GkBNFySr-paGw9uIUUn73LIPrQ24n)



### 2.1.5 Derivatives 
Intuitive understanding of derivative  

* f(a) = 3a --- stratight line. 
* a =2 f(a) = 6 
* a = 2.0001 f(a) = 6.003
* Look at the little triangle. We moved a 0.001 but f(a) moved 0.003. Slope = height/width (of the triangle) = 0.003/ 0.001 = 3  i.e y increased by 3x the increase of x 
* Same when a=5, 5.001 f(a)= 15.003 
* This is why the d(f(a) = 3. Formal definition: nudge a infinitesimal value to the right![img](images/coursera-deep-learning/C1slpoUfaM5j-qX9Z_y9xlpRhfUGXZADMCsVS-FHn1lIUwJZMLGKY1lIONku0zA-y0de_1zeJdU-e04MSfYzqlUVxYf7rS1v-Tvsh2i6ED4d_eJ-wADVEpCSwNG8xUCPPu0LPVpc)

### 2.1.6 More Derivatives

![image-20200816162118600](images/coursera-deep-learning/image-20200816162118600.png)

* f(a) = a^2 a =2 , f(a) = 4a = 2.001 f(a) = 4.004001 -> Slope = 0.004/0.001 = 4 
* Slope is different for different values a = 5 , f(a) = 25 a = 5.001 f(a) = 25.010 -> Slope = 0.010 / 0.001 = 10 
* derivative is different for different values 
* so d(f(a^2)) = 2*a 

* f(a) = log(a) Slope = 1/a 



### 2.1.7 Computation Graph 

J(a,b,c) =3(a + bc) ![img](images/coursera-deep-learning/ajIMud70S1vH2zbf0Sa7MzoQe8jZTGronqG_0oCjsNczzybQml_vtx0ohPveiiqRQBaziXtoyM_ukdvEyremBKM6VrTS2bCC67OnFOlubs4B-VgnSmiUOAt20fYmizck6Jj84ozd)

The computation graph makes it possible to do left to right computation to calculate J. To update a,b,c we need to perform computations in the reverse direction i.e from right to left. 

### 2.1.8 Derivatives with a computation graph 

* d(j)/ d(v) --- by how much does j increase when v increases

* d(j) / d(a) --- d(j) / d(v) * d(v) / d(a) --- chain rule 

  ![image-20200816165349838](images/coursera-deep-learning/image-20200816165349838.png)

![img](images/coursera-deep-learning/WQ1QHnRV26pSFfkiiKhmRhmnx1sd5J3PZhZ1D5rcQpmxv8EvU0swUWBR1v6hkxhN_tk-bVTzq2lgSAlvnzGEqios5hM1qHHH4t_VtIK9farODCwL2ZUc9pzT46rlPtSpMIWpHGjd)



"dvar' = d(final output var)/d var  --- in code this represents the derivative of the final output value wrt variable

![image-20200816165543460](images/coursera-deep-learning/image-20200816165543460.png)



* Right to left derivative calculation 
  * d(j) / d(u) = d(j)/d(v) * d(v)/d(u)
  * d(j) / d(b) = d(j) / d(u) * d(u)/d(b) = d(j)/d(v) * d(v)/d(u) *  d(u)/d(b)

### 2.1.9 Logistic regression gradient descent 

recap of logistic regression 

![image-20200816170235706](images/coursera-deep-learning/image-20200816170235706.png)

backward derivative calculation with computation graph

![img](images/coursera-deep-learning/0Qs1hOwHOfQfOMIvTkDFIxGFNCek4zpPtYASFHsSBYZtPmRPA572QfhyIOEmSA7-jPewRtyPnFSOzGK3jWY9Pq4aSDvjX0MJ1Sx3Ufj9vmgF2XIJgZqCwQWWqzCSmAWtvf2bZU8z)

### 2.1.10 Gradient descent on m examples 

Get derivative wrt to one training sample and average that for all
![img](images/coursera-deep-learning/ZhCa2TJTBF1hbGNarN5qpwvrNFEf2Y4tUg9Hr7mkGbPC4La-_89XGOu8crQwVOtCxKV-ZftC5vILBfTH8NfDbgp9JlziZUXkq-IEwW6SMNmY-oDFSJ0cy16lZND9IYsqS-Ug2ajg) ![img](images/coursera-deep-learning/jQSRsuIvKWBig2exs1jEs7qc5IyAlFqEmlwjj1yHG9BOK6QVaBAxL-WEUy5k-3MWUgpF06RnsTd4ve4xscrCmzdDYhWC1Vy-piRezufSaB15miIzO2ngyrXUuZwWGQEd3eAlfy56) One full steps of GD. 

* There are 2 for loops. 
* One for each training sample and one for each feature. 
* The dw1, dw2, db on the right is the cumulative update across all samples
* For loops slow down computation. 
* In DL world we use “vectorization” 
* Vectorization get rid of explicit for loops in code. ![img](images/coursera-deep-learning/iiqllmCwM0YzAzU899tt9-ND_tWny-21l2CMoLmIvpOcB6az8w8zuyuIfK4pMQN97irHCKjAaybp8Ug1gDhpYYAZVjCSSs5uOBJ3dUHoXCKI7KFtUgELlDLL5JyTTFVoqn9GTH_N)
* Vectorized version 1.5 ms. Non vector : 480 ms !!! that’s a lot 300x
* Both CPU and GPU support parallelization of operations using SIMD. *single instruction multiple data*. This is true when using inbuilt functions.

## 2.2 Vectorization  

### 2.2.1 Intro 

SIMD - single instruction multiple data. Applicable for CPU, GPU

### 2.2.2 More Vectorization Examples![img](images/coursera-deep-learning/uxkfsQNt8nkr6Vzn0vhsOKF7OnVoUnAc7llpaaOFqn2pbvwA2ZxhExgckeR7sl5qk2WqQFaZTu1KZnz_5Pr_TzWAxW4bXzRiaLX4E6ECyrGVMCkMOAVedv2DNIn8TWmFaEAZC9Du)![img](images/coursera-deep-learning/w0Xw7Qdce_kZ5Lv6qI4u2YLeo2B3l_IeLZ7DauEz6acztAZIi_QksZ_sOuJWyoGKUwXeV57ocgBRfH03B_YiAhdus5uG5RIMPIluT6O1XeRlcnrpNLgd9T12Wh4E1aVpxgYTzR10)
In the logistic regression algo instead of having a for loop to calculate the w1, w2 … we can use a numpy vector 

* get rid of dw1, dw2 ... dw = np.zeroes(nx-1)
* remove the individual weight updates ... dw += x.dz
* remove the averaging at the end of the loop ... dw = dw/m 

![img](images/coursera-deep-learning/vh2xc7L1TNDAN6Qz1gcx3bJKWvStjXRaw3n5OaRHcBR69RZyoX1dyhRonykm7C4COvXQEQstwGpd8pKOxGapi-p7Kbo1wdD7XIVc9dDp6ZKIwsktA7bsrAIB8n428IGPK8wtU5kU)



Now we are left with the outer for loop 



### 2.2.3 Vectorizing logistic regression 

* Remove the for loop iterating over training samples in previous example

* Replacing x1, x2 … with X . 

* Replace z1, z2 … with Z. 

* Then use np.dot(w_tr, X)+b

* b will be broadcasted to match the correct row/col size
  ![img](images/coursera-deep-learning/wtfQ1Pw3YER9Z-97NegT2tRsa2-9cnHjZOfYrInpD7BkCTXyZ9dl9BM1_5d0nVCi6mTYkNXHv9Lj7O9JUaThTnTjrQne24dw9WrGngVx_wpt3HB_nadz0CuoxBT8Ch5XV4BRQ6ZB)

  ### 2.2.4 Vectorizing logistic regression gradient output 

  Calculating the derivative with vectorization ![img](images/coursera-deep-learning/VQovuFilvX0Up5jt07UxlErdMy7N223b9G70b2oH_Gi9Y0XoRq1fuNYExJKAO-3qnNd1B9tfSyzmf9u94UVNqbJsVVNBShhgSsqo10yqfjE-hQ8NGpGVosTvOVxtaTfL7SKe45Y3)![img](images/coursera-deep-learning/ceGUHVPvhjGYNGLFdrCCXJGv_z_eeoLXSxOdUDRZilWf5gDXQv_FFSVuWD3gK8_6KoyQzp4qw4Z32P4aaaw7s75JCdnMxeFb80lluxG5bsCLmcgTJDPAyWzz3vOWIPlQihS23YQB)
  All together with vectorization for single iteration: (multiple iterations would require for loop)![img](images/coursera-deep-learning/KKwq2mZcWtaIqNYVLsnhLH0i0NB_1qd1qWKl2GzmBYtY0sbKw7HdqpUtikUoZQ462ge5OJyMLqY7ZzaKvs8gbTyKYUkXbnlDRt5AFQHNDhSp0zZttoDqVWUhX5BBi_S18x4VtwJE) 

  ### 2.2.4  Broadcasting in python

  ![image-20200825083323049](images/coursera-deep-learning/image-20200825083323049.png)

  no for loops. just two commands.

  

  Another example. automatically create a 4*1 matrix to add 100 to the original matrix 

  ![image-20200825083451887](images/coursera-deep-learning/image-20200825083451887.png)

  

  Another example. 

  ![image-20200825083544793](images/coursera-deep-learning/image-20200825083544793.png)

  

  General principle : 

  *  (m,n) matrix (+ - * /) (1,n) ---- make it a (m,n) matrix and apply it to the original matrix. [https://docs.scipy.or g/doc/numpy/user/basics.broadcasting.html](https://docs.scipy.org/doc/numpy/user/basics.broadcasting.html) 
  * ![image-20200825083659342](images/coursera-deep-learning/image-20200825083659342.png)

  

### 2.2.5 python/numpy vectors 

a = np.random.randn(5)

a.shape 

(5,) ---> rank 1 array. do NOT use 

a.T ----> same as a! confusing. 

VS

a = np.random.randn(5,1)

a.shape

(5,1) ---->column vector 



# Week 3 : Shallow neural networks



## 3.2 Neural network representation 

* hidden === we dont see what the values should be in the training set. 

* The below network is called a "2 layer NN". hidden + output = 2

![image-20200825085602430](images/coursera-deep-learning/image-20200825085602430.png)

## 3.2 Computing a neural networks output 

zoom into one node. 

![image-20200825085809682](images/coursera-deep-learning/image-20200825085809682.png)

notation : <img src="images/coursera-deep-learning/image-20200825085913731.png" alt="image-20200825085913731" style="zoom: 50%;" />

stack the W's, X's and b's to create Z1 

![image-20200825090129171](images/coursera-deep-learning/image-20200825090129171.png)

so summarizing ... 

<img src="images/coursera-deep-learning/image-20200825090232395.png" alt="image-20200825090232395" style="zoom: 33%;" />

## 3.3 Vectorizing across multiple examples 

We need to do the Z,A computation for each layer for each training example. Here is a for loop for computing it (bad!)

<img src="images/coursera-deep-learning/image-20200825090635886.png" alt="image-20200825090635886" style="zoom:33%;" />

<img src="images/coursera-deep-learning/image-20200825090654358.png" alt="image-20200825090654358" style="zoom:50%;" />

stack up x(i) to create X. <img src="images/coursera-deep-learning/image-20200825090837304.png" alt="image-20200825090837304" style="zoom:33%;" />

then re-write Z, A to use X <img src="images/coursera-deep-learning/image-20200825090911167.png" alt="image-20200825090911167" style="zoom:33%;" />

<img src="images/coursera-deep-learning/image-20200825091018680.png" alt="image-20200825091018680" style="zoom:33%;" />

## 3.3.5 Activation functions 



Sigmoid  <img src="images/coursera-deep-learning/image-20200825091536562.png" alt="image-20200825091536562" style="zoom:33%;" />

Better activation = tanh <img src="images/coursera-deep-learning/image-20200825091612147.png" alt="image-20200825091612147" style="zoom:33%;" />

center the data so the mean of the data is 0. almost never use sigmoid for inner layers. it makes sense for the output layer. 



ReLu. rectified linear unit. <img src="images/coursera-deep-learning/image-20200825091816970.png" alt="image-20200825091816970" style="zoom:33%;" />

Leaky ReLu <img src="images/coursera-deep-learning/image-20200825092035097.png" alt="image-20200825092035097" style="zoom:33%;" />

Rules: 

* if output layer needs to be 0/1 use sigmoid 
* for inner layers just use relu. 

### 3.3.6 Why do you need non-linear activation function 

what happens if we remove sigmoid/activation function ... a breaks down to a linear combination of W,x,b 

### 3.3.7 Derivatives of activation functions 

derivative of sigmoid <img src="images/coursera-deep-learning/image-20200825092745099.png" alt="image-20200825092745099" style="zoom:33%;" />

derivative of tanh <img src="images/coursera-deep-learning/image-20200825092825810.png" alt="image-20200825092825810" style="zoom:33%;" />

derivative of relu <img src="images/coursera-deep-learning/image-20200825092904654.png" alt="image-20200825092904654" style="zoom:33%;" />

### 3.3.8 Gradient descent for neural networks 

formula heavy slide 

![image-20200825094204314](images/coursera-deep-learning/image-20200825094204314.png)

skipping the intuition video .. 

### 3.3.9 Random initialization 

* initializing bias to zero is okay but NOT okay for w. 
* w =0 , a1 = a2. dz1 = dz2. nodes are completely symmetric. 
* basically, all hidden units will compute the same function. no matter how long you nothing will change. 

<img src="images/coursera-deep-learning/image-20200825094512975.png" alt="image-20200825094512975" style="zoom:50%;" />

Correct way to do it : <img src="images/coursera-deep-learning/image-20200825094636701.png" alt="image-20200825094636701" style="zoom:33%;" />

* multiply by 0.001 -> makes w very small -> makes z small -> slope of gradient large. 
* if w large -> z large -> slope will be small -> learning will slow down. <img src="images/coursera-deep-learning/image-20200825094750887.png" alt="image-20200825094750887" style="zoom:25%;" />