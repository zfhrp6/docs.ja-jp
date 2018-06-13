---
title: Distinct 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 4b0ce12f6361d3dc6e5cc3601e96fc3a9bcf3841
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603978"
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
