---
title: "数値演算子および比較演算子"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25b4a26a-06f2-4f80-87a9-76705ed46197
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f77cb612468b401f6aa526e46cc7481d0b47d385
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="numeric-and-comparison-operators"></a>数値演算子および比較演算子
算術演算子と比較演算子は、次の点を除いて、共通言語ランタイム (CLR) では期待どおりに動作します。  
  
-   SQL では、浮動小数点数に対して剰余演算子がサポートされません。  
  
-   SQL ではチェックされない算術はサポートされません。  
  
-   インクリメント演算子とデクリメント演算子は、SQL に複製できない式で使用すると副作用があるため、SQL ではサポートされません。  
  
## <a name="supported-operators"></a>サポートされる演算子  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] は、次の演算子をサポートしています。  
  
-   基本算術演算子  
  
    -   `+`  
  
    -   `-` (減算)  
  
    -   `*`  
  
    -   `/`  
  
    -   Visual Basic 整数除算 (`\`)  
  
    -   `%` (Visual Basic `Mod`)  
  
    -   `<<`  
  
    -   `>>`  
  
    -   `-` (単項マイナス符号)  
  
-   基本比較演算子  
  
    -   Visual Basic `=` および C# `==`  
  
    -   Visual Basic `<>` および C# `!=`  
  
    -   Visual Basic `Is/IsNot`  
  
    -   `<`  
  
    -   `<=`  
  
    -   `>`  
  
    -   `>=`  
  
## <a name="see-also"></a>関連項目  
 [データ型および関数](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)  
 [C# 演算子](http://msdn.microsoft.com/library/0301e31f-22ad-49af-ac3c-d5eae7f0ac43)  
 [演算子](../../../../../visual-basic/language-reference/operators/index.md)
