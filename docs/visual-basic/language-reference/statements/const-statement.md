---
title: Const ステートメント (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
ms.openlocfilehash: a5842e284eaa858e7a66160060123edc21858a3a
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34233848"
---
# <a name="const-statement-visual-basic"></a>Const ステートメント (Visual Basic)
宣言し、1 つまたは複数の定数を定義します。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ]   
Const constantlist  
```  
  
## <a name="parts"></a>指定項目  
 `attributelist`  
 任意。 すべての定数に適用される属性の一覧は、このステートメントで宣言します。 参照してください[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)山かっこ ("`<`「と」`>`") です。  
  
 `accessmodifier`  
 任意。 これらの定数にアクセスできるコードを指定するのにには、これを使用します。 指定できます[パブリック](../../../visual-basic/language-reference/modifiers/public.md)、 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)、[フレンド](../../../visual-basic/language-reference/modifiers/friend.md)、 [Protected Friend](../modifiers/protected-friend.md)、[プライベート](../../../visual-basic/language-reference/modifiers/private.md)、または[保護されたプライベート](../../language-reference/modifiers/private-protected.md)です。
  
 `Shadows`  
 任意。 再宣言して、基底クラスのプログラミング要素を非表示にするには、これを使用します。 参照してください[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)です。  
  
 `constantlist`  
 必須。 このステートメントで宣言されている定数の一覧です。  
  
 `constant` `[ ,` `constant` `... ]`  
  
 `constant` の構文と指定項目は次のとおりです。  
  
 `constantname` `[ As` `datatype` `] =` `initializer`  
  
|パーツ|説明|  
|----------|-----------------|  
|`constantname`|必須。 定数の名前です。 参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。|  
|`datatype`|場合は必須`Option Strict`は`On`します。 定数のデータ型。|  
|`initializer`|必須。 コンパイル時に評価され、式を定数に割り当てられています。|  
  
## <a name="remarks"></a>コメント  
 アプリケーションで変更されない値があれば、名前付き定数を定義でき、リテラル値の代わりに使用できます。 名前は、値よりも覚えやすくです。 定数を 1 回だけ定義し、コードでのさまざまな場所で使用できます。 以降のバージョンでは、値を再定義する必要がある場合、`Const`ステートメントは、唯一の場所を変更する必要があります。  
  
 使用することができます`Const`モジュールまたはプロシージャ レベルでのみです。 つまり、*宣言コンテキスト*変数はクラス、構造体、モジュール、プロシージャ、またはブロックする必要があり、ソース ファイル、名前空間、またはインターフェイスにすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 ローカル定数 (プロシージャ) 内の既定値は、パブリック アクセスとは、それらのアクセス修飾子を使用できません。 クラスとモジュールのメンバー (プロシージャ) の外部の定数既定でプライベート アクセスは、および構造体メンバー定数とパブリック アクセスの既定値です。 アクセス修飾子を使用してこれらのアクセス レベルを調整できます。  
  
## <a name="rules"></a>ルール  
  
-   **宣言コンテキスト。** 定数は、プロシージャの外部のモジュール レベルで宣言された、*メンバー定数*以外の場合は、クラス、構造体のメンバーであるかを宣言するモジュールです。  
  
     プロシージャ レベルで宣言されている定数は、*ローカル定数*; プロシージャまたはブロックを宣言したに対してローカルであります。  
  
-   **属性。** 属性は、ローカル定数ではなく、メンバー定数にのみ適用できます。 属性は、ローカル定数などの一時的なストレージの意味ではないアセンブリのメタデータに情報を提供します。  
  
-   **修飾子です。** すべての定数は、既定では、 `Shared`、 `Static`、および`ReadOnly`です。 定数を宣言するときに、これらのキーワードのいずれかを使用することはできません。  
  
     プロシージャ レベルでは使用できません`Shadows`またはのいずれかのアクセス修飾子をローカル定数を宣言します。  
  
-   **複数の定数です。** 同じ宣言ステートメントで複数の定数を宣言することができますを指定する、`constantname`それぞれの一部です。 複数の定数は、コンマで区切られます。  
  
## <a name="data-type-rules"></a>データ型のルール  
  
-   **データ型。** `Const`ステートメントは、変数のデータ型を宣言できます。 任意のデータ型または列挙型の名前を指定することができます。  
  
-   **既定の型。** 指定しない場合`datatype`、定数のデータ型を受け取る`initializer`です。 両方を指定する場合`datatype`と`initializer`のデータ型`initializer`に変換できる必要があります`datatype`です。 どちらの場合`datatype`も`initializer`が含まれているデータ型の既定値は`Object`します。  
  
-   **さまざまな種類。** 個別を使用して複数の定数に異なるデータ型を指定することができます`As`それぞれの変数を宣言する句。 ただし、一般的に使われるを使用して同じ型にいくつかの定数を宣言することはできません`As`句。  
  
-   **初期化します。** すべての定数の値を初期化する必要があります`constantlist`です。 使用する`initializer`を定数に割り当てられる式を指定します。 式には、リテラル、既に定義されているその他の定数、および既に定義されている列挙型メンバーの任意の組み合わせを指定できます。 算術演算子および論理演算子を使用すると、このような要素を結合します。  
  
     変数または関数を使用することはできません`initializer`です。 変換キーワードなどを使用するただし、`CByte`と`CShort`です。 使用することも`AscW`定数で呼び出す場合は、`String`または`Char`引数、コンパイル時に評価できるためです。  
  
## <a name="behavior"></a>動作  
  
-   **スコープです。** ローカル定数は、そのプロシージャまたはブロック内からしかアクセスできません。 メンバー定数には、クラス、構造体、またはモジュール内で任意の場所からアクセスします。  
  
-   **パス名です。** コードをクラスの外部構造体、またはモジュール修飾する必要がありますそのクラス、構造体、モジュールの名前を持つメンバー定数の名前。 プロシージャまたはブロックは、そのプロシージャまたはブロック内であるローカル定数を参照できません外部をコードします。  
  
## <a name="example"></a>例  
 次の例では、`Const`ステートメントをリテラル値の代わりに使用する定数を宣言します。  
  
 [!code-vb[VbVbalrStatements#13](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/const-statement_1.vb)]  
  
## <a name="example"></a>例  
 データ型の定数を定義した場合`Object`、Visual Basic コンパイラは、の型を提供、`initializer`の代わりに`Object`です。 次の例では、定数`naturalLogBase`実行時の型を持つ`Decimal`します。  
  
 [!code-vb[VbVbalrStatements#87](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/const-statement_2.vb)]  
  
 前の例では、<xref:System.Type.ToString%2A>メソッドを<xref:System.Type>によって返されるオブジェクト、 [GetType 演算子](../../../visual-basic/language-reference/operators/gettype-operator.md)ため、<xref:System.Type>に変換できない`String`を使用して`CStr`です。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 [Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [#Const ディレクティブ](../../../visual-basic/language-reference/directives/const-directive.md)  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [ReDim ステートメント](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [暗黙の型変換と明示的な型変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [定数と列挙体](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)  
 [定数と列挙体](../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
