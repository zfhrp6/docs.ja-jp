---
title: Public (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: a5e9161132ba6d571daa30ce82e1bfb1dd2b064f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34235919"
---
# <a name="public-visual-basic"></a>Public (Visual Basic)
1 つまたは複数の宣言されたプログラミング要素にアクセス制限がありますいないことを指定します。  
  
## <a name="remarks"></a>コメント  
 コンポーネントまたはクラス ライブラリなどのコンポーネントのセットを公開している場合は、プログラミング要素へのアセンブリと相互運用する任意のコードからアクセスできる通常します。 このような要素に無制限のアクセスを与えるには、ことを宣言できます`Public`です。  
  
 パブリック アクセスへのアクセスを制限する必要がないときに、プログラミング要素には、通常のレベルです。 要素のアクセス レベルがインターフェイス、モジュール、クラスまたは構造体内で宣言されていることに注意してください。 既定値は`Public`特に宣言しない場合。  
  
## <a name="rules"></a>ルール  
  
-   **宣言コンテキスト。** 使用することができます`Public`モジュール、インターフェイス、または名前空間レベルでのみです。 つまりの宣言コンテキスト、`Public`要素は、ソース ファイル、名前空間、インターフェイス、モジュール、クラス、または構造体にある必要があるあり、プロシージャをすることはできません。  
  
## <a name="behavior"></a>動作  
  
-   **アクセス レベル。** モジュール、クラスまたは構造体にアクセスできるすべてのコードがアクセスできる、`Public`要素。  
  
-   **既定のアクセス。** パブリック アクセスを既定のプロシージャ内のローカル変数は、それらのアクセス修飾子を使用できません。  
  
-   **アクセス修飾子。** アクセス レベルを指定するキーワードと呼ばれる*アクセス修飾子*です。 アクセス修飾子の比較を参照してください。 [Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。  
  
 `Public` 修飾子は、次のコンテキストで使用できます。  
  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Module ステートメント](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目  
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [保護されたプライベート](private-protected.md)   
 [保護されたフレンド](protected-friend.md)   
 [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [手順](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
