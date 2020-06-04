
#ifndef _PROFILE_TABLEAU_HPP
#define _PROFILE_TABLEAU_HPP

/**
 * @brief Un tableau conservant un profil d'accès.
 *
 * Cette classe represente un tableau.  La premiere valeur du tableau
 * est a l'indice 0.
 * Ce tableau conserve une trace du nombre
 * d'acces pour chaque case.  Le nombre d'acces demarre a 0 et augmente de
 * 1 pour les acces de lecture et de un pour les acces d'ecriture.

 * Il est possible de consulter des statistiques sur le nombre d'acces.
 *    -# nombre d'acces pour chaque case.
 *    -# moyenne du nombre d'acces.
 *    -# ecart type.
 *    -# indexe des cases les plus accedes.
 */
class ProfileTableau {

    /**
	 * Represente le contenue du tableau, donc les valeurs accedes pour chaque 
	 * case.
	 */
    int * _contenue;

	
	/**
	 * Ce tableau est utilise pour maintenir le nombre d'acces total pour 
	 * chaque case du tableau.
	 *
	 * @invariant \f$\forall i, 0 \le \f$ _nbrAcces[\f$i\f$]
	 */
    double * _nbrAcces;


	/**
	 * Conserve la taille du tableau.
	 */
	int _taille;
	
	
    /**
	 * La moyenne des nombres d'acces au tableau.  Cette variable est utilisee 
	 * pour optimiser l'acces a la moyenne.  Elle conserve le resultat du 
	 * calcul de la moyenne tant qu'il n'y a pas de changement dans le 
	 * tableau.
	 */
	double _nbrAccesMoyen;
	
	
	/**
	 * Un booleen indiquant si le contenue de la variable _nbrAccesMoyen est
	 * a jour.
	 */
	bool _estValideNbrAccesMoyen;
	

	/**
	 * L'ecart type calcule sur le nombre d'acces.  Cette variable est utilisee 
	 * pour optimiser l'acces a l'ecart type.  Elle conserve le resultat du 
	 * calcul de l'ecart type tant qu'il n'y a pas de changement dans le 
	 * tableau.
	 */
	double _ecartType;
	
	
	/**
	 * Un booleen indiquant si le contenue de la variable _ecartType est
	 * a jour.
	 */
	bool _estValideEcartType;
	
	
	
public :

    /**
	 * @brief Constructeur.
	 *
	 * Construit un nouveau tableau avec systeme de profil automatise.
	 *
	 * @param [in] int la taille du tableau construit.
	 *  @pre 0 \f$<\f$ _taille
	 *
	 * @return un nouveau tableau qui a la taille demande.  Les cases du 
	 *         tableau n'ont pas ete initialise.
	 *  @post \f$\forall i, 0 = \f$ _nbrAcces[\f$i\f$]
	 */
    ProfileTableau( int );


    /**
	 * @brief Destructeur.
	 */
    virtual ~ProfileTableau( void );
    
	
	/**
	 * @brief setter pour les cases du tableau.
	 *
	 * Permet de placer une valeur dans le tableau.
	 * Cela aura pour effet d'incrementer de 1 le compteur d'acces de cette 
	 * case.
	 *
	 * @param [in] int la position a acceder dans le tableau.
	 *  @pre 0 \f$\le\f$ position \f$<\f$ _taille 
     *
	 * @return une reference sur la case du tableau.
	 */
    int & operator []( int );
	
	
    /**
	 * @brief Retourne la taille du tableau.
	 *
	 * @return le nombre d'elements contenu dans le tableau.
	 */
	int taille( void ) const;
	
	
	/**
	 * @brief Permet de consulter le nombre d'acces pour une case specifique.
	 *
	 * @param [in] int la position a acceder dans le tableau.
	 *  @pre 0 \f$\le\f$ position \f$<\f$ _taille 
	 *
	 * @return le nombre d'acces a cette case depuis la construction du 
	 *         tableau.
	 *  @post 0 \f$\le\f$ _nbrAcces[position]
	 */
    double nbrAcces( int ) const;
	
	
	/**
	 * @brief Retourne le nombre moyen d'acces par case pour le tableau.
	 *
	 * Une technique de memoisation est utilise afin de limiter le nombre de
	 * fois que le calcul est effectue.  Afin que cette mecanique reste 
	 * fonctionnelle, il est conseille de toujours utiliser cette fonction
	 * pour acceder a la moyenne.
	 *
	 * @return la moyenne
	 *  @post nbrAccesMoyen \f$= \frac{1}{\textrm{\underscore{}taille}}\sum_{i=0}^{\textrm{\underscore{}_taille}}\f$_nbrAcces[\f$i\f$]
	 */
	double nbrAccesMoyen( void );


	/**
	 * @brief Retourne l'ecart type des acces par case pour le tableau.
	 *
	 * Une technique de memoisation est utilise afin de limiter le nombre de
	 * fois que le calcul est effectue.  Afin que cette mecanique reste 
	 * fonctionnelle, il est conseille de toujours utiliser cette fonction
	 * pour acceder a l'ecart type.
	 *
	 * @return la moyenne
	 *  @post ecartType \f$= \sqrt{\frac{1}{\textrm{\underscore{}taille}}\sum_{i=0}^{\textrm{\underscore{}_taille}}(\textrm{\underscore{}_nbrAcces}[i]-\textrm{\underscore{}_nbrAccesMoyen})^2}
	 */
	double ecartType( void );
	
	
	/**
	 * @brief Retourne un tableau des indices des cases les plus utilises 
	 *        dans le tableau.
	 *
	 * Les cases les plus utilisees sont celles dont le nombre d'acces est 
	 * superieur ou egal a : moyenne + ecart type.
	 * Le tableau retourne doit avoir une taille egal au nombre d'indice
	 * retourne plus 1.
	 * La derniere case du tableau retourne va contenir la valeur -1.
	 * Les autres case vont contenir les indices des cases selectionnees.
	 * S'il n'y a pas de case selectionnee, alors le tableau de retour
	 * va contenir une seule case avec la valeur -1.
	 *
	 *   placez votre analyse ici
	 *
	 *   Pour ./pTri -s x:
	 *   
	 *   ./pTri -s 10
	 *   moyenne : 10.6
	 *   ecart type : 4.36348
	 *   indices les plus utilises : 7, 8						
	 *
	 *   Donne 2 valeurs sequentielles.
	 *  
	 *   
	 *   ./pTri -s 50
	 *   moyenne : 31.98
	 *   ecart type : 16.342
	 *   indices les plus utilises : 28, 38, 40, 41, 43, 44, 45, 46, 47, 48, 49		
	 *
	 *   Donne 2 valeurs seules, 2 valeurs sequentielles, les autres sequentielles.
	 *  
	 *
	 *   ./pTri -s 100
	 *   moyenne : 57.25
	 *   ecart type : 30.6021									
	 *   indices les plus utilises : 79, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99
	 *
	 *   Donnne 1 valeur seule, les autres sequentielles.
	 *   
	 *
 	 *   ./pTri -s 500	
	 *   moyenne : 259.02
	 *   ecart type : 146.115							
	 *   indices les plus utilises : 387, 391, 397, 398, 399, 400, 401, 402, 403, 404, 405, 406, 407, 408, 409, 410, 411, 412, 413, 414, 415, 416, 417, 418, 419, 420, 421, 422, 423, 424, 425, 426, 427, 428, 429, 430, 431, 432, 433, 434, 435, 436, 437, 438, 439, 440, 441, 442, 443, 444, 445, 446, 447, 448, 449, 450, 451, 452, 453, 454, 455, 456, 457, 458, 459, 460, 461, 462, 463, 464, 465, 466, 467, 468, 469, 470, 471, 472, 473, 474, 475, 476, 477, 478, 479, 480, 481, 482, 483, 484, 485, 486, 487, 488, 489, 490, 491, 492, 493, 494, 495, 496, 497, 498, 499
	 *
	 *   Donne 2 valeurs seules, les autres sequentielles.
	 *
	 *   Pour les ./pTri -s on observe que les indices representent les dernieres cases. Plus on augmente la valeur, plus le nombre d'elements augmente.
	 *
	 *
	 *   Pour ./pTri -b x:
 	 *
	 *   ./pTri -b 10
	 *   moyenne : 23.7
	 *   ecart type : 9.98048
	 *   indices les plus utilises : 2, 3
	 *
	 *   Donne 2 valeurs sequentielles.
	 *
	 *
	 *   ./pTri -b 50
	 *   moyenne : 92.3
	 *   ecart type : 38.0433
	 *   indices les plus utilises : 10, 11, 12, 13, 14, 15, 16
	 *
	 *   Donne des valeurs sequentielles.
         *
	 * 
	 *   ./pTri -b 100
	 *   moyenne : 192.35
	 *   ecart type : 76.5107
	 *   indices les plus utilises : 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36
 	 *
	 *   Donne des valeurs sequentielles.
	 *
	 *
	 *   ./pTri -b 500
	 *   moyenne : 983.818
	 *   ecart type : 416.917
	 *   indices les plus utilises : 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99, 100, 101, 102, 103, 104, 105, 106, 107, 108, 109, 110, 111, 112, 113, 114, 115, 116, 122, 123, 124, 125, 126, 127, 132, 133, 134, 135, 136, 137, 138
	 *
	 *   Donne des valeurs sequentielles.
	 *
	 *   Pour les ./pTri -b on observe que les indices representent les premieres cases. Plus on augmente la valeue, plus le nombre d'elements augmente. 
	 *
 	 *
	 *
 	 * @author : Sephora Thurel THUS15609305.
	 */
	int * indicesPlusUtilises( void );
};

#endif
