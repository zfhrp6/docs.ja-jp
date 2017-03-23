---
title: "Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30424"
  - "bc30424"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30424"
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

定数を、クラス、構造体、配列型として、またはジェネリック型を用いて定義される型パラメーターとして宣言しようとしました。  
  
 定数は、組み込み型 \(`Boolean`、`Byte`、`Date`、`Decimal`、`Double`、`Integer`、`Long`、`Object`、`SByte`、`Short`、`Single`、`String`、`UInteger`、`ULong`、または `UShort`\) か整数型の 1 つを基にした `Enum` 型である必要があります。  
  
 **Error ID:** BC30424  
  
### このエラーを解決するには  
  
1.  定数を組み込み型または `Enum` 型として宣言します。  
  
2.  `True`、`False`、`Nothing` など特定の値を定数にすることもできます。  コンパイラは、これら定義済みの値を、適切な組み込み型として解釈します。  
  
## 参照  
 [Constants and Enumerations](../../../visual-basic/language-reference/constants-and-enumerations.md)   
 [データ型](../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)