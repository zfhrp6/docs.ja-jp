---
title: Nothing (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Nothing
- vb.Nothing
helpviewer_keywords:
- Nothing keyword [Visual Basic]
- Nothing keyword [Visual Basic], syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
ms.openlocfilehash: fb1af7d748faac78b26177af453a0e858f9e97c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603991"
---
# <a name="nothing-visual-basic"></a>Nothing (Visual Basic)
任意のデータ型の既定値を表します。 参照型の場合、既定値は、`null`参照します。 値型の場合、既定値は値の型が null 値を許容するかどうかに依存します。  
  
> [!NOTE]
>  Null 非許容値型の場合は、 `Nothing` Visual Basic では異なって`null`(C#)。 Visual Basic の場合に null 非許容値型の変数を設定した場合に`Nothing`変数が宣言された型の既定値に設定されています。 C# の場合、null 非許容値型の変数を割り当てる場合`null`コンパイル時エラーが発生します。  
  
## <a name="remarks"></a>コメント  
 `Nothing` データ型の既定値を表します。 既定値は、変数が、値の型または参照型によって異なります。  
  
 変数、*値の型*直接その値が含まれています。 値の型は、すべての数値データ型を含める`Boolean`、 `Char`、 `Date`、すべての構造体、およびすべての列挙体です。 変数、*型参照*メモリ内オブジェクトのインスタンスへの参照を格納します。 参照型には、クラス、配列、デリゲート、および文字列が含まれます。 詳細については、「 [Value Types and Reference Types](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)」を参照してください。  
  
 変数は、値の場合は入力の動作`Nothing`かどうか、変数が null 許容型のデータ型によって異なります。 Null 許容値型を表す、追加、`?`型名を修飾子です。 割り当てる`Nothing`null 許容変数に値を設定`null`です。 詳細と例については、次を参照してください。 [null 許容値型](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)です。  
  
 変数が null 許容ではない値型である場合、割り当てる`Nothing`ことのセットには、既定値に、宣言された型。 その型の変数のメンバーが含まれている場合はすべて、既定値に設定します。 次の例は、スカラー型の場合、これを示しています。  
  
 [!code-vb[VbVbalrKeywords#7](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_1.vb)]  
  
 変数が参照型である場合、割り当てる`Nothing`変数設定、`null`変数の型の参照。 設定されている変数、`null`参照に関連付けられていない任意のオブジェクト。 次に例を示します。  
  
 [!code-vb[VbVbalrKeywords#8](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_2.vb)]  
  
 変数は参照 (または null 許容の値を入力) するかどうかをチェックするときに`null`、使用しない`= Nothing`または`<> Nothing`です。 常に使用する`Is Nothing`または`IsNot Nothing`です。  
  
 Visual Basic における文字列、空の文字列と同じ`Nothing`です。 したがって、`"" = Nothing`は true です。  
  
 次の例を使用する比較を示しています、`Is`と`IsNot`演算子。  
  
 [!code-vb[VbVbalrKeywords#9](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_3.vb)]  
  
 使用せずに変数を宣言する場合、`As`句には、設定と`Nothing`、変数の型を持つ`Object`します。 この例は、`Dim something = Nothing`です。 ここでは、コンパイル時エラーが発生したときに`Option Strict`上と`Option Infer`は無効になってです。  
  
 割り当てると`Nothing`を object 変数にその参照しなく任意のオブジェクト インスタンスにします。 場合は、変数インスタンスを参照していたに設定すると`Nothing`インスタンス自体は終了しません。 インスタンスが終了し、ガベージ コレクター (GC) では、アクティブな参照が残ってがないことが検出された後にのみ関連付けられているメモリとシステム リソースを解放します。  
  
 `Nothing` 異なります、<xref:System.DBNull>初期化されていないバリアントまたは存在しないデータベース列を表すオブジェクト。  
  
## <a name="see-also"></a>関連項目  
 [Dim ステートメント](../../visual-basic/language-reference/statements/dim-statement.md)  
 [オブジェクトの有効期間 : オブジェクトの作成と破棄](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [Visual Basic における有効期間](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Is 演算子](../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot 演算子](../../visual-basic/language-reference/operators/isnot-operator.md)  
 [null 許容値型](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
