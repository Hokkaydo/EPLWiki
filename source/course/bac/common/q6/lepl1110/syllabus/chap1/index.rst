Interpolation sur un maillage non structuré
============================================
Supposons que nous disposions d'une fonction connue :math:`u\in\mathcal U`. La méthode des éléments finis consiste à écrire cette interpolation sous la forme suivante

.. math::
   u^h(\mathbf x) = \sum^n_{j=1}U_j\tau_j(\mathbf x)

où :math:`U_j` sont des *valeurs nodales* inconnues, tandis que :math:`\tau_j` sont des *fonctions de forme* spécifiées a priori et appartenant à l'espace :math:`\mathcal U`. Les fonctions de forme sont choisies afin qu'aucune d'entre elles ne puisse être obtenue par combinaison linéaire des autres.

Il y a donc :math:`n` degrés de libertés pour définir un élément particuleir du sous-espace discret :math:`\mathcal U^h\in\mathcal U`. La dimension :math:`\mathcal U^h` est clairement :math:`n` et les fonctions de forme sont une base de cet espace dont tous les éléments sont obtenus par une combinaison linéaire unique des éléments de cette base. La plupart des fonctions de forme utilisées sont associées à un point particulier de l'esapce :math:`\mathbf X_i` et satisfont la propriété suivante :

.. math::
   \tau_j(\mathbf X_i)=\delta_{ij}

où :math:`\delta_{ij}` est le symbole de Kronecker (:math:`\delta_{ij}=1` si :math:`i=j` et :math:`0` autrement).

On peut directement en déduire que les valeurs nodales sont les valeurs de :math:`u^h` en :math:`\mathbf X_i`.

.. math::
   \begin{aligned}
   u^h(\mathbf X_i) &= \sum^n_{j=1}U_j\tau_j(\mathbf X_i),\\
   u^h(\mathbf X_i) &= \sum^n_{j=1}U_j\delta_{ij}\\
   u^h(\mathbf X_i) &= U_i.
   \end{aligned}

.. toctree::
    :maxdepth: 1
    
    unidimensional
    bidimensional
