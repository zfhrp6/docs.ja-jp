---
title: Partial (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Partial
- partial
helpviewer_keywords:
- structures [Visual Basic], partial
- classes [Visual Basic]
- partial, types [Visual Basic]
- partial, structures
- partial, classes [Visual Basic]
- classes [Visual Basic], partial
- Partial keyword [Visual Basic]
- type promotion
ms.assetid: 7adaef80-f435-46e1-970a-269fff63b448
ms.openlocfilehash: c94c3bf1a1e3e4c724f90690f52e97e8216cb9a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604615"
---
# <a name="partial-visual-basic"></a>Partial (Visual Basic)
型宣言が、型の部分定義であることを示します。  
  
 `Partial` キーワードを使用して、型の定義を複数の宣言に分割できます。 部分宣言は必要に応じていくつでも使用でき、複数のソース ファイルとして作成することもできます。 ただし、すべての宣言は同じアセンブリおよび同じ名前空間にある必要があります。  
  
> [!NOTE]
>  Visual Basic サポート*部分メソッド*、部分クラスで実装されているが一般的です。 詳細については、次を参照してください。[部分メソッド](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)と[Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`attrlist`|任意。 この型に適用される属性の一覧です。 囲む必要があります、[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)山かっこ (`< >`)。|  
|`accessmodifier`|任意。 どのようなコードから型にアクセスできるのかを指定します。 参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。|  
|`Shadows`|任意。 参照してください[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)です。|  
|`MustInherit`|任意。 参照してください[MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)です。|  
|`NotInheritable`|任意。 参照してください[NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)です。|  
|`name`|必須。 この型の名前です。 同じ型の他のすべての部分宣言で定義されている名前と一致する必要があります。|  
|`Of`|任意。 これがジェネリック型であることを指定します。 参照してください[Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)です。|  
|`typelist`|使用するかどうかは必ず[の](../../../visual-basic/language-reference/statements/of-clause.md)します。 参照してください[のリストを入力](../../../visual-basic/language-reference/statements/type-list.md)です。|  
|`Inherits`|任意。 参照してください[Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)です。|  
|`classname`|`Inherits` を使用する場合は必ず指定します。 このクラスの派生元のクラスまたはインターフェイスの名前です。|  
|`Implements`|任意。 参照してください[ステートメントを実装します](../../../visual-basic/language-reference/statements/implements-statement.md)です。|  
|`interfacenames`|`Implements` を使用する場合は必ず指定します。 この型が実装するインターフェイスの名前を指定します。|  
|`variabledeclarations`|任意。 この型の追加の変数やイベントを宣言するステートメントです。|  
|`proceduredeclarations`|任意。 この型の追加のプロシージャを宣言および定義するステートメントです。|  
|`End Class` または `End Structure`|この `Class` または `Structure` の部分定義を終了します。|  
  
## <a name="remarks"></a>コメント  
 Visual Basic では、部分クラス定義を使用して、生成されたコードとユーザーが作成したコードとを別々のソース ファイルに分離します。 たとえば、**Windows フォーム デザイナー**では、<xref:System.Windows.Forms.Form> などのコントロールに部分クラスを定義します。 これらのコントロールでは、生成されたコードを変更しないでください。  
  
 部分型を作成する際、クラス、構造体、インターフェイス、およびモジュールの作成に関するすべての規則 (修飾子の利用法や継承に関する規則など) が適用されます。  
  
## <a name="best-practices"></a>ベスト プラクティス  
  
-   通常の状況では、1 つの型の開発を複数の宣言に分割しないようにします。 したがって、ほとんどの場合は、`Partial` キーワードは必要ありません。  
  
-   読みやすくするために、型の部分宣言にはすべて、`Partial` キーワードを含めます。 コンパイラでは、最大 1 つの部分宣言でキーワードを省略できますが、複数の部分宣言で省略するとエラーになります。  
  
## <a name="behavior"></a>動作  
  
-   **宣言の和集合です。** コンパイラは型を、すべての部分宣言の共用体として扱います。 すべての部分定義で使用されているすべての修飾子は、型全体に適用され、すべての部分定義のすべてのメンバーは、型全体で使用できます。  
  
-   **型の昇格のモジュール内の部分型は許可されていません。** 部分定義がモジュール内にある場合、その型の上位変換は自動的に失敗します。 この場合、一連の部分定義によって、予期しない結果になったり、場合によってはコンパイラ エラーが発生することがあります。 詳細については、次を参照してください。[型の上位変換](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)です。  
  
     コンパイラは、完全修飾されたパスがまったく同じ場合にのみ、部分定義をマージします。  
  
 キーワード `Partial` は次のコンテキストで使用できます。  
  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## <a name="example"></a>例  
 次の例では、クラス `sampleClass` の定義を 2 つの宣言に分割し、それぞれ別の `Sub` プロシージャを定義します。  
  
 [!code-vb[VbVbalrKeywords#3](../../../visual-basic/language-reference/codesnippet/VisualBasic/partial_1.vb)]  
  
 この例にある 2 つの部分定義は、同じソース ファイル内にあっても、別々のソース ファイル内にあってもかまいません。  
  
## <a name="see-also"></a>関連項目  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [型の上位変換](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [部分メソッド](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
