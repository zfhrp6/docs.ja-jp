---
title: New 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.new
- vb.NewConstraint
helpviewer_keywords:
- constraints, Visual Basic generic types
- generics [Visual Basic], constraints
- constraints, New keyword [Visual Basic]
- New constraint
- New keyword [Visual Basic]
ms.assetid: d7d566d7-fe0e-4336-91f7-641a542de4d0
ms.openlocfilehash: 0fe511b2c16681d7bab7eeda7c121fcbbaa2f5dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603640"
---
# <a name="new-operator-visual-basic"></a>New 演算子 (Visual Basic)
導入されています、`New`句を新しいオブジェクト インスタンスを作成する型パラメーターにコンス トラクター制約を指定または識別、`Sub`クラス コンス トラクターと手順。  
  
## <a name="remarks"></a>コメント  
 代入ステートメントの宣言で、`New`句は、定義済みのインスタンスの作成元となるクラスを指定する必要があります。 つまり、クラスが呼び出し元のコードがアクセスできる 1 つまたは複数のコンス トラクターを公開する必要があります。  
  
 使用することができます、`New`宣言ステートメントまたは代入ステートメントの句。 ステートメントを実行すると、指定した任意の引数を渡して、指定したクラスの適切なコンス トラクターを呼び出します。 次の例では、これを示しますのインスタンスを作成することで、`Customer`いずれかのパラメーターをとらない使用し、文字列パラメーターを受け取るいずれかを使用する、2 つのコンス トラクターを持つクラス。  
  
 [!code-vb[VbVbalrKeywords#11](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_1.vb)]  
  
 配列はクラス、`New`次の例に示すように、配列の新しいインスタンスを作成することができます。  
  
 [!code-vb[VbVbalrKeywords#12](../../../visual-basic/language-reference/codesnippet/VisualBasic/new-operator_2.vb)]  
  
 共通言語ランタイム (CLR) スロー、<xref:System.OutOfMemoryException>メモリ不足の新しいインスタンスを作成する場合はエラーです。  
  
> [!NOTE]
>  `New`キーワードにも使用型パラメーター リストで指定された型がアクセスできるパラメーターなしコンス トラクターを公開する必要がありますを指定します。 型パラメーターや制約の詳細については、次を参照してください。[型リスト](../../../visual-basic/language-reference/statements/type-list.md)です。  
  
 クラスのコンス トラクターのプロシージャを作成するには、名前を設定、`Sub`する手順、`New`キーワード。 詳細については、次を参照してください。[オブジェクトの有効期間: オブジェクトが作成と破棄にはどのように](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)です。  
  
 キーワード `New` は次のコンテキストで使用できます。  
  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Of](../../../visual-basic/language-reference/statements/of-clause.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目  
 <xref:System.OutOfMemoryException>  
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)  
 [型リスト](../../../visual-basic/language-reference/statements/type-list.md)  
 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [オブジェクトの有効期間 : オブジェクトの作成と破棄](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
