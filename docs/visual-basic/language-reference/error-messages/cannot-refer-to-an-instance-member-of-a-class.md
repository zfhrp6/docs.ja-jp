---
title: クラスの明示的なインスタンスを指定しないで、共有メソッドまたは共有メンバー初期化子内からクラスのインスタンス メンバーへ参照することはできません。
ms.date: 07/20/2015
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
ms.openlocfilehash: 368539ed24d9819c8d1ddbbb9e3e0dff21d27c32
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590184"
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a>クラスの明示的なインスタンスを指定しないで、共有メソッドまたは共有メンバー初期化子内からクラスのインスタンス メンバーへ参照することはできません。
クラスを共有プロシージャ内での非共有メンバーを参照しようとしました。 次の例では、このような状況を示します。  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 前の例では、代入ステートメントで`x = 10`でこのエラー メッセージが生成されます。 これは、ため、インスタンス変数にアクセスしようとして、共有プロシージャです。  
  
 変数`x`として宣言されていないため、インスタンス メンバーは、 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)です。 クラスの各インスタンス`sample`独自の個別の変数が含まれる`x`です。 1 つのインスタンスを設定またはの値を変更するときに`x`の値は影響を与えない`x`他のインスタンス。  
  
 ただし、プロシージャ`setX`は`Shared`クラスのすべてのインスタンス間で`sample`です。 つまり、クラスのインスタンスのいずれかに関連付けられていないことが、個々 のインスタンスから独立して動作ではなくです。 特定のインスタンスとの接続があるないため`setX`インスタンス変数にアクセスできません。 のみ動作する必要があります、`Shared`変数。 ときに`setX`その新しい値が、クラスのすべてのインスタンスで使用できる、共有変数の値を変更または設定します。  
  
 **エラー ID:** BC30369  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  クラスのすべてのインスタンス間で共有またはインスタンスごとに保持するメンバーにするかどうかを決定します。  
  
2.  すべてのインスタンス間で共有できるメンバーの 1 つのコピーを実行する場合に、追加、`Shared`メンバーの宣言するキーワードです。 保持、`Shared`プロシージャ宣言でキーワード。  
  
3.  各インスタンスに、メンバーの個別コピーする場合を指定しない`Shared`メンバー宣言にします。 削除、`Shared`プロシージャ宣言からキーワード。  
  
## <a name="see-also"></a>関連項目  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
