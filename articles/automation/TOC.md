# Vue d'ensemble
## [Qu'est-ce qu'Azure Automation ?](automation-intro.md)
# Prise en main
## [Prise en main d’Azure Automation](automation-offering-get-started.md)
## Didacticiel de runbook
### [Créer un runbook graphique](automation-first-runbook-graphical.md)
### [Mon premier Runbook PowerShell](automation-first-runbook-textual-powershell.md)
### [Mon premier runbook Python](automation-first-runbook-textual-python2.md)
### [Mon premier runbook PowerShell Workflow](automation-first-runbook-textual.md)
# Procédures
## Authentification et sécurité
### [Créer un compte Automation autonome](automation-create-standalone-account.md)
### [Créer un compte d’utilisateur Azure AD](automation-create-aduser-account.md)
### [Configurer l’authentification avec AWS](automation-config-aws-account.md)
### [Créer un compte d’identification Automation](automation-create-runas-account.md)
### [Valider la configuration du compte Automation](automation-verify-runas-authentication.md)
### [Contrôle d’accès en fonction du rôle Azure](automation-role-based-access-control.md)
### [Gérer le compte Automation](automation-manage-account.md)
## Création de runbooks
### [Types de runbook](automation-runbook-types.md)
### [Créer et importer des runbooks](automation-creating-importing-runbook.md)
### [Modifier des runbooks textuels](automation-edit-textual-runbook.md)
### [Modifier des runbooks graphiques](automation-graphical-authoring-intro.md)
### [Tester un runbook](automation-testing-runbook.md)
### [Apprentissage du workflow PowerShell](automation-powershell-workflow.md)
### [Runbooks enfants](automation-child-runbooks.md)
### [Sortie de Runbook](automation-runbook-output-and-messages.md)
### [Intégration du contrôle de code source](automation-source-control-integration.md)
## Automatisation
### [Démarrer un runbook](automation-starting-a-runbook.md)
### [Démarrer un runbook depuis un webhook](automation-webhooks.md)
### [Paramètres d'entrée de Runbook](automation-runbook-input-parameters.md)
### [Gestion des erreurs dans les runbooks graphiques](automation-runbook-graphical-error-handling.md)
### [Suivre une tâche de Runbook](automation-runbook-execution.md)
### [Paramètres du Runbook](automation-runbook-settings.md)
### [Gestion des données Azure Automation](automation-managing-data.md)
### [Appeler un runbook Azure Automation à partir d’une alerte Log Analytics](automation-invoke-runbook-from-omsla-alert.md)
### [Valider un objet JSON dans un runbook Azure Automation](automation-pass-json-string.md)
## Runbook Worker hybride
### [Déployer Runbook Worker hybride](automation-hybrid-runbook-worker.md)
### [Runbook Worker hybride Windows Azure Automation](automation-windows-hrw-install.md)
### [Runbook Worker hybride Linux Azure Automation](automation-linux-hrw-install.md)
### [Exécuter des runbooks sur Worker](automation-hrw-run-runbooks.md)
### [Supprimer des runbooks Workers hybrides Azure Automation](automation-remove-hrw.md)
## Gestion des configurations (configuration d’état souhaité)
### [Présentation de la configuration de l’état souhaité](automation-dsc-overview.md)
### [Prise en main](automation-dsc-getting-started.md)
### [Configurer des serveurs à l’état souhaité et gérer la dérive avec Azure Automation](tutorial-configure-servers-desired-state.md)
### [Intégration des machines pour la gestion](automation-dsc-onboarding.md)
### [Compilation de configurations d’état souhaité](automation-dsc-compile.md)
### [Déploiement continu avec Chocolatey](automation-dsc-cd-chocolatey.md)
### [Transférer des données de rapport Azure Automation DSC à OMS Log Analytics](automation-dsc-diagnostics.md)
## Gérer les ressources
### [Certificats](automation-certificates.md)
### [Connexions](automation-connections.md)
### [Informations d'identification](automation-credentials.md)
### [Modules d’intégration](automation-integration-modules.md)
### [Planifications](automation-schedules.md)
### [Variables](automation-variables.md)
### [Mettre à jour les modules Azure PowerShell](automation-update-azure-modules.md)
## Scénarios
### [Galerie de runbooks](automation-runbook-gallery.md)
### [Créer une machine virtuelle Amazon Web Service](automation-scenario-aws-deployment.md)
### [Résoudre une alerte de machine virtuelle Azure](automation-azure-vm-alert-integration.md)
### [Démarrer/arrêter une machine virtuelle avec des balises JSON](automation-scenario-start-stop-vm-wjson-tags.md)
### [Supprimer le groupe de ressources](automation-scenario-remove-resourcegroup.md)
### [Intégration du contrôle de code source avec GitHub Enterprise](automation-scenario-source-control-integration-with-github-ent.md)
### [Intégration du contrôle de code source avec VSTS](automation-scenario-source-control-integration-with-VSTS.md)
### [Appeler un runbook Azure Automation à partir d’une alerte Log Analytics](automation-invoke-runbook-from-omsla-alert.md)
### [Déployer un modèle Azure Resource Manager dans un runbook PowerShell Azure Automation](automation-deploy-template-runbook.md)
## Solutions
### [Gestion des mises à jour](../operations-management-suite/oms-solution-update-management.md)
#### [Gérer les mises à jour pour plusieurs machines virtuelles](manage-update-multi.md)
#### [Intégrer SCCM avec OMS Update Management](oms-solution-updatemgmt-sccmintegration.md)
### [Suivi des modifications](../log-analytics/log-analytics-change-tracking.md)
### [Suivi des modifications dans vos machines virtuelles](automation-vm-change-tracking.md)
### [Gérer une machine virtuelle avec la collecte d’inventaire](automation-vm-inventory.md)
### [Démarrer/arrêter des machines virtuelles pendant les heures creuses](automation-solution-vm-management.md)
## Surveiller
### [Transférer des données de travaux Azure Automation à Log Analytics](automation-manage-send-joblogs-log-analytics.md)
### [Supprimer le lien d’un compte Azure Automation à partir de Log Analytics](automation-unlink-from-log-analytics.md)
## Migrer
### [Migrer à partir d’Orchestrator](automation-orchestrator-migration.md)
### [Déplacer le compte Automation](automation-migrate-account-subscription.md)
## Résolution des problèmes
### [Résoudre les problèmes courants](automation-troubleshooting-automation-errors.md)
### [Dépanner la fonctionnalité Runbook Worker hybride](automation-troubleshooting-hybrid-runbook-worker.md)
# Référence
## [Azure PowerShell](/powershell/module/azurerm.automation)
## [Azure PowerShell (classic)](/powershell/module/azure/?view=azuresmps-3.7.0)
## [.NET](/dotnet/api/microsoft.azure.management.automation)
## [REST](/rest/api/automation)
## [REST (classique)](https://msdn.microsoft.com/library/azure/mt163781)
# Ressources
## [Vidéo de présentation d’Automation](https://azure.microsoft.com/documentation/videos/azure-automation-101-with-powershell-and-eamon-o-reilly/)
## [Formation Azure Automation](https://mva.microsoft.com/en-US/training-courses/automating-the-cloud-with-azure-automation-8323?l=C6mIpCay_4804984382)
## [Feuille de route Azure](https://azure.microsoft.com/roadmap/?category=monitoring-management)
## [Parcours d’apprentissage](https://azure.microsoft.com/documentation/learning-paths/automation/)
## [Forum MSDN](https://social.msdn.microsoft.com/Forums/azure/en-US/home?forum=azureautomation)  
## [Tarification](https://azure.microsoft.com/pricing/details/automation/)  
## [Calculatrice de prix](https://azure.microsoft.com/pricing/calculator/)
## [Notes de publication](https://azure.microsoft.com/updates/?product=automation)
## [Mises à jour de service](https://azure.microsoft.com/updates/?product=automation)
## [Stack Overflow](http://stackoverflow.com/questions/tagged/azure-automation)
## [Vidéos](https://azure.microsoft.com/documentation/videos/index/?services=automation)
