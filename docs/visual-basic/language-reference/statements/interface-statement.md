---
title: "Interface Statement (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Interface"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "interface statement [Visual Basic]"
  - "interfaces, interface definition"
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
caps.latest.revision: 26
caps.handback.revision: 26
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Interface Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

インターフェイスの名前を宣言し、インターフェイスに含まれるメンバーの定義を開始します。  
  
## 構文  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] _  
Interface name [ ( Of typelist ) ]  
    [ Inherits interfacenames ]  
    [ [ modifiers ] Property membername ]  
    [ [ modifiers ] Function membername ]  
    [ [ modifiers ] Sub membername ]  
    [ [ modifiers ] Event membername ]  
    [ [ modifiers ] Interface membername ]  
    [ [ modifiers ] Class membername ]  
    [ [ modifiers ] Structure membername ]  
End Interface  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`attributelist`|省略可能です。  「[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)」を参照してください。|  
|`accessmodifier`|省略可能です。  次のいずれかになります。<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> 「[Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。|  
|`Shadows`|省略可能です。  「[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)」を参照してください。|  
|`name`|必ず指定します。  このインターフェイスの名前です。  「[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。|  
|`Of`|省略可能です。  ジェネリック インターフェイスであることを指定します。|  
|`typelist`|[Of](../../../visual-basic/language-reference/statements/of-clause.md) キーワードを使用する場合は必ず指定します。  このインターフェイスの型パラメーターのリストを指定します。  必要に応じて、ジェネリックの `In` 修飾子や `Out` 修飾子を使用して、それぞれの型パラメーターをバリアントとして宣言できます。  「[型リスト](../../../visual-basic/language-reference/statements/type-list.md)」を参照してください。|  
|`Inherits`|省略可能です。  このインターフェイスが別のインターフェイスの属性およびメンバーを継承することを指定します。  「[Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)」を参照してください。|  
|`interfacenames`|`Inherits` ステートメントを使用する場合は必ず指定します。  このインターフェイスの派生元のインターフェイスの名前を指定します。|  
|`modifiers`|省略可能です。  定義するインターフェイス メンバーに適した修飾子を指定します。|  
|`Property`|省略可能です。  インターフェイスのメンバーであるプロパティを定義します。|  
|`Function`|省略可能です。  インターフェイスのメンバーである `Function` プロシージャを定義します。|  
|`Sub`|省略可能です。  インターフェイスのメンバーである `Sub` プロシージャを定義します。|  
|`Event`|省略可能です。  インターフェイスのメンバーであるイベントを定義します。|  
|`Interface`|省略可能です。  このインターフェイスの内部に入れ子になったインターフェイスを定義します。  入れ子になったインターフェイスの定義は、`End Interface` ステートメントで終了する必要があります。|  
|`Class`|省略可能です。  インターフェイスのメンバーであるクラスを定義します。  このクラスの定義は、`End Class` ステートメントで終了する必要があります。|  
|`Structure`|省略可能です。  インターフェイスのメンバーである構造体を定義します。  このメンバーの構造体の定義は、`End Structure` ステートメントで終了する必要があります。|  
|`membername`|インターフェイスのメンバーとして定義したプロパティ、プロシージャ、イベント、インターフェイス、クラスまたは構造体のそれぞれに必ず指定します。  メンバーの名前です。|  
|`End Interface`|`Interface` の定義を終了します。|  
  
## 解説  
 *インターフェイス*にはプロパティやプロシージャなど、クラスや構造体で実装可能なメンバーをまとめて定義します。  インターフェイスにはメンバーのシグネチャだけを定義し、内部の処理は定義しません。  
  
 クラスや構造体でインターフェイスを実装する場合は、そのインターフェイスに定義されたすべてのメンバーのコードを定義します。  最後に、アプリケーションがそのクラスまたは構造体からインスタンスを作成した時点でオブジェクトが存在し、メモリ内で実行されます。  詳細については、「[Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)」および「[Interfaces](../../../visual-basic/reference/command-line-compiler/index.md)」を参照してください。  
  
 `Interface` は、名前空間またはモジュール レベルでのみ使用できます。  つまり、インターフェイスの*宣言コンテキスト*はソース ファイル、名前空間、クラス、構造体、モジュール、またはインターフェイスのいずれかである必要があり、プロシージャまたはブロックでは宣言できません。  詳細については、「[Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 インターフェイスには既定で [Friend](../../../visual-basic/language-reference/modifiers/friend.md) のアクセス レベルが設定されます。  アクセス修飾子を使用してこれらのアクセス レベルを調整できます。  詳細については、「[Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。  
  
## 規則  
  
-   **インターフェイスの入れ子。**インターフェイスを別のインターフェイスの内部に定義できます。  外側のインターフェイスを*包含インターフェイス*と呼び、内側のインターフェイスを*入れ子になったインターフェイス*と呼びます。  
  
-   **メンバーの宣言。**プロパティまたはプロシージャをインターフェイスのメンバーとして宣言する場合は、その*シグネチャ*だけを定義します。  シグネチャには要素の種類 \(プロパティまたはプロシージャ\)、パラメーターとその型、および戻り値の型が含まれます。  このため、メンバーの定義にはコードを 1 行だけ使用し、`End Function` や `End Property` などの終了ステートメントをインターフェイスに定義することはできません。  
  
     これに対し、列挙体や構造体、または入れ子になったクラスやインターフェイスを定義するときには、そのデータ メンバーを含める必要があります。  
  
-   **メンバー修飾子。**モジュールのメンバーを定義するときには、アクセス修飾子を使用できません。また、[Overloads](../../../visual-basic/language-reference/modifiers/overloads.md) を除くどのプロシージャ修飾子 \([Shared](../../../visual-basic/language-reference/modifiers/shared.md) など\) も指定できません。  どのメンバーでも、[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) を使って宣言できます。また、プロパティを定義するときには、[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) や [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md) の他に [Default](../../../visual-basic/language-reference/modifiers/default.md) を使用できます。  
  
-   **継承。**インターフェイスに [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md) を使用して、1 つ以上の基本インターフェイスを指定できます。  2 つのインターフェイスに同じ名前のメンバーが定義されている場合でも、その 2 つを継承できます。  その場合、実装コードでは、実装するメンバーを指すために名前の修飾を使う必要があります。  
  
     インターフェイスには、それ自身より厳しいアクセス レベルを持つ別のインターフェイスを継承することはできません。  たとえば、`Public` インターフェイスは `Friend` インターフェイスを継承できません。  
  
     インターフェイスは、自分の中に入れ子になっているインターフェイスを継承できません。  
  
-   **実装。**クラスに [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) ステートメントを使ってインターフェイスを実装するときには、そのインターフェイスに定義されているすべてのメンバーを実装する必要があります。  さらに、実装先のコードでは、各シグネチャがインターフェイスに定義された対応するシグネチャと完全に一致していることが必要です。  ただし、実装先のコードでのメンバーの名前は、インターフェイスに定義されたメンバー名と同じでなくてもかまいません。  
  
     クラスにプロシージャを実装するとき、そのプロシージャに `Shared` を指定できません。  
  
-   **既定のプロパティ。**インターフェイスには、1 つまでのプロパティを*既定のプロパティ*として指定できます。既定のプロパティは、プロパティ名を使用せずに参照できます。  既定のプロパティを指定するには、[Default](../../../visual-basic/language-reference/modifiers/default.md) 修飾子を使って宣言します。  
  
     つまり、インターフェイスに既定のプロパティを定義できるのは、インターフェイスが何も継承していない場合だけです。  
  
## \[動作\]  
  
-   **アクセス レベル。**すべてのインターフェイス メンバーは、暗黙的に [Public](../../../visual-basic/language-reference/modifiers/public.md) アクセスになります。  メンバーを定義するとき、アクセス修飾子は使用できません。  ただし、インターフェイスを実装するクラスで、実装された各メンバーに対してアクセス レベルを宣言できます。  
  
     クラスのインスタンスを変数に割り当てる場合、そのメンバーのアクセス レベルは、変数のデータ型が基のインターフェイスかそれとも実装先のクラスかによって変わります。  次に例を示します。  
  
     [!code-vb[VbVbalrStatements#39](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/interface-statement_1.vb)]  
  
     `varAsInterface` を指定してクラス メンバーにアクセスする場合は、すべてのメンバーがパブリック アクセスになります。  ただし、`varAsClass` を指定してメンバーにアクセスする場合、`Sub` プロシージャである `doSomething` はプライベート アクセスになります。  
  
-   **スコープ。**インターフェイスのスコープは名前空間、クラス、構造体、またはモジュール全体です。  
  
     インターフェイスのすべてのメンバーのスコープは、インターフェイス全体になります。  
  
-   **有効期間。**インターフェイスおよびそのメンバーには、有効期間がありません。  クラスがインターフェイスを実装し、そのクラスのインスタンスとしてオブジェクトが作成されると、そのオブジェクトが有効期間 \(オブジェクトを実行しているアプリケーションが終了するまで\) を持ちます。  詳細については、「[Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)」の「有効期間」を参照してください。  
  
## 使用例  
 次の例は `Interface` ステートメントを使用して、`thisInterface` という名前のインターフェイスを定義します。これを実装するには、`Property` ステートメントと `Function` ステートメントを使用する必要があります。  
  
 [!code-vb[VbVbalrStatements#40](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/interface-statement_2.vb)]  
  
 インターフェイス内で `Property` ステートメントと `Function` ステートメントで開始されたブロックが、`End Property` と `End Function` で終了していない点に注意してください。  インターフェイスには、そのメンバーのシグネチャのみを定義します。  `Property` ブロックと `Function` ブロックの完全な定義は、`thisInterface` を実装するクラスに記述されています。  
  
## 参照  
 [Interfaces](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [ジェネリック インターフェイスの分散](../Topic/Variance%20in%20Generic%20Interfaces%20\(C%23%20and%20Visual%20Basic\).md)   
 [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)   
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)