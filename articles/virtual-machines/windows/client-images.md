---
title: "Utilisation d’images de client Windows dans Azure | Microsoft Docs"
description: "Comment utiliser les avantages de l’abonnement Visual Studio pour déployer Windows 7, Windows 8 ou Windows 10 dans Azure pour des scénarios de développement et/ou de test"
services: virtual-machines-windows
documentationcenter: 
author: iainfoulds
manager: timlt
editor: 
ms.assetid: 91c3880a-cede-44f1-ae25-f8f9f5b6eaa4
ms.service: virtual-machines-windows
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: vm-windows
ms.workload: infrastructure-services
ms.date: 07/05/2017
ms.author: iainfou
ms.openlocfilehash: 207a6562965b4913416bd4dbf3eb132b42938dc9
ms.sourcegitcommit: 6699c77dcbd5f8a1a2f21fba3d0a0005ac9ed6b7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2017
---
# <a name="use-windows-client-in-azure-for-devtest-scenarios"></a>Utilisation d’un client Windows dans Azure pour les scénarios de développement et/ou test
Vous pouvez utiliser Windows 7, Windows 8 ou Windows 10 dans Azure pour des scénarios de développement / de test à condition de disposer d'un abonnement Visual Studio (anciennement MSDN) approprié. Cet article décrit les conditions d’admissibilité pour les clients Windows en cours d’exécution dans Azure et l’utilisation des images de galerie Azure.

## <a name="subscription-eligibility"></a>Admissibilité à un abonnement
Les abonnés Visual Studio actifs (les personnes qui ont acquis une licence d’abonnement Visual Studio) peuvent utiliser un client Windows à des fins de développement et de tests. Un client Windows peut être utilisé sur votre propre matériel et vos machines virtuelles Azure en cours d’exécution dans n’importe quel type d’abonnement Azure. Il ne peut pas être déployé ou utilisé dans Azure pour la production normale ou utilisé par des personnes qui ne sont pas des abonnés Visual Studio actifs.

Pour votre commodité, certaines images Windows 10 disponibles sont disponibles dans la galerie Azure sous [eligible dev/test offers](#eligible-offers). Les abonnés Visual Studio dans n’importe quel type d’offre peuvent également [préparer et créer correctement](prepare-for-upload-vhd-image.md) une image 64 bits de Windows 7, Windows 8 ou Windows 10, puis la [charger dans Azure](upload-generalized-managed.md). L’utilisation reste limitée au développement/test par les abonnés Visual Studio actifs.

## <a name="eligible-offers"></a>Offres admissibles
Le tableau suivant décrit en détail les ID d’offres admissibles pour le déploiement de Windows 10 par le biais de la galerie Azure. Les images Windows 10 sont uniquement visibles par les offres suivantes. Les abonnés Visual Studio qui doivent exécuter le client Windows dans un autre type d’offre doivent [préparer et créer correctement](prepare-for-upload-vhd-image.md) une image 64 bits de Windows 7, Windows 8 ou Windows 10, [puis la charger dans Azure](upload-generalized-managed.md).

| Nom de l’offre | Numéro de l’offre | Images de client disponibles |
|:--- |:---:|:---:|
| [Pay-As-You-Go Dev/Test](https://azure.microsoft.com/offers/ms-azr-0023p/) |0023P |Windows 10 |
| [Abonnés Visual Studio Enterprise (MPN)](https://azure.microsoft.com/offers/ms-azr-0029p/) |0029P |Windows 10 |
| [Abonnés Visual Studio Professional](https://azure.microsoft.com/offers/ms-azr-0059p/) |0059P |Windows 10 |
| [Abonnés Visual Studio Test Professional](https://azure.microsoft.com/offers/ms-azr-0060p/) |0060P |Windows 10 |
| [Visual Studio Premium avec MSDN (avantage)](https://azure.microsoft.com/offers/ms-azr-0061p/) |0061P |Windows 10 |
| [Abonnés Visual Studio Enterprise](https://azure.microsoft.com/offers/ms-azr-0063p/) |0063P |Windows 10 |
| [Abonnés Visual Studio Enterprise (BizSpark)](https://azure.microsoft.com/offers/ms-azr-0064p/) |0064P |Windows 10 |
| [Enterprise Dev/Test](https://azure.microsoft.com/ofers/ms-azr-0148p/) |0148P |Windows 10 |

## <a name="check-your-azure-subscription"></a>Vérification de votre abonnement Azure
Si vous ne connaissez pas votre ID d’offre, vous pouvez l’obtenir via le portail Azure de l’une des manières suivantes :  

- Dans le panneau « Abonnements » :

  ![Détails de l’ID de l’offre dans le portail Azure](./media/client-images/offer-id-azure-portal.png) 

- Vous pouvez également cliquer sur **Facturation**, puis sur votre ID d’abonnement. L’ID d’offre s’affiche dans le panneau Facturation.

Vous pouvez également voir l’ID d’offre dans [l’onglet « Abonnements »](http://account.windowsazure.com/Subscriptions) du portail de compte Azure :

![Détails de l’ID de l’offre dans le portail de compte Azure](./media/client-images/offer-id-azure-account-portal.png) 

## <a name="next-steps"></a>Étapes suivantes
Vous pouvez désormais déployer vos machines virtuelles à l’aide de [PowerShell](quick-create-powershell.md), de [modèles Resource Manager](ps-template.md) ou de [Visual Studio](../../vs-azure-tools-resource-groups-deployment-projects-create-deploy.md).

