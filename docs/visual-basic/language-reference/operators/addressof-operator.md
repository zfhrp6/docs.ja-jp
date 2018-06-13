---
title: AddressOf 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
ms.openlocfilehash: 7c229c32a3b295b4dbfe50ca2abc60d4ad5f2145
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597788"
---
# <a name="addressof-operator-visual-basic"></a>AddressOf 演算子 (Visual Basic)
特定のプロシージャを参照するプロシージャ デリゲート インスタンスを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a>指定項目  
 `procedurename`  
 必須。 新しく作成されたプロシージャ デリゲートで参照するプロシージャを指定します。  
  
## <a name="remarks"></a>コメント  
 `AddressOf`演算子で指定された関数を指して関数デリゲートを作成する`procedurename`です。 指定したプロシージャが場合、関数デリゲートのインスタンス メソッドが、インスタンスとメソッドの両方を参照します。 次に、関数デリゲートが呼び出されたときに、指定したインスタンスの指定したメソッドが呼び出されます。  
  
 `AddressOf`演算子は、デリゲート コンス トラクターのオペランドとして使用できますか、コンパイラによってデリゲートの型を決定できるコンテキストで使用できます。  
  
## <a name="example"></a>例  
 この例では、`AddressOf`を処理するデリゲートを指定する演算子、`Click`ボタンのイベントです。  
  
 [!code-vb[VbVbalrDelegates#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]  
  
## <a name="example"></a>例  
 次の例では、`AddressOf`スレッドのスタートアップ関数を指定する演算子です。  
  
 [!code-vb[VbVbalrDelegates#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md)
