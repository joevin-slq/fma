# Classification de genres musicaux

## Code

Les notebooks suivants ont été crées en vue de réaliser un projet de **classification de genres musicaux** dans le cadre du cours **INF6243 - Techniques d'apprentissage** réalisé par **Mohand Allili Said** à **l'Université du Québec en Outaouais**.

1. `1_extraction`: extraction de l'indicateur audio MFCC
2. `2_comparaison_classifieurs`: comparaison des différents classifieurs
3. `3_prediction`: prédiction sur des musiques individuelles
4. `4_classification`: classification via SVM


## Donnnées

Plusieurs versions de la base de données existent :

1. **[fma_small.zip]**: 8,000 musiques de 30s, 8 genres (7.2 GiB)
2. **[fma_medium.zip]**: 25,000 musiques de 30s, 16 genres (22 GiB)
3. **[fma_large.zip]**: 106,574 musiques de 30s, 161 genres (93 GiB)
4. **[fma_full.zip]**: 106,574 musiques, 161 genres (879 GiB)

[fma_metadata.zip]: https://os.unil.cloud.switch.ch/fma/fma_metadata.zip
[fma_small.zip]:    https://os.unil.cloud.switch.ch/fma/fma_small.zip
[fma_medium.zip]:   https://os.unil.cloud.switch.ch/fma/fma_medium.zip
[fma_large.zip]:    https://os.unil.cloud.switch.ch/fma/fma_large.zip
[fma_full.zip]:     https://os.unil.cloud.switch.ch/fma/fma_full.zip


## Installation

Installation depuis l'image Docker fournie :

	cd docker/
	docker build -t fma .
	docker run --name=fma -d -p 8888:8888 fma
	docker logs fma


## Crédits

Modifications réalisées par : Lionel Baptiste, Ghali El Ouarzazi et Joévin Soulenq. 

Auteurs originels : [Michaël Defferrard](http://deff.ch), [Kirell Benzi](http://kirellbenzi.com), [Pierre Vandergheynst](https://people.epfl.ch/pierre.vandergheynst), [Xavier Bresson](http://www.ntu.edu.sg/home/xbresson), [EPFL LTS2](https://lts2.epfl.ch).

La banque de données : [Free Music Archive (FMA)](https://freemusicarchive.org).

## License

Le code source présent dans cette page est est sous la license :
[MIT license](LICENSE.txt).
