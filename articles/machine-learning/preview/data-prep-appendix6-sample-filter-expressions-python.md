---
title: "Exemples d’expressions de filtre possibles avec la préparation des données Azure Machine Learning | Microsoft Docs"
description: "Ce document fournit un ensemble d’exemples d’expressions de filtre possibles avec la préparation des données Azure Machine Learning."
services: machine-learning
author: euangMS
ms.author: euang
manager: lanceo
ms.reviewer: 
ms.service: machine-learning
ms.workload: data-services
ms.custom: 
ms.devlang: 
ms.topic: article
ms.date: 09/11/2017
ms.openlocfilehash: f8b18b2a94885a76df4026a29400f4d651cbcad4
ms.sourcegitcommit: e5355615d11d69fc8d3101ca97067b3ebb3a45ef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="sample-of-filter-expressions-python"></a>Exemple d’expressions de filtre (Python) 
Avant de lire cette annexe, lisez la [présentation de l’extensibilité de Python](data-prep-python-extensibility-overview.md).

## <a name="filter-with-equivalence-test"></a>Filtrer avec un test d’équivalence
Filtrer uniquement les lignes dont la valeur (numérique) de Col2 est supérieure à 4. 

```python
    row["Col2"] > 4
```

## <a name="filter-with-multiple-columns"></a>Filtrer avec plusieurs colonnes 
Filtrer uniquement les lignes où Col1 contient la valeur **Good** et Col2 contient la valeur (numérique) 1. 
```python
    row["Col1"] == 'Good' and row["Col2"] == 1
```

## <a name="test-filter-against-null"></a>Tester le filtre par rapport à null
Filtrer uniquement les lignes où Col1 a la valeur null. 
```python
    pd.isnull(row["Col1"])
```
