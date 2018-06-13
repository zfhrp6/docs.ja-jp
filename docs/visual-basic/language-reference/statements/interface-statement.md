---
title: Interface ステートメント (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Interface
helpviewer_keywords:
- interface statement [Visual Basic]
- interfaces [Visual Basic], interface definition
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
ms.openlocfilehash: 31ff9211034438e225494b916045acd07c37810f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34233913"
---
# <a name="interface-statement-visual-basic"></a>Interface ステートメント (Visual Basic)
インターフェイスの名前を宣言し、インターフェイスに含まれるメンバーの定義を紹介します。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] _  
Interface name [ ( Of typelist ) ]  
    [ Inherits interfacenames ]  
    [ [ modifiers ] Property membername ]  
    [ [ modifiers ] Function membername ]  
    [ [ modifiers ] Sub membername ]  
    [ [ modifiers ] Event membername ]  
    [ [ modifiers ] Interface membername ]  
    [ [ modifiers ] Class membername ]  
    [ [ modifiers ] Structure membername ]  
End Interface  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`attributelist`|任意。 参照してください[属性一覧](../../../visual-basic/language-reference/statements/attribute-list.md)です。|  
|`accessmodifier`|任意。 次のいずれかの値を指定します。<br /><br /> -   [パブリック](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [保護されています。](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [プライベート](../../../visual-basic/language-reference/modifiers/private.md)<br />-  [保護されたフレンド](../../language-reference/modifiers/protected-friend.md)<br/>- [保護されたプライベート](../../language-reference/modifiers/private-protected.md)<br /><br /> 参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。|  
|`Shadows`|任意。 参照してください[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)です。|  
|`name`|必須。 このインターフェイスの名前です。 参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。|  
|`Of`|任意。 ジェネリック インターフェイスは、これを指定します。|  
|`typelist`|使用するかどうかは必ず、[の](../../../visual-basic/language-reference/statements/of-clause.md)キーワード。 このインターフェイスの型パラメーターの一覧です。 必要に応じて、型パラメーターごとに宣言できますバリアントを使用して`In`と`Out`ジェネリック修飾子です。 参照してください[のリストを入力](../../../visual-basic/language-reference/statements/type-list.md)です。|  
|`Inherits`|任意。 このインターフェイスが別のインターフェイスまたはインターフェイスのメンバーと属性を継承することを示します。 参照してください[Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)です。|  
|`interfacenames`|`Inherits` ステートメントを使用する場合は必ず指定します。 このインターフェイスの派生元のインターフェイスの名前。|  
|`modifiers`|任意。 定義するインターフェイス メンバーの適切な修飾子。|  
|`Property`|任意。 インターフェイスのメンバーであるプロパティを定義します。|  
|`Function`|任意。 定義、`Function`インターフェイスのメンバーであるプロシージャです。|  
|`Sub`|任意。 定義、`Sub`インターフェイスのメンバーであるプロシージャです。|  
|`Event`|任意。 インターフェイスのメンバーであるイベントを定義します。|  
|`Interface`|任意。 このインターフェイス内で入れ子になったであるインターフェイスを定義します。 入れ子になったインターフェイスの定義が終了する必要があります、`End Interface`ステートメントです。|  
|`Class`|任意。 インターフェイスのメンバーであるクラスを定義します。 クラスの定義が終了する必要があります、`End Class`ステートメントです。|  
|`Structure`|任意。 インターフェイスのメンバーである構造体を定義します。 構造体のメンバーの定義がで終了する必要があります、`End Structure`ステートメントです。|  
|`membername`|各プロパティ、プロシージャ、イベント、インターフェイス、クラス、またはインターフェイスのメンバーとして定義された構造に必要です。 メンバーの名前。|  
|`End Interface`|`Interface` の定義を終了します。|  
  
## <a name="remarks"></a>コメント  
 *インターフェイス*プロパティおよびプロシージャは、クラスし、構造体を実装できますなど、メンバーのセットを定義します。 インターフェイスのメンバーとその内部機能ではない署名のみを定義します。  
  
 クラスまたは構造体、インターフェイスで定義されたすべてのメンバー コードを指定することによって、インターフェイスを実装します。 最後に、アプリケーションは、そのクラスまたは構造体からのインスタンスを作成するときに、オブジェクトが存在し、メモリ内で実行します。 詳細については、次を参照してください。[クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)と[インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)です。  
  
 `Interface` は、名前空間またはモジュール レベルでのみ使用できます。 つまり、*宣言コンテキスト*インターフェイスは、ソース ファイル、名前空間、クラス、構造体、モジュール、またはインターフェイスである必要があります、プロシージャまたはブロックすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 インターフェイスの既定値は[フレンド](../../../visual-basic/language-reference/modifiers/friend.md)アクセスします。 アクセス修飾子を使用してこれらのアクセス レベルを調整できます。 詳細については、次を参照してください。 [Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。  
  
## <a name="rules"></a>ルール  
  
-   **インターフェイスの入れ子。** 他の中で 1 つのインターフェイスを定義できます。 外側のインターフェイス、*インターフェイスを含む*、内部のインターフェイスを呼び出すと、*入れ子になったインターフェイス*です。  
  
-   **メンバーの宣言。** のみを定義するインターフェイスのメンバーとして、プロパティまたはプロシージャを宣言する場合、*署名*そのプロパティまたはプロシージャのです。 これには、要素の型 (プロパティまたはプロシージャ)、そのパラメーターとパラメーターの型、および戻り値の型が含まれます。 このため、メンバーの定義はコード、および終端ステートメントなどの 1 行のみを使用して`End Function`または`End Property`はインターフェイスでは無効です。  
  
     これに対し、列挙型または構造体、または入れ子になったクラスまたはインターフェイスを定義するときに、そのデータ メンバーを含める必要です。  
  
-   **メンバー修飾子。** アクセス修飾子を使用することはできませんモジュール メンバーを定義するときに指定することも[共有](../../../visual-basic/language-reference/modifiers/shared.md)またはを除き、プロシージャ修飾子[Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)です。 持つメンバーを宣言することができます[シャドウ](../../../visual-basic/language-reference/modifiers/shadows.md)、使用することができます[既定](../../../visual-basic/language-reference/modifiers/default.md)、プロパティを定義するときにだけでなく[読み取り専用](../../../visual-basic/language-reference/modifiers/readonly.md)または[WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)です。  
  
-   **継承。** インターフェイスで使用する場合、 [Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)、1 つまたは複数の基底インターフェイスを指定することができます。 同じ名前のメンバーが定義されている場合でも、2 つのインターフェイスから継承することができます。 これを行う場合、実装コードは、実装するメンバーを指定する名前の修飾を使用する必要があります。  
  
     インターフェイスより制限の厳しいアクセス レベルを持つ別のインターフェイスから継承できません。 たとえば、`Public`インターフェイスを継承できません、`Friend`インターフェイスです。  
  
     インターフェイスは、内部に入れ子になったインターフェイスから継承できません。  
  
-   **実装です。** クラスを使用する場合、 [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)ステートメントをこのインターフェイスを実装するインターフェイス内で定義されているすべてのメンバーを実装する必要があります。 さらに、各シグネチャの実装コードには、このインターフェイスで定義されている対応する署名を正確に一致する必要があります。 ただし、実装コードに含まれるメンバーの名前は、インターフェイスで定義されているメンバー名と一致する必要はありません。  
  
     クラスが実装する場合、プロシージャ、としてプロシージャを指定することできません`Shared`です。  
  
-   **既定のプロパティ。** インターフェイスとして最大で 1 つのプロパティを指定できます、*既定プロパティ*プロパティ名を使用しない参照されていることができます。 宣言することによってこのようなプロパティを指定する、[既定](../../../visual-basic/language-reference/modifiers/default.md)修飾子です。  
  
     つまり、何も継承している場合にのみ、インターフェイスに、既定のプロパティを定義できますに注意してください。  
  
## <a name="behavior"></a>動作  
  
-   **アクセス レベル。** すべてのインターフェイス メンバーが暗黙的が[パブリック](../../../visual-basic/language-reference/modifiers/public.md)アクセスします。 メンバーを定義するときに、アクセス修飾子を使用することはできません。 ただし、インターフェイスを実装するクラスでは、実装された各メンバーのアクセス レベルを宣言することができます。  
  
     クラスのインスタンスを変数に代入する場合、そのメンバーのアクセス レベルは、変数のデータ型が、基になるインターフェイスまたはクラスの実装がかどうかに依存できます。 次に例を示します。  
  
     [!code-vb[VbVbalrStatements#39](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/interface-statement_1.vb)]  
  
     を通じてクラス メンバーにアクセスする場合`varAsInterface`、すべてのパブリック アクセスがあります。 ただし、を通じてメンバーにアクセスする場合`varAsClass`、`Sub`プロシージャ`doSomething`プライベート アクセスします。  
  
-   **スコープです。** インターフェイスでは、その名前空間、クラス、構造体、またはモジュール全体にわたってスコープ内です。  
  
     すべてのインターフェイス メンバーのスコープは、全体のインターフェイスです。  
  
-   **有効期間。** インターフェイス自体が有効期間は、また、そのメンバーをしないでください。 ときに、クラス インターフェイスを実装し、オブジェクトとして作成されますのインスタンス クラス、オブジェクトが実行されているアプリケーション内で有効期間。 詳細についてを参照してください「の有効期間」[クラス ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)です。  
  
## <a name="example"></a>例  
 次の例では、`Interface`をという名前のインターフェイスを定義するステートメント`thisInterface`、これを使用して実装する必要があります、`Property`ステートメントと`Function`ステートメントです。  
  
 [!code-vb[VbVbalrStatements#40](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/interface-statement_2.vb)]  
  
 なお、`Property`と`Function`ステートメントは終わるブロックを導入していません`End Property`と`End Function`インターフェイス内で。 インターフェイスでは、そのメンバーのシグネチャのみを定義します。 完全`Property`と`Function`を実装するクラスに表示されるブロック`thisInterface`です。  
  
## <a name="see-also"></a>関連項目  
 [インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Module ステートメント](../../../visual-basic/language-reference/statements/module-statement.md)  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [ジェネリック インターフェイスの分散](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
