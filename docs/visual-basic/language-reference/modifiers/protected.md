---
title: Protected (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: 5f279ed0a33840bb1f2321c17a1ffba412837c07
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="protected-visual-basic"></a>Protected (Visual Basic)
1 つまたは複数のプログラミング要素が宣言されていることを指定するメンバーのアクセス修飾子は、独自のクラス内または派生クラスからからのみアクセスできます。  
  
## <a name="remarks"></a>コメント  
 クラスで宣言されたプログラミング要素が機密データまたは制限付きのコードを格納することもありますし、要素へのアクセスを制限します。 ただし、クラスが継承可能、派生クラスの階層が予想される場合は、これらの派生クラスのデータまたはコードにアクセスする必要があります。 このような場合は、要素は、基本クラスとすべての派生クラスの両方にアクセスできるようにします。 このような要素へのアクセスを制限するために宣言できます`Protected`です。  

> [!NOTE]
> `Protected`アクセス修飾子は、その他の 2 つの修飾子と組み合わせることができます。
> - [Protected Friend](protected-friend.md)修飾子は、クラス メンバーをそのクラスの派生クラスからそのクラスが定義されている同じアセンブリ内からアクセスできません。 
> - [プライベート保護](private-protected.md)修飾子により、クラス メンバー アクセス、含んでいるアセンブリ内でのみ、派生型です。
  
## <a name="rules"></a>ルール  
  
-   **宣言コンテキスト。** 使用することができます`Protected`クラス レベルでのみです。 つまりの宣言コンテキスト、`Protected`要素がクラスである必要があり、ソース ファイル、名前空間、インターフェイス、モジュール、構造体、またはプロシージャにすることはできません。  

## <a name="behavior"></a>動作  
  
-   **アクセス レベル。** クラスのすべてのコードは、その要素にアクセスできます。 基本クラスから派生したクラス内のコードはすべてにアクセスできる、`Protected`基底クラスの要素。 これは、派生のすべてのジェネレーションの場合は true です。 つまり、クラスにアクセスできるように`Protected`と基本クラスの基底クラスの要素。  
  
     保護されたアクセスは、スーパー セットであるかのフレンド アクセスのサブセットではありません。  
  
-   **アクセス修飾子。** アクセス レベルを指定するキーワードと呼ばれる*アクセス修飾子*です。 アクセス修飾子の比較を参照してください。 [Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。  
  
 `Protected` 修飾子は、次のコンテキストで使用できます。  
  
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
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [保護されたプライベート](private-protected.md)   
 [保護されたフレンド](protected-friend.md)   
 [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [手順](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
