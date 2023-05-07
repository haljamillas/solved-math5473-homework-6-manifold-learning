Download Link: https://assignmentchef.com/product/solved-math5473-homework-6-manifold-learning
<br>
<ol>

 <li><em>Order the faces: </em>The following dataset contains 33 faces of the same person (<em>Y </em>∈ R<sup>112×92×33</sup>) in different angles, <a href="https://yao-lab.github.io/data/face.mat">https://yao-lab.github.io/data/face.mat</a></li>

</ol>

You may create a data matrix <em>X </em>∈ R<em><sup>n</sup></em><sup>×<em>p </em></sup>where <em>n </em>= 33<em>,p </em>= 112 × 92 = 10304 (e.g.

X=reshape(Y,[10304,33])’; in matlab).

<ul>

 <li>Explore the MDS-embedding of the 33 faces on top two eigenvectors: order the facesaccording to the top 1st eigenvector and visualize your results with figures.</li>

 <li>Explore the ISOMAP-embedding of the 33 faces on the <em>k </em>= 5 nearest neighbor graph and compare it against the MDS results. Note: you may try Tenenbaum’s Matlab code <a href="https://yao-lab.github.io/data/isomapII.m">https://yao-lab.github.io/data/isomapII.m</a></li>

 <li>Explore the LLE-embedding of the 33 faces on the <em>k </em>= 5 nearest neighbor graph and compare it against ISOMAP. Note: you may try the following Matlab code <a href="https://yao-lab.github.io/data/lle.m">https://yao-lab.github.io/data/lle.m</a></li>

</ul>

<ol start="2">

 <li><em>Manifold Learning</em>: The following codes by Todd Wittman contain major manifold learning algorithms talked on class.</li>

</ol>

<a href="http://math.stanford.edu/~yuany/course/data/mani.m">http://math.stanford.edu/</a><a href="http://math.stanford.edu/~yuany/course/data/mani.m">~</a><a href="http://math.stanford.edu/~yuany/course/data/mani.m">yuany/course/data/mani.m</a>

Precisely, eight algorithms are implemented in the codes: MDS, PCA, ISOMAP, LLE, Hessian Eigenmap, Laplacian Eigenmap, Diffusion Map, and LTSA. The following nine examples are given to compare these methods,

<ul>

 <li>Swiss roll;</li>

 <li>Swiss hole;</li>

 <li>Corner Planes;</li>

 <li>Punctured Sphere;</li>

 <li>Twin Peaks;</li>

 <li>3D Clusters;</li>

 <li>Toroidal Helix;</li>

 <li>Gaussian;</li>

 <li>Occluded Disks.</li>

</ul>

1

<em>Homework 6. Manifold Learning                                                                                                                                              </em>2

Run the codes for each of the nine examples, and analyze the phenomena you observed.

*Moreover if possible, play with t-SNE using scikit-learn manifold package:

<a href="http://scikit-learn.org/stable/modules/generated/sklearn.manifold.TSNE.html">http://scikit-learn.org/stable/modules/generated/sklearn.manifold.TSNE.html </a>or any other implementations collected at

<a href="https://lvdmaaten.github.io/tsne/">http://lvdmaaten.github.io/tsne/</a>

<ol start="3">

 <li><em>Nystr¨om method: </em>In class, we have shown that every manifold learning algorithm can be regarded as Kernel PCA on graphs: (1) given <em>N </em>data points, define a neighborhood graph with <em>N </em>nodes for data points; (2) construct a positive semidefinite kernel <em>K</em>; (3) pursue spectral decomposition of <em>K </em>to find the embedding (using top or bottom eigenvectors).</li>

</ol>

However, this approach might suffer from the expensive computational cost in spectral decomposition of <em>K </em>if <em>N </em>is large and <em>K </em>is non-sparse, e.g. ISOMAP and MDS.

To overcome this hurdle, Nystr¨om method leads us to a scalable approach to compute eigenvectors of low rank matrices. Suppose that an <em>N</em>-by-<em>N </em>positive semidefinite matrix

0 admits the following block partition

<em> .                                                                          </em>(1)

where <em>A </em>is an <em>n</em>-by-<em>n </em>block. Assume that <em>A </em>has the spectral decomposition <em>A </em>= <em>U</em>Λ<em>U<sup>T</sup></em>,

Λ = diag(<em>λ<sub>i</sub></em>) (<em>λ</em><sub>1 </sub>≥ <em>λ</em><sub>2 </sub>≥ <em>…λ<sub>k </sub>&gt; λ<sub>k</sub></em><sub>+1 </sub>= <em>… </em>= 0) and <em>U </em>= [<em>u</em><sub>1</sub><em>,…,u<sub>n</sub></em>] satisfies <em>U<sup>T</sup>U </em>= <em>I</em>.

<ul>

 <li>Assume that <em>K </em>= <em>XX<sup>T </sup></em>for some <em>X </em>= [<em>X</em><sub>1</sub>;<em>X</em><sub>2</sub>] ∈ R<em><sup>N</sup></em><sup>×<em>k </em></sup>with the block <em>X</em><sub>1 </sub>∈ R<em><sup>n</sup></em><sup>×<em>k</em></sup>.</li>

</ul>

Show that <em>X</em><sub>1 </sub>and <em>X</em><sub>2 </sub>can be decided by:

1<em>/</em>2

<em>X</em><sub>1 </sub>= <em>U<sub>k</sub></em>Λ<em><sub>k </sub>,                                                                            </em>(2)

<em>X</em>2 = <em>B</em><em>TU</em><em>k</em>Λ−<em>k </em>1<em>/</em>2<em>,                                                                      </em>(3)

where <em>U<sub>k </sub></em>= [<em>u</em><sub>1</sub><em>,…,u<sub>k</sub></em>] consists of those <em>k </em>columns of <em>U </em>corresponding to top <em>k </em>eigenvalues <em>λ<sub>i </sub></em>(<em>i </em>= 1<em>,…,k</em>).

<ul>

 <li>Show that for general 0, one can construct an approximation from (2) and (3),</li>

</ul>

<em> .                                                                     </em>(4)

where , and  denoting the Moore-

Penrose (pseudo-) inverse of <em>A</em>. Therefore k<em>K</em><sup>ˆ </sup>− <em>K</em>k<em><sub>F </sub></em>= k<em>C </em>− <em>B<sup>T</sup>A</em><sup>†</sup><em>B</em>k<em><sub>F</sub></em>. Here the matrix <em>C </em>− <em>B<sup>T</sup>A</em><sup>†</sup><em>B </em>=: <em>K/A </em>is called the (generalized) <em>Schur Complement </em>of <em>A </em>in <em>K</em>.

<ul>

 <li>Explore Nystr¨om method on the Swiss-Roll dataset (<a href="https://yao-lab.github.io/data/swiss_roll_data.mat">http://yao-lab.github.io/data/ </a><a href="https://yao-lab.github.io/data/swiss_roll_data.mat">mat</a> contains 3D-data X; <a href="https://yao-lab.github.io/data/swissroll.m">http://yao-lab.github.io/data/swissro</a>ll. <a href="https://yao-lab.github.io/data/swissroll.m">m</a> is the matlab code) with ISOMAP. To construct the block <em>A</em>, you may choose either of the following:</li>

</ul>

<em>n </em>random data points;

<em>Homework 6. Manifold Learning                                                                                                                                              </em>3

*<em>n </em>landmarks as minimax <em>k</em>-centers (<a href="https://yao-lab.github.io/data/kcenter.m">https://yao-lab.github.io/data/kcenter. </a><a href="https://yao-lab.github.io/data/kcenter.m">m</a><a href="https://yao-lab.github.io/data/kcenter.m">)</a>;

Some references can be found at:

[dVT04] Vin de Silva and J. B. Tenenbaum, “Sparse multidimensional scaling using landmark points”, 2004, downloadable at <a href="http://pages.pomona.edu/~vds04747/public/papers/landmarks.pdf">http://pages.pomona.edu/</a><a href="http://pages.pomona.edu/~vds04747/public/papers/landmarks.pdf">~</a><a href="http://pages.pomona.edu/~vds04747/public/papers/landmarks.pdf">vds04747/ </a><a href="http://pages.pomona.edu/~vds04747/public/papers/landmarks.pdf">public/papers/landmarks.pdf</a><a href="http://pages.pomona.edu/~vds04747/public/papers/landmarks.pdf">;</a>

[P05] John C. Platt, “FastMap, MetricMap, and Landmark MDS are all Nystr¨om Algorithms”, 2005, downloadable at <a href="http://research.microsoft.com/en-us/um/people/jplatt/nystrom2.pdf">http://research.microsoft.com/en-us/um/people</a>/ <a href="http://research.microsoft.com/en-us/um/people/jplatt/nystrom2.pdf">jplatt/nystrom2.pdf</a><a href="http://research.microsoft.com/en-us/um/people/jplatt/nystrom2.pdf">.</a>

<ul>

 <li>*Assume that <em>A </em>is invertible, show that</li>

</ul>

det(<em>K</em>) = det(<em>A</em>) · det(<em>K/A</em>)<em>,</em>

<ul>

 <li>*Assume that <em>A </em>is invertible, show that</li>

</ul>

rank(<em>K</em>) = rank(<em>A</em>) + rank(<em>K/A</em>)<em>.</em>

<ul>

 <li>*Can you extend the identities in (c) and (d) to the case of noninvertible <em>A</em>? A good reference can be found at,</li>

</ul>

[Q81] Diane V. Quellette, “Schur Complements and Statistics”, Linear Algebra and Its Applications, 36:187-295, 1981. <a href="https://www.sciencedirect.com/science/article/pii/0024379581902329">http://www.sciencedirect.com/science/ </a><a href="https://www.sciencedirect.com/science/article/pii/0024379581902329">article/pii/0024379581902329</a>