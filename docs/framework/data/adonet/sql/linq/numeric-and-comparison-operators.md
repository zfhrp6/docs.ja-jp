---
title: "Numeric and Comparison Operators | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Numeric and Comparison Operators
算術演算子と比較演算子は、次の点を除いて、共通言語ランタイム \(CLR\) では期待どおりに動作します。  
  
-   SQL では、浮動小数点数に対して剰余演算子がサポートされません。  
  
-   SQL ではチェックされない算術はサポートされません。  
  
-   インクリメント演算子とデクリメント演算子は、SQL に複製できない式で使用すると副作用があるため、SQL ではサポートされません。  
  
## サポートされる演算子  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、次の演算子をサポートしています。  
  
-   基本算術演算子  
  
    -   `+`  
  
    -   `-` \(減算\)  
  
    -   `*`  
  
    -   `/`  
  
    -   Visual Basic 整数除算 \(`\`\)  
  
    -   `%` \(Visual Basic `Mod`\)  
  
    -   `<<`  
  
    -   `>>`  
  
    -   `-` \(単項マイナス符号\)  
  
-   基本比較演算子  
  
    -   Visual Basic `=` および C\# `==`  
  
    -   Visual Basic `<>` および C\# `!=`  
  
    -   Visual Basic `Is/IsNot`  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## 参照  
 [Data Types and Functions](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)   
 [C\# 演算子](../Topic/C%23%20Operators.md)   
 [Operators](../Topic/Operators%20\(Visual%20Basic\).md)