---
title: Set ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Set
helpviewer_keywords:
- property procedures [Visual Basic], Set statements
- Set statement [Visual Basic]
- Set statement [Visual Basic], syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
ms.openlocfilehash: dbc48d14bac54809e4ddd12c87429bf407169950
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604836"
---
# <a name="set-statement-visual-basic"></a>Set ステートメント (Visual Basic)
宣言、`Set`プロパティ プロシージャのプロパティに値を代入するために使用します。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a>指定項目  
 `attributelist`  
 任意。 参照してください[属性一覧](../../../visual-basic/language-reference/statements/attribute-list.md)です。  
  
 `accessmodifier`  
 1 つの省略可能な`Get`と`Set`このプロパティ内のステートメント。 次のいずれかの値を指定します。  
  
-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
-   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
-   `Protected Friend`  
  
 参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。  
  
 `value`  
 必須。 プロパティの新しい値を格納するパラメーター。  
  
 `datatype`  
 場合は必須`Option Strict`は`On`します。 データ型、`value`パラメーター。 指定されたデータ型は、プロパティのデータ型と同じである必要があります、これ`Set`ステートメントを宣言します。  
  
 `statements`  
 任意。 場合に実行する 1 つまたは複数のステートメント、`Set`プロパティ プロシージャが呼び出されます。  
  
 `End Set`  
 必須。 定義を終了、`Set`プロパティ プロシージャです。  
  
## <a name="remarks"></a>コメント  
 すべてのプロパティがあります、`Set`プロパティ プロシージャ、プロパティが設定されていない限り`ReadOnly`です。 `Set`プロパティの値を設定する手順を使用します。  
  
 Visual Basic は、このプロパティの自動的に呼び出します`Set`代入ステートメントは、プロパティに格納される値を提供するときの手順です。  
  
 Visual Basic のパラメーターを渡す、`Set`プロパティの割り当て時にプロシージャです。 パラメーターを指定しない場合`Set`、統合開発環境 (IDE) という名前の暗黙のパラメーターを使用して`value`です。 パラメーターでは、プロパティに割り当てられる値を保持します。 通常プライベート ローカル変数にこの値を格納して返すたびに、`Get`プロシージャが呼び出されます。  
  
 プロパティの宣言の本体でのみ、プロパティを含めることができます`Get`と`Set`間でのプロシージャ、 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)と`End Property`ステートメントです。 これらのプロシージャ以外のものを格納できません。 具体的には、プロパティの現在の値を格納できません。 プロパティ プロシージャのいずれかの内側で保存する場合、その他のプロパティ プロシージャ アクセスできないために、プロパティの外部には、この値を格納する必要があります。 通常の方法は、の値を格納する、[プライベート](../../../visual-basic/language-reference/modifiers/private.md)プロパティと同じレベルで宣言された変数です。 定義する必要があります、`Set`に適用すると、プロパティの内部プロシージャです。  
  
 `Set`プロシージャの既定値は、包含するプロパティのアクセス レベルを使用する場合を除き、`accessmodifier`で、`Set`ステートメントです。  
  
## <a name="rules"></a>ルール  
  
-   **混合アクセス レベル。** 必要に応じていずれかの異なるアクセス レベルを指定することができます、読み取り/書き込みプロパティを定義する場合、`Get`または`Set`プロシージャが、両方は使用できません。 これを行うと、プロシージャのアクセス レベルがプロパティのアクセス レベルよりも制限する必要があります。 プロパティが宣言されている場合など、 `Friend`、宣言することができます、`Set`プロシージャ`Private`、ではなく`Public`です。  
  
     定義する場合、 `WriteOnly` 、プロパティ、`Set`プロシージャが全体のプロパティを表します。 レベルを別のアクセスを宣言することはできません`Set`プロパティの 2 つのアクセス レベルを設定することがあるため、します。  
  
## <a name="behavior"></a>動作  
  
-   **プロパティ プロシージャから取得します。** ときに、`Set`次のステートメントを格納する値が指定されている、プロシージャ呼び出し元のコードに戻ると、実行が継続します。  
  
     `Set` プロパティ プロシージャは、いずれかを使用して返すことができます、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)または[Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)です。  
  
     `Exit Property`と`Return`ステートメントでは、プロパティ プロシージャからすぐに終了します。 任意の数の`Exit Property`と`Return`ステートメントがどこにでも表示、プロシージャとを混在させること`Exit Property`と`Return`ステートメントです。  
  
## <a name="example"></a>例  
 次の例では、`Set`プロパティの値を設定するステートメント。  
  
 [!code-vb[VbVbalrStatements#55](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/set-statement_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Get ステートメント](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Property プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
