---
title: Private (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 40b64b8d2b6306d458b7a9cc657c5b7dc4270eb2
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234556"
---
# <a name="private-visual-basic"></a>Private (Visual Basic)
1 つまたは複数の宣言されたプログラミング要素がすべて含まれている型内からなど、宣言のコンテキストからのみアクセスできることを指定します。  
  
## <a name="remarks"></a>コメント  
 プログラミング要素は、独自の機能または機密データを含む、通常する場合、できるだけ厳密にへのアクセスを制限します。 最大の制限は、モジュール、クラス、またはそれへのアクセスを定義する構造体のみを許可することで実現します。 この方法で要素へのアクセスを制限するために宣言できます`Private`です。  

> [!NOTE]
> 使用することも、[プライベート保護](private-protected.md)メンバーにそのクラス内、および、含んでいるアセンブリにある派生クラスからアクセスできるよう、アクセス修飾子。

## <a name="rules"></a>ルール  

-   **宣言コンテキスト。** `Private` は、モジュール レベルでのみ使用できます。 つまりの宣言コンテキスト、`Private`要素は、モジュール、クラス、または構造体にある必要があるあり、ソース ファイル、名前空間、インターフェイス、またはプロシージャにすることはできません。  
  
## <a name="behavior"></a>動作  
  
-   **アクセス レベル。** 宣言コンテキスト内のすべてのコードがアクセスできる、`Private`要素。 これには、入れ子になったクラスまたは列挙型の代入式などの包含の種類の中でコードが含まれます。 宣言コンテキスト以外のコードからもアクセスできない、`Private`要素。  
  
-   **アクセス修飾子。** アクセス レベルを指定するキーワードと呼ばれる*アクセス修飾子*です。 アクセス修飾子の比較を参照してください。 [Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。  
  
 `Private` 修飾子は、次のコンテキストで使用できます。  
  
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
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [保護されたプライベート](./private-protected.md)   
 [Protected Friend](./protected-friend.md)[Visual Basic でのレベルのアクセス    ](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [手順](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
