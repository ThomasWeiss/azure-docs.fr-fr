---
title: Forum aux questions pour Azure Cost Management | Microsoft Docs
description: "Fournit des réponses à certaines des questions les plus fréquemment posées sur Azure Cost Management."
services: cost-management
keywords: 
author: bandersmsft
ms.author: banders
ms.date: 10/23/2017
ms.topic: article
ms.service: cost-management
manager: carmonm
ms.custom: 
ms.openlocfilehash: a01d8d1ed0f5234f4950d448b54087767353c8ef
ms.sourcegitcommit: 3ab5ea589751d068d3e52db828742ce8ebed4761
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="frequently-asked-questions-for-azure-cost-management"></a>Forum aux questions pour Azure Cost Management


Cet article traite des questions courantes sur Azure Cost Management (également appelé Cloudyn). Si vous avez des questions sur la Gestion des coûts, vous pouvez les poser dans le [FAQ pour Azure Cost Management par Cloudyn](https://social.msdn.microsoft.com/Forums/en-US/231bf072-2c71-4121-8339-ac9d868137b9/faqs-for-azure-cost-management-by-cloudyn?forum=Cloudyn).

## <a name="how-can-i-resolve-common-indirect-enterprise-setup-problems"></a>Comment puis-je résoudre des problèmes courants de configuration d’entreprise indirecte ?

Lorsque vous utilisez le portail Cloudyn pour la première fois, les messages suivants peuvent s’afficher si vous disposez d’un contrat Entreprise ou de fournisseur de solutions cloud (CSP) :

- « La clé d’API spécifiée n’est pas une clé d’inscription de niveau supérieur », dans l’Assistant **Configurer Azure Cost Management**.
- « Inscription directe – Non », sur le portail Contrat Entreprise.
- « Aucune donnée d’utilisation trouvée pour les 30 derniers jours. Contactez votre distributeur pour vous assurer que le balisage a été activé pour votre compte Azure », sur le portail Cloudyn.

Ces messages indiquent que vous avez acheté un Contrat Entreprise Azure via un revendeur ou un CSP. Votre revendeur ou CSP doit activer le _balisage_ pour votre compte Azure afin que vous puissiez afficher vos données dans Cloudyn.

Voici comment corriger les problèmes :

1. Votre revendeur doit activer le _balisage_ pour votre compte. Consultez les instructions sous [Indirect Customer Onboarding Guide](https://ea.azure.com/api/v3Help/v2IndirectCustomerOnboardingGuide) (Guide d’intégration de client indirecte).

2. Vous générez la clé Azure Enterprise Agreement à utiliser avec Cloudyn. Consultez les instructions sous [Adding Your Azure EA](https://support.cloudyn.com/hc/en-us/articles/210429585-Adding-Your-AZURE-EA) (Ajout de votre Azure EA) ou [How to Find Your EA Enrollment ID and API Key](https://youtu.be/u_phLs_udig) (Comment trouver l’ID d’inscription EA et la clé API).

Seul un administrateur de service Azure peut activer la Gestion des coûts. Les autorisations de coadministrateur sont insuffisantes.

Afin de pouvoir générer la clé API Azure Enterprise Agreement pour configurer Cloudyn, activez l’API de facturation Azure en suivant les instructions sous :

- [Vue d’ensemble des API de création de rapports pour les clients Enterprise](../billing/billing-enterprise-api.md)
- [API de création de rapports Microsoft Azure Enterprise Portal](https://ea.azure.com/helpdocs/reportingAPI) sous **Autoriser l’API à accéder aux données**


Vous devrez peut-être également accorder aux administrateurs de service, propriétaires de compte et administrateurs d’entreprise l’autorisation _d’afficher les frais_ avec l’API de facturation.

## <a name="how-do-i-enable-suspended-or-locked-out-users"></a>Comment faire pour activer les utilisateurs suspendus ou verrouillés ?

Si vous recevez une alerte vous demandant d’autoriser l’accès pour un utilisateur, vous devez activer le compte d’utilisateur.

Pour activer le compte d’utilisateur :

1. Connectez-vous à Cloudyn à l’aide du compte d’utilisateur administrateur Azure que vous avez utilisé pour configurer Cloudyn. Ou connectez-vous avec un compte d’utilisateur qui bénéficie de l’accès administrateur.

2. Sélectionnez le symbole d’engrenage dans le coin supérieur droit et sélectionnez **User Management** (Gestion des utilisateurs).

3. Recherchez l’utilisateur, sélectionnez l’icône du crayon, puis modifiez l’utilisateur.

4. Sous **User status** (État de l’utilisateur), modifiez l’état de **Suspended** (Suspendu) à **Active** (Actif).

Les comptes d’utilisateur Cloudyn se connectent à l’aide de l’authentification unique à partir d’Azure. Si un utilisateur ne saisit pas correctement son mot de passe, il peut être verrouillé dans Cloudyn, même s’il a toujours accès à Azure.

Si vous modifiez votre adresse e-mail dans Cloudyn pour une adresse autre que l’adresse par défaut dans Azure, votre compte risque d’être verrouillé. L’erreur suivante peut s’afficher : « status initiallySuspended. » Si votre compte d’utilisateur est verrouillé, contactez un autre administrateur pour réinitialiser votre compte.

Nous vous recommandons de créer au moins deux comptes d’administrateur Cloudyn au cas où l’un des comptes serait verrouillé.

Si vous ne pouvez pas vous connecter au portail Cloudyn, vérifiez que vous utilisez l’URL Azure Cost Management correcte pour vous connecter à Cloudyn. Utilisez l’une des URL suivantes :

- https://azure.cloudyn.com
- https://ms.portal.azure.com/#blade/Microsoft_Azure_CostManagement/CloudynMainBlade

Évitez d’utiliser l’URL Cloudyn directe https://app.cloudyn.com.

## <a name="how-do-i-activate-unactivated-accounts-with-azure-credentials"></a>Activation de comptes désactivés avec les informations d’identification Azure

Dès que vos comptes Azure sont découverts par Cloudyn, les données de coût sont immédiatement fournies dans des rapports basés sur les coûts. Toutefois, pour que Cloudyn fournisse des données sur l’utilisation et les performances, vous devez enregistrer vos informations d’identification Azure pour les comptes. Pour obtenir des instructions, consultez la page [Add Azure Resource Manager](https://support.cloudyn.com/hc/en-us/articles/212784085-Adding-Azure-Resource-Manager) (Ajouter Azure Resource Manager).

Pour ajouter des informations d’identification Azure pour un compte, dans le portail Cloudyn, sélectionnez le symbole de modification à droite du nom du compte, pas de l’abonnement.

Tant que vos informations d’identification Azure ne sont pas ajoutées dans Cloudyn, le compte apparaît comme étant _non activé_.

## <a name="how-do-i-add-multiple-accounts-and-entities-to-an-existing-subscription"></a>Comment ajouter plusieurs comptes et entités à un abonnement existant ?

Les entités supplémentaires sont utilisées pour ajouter des Contrats Entreprise supplémentaires dans un abonnement Cloudyn. Les liens suivants décrivent comment ajouter des entités supplémentaires :

- Article [Ajout d’une entité](https://support.cloudyn.com/hc/en-us/articles/212016145-Adding-an-Entity)
- Vidéo [Définition de votre hiérarchie avec les entités de coût](https://support.cloudyn.com/hc/en-us/articles/115005142529-Video-Defining-your-hierarchy-with-Cost-Entities)

Pour les CSP :

Pour ajouter des comptes CSP supplémentaires à une entité, sélectionnez **MSP Access** (Accès MSP) au lieu de **Enterprise** (Entreprise) lorsque vous créez la nouvelle entité. Si votre compte est inscrit en tant qu’Accord Entreprise et si vous souhaitez ajouter des informations d’identification CSP, le service de support technique Cloudyn devra peut-être modifier les paramètres de votre compte. Si vous êtes un abonné Azure payant, vous pouvez créer une nouvelle demande de support dans le portail Azure. Sélectionnez **Aide + Support**, puis **Nouvelle demande de support**.

## <a name="how-do-i-change-the-currency-symbol-used-in-cloudyn"></a>Comment modifier le symbole monétaire utilisé dans Cloudyn ?

Lorsque tous les comptes Azure dans une seule entité utilisent la même devise, la devise que vous utilisez est automatiquement détectée. Toutefois, le symbole monétaire est indiqué par erreur en tant que **$** pour les devises suivantes :

- GBP = Livre sterling du Royaume-Uni
- EUR = Euro européen
- INR = Roupie indienne
- NOK = Couronne norvégienne

Bien que le symbole monétaire affiche **$** pour le dollar américain, les valeurs de coût sont affichées dans votre devise. Par exemple, si tous vos comptes utilisent l’Euro dans la même entité, les _valeurs_ affichées dans Cloudyn sont en Euros, même si le symbole **$** s’affiche par erreur.

Si vous êtes un client Azure Enterprise Agreement, le service de support technique Cloudyn peut modifier le symbole monétaire affiché dans les rapports de coût pour utiliser un symbole autre que $. Vous pouvez créer une nouvelle demande de support dans le portail Azure. Sélectionnez **Aide + Support**, puis **Nouvelle demande de support**.

Si vous êtes un client CSP, vous ne pouvez pas modifier le symbole monétaire. Cloudyn prend uniquement en charge les cartes de tarifs qui utilisent le dollar américain. Cloudyn explore actuellement la possibilité de prendre en charge des cartes de tarifs dans d’autres devises.

## <a name="what-are-cloudyn-data-refresh-timelines"></a>Que sont les chronologies d’actualisation des données de Cloudyn ?

Cloudyn dispose des chronologies d’actualisation des données suivantes :

- **Initial (Initiale)** : l’affichage des données de coût dans Cloudyn après la configuration peut prendre jusqu’à 24 heures. Cloudyn peut également nécessiter jusqu’à 10 jours afin de collecter les données nécessaires pour afficher les recommandations de dimensionnement.
- **Daily (Quotidienne)** : à partir du dixième jour jusqu’à la fin de chaque mois, Cloudyn doit afficher vos données à jour depuis la veille jusqu’à environ UTC+3 le jour suivant.
- **Monthly (Mensuelle)** : du premier jour au dixième jour de chaque mois, Cloudyn peut n’afficher vos données que jusqu’à la fin du mois précédent.

Cloudyn traite les données du jour précédent lorsque des données complètes pour le jour précédent sont disponibles. Les données du jour précédent sont généralement disponibles dans Cloudyn avec un décalage UTC+3 chaque jour. Le traitement de certaines données, telles que les balises, peut prendre 24 heures supplémentaires.

Les données du mois en cours ne sont pas disponibles pour la collecte au début de chaque mois. Durant la période, les fournisseurs de services finalisent leur facturation pour le mois précédent. Les données du mois précédent s’affichent dans Cloudyn 5 à 10 jours après le début de chaque mois. Pendant ce temps, seuls les coûts amortis du mois précédent peuvent s’afficher. Les données de facturation ou d’utilisation quotidiennes peuvent ne pas s’afficher. Lorsque les données deviennent disponibles, Cloudyn les traite de façon rétroactive. Après le traitement, toutes les données mensuelles s’affichent entre le 5 et le 10 de chaque mois.

En cas de délai d’envoi des données à partir d’Azure vers Cloudyn, les données sont toujours enregistrées dans Azure. Les données sont transférées à Cloudyn lorsque la connexion est rétablie.

## <a name="how-can-a-direct-csp-configure-cloudyn-access-for-indirect-csp-customers-or-partners"></a>Comment un CSP direct peut-il configurer l’accès à Cloudyn pour les clients ou partenaires d’un CSP indirect ?

Pour obtenir des instructions, consultez [Configurer l’accès CSP indirect dans Cloudyn](quick-register-csp.md#configure-indirect-csp-access-in-cloudyn).
