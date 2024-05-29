Éléments finis bidimensionnels
===============================

Considérons, par exemple, :math:`u(x)=2(1-x^3)x`. Nous désirons obtenir une interpolation :math:`u^h(x)` au moyen de polynômes par morceaux. Sur la figure ??, nous considérons un cas très simple. Le domaine :math:`\Omega` est divisés en deux segments, qui sont appelés *éléments finis*. Leur longueur est respectivement 0.6 et 0.4. Sur chaque élément, nous désirons remplacer la fonction :math:`u` par une fonction polynomiale

Le cas le plus simple est celui où l'approximation est un polynôme d'ordre zéro, c'est-à-dire une constante sur chaque élément. On a ici choisi la valeur :math:`u` au centre de l'élément comme constante. L'approximation :math:`u^h` est continue par morceaux.

figure 1.1

Nous pouvons ensuite introduire une interpolation linéaire par morceaux au moyen de polynômes du premier degré. L'approximation est maintenant continue. Dans la troisième partie de la figure, on introduit un polynôme du second degré dans chaque élément. Les coefficients du polynôme sont déterminés par l'imposition de la valeur de :math:`u` aux extrémités et au milieu de l'élément.

Après avoir présenté le problème au moyen d'une exemple simple, définissions en termes plus généraux le processus d’approximation de :math:`u` sur le domaine :math:`\Omega` en un nombre donné d'éléments :math:`\Omega_e=\left]X_e,X_{e+1}\right[`, segments ouverts successifs qui ne se recouvrent pas. On définit ainsi une partition de :math:`\Omega` appelée maillage. Les points :math:`X_e` aux extrémités des éléments sont appelés les sommets du maillage. De manière plus formelle, un maillage d'un domaine :math:`\Omega` doit être tel que :

.. math::
    \overline\Omega = \bigcup_{e=1}^{N_1}\{\overline\Omega_e\},\quad \Omega_e\cap\Omega_f = \emptyset,\quad \text{si } e\ne f

La taille d'un tel maillage est caractérisée par l'un des deux nombres :

- :math:`N_0` le nombre de sommets,
- :math:`N_1=N_0-1` le nombre d'éléments.

**Élément parent**

Pour construire une interpolation polynomiale sur ces éléments qui peuvent être de longueurs diverses, il est opportun d'établir un isomorphisme entre chaque point :math:`x` de chaque élément :math:`\Omega_e` et un point :math:`\xi` de l'intervalle ouvert :math:`\hat\Omega=\left]-1,+1\right[`,

fig 1.2

.. math::
    :name: eq:xtoxi
   
    \begin{aligned}
    x(\xi) &= \xi\frac{(X_{e+1}-X_e)}2 + \frac{(X_{e+1}+X_e)}2,\\
    \xi(x) &= \frac{2x-(X_{e+1}+X_e)}{(X_{e+1}-X_e)}.
    \end{aligned}

L'isomorphisme est illustré à la figure 1.2. L'intervalle :math:`\hat\Omega` est appelé *l'élément parent*. Les coordonées :math:`x\in\Omega_e` et :math:`\xi\in\hat\Omega` sont reliées entre elles de manière univoque par les relations :ref:`ci-dessus <eq:xtoxi>`.
