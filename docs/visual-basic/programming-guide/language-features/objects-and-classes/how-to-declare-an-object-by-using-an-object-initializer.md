---
title: '方法: オブジェクト初期化子を使用してオブジェクトを宣言する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: 3a372ba91377b53c87c05976e416ca8ed55ccbbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649166"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a>方法: オブジェクト初期化子を使用してオブジェクトを宣言する (Visual Basic)
オブジェクト初期化子を使用すると、宣言して、単一のステートメント内のクラスのインスタンスをインスタンス化できます。 さらに、パラメーター化されたコンス トラクターを呼び出さずに、同時にインスタンスの 1 つまたは複数のメンバーを初期化することができます。  
  
 オブジェクト初期化子を使用して名前付きの型のインスタンスを作成するときに指定した順序で指定されたメンバーの初期化後に、クラスの既定のコンス トラクターが呼び出されます。  
  
 次の手順のインスタンスを作成する方法を示しています、 `Student` 3 つの方法でクラスです。 クラスには、名、姓、名、およびクラス年などのプロパティがあります。 新しいインスタンスを作成、3 つの宣言の各`Student`、プロパティを持つ`First`プロパティ「マイケル ・」に設定`Last`"Tucker"に設定され、その他のすべてのメンバーが既定値に設定します。 プロシージャのそれぞれの宣言の結果は、次の例は、オブジェクト初期化子を使用しないと等価です。  
  
 [!code-vb[VbVbalrObjectInit#20](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_1.vb)]  
  
 実装については、`Student`クラスを参照してください[する方法: リストの項目を作成](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)です。 コードをコピーするには、クラスを設定しの一覧を作成するには、そのトピックから`Student`オブジェクトを使用します。  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a>オブジェクト初期化子を使用して、名前付きクラスのオブジェクトを作成するには  
  
1.  コンス トラクターを使用する場合に、宣言を開始します。  
  
     `Dim student1 As New Student`  
  
2.  キーワードを入力`With`、中かっこで初期化リストは、その後にします。  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3.  初期化リストには初期化し、初期値を割り当てる必要とする各プロパティが含まれます。 プロパティの名前の前にピリオドです。  
  
     [!code-vb[VbVbalrObjectInit#21](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_2.vb)]  
  
     クラスの 1 つまたは複数のメンバーを初期化することができます。  
  
4.  または、クラスの新しいインスタンスを宣言しに値を割り当てることができます。 インスタンスを最初に、宣言`Student`:  
  
     `Dim student2 As Student`  
  
5.  インスタンスの作成を開始します`Student`通常の方法でします。  
  
     `Dim student2 As Student = New Student`  
  
6.  型`With`とし、オブジェクト初期化子に 1 つまたは複数のメンバーの新しいインスタンスを初期化します。  
  
     [!code-vb[VbVbalrObjectInit#22](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_3.vb)]  
  
7.  省略することで、前の手順で定義を簡素化できます`As Student`です。 これを行う場合、コンパイラが判断した`student3`のインスタンスは、`Student`ローカル型推論を使用しています。  
  
     [!code-vb[VbVbalrObjectInit#23](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_4.vb)]  
  
     詳細については、次を参照してください。[ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [方法: 項目のリストを作成する](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)  
 [オブジェクト初期化子 : 名前付きの型と匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
