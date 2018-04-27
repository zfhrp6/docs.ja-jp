---
title: Module ステートメント
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 51f8fd063449c072a69cdffd9f6ce2a96cc3f68c
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="module-statement"></a>Module ステートメント
モジュールの名前を宣言し、変数、プロパティ、イベント、およびモジュールを構成するプロシージャの定義を紹介します。  
  
## <a name="syntax"></a>構文  
  
```vb 
[ <attributelist> ] [ accessmodifier ]  Module name  
    [ statements ]  
End Module  
```  
  
## <a name="parts"></a>指定項目  
 `attributelist`  
 任意。 参照してください[属性一覧](../../../visual-basic/language-reference/statements/attribute-list.md)です。  
  
 `accessmodifier`  
 任意。 次のいずれかの値を指定します。  
  
-   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
 参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。  
  
 `name`  
 必須。 このモジュールの名前です。 参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。  
  
 `statements`  
 任意。 変数、プロパティ、イベント、プロシージャ、およびこのモジュールの入れ子にされた型を定義するステートメント。  
  
 `End Module`  
 `Module` の定義を終了します。  
  
## <a name="remarks"></a>コメント  
 A`Module`ステートメントは、その名前空間全体で使用できる参照型を定義します。 A*モジュール*(とも呼ばれる、*標準的なモジュール*) のようないくつかの重要な違いですが、クラスにします。 すべてのモジュールは、1 つのインスタンスを持ち、作成または変数に代入する必要はありません。 モジュールは継承をサポートしていないまたはインターフェイスを実装します。 モジュールは通知、*型*クラスまたは構造体は、という意味で、モジュールのデータ型を持つプログラミング要素を宣言することはできません。  
  
 使用することができます`Module`名前空間レベルでのみです。 つまり、*宣言コンテキスト*モジュールのソース ファイルまたは名前空間にある必要があります、クラス、構造体、モジュール、インターフェイス、プロシージャ、またはブロックすることはできません。 文字列または任意の種類別のモジュール内のモジュールを入れ子にすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 モジュールが、有効期間は、プログラムと同じです。 そのメンバーはすべてため`Shared`、また以下にするプログラムの有効期間があります。  
  
 既定で、モジュール[フレンド](../../../visual-basic/language-reference/modifiers/friend.md)アクセスします。 アクセス修飾子を使用してこれらのアクセス レベルを調整できます。 詳細については、次を参照してください。 [Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。  
  
 モジュールのすべてのメンバーは、暗黙的に`Shared`です。  
  
## <a name="classes-and-modules"></a>クラスとモジュール  
 これらの要素がある多くの類似点がいくつかの重要な違いがあります。  
  
-   **用語集。** 以前のバージョンの Visual Basic モジュールの 2 つの種類を認識する:*クラス モジュール*(.cls ファイル) と*標準モジュール*(.bas ファイル)。 現在のバージョンを呼び出す*クラス*と*モジュール*、それぞれします。  
  
-   **共有メンバー。** クラスのメンバーは、共有するかどうか、またはインスタンス メンバーを制御できます。  
  
-   **オブジェクトの方向。** クラスは、オブジェクト指向しますが、モジュールがないです。 したがって、クラスだけをオブジェクトとしてインスタンス化できます。 詳細については、次を参照してください。[クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)です。  
  
## <a name="rules"></a>ルール  
  
-   **修飾子です。** すべてのモジュールのメンバーは、暗黙的に[Shared](../../../visual-basic/language-reference/modifiers/shared.md)です。 使用することはできません、`Shared`キーワードと、任意のメンバーの共有の状態を変更して、メンバーを宣言することはできません。  
  
-   **継承。** モジュールが以外の任意の型から継承できません<xref:System.Object>、どのすべてのモジュールから継承します。 具体的には、1 つのモジュールは、別の継承できません。  
  
     使用することはできません、 [Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)モジュールの定義を指定するも<xref:System.Object>します。  
  
-   **既定のプロパティ。** モジュールには、既定のプロパティを定義できません。 詳細については、次を参照してください。[既定](../../../visual-basic/language-reference/modifiers/default.md)です。  
  
## <a name="behavior"></a>動作  
  
-   **アクセス レベル。** モジュール内では、各メンバーを独自のアクセス レベルを宣言できます。 モジュール メンバー[パブリック](../../../visual-basic/language-reference/modifiers/public.md)へのアクセス、変数および定数を除く既定[プライベート](../../../visual-basic/language-reference/modifiers/private.md)アクセスします。 モジュールがアクセスより制限のメンバーのいずれか、ときに、指定されたモジュールのアクセス レベルが優先されます。  
  
-   **スコープです。** モジュールのスコープは全体の名前空間です。  
  
     すべてのモジュール メンバーのスコープは、モジュール全体です。 すべてのメンバーに注意してください*プロモーションを入力*、それが原因で、モジュールを含む名前空間に昇格するには、そのスコープ。 詳細については、次を参照してください。[型の上位変換](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)です。  
  
-   **パス名です。** プロジェクトでは、複数のモジュールがあることができ、2 つ以上のモジュール内の同じ名前を持つメンバーを宣言できます。 ただし、参照がそのモジュールの外部から場合は、このような名前のメンバーが、適切なモジュールへの参照を修飾する必要があります。 詳細については、次を参照してください。[宣言された要素への参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)です。  
  
## <a name="example"></a>例  
 [!code-vb[VbVbalrStatements#69](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/module-statement_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Namespace ステートメント](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
 [型の上位変換](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
