---
title: '方法: Visual Basic で配列変数を初期化する'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], initializing
- arrays [Visual Basic], variables
- arrays [Visual Basic], initializing
- arrays [Visual Basic], declaring
ms.assetid: aadd7a60-7ca4-4608-b986-091f19e7fc10
ms.openlocfilehash: ee8cb91fd2fae9637a0d0e33fca63a4cdb9d2fce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651571"
---
# <a name="how-to-initialize-an-array-variable-in-visual-basic"></a>方法: Visual Basic で配列変数を初期化する
配列リテラルを `New` 句に含めること、および配列の初期値を指定することで、配列変数を初期化します。 型を指定するか、配列リテラル内の値から推論することを許可できます。 型を推論する方法の詳細についてを参照してください「を設定する、配列に初期値」[配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)です。  
  
### <a name="to-initialize-an-array-variable-by-using-an-array-literal"></a>配列リテラルを使用して配列変数を初期化するには  
  
-   `New` 句で、または配列値を割り当てるときに、中かっこ (`{}`) の中に要素の値を指定します。 変数を宣言、作成、および初期化して `Char` 型の要素を持つ配列を含めるいくつかの方法を次の例に示します。  
  
     [!code-vb[VbVbalrArrays#16](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_1.vb)]  
  
     各ステートメントを実行すると、長さが 3 の配列が作成され、インデックス 0 からインデックス 2 の各要素に初期値が格納されます。 上限および値の両方を指定した場合、インデックス 0 から上限までの、すべての要素の値を含める必要があります。  
  
     配列リテラルで要素の値を指定した場合は、インデックスの上限を指定する必要はありません。 上限が指定されていない場合、配列リテラル内の値の数に基づいて配列のサイズが推論されます。  
  
### <a name="to-initialize-a-multidimensional-array-variable-by-using-array-literals"></a>配列リテラルを使用して多次元配列変数を初期化するには  
  
-   中かっこ (`{}`) で囲んだ値を入れ子にして中かっこの中に含めます。 入れ子になったすべての配列リテラルが、型と長さが同じ配列として推論されるようにします。 多次元配列を初期化するいくつかの例を次に示します。  
  
     [!code-vb[VbVbalrArrays#17](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_2.vb)]  
  
-   配列の範囲は明示的に指定することも省略することもできます。省略した場合、配列リテラル内の値に基づいてコンパイラによって配列の範囲が推論されます。 上限と値の両方を指定する場合は、すべての次元について、インデックス 0 ～上限までの値を指定する必要があります。 変数を宣言、作成、および初期化して `Short` 型の要素を持つ 2 次元配列を含めるいくつかの方法を次の例に示します。  
  
     [!code-vb[VbVbalrArrays#18](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_3.vb)]  
  
     各ステートメントを実行すると、初期化された 6 つの要素 (インデックスは `(0,0)`、`(0,1)`、`(0,2)`、`(1,0)`、`(1,1)`、および `(1,2)`) が格納された配列が作成されます。 配列のそれぞれの位置には値 `10` が格納されます。  
  
-   次の例では、多次元配列を反復処理します。 Visual Basic で記述された Windows コンソール アプリケーションでは、コードを `Sub Main()` メソッド内に貼り付けます。 最終コメントは出力を示しています。  
  
     [!code-vb[VbVbalrArrays#31](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_4.vb)]  
  
### <a name="to-initialize-a-jagged-array-variable-by-using-array-literals"></a>配列リテラルを使用してジャグ配列変数を初期化するには  
  
-   中かっこ (`{}`) で囲んだオブジェクトの値を入れ子にします。 ジャグ配列の場合、長さが異なる配列を指定する配列リテラルを入れ子にすることもできますが、入れ子になった配列リテラルがかっこ (`()`) で囲まれていることを確認してください。 かっこで囲むことで、入れ子になった配列リテラルが強制的に評価され、結果の配列がジャグ配列の初期値として使用されるようになります。 ジャグ配列を初期化する 2 つの例を次に示します。  
  
     [!code-vb[VbVbalrArrays#19](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_5.vb)]  
  
-   次の例では、ジャグ配列を反復処理します。 Visual Basic で記述された Windows コンソール アプリケーションでは、コードを `Sub Main()` メソッド内に貼り付けます。  コードの最終コメントは出力を示しています。  
  
     [!code-vb[VbVbalrArrays#32](../../../../visual-basic/programming-guide/language-features/arrays/codesnippet/VisualBasic/how-to-initialize-an-array-variable_6.vb)]  
  
## <a name="see-also"></a>関連項目  
 [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [配列のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)
