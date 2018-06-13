---
title: Let 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 6484da5329c8240735b7c35f506637dd01cbeda4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604472"
---
# <a name="let-clause-visual-basic"></a>Let 句 (Visual Basic)
値を計算し、クエリ内で新しい変数に代入します。  
  
## <a name="syntax"></a>構文  
  
```  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`variable`|必須。 指定した式の結果を参照に使用できるエイリアスです。|  
|`expression`|必須。 評価し、指定された変数に割り当てられている式です。|  
  
## <a name="remarks"></a>コメント  
 `Let`句では、計算値はそれぞれのクエリの結果とエイリアスを使用してそれらを参照することができます。 エイリアスをなどの他の句で使用できます、`Where`句。 `Let`句では、クエリに含まれる式の句の別名を指定し、式の句が使用されるたびに、エイリアスに置き換えるために読みやすくクエリ ステートメントを作成することができます。  
  
 任意の数を含めることができます`variable`と`expression`の割り当て、`Let`句。 コンマ (,) では、各割り当てを区切ります。  
  
## <a name="example"></a>例  
 次のコード例では、`Let`句の製品に 10% の割引を計算します。  
  
 [!code-vb[VbSimpleQuerySamples#16](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [クエリ](../../../visual-basic/language-reference/queries/queries.md)  
 [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From 句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [WHERE 句](../../../visual-basic/language-reference/queries/where-clause.md)
