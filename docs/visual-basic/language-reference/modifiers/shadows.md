---
title: Shadows (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Shadows
- shadows
helpviewer_keywords:
- shadowing
- duplicate names [Visual Basic]
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic]
- names [Visual Basic], shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
ms.openlocfilehash: 4ca4ec48ee63b71447056a2c5cb68e8948f27ad0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604654"
---
# <a name="shadows-visual-basic"></a>Shadows (Visual Basic)
宣言されたプログラミング要素を宣言し、同じ名前を持つ要素は、または基底クラスのオーバー ロードされる要素のセットを非表示にすることを指定します。  
  
## <a name="remarks"></a>コメント  
 シャドウの主な目的は、(とも呼ばれるは*名前による隠ぺい*) をクラスのメンバーの定義を維持しています。 基本クラスがありますを変えることが定義されている 1 つとして同じ名前の要素を作成します。 この場合、`Shadows`修飾子強制的に実行をするメンバーに解決するのには、クラスを参照する基本クラスの新しい要素の代わりに定義された、します。  
  
 シャドウとオーバーライドは、どちらも継承された要素を再定義しますが、その方法は大きく異なります。 詳細については、次を参照してください。 [Visual Basic におけるシャドウ](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)です。  
  
## <a name="rules"></a>ルール  
  
-   **宣言コンテキスト。** 使用することができます`Shadows`クラス レベルでのみです。 つまりの宣言コンテキスト、`Shadows`要素がクラスである必要があり、ソース ファイル、名前空間、インターフェイス、モジュール、構造体、またはプロシージャにすることはできません。  
  
     1 つの宣言ステートメントで 1 つだけのシャドウ要素を宣言することができます。  
  
-   **結合された修飾子。** 指定することはできません`Shadows`と共に`Overloads`、 `Overrides`、または`Static`同じ宣言内で。  
  
-   **要素の型。** 宣言された要素は、他の任意の種類の要素でシャドウできます。 プロパティまたはプロシージャを別のプロパティまたはプロシージャをシャドウする場合、パラメーターと戻り値の型はありません、基底クラスのプロパティまたはプロシージャのものと一致します。  
  
-   **アクセスします。** 基本クラスの影付きの要素は、それをシャドウする派生クラス内で通常利用ではありません。 ただし、次の考慮事項が適用されます。  
  
    -   シャドウする要素が参照するコードからアクセスできない場合は、シャドウされた要素への参照は解決されます。 たとえば場合、`Private`要素をシャドウする基本クラスの要素では、コードへのアクセス許可がない、`Private`要素は、基底クラス要素を代わりにアクセスします。  
  
    -   要素をシャドウする場合は、基底クラスの型で宣言されたオブジェクトをシャドウされた要素を引き続きアクセスできます。 を通じてアクセスすることも`MyBase`します。  
  
 `Shadows` 修飾子は、次のコンテキストで使用できます。  
  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Static](../../../visual-basic/language-reference/modifiers/static.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [Me、My、MyBase、および MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [オーバーロード](../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Visual Basic におけるシャドウ](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
