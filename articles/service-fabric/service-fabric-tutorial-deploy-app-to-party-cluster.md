---
title: "Déployer une application Azure Service Fabric sur un cluster tiers | Microsoft Docs"
description: "Découvrez comment déployer une application sur un cluster tiers."
services: service-fabric
documentationcenter: .net
author: mikkelhegn
manager: msfussell
editor: 
ms.assetid: 
ms.service: service-fabric
ms.devlang: dotNet
ms.topic: tutorial
ms.tgt_pltfrm: NA
ms.workload: NA
ms.date: 08/09/2017
ms.author: mikhegn
ms.custom: mvc
ms.openlocfilehash: d7496b0578301713ebae7381e9a54642e226eb96
ms.sourcegitcommit: adf6a4c89364394931c1d29e4057a50799c90fc0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="deploy-an-application-to-a-party-cluster-in-azure"></a>Déployer une application sur un cluster tiers dans Azure
Deuxième d’une série, ce didacticiel vous montre comment déployer une application Azure Service Fabric sur un cluster tiers dans Azure.

Dans ce deuxième volet, vous apprenez à :
> [!div class="checklist"]
> * Déployer une application sur un cluster distant à l’aide de Visual Studio
> * Supprimer une application d’un cluster à l’aide de Service Fabric Explorer

Cette série de didacticiels vous montre comment effectuer les opérations suivantes :
> [!div class="checklist"]
> * [Créer une application .NET Service Fabric](service-fabric-tutorial-create-dotnet-app.md)
> * Déployer l’application sur un cluster distant
> * [Configurer l’intégration et le déploiement continus à l’aide de Visual Studio Team Services](service-fabric-tutorial-deploy-app-with-cicd-vsts.md)
> * [Configurer la surveillance et les diagnostics pour l’application](service-fabric-tutorial-monitoring-aspnet.md)

## <a name="prerequisites"></a>Composants requis
Avant de commencer ce didacticiel :
- Si vous n’avez pas d’abonnement Azure, créez un [compte gratuit](https://azure.microsoft.com/free/?WT.mc_id=A261C142F).
- [Installez Visual Studio 2017](https://www.visualstudio.com/) et les charges de travail **Développement Azure** et **Développement web et ASP.NET**.
- [Installez le Kit de développement logiciel (SDK) Service Fabric](service-fabric-get-started.md).

## <a name="download-the-voting-sample-application"></a>Télécharger l’exemple d’application de vote
Si vous n’avez pas généré l’exemple d’application de vote lors de la [première partie de cette série de didacticiels](service-fabric-tutorial-create-dotnet-app.md), vous pouvez le télécharger. Dans une fenêtre Commande, exécutez la commande suivante pour cloner le référentiel de l’exemple d’application sur votre ordinateur local.

```
git clone https://github.com/Azure-Samples/service-fabric-dotnet-quickstart
```

## <a name="set-up-a-party-cluster"></a>Configurer un cluster tiers
Les clusters tiers sont des clusters Service Fabric gratuits et limités dans le temps. Ils sont hébergés sur Azure et exécutés par l’équipe Service Fabric, dont tous les membres peuvent déployer des applications et en savoir plus sur la plateforme gratuitement.

Pour accéder à un cluster tiers, rendez-vous sur le site http://aka.ms/tryservicefabric et suivez les instructions. Vous avez besoin d’un compte Facebook ou GitHub pour accéder à un cluster tiers.

Si vous le souhaitez, vous pouvez utiliser votre propre cluster à la place du cluster tiers.  Le frontend web ASP.NET Core utilise le proxy inverse pour communiquer avec le backend de service avec état.  Le proxy inverse est activé par défaut sur les clusters tiers et le cluster de développement local.  Si vous déployez l’exemple d’application Voting sur votre propre cluster, vous devez [activer le proxy inverse dans le cluster](service-fabric-reverseproxy.md#setup-and-configuration).

> [!NOTE]
> Les clusters tiers ne sont pas sécurisés. Vos applications et toutes les données que vous y placez sont donc visibles par d’autres personnes. Ne déployez aucun élément que vous souhaitez cacher aux autres utilisateurs. Veillez à lire les conditions d’utilisation pour plus d’informations.

## <a name="deploy-the-app-to-the-azure"></a>Déployer l’application dans Azure
Maintenant que l’application est prête, vous pouvez la déployer sur le cluster tiers directement à partir de Visual Studio.

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur **Voting**, puis choisissez **Publier**.

    ![Boîte de dialogue Publier](./media/service-fabric-tutorial-deploy-app-to-party-cluster/publish-app.png)

2. Saisissez le point de terminaison de connexion du cluster tiers dans le champ **Point de terminaison de connexion** et cliquez sur **Publier**.

    Une fois la publication terminée, vous devez être en mesure d’envoyer une demande à l’application via un navigateur.

3. Ouvrez le navigateur de votre choix et saisissez l’adresse du cluster (le point de terminaison de connexion sans les informations de port ; par exemple, win1kw5649s.westus.cloudapp.azure.com).

    Vous devez maintenant obtenir le même résultat que lors de l’exécution de l’application en local.

    ![Réponse de l’API à partir du cluster](./media/service-fabric-tutorial-deploy-app-to-party-cluster/response-from-cluster.png)

## <a name="remove-the-application-from-a-cluster-using-service-fabric-explorer"></a>Supprimer l’application d’un cluster à l’aide de Service Fabric Explorer
Service Fabric Explorer est une interface utilisateur graphique qui permet d’explorer et de gérer des applications dans un cluster Service Fabric.

Pour supprimer l’application du cluster tiers :

1. Accédez à Service Fabric Explorer à l’aide du lien fourni sur la page d’inscription du cluster tiers. Par exemple, http://win1kw5649s.westus.cloudapp.azure.com:19080/Explorer/index.html.

2. Dans Service Fabric Explorer, accédez au nœud **fabric://Voting**, dans l’arborescence figurant sur le côté gauche.

3. Cliquez sur le bouton **Action** dans le volet **Essentials** à droite, puis choisissez **Supprimer l’application**. Confirmez la suppression de l’instance d’application, ce qui supprime l’instance de notre application en cours d’exécution dans le cluster.

![Supprimer l’application dans Service Fabric Explorer](./media/service-fabric-tutorial-deploy-app-to-party-cluster/delete-application.png)

## <a name="remove-the-application-type-from-a-cluster-using-service-fabric-explorer"></a>Supprimer le type d’application d’un cluster à l’aide de Service Fabric Explorer
Les applications sont déployées en tant que types d’applications dans un cluster Service Fabric, ce qui vous permet d’avoir plusieurs instances et versions de l’application en cours d’exécution au sein du cluster. Après avoir supprimé l’instance en cours d’exécution de notre application, nous pouvons également supprimer le type pour nettoyer le déploiement.

Pour plus d’informations sur le modèle d’application dans Service Fabric, consultez [Modéliser une application dans Service Fabric](service-fabric-application-model.md).

1. Accédez au nœud **VotingType** dans l’arborescence.

2. Cliquez sur le bouton **Action** dans le volet **Essentials** à droite, puis choisissez **Unprovision Type** (Annuler la mise en service du type). Confirmez l’annulation de la mise en service du type d’application.

![Annuler la mise en service du type d’application dans Service Fabric Explorer](./media/service-fabric-tutorial-deploy-app-to-party-cluster/unprovision-type.png)

Cela conclut le didacticiel.

## <a name="next-steps"></a>Étapes suivantes
Dans ce didacticiel, vous avez appris à :

> [!div class="checklist"]
> * Déployer une application sur un cluster distant à l’aide de Visual Studio
> * Supprimer une application d’un cluster à l’aide de Service Fabric Explorer

Passez au didacticiel suivant :
> [!div class="nextstepaction"]
> [Configurer l’intégration continue avec Visual Studio Team Services](service-fabric-tutorial-deploy-app-with-cicd-vsts.md)