---
title: "Personnalisation : réinitialisation de mot de passe en libre-service d’Azure AD | Microsoft Docs"
description: "Options de personnalisation pour la réinitialisation de mot de passe libre-service Azure AD"
services: active-directory
keywords: 
documentationcenter: 
author: MicrosoftGuyJFlo
manager: femila
ms.reviewer: sahenry
ms.assetid: 
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 10/24/2017
ms.author: joflore
ms.custom: it-pro
ms.openlocfilehash: f2b172208185e343c9c10d55036c20d60346778c
ms.sourcegitcommit: 732e5df390dea94c363fc99b9d781e64cb75e220
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2017
---
# <a name="customize-azure-ad-functionality-for-self-service-password-reset"></a>Personnaliser les fonctionnalités d’Azure AD pour la réinitialisation de mot en passe libre-service

Les professionnels de l’informatique qui souhaitent déployer la réinitialisation de mot de passe libre-service peuvent personnaliser l’expérience en fonction de leurs utilisateurs.

## <a name="customize-the-contact-your-administrator-link"></a>Personnaliser le lien « Contactez votre administrateur »

Même si la réinitialisation n’est pas activée, les utilisateurs peuvent toujours voir un lien « contactez votre administrateur » portail de réinitialisation de mot de passe.  Cliquer sur ce lien envoie un e-mail à vos administrateurs pour demander une assistance durant la modification du mot de passe de l’utilisateur ou dirige vos utilisateurs vers une URL que vous spécifiez. Nous vous recommandons de le définir sur une valeur telle qu’une adresse de messagerie ou un site Web que vos utilisateurs ont l’habitude de visiter pour demander de l’assistance.

![Contact][Contact]

Ce message électronique est envoyé aux destinataires suivants dans cet ordre :

1. Si le rôle **Administrateur de mot de passe** est affecté, les administrateurs détenteurs de ce rôle sont avertis
2. Si aucun administrateur de mot de passe n’est affecté, les administrateurs disposant du rôle **Administrateur d’utilisateurs** sont avertis
3. Si aucun des rôles précédents n’a été affecté, les **Administrateurs globaux** sont avertis

Dans tous les cas, un maximum de 100 destinataires sont informés.

Pour en savoir plus sur les différents rôles d’administrateur et sur la façon de les affecter, consultez le document [Attribution de rôles d’administrateur dans Azure Active Directory](active-directory-assign-admin-roles-azure-portal.md).

### <a name="disable-contact-your-administrator-emails"></a>Désactiver les e-mails Contactez votre administrateur

Si votre organisation ne souhaite pas avertir les administrateurs au sujet des demandes de réinitialisation de mot de passe, la configuration suivante peut être activée.

* Activez la réinitialisation du mot de passe en libre-service pour tous les utilisateurs finaux. Cette option se trouve sous **Réinitialisation de mot de passe > Propriétés**.
    * Si vous ne voulez pas que les utilisateurs réinitialisent leurs propres mots de passe, vous pouvez étendre l’accès à un groupe vide, mais **nous ne recommandons pas cette option**.
* Personnalisez le lien du support technique pour fournir une URL web ou un lien mailto: que les utilisateurs peuvent utiliser pour obtenir une assistance. Cette option se trouve sous **Réinitialisation de mot de passe > Personnalisation > Adresse e-mail ou URL du support technique**.

## <a name="customize-adfs-sign-in-page-for-sspr"></a>Personnaliser la page de connexion AD FS pour SSPR

Les administrateurs des services AD FS peut ajouter un lien à leur page de connexion à l’aide des instructions figurant dans l’article [Ajouter la description de la page de connexion](https://docs.microsoft.com/windows-server/identity/ad-fs/operations/add-sign-in-page-description).

L’exécution de la commande suivante sur votre serveur AD FS ajoute un lien vers la page de connexion AD FS permettant aux utilisateurs d’accéder directement au flux de travail de réinitialisation de mot de passe libre-service.

``` Set-ADFSGlobalWebContent -SigninPageDescriptionText "<p><A href=’https://passwordreset.microsoftonline.com’>Can’t access your account?</A></p>" ```

## <a name="customize-the-sign-in-and-access-panel-look-and-feel"></a>Personnaliser l’apparence du panneau d’accès et de connexion

Lorsque vos utilisateurs accèdent à la page de connexion, vous pouvez personnaliser le logo qui s’affiche, ainsi que l’image de la page de connexion en fonction de l’identité de votre société.

Ces graphiques s’affichent dans les circonstances suivantes :

* Lorsqu’un utilisateur saisit son nom d’utilisateur
* Lorsque l’utilisateur accède à une URL personnalisée
    * Lors de la transmission du paramètre « whr » à la page de réinitialisation de mot de passe, par exemple « https://login.microsoftonline.com/?whr=contoso.com »
    * Lors de la transmission du paramètre « username » à la page de réinitialisation de mot de passe, par exemple « https://login.microsoftonline.com/?username=admin@contoso.com »

### <a name="graphics-details"></a>Détails des éléments visuels

Les paramètres suivants vous permettent de modifier les caractéristiques visuelles de la page de connexion et se trouvent sous **Azure Active Directory**, **Personnalisation de la société**, **Modifier la personnalisation de la société**

* L’image de la page de connexion doit être un fichier PNG ou JPG de 1420 x 1200 pixels et ne dépassant pas 500 ko. Nous recommandons une taille d’environ 200 ko pour de meilleurs résultats.
* La couleur d’arrière-plan de la page de connexion est utilisée sur des connexions à latence élevée et doit être au format hexadécimal RVB.
* L’image de la bannière doit être un fichier PNG ou JPG de 60 x 280 pixels ne dépassant pas 10 Ko.
* Le logo carré (thème normal et foncé) doit être un fichier PNG ou JPG de 240 x 240 (redimensionnable) ne dépassant pas 10 Ko.

### <a name="sign-in-text-options"></a>Options de texte de connexion

Les paramètres suivants permettent d’ajouter du texte à la page de connexion propre à votre organisation. Ces paramètres se trouvent sous **Azure Active Directory**, **Personnalisation de la société**, **Modifier la personnalisation de la société**

* **Indice de nom d’utilisateur** remplace le texte d’exemple de someone@example.com avec un nom plus approprié pour vos utilisateurs, il est recommandé de laisser la valeur par défaut lors de la prise en charge d’utilisateurs internes et externes
* Le **Texte de la page de connexion** fait un maximum de 256 caractères. Ce texte apparaît partout où vos utilisateurs se connectent, et dans l’interface Azure AD Join sur Windows 10. Utilisez ce texte pour les conditions d’utilisation, les instructions et conseils pour vos utilisateurs. **N’importe qui peut voir votre page de connexion, aussi ne fournissez pas d’informations sensibles ici.**

### <a name="keep-me-signed-in-disabled"></a>Désactiver le maintien de la connexion

L’option « Désactiver le maintien de la connexion » permet aux utilisateurs de rester connectés quand ils ferment et rouvrent la fenêtre du navigateur. Cette option n’affecte pas la durée de vie de session. Ce paramètre se trouve sous **Azure Active Directory > Personnalisation de la société > Modifier la personnalisation de la société**.

Certaines fonctionnalités de SharePoint Online et Office 2010 dépendent de la capacité des utilisateurs à sélectionner cette case à cocher. Si vous masquez cette option, les utilisateurs peuvent obtenir des invites de connexion supplémentaires et inattendues.

### <a name="directory-name"></a>Nom de l’annuaire

Vous pouvez modifier l’attribut de nom sous **Azure Active Directory > Propriétés** pour indiquer un nom d’organisation convivial dans les communications automatisées et sur le portail. Cette option est essentiellement visible sous la forme d’e-mails automatiques dans les formes qui suivent

* Nom convivial dans l’e-mail « Microsoft pour le compte de la démonstration CONTOSO »
* Ligne d’objet dans l’e-mail « Code de vérification d’e-mail pour le compte de démonstration CONTOSO »

## <a name="next-steps"></a>Étapes suivantes

* [Comment réussir le lancement de la réinitialisation de mot de passe en libre-service ?](active-directory-passwords-best-practices.md)
* [Réinitialisez ou modifiez votre mot de passe](active-directory-passwords-update-your-own-password.md).
* [Inscrivez-vous pour la réinitialisation du mot de passe en libre-service](active-directory-passwords-reset-register.md).
* [Vous avez une question relative à la licence ?](active-directory-passwords-licensing.md)
* [Quelles données sont utilisées par la réinitialisation de mot de passe en libre-service et quelles données vous devez renseigner pour vos utilisateurs ?](active-directory-passwords-data.md)
* [Quelles méthodes d'authentification sont accessibles aux utilisateurs ?](active-directory-passwords-how-it-works.md#authentication-methods)
* [Quelles sont les options de stratégie disponibles avec la réinitialisation de mot de passe en libre-service ?](active-directory-passwords-policy.md)
* [Quelle est l’écriture différée de mot de passe et pourquoi dois-je m’y intéresser ?](active-directory-passwords-writeback.md)
* [Comment puis-je générer des rapports sur l’activité dans la réinitialisation de mot de passe en libre-service ?](active-directory-passwords-reporting.md)
* [Quelles sont toutes les options disponibles dans la réinitialisation de mot de passe en libre-service et que signifient-elles ?](active-directory-passwords-how-it-works.md)
* [Je pense qu’il y a une panne quelque part. Comment puis-je résoudre les problèmes de la réinitialisation de mot de passe en libre-service ?](active-directory-passwords-troubleshoot.md)
* [J’ai une question à laquelle je n’ai pas trouvé de réponse ailleurs](active-directory-passwords-faq.md)

[Contact]: ./media/active-directory-passwords-customize/sspr-contact-admin.png "Si nécessaire, contactez votre administrateur pour réinitialiser votre exemple d’e-mail de mot le passe"