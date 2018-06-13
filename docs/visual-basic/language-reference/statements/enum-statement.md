---
title: Enum ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: 7cac4d5bde9ec617a1877a0605dc6dbab67ddf7f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234017"
---
# <a name="enum-statement-visual-basic"></a>Enum ステートメント (Visual Basic)
列挙体を宣言し、そのメンバーの値を定義します。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a>指定項目  
  
-   `attributelist`  
  
     任意。 この列挙体に適用される属性の一覧です。 囲む必要があります、[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)山かっこ ("`<`「と」`>`") です。  
  
     <xref:System.FlagsAttribute>属性は、列挙型のインスタンスの値が、複数の列挙型メンバーを含めることができ、各メンバーが、列挙値のビット フィールドを表すことを示します。  
  
-   `accessmodifier`  
  
     任意。 この列挙体にアクセスできるコードを指定します。 次のいずれかの値を指定します。  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [保護されたフレンド](../../language-reference/modifiers/protected-friend.md)
    
    - [保護されたプライベート](../../language-reference/modifiers/private-protected.md)

-   `Shadows`  
  
     任意。 この列挙体を宣言し、同じ名前を持つプログラミング要素、または基底クラスのオーバー ロードされる要素のセットを非表示にすることを指定します。 指定できます[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)のみ列挙体自体ではなく、メンバーのいずれか。  
  
-   `enumerationname`  
  
     必須。 列挙体の名前です。 有効な名前については、次を参照してください。[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。  
  
-   `datatype`  
  
     任意。 列挙体およびそのすべてのメンバーのデータ型。  
  
-   `memberlist`  
  
     必須。 このステートメントで宣言されているメンバー定数の一覧です。 複数のメンバーは、個々 のソース コード行に表示されます。  
  
     各`member`が次の構文とパーツ。 `[<attribute list>] member name [ = initializer ]`  
  
    |パーツ|説明|  
    |---|---|  
    |`membername`|必須。 このメンバーの名前です。|  
    |`initializer`|任意。 式がコンパイル時に評価され、このメンバーに割り当てられているです。|  
  
-   `End` `Enum`  
  
     `Enum` ブロックを終了します。  
  
## <a name="remarks"></a>コメント  
 互いに論理的に関連付けられている不変の値のセットがあれば、それらを一緒に列挙で定義できます。 これは、列挙体およびそのメンバーは、その値よりも覚えやすくにわかりやすい名前を提供します。 多くの場所で列挙型のメンバーを使用して、コードでことができますし、します。  
  
 列挙体を使用する利点は次のとおりです。  
  
-   転置または番号の入力ミスによって発生したエラーが減少します。  
  
-   将来の値を変更するのには便利です。  
  
-   によりコードを読みやすくする可能性は低くなりますエラーが発生することを意味します。  
  
-   前方の互換性を確保します。 列挙体を使用する場合、コードが後で、メンバー名に対応する値が変更された場合は失敗する可能性は低くします。  
  
 列挙体は、名前、基のデータ型およびメンバーのセットがします。 各メンバーは、定数を表します。  
  
 クラス、構造体、モジュール、またはインターフェイス レベルでは、プロシージャの外部で宣言された列挙型は、*メンバー列挙*です。 これは、クラス、構造体、モジュール、またはそれを宣言したインターフェイスのメンバーです。  
  
 列挙体のメンバーは、クラス、構造体、モジュール、またはインターフェイス内の任意の場所からアクセスできます。 コードをクラスの外部構造体、またはモジュール修飾する必要がありますそのクラス、構造体、モジュールの名前を持つメンバーの列挙体の名前。 追加することによって完全修飾名を使用する必要を避けることができます、 [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)ステートメントをソース ファイルにします。  
  
 任意のクラス、構造体、モジュール、またはインターフェイスの外部の名前空間レベルで宣言された列挙型が表示される名前空間のメンバーであります。  
  
 *宣言コンテキスト*列挙体のソース ファイル、名前空間、クラス、構造体、モジュール、またはインターフェイスである必要があります、プロシージャをすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 属性を適用できますがそのメンバーに、全体として列挙型には個別にします。 属性は、アセンブリのメタデータに情報を提供します。  
  
## <a name="data-type"></a>データの種類  
 `Enum`ステートメントは、列挙型のデータ型を宣言できます。 各メンバーは、列挙型のデータ型を取得します。 指定できます`Byte`、 `Integer`、 `Long`、 `SByte`、 `Short`、 `UInteger`、 `ULong`、または`UShort`です。  
  
 指定しない場合`datatype`列挙体の各メンバーのデータ型を受け取り、`initializer`です。 両方を指定する場合`datatype`と`initializer`のデータ型`initializer`に変換できる必要があります`datatype`です。 どちらの場合`datatype`も`initializer`が含まれているデータ型の既定値は`Integer`します。  
  
## <a name="initializing-members"></a>メンバーの初期化  
 `Enum`ステートメントで選択したメンバーの内容を初期化できる`memberlist`です。 使用する`initializer`をメンバーに割り当てられる式を指定します。  
  
 指定しない場合`initializer`のメンバーは、Visual Basic 初期化をゼロにするか (最初である場合`member`で`memberlist`)、またはその直前の場合よりも 1 だけ大きい数値の値に`member`です。  
  
 それぞれに指定する式`initializer`リテラル、既に定義されているその他の定数と列挙型のメンバーは既に定義されている、この列挙体のメンバーの組み合わせにすることができます。 算術演算子および論理演算子を使用すると、このような要素を結合します。  
  
 変数または関数を使用することはできません`initializer`です。 変換キーワードなどを使用するただし、`CByte`と`CShort`です。 使用することも`AscW`定数で呼び出す場合は、`String`または`Char`引数、コンパイル時に評価できるためです。  
  
 列挙体には、浮動小数点値を持つことはできません。 メンバーが浮動小数点値が割り当てられている場合と`Option Strict`on に設定する、コンパイラ エラーが発生します。 場合`Option Strict`に値が自動的に変換がオフ、`Enum`型です。  
  
 メンバーの値は、基になるデータ型の許容範囲を超える場合、または基になるデータ型で許容される最大値の任意のメンバーを初期化する場合は、コンパイラはエラーを報告します。  
  
## <a name="modifiers"></a>修飾子  
 クラス、構造体、モジュール、およびインターフェイス メンバーの列挙体既定でパブリック アクセスです。 アクセス修飾子を使用してこれらのアクセス レベルを調整できます。 Namespace フレンド アクセスを既定値の列挙型をメンバーです。 パブリックではプライベートまたはプロテクト メンバーのアクセス レベルを調整することができます。 詳細については、次を参照してください。 [Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。  
  
 すべての列挙体メンバーは、パブリック アクセスを持ち、それらのアクセス修飾子を使用することはできません。 ただし、列挙体自体にさらに制限されたアクセス レベルがある場合は、指定した列挙体のアクセス レベルが優先されます。  
  
 既定では、すべての列挙体は、型とそのフィールドは定数です。 したがって、 `Shared`、 `Static`、および`ReadOnly`列挙型またはそのメンバーを宣言するときに、キーワードを使用できません。  
  
## <a name="assigning-multiple-values"></a>複数の値を割り当てる  
 通常、列挙体は、相互に排他的な値を表します。 含めることによって、<xref:System.FlagsAttribute>属性、`Enum`宣言、割り当てることができます代わりに複数の値、列挙型のインスタンスにします。 <xref:System.FlagsAttribute>属性は、列挙体をビット フィールド、つまりフラグのセットとして扱われることを指定します。 いい*ビット*列挙体です。  
  
 使用して列挙体を宣言する場合、<xref:System.FlagsAttribute>属性、ことをお勧めの値は 2、1、2、4、8、16、およびの累乗を使用することです。 また、値が 0 のメンバーの名前にする"None"ことをお勧めします。 その他のガイドラインについては、次を参照してください。<xref:System.FlagsAttribute>と<xref:System.Enum>です。  
  
## <a name="example"></a>例  
 次の例を使用する方法を示しています、`Enum`ステートメントです。 メンバーと呼ばれる注`EggSizeEnum.Medium`とではなく`Medium`です。  
  
 [!code-vb[VbEnumsTask#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]  
  
## <a name="example"></a>例  
 次の例では、メソッドが範囲外、`Egg`クラスです。 したがって、`EggSizeEnum`として完全修飾されて`Egg.EggSizeEnum`です。  
  
 [!code-vb[VbEnumsTask#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]  
  
## <a name="example"></a>例  
 次の例では、`Enum`を関連するセットを定義するステートメントが定数値をという名前です。 この例で値は、色、データベースのデータ エントリ フォームをデザインすることもできます。  
  
 [!code-vb[VbEnumsTask#30](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]  
  
## <a name="example"></a>例  
 次の例では、正と負の値の両方の番号を含む値を示します。  
  
 [!code-vb[VbEnumsTask#31](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]  
  
## <a name="example"></a>例  
 次の例で、`As`句が指定に使用される、`datatype`列挙体の。  
  
 [!code-vb[VbEnumsTask#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]  
  
## <a name="example"></a>例  
 次の例では、ビットごとの列挙を使用する方法を示します。 複数の値は、ビットごとの列挙体のインスタンスに割り当てることができます。 `Enum`宣言が含まれる、<xref:System.FlagsAttribute>属性は、列挙体をフラグのセットとして扱えることを示します。  
  
 [!code-vb[VbEnumsTask#61](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]  
  
## <a name="example"></a>例  
 次の例は、列挙型を反復処理します。 使用して、 <xref:System.Enum.GetNames%2A> 、列挙メンバー名の配列を取得する方法と<xref:System.Enum.GetValues%2A>メンバー値の配列を取得します。  
  
 [!code-vb[VbEnumsTask#51](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Enum>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [暗黙の型変換と明示的な型変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [定数と列挙体](../../../visual-basic/language-reference/constants-and-enumerations.md)
