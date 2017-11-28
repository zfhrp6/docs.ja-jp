---
title: "Distinct 句 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6ed92d5d601c1ec329728346ac881c4fa2bad8aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="distinct-clause-visual-basic"></a>Distinct 句 (Visual Basic)
次のクエリ句で、重複を回避するのには、現在の範囲変数の値を制限します。  
  
## <a name="syntax"></a>構文  
  
```  
Distinct  
```  
  
## <a name="remarks"></a>コメント  
 使用することができます、`Distinct`句に固有のアイテムの一覧を返します。 `Distinct`句によって重複するクエリの結果を無視するクエリ。 `Distinct`句は、すべてで指定されたフィールドの戻り値の重複する値に適用されます、`Select`句。 ない場合は`Select`句を指定する、`Distinct`句は、クエリで特定の範囲変数に適用、`From`句。 範囲変数が、不変の型でない場合は、型のすべてのメンバーには、既存のクエリ結果が一致する場合、クエリはのみ、クエリ結果が無視されます。  
  
## <a name="example"></a>例  
 次のクエリ式は、顧客注文のリストと顧客のリストを結合します。 `Distinct`句は一意の顧客名のリストを返し、注文日に含まれています。  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [クエリ](../../../visual-basic/language-reference/queries/queries.md)  
 [From 句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [WHERE 句](../../../visual-basic/language-reference/queries/where-clause.md)
