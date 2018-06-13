---
title: ParamArray (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ParamArray
- ParamArray
helpviewer_keywords:
- ParamArray keyword [Visual Basic]
- ParamArray keyword [Visual Basic], syntax
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
ms.openlocfilehash: be8ddb7f9ba08535d12890d1c5c82a9b7b485f3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597361"
---
# <a name="paramarray-visual-basic"></a>ParamArray (Visual Basic)
プロシージャのパラメーターが、指定した型の要素のオプション配列を受け取ることを指定します。 `ParamArray` パラメーター リストの最後のパラメーターでのみ使用できます。  
  
## <a name="remarks"></a>コメント  
 `ParamArray` プロシージャに任意の数の引数を渡すことができます。 A`ParamArray`宣言されたパラメーターを常に使用する[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)です。  
  
 1 つまたは複数の引数を指定することができます、`ParamArray`適切なデータの配列を渡すことによってパラメーターの型、値、または何ものコンマ区切りの一覧にします。 詳細についてを参照してください"の呼び出しを ParamArray"[パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)です。  
  
> [!IMPORTANT]
>  無制限に大きくなることが、配列を処理するたびに、アプリケーションの内部の容量を超過してしまうリスクがあります。 呼び出し元のコード、パラメーター配列を同意する場合は、その長さをテストしはアプリケーションには大きすぎる場合は、適切な手順を実行する必要があります。  
  
 `ParamArray` 修飾子は、次のコンテキストで使用できます。  
  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目  
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)  
 [パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
