---
title: "Dim ステートメント (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Dim"
  - "Dim"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Dim ステートメントでの public キーワード"
  - "Dim ステートメント"
  - "宣言の固定長文字列"
  - "変数 [Visual Basic]、宣言"
  - "WithEvents キーワード、Dim ステートメント"
  - "動的配列、Dim ステートメント"
  - "変数 [Visual Basic] の初期化"
  - "中かっこ ({})"
  - "メンバー変数としてのフィールド"
  - "動的配列の宣言"
  - "メンバー変数"
  - "既定値"
  - "割り当てのデータ型 [Visual Basic]"
  - "中かっこ ({})"
  - "Dim ステートメントでキーワードとして"
  - "配列 [Visual Basic] の宣言"
  - "New キーワード、Dim ステートメント"
  - "Dim ステートメントのキーワードに"
  - "記憶域の割り当て"
  - "ローカル変数"
  - "宣言ステートメント"
  - "Dim ステートメント構文"
  - "変数 [Visual Basic]、メンバー、およびローカル"
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
caps.latest.revision: 72
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 72
---
# Dim ステートメント (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

宣言し、1 つまたは複数の変数の記憶域を割り当てます。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]   
Dim [ WithEvents ] variablelist  
```  
  
## <a name="parts"></a>指定項目  
  
-   `attributelist`  
  
     省略可能です。 参照してください [属性一覧](../../../visual-basic/language-reference/statements/attribute-list.md)します。  
  
-   `accessmodifier`  
  
     省略可能です。 次のいずれかの値を指定します。  
  
    -   [パブリック](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [保護されています。](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [プライベート](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     「 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。  
  
-   `Shared`  
  
     省略可能です。 参照してください [共有](../../../visual-basic/language-reference/modifiers/shared.md)します。  
  
-   `Shadows`  
  
     省略可能です。 参照してください [シャドウ](../../../visual-basic/language-reference/modifiers/shadows.md)します。  
  
-   `Static`  
  
     省略可能です。 参照してください [静的](../../../visual-basic/language-reference/modifiers/static.md)します。  
  
-   `ReadOnly`  
  
     省略可能です。 参照してください [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)します。  
  
-   `WithEvents`  
  
     省略可能です。 これらがイベントを発生させるクラスのインスタンスを参照するオブジェクト変数であることを指定します。 参照してください [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)します。  
  
-   `variablelist`  
  
     必須です。 このステートメントで宣言されている変数の一覧です。  
  
     `variable [ , variable ... ]`  
  
     `variable` の構文と指定項目は次のとおりです。  
  
     `variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`  
  
    |||  
    |-|-|  
    |パーツ|説明|  
    |`variablename`|必須です。 変数名。 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。|  
    |`boundslist`|省略可能です。 配列変数の各次元の境界のリストです。|  
    |`New`|省略可能です。 クラスの新しいインスタンスを作成するときに、 `Dim` ステートメントが実行されています。|  
    |`datatype`|省略可能です。 変数のデータ型。|  
    |`With`|省略可能です。 オブジェクト初期化子リストを紹介します。|  
    |`propertyname`|省略可能です。 インスタンスを作成するクラスのプロパティの名前。|  
    |`propinitializer`|後に必要な `propertyname` = です。 この式は評価され、プロパティ名に割り当てられているです。|  
    |`initializer`|省略可能な場合 `New` が指定されていません。 評価され、作成時に、変数に代入する式です。|  
  
## <a name="remarks"></a>コメント  
 Visual Basic コンパイラを使用して、 `Dim` 変数のデータ型と変数にアクセスできるコードなど、他の情報を確認するステートメントです。 次の例を保持する変数の宣言、 `Integer` 値。  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 任意のデータ型または列挙型、構造体、クラス、インターフェイスの名前を指定することができます。  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 参照型を使用する、 `New` データ型で、クラスの新しいインスタンスを作成または構造体にキーワードを指定します。 使用する場合 `New`, 、初期化子式を使用しないでください。 代わりに、変数の作成元となるクラスのコンス トラクターに必要な場合は、引数を指定します。  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 プロシージャ、ブロック、クラス、構造体、またはモジュール内の変数を宣言することができます。 ソース ファイル、名前空間、またはインターフェイスの変数を宣言することはできません。 詳細については、次を参照してください。 [宣言コンテキストとアクセス レベルの既定の](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)です。  
  
 プロシージャの外部のモジュール レベルで宣言されている変数は、 *メンバー変数* または *フィールド*します。 メンバー変数は、クラス、構造体、またはモジュール全体に及びます。 プロシージャ レベルで宣言されている変数は、 *ローカル変数*します。 ローカル変数はそのプロシージャまたはブロック内でのみに及びます。  
  
 プロシージャの外の変数を宣言する次のアクセス修飾子を使用します。 `Public`, 、`Protected`, 、`Friend`, 、`Protected Friend`, 、および `Private`です。 詳細については、次を参照してください。 [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)します。  
  
  `Dim` キーワードを省略し、次の修飾子のいずれかを指定する場合は通常省略: `Public`, 、`Protected`, 、`Friend`, 、`Protected Friend`, 、`Private`, 、`Shared`, 、`Shadows`, 、`Static`, 、`ReadOnly`, 、または `WithEvents`です。  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 場合 `Option Explicit` はコンパイラ on (既定値) を使用するすべての変数の宣言が必要です。 詳細については、次を参照してください。 [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)します。  
  
## <a name="specifying-an-initial-value"></a>初期値を指定します。  
 作成されるときに、変数に値を割り当てることができます。 値の型を使用する、 *初期化子* 変数に割り当てられる式を指定します。 式は、コンパイル時に計算できる定数に評価される必要があります。  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 初期化子が指定されており、データ型がで指定されていない場合、 `As` 句、 *型の推論* は初期化子からのデータ型の推論に使用します。 次の例では両方とも `num1` と `num2` 整数として厳密に型指定します。 2 番目の宣言では、型の推論は、値 3 から型を推測します。  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 型の推論は、プロシージャ レベルで適用されます。 これは、クラス、構造体、モジュール、またはインターフェイスのプロシージャの外側は適用されません。 型の推定の詳細については、次を参照してください。 [Option Infer ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md) と [ローカル型推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)します。  
  
 データ型または初期化子が指定されていないときの動作方法については、次を参照してください。 [既定のデータ型や値](../../../visual-basic/language-reference/statements/dim-statement.md#default) このトピックで後述します。  
  
 使用することができます、 *オブジェクト初期化子* 、匿名の名前付きの型のインスタンスを宣言します。 次のコードは、のインスタンスを作成、 `Student` クラスし、オブジェクト初期化子を使用してプロパティを初期化します。  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 オブジェクト初期化子の詳細については、次を参照してください。 [方法: オブジェクト初期化子を使用してオブジェクトを宣言](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), 、[オブジェクト初期化子: 名前付きおよび匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), 、および [匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)します。  
  
## <a name="declaring-multiple-variables"></a>複数の変数を宣言します。  
 かっこを使用し、各配列名ごとに、変数名を指定する 1 つの宣言ステートメントで複数の変数を宣言することができます。 複数の変数を指定するときは、コンマで区切ります。  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 いずれかで 1 つ以上の変数を宣言する場合は、 `As` 句の変数には、そのグループの初期化子を指定することはできません。  
  
 別々 の異なる変数に異なるデータ型を指定する `As` を宣言する各変数の句。 各変数は、最初に指定されているデータ型を受け取り `As` 句の後に発生したその `variablename` 部分です。  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a>配列  
 保持する変数を宣言する、 *配列*, 、複数の値を保持することができます。 変数は配列を保持することを指定するには、次の `variablename` 直後のかっこを使用します。 配列の概要の詳細については、次を参照してください。 [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)します。  
  
 配列の各次元の上限と下限を指定することができます。 これを行うには、含める、 `boundslist` かっこ内にします。 各ディメンションに対して、 `boundslist` 上限と下限の境界のオプションでを指定します。 下限値は常に 0、指定するかどうかどうか。 各インデックスには、0 ~ 上限値は異なります。  
  
 次の 2 つのステートメントは等価です。 各ステートメントが 21 の配列を宣言して `Integer` 要素。 配列にアクセスする場合は、インデックスが 0 ~ 20 異なることができます。  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 次のステートメントは、型の 2 次元配列を宣言して `Double`します。 配列には、6 列 (5 + 1) ごとの 4 つの行 (3 + 1) があります。 上限の境界がの次元の長さではなく、インデックスを指定できる最大値を表すことに注意してください。 次元の長さは、上限の境界と 1 つです。  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 配列は、32 のディメンションに 1 ができます。  
  
 すべての境界に配列の宣言で空白しておきます。 これを行う場合は、配列は、指定したディメンションの数が初期化されていません。 値がある `Nothing` には、少なくとも初期化しないと、その要素の一部です。  `Dim` ステートメントは、境界内のすべてのディメンションまたはディメンションがありませんのいずれかを指定する必要があります。  
  
```vb  
' Declare an array with blank array bounds.  
Dim messages() As String  
' Initialize the array.  
ReDim messages(4)  
```  
  
 配列に 1 つ以上のディメンションがある場合は、ディメンションの数を示すためにかっこで囲まれたコンマを含める必要があります。  
  
```vb  
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte  
```  
  
 宣言することができます、 *長さ 0 の配列* を-1 配列の次元のいずれかを宣言することで。 長さ 0 の配列を保持する変数は、値を持たない `Nothing`します。 共通言語ランタイムの一部の関数では、長さ 0 の配列が必要です。 このような配列にアクセスしようとすると、ランタイム例外が発生します。 詳細については、次を参照してください。 [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)します。  
  
 配列の値を初期化するには、配列リテラルを使用します。 これを行うには、初期化値を中かっこで囲みます (`{}`)。  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 多次元配列の各次元の初期化は、外側のディメンションの中かっこで囲まれました。 要素は、行優先順で指定されます。  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 配列リテラルの詳細については、次を参照してください。 [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)します。  
  
##  <a name="a-namedefaulta-default-data-types-and-values"></a><a name="default"></a> 既定のデータ型し、値  
 次の表では、`Dim` ステートメントのデータ型と初期化子を指定するさまざまな組み合わせの結果を示します。  
  
|||||  
|-|-|-|-|  
|データ型が指定されているか|初期化子が指定されているか|例|結果|  
|Ｘ|いいえ|`Dim qty`|場合 [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) に設定されている、変数、off (既定)、 `Nothing`です。<br /><br /> `Option Strict` がオンの場合、コンパイル時エラーが発生します。|  
|Ｘ|はい|`Dim qty = 5`|場合 [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) on (既定値) は、変数は、データが、初期化子の型します。 参照してください [ローカル型推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)します。<br /><br /> `Option Infer` がオフで、`Option Strict` がオフの場合、変数は `Object` のデータ型になります。<br /><br /> `Option Infer` がオフで、`Option Strict` がオンの場合、コンパイル時エラーが発生します。|  
|○|Ｘ|`Dim qty As Integer`|変数は、データ型の既定値に初期化されます。 このセクションの後半の表を参照してください。|  
|はい|○|`Dim qty  As Integer = 5`|初期化子のデータ型を指定したデータ型に変換できない場合は、コンパイル時エラーが発生します。|  
  
 データ型を指定して、初期化子を指定しない場合 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は変数のデータ型の既定値を初期化します。 次の表は、既定値に初期値を示します。  
  
|||  
|-|-|  
|データ型|既定値|  
|すべての数値型 (を含む `Byte` と `SByte`)|0|  
|`Char`|バイナリ 0|  
|参照型はすべて (を含む `Object`, 、`String`, 、およびすべての配列)|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|1 年 1 月 1 日の午前 12時 00分 (01/01/0001 12時 00分: 00 AM)|  
  
 構造体の各要素は別々 の変数の場合と同様に初期化されます。 配列の長さを宣言、要素を初期化しない場合は、各要素は別々 の変数の場合と同様に初期化されます。  
  
## <a name="static-local-variable-lifetime"></a>静的ローカル変数有効期間  
 A `Static` ローカル変数が宣言されているプロシージャの場合よりも有効期間が長くなります。 変数の有効期間の境界は、プロシージャが宣言されていると、かどうかによって異なります。 `Shared`します。  
  
||||  
|-|-|-|  
|プロシージャの宣言|初期化された変数|既存の変数を停止します。|  
|モジュールで|初めてのプロシージャが呼び出されたとき|プログラムが実行を停止します。|  
|手順は、クラスまたは構造体は、します。 `Shared`|最初に特定のインスタンスで、またはクラスまたは構造体自体でプロシージャが呼び出されます|プログラムが実行を停止します。|  
|クラスまたは構造体では、プロシージャはではありません。 `Shared`|初めてのプロシージャが特定のインスタンスで呼び出されたとき|ガベージ コレクション (GC) のインスタンスを解放する場合|  
  
## <a name="attributes-and-modifiers"></a>属性および修飾子  
 属性は、ローカル変数ではなく、メンバー変数にのみ適用できます。 属性は、意味のあるローカル変数などの一時的なストレージではないアセンブリのメタデータに情報を提供します。  
  
 モジュール レベルでは使用できません、 `Static` 修飾子をメンバー変数を宣言します。 プロシージャ レベルでは使用できません `Shared`, 、`Shadows`, 、`ReadOnly`, 、`WithEvents`, 、またはいずれかのアクセスをローカル変数を宣言する修飾子です。  
  
 指定することによって、変数にアクセスできるコードを指定する、 `accessmodifier`です。 クラスとモジュールのメンバー (プロシージャ) の外部変数デフォルト プライベート アクセスには、構造体のメンバー変数の既定でパブリック アクセス。 アクセス修飾子を使用してこれらのアクセス レベルを調整できます。 ローカル変数 (プロシージャ) 内では、アクセス修飾子を使用できません。  
  
 指定できます `WithEvents` のみメンバー変数ではなく、プロシージャ内のローカル変数。 指定した場合 `WithEvents`, 、変数のデータ型がない、特定のクラス型をする必要があります `Object`します。 配列を宣言することはできません `WithEvents`します。 イベントの詳細については、次を参照してください。 [イベント](../../../visual-basic/programming-guide/language-features/events/events.md)です。  
  
> [!NOTE]
>  コードをクラスの外部構造体、またはモジュール修飾する必要があります、クラス、構造体、モジュールの名前のメンバー変数の名前。 プロシージャまたはブロックは、そのプロシージャまたはブロック内のローカル変数を参照できません外部をコードします。  
  
## <a name="releasing-managed-resources"></a>マネージ リソースを解放します。  
 ユーザー側でコードを追加せずに、.NET Framework のガベージ コレクターがマネージ リソースを破棄します。 ただし、ガベージ コレクターを待つことがなく管理されているリソースの破棄を強制できます。  
  
 クラスは、データベース接続やファイル ハンドル) などの特に役に立つと不足しているリソース上に保持している場合、次のガベージ コレクションが不要で使用されるクラスのインスタンスをクリーンアップするまで待機することがないできます。 クラスで実装が、 <xref:System.IDisposable> ガベージ コレクションの前にリソースを解放する方法を提供するインターフェイスです。 そのインターフェイスを実装するクラスは、公開、 `Dispose` メソッド強制的に貴重なリソースをすぐに解放するために呼び出すことができます。  
  
  `Using` ステートメントがリソースを取得する、一連のステートメントを実行して、リソースを破棄し、プロセスを自動化します。 ただし、リソースを実装する必要があります、 <xref:System.IDisposable> インターフェイスです。 詳細については、次を参照してください。 [Using ステートメント](../../../visual-basic/language-reference/statements/using-statement.md)します。  
  
## <a name="example"></a>例  
 次の例では、変数を宣言を使用して、 `Dim` さまざまなオプションを含むステートメント。  
  
 [!code-vb[VbVbalrStatements#141](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_1.vb)]  
  
## <a name="example"></a>例  
 次の例は、1 ~ 30 の素数を一覧表示します。 ローカル変数のスコープには、コードのコメントが記載されています。  
  
 [!code-vb[VbVbalrStatements#142](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_2.vb)]  
  
## <a name="example"></a>例  
 次の例では、 `speedValue` 変数はクラス レベルで宣言します。  `Private` 、変数を宣言するキーワードを使用します。 変数は、の任意のプロシージャからアクセスできる、 `Car` クラスです。  
  
 [!code-vb[VbVbalrStatements#144](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#145](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_4.vb)]  
  
## <a name="see-also"></a>「  
 [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)   
 [ReDim ステートメント](../../../visual-basic/language-reference/statements/redim-statement.md)   
 [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [Option Infer ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [[コンパイル] ページ、プロジェクト デザイナー) (Visual Basic)](../Topic/Compile%20Page,%20Project%20Designer%20\(Visual%20Basic\).md)   
 [変数宣言](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [オブジェクト初期化子: 名前付きおよび匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [オブジェクト初期化子: 名前付きおよび匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [方法: オブジェクト初期化子を使用してオブジェクトを宣言](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)   
 [ローカル型推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)