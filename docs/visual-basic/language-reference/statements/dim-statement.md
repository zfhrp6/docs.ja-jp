---
title: Dim ステートメント (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Dim
- Dim
helpviewer_keywords:
- Public keyword [Visual Basic], in Dim statement
- Dim statement [Visual Basic]
- fixed-length strings [Visual Basic], declaring
- variables [Visual Basic], declaring
- WithEvents keyword [Visual Basic], Dim statement
- dynamic arrays [Visual Basic], Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields [Visual Basic], as member variables
- declarations [Visual Basic], dynamic arrays
- member variables [Visual Basic]
- default values [Visual Basic]
- data types [Visual Basic], assigning
- braces {}
- As keyword [Visual Basic], in Dim statement
- arrays [Visual Basic], declaring
- New keyword [Visual Basic], Dim statement
- To keyword [Visual Basic], in Dim statement
- storage [Visual Basic], allocating
- local variables [Visual Basic]
- declaration statements [Visual Basic]
- Dim statement [Visual Basic], syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
ms.openlocfilehash: b3384b771748a1f2c9e841407042f81ce6ebe76d
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234728"
---
# <a name="dim-statement-visual-basic"></a>Dim ステートメント (Visual Basic)
宣言し、1 つまたは複数の変数の記憶域を割り当てます。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]   
Dim [ WithEvents ] variablelist  
```  
  
## <a name="parts"></a>指定項目  
  
-   `attributelist`  
  
     任意。 参照してください[属性一覧](../../../visual-basic/language-reference/statements/attribute-list.md)です。  
  
-   `accessmodifier`  
  
     任意。 次のいずれかの値を指定します。  
  
    -   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   [保護されたフレンド](../../language-reference/modifiers/protected-friend.md)
    
    - [保護されたプライベート](../../language-reference/modifiers/private-protected.md)

     参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。  
  
-   `Shared`  
  
     任意。 参照してください[共有](../../../visual-basic/language-reference/modifiers/shared.md)です。  
  
-   `Shadows`  
  
     任意。 参照してください[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)です。  
  
-   `Static`  
  
     任意。 参照してください[静的](../../../visual-basic/language-reference/modifiers/static.md)です。  
  
-   `ReadOnly`  
  
     任意。 参照してください[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)です。  
  
-   `WithEvents`  
  
     任意。 これらがイベントを発生させるクラスのインスタンスを参照するオブジェクト変数であることを指定します。 参照してください[WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)です。  
  
-   `variablelist`  
  
     必須。 このステートメントで宣言されている変数の一覧です。  
  
     `variable [ , variable ... ]`  
  
     `variable` の構文と指定項目は次のとおりです。  
  
     `variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`  
  
    |パーツ|説明|  
    |---|---|  
    |`variablename`|必須。 変数の名前です。 参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。|  
    |`boundslist`|任意。 配列変数の各次元の境界の一覧です。|  
    |`New`|任意。 クラスの新しいインスタンスを作成時に、`Dim`ステートメントが実行されています。|  
    |`datatype`|任意。 変数のデータ型。|  
    |`With`|任意。 オブジェクト初期化子リストが導入されています。|  
    |`propertyname`|任意。 インスタンスを作成するクラスのプロパティの名前。|  
    |`propinitializer`|後に必要な`propertyname`= です。 評価され、プロパティ名に割り当てられている式です。|  
    |`initializer`|省略可能な場合`New`が指定されていません。 式が評価され、変数に割り当てが作成されるときです。|  
  
## <a name="remarks"></a>コメント  
 Visual Basic コンパイラを使用して、`Dim`変数のデータ型とどのようなコードが変数にアクセスできるなど、他の情報を確認するステートメント。 次の例を保持する変数の宣言、`Integer`値。  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 任意のデータ型または列挙型、構造体、クラス、またはインターフェイスの名前を指定することができます。  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 使用する参照型の場合、`New`データ型によって、クラスの新しいインスタンスを作成または構造体にキーワードを指定します。 使用する場合`New`、初期化子式を使用しないでください。 代わりに、これらが必要な場合、変数の作成元となるクラスのコンス トラクターに引数を指定します。  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 プロシージャ、ブロック、クラス、構造体、またはモジュール内の変数を宣言することができます。 ソース ファイル、名前空間、またはインターフェイスの変数を宣言することはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 プロシージャの外部のモジュール レベルで宣言された変数は、*メンバー変数*または*フィールド*です。 メンバー変数は、そのクラス、構造体、またはモジュール全体にわたってスコープでは。 プロシージャ レベルで宣言された変数は、*ローカル変数*です。 ローカル変数は、そのプロシージャまたはブロック内でのみスコープでは。  
  
 次のアクセス修飾子を使用して、プロシージャの外部変数を宣言します。 `Public`、 `Protected`、 `Friend`、 `Protected Friend`、および`Private`です。 詳細については、次を参照してください。 [Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。  
  
 `Dim`キーワードは省略可能な次の修飾子のいずれかを指定する場合、通常は省略して: `Public`、 `Protected`、 `Friend`、 `Protected Friend`、 `Private`、 `Shared`、 `Shadows`、 `Static`、`ReadOnly`、または`WithEvents`です。  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 場合`Option Explicit`はコンパイラ on (既定値) を使用するすべての変数の宣言が必要です。 詳細については、次を参照してください。 [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)です。  
  
## <a name="specifying-an-initial-value"></a>初期値を指定します。  
 作成されるときに、変数に値を割り当てることができます。 値の型を使用する、*初期化子*を変数に割り当てられる式を指定します。 式は、コンパイル時に計算できる定数に評価される必要があります。  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 初期化子が指定され、データ型がで指定されていない場合、`As`句、*型推論*初期化子からのデータ型を推論するために使用します。 次の例では、両方とも`num1`と`num2`整数値として厳密に型指定します。 2 番目の宣言では、型の推論は、値は 3 から型を推測します。  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 型の推論は、プロシージャ レベルで適用されます。 クラス、構造体、モジュール、またはインターフェイスのプロシージャの外側は適用されません。 型の推定の詳細については、次を参照してください。 [Option Infer ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md)と[ローカル型推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)です。  
  
 データ型または初期化子が指定されていない場合の動作方法については、次を参照してください。[既定のデータ型と値](../../../visual-basic/language-reference/statements/dim-statement.md#default)このトピックで後述します。  
  
 使用することができます、*オブジェクトの初期化子*匿名の名前付きの型のインスタンスを宣言します。 次のコードがのインスタンスを作成、`Student`クラスし、プロパティを初期化するために、オブジェクト初期化子を使用します。  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 オブジェクト初期化子の詳細については、次を参照してください[する方法: オブジェクト初期化子を使用してオブジェクトを宣言](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)、[オブジェクト初期化子: 名前付きおよび匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)、および[匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)。  
  
## <a name="declaring-multiple-variables"></a>複数の変数を宣言します。  
 かっこで次の各配列名と、それぞれの変数名を指定する 1 つの宣言ステートメントで複数の変数を宣言できます。 複数の変数を指定するときは、コンマで区切ります。  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 いずれかで 1 つ以上の変数を宣言する場合`As`句、そのグループの変数の初期化子を指定することはできません。  
  
 個別を使用して別の変数の別のデータ型を指定することができます`As`それぞれの変数を宣言する句。 各変数は、最初に指定されたデータ型を受け取り`As`句の後に発生したその`variablename`一部です。  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a>配列  
 保持する変数を宣言することができます、*配列*、複数の値を保持することができます。 次の変数は配列を保持することを指定する、`variablename`かっこですぐにします。 配列の詳細については、次を参照してください。[配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)です。  
  
 配列の各次元の上限と下限を指定することができます。 これを行うには、含める、`boundslist`かっこの中にします。 各ディメンションに対して、`boundslist`上限の境界と必要に応じて、下限を指定します。 下限とは常に 0 の場合か、指定するかどうか。 各インデックスは、0 ~ 上限値から変更できます。  
  
 次の 2 つのステートメントは同等です。 各ステートメントは、21 の配列を宣言`Integer`要素。 配列にアクセスするときにインデックスが 0 ~ 20 異なることができます。  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 次のステートメントは、型の 2 次元配列を宣言して`Double`です。 配列は、4 6 列 (5 + 1) 各の行 (3 + 1) です。 上限が、ディメンションの長さではなく、インデックスの最大値を表すことに注意してください。 次元の長さは、上限の境界と 1 つです。  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 配列は、1 から 32 次元を持つことができます。  
  
 すべての境界を配列の宣言に空白にできます。 これを行う場合は、配列は、指定すると、ディメンションの数が初期化されていません。 値がある`Nothing`には、少なくとも初期化するまでその要素の一部です。 `Dim`ステートメントは、境界内のすべてのディメンションまたはディメンションがありませんのいずれかを指定する必要があります。  
  
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
  
 宣言することができます、*長さ 0 の配列*-1 である配列の次元のいずれかを宣言することによりします。 長さ 0 の配列を保持する変数は、値を持たない`Nothing`です。 長さ 0 の配列は、共通言語ランタイムの一部の関数は必要です。 このような配列にアクセスしようとすると、ランタイム例外が発生します。 詳細については、次を参照してください。[配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)です。  
  
 配列リテラルを使用して、配列の値を初期化することができます。 これを行うには、中かっこと初期化の値を囲む (`{}`)。  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 多次元配列は、各次元の初期化は、外側のディメンションの中かっこで囲まれます。 要素は、行優先順で指定されます。  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 配列リテラルの詳細については、次を参照してください。[配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)です。  
  
##  <a name="default"></a> 既定のデータ型し、値  
 次の表では、`Dim` ステートメントのデータ型と初期化子を指定するさまざまな組み合わせの結果を示します。  
  
|データ型が指定されているか|初期化子が指定されているか|例|結果|  
|---|---|---|---|  
|Ｘ|いいえ|`Dim qty`|場合[Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)に設定されている変数 off (既定)、`Nothing`です。<br /><br /> `Option Strict` がオンの場合、コンパイル時エラーが発生します。|  
|Ｘ|[はい]|`Dim qty = 5`|場合[Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) on (既定値) は、変数は、データが初期化子の型します。 参照してください[ローカル型推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)です。<br /><br /> `Option Infer` がオフで、`Option Strict` がオフの場合、変数は `Object` のデータ型になります。<br /><br /> `Option Infer` がオフで、`Option Strict` がオンの場合、コンパイル時エラーが発生します。|  
|○|Ｘ|`Dim qty As Integer`|変数は、データ型の既定値に初期化されます。 このセクションの後半の表を参照してください。|  
|[はい]|○|`Dim qty  As Integer = 5`|初期化子のデータ型を指定したデータ型に変換できない場合は、コンパイル時エラーが発生します。|  
  
 データ型を指定して、初期化子を指定しない場合、Visual Basic は、そのデータ型の既定値に変数を初期化します。 次の表は、既定値に初期化の値を示します。  
  
|データの種類|既定値|  
|---|---|  
|すべての数値型 (など`Byte`と`SByte`)|0|  
|`Char`|バイナリ 0|  
|参照型はすべて (含む`Object`、 `String`、およびすべての配列)|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|1 年 1 月 1 日の午前 12時 00分 (01/01/0001 12時 00分: 00 AM)|  
  
 構造体の各要素は個別の変数の場合と同様に初期化します。 配列の長さを宣言でその要素を初期化しない場合、各要素は、個別の変数の場合と同様に初期化されます。  
  
## <a name="static-local-variable-lifetime"></a>静的ローカル変数有効期間  
 A`Static`ローカル変数が宣言されているプロシージャの場合よりも有効期間が長くなります。 変数の有効期間の境界は、プロシージャが宣言されていると、かどうかによって異なります。`Shared`です。  
  
|プロシージャの宣言|初期化された変数|既存の変数を停止します。|  
|---|---|---|  
|モジュールで|最初に、プロシージャを呼び出す|プログラムが実行を停止します。|  
|手順は、クラスまたは構造体は、します。 `Shared`|最初に、プロシージャを呼び出すか、特定のインスタンスまたはクラスまたは構造体自体|プログラムが実行を停止します。|  
|クラスまたは構造体では、プロシージャはありません。 `Shared`|初めてプロシージャは特定のインスタンスで呼び出されます。|ガベージ コレクション (GC) のインスタンスを解放する場合|  
  
## <a name="attributes-and-modifiers"></a>属性と修飾子  
 属性は、ローカル変数ではなく、メンバー変数にのみ適用できます。 属性は、ローカル変数などの一時的なストレージの意味ではないアセンブリのメタデータに情報を提供します。  
  
 モジュール レベルで使用することはできません、`Static`修飾子メンバー変数を宣言します。 プロシージャ レベルでは使用できません`Shared`、 `Shadows`、 `ReadOnly`、`WithEvents`のいずれかのアクセス修飾子をローカル変数を宣言するか。  
  
 指定することによって、変数にアクセスできるコードを指定することができます、`accessmodifier`です。 クラスとモジュールのメンバー (プロシージャ) の外部変数既定でプライベート アクセスは、および構造体のメンバー変数の既定でパブリック アクセスです。 アクセス修飾子を使用してこれらのアクセス レベルを調整できます。 (プロシージャ) 内のローカル変数にアクセス修飾子を使用することはできません。  
  
 指定できます`WithEvents`のみメンバー変数ではなく、プロシージャ内のローカル変数。 指定した場合`WithEvents`、変数のデータ型では、特定のクラス型を解除する必要がある`Object`です。 格納された配列を宣言することはできません`WithEvents`です。 イベントの詳細については、次を参照してください。[イベント](../../../visual-basic/programming-guide/language-features/events/index.md)です。  
  
> [!NOTE]
>  コードをクラスの外部構造体、またはモジュール修飾する必要がありますそのクラス、構造体、モジュールの名前を持つメンバー変数の名前。 プロシージャまたはブロックは、そのプロシージャまたはブロック内のローカル変数を参照できません外部をコードします。  
  
## <a name="releasing-managed-resources"></a>マネージ リソースを解放します。  
 ユーザーによる追加のコーディングなしに、.NET Framework のガベージ コレクターがマネージ リソースを破棄します。 ただし、ガベージ コレクターを待つ代わりにマネージ リソースの破棄を強制することができます。  
  
 クラスは、特に、不足しているリソース (データベース接続やファイル ハンドル) などの上に保持している場合、次のガベージ コレクションが不要で使用されるクラスのインスタンスをクリーンアップするまで待機することがないできます。 クラスが実装することが、<xref:System.IDisposable>ガベージ コレクションの前にリソースを解放する方法を提供するインターフェイスです。 そのインターフェイスを実装するクラスは、公開、`Dispose`貴重なリソースを直ちに解放を強制的に呼び出すことができるメソッドです。  
  
 `Using`ステートメントは、リソースを取得する、一連のステートメントを実行およびリソースの破棄し、プロセスを自動化します。 ただし、リソースを実装する必要があります、<xref:System.IDisposable>インターフェイスです。 詳細については、「[Using ステートメント](../../../visual-basic/language-reference/statements/using-statement.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、変数を宣言を使用して、`Dim`さまざまなオプションを含むステートメント。  
  
 [!code-vb[VbVbalrStatements#141](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_1.vb)]  
  
## <a name="example"></a>例  
 次の例は、1 ~ 30 の素数を一覧表示します。 ローカル変数のスコープには、コードのコメントが記載されています。  
  
 [!code-vb[VbVbalrStatements#142](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_2.vb)]  
  
## <a name="example"></a>例  
 次の例で、`speedValue`変数はクラス レベルで宣言します。 `Private`変数を宣言するキーワードを使用します。 変数のいずれの手順によってアクセスできる、`Car`クラスです。  
  
 [!code-vb[VbVbalrStatements#144](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#145](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_4.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)  
 [ReDim ステートメント](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Option Infer ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [変数宣言](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [オブジェクト初期化子 : 名前付きの型と匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [オブジェクト初期化子 : 名前付きの型と匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [方法 : オブジェクト初期化子を使用してオブジェクトを宣言する](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)  
 [ローカル型の推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
