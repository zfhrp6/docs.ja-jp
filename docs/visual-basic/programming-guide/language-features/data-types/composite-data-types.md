---
title: "複合データ型 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types
- composite data types
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures, composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d81b2c08155cb16754e780fdfb341b596322302d
ms.lasthandoff: 03/13/2017

---
# <a name="composite-data-types-visual-basic"></a>複合データ型 (Visual Basic)
基本データ型だけでなく[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]物資を作成するさまざまな種類の項目も組み合わせてできます*複合データ型*構造体、配列、およびクラスなどです。 基本型およびその他の複合型、複合データ型を構築できます。 たとえば、配列メンバーを持つ、構造体または構造体の要素の配列を定義できます。  
  
## <a name="data-types"></a>データ型  
 複合型は、そのコンポーネントのいずれかのデータ型と異なります。 たとえば、配列の`Integer`の要素ではありません、`Integer`データ型。  
  
 配列のデータ型は、通常、必要に応じて、要素の型、かっこ、およびコンマを使用して表されます。 1 次元の配列など`String`として表される要素`String()`と、2 次元の配列`Boolean`として表される要素`Boolean(,)`します。  
  
## <a name="structure-types"></a>構造体の型  
 すべての構造を包括する&1; つのデータ型はありません。 代わりに、2 つの構造が同じ順序で同一要素を定義する場合でも、構造体の各定義は、固有のデータ型を表します。 ただし、同じ構造の&2; つ以上のインスタンスを作成する場合[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]はそれらを同じデータ型と見なします。  
  
## <a name="array-types"></a>配列型  
 すべての配列を包括する&1; つのデータ型はありません。 配列の特定のインスタンスのデータ型は、次のように決定されます。  
  
-   配列であること  
  
-   配列のランク (次元数)  
  
-   配列の要素の型  
  
 特に、次元の長さは、インスタンスのデータ型の一部ではありません。 次に例を示します。  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 上記の例では、配列変数`arrayA`と`arrayB`、同じデータ型と見なされます: `Byte()` — 場合でも、異なる長さに初期化されます。 変数`arrayB`と`arrayC`は、同じ型のない、要素型が異なるためです。 変数`arrayC`と`arrayD`は、同じ型のない、ランクが異なるためです。 変数`arrayD`と`arrayE`同じ型を持つ — `Short(,)` -ランクと要素の型が同じなので、たとえ`arrayD`がまだ初期化されていません。  
  
 配列の詳細については、次を参照してください。[配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)します。  
  
## <a name="class-types"></a>クラスの種類  
 すべてのクラスを包括する&1; つのデータ型はありません。 1 つのクラスが別のクラスから継承できる各は個別のデータ型です。 同じクラスの複数のインスタンスでは、同じデータ型です。 クラスのインスタンスの&1; つの変数を割り当てるには別に、同じデータ型を持つ操作を行いますだけでなく、メモリ内の同じクラス インスタンスを指すようにします。  
  
 クラスの詳細については、次を参照してください。[オブジェクトおよびクラス](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)します。  
  
## <a name="see-also"></a>関連項目  
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [データ型のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [方法 : 変数内で複数の値を保持する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
