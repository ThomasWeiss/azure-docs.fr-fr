---
title: "Comparaison des plans d’hébergement Azure Functions | Microsoft Docs"
description: "Découvrez comment choisir entre le plan Consommation et le plan App Service d’Azure Functions."
services: functions
documentationcenter: na
author: ggailey777
manager: cfowler
editor: 
tags: 
keywords: "azure functions, fonctions, plan consommation, plan app service, traitement des événements, webhooks, calcul dynamique, architecture sans serveur"
ms.assetid: 5b63649c-ec7f-4564-b168-e0a74cb7e0f3
ms.service: functions
ms.devlang: multiple
ms.topic: reference
ms.tgt_pltfrm: multiple
ms.workload: na
ms.date: 06/12/2017
ms.author: glenga
ms.custom: H1Hack27Feb2017
ms.openlocfilehash: cb6ade65879b245bf44800da3352354ba274ee5a
ms.sourcegitcommit: 6acb46cfc07f8fade42aff1e3f1c578aa9150c73
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="azure-functions-hosting-plans-comparison"></a>Comparaison des plans d’hébergement Azure Functions

## <a name="introduction"></a>Introduction

Vous pouvez exécuter la solution Azure Functions dans deux modes : le plan Consommation et le plan Azure App Service. Le plan Consommation alloue automatiquement la puissance de calcul pendant l’exécution du code, augmente la taille des instances quand c’est nécessaire pour gérer la charge, puis descend en puissance quand le code n’est pas en cours d’exécution. Vous n’avez donc pas à payer pour des machines virtuelles inactives ni à disposer d’une capacité de réserve à l’avance. Cet article est consacré au plan Consommation, un modèle d’application [sans serveur](https://azure.microsoft.com/overview/serverless-computing/). Pour plus d’informations sur le fonctionnement du plan App Service, consultez l’article [Présentation détaillée des plans d’Azure App Service](../app-service/azure-web-sites-web-hosting-plans-in-depth-overview.md). 

Si vous n’êtes pas familiarisé avec Azure Functions, consultez [Vue d’ensemble d’Azure Functions](functions-overview.md).

Quand vous créez une application de fonction, vous devez configurer un plan d’hébergement pour les fonctions que l’application contient. Dans ces deux modes, une instance de *l’hôte Azure Functions* exécute les fonctions. Le type de plan contrôle :

* la façon dont les instances d’hôte font l’objet d’une augmentation de taille ;
* les ressources disponibles pour chaque hôte.

Vous devez choisir le type de plan d’hébergement durant la création de l’application de fonction. Vous ne pouvez pas en changer ultérieurement. 

Dans un plan App Service, vous pouvez adapter les niveaux pour allouer différentes quantités de ressources. Dans le plan Consommation, Azure Functions gère automatiquement l’allocation de toutes les ressources.

## <a name="consumption-plan"></a>Plan de consommation

Quand vous utilisez un plan Consommation, les instances de l’hôte Azure Functions sont ajoutées et supprimées de façon dynamique en fonction du nombre d’événements entrants. Ce plan est mis à l’échelle automatiquement, et vous êtes facturé pour les ressources de calcul uniquement quand vos fonctions sont exécutées. Dans un plan Consommation, une fonction peut s’exécuter pendant 10 minutes au plus. 

> [!NOTE]
> Le délai d’expiration par défaut pour les fonctions dans un plan Consommation est de 5 minutes. Vous pouvez augmenter la valeur à 10 minutes pour l’application de fonction en modifiant la propriété `functionTimeout` dans [host.json](https://github.com/Azure/azure-webjobs-sdk-script/wiki/host.json).

La facturation est basée sur le nombre d’exécutions, la durée d’exécution et la mémoire utilisée. La facturation est unifiée pour toutes les fonctions d’une même application de fonction. Pour plus d’informations, consultez la page [Tarification d’Azure Functions].

Le plan d’hébergement par défaut (le plan Consommation) présente les avantages suivants :
- Paiement uniquement à l’exécution de vos fonctions
- Augmentation automatique de la taille des instances même pendant les périodes de charge élevée

## <a name="app-service-plan"></a>Plan App Service

Dans le plan App Service, vos applications de fonction sont exécutées sur des machines virtuelles dédiées sur des références SKU de base, Standard, Premium et Isolé, à l’instar de Web Apps, d’API Apps et de Mobile Apps. Les machines virtuelles dédiées sont allouées à vos applications App Service, ce qui signifie que l’hôte des fonctions est toujours en cours d’exécution.

Pensez à un plan App Service dans les cas suivants :
- Vous disposez de machines virtuelles existantes, sous-utilisées qui exécutent déjà d’autres instances App Service.
- Vous souhaitez que vos applications de fonction s’exécutent en continu ou presque. Dans ce cas, un plan App Service peut être plus économique.
- Vous avez besoin de plus d’options de mémoire ou de processeur que celles qui sont proposées dans le plan Consommation.
- Vous avez besoin d’une durée d’exécution supérieure à celle qui est autorisée dans le plan Consommation (de 10 minutes).
- Vous avez besoin de fonctionnalités qui sont disponibles uniquement dans un plan App Service, telles que la prise en charge d’App Service Environment, la connectivité des réseaux virtuels/VPN et la configuration de machines virtuelles volumineuses. 

L’utilisation d’une machine virtuelle dissocie le coût du nombre d’exécutions, de la durée d’exécution et de la mémoire utilisée. Vous ne payez donc pas plus que le coût de l’instance de machine virtuelle que vous allouez. Pour plus d’informations sur le fonctionnement du plan App Service, consultez l’article [Présentation détaillée des plans d’Azure App Service](../app-service/azure-web-sites-web-hosting-plans-in-depth-overview.md). 

Avec un plan App Service, vous pouvez augmenter manuellement la taille des instances en ajoutant des instances de machine virtuelle, ou vous pouvez activer la mise à l’échelle automatique. Pour plus d’informations, consultez [Mettre à l’échelle le nombre d’instances manuellement ou automatiquement](../monitoring-and-diagnostics/insights-how-to-scale.md?toc=%2fazure%2fapp-service-web%2ftoc.json). Vous pouvez également effectuer une montée en puissance en choisissant un autre plan App Service. Pour plus d’informations, consultez [Faire monter en puissance une application web dans Azure](../app-service/web-sites-scale.md). 

Si vous prévoyez d’exécuter des fonctions JavaScript dans un plan App Service, vous devez choisir un plan qui comporte moins de cœurs. Pour plus d’informations, consultez les [informations de référence sur JavaScript pour Functions](functions-reference-node.md#choose-single-core-app-service-plans).  

<!-- Note: the portal links to this section via fwlink https://go.microsoft.com/fwlink/?linkid=830855 --> 
<a name="always-on"></a>
### Toujours actif

Si vous utilisez un plan App Service, vous devez activer le paramètre **Toujours actif** afin que l’application de fonction s’exécute correctement. Dans un plan App Service, comme le runtime des fonctions devient inactif après quelques minutes d’inactivité, seuls des déclencheurs HTTP « relancent » vos fonctions. Ce fonctionnement est semblable à celui du service WebJobs pour lequel le paramètre Toujours actif doit toujours être activé. 

Le paramètre Toujours actif est disponible uniquement dans un plan App Service. Dans un plan Consommation, la plateforme active automatiquement les applications de fonction.

## <a name="storage-account-requirements"></a>Conditions requises pour le compte de stockage

Dans un plan Consommation ou un plan App Service, une application de fonction nécessite un compte de stockage Azure général prenant en charge les stockages Blob, File d’attente, Fichiers et Table Azure. En interne, Azure Functions utilise le stockage Azure pour les opérations telles que la gestion des déclencheurs et la journalisation des exécutions de fonctions. Certains comptes de stockage ne prennent pas en charge les files d’attente et les tables, comme les comptes de stockage Blob uniquement (notamment le stockage Premium) et les comptes de stockage à usage général avec la réplication ZRS. Ces comptes sont filtrés à partir du panneau **Compte de stockage** quand vous créez une application de fonction.

Pour en savoir plus sur les types de compte de stockage, consultez [Présentation des services Stockage Azure](../storage/common/storage-introduction.md#introducing-the-azure-storage-services).

## <a name="how-the-consumption-plan-works"></a>Fonctionnement du plan de consommation

Dans le plan Consommation, le contrôleur de mise à l’échelle met automatiquement à l’échelle les ressources processeur et mémoire en ajoutant des instances de l’hôte Functions en fonction du nombre d’événements en fonction desquels ses fonctions sont déclenchées. Chaque instance de l’hôte Functions est limitée à 1,5 Go de mémoire.

Quand vous utilisez le plan d’hébergement Consommation, les fichiers de code de fonction sont stockés dans des partages de fichiers Azure du compte de stockage principal de la fonction. Lorsque vous supprimez le compte de stockage principal de l’application de fonction, les fichiers de code de fonction sont supprimés et ne peuvent pas être récupérés.

> [!NOTE]
> Quand vous utilisez un déclencheur d’objet blob dans un plan Consommation, il peut y avoir jusqu’à 10 minutes de délai dans le traitement des nouveaux objets blob si une application de fonction est devenue inactive. Une fois l’application de fonction en cours d’exécution, les blobs sont traités immédiatement. Pour éviter ce délai initial, pensez à l’une des options suivantes :
> - Utilisez l’application de fonction dans un plan App Service, avec le paramètre Toujours actif activé.
> - Utilisez un autre mécanisme pour déclencher le traitement de l’objet blob, comme un message de file d’attente qui contient le nom de l’objet blob. Pour en obtenir un exemple, consultez [Déclencheur de file d’attente avec liaison d’entrée d’objet blob](functions-bindings-storage-blob.md#input-sample).

### <a name="runtime-scaling"></a>Mise à l’échelle du runtime

Azure Functions utilise un composant appelé *contrôleur de mise à l’échelle* pour surveiller la fréquence des événements et déterminer s’il convient de monter en puissance ou de diminuer la taille des instances. Le contrôleur de mise à l’échelle utilise une méthode heuristique pour chaque type de déclencheur. Par exemple, si vous utilisez un déclencheur de stockage File d’attente Azure, il est mis à l’échelle en fonction de la longueur de la file d’attente et de l’âge du plus ancien message en file d’attente.

L’unité de mise à l’échelle est l’application de fonction. Quand les instances de l’application de fonction font l’objet d’une augmentation de taille, des ressources supplémentaires sont allouées pour exécuter plusieurs instances de l’hôte Azure Functions. À l’inverse, quand la demande de calcul est réduite, le contrôleur de mise à l’échelle supprime des instances de l’hôte de fonction. Le nombre d’instances est finalement réduit à zéro si aucune fonction n’est exécutée dans une application de fonction.

![Contrôleur de mise à l’échelle surveillant les événements et créant des instances](./media/functions-scale/central-listener.png)

### <a name="billing-model"></a>Modèle de facturation

La facturation du plan de consommation est décrite en détail dans la page [Tarification d’Azure Functions]. L’utilisation est agrégée au niveau de l’application de fonction et compte uniquement la durée d’exécution du code de fonction. Les unités de facturation sont les suivantes : 
* **Consommation des ressources en gigaoctet/seconde (Go/s)**. Calcul effectué d’après une combinaison de la taille de la mémoire et de la durée d’exécution pour toutes les fonctions d’une application de fonction. 
* **Exécutions**. Comptées chaque fois qu’une fonction est exécutée en réponse à un déclencheur d’événements.

[Tarification d’Azure Functions]: https://azure.microsoft.com/pricing/details/functions
