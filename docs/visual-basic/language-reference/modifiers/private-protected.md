---
title: Private Protected (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: 23fd6583182a1fee544d0458dc3fc390aed86b9f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="private-protected-visual-basic"></a>Private Protected (Visual Basic)

`Private Protected`キーワードの組み合わせは、メンバー アクセス修飾子。 A`Private Protected`メンバーがアクセスできるは、外側のクラスから派生した型およびその外側のクラスのすべてのメンバーでは、含んでいるアセンブリ内にある場合にのみです。 

指定できます`Private Protected`クラスのメンバーにのみ適用することはできません`Private Protected`構造体のメンバーにため、構造体は継承できません。

`Private Protected`アクセス修飾子は Visual Basic 15.5 以降でサポートされています。 これを使用するには、Visual Basic プロジェクト (*.vbproj) ファイルに次の要素を追加できます。 Visual Basic 15.5 として時間またはそれ以降は、システムにインストールされているが、最新バージョンの Visual Basic コンパイラでサポートされているすべての言語機能を利用することができます。

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

> [!NOTE]
> Visual Studio で、の F1 ヘルプ`private protected`いずれかのヘルプを提供[プライベート](private.md)または[保護](protected.md)です。 IDE では、複合語ではなく、カーソルの下にある 1 つのトークンを取得します。

## <a name="rules"></a>ルール

- **宣言コンテキスト。** 使用することができます`Private Protected`クラス レベルでのみです。 つまりの宣言コンテキスト、`Protected`要素がクラスである必要があり、ソース ファイル、名前空間、インターフェイス、モジュール、構造体、またはプロシージャにすることはできません。

## <a name="behavior"></a>動作

- **アクセス レベル。** クラスのすべてのコードは、その要素にアクセスできます。 基本クラスから派生し、同じアセンブリに含まれる任意のクラス内のコードはすべてにアクセスできます、`Private Protected`基底クラスの要素。 基本クラスから派生し、別のアセンブリに含まれるクラスにコードが、基底クラスにアクセスできませんただし、`Private Protected`要素。

- **アクセス修飾子。** アクセス レベルを指定するキーワードと呼ばれる*アクセス修飾子*です。 アクセス修飾子の比較を参照してください。 [Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。
  
 `Private Protected` 修飾子は、次のコンテキストで使用できます。  
  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)の入れ子になったクラス  
  
 [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)デリゲートのクラスで入れ子になった  
  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)eumeration のクラスで入れ子になった 
  
 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)インターフェイスのクラスで入れ子になった 
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [ステートメントを構造体](../../../visual-basic/language-reference/statements/structure-statement.md)クラスで入れ子になった構造体 
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目

[Public](../../../visual-basic/language-reference/modifiers/public.md)  
[Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
[Friend](friend.md)   
[Private](../../../visual-basic/language-reference/modifiers/private.md)  
[保護されたフレンド](./protected-friend.md)   
[Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[手順](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
