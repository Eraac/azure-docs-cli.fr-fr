---
title: Exécuter Azure CLI dans un conteneur Docker
description: Comment exécuter un conteneur Docker hébergeant Azure CLI
author: sptramer
ms.author: sttramer
manager: carmonm
ms.date: 01/29/2018
ms.topic: conceptual
ms.prod: azure
ms.technology: azure-cli
ms.devlang: azurecli
ms.openlocfilehash: 346014c1890cd7aa5b4225df15078e55db908a33
ms.sourcegitcommit: 334a1da92a73e42e715e33470057f4194f10b2ea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59289081"
---
# <a name="run-azure-cli-in-a-docker-container"></a>Exécuter Azure CLI dans un conteneur Docker

Vous pouvez utiliser Docker pour exécuter un conteneur Linux autonome avec Azure CLI préinstallée. Docker vous permet de vous familiariser rapidement avec un environnement isolé pour pouvoir y exécuter l’interface CLI. L’image peut également être utilisée comme base pour vos propres déploiements.

## <a name="run-in-a-docker-container"></a>Exécution dans un conteneur Docker

> [!NOTE]
> Azure CLI a été déplacé vers [Microsoft Container Registry](https://azure.microsoft.com/services/container-registry). Les balises existantes sur Docker Hub sont toujours prises en charge, mais les nouvelles versions pourront uniquement être utilisées sous la forme mcr.microsoft.com/azure-cli.

Installez l’interface de ligne de commande à l’aide de `docker run`.

   ```bash
   docker run -it mcr.microsoft.com/azure-cli
   ```

> [!NOTE]
> Si vous souhaitez sélectionner les clés SSH à partir de votre environnement utilisateur, utilisez `-v ${HOME}/.ssh:/root/.ssh` pour monter vos clés SSH dans l’environnement.
>
> ```bash
> docker run -it -v ${HOME}/.ssh:/root/.ssh mcr.microsoft.com/azure-cli
> ```

L’interface de ligne de commande est installé sur l’image en tant que commande `az` dans `/usr/local/bin`. Pour vous connecter, exécutez la commande [az login](/cli/azure/reference-index#az-login).

[!INCLUDE [interactive-login](includes/interactive-login.md)]

Pour en savoir plus sur les différentes méthodes d’authentification, consultez [Se connecter avec Azure CLI](authenticate-azure-cli.md).

## <a name="update-docker-image"></a>Mise à jour d’une image Docker

La mise à jour avec Docker nécessite l’extraction de la nouvelle image et la recréation de tous les conteneurs existants. Pour cette raison, évitez d’utiliser un conteneur hébergeant l’interface CLI comme magasin de données.

Mettre à jour votre image locale avec `docker pull`.

```bash
docker pull mcr.microsoft.com/azure-cli
```

## <a name="uninstall-docker-image"></a>Désinstallation d’une image Docker

[!INCLUDE [uninstall-boilerplate.md](includes/uninstall-boilerplate.md)]

Après l’arrêt de tous les conteneurs exécutant l’image de l’interface CLI, supprimez-la.

```bash
docker rmi mcr.microsoft.com/azure-cli
```

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous êtes prêt à utiliser l’interface CLI, découvrez ses fonctionnalités et ses commandes courantes.

> [!div class="nextstepaction"]
> [Prise en main de l’interface Azure CLI](get-started-with-azure-cli.md)
