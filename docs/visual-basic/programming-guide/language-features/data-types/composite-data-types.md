---
title: 複合データ型 (Visual Basic)
ms.date: 04/25/2017
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
ms.openlocfilehash: 73867a5881db7c94d258e8716c4ff4c5b1119e71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650440"
---
# <a name="composite-data-types-visual-basic"></a>複合データ型 (Visual Basic)
Visual Basic に用意されている基本データ型だけでなく、作成するさまざまな種類の項目を作成することができますも*複合データ型*構造体、配列、およびクラスなどです。 その他の複合型および基本型からは、複合データ型を構築できます。 たとえば、配列メンバーを持つ構造体の要素の配列または構造体を定義できます。  
  
## <a name="data-types"></a>データの種類  
 複合型は、そのコンポーネントのいずれかのデータ型と異なるです。 たとえば、配列の`Integer`の要素ではありません、`Integer`データ型。  
  
 配列のデータ型は、通常、必要に応じて、要素の型、丸かっこ、コンマを使用して表されます。 たとえば、1 次元配列`String`として表される要素`String()`と、2 次元の配列`Boolean`として表される要素`Boolean(,)`です。  
  
## <a name="structure-types"></a>構造体の型  
 すべての構造を包括する 1 つのデータ型はありません。 代わりに、2 つの構造が同じ順序で同一要素を定義する場合でも、構造体の各定義は、固有のデータ型を表します。 ただし、同じ構造の 2 つ以上のインスタンスを作成する場合は、Visual Basic は、同じデータ型のそれらと見なします。  
  
## <a name="tuples"></a>タプル

組は、定義済みの型を持つ 2 つ以上のフィールドが含まれる軽量な構造です。 組は、以降 2017 年 Visual Basic でサポートされます。 組は、参照渡しの引数を渡さずにまたはより多量のクラスまたは構造体で返されるフィールドをパッケージ化せず、1 つのメソッドの呼び出しから複数の値を返す最もよく使用されます。 参照してください、[組](tuples.md)組の詳細については、トピックです。

## <a name="array-types"></a>配列型  
 すべての配列を包括する 1 つのデータ型はありません。 配列の特定のインスタンスのデータ型は、次のように決定されます。  
  
-   配列であること  
  
-   配列のランク (次元数)  
  
-   配列の要素の型  
  
 特に、指定した次元の長さは、インスタンスのデータ型の一部ではありません。 次に例を示します。  
  
```  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 上記の例では、配列変数`arrayA`と`arrayB`は、同じデータ型であると見なされます: `Byte()` — 場合でも、異なる長さに初期化されます。 変数`arrayB`と`arrayC`同じ種類が、要素型が異なるためです。 変数`arrayC`と`arrayD`ランクが異なるために、同じ型のされていません。 変数`arrayD`と`arrayE`同じ型を持つ — `Short(,)` — ランクと要素の型が同じなので、たとえ`arrayD`がまだ初期化されていません。  
  
 配列の詳細については、次を参照してください。[配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)です。  
  
## <a name="class-types"></a>クラスの種類  
 すべてのクラスを構成する 1 つのデータ型はありません。 1 つのクラスは、別のクラスから継承できます、それぞれが個別のデータ型です。 同じクラスの複数のインスタンスでは、同じデータ型です。 1 つのクラスのインスタンス変数を割り当てるには別に、同じデータ型がだけでなく、メモリ内で同じクラスのインスタンスを指すようにします。  
  
 クラスの詳細については、次を参照してください。[クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)です。  
  
## <a name="see-also"></a>関連項目  
 [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Visual Basic での型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [方法 : 変数内で複数の値を保持する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
