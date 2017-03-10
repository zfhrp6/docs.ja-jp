---
title: "Class Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Class"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "class modules"
  - "Class statement"
  - "classes [Visual Basic], fields"
  - "fields, of classes"
  - "class types, class statements"
  - "classes [Visual Basic], creating"
  - "classes [Visual Basic], data members"
  - "data members, of classes"
ms.assetid: f2664f38-eb5a-4d4b-a374-1d041521fb6c
caps.latest.revision: 29
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 29
---
# Class Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

クラスの名前を宣言し、そのクラスを構成する変数、プロパティ、イベント、およびプロシージャの定義を示します。  
  
## 構文  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] [ Partial ] _  
Class name [ ( Of typelist ) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ statements ]  
End Class  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`attributelist`|省略可能です。  「[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)」を参照してください。|  
|`accessmodifier`|省略可能です。  次のいずれかになります。<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> 「[Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。|  
|`Shadows`|省略可能です。  「[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)」を参照してください。|  
|`MustInherit`|省略可能です。  「[MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)」を参照してください。|  
|`NotInheritable`|省略可能です。  「[NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)」を参照してください。|  
|`Partial`|省略可能です。  クラスの部分定義であることを示します。  「[Partial](../../../visual-basic/language-reference/modifiers/partial.md)」を参照してください。|  
|`name`|必ず指定します。  このクラスの名前です。  「[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。|  
|`Of`|省略可能です。  これがジェネリック クラスであることを指定します。|  
|`typelist`|[Of](../../../visual-basic/language-reference/statements/of-clause.md) キーワードを使用する場合は必ず指定します。  このクラスの型パラメーターの一覧を指定します。  「[型リスト](../../../visual-basic/language-reference/statements/type-list.md)」を参照してください。|  
|`Inherits`|省略可能です。  このクラスが他のクラスのメンバーを継承することを示します。  「[Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)」を参照してください。|  
|`classname`|`Inherits` ステートメントを使用する場合は必ず指定します。  このクラスの派生元となるクラスの名前です。|  
|`Implements`|省略可能です。  このクラスが、1 つ以上のインターフェイスのメンバーを実装していることを示します。  「[Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md)」を参照してください。|  
|`interfacenames`|`Implements` ステートメントを使用する場合は必ず指定します。  このクラスが実装するインターフェイスの名前を指定します。|  
|`statements`|省略可能です。  このクラスのメンバーを定義するステートメントを指定します。|  
|`End Class`|必ず指定します。  `Class` 定義を終了します。|  
  
## 解説  
 `Class` ステートメントは新しいデータ型を定義します。  *クラス*はオブジェクト指向プログラミング \(OOP: Object\-Oriented Programming\) の基本的なビルド ブロックです。  詳細については、「[Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)」を参照してください。  
  
 `Class` は、名前空間またはモジュール レベルでのみ使用できます。  つまり、クラスの*宣言コンテキスト*は、ソース ファイル、名前空間、クラス、構造体、モジュール、またはインターフェイスのいずれかである必要があり、プロシージャまたはブロックでは宣言できません。  詳細については、「[Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 クラスの各インスタンスは、他のインスタンスからは独立した有効期間を持ちます。  インスタンスの有効期間は、[New Operator](../../../visual-basic/language-reference/operators/new-operator.md) 句または <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A> などの関数で作成されたときに開始します。  インスタンスを参照している変数がすべて [Nothing](../../../visual-basic/language-reference/nothing.md) に設定されるか、他のクラスのインスタンスに設定されると、インスタンスの有効期間は終了します。  
  
 既定では、クラスのアクセス レベルは [Friend](../../../visual-basic/language-reference/modifiers/friend.md) です。  アクセス修飾子を使用してこれらのアクセス レベルを調整できます。  詳細については、「[Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。  
  
## 規則  
  
-   **入れ子。**クラス内に別のクラスを定義できます。  外側のクラスは*包含クラス*、内側のクラスは*入れ子クラス*と呼ばれます。  
  
-   **継承。**クラスが [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)を使用している場合は、1 つの基本クラスまたはインターフェイスのみを指定できます。  複数の要素を継承することはできません。  
  
     自分よりもアクセス レベルの厳しいクラスは継承できません。  たとえば、`Public` クラスは `Friend` クラスを継承できません。  
  
     中に入れ子になったクラスは継承できません。  
  
-   **実装。**クラスが [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md)を使用している場合は、`interfacenames` に指定したすべてのインターフェイスで定義されているメンバーをすべて実装する必要があります。  ただし、基本クラスのメンバーを再実装する必要はありません。  詳細については、「[Implements](../../../visual-basic/language-reference/statements/implements-clause.md)」の「再実装」を参照してください。  
  
-   **既定のプロパティ。**クラス内の最大 1 つのプロパティを*既定のプロパティ*として指定できます。  詳細については、「[Default](../../../visual-basic/language-reference/modifiers/default.md)」を参照してください。  
  
## \[動作\]  
  
-   **アクセス レベル。**クラス内では、それぞれのメンバーにアクセス レベルを宣言できます。  変数と定数を除くクラス メンバーは既定で [Public](../../../visual-basic/language-reference/modifiers/public.md) アクセスになります。変数と定数は既定で [Private](../../../visual-basic/language-reference/modifiers/private.md) アクセスになります。  クラスのアクセス レベルの方がメンバーのアクセス レベルよりも厳しいときは、クラスのアクセス レベルが優先されます。  
  
-   **スコープ。**クラスのスコープは、そのクラスを含んでいる名前空間、クラス、構造体、またはモジュールになります。  
  
     すべてのクラス メンバーのスコープは、クラス全体になります。  
  
     **有効期間。**Visual Basic は静的クラスをサポートしません。  静的クラスと同等の機能はモジュールで実現されます。  詳細については、「[Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)」を参照してください。  
  
     クラス メンバーの有効期間は、宣言された方法と場所によって左右されます。  詳細については、「[Lifetime in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)」を参照してください。  
  
-   **修飾。**クラス外部のコードがメンバーにアクセスするときには、メンバー名をクラス名で修飾する必要があります。  
  
     入れ子クラスの内部のコードがプログラミング要素に対する非修飾参照を行った場合、Visual Basic は目的の要素をまず入れ子クラス内で検索し、次にそのコンテナー クラス内で検索し、同様にして一番外側のコンテナー要素まで検索します。  
  
## クラスとモジュール  
 これらの要素はよく似ていますが、重要な相違点がいくつかあります。  
  
-   **用語。**以前のバージョンの Visual Basic には、*クラス モジュール* \(.cls ファイル\) と*標準モジュール* \(.bas ファイル\) という 2 種類のモジュールがありました。  現在のバージョンでは、これらをそれぞれ*クラス*と*モジュール*と呼びます。  
  
-   **共有メンバー。**クラスのメンバーを共有メンバーにするかインスタンス メンバーにするかを制御できます。  
  
-   **オブジェクト指向。**クラスはオブジェクト指向ですが、モジュールはオブジェクト指向ではありません。  クラスについては 1 つ以上のインスタンスを作成できます。  詳細については、「[Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)」を参照してください。  
  
## 使用例  
 次の例では、`Class` ステートメントを使用してクラスといくつかのメンバーを定義しています。  
  
 [!code-vb[VbVbalrStatements#62](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/class-statement_1.vb)]  
  
## 参照  
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Structures and Classes](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)   
 [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)   
 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [方法 : ジェネリック クラスを使用する](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)