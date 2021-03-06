---
title: "Azure Active Directory B2C : réinitialisation de mot de passe libre-service | Microsoft Docs"
description: "Rubrique montrant comment configurer une réinitialisation de mot de passe libre-service pour vos consommateurs dans Azure Active Directory B2C"
services: active-directory-b2c
documentationcenter: 
author: swkrish
manager: mbaldwin
editor: curtand
ms.assetid: c87ed86e-1520-42b1-8c31-46cd44ed5310
ms.service: active-directory-b2c
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 12/06/2016
ms.author: swkrish
ms.openlocfilehash: beaf7dc6260db7509b2202c7801bcc0d2dd2c69e
ms.sourcegitcommit: 732e5df390dea94c363fc99b9d781e64cb75e220
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2017
---
# <a name="azure-active-directory-b2c-set-up-self-service-password-reset-for-your-consumers"></a>Azure Active Directory B2C : configuration de la réinitialisation du mot de passe libre-service pour vos consommateurs
La fonctionnalité de réinitialisation du mot de passe en libre-service permet à vos consommateurs (qui ont souscrit des comptes locaux) de réinitialiser eux-mêmes leurs mots de passe. Cela réduit considérablement la charge pesant sur votre personnel de support, surtout si votre application est utilisée régulièrement par des millions de consommateurs. Actuellement, nous prenons uniquement en charge l’utilisation d’une adresse électronique vérifiée comme méthode de récupération. Nous allons ajouter des méthodes de récupération supplémentaires (numéro de téléphone vérifié, questions de sécurité, etc.) à l’avenir.

> [!NOTE]
> Cet article s’applique à un mot de passe libre-service utilisé dans le contexte d’une stratégie de connexion. Si vous avez besoin de stratégies de réinitialisation de mot de passe entièrement personnalisables appelées à partir de votre application, consultez [cet article](active-directory-b2c-reference-policies.md#create-a-password-reset-policy).
> 
> 

Par défaut, la réinitialisation de mot de passe libre-service ne sera pas activée pour votre annuaire. Pour l’activer, procédez comme suit :

1. Connectez-vous au [portail Azure Classic](https://manage.windowsazure.com/) en tant qu’administrateur d’abonnements. Il s’agit du compte professionnel ou scolaire, ou du compte Microsoft que vous avez utilisé pour créer votre annuaire.
2. Accédez à l’extension Active Directory dans la barre de navigation sur le côté gauche.
3. Recherchez votre répertoire sous l’onglet **Répertoire** , puis cliquez dessus.
4. Cliquez sur l'onglet **Configurer** .
5. Faites défiler jusqu’à la section **Stratégie de réinitialisation du mot de passe utilisateur**, puis définissez l’option **Utilisateurs autorisés à réinitialiser leur mot de passe** sur **OUI**. Notez que l’option **Autre adresse de messagerie** est activée ; laissez-la telle quelle.
   
    ![Réinitialisation de mot de passe libre-service](./media/active-directory-b2c-reference-sspr/sspr.png)
6. Cliquez sur **Enregistrer** au bas de la page. Vous avez terminé !

Pour tester, utilisez la fonctionnalité « Exécuter maintenant » sur une stratégie de connexion (qui comporte des comptes locaux en tant que fournisseur d’identité). Sur la page de connexion au compte local (où vous entrez une adresse e-mail et un mot de passe, ou un nom d’utilisateur et un mot de passe), cliquez sur **Votre compte n’est pas accessible ?** pour vérifier l’expérience du consommateur.

> [!NOTE]
> Les pages de réinitialisation de mot de passe libre-service sont personnalisables à l’aide de la [fonctionnalité de personnalisation de la société](../active-directory/customize-branding.md).
> 
> 

