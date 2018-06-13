---
title: IsNot 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: babee364d350ca84a8379f675acc4b5c87f98303
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603315"
---
# <a name="isnot-operator-visual-basic"></a>IsNot 演算子 (Visual Basic)
2 つのオブジェクト参照変数を比較します。  
  
## <a name="syntax"></a>構文  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 `Boolean` 値。  
  
 `object1`  
 必須。 どの`Object`変数または式。  
  
 `object2`  
 必須。 どの`Object`変数または式。  
  
## <a name="remarks"></a>コメント  
 `IsNot`演算子は、次の 2 つのオブジェクト参照が別のオブジェクトを参照してかどうかを決定します。 ただし、値の比較は実行しません。 場合`object1`と`object2`正確な同じオブジェクト インスタンスをどちらも参照してください`result`は`False`以外の場合は一致しない場合、`result`は`True`します。  
  
 `IsNot` 逆の`Is`演算子。 利点は、`IsNot`は避けることができますを組み合わせて`Not`と`Is`、読みにくくなることができます。  
  
 使用することができます、`Is`と`IsNot`事前バインドおよび遅延バインディングの両方のオブジェクトをテストする演算子です。  
  
> [!NOTE]
>  `IsNot`から返される式を比較する演算子を使用することはできません、`TypeOf`演算子。 代わりに、使用する必要があります、`Not`と`Is`演算子。  
  
## <a name="example"></a>例  
 次のコード例では、両方は使用して、`Is`演算子および`IsNot`を同じ比較を実行する演算子です。  
  
 [!code-vb[VbVbalrOperators#29](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Is 演算子](../../../visual-basic/language-reference/operators/is-operator.md)  
 [TypeOf 演算子](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [方法: 2 つのオブジェクトが等しいかどうかをテストする](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
