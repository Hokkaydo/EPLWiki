Éléments finis unidimensionnels
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

Élément parent
------------------

Pour construire une interpolation polynomiale sur ces éléments qui peuvent être de longueurs diverses, il est opportun d'établir un isomorphisme entre chaque point :math:`x` de chaque élément :math:`\Omega_e` et un point :math:`\xi` de l'intervalle ouvert :math:`\hat\Omega=\left]-1,+1\right[`,

fig 1.2

.. math::
    :label: xtoxi
   
    \begin{aligned}
    x(\xi) &= \xi\frac{(X_{e+1}-X_e)}2 + \frac{(X_{e+1}+X_e)}2,\\
    \xi(x) &= \frac{2x-(X_{e+1}+X_e)}{(X_{e+1}-X_e)}.
    \end{aligned}

L'isomorphisme est illustré à la figure 1.2. L'intervalle :math:`\hat\Omega` est appelé *l'élément parent*. Les coordonées :math:`x\in\Omega_e` et :math:`\xi\in\hat\Omega` sont reliées entre elles de manière univoque par les relations :eq:`xtoxi`.

Valeurs nodales et fonctions de forme locales
---------------------------------------------

Définissons sur :math:`\hat\Omega` une base de polynômes :math:`\phi_i` de degré :math:`p` de la manière suivante. Nous sélectionnons un nombre :math:`p + 1` de noeuds :math:`\Xi_i` sur l'intervalle parent. A chaque noeud est
associé une fonction de la base, c’est-à-dire un polynôme de degré :math:`p` valant l'unité pour le noeud auquel elle est associée et s'annulant aux autres noeuds.

fig 1.3

Il est dès lors possible de construire des bases de fonctions de forme de degrés divers :

- Pour les polynômes de degré 0, on a besoin d'une seule fonction de base,

.. math::
   \phi_1(\xi) = 1.

- Pour les polynômes du premier degré, nous choisissons les deux noeuds aux extrémités de l'élément parent, et obtenus une base des fonctions linéaires, 

.. math::
   \begin{aligned}
   \phi_1(\xi) &= (1-\xi)/2,\\
   \phi_2(\xi) &= (1+\xi)/2.\\
   \end{aligned}

- Pour les polynômes du deuxième degré, nous pouvons identifier deux noeuds aux extrémités et un noeud au centre de l'élément parent. Nous obtenons ainsi une base des fonctions quadratiques,

.. math::
   \begin{aligned}
   \phi_1(\xi) &= -\xi(1-\xi)/2,\\
   \phi_2(\xi) &= \xi(1+\xi)/2,\\
   \phi_3(\xi) &= (1-\xi)(1+\xi).
   \end{aligned}

La figure ?? montre clairement l'allure et la signification de ces fonctions. Il est clair que d'autres choix sont possibles et nous aborderons ce probblème plus tard.

Une interpolation :math:`u^h` de degré :math:`p` sur l'élément :math:`\Omega_e` passant par des valeurs nodales :math:`U_i^e` s'obtient ensuite par combinaison linéaire des fonctions de base 

.. math::
    :label: local_form

    u^h(x) = \sum^{p+1}_{i=1}U_i^e\phi_i^e(x),\quad x\in\Omega_e,

où les :math:`U_i^e` sont les *valeurs nodales locales* inconnues a priori, tandis que les fonctions de base :math:`\phi_i^e(x)=\phi_e(\xi(x))` connues a priori sont appelées les *fonctions de forme locales*. De façon plus synthétique, on parle d'*élément unidimensionnel constant discontinu*, d'*élément unidimensionnel linéaire continu* ou *unidimensionnel quadratique continu* pour caractériser le choix d'un type d'élément et d'une base de fonctions de forme sur cet élément.

Valeurs nodales et fonctions de forme globales
----------------------------------------------

Nous avons montré qu'une interpolation peut être construite en associant les valeurs nodales et les fonctions de forme dans chaque élément. Par la suite, il sera utile d'écrire une expression sur le domaine :math:`\Omega` plutôt que sur les éléments séparés. 

Dans cette optique, nous sélectionnons un nombre :math:`N` de noeuds dont on donne les positions :math:`X^{node}_i` au sein du maillage. Ces noeuds peuvent être à nouveau les extrémités d'éléments, ou des points à l'intérieur des éléments. Il est fondamental de distinguer, dès à présent, les concepts de noeud et de sommet, comme nous l'illustrons sur la figure ??. Un sommet est un point à l'intersection de plusieurs éléments finis, tandis qu'un noeud est un point où est définie une valeur discrète ou nodale de l'interpolation.

fig 1.4

L'interpolation globale :math:`u^h` peut alors s'écrire,

.. math::
    :label: global_form

    u^h(x) = \sum^N_{j=1} U_j\tau_j(x)

où les :math:`U_j` sont les *valeurs nodales globales*, tandis que les :math:`\tau_j(x)` les *fonctions de forme globales*. Cette équation montre clairement que l'approximation :math:`u^h` dépend d'un nombre fini de valeurs nodales. Appelons :math:`\mathcal U` l'espace fonctionnel dans lequel est inclus la solution exacte :math:`u`. On constate que les fonctions de forme globales forment la base d'un sous-espace :math:`\mathcal U^h` de dimension :math:`N`, appelé un *sous-espace discret*.

Afin de construire la forme globale :eq:`global_form` à partir de la forme locale :eq:`local_form`, il est nécessaire de définir la correspondance entre noeuds locaux et noeuds globaux de la manière suivante.

.. TODO grid à retravailler !

+-----------------------------+----------------------------------+
|                             |                                  |
+=============================+==================================+
|                             | Indice local de noeud :math:`i`  |
+-----------------------------+----------------------------------+
| Indice d'éléments :math:`e` | Indice global de noeud :math:`j` |
+----------------------------------------------------------------+

Ces correspondances peuvent être établies très facilement dans le cas unidimensionnel.

- Nous pouvons construire ainsi toutes les fonctions de forme globales linéaires sur un éléments :math:`\Omega_e`.

.. math::
  \begin{aligned}
  \tau_e(x) &= \phi_1^e(x),&\quad &\quad &x\in\Omega_e,\\
  \tau_{e+1}(x) &= \phi_2^e(x),&\quad &\quad &x\in\Omega_e,\\
  \tau_f(x) &= 0,&\quad &f\not\in\{e,e+1\}, &x\in\Omega_e.
  \end{aligned}

- Il est facile de suivre le même raisonnement pour une interpolatio,n quadratique et d'obtenir les fonctions de forme globales correspondantes sur un élément :math:`\Omega_e`

.. math::
      \begin{aligned}
      \tau_{2e-1}(x) &= \phi_1^e(x),&\quad &\quad &x\in\Omega_e,\\
      \tau_{2e}(x) &= \phi_3^e(x),&\quad &\quad &x\in\Omega_e,\\
      \tau_{2e+1}(x) &= \phi_2^e(x),&\quad &\quad &x\in\Omega_e,\\
      \tau_f(x) &= 0, && f\not\in\{2e-1,2e, 2e+1\}, &x\in\Omega_e.
      \end{aligned}

Le fait que les fonctions :math:`\tau_i` sont des fonctions polynomiales par morceaux qui s'annulent en dehors d'un support compact est une des caractéristiques principales de la méthode des éléments finis. Nous verrons ultérieurement que c'est aussi une des clés du succès et de la popularité de la méthode.


