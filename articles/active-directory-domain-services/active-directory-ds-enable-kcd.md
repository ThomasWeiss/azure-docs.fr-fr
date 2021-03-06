---
title: "Azure Active Directory Domain Services : Activer la délégation Kerberos contrainte | Microsoft Docs"
description: "Activer la délégation Kerberos contrainte sur les domaines gérés par les services de domaine Azure Active Directory"
services: active-directory-ds
documentationcenter: 
author: mahesh-unnikrishnan
manager: stevenpo
editor: curtand
ms.assetid: 938a5fbc-2dd1-4759-bcce-628a6e19ab9d
ms.service: active-directory-ds
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 03/06/2017
ms.author: maheshu
ms.openlocfilehash: f36f16a7bb00ace9fd5164eb38ba77f015f22f5c
ms.sourcegitcommit: 6699c77dcbd5f8a1a2f21fba3d0a0005ac9ed6b7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2017
---
# <a name="configure-kerberos-constrained-delegation-kcd-on-a-managed-domain"></a>Configurer la délégation Kerberos contrainte (KCD) sur un domaine géré
De nombreuses applications doivent accéder à des ressources dans le contexte de l’utilisateur. Active Directory prend en charge un mécanisme, appelé délégation Kerberos, qui rend possible ce cas d’utilisation. En outre, vous pouvez limiter la délégation afin que seules des ressources spécifiques soient accessibles dans le contexte de l’utilisateur. Les domaines gérés des services de domaine Azure AD diffèrent des domaines Active Directory traditionnels dans la mesure où ils sont verrouillés de façon mieux sécurisée.

Cet article vous montre comment configurer la délégation Kerberos contrainte sur un domaine géré de services de domaine Azure AD.

## <a name="kerberos-constrained-delegation-kcd"></a>Délégation Kerberos contrainte (KCD)
La délégation Kerberos contrainte permet à un compte d’emprunter l’identité d’un autre principal de sécurité (par exemple, un utilisateur) pour accéder aux ressources. Imaginez une application web qui accède à une API web principale dans le contexte d’un utilisateur. Dans cet exemple, l’application web (en cours d’exécution dans le contexte d’un compte de service ou d’un compte d’ordinateur) emprunte l’identité de l’utilisateur pour accéder à la ressource (API web principale). La délégation Kerberos n’est pas sécurisée, car elle ne limite pas les ressources auxquelles le compte d’emprunt peut accéder dans le contexte de l’utilisateur.

La délégation Kerberos contrainte (KCD) restreint les services/ressources sur lesquels le serveur spécifié peut agir pour le compte d’un utilisateur. La KCD traditionnelle requiert des privilèges d’administrateur de domaine pour configurer un compte de domaine pour un service, et elle restreint le compte à un seul domaine.

La KCD traditionnelle a également quelques problèmes qui lui sont associés. Dans les systèmes d’exploitation précédents sur lesquels l’administrateur de domaine a configuré le service, l’administrateur de service ne possédait aucun moyen de connaître les services frontaux qui déléguaient vers des services de ressources qu’ils détenaient. Et tout service frontal qui pouvait déléguer à un service de ressources représentait un point d’attaque potentiel. Si un serveur hébergeant un service frontal était compromis, et qu’il était configuré pour déléguer aux services de ressources, les services de ressources pouvaient également être compromis.

> [!NOTE]
> Sur un domaine géré des services de domaine Azure AD, vous n’avez pas les privilèges d’administrateur de domaine. Par conséquent, **la KCD traditionnelle ne peut pas être configurée sur un domaine géré**. Utilisez plutôt la KCD basée sur la ressource, comme décrit dans cet article. Ce mécanisme est également plus sécurisé.
>
>

## <a name="resource-based-kerberos-constrained-delegation"></a>Délégation Kerberos contrainte basée sur les ressources
Dans Windows Server 2012 R2 et Windows Server 2012, la possibilité de configurer la délégation contrainte pour le service a été transférée de l’administrateur de domaine à l’administrateur de service. De cette façon, l’administrateur de service principal peut autoriser ou refuser les services frontaux. Ce modèle est appelé **délégation Kerberos contrainte basée sur la ressource**.

La KCD basée sur la ressource est configurée à l’aide de PowerShell. Vous utilisez les applets de commande Set-ADComputer ou Set-ADUser, selon que le compte d’emprunt est un compte d’ordinateur ou un compte de service/compte utilisateur.

### <a name="configure-resource-based-kcd-for-a-computer-account-on-a-managed-domain"></a>Configuration d’une KCD basée sur la ressource pour un compte d’ordinateur sur un domaine géré
Supposons que vous ayez une application web en cours d’exécution sur l’ordinateur « contoso100-webapp.contoso100.com ». Elle doit accéder à la ressource (une API web s’exécutant sur « contoso100-api.contoso100.com ») dans le contexte des utilisateurs du domaine. Voici comment configurer une KCD basée sur les ressources pour ce scénario.

```
$ImpersonatingAccount = Get-ADComputer -Identity contoso100-webapp.contoso100.com
Set-ADComputer contoso100-api.contoso100.com -PrincipalsAllowedToDelegateToAccount $ImpersonatingAccount
```

### <a name="configure-resource-based-kcd-for-a-user-account-on-a-managed-domain"></a>Configuration d’une KCD basée sur la ressource pour un compte utilisateur sur un domaine géré
Supposons que vous ayez une application web en cours d’exécution en tant que compte de service « appsvc » et qu’elle doit accéder à la ressource (une API web en cours d’exécution en tant que compte de service - 'backendsvc') dans le contexte des utilisateurs du domaine. Voici comment configurer une KCD basée sur les ressources pour ce scénario.

```
$ImpersonatingAccount = Get-ADUser -Identity appsvc
Set-ADUser backendsvc -PrincipalsAllowedToDelegateToAccount $ImpersonatingAccount
```

## <a name="related-content"></a>Contenu connexe
* [Services de domaine Azure AD : guide de prise en main](active-directory-ds-getting-started.md)
* [Présentation de la délégation Kerberos contrainte](https://technet.microsoft.com/library/jj553400.aspx)
