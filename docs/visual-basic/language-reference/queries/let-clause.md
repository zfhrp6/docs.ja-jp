---
title: Let 句 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 70e47517a62f58dcababd31c26277417b62eab66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
|`variable`|必須です。 指定した式の結果を参照に使用できるエイリアスです。|  
|`expression`|必須です。 評価し、指定された変数に割り当てられている式です。|  
  
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
