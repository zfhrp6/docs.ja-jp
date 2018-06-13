---
title: 範囲変数&lt;変数&gt;外側のブロックを以前に定義された範囲変数、またはクエリ式内で暗黙的に宣言された変数内の変数を非表示になります
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: f02533cf7cb79c34e5bb5a6d445aaef7ab0e86da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593127"
---
# <a name="range-variable-ltvariablegt-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a>範囲変数&lt;変数&gt;外側のブロックを以前に定義された範囲変数、またはクエリ式内で暗黙的に宣言された変数内の変数を非表示になります
指定された範囲変数の名前、 `Select`、 `From`、 `Aggregate`、または`Let`句が既に指定されている、クエリまたはクエリで暗黙的に宣言されている変数の名前で、範囲変数の名前に重複などのフィールド名または集計関数の名前。  
  
 **エラー ID:** BC36633  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   特定のクエリ スコープ内のすべての範囲変数に一意の名前があることを確認します。 クエリは、入れ子になったクエリは、一意のスコープであることを確認するかっこで囲むことができます。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [From 句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Let 句](../../../visual-basic/language-reference/queries/let-clause.md)  
 [Aggregate 句](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
