---
title: Select 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySelect
helpviewer_keywords:
- Select statement [Visual Basic]
- Select clause [Visual Basic]
- queries [Visual Basic], Select
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
ms.openlocfilehash: 55c1e79b9e8e26483c1b7374a755bf977129169b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="select-clause-visual-basic"></a>Select 句 (Visual Basic)
クエリの結果を定義します。  
  
## <a name="syntax"></a>構文  
  
```  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## <a name="parts"></a>指定項目  
 `var1`  
 任意。 列の式の結果を参照に使用できるエイリアスです。  
  
 `fieldName1`  
 必須。 クエリの結果で返されるフィールドの名前。  
  
## <a name="remarks"></a>コメント  
 使用することができます、`Select`句をクエリから返される結果を定義します。 これにより、クエリによって作成される新しい匿名型のメンバーを定義するか、またはクエリによって返される名前付きの型のメンバーを対象にすることができます。 `Select`句は、クエリの必要はありません。 ない場合は`Select`句を指定すると、現在のスコープで示されている範囲変数のすべてのメンバーに基づいた型が返されます。 詳細については、「[匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。 クエリでは、名前付きの型を作成するときの型の結果が返されます。<xref:System.Collections.Generic.IEnumerable%601>場所`T`は、作成された型です。  
  
 `Select`句は、現在のスコープ内のどの変数を参照できます。 これで示されている範囲変数が含まれます、`From`句 (または`From`句)。 別名によって作成された新しい変数も含まれています、 `Aggregate`、 `Let`、 `Group By`、または`Group Join`句、または、以前の変数`Select`クエリ式内の句。 `Select`句では、静的な値を含めることもできます。 次のコード例は、クエリ式を示しますたとえば、`Select`句は、4 つのメンバーを持つ新しい匿名型として、クエリの結果を定義します。 `ProductName`、 `Price`、 `Discount`、および`DiscountedPrice`です。 `ProductName`と`Price`メンバー値で定義されている製品の範囲変数から取得されますが、`From`句。 `DiscountedPrice`でメンバーの値を計算、`Let`句。 `Discount`メンバーは、静的な値です。  
  
 [!code-vb[VbSimpleQuerySamples#27](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_1.vb)]  
  
 `Select`句が後続のクエリ句の範囲変数の新しいセットを紹介し、前の範囲変数がスコープ内に不要になった。 最後の`Select`句をクエリ式では、クエリの戻り値を決定します。 たとえば、次のクエリ ID を返します、会社名と注文合計が 500 を超えるすべての顧客注文の。 最初の`Select`句は指定の範囲変数、`Where`句と、2 つ目`Select`句。 2 番目`Select`句は、新しい匿名型として、クエリによって返される値を指定します。  
  
 [!code-vb[VbSimpleQuerySamples#28](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_2.vb)]  
  
 場合、`Select`句を返す 1 つの項目を識別する、クエリ式は、その 1 つの項目の種類のコレクションを返します。 場合、`Select`句を返す複数の項目を識別する、クエリ式は、選択したアイテムに基づいて、新しい匿名型のコレクションを返します。 たとえば、次の 2 つのクエリがに基づいて 2 つの異なる型のコレクションを返す、`Select`句。 最初のクエリでは、会社名の文字列としてのコレクションを返します。 2 番目のクエリのコレクションを返します`Customer`と会社名とアドレス情報が格納されます。  
  
 [!code-vb[VbSimpleQuerySamples#29](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_3.vb)]  
  
## <a name="example"></a>例  
 次のクエリ式は、`From`範囲変数を宣言する句`cust`の`customers`コレクション。 `Select`句は、顧客名と ID 値を選択し、設定、`CompanyName`と`CustomerID`新しい範囲変数の列です。 `For Each`ステートメントが返された各オブジェクトをループ処理し、表示、`CompanyName`と`CustomerID`各レコードの列です。  
  
 [!code-vb[VbSimpleQuerySamples#30](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/select-clause_4.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [クエリ](../../../visual-basic/language-reference/queries/queries.md)  
 [From 句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [WHERE 句](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Order By 句](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
