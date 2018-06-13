---
title: Friend (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
ms.openlocfilehash: d906fc8ada19f22059da44acbd76dd07dacd4801
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234590"
---
# <a name="friend-visual-basic"></a>Friend (Visual Basic)
1 つまたは複数の宣言されたプログラミング要素がその宣言を含むアセンブリ内からのみアクセスできることを指定します。  
  
## <a name="remarks"></a>コメント  
 多くの場合、クラスと構造体を宣言しているコンポーネントがだけでなく、アセンブリ全体で使用するなどの要素をプログラミングできるようにします。 ただしに (たとえば、アプリケーションは商標で守ら) 場合、アセンブリの外部コードによってアクセスできるようにする必要があります。 この方法で要素へのアクセスを制限する場合は、使用して宣言できます、`Friend`修飾子です。  
  
 その他のクラス、構造体、およびコンパイルされますが、同じモジュールのコード アセンブリはすべてにアクセスできる、`Friend`そのアセンブリ内の要素。  
  
 `Friend` アクセスは、アプリケーションのプログラミング要素に望ましいレベルでは多くの場合と`Friend`インターフェイス、モジュール、クラスまたは構造のレベルで既定のアクセス。  
  
 使用することができます`Friend`モジュール、インターフェイス、または名前空間レベルでのみです。 したがって、宣言コンテキスト、`Friend`ソース ファイル、名前空間、インターフェイス、モジュール、クラスまたは構造体を要素として使用することがあります。 プロシージャをすることはできません。  

> [!NOTE]
> 使用することも、 [Protected Friend](protected-friend.md)アクセス修飾子は、クラス メンバーをそのクラスの派生クラスからそのクラスが定義されている同じアセンブリ内からアクセスできるようになります。 使用して、同じアセンブリ内の派生クラスからそのクラス内からのメンバーへのアクセスを制限する、[プライベート保護](private-protected.md)アクセス修飾子。

 比較について`Friend`と、その他のアクセス修飾子を参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。  
  
> [!NOTE]
>  別のアセンブリがで許可されているすべての種類およびとマークされているメンバーにアクセスするアセンブリを指定することができます`Friend`です。 詳細については、[Friend アセンブリ](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)に関するページを参照してください。  
  
## <a name="example"></a>例  
 次のクラスは、`Friend`特定のメンバーにアクセスする同じアセンブリ内の他のプログラミング要素を許可する修飾子です。  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]  
  
## <a name="usage"></a>使用法  
 使用することができます、`Friend`これらのコンテキストで修飾子。  
  
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
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [保護されたプライベート](./private-protected.md)   
 [保護されたフレンド](./protected-friend.md)   
 [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [手順](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
