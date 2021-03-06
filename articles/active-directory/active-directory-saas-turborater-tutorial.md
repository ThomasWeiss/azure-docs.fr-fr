---
title: "Didacticiel : Intégration d’Azure Active Directory avec TurboRater | Microsoft Docs"
description: "Découvrez comment configurer l’authentification unique entre Azure Active Directory et TurboRater."
services: active-directory
documentationCenter: na
author: jeevansd
manager: femila
ms.reviewer: joflore
ms.assetid: abb116b8-8024-4cc6-bc81-f32ef490ea17
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 10/03/2017
ms.author: jeedes
ms.openlocfilehash: 1d8f7b438858df1944a1fe11073e0f1dcdf954df
ms.sourcegitcommit: 6699c77dcbd5f8a1a2f21fba3d0a0005ac9ed6b7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2017
---
# <a name="tutorial-azure-active-directory-integration-with-turborater"></a>Didacticiel : Intégration d’Azure Active Directory à TurboRater

Dans ce didacticiel, vous allez découvrir comment intégrer TigerText à Azure Active Directory (Azure AD).

Cette intégration vous offre les avantages suivants :

- Dans Azure AD, vous pouvez contrôler qui a accès à TurboRater.
- Vous pouvez autoriser vos utilisateurs à se connecter automatiquement à TurboRater (via l’authentification unique) avec leur compte Azure AD.
- Vous pouvez gérer vos comptes dans un emplacement central : le portail Azure.

Pour en savoir plus sur l’intégration des applications SaaS avec Azure AD, consultez [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](active-directory-appssoaccess-whatis.md).

## <a name="prerequisites"></a>Composants requis

Pour configurer l’intégration d’Azure AD à TurboRater, vous avez besoin des éléments suivants :

- Un abonnement Azure AD
- Un abonnement à TurboRater, pour lequel l’authentification unique est activée

> [!NOTE]
> Pour tester les étapes de ce didacticiel, nous déconseillons l’utilisation d’un environnement de production.

Vous devez en outre suivre les recommandations ci-dessous :

- N’utilisez pas votre environnement de production, sauf si cela est nécessaire.
- Si vous n’avez pas d’environnement d’essai Azure AD, vous pouvez [obtenir un essai d’un mois](https://azure.microsoft.com/pricing/free-trial/).

## <a name="scenario-description"></a>Description du scénario
Dans ce didacticiel, vous testez l’authentification unique Azure AD dans un environnement de test. Le scénario décrit dans ce didacticiel se compose des deux sections principales suivantes :

1. Ajout de TurboRater depuis la galerie
2. Configuration et test de l’authentification unique Azure AD

## <a name="adding-turborater-from-the-gallery"></a>Ajout de TurboRater depuis la galerie
Pour configurer l’intégration de TurboRater dans Azure AD, vous devez ajouter TurboRater, disponible dans la galerie, à votre liste d’applications SaaS managées.

**Pour ajouter TurboRater à partir de la galerie, procédez comme suit :**

1. Dans le volet de navigation gauche du **[portail Azure](https://portal.azure.com)**, cliquez sur l’icône **Azure Active Directory**. 

    ![Bouton Azure Active Directory][1]

2. Accédez à **Applications d’entreprise**. Accédez ensuite à **Toutes les applications**.

    ![Panneau Applications d’entreprise][2]
    
3. Pour ajouter l’application, cliquez sur le bouton **Nouvelle application** en haut de la boîte de dialogue.

    ![Bouton Nouvelle application][3]

4. Dans la zone de recherche, saisissez **TurboRater**, sélectionnez **TurboRater** dans le volet de résultats, puis cliquez sur le bouton **Ajouter** pour ajouter l’application.

    ![TurboRater dans la liste des résultats](./media/active-directory-saas-turborater-tutorial/tutorial_turborater_addfromgallery.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>Configurer et tester l’authentification unique Azure AD

Dans cette section, vous allez configurer et tester l’authentification unique Azure AD avec TurboRater, en ayant recours à un utilisateur de test appelé « Britta Simon ».

Pour que l’authentification unique fonctionne, Azure AD doit savoir qui est l’utilisateur TurboRater équivalent dans Azure AD. En d’autres termes, une relation entre un utilisateur Azure AD et un utilisateur TurboRater associé doit être établie.

Dans TurboRater, affectez la valeur de **nom d’utilisateur** dans Azure AD en tant que valeur de **nom d’utilisateur** pour établir la relation.

Pour configurer et tester l’authentification unique Azure AD avec TurboRater, vous devez suivre les indications des sections suivantes :

1. **[Configurer l’authentification unique Azure AD](#configure-azure-ad-single-sign-on)** pour permettre à vos utilisateurs d’utiliser cette fonctionnalité.
2. **[Créer un utilisateur de test Azure AD](#create-an-azure-ad-test-user)** pour tester l’authentification unique Azure AD avec Britta Simon.
3. **[Créer utilisateur de test TurboRater](#create-a-turborater-test-user)** pour avoir un équivalent de Britta Simon dans TurboRater, lié à la représentation Azure AD associée.
4. **[Affecter l’utilisateur de test Azure AD](#assign-the-azure-ad-test-user)** pour permettre à Britta Simon d’utiliser l’authentification unique Azure AD.
5. **[Tester l’authentification unique](#test-single-sign-on)** : pour vérifier si la configuration fonctionne.

### <a name="configure-azure-ad-single-sign-on"></a>Configurer l’authentification unique Azure AD

Dans cette section, vous allez activer l’authentification unique Azure AD dans le portail Azure et configurer l’authentification unique dans votre application TurboRater.

**Pour configurer l’authentification unique Azure AD avec TurboRater, procédez comme suit :**

1. Dans le portail Azure, sur la page d’intégration de l’application **TurboRater**, cliquez sur **Authentification unique**.

    ![Lien Configurer l’authentification unique][4]

2. Dans la boîte de dialogue **Authentification unique**, pour le **Mode**, sélectionnez **Authentification basée sur SAML** pour activer l’authentification unique.
 
    ![Boîte de dialogue Authentification unique](./media/active-directory-saas-turborater-tutorial/tutorial_turborater_samlbase.png)

3. Dans la section relative aux **domaine et URL TurboRater**, procédez comme suit :

    ![Informations d’authentification unique des URL et du domaine TurboRater](./media/active-directory-saas-turborater-tutorial/tutorial_turborater_url.png)

    a. Dans la zone de texte **Identificateur**, entrez la valeur `https://www.itcdataservices.com`
 
    b. Dans la zone de texte **URL de réponse**, saisissez la valeur comme suit :
    
    | Environnement | URL |
    | ---------------| --------------- |    
    | Test  | `https://ratingqa.itcdataservices.com/webservices/imp/saml/login` |
    | En direct  | `https://www.itcratingservices.com/webservices/imp/saml/login` |

4. Dans la section **Certificat de signature SAML**, cliquez sur **Métadonnées XML** puis enregistrez le fichier de métadonnées sur votre ordinateur.

    ![Lien Téléchargement de certificat](./media/active-directory-saas-turborater-tutorial/tutorial_turborater_certificate.png) 

5. Cliquez sur le bouton **Enregistrer** .

    ![Bouton Enregistrer de la page Configurer l’authentification unique](./media/active-directory-saas-turborater-tutorial/tutorial_general_400.png)

7. Pour configurer l’authentification unique côté **TurboRater**, vous devez envoyer le fichier **XML de métadonnées** téléchargé à [l’équipe de support technique de TurboRater](https://www.getitc.com/support). Celles-ci configurent ensuite ce paramètre pour que la connexion SSO SAML soit définie correctement des deux côtés.

> [!TIP]
> Vous pouvez maintenant lire une version concise de ces instructions dans le [portail Azure](https://portal.azure.com), pendant que vous configurez l’application.  Après avoir ajouté cette application à partir de la section **Active Directory > Applications d’entreprise**, cliquez simplement sur l’onglet **Authentification unique** et accédez à la documentation incorporée par le biais de la section **Configuration** en bas. Vous pouvez en savoir plus sur la fonctionnalité de documentation incorporée ici : [Documentation incorporée Azure AD]( https://go.microsoft.com/fwlink/?linkid=845985)

### <a name="create-an-azure-ad-test-user"></a>Créer un utilisateur de test Azure AD

L’objectif de cette section est de créer un utilisateur de test appelé Britta Simon dans le portail Azure.

   ![Créer un utilisateur de test Azure AD][100]

**Pour créer un utilisateur de test dans Azure AD, procédez comme suit :**

1. Dans le volet gauche du Portail Azure, cliquez sur le bouton **Azure Active Directory**.

    ![Bouton Azure Active Directory](./media/active-directory-saas-turborater-tutorial/create_aaduser_01.png)

2. Pour afficher la liste des utilisateurs, accédez à **Utilisateurs et groupes**, puis cliquez sur **Tous les utilisateurs**.

    ![Liens « Utilisateurs et groupes » et « Tous les utilisateurs »](./media/active-directory-saas-turborater-tutorial/create_aaduser_02.png)

3. Pour ouvrir la boîte de dialogue **Utilisateur**, cliquez sur **Ajouter** en haut de la boîte de dialogue **Tous les utilisateurs**.

    ![Bouton Ajouter](./media/active-directory-saas-turborater-tutorial/create_aaduser_03.png)

4. Dans la boîte de dialogue **Utilisateur**, procédez comme suit :

    ![Boîte de dialogue Utilisateur](./media/active-directory-saas-turborater-tutorial/create_aaduser_04.png)

    a. Dans la zone **Nom**, tapez **BrittaSimon**.

    b. Dans la zone **Nom d’utilisateur** , tapez l’adresse e-mail de l’utilisateur Britta Simon.

    c. Cochez la case **Afficher le mot de passe**, puis notez la valeur affichée dans le champ **Mot de passe**.

    d. Cliquez sur **Créer**.
  
### <a name="create-a-turborater-test-user"></a>Créer un utilisateur de test TurboRater

Pour se connecter à TurboRater, les utilisateurs d’Azure AD doivent être approvisionnés dans TurboRater.  
Pour TurboRater, l’approvisionnement est une tâche manuelle.
Pour créer un utilisateur, collaborez avec [l’équipe de support TurboRater](https://www.getitc.com/support).

### <a name="assign-the-azure-ad-test-user"></a>Affecter l’utilisateur de test Azure AD

Dans cette section, vous allez autoriser Britta Simon à utiliser l’authentification unique Azure en lui accordant l’accès à TurboRater.

![Attribuer le rôle utilisateur][200] 

**Pour affecter Britta Simon à TurboRater, procédez comme suit :**

1. Dans le portail Azure, ouvrez la vue des applications, accédez à la vue des répertoires, accédez à **Applications d’entreprise**, puis cliquez sur **Toutes les applications**.

    ![Affecter des utilisateurs][201] 

2. Dans la liste des applications, sélectionnez **TurboRater**.

    ![Lien vers TurboRater dans la liste des applications](./media/active-directory-saas-turborater-tutorial/tutorial_turborater_app.png)  

3. Dans le menu de gauche, cliquez sur **Utilisateurs et groupes**.

    ![Lien « Utilisateurs et groupes »][202]

4. Cliquez sur le bouton **Ajouter**. Ensuite, sélectionnez **Utilisateurs et groupes** dans la boîte de dialogue **Ajouter une affectation**.

    ![Volet Ajouter une attribution][203]

5. Dans la boîte de dialogue **Utilisateurs et groupes**, sélectionnez **Britta Simon** dans la liste des utilisateurs.

6. Cliquez sur le bouton **Sélectionner** dans la boîte de dialogue **Utilisateurs et groupes**.

7. Cliquez sur le bouton **Affecter** dans la boîte de dialogue **Ajouter une affectation**.
    
### <a name="test-single-sign-on"></a>Tester l’authentification unique

Dans cette section, vous allez tester la configuration de l’authentification unique Azure AD à l’aide du volet d’accès.

Lorsque vous cliquez sur la mosaïque TurboRater dans le volet d’accès, vous devez être connecté automatiquement à votre application TurboRater.
Pour plus d’informations sur le panneau d’accès, consultez [Présentation du panneau d’accès](active-directory-saas-access-panel-introduction.md). 

## <a name="additional-resources"></a>Ressources supplémentaires

* [Liste de didacticiels sur l’intégration d’applications SaaS avec Azure Active Directory](active-directory-saas-tutorial-list.md)
* [Qu’est-ce que l’accès aux applications et l’authentification unique avec Azure Active Directory ?](active-directory-appssoaccess-whatis.md)



<!--Image references-->

[1]: ./media/active-directory-saas-turborater-tutorial/tutorial_general_01.png
[2]: ./media/active-directory-saas-turborater-tutorial/tutorial_general_02.png
[3]: ./media/active-directory-saas-turborater-tutorial/tutorial_general_03.png
[4]: ./media/active-directory-saas-turborater-tutorial/tutorial_general_04.png

[100]: ./media/active-directory-saas-turborater-tutorial/tutorial_general_100.png

[200]: ./media/active-directory-saas-turborater-tutorial/tutorial_general_200.png
[201]: ./media/active-directory-saas-turborater-tutorial/tutorial_general_201.png
[202]: ./media/active-directory-saas-turborater-tutorial/tutorial_general_202.png
[203]: ./media/active-directory-saas-turborater-tutorial/tutorial_general_203.png

