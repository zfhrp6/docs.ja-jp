---
title: Get ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Get
helpviewer_keywords:
- Get statement [Visual Basic], syntax
- Get statement [Visual Basic]
- properties [Visual Basic], read-only
- read-only properties
- Get keyword [Visual Basic]
- property procedures [Visual Basic], Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
ms.openlocfilehash: d6a6fdfd191de76871619dea3bd1794b487698aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605109"
---
# <a name="get-statement"></a>Get ステートメント
宣言、`Get`プロパティ プロシージャのプロパティの値を取得するために使用します。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`attributelist`|任意。 参照してください[属性一覧](../../../visual-basic/language-reference/statements/attribute-list.md)です。|  
|`accessmodifier`|1 つの省略可能な`Get`と`Set`このプロパティ内のステートメント。 次のいずれかの値を指定します。<br /><br /> -   [保護されています。](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [プライベート](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> 参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。|  
|`statements`|任意。 場合に実行する 1 つまたは複数のステートメント、`Get`プロパティ プロシージャが呼び出されます。|  
|`End Get`|必須。 定義を終了、`Get`プロパティ プロシージャです。|  
  
## <a name="remarks"></a>コメント  
 すべてのプロパティがあります、`Get`プロパティ プロシージャ、プロパティが設定されていない限り`WriteOnly`です。 `Get`プロパティの現在の値を返すプロシージャを使用します。  
  
 Visual Basic は、このプロパティの自動的に呼び出します`Get`式は、プロパティの値を要求するときの手順です。  
  
 プロパティの宣言の本体でのみ、プロパティを含めることができます`Get`と`Set`間でのプロシージャ、 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)と`End Property`ステートメントです。 これらのプロシージャ以外のものを格納できません。 具体的には、プロパティの現在の値を格納できません。 プロパティ プロシージャのいずれかの内側で保存する場合、その他のプロパティ プロシージャ アクセスできないために、プロパティの外部には、この値を格納する必要があります。 通常の方法は、の値を格納する、[プライベート](../../../visual-basic/language-reference/modifiers/private.md)プロパティと同じレベルで宣言された変数です。 定義する必要があります、`Get`に適用すると、プロパティの内部プロシージャです。  
  
 `Get`プロシージャの既定値は、包含するプロパティのアクセス レベルを使用する場合を除き、`accessmodifier`で、`Get`ステートメントです。  
  
## <a name="rules"></a>ルール  
  
-   **混合アクセス レベル。** 必要に応じていずれかの異なるアクセス レベルを指定することができます、読み取り/書き込みプロパティを定義する場合、`Get`または`Set`プロシージャが、両方は使用できません。 これを行うと、プロシージャのアクセス レベルがプロパティのアクセス レベルよりも制限する必要があります。 プロパティが宣言されている場合など、 `Friend`、宣言することができます、`Get`プロシージャ`Private`、ではなく`Public`です。  
  
     定義する場合、 `ReadOnly` 、プロパティ、`Get`プロシージャが全体のプロパティを表します。 レベルを別のアクセスを宣言することはできません`Get`プロパティの 2 つのアクセス レベルを設定することがあるため、します。  
  
-   **型を返します。** [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)が返す値のデータ型を宣言できます。 `Get`プロシージャが自動的にそのデータ型を返します。 任意のデータ型または列挙型、構造体、クラス、またはインターフェイスの名前を指定することができます。  
  
     場合、`Property`ステートメントで指定されていない`returntype`、プロシージャを返します`Object`です。  
  
## <a name="behavior"></a>動作  
  
-   **プロシージャから取得します。** ときに、`Get`プロパティ値を要求するステートメント内で、プロシージャ呼び出し元のコードに戻ると、実行が継続します。  
  
     `Get` プロパティ プロシージャは、いずれかを使用して値を返すことができます、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)か、プロパティ名を戻り値を割り当てます。 詳細についてを参照してください「戻り値」[関数ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)です。  
  
     `Exit Property`と`Return`ステートメントでは、プロパティ プロシージャからすぐに終了します。 任意の数の`Exit Property`と`Return`ステートメントがどこにでも表示、プロシージャとを混在させること`Exit Property`と`Return`ステートメントです。  
  
-   **値を返します。** 値を返す、`Get`プロシージャ、プロパティ名に値を割り当てるか、含めることで、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)です。 `Return`ステートメントを同時に割り当てます、`Get`プロシージャを返す値し、手順を終了します。  
  
     使用する場合`Exit Property`プロパティ名に値を代入せず、`Get`プロシージャは、プロパティのデータ型の既定値を返します。 詳細についてを参照してください「戻り値」[関数ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)です。  
  
     次の例は、読み取り専用プロパティの 2 つの方法を示しています。`quoteForTheDay`プライベート変数に保持されている値を返すことができます`quoteValue`です。  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_2.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_3.vb)]  
  
## <a name="example"></a>例  
 次の例では、`Get`プロパティの値を返すステートメントです。  
  
 [!code-vb[VbVbalrStatements#30](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_4.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Set ステートメント](../../../visual-basic/language-reference/statements/set-statement.md)  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [チュートリアル : クラスの定義](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
