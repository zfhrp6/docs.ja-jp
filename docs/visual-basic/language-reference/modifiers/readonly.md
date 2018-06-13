---
title: ReadOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: e2957bf49292dfcafab8e78f4b997247c34ad279
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599913"
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
変数またはプロパティを読み取るがある書き込まれませんを指定します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="rules"></a>ルール  
  
-   **宣言コンテキスト。** `ReadOnly` は、モジュール レベルでのみ使用できます。 つまりの宣言コンテキスト、`ReadOnly`要素は、クラス、構造体、またはモジュールにある必要があるあり、ソース ファイル、名前空間、またはプロシージャにすることはできません。  
  
-   **結合された修飾子。** 指定することはできません`ReadOnly`と共に`Static`同じ宣言内で。  
  
-   **値を代入しています。** コードの使用、`ReadOnly`プロパティは、その値を設定できません。 基になる記憶域にアクセスするコードが割り当てるまたはいつでも、値を変更します。  
  
     値を割り当てることができます、`ReadOnly`変数の宣言またはクラスまたは定義されている構造体のコンス トラクターでのみです。  
  
## <a name="when-to-use-a-readonly-variable"></a>読み取り専用変数を使用する場合  
 使用することはできませんが、 [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)を宣言し、定数値を割り当てます。 たとえば、`Const`ステートメントで割り当てるには、必要なデータ型を受け入れない場合や、定数式でのコンパイル時に値を計算することができません。 わからない場合がありますも値コンパイル時にします。 このような場合は、使用することができます、`ReadOnly`定数値を保持する変数。  
  
> [!IMPORTANT]
>  場合でも、変数自体に、そのメンバーを変更することができます、変数のデータ型が配列またはクラスのインスタンスなど、参照型の場合`ReadOnly`です。 次に例を示します。  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 初期化する場合、配列を指す`characterArray()`を保持"x"、"y"および"z"です。 変数`characterArray`は`ReadOnly`、初期化; であると、その値を変更することはできません、新しい配列を割り当てることはできません。 ただし、配列メンバーの 1 つ以上の値を変更することができます。 次のプロシージャの呼び出し`changeArrayElement`、配列を指す`characterArray()`を保持"x"、"M"および"z"です。  
  
 これは、プロシージャ パラメーターの宣言に似て[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)プロシージャが呼び出し元引数自体を変更できないようにするが、そのメンバーを変更することができます。  
  
## <a name="example"></a>例  
 次の例では定義、`ReadOnly`従業員が雇用された日付のプロパティです。 プロパティ値としての内部クラス ストア、`Private`クラス内の変数、およびのみのコードは、その値を変更できます。 ただし、このプロパティは`Public`、すべてのコードをクラスにアクセスできますが、プロパティを読み取ることができます。  
  
 [!code-vb[VbVbalrKeywords#4](../../../visual-basic/language-reference/codesnippet/VisualBasic/readonly_1.vb)]  
  
 `ReadOnly` 修飾子は、次のコンテキストで使用できます。  
  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>関連項目  
 [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)
