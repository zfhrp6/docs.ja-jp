---
title: '方法: 配列を別の配列に代入する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: 63c7d187152fcb5ea84378c677aa687f334f63de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647931"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a>方法: 配列を別の配列に代入する (Visual Basic)
配列がオブジェクトであるため、他のオブジェクト型のような代入ステートメントで使用することができます。 配列変数、配列要素と、ランクと長さの情報を構成するデータへのポインターを保持し、割り当ては、このポインターだけをコピーします。  
  
### <a name="to-assign-one-array-to-another-array"></a>別の配列に 1 つの配列を割り当てる  
  
1.  2 つの配列に同じランク (次元数) と互換性のある要素のデータ型があることを確認します。  
  
2.  標準の代入ステートメントを使用して、コピー先の配列を元の配列を割り当てます。 かっこ付きのいずれかの配列名は使用しないでください。  
  
    ```  
    Dim formArray() As System.Windows.Forms.Form  
    Dim controlArray() As System.Windows.Forms.Control  
    controlArray = formArray  
    ```  
  
 1 つの配列を別に代入すると、次の規則が適用されます。  
  
-   **ランクが等しい。** コピー先の配列のランク (次元数) は、元の配列と同じにする必要があります。  
  
     2 つの配列のランクが等しい、提供されたディメンションは同等である必要はありません。 指定した次元にある要素の数を割り当て中に変更できます。  
  
-   **要素の型。** 両方のいずれかの配列にいる必要があります*型参照*要素または両方の配列にいる必要があります*値の型*要素。 詳細については、次を参照してください。[値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)です。  
  
    -   両方の配列には、値型の要素がある、要素のデータ型があります正確に同じです。 唯一の例外は、の配列を割り当てることができます`Enum`の基本型の配列に要素`Enum`です。  
  
    -   両方の配列には、参照型の要素がある、ソース要素の型が変換先の要素の型から派生する必要があります。 そうでは、ときに、その要素として同じ継承関係がある 2 つの配列。 これと呼ばれる*配列の共変性*です。  
  
 コンパイラは、エラー場合は、上記の規則に違反している、たとえば、データ型は互換性がない場合や、ランクが等しくないことを報告します。 割り当てを試行する前に、配列に互換性があるかどうかを確認するコードにエラー処理を追加することができます。 使用することも、 [TryCast 演算子](../../../../visual-basic/language-reference/operators/trycast-operator.md)例外がスローされないようにする場合は、キーワード。  
  
## <a name="see-also"></a>関連項目  
 [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [配列のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [Enum ステートメント](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [配列変換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
