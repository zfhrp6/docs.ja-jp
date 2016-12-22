---
title: "Nullable type inference is not supported in this context | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36629"
  - "bc36629"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36629"
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Nullable type inference is not supported in this context
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

値の型と構造を Null 許容として宣言することは可能です。  
  
```vb#  
Dim a? As Integer  
Dim b As Integer?  
```  
  
 ただし、Null 許容の宣言と型の推論を組み合わせて使用することはできません。  次の例はエラーになります。  
  
```vb#  
' Not valid.  
' Dim c? = 10  
' Dim d? = a  
```  
  
 **エラー ID:** BC36629  
  
### このエラーを解決するには  
  
-   `As` 句を使用して、変数を Null 許容として宣言します。  
  
## 参照  
 [Nullable Value Types](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)