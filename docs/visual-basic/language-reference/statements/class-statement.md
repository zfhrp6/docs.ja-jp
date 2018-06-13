---
title: Class ステートメント (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Class
helpviewer_keywords:
- class modules
- Class statement [Visual Basic]
- classes [Visual Basic], fields
- fields [Visual Basic], of classes
- class types [Visual Basic], class statements
- classes [Visual Basic], creating
- classes [Visual Basic], data members
- data members [Visual Basic], of classes
ms.assetid: f2664f38-eb5a-4d4b-a374-1d041521fb6c
ms.openlocfilehash: 1d81ce148e237df6997934f70c294630f6cc7b8d
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34235883"
---
# <a name="class-statement-visual-basic"></a>Class ステートメント (Visual Basic)
クラスの名前を宣言し、変数、プロパティ、イベント、およびクラスを構成するプロシージャの定義が追加されました。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] [ Partial ] _  
Class name [ ( Of typelist ) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ statements ]  
End Class  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`attributelist`|任意。 参照してください[属性一覧](../../../visual-basic/language-reference/statements/attribute-list.md)です。|  
|`accessmodifier`|任意。 次のいずれかの値を指定します。<br /><br /> -   [パブリック](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [保護されています。](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [プライベート](../../../visual-basic/language-reference/modifiers/private.md)<br />-   [保護されたフレンド](../../language-reference/modifiers/protected-friend.md)<br />- [保護されたプライベート](../../language-reference/modifiers/private-protected.md)<br/><br/> 参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。|  
|`Shadows`|任意。 参照してください[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)です。|  
|`MustInherit`|任意。 参照してください[MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)です。|  
|`NotInheritable`|任意。 参照してください[NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)です。|  
|`Partial`|任意。 クラスの部分定義を示します。 参照してください[部分](../../../visual-basic/language-reference/modifiers/partial.md)です。|  
|`name`|必須。 このクラスの名前です。 参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。|  
|`Of`|任意。 これは、ジェネリック クラスであることを指定します。|  
|`typelist`|使用するかどうかは必ず、[の](../../../visual-basic/language-reference/statements/of-clause.md)キーワード。 このクラスの型パラメーターの一覧。 参照してください[のリストを入力](../../../visual-basic/language-reference/statements/type-list.md)です。|  
|`Inherits`|任意。 このクラスが別のクラスのメンバーを継承することを示します。 参照してください[Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)です。|  
|`classname`|`Inherits` ステートメントを使用する場合は必ず指定します。 このクラスの派生元となるクラスの名前。|  
|`Implements`|任意。 このクラスで、1 つまたは複数のインターフェイスのメンバーを実装することを示します。 参照してください[ステートメントを実装します](../../../visual-basic/language-reference/statements/implements-statement.md)です。|  
|`interfacenames`|`Implements` ステートメントを使用する場合は必ず指定します。 このクラスが実装するインターフェイスの名前。|  
|`statements`|任意。 このクラスのメンバーを定義するステートメント。|  
|`End Class`|必須。 `Class` の定義を終了します。|  
  
## <a name="remarks"></a>コメント  
 A`Class`ステートメントが、新しいデータ型を定義します。 A*クラス*オブジェクト指向プログラミング (OOP) の基本的なビルド ブロックです。 詳細については、次を参照してください。[クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)です。  
  
 `Class` は、名前空間またはモジュール レベルでのみ使用できます。 つまり、*宣言コンテキスト*クラスのソース ファイル、名前空間、クラス、構造体、モジュール、またはインターフェイスである必要があります、プロシージャまたはブロックすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 クラスの各インスタンスには、その他のすべてのインスタンスの独立した有効期間があります。 これを作成するときにこの有効期間が開始、 [New 演算子](../../../visual-basic/language-reference/operators/new-operator.md)句またはなどの関数によって<xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>です。 インスタンスを指すすべての変数に設定されている時に終了[Nothing](../../../visual-basic/language-reference/nothing.md)またはその他のクラスのインスタンスにします。  
  
 クラスの既定値は[フレンド](../../../visual-basic/language-reference/modifiers/friend.md)アクセスします。 アクセス修飾子を使用してこれらのアクセス レベルを調整できます。 詳細については、次を参照してください。 [Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。  
  
## <a name="rules"></a>ルール  
  
-   **入れ子にするとします。** 他の中で 1 つのクラスを定義できます。 外側のクラス、*クラスを含む*、内部クラスを呼び出すと、*入れ子になったクラス*です。  
  
-   **継承。** クラスで使用する場合、 [Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)、基底クラスまたはインターフェイスの 1 つだけを指定することができます。 クラスは、複数の要素から継承できません。  
  
     クラスより制限の厳しいアクセス レベルを持つ別のクラスから継承できません。 たとえば、`Public`クラスから継承できません、`Friend`クラスです。  
  
     クラスは、内部に入れ子になったクラスから継承できません。  
  
-   **実装です。** クラスで使用する場合、 [Implements ステートメント](../../../visual-basic/language-reference/statements/implements-statement.md)で指定したすべてのインターフェイスによって定義されたすべてのメンバーを実装する必要があります`interfacenames`です。 この例外は、基底クラスのメンバーの再実装が必要です。 詳細についてを参照してください再実装が「必要」 [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)です。  
  
-   **既定のプロパティ。** クラスとして最大で 1 つのプロパティを指定できます、*既定プロパティ*です。 詳細については、次を参照してください。[既定](../../../visual-basic/language-reference/modifiers/default.md)です。  
  
## <a name="behavior"></a>動作  
  
-   **アクセス レベル。** クラス内では、各メンバーを独自のアクセス レベルを宣言できます。 クラス メンバーは既定[パブリック](../../../visual-basic/language-reference/modifiers/public.md)へのアクセス、変数および定数を除く既定[プライベート](../../../visual-basic/language-reference/modifiers/private.md)アクセスします。 クラスがそのメンバーの 1 つ以上のアクセスが制限されたよりする場合は、クラスのアクセス レベルが優先されます。  
  
-   **スコープです。** クラスは、そのを含む名前空間、クラス、構造体、またはモジュール全体にわたってスコープ内です。  
  
     すべてのクラス メンバーのスコープは、クラス全体です。  
  
     **有効期間。** Visual Basic は、静的クラスをサポートしていません。 静的クラスと同等の機能は、モジュールによって提供されます。 詳細については、次を参照してください。[モジュール ステートメント](../../../visual-basic/language-reference/statements/module-statement.md)です。  
  
     クラスのメンバーには、宣言されている方法と場所に応じて有効期間があります。 詳細については、次を参照してください。 [Visual Basic における有効期間](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)です。  
  
-   **パス名です。** クラスの外側のコードでは、そのクラスの名前を持つメンバーの名前を修飾する必要があります。  
  
     入れ子になったクラス内のコード、プログラミング要素への参照を修飾されていない場合は、Visual Basic 要素を検索、まず、入れ子になったクラスで、そのクラスを含むなど外側のコンテナー要素にします。  
  
## <a name="classes-and-modules"></a>クラスとモジュール  
 これらの要素がある多くの類似点がいくつかの重要な違いがあります。  
  
-   **用語集。** 以前のバージョンの Visual Basic モジュールの 2 つの種類を認識する:*クラス モジュール*(.cls ファイル) と*標準モジュール*(.bas ファイル)。 現在のバージョンを呼び出す*クラス*と*モジュール*、それぞれします。  
  
-   **共有メンバー。** クラスのメンバーは、共有するかどうか、またはインスタンス メンバーを制御できます。  
  
-   **オブジェクトの方向。** クラスは、オブジェクト指向しますが、モジュールがないです。 クラスの 1 つまたは複数のインスタンスを作成することができます。 詳細については、次を参照してください。[クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)です。  
  
## <a name="example"></a>例  
 次の例では、`Class`クラスといくつかのメンバーを定義するステートメント。  
  
 [!code-vb[VbVbalrStatements#62](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/class-statement_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [構造体とクラス](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Module ステートメント](../../../visual-basic/language-reference/statements/module-statement.md)  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
 [オブジェクトの有効期間 : オブジェクトの作成と破棄](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [方法 : ジェネリック クラスを使用する](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
