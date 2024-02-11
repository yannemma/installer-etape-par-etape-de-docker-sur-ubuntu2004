installer-etape-par-etape-de-docker-sur-ubuntu2004

Conditions préalables
Pour suivre ce tutoriel, vous aurez besoin des éléments suivants :

Un serveur Ubuntu 20.04 configuré en suivant le guide de configuration initiale du serveur Ubuntu 20.04 , comprenant un utilisateur sudo non root et un pare-feu.
Un compte sur Docker Hub si vous souhaitez créer vos propres images et les transférer vers Docker Hub, comme indiqué aux étapes 7 et 8.

Étape 1 — Installation de Docker

Le package d'installation Docker disponible dans le référentiel officiel Ubuntu n'est peut-être pas la dernière version. Pour garantir que nous obtenons la dernière version, nous installerons Docker à partir du référentiel Docker officiel. Pour ce faire, nous allons ajouter une nouvelle source de package, ajouter la clé GPG de Docker pour garantir la validité des téléchargements, puis installer le package.

Tout d’abord, mettez à jour votre liste de packages existante :
$ sudo apt update
Ensuite, installez quelques packages prérequis qui permettent aptd'utiliser des packages via HTTPS :
$ sudo apt install apt-transport-https ca-certificates curl software-properties-common
Ajoutez ensuite la clé GPG du référentiel Docker officiel à votre système :
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
Ajoutez le dépôt Docker aux sources APT :
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
Cela mettra également à jour notre base de données de packages avec les packages Docker du dépôt nouvellement ajouté.
Assurez-vous que vous êtes sur le point d'installer à partir du dépôt Docker au lieu du dépôt Ubuntu par défaut :
$ apt-cache policy docker-ce
Enfin, installez Docker :
$ sudo apt install docker-ce
Docker doit maintenant être installé, le démon démarré et le processus activé pour démarrer au démarrage. Vérifiez qu'il fonctionne :
$ sudo systemctl status docker
$ sudo usermod -aG docker username
$ sudo usermod -aG docker username


