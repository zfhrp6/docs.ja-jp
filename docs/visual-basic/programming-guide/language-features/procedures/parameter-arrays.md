---
title: パラメーター配列 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
ms.openlocfilehash: a91da0d9e16ff11fdd4980588fee64b3e4a603c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652378"
---
# <a name="parameter-arrays-visual-basic"></a>パラメーター配列 (Visual Basic)
通常、プロシージャ宣言で指定より引数を持つプロシージャを呼び出すことはできません。 不特定多数の引数が必要なときを宣言できます、*パラメーター配列*、これにより、プロシージャ パラメーターの値の配列を受け入れるようにします。 プロシージャを定義するときに、パラメーター配列内の要素の数を把握する必要はありません。 配列のサイズは、プロシージャ呼び出しごとに個別に決定されます。  
  
## <a name="declaring-a-paramarray"></a>ParamArray を宣言します。  
 使用する、 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)パラメーター リストでは、パラメーター配列を示すキーワードです。 次の規則が適用されます。  
  
-   プロシージャが 1 つだけのパラメーター配列を定義およびプロシージャの定義の最後のパラメーターをする必要があります。  
  
-   パラメーター配列は、値で渡される必要があります。 明示的に指定することをお勧め、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)プロシージャの定義のキーワードです。  
  
-   パラメーター配列は、自動的に省略可能です。 既定値は、パラメーター配列の要素の型の空の 1 次元配列です。  
  
-   パラメーター配列の前のすべてのパラメーターを必須にする必要があります。 パラメーター配列は、のみ省略可能なパラメーターである必要があります。  
  
## <a name="calling-a-paramarray"></a>ParamArray を呼び出す  
 パラメーター配列を定義するプロシージャを呼び出すときに、次の方法のいずれかで、引数を指定できます。  
  
-   何も — は、省略できます、 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)引数。 この場合、空の配列は、プロシージャに渡されます。 渡すことも、 [Nothing](../../../../visual-basic/language-reference/nothing.md)キーワードは、同じ効果を持つ。  
  
-   任意の数の引数、コンマ区切りの一覧。 各引数のデータ型は暗黙的に変換する必要があります、`ParamArray`要素の型。  
  
-   同じ要素を持つ配列は、パラメーター配列の要素型として入力します。  
  
 すべての場合、プロシージャ内のコード、パラメーターは配列として扱いますと同じデータ型の要素を持つ 1 次元配列、`ParamArray`データ型。  
  
> [!IMPORTANT]
>  無制限に大きくなることが、配列を処理するたびに、アプリケーションの内部の容量を超過してしまうリスクがあります。 パラメーター配列を受け取る場合は、呼び出し元のコードによって渡される配列のサイズをテストする必要があります。 アプリケーションには大きすぎる場合は、適切な手順を実行します。 詳細については、次を参照してください。[配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)です。  
  
## <a name="example"></a>例  
 次の例を定義し、関数を呼び出す`calcSum`です。 `ParamArray`パラメーター修飾子`args`可変個の引数を受け入れるように関数を有効にします。  
  
 [!code-vb[VbVbalrStatements#26](../../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-arrays_1.vb)]  
  
 次の例では、パラメーター配列を持つプロシージャを定義し、パラメーター配列に渡されるすべての配列要素の値を出力します。  
  
 [!code-vb[VbVbcnProcedures#48](./codesnippet/VisualBasic/parameter-arrays_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#49](./codesnippet/VisualBasic/parameter-arrays_3.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [手順](./index.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)  
 [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md)  
 [省略可能なパラメーター](./optional-parameters.md)  
 [プロシージャのオーバーロード](./procedure-overloading.md)  
 [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)
