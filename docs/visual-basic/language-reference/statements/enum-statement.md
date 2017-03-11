---
title: "Enum ステートメント (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Enum"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "列挙定数"
  - "Enum ステートメント"
  - "Private キーワード、Enum ステートメント"
  - "Enum ステートメントの public キーワード"
  - "変数 [Visual Basic] 列挙型"
  - "列挙定数"
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
caps.latest.revision: 44
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 44
---
# Enum ステートメント (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

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
  
     省略可能です。 この列挙体に適用される属性の一覧です。 囲む必要があります、 [属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md) 山かっこで ("`<`「と」`>`") です。  
  
      <xref:System.FlagsAttribute> 属性は、列挙体のインスタンスの値が、複数の列挙型メンバーを含めることができ、各メンバーが列挙値のビット フィールドを表すことを示します。  
  
-   `accessmodifier`  
  
     省略可能です。 この列挙体にアクセスできるコードを指定します。 次のいずれかの値を指定します。  
  
    -   [パブリック](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [保護されています。](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [プライベート](../../../visual-basic/language-reference/modifiers/private.md)  
  
     指定できます `Protected``Friend` 列挙型のクラスを派生クラスでは、または同じアセンブリ内のコードからのアクセスを許可するようにします。  
  
-   `Shadows`  
  
     省略可能です。 この列挙体を宣言し、同じ名前を持つプログラミング要素、または基底クラスのオーバー ロードされた要素のセットを非表示にことを指定します。 指定できます [シャドウ](../../../visual-basic/language-reference/modifiers/shadows.md) のみ列挙体自体ではなく、メンバーのいずれかです。  
  
-   `enumerationname`  
  
     必須です。 列挙体の名前です。 有効な名前については、次を参照してください。 [宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。  
  
-   `datatype`  
  
     省略可能です。 列挙体およびそのすべてのメンバーのデータ型。  
  
-   `memberlist`  
  
     必須です。 このステートメントで宣言されているメンバー定数の一覧です。 複数のメンバーは、個々 のソース コード行に表示されます。  
  
     各 `member` が次の構文とパーツ。 `[<attribute list>] member name [ = initializer ]`  
  
    |||  
    |-|-|  
    |パーツ|説明|  
    |`membername`|必須です。 このメンバーの名前です。|  
    |`initializer`|省略可能です。 このメンバーに割り当てられているされ、コンパイル時に評価される式です。|  
  
-   `End` `Enum`  
  
     `Enum` ブロックを終了します。  
  
## <a name="remarks"></a>コメント  
 互いに論理的に関連付けられている不変の値のセットがあれば、列挙体で一緒に定義できます。 これは、列挙体とそのメンバーでは、それらの値よりも覚えやすく、わかりやすい名前を提供します。 多くの場所で列挙型のメンバーを使用して、コードでことができますし、します。  
  
 列挙体を使用する利点は次のとおりです。  
  
-   置き換えや数値の入力ミスによって発生したエラーを削減します。  
  
-   値は、将来変更を簡単にできます。  
  
-   コードを読みやすくする可能性は低くなりますエラーが発生することを意味するようにします。  
  
-   上位互換性を確認します。 列挙体を使用する場合、コードは、メンバーの名前に対応する値が変更された後で、エラーが発生する可能性は低くです。  
  
 列挙体は、名前、基のデータ型およびメンバーのセットを持ちます。 各メンバーは、定数を表します。  
  
 クラス、構造体、モジュール、または、プロシージャの外側のインターフェイス レベルで宣言された列挙型は、 *メンバー列挙*します。 これは、クラス、構造体、モジュール、またはそれを宣言したインターフェイスのメンバーです。  
  
 列挙体のメンバーは、クラス、構造体、モジュール、またはインターフェイス内の任意の場所からアクセスできます。 コードがクラスの外部構造体、またはモジュール必要がありますメンバー列挙体の名前で修飾するクラス、構造体、またはモジュールの名前。 追加することによって完全修飾名を使用する必要を避けることができます、 [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) ステートメントをソース ファイルにします。  
  
 任意のクラス、構造体、モジュール、またはインターフェイスの外部の名前空間レベルで宣言された列挙体が表示される名前空間のメンバーであります。  
  
  *宣言コンテキスト* 列挙体は、ソース ファイル、名前空間、クラス、構造体、モジュール、またはインターフェイスである必要があり、プロシージャになることはできません。 詳細については、次を参照してください。 [宣言コンテキストとアクセス レベルの既定の](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)です。  
  
 属性を適用できますのメンバーではなく、全体としての列挙体に個別にします。 属性は、アセンブリのメタデータに情報を提供します。  
  
## <a name="data-type"></a>データ型  
  `Enum` ステートメントは、列挙型のデータ型を宣言できます。 各メンバーは、列挙型のデータ型を受け取ります。 指定できます `Byte`, 、`Integer`, 、`Long`, 、`SByte`, 、`Short`, 、`UInteger`, 、`ULong`, 、または `UShort`です。  
  
 指定しない場合 `datatype` 、列挙体の各メンバーのデータ型を受け取り、 `initializer`です。 両方を指定する場合は、 `datatype` と `initializer`, のデータ型 `initializer` に変換できなければなりません `datatype`します。 どちらの場合 `datatype` も `initializer` が含まれているデータ型の既定値は `Integer`です。  
  
## <a name="initializing-members"></a>メンバーの初期化  
  `Enum` ステートメントで選択したメンバーの内容を初期化できる `memberlist`です。 使用する `initializer` メンバーに割り当てられる式を指定します。  
  
 指定しない場合 `initializer` メンバーの場合は、Visual Basic を初期化して 0 のいずれか (1 つ目である場合 `member` で `memberlist`)、またはその直前のより 1 だけ大きい値に `member`します。  
  
 それぞれに指定する式 `initializer` リテラル、既に定義されている他の定数と列挙型のメンバーは既に定義されている、この列挙体のメンバーの組み合わせにすることができます。 算術演算および論理演算子を使用すると、このような要素を結合します。  
  
 変数または関数では使用できません `initializer`します。 変換キーワードなどを使用する、 `CByte` と `CShort`です。 使用することも `AscW` 定数を呼び出した場合、 `String` または `Char` 引数、コンパイル時に計算できるためです。  
  
 列挙体には、浮動小数点値を持つことはできません。 メンバーが浮動小数点値を割り当てられている場合、 `Option Strict` に設定されている、コンパイラ エラーが発生します。 場合 `Option Strict` はオフで、値が自動的に変換する、 `Enum` 型です。  
  
 メンバーの値が、基になるデータ型の許容範囲を超えている場合、または基になるデータ型で許容される最大値に任意のメンバーを初期化する場合は、コンパイラはエラーを報告します。  
  
## <a name="modifiers"></a>修飾子  
 クラス、構造体、モジュール、およびインターフェイス メンバーの列挙体の既定でパブリック アクセスです。 アクセス修飾子を使用してこれらのアクセス レベルを調整できます。 名前空間のフレンド アクセスを既定値の列挙体をメンバーです。 これらのアクセス レベルをパブリックがプライベートまたはプロテクトには調整できます。 詳細については、次を参照してください。 [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)します。  
  
 列挙型のすべてのメンバーは、パブリック アクセスを持ち、それらのアクセス修飾子を使用することはできません。 ただし、列挙体自体により厳しいアクセス レベルがある場合は、指定した列挙体のアクセス レベルが優先されます。  
  
 既定では、すべての列挙は型とそのフィールドは定数です。 したがって、 `Shared`, 、`Static`, 、および `ReadOnly` 列挙型またはそのメンバーを宣言するときに、キーワードを使用できません。  
  
## <a name="assigning-multiple-values"></a>複数の値を割り当てる  
 列挙体は、通常、相互に排他的な値を表します。 含めることによって、 <xref:System.FlagsAttribute> 属性、 `Enum` 宣言、代わりに複数の値に割り当てる列挙体のインスタンス。  <xref:System.FlagsAttribute> 属性は、列挙体をビット フィールド、つまり、フラグのセットとして処理することを指定します。 これらと呼びます *ビット* 列挙体です。  
  
 使用して列挙体を宣言する場合、 <xref:System.FlagsAttribute> 属性、お勧めの値は 2、1、2、4、8、16、およびの累乗を使用することです。 また、値が 0 のメンバーの名前を"None"ことをお勧めします。 追加のガイドラインを参照してください。 <xref:System.FlagsAttribute> と <xref:System.Enum>します。  
  
## <a name="example"></a>例  
 次の例では、使用する方法、 `Enum` ステートメントです。 メンバーと呼びます注 `EggSizeEnum.Medium`, ではなく `Medium`です。  
  
 [!code-vb[VbEnumsTask#41](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/WindowsApplication1/Class1.vb#41)]  
  
## <a name="example"></a>例  
 次の例では、メソッドが範囲外です、 `Egg` クラスです。 したがって、 `EggSizeEnum` として完全修飾 `Egg.EggSizeEnum`します。  
  
 [!code-vb[VbEnumsTask#42](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/WindowsApplication1/Class1.vb#42)]  
  
## <a name="example"></a>例  
 次の例では、 `Enum` という名前の定数値を関連のセットを定義するステートメントです。 この場合、値は、色のデータベースのデータ入力フォームをデザインすることもできます。  
  
 [!code-vb[VbEnumsTask#30](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/WindowsApplication1/Class2.vb#30)]  
  
## <a name="example"></a>例  
 次の例では、正と負の両方の番号を含む値を示します。  
  
 [!code-vb[VbEnumsTask#31](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/WindowsApplication1/Class2.vb#31)]  
  
## <a name="example"></a>例  
 次の例では、 `As` 句を使用して指定、 `datatype` 列挙体の。  
  
 [!code-vb[VbEnumsTask#6](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/WindowsApplication1/Class2.vb#6)]  
  
## <a name="example"></a>例  
 次の例では、ビットごとの列挙体の使用方法を示します。 複数の値は、ビットごとの列挙型のインスタンスに割り当てることができます。  `Enum` 宣言が含まれる、 <xref:System.FlagsAttribute> 属性には、列挙型をフラグのセットとして扱えることを示します。  
  
 [!code-vb[VbEnumsTask#61](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/WindowsApplication1/Class1.vb#61)]  
  
## <a name="example"></a>例  
 次の例は、列挙型を反復処理します。 使用して、 <xref:System.Enum.GetNames%2A> 、列挙体のメンバー名の配列を取得するメソッドと <xref:System.Enum.GetValues%2A> メンバーの値の配列を取得します。  
  
 [!code-vb[VbEnumsTask#51](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/WindowsApplication1/Class1.vb#51)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Enum>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)   
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [明示的および暗黙的な変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [定数と列挙型](../../../visual-basic/language-reference/constants-and-enumerations.md)