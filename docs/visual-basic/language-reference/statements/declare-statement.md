---
title: Declare Statement
ms.date: 07/20/2015
f1_keywords:
- vb.Declare
- vb.Lib
- vb.Any
helpviewer_keywords:
- Lib keyword [Visual Basic]
- declaring procedures [Visual Basic], Declare statement
- functions [Visual Basic], function procedures
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- procedures [Visual Basic], external
- Alias keyword [Visual Basic]
- external references [Visual Basic], Visual Basic
- DLLs, declaring procedures
- Declare statement [Visual Basic]
- declarations [Visual Basic], external
- Visual Basic code, Function procedures
- As keyword [Visual Basic], in Declare statement
- resources [Visual Basic], declaring
- Public keyword [Visual Basic], Declare statement
- platform invoke, Visual Basic external references
- Sub procedures [Visual Basic], declarations
- APIs, declaring API functions
- Visual Basic code, Sub procedures
- Function procedures [Visual Basic], declaring
ms.assetid: d3f21fb0-b804-4c99-97ed-583b23894cf1
ms.openlocfilehash: 75d41883aefbaa54eb836d89bbfc034d99b7bba0
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
ms.locfileid: "34233978"
---
# <a name="declare-statement"></a>Declare Statement
外部ファイルで実装されているプロシージャへの参照を宣言します。  
  
## <a name="syntax"></a>構文  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _  
Declare [ charsetmodifier ] [ Sub ] name Lib "libname" _  
[ Alias "aliasname" ] [ ([ parameterlist ]) ]  
' -or-  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _  
Declare [ charsetmodifier ] [ Function ] name Lib "libname" _  
[ Alias "aliasname" ] [ ([ parameterlist ]) ] [ As returntype ]  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`attributelist`|任意。 参照してください[属性一覧](../../../visual-basic/language-reference/statements/attribute-list.md)です。|  
|`accessmodifier`|任意。 次のいずれかの値を指定します。<br /><br /> -   [パブリック](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [保護されています。](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [プライベート](../../../visual-basic/language-reference/modifiers/private.md)<br />- [保護されたフレンド](../../language-reference/modifiers/protected-friend.md)<br />- [保護されたプライベート](../../language-reference/modifiers/private-protected.md)<br /><br /> 参照してください[Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。|  
|`Shadows`|任意。 参照してください[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)です。|  
|`charsetmodifier`|任意。 文字セットとファイルを指定の情報を検索します。 次のいずれかの値を指定します。<br /><br /> -   [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md) (既定値)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [自動](../../../visual-basic/language-reference/modifiers/auto.md)|  
|`Sub`|省略可能、ただしか`Sub`または`Function`表示する必要があります。 外部プロシージャが値を返さないことを示します。|  
|`Function`|省略可能、ただしか`Sub`または`Function`表示する必要があります。 外部プロシージャが値を返すことを示します。|  
|`name`|必須。 この外部参照の名前です。 詳細については、次を参照してください。[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。|  
|`Lib`|必須。 導入されています、`Lib`句は、外部プロシージャを含む外部ファイル (DLL またはコード リソース) を識別します。|  
|`libname`|必須。 宣言されたプロシージャを含むファイルの名前。|  
|`Alias`|任意。 指定された名前で、ファイル内で宣言されているプロシージャを識別できないことを示す`name`です。 その id を指定する`aliasname`です。|  
|`aliasname`|使用するかどうかは必ず、`Alias`キーワード。 2 つの方法のいずれかでプロシージャを識別する文字列。<br /><br /> 引用符で囲まれた、ファイルの内部でプロシージャのエントリ ポイント名 (`""`)<br /><br /> - または -<br /><br /> 番号記号 (`#`) とファイルの内部でプロシージャのエントリ ポイントの序数を指定する整数値|  
|`parameterlist`|かどうか、プロシージャでは、パラメーターが必要です。 参照してください[パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)です。|  
|`returntype`|場合は必須`Function`が指定されていると`Option Strict`は`On`します。 プロシージャによって返される値のデータ型。|  
  
## <a name="remarks"></a>コメント  
 場合があります (DLL またはコード リソース) などのファイルをプロジェクト外で定義されているプロシージャを呼び出す必要があります。 これを行うときに、Visual Basic コンパイラには、プロシージャが配置されているなどと識別する方法、その呼び出し元のシーケンスと戻り値の型、文字列の文字セットを使用して、プロシージャを正しく呼び出すために必要な情報へのアクセスはありません。 `Declare`ステートメントは、外部プロシージャへの参照を作成し、この必要な情報を提供します。  
  
 `Declare` は、モジュール レベルでのみ使用できます。 つまり、*宣言コンテキスト*外部参照は、クラス、構造体、またはモジュールにする必要があり、ソース ファイル、名前空間、インターフェイス、プロシージャ、またはブロックすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 外部参照の既定値は[パブリック](../../../visual-basic/language-reference/modifiers/public.md)アクセスします。 アクセス修飾子を使用してこれらのアクセス レベルを調整できます。  
  
## <a name="rules"></a>ルール  
  
-   **属性。** 属性は、外部参照に適用できます。 外部のファイルではなく、プロジェクトでのみ適用するすべての属性を持ちません。  
  
-   **修飾子です。** 外部プロシージャは、暗黙的に[Shared](../../../visual-basic/language-reference/modifiers/shared.md)です。 使用することはできません、`Shared`キーワードと、共有状態を変更して、外部参照を宣言することはできません。  
  
     外部プロシージャでは、オーバーライドに参加したり、インターフェイス メンバーの実装、またはイベントを処理できません。 同様に、使用することはできません、 `Overrides`、 `Overridable`、 `NotOverridable`、 `MustOverride`、 `Implements`、または`Handles`キーワード、`Declare`ステートメントです。  
  
-   **外部プロシージャの名前。** この外部参照に同じ名前を指定する必要はありません (で`name`)、外部ファイル内で、プロシージャのエントリ ポイント名として (`aliasname`)。 使用することができます、`Alias`句をエントリ ポイント名を指定します。 これは、外部プロシージャに同じ名前の Visual Basic の予約済み修飾子または変数、プロシージャ、またはその他のプログラミング要素がある場合は、同じスコープ内に役立ちます。 ことができます。  
  
    > [!NOTE]
    >  ほとんどの Dll のエントリ ポイント名は大文字小文字を区別します。  
  
-   **外部プロシージャの数です。** また、使用することができます、`Alias`句を外部のファイルのエクスポート テーブル内のエントリ ポイントの序数を指定します。 開始するには、`aliasname`は、番号記号 (`#`)。 Visual basic では外部プロシージャ名の任意の文字が許可されていない場合、または外部のファイル名を指定せず、プロシージャをエクスポートする場合、これは役立つあります。  
  
## <a name="data-type-rules"></a>データ型のルール  
  
-   **パラメーターのデータ型。** 場合`Option Strict`は`On`、内の各パラメーターのデータ型を指定する必要があります`parameterlist`です。 これには、任意のデータ型または列挙型、構造体、クラス、またはインターフェイスの名前を指定できます。 内で`parameterlist`を使用する、`As`句を各パラメーターに渡される引数のデータ型を指定します。  
  
    > [!NOTE]
    >  場合は、.NET Framework の外部プロシージャが書き込まれませんでした、する必要があります注意するデータ型の対応します。 たとえばを使用する Visual Basic 6.0 プロシージャへの外部参照を宣言する場合、`Integer`パラメーター (Visual Basic 6.0 では 16 ビット) として、対応する引数を指定する必要があります`Short`で、`Declare`ステートメントでは、16 ビットであるためVisual Basic のビットの整数型。 同様に、`Long`別のデータ幅が、Visual Basic 6.0 と`Date`は異なる方法で実装します。  
  
-   **データ型を返します。** 外部プロシージャがある場合、`Function`と`Option Strict`は`On`、呼び出し元のコードに返される値のデータ型を指定する必要があります。 これには、任意のデータ型または列挙型、構造体、クラス、またはインターフェイスの名前を指定できます。  
  
    > [!NOTE]
    >  Visual Basic コンパイラでは、データ型が外部プロシージャのものと互換性があるは検証されません。 不一致がある場合、共通言語ランタイムを生成、<xref:System.Runtime.InteropServices.MarshalDirectiveException>実行時に例外です。  
  
-   **既定のデータ型。** 場合`Option Strict`は`Off`内のパラメーターのデータ型を指定しないと`parameterlist`、Visual Basic コンパイラに対応する引数の変換、[オブジェクト データ型](../../../visual-basic/language-reference/data-types/object-data-type.md)です。 同様に、指定しない場合`returntype`、コンパイラは、戻り値のデータ型を受け取る`Object`です。  
  
    > [!NOTE]
    >  別のプラットフォームで書き込まれた外部プロシージャを扱うために、危険性のあるデータ型について、推測に基づいて作成したりすると、既定値です。 存在する場合は安全にすべてのパラメーターと戻り値のデータ型を指定します。 これも、コードの読みやすさを向上します。  
  
## <a name="behavior"></a>動作  
  
-   **スコープです。** 外部参照では、そのクラス、構造体、またはモジュール全体にわたってスコープ内です。  
  
-   **有効期間。** 外部参照は、クラス、構造体、またはモジュールが宣言されている有効期間と同じです。  
  
-   **外部プロシージャを呼び出しています。** 呼び出すのと同じ方法で外部プロシージャを呼び出す、`Function`または`Sub`プロシージャ、またはを指定することで、値を返す場合、式で使用して、 [Call ステートメント](../../../visual-basic/language-reference/statements/call-statement.md)値を返さない場合です。  
  
     指定したとおり正確に外部プロシージャに引数を渡す`parameterlist`で、`Declare`ステートメントです。 考慮されない方法、パラメーター宣言されている外部ファイルにします。 同様に、戻り値がある場合を使用して、指定したとおり正確に`returntype`で、`Declare`ステートメントです。  
  
-   **文字を設定します。** 指定できる`charsetmodifier`方法 Visual Basic が文字列マーシャ リングが外部プロシージャを呼び出すときにします。 `Ansi`修飾子に指示を ANSI 値に、すべての文字列をマーシャ リングする Visual Basic、および`Unicode`修飾子の指示を Unicode 値のすべての文字列をマーシャ リングします。 `Auto`修飾子は、Visual Basic .NET Framework に従って文字列をマーシャ リングにルールが外部参照に基づくように指示`name`、または`aliasname`指定されている場合。 既定値は `Ansi` です。  
  
     `charsetmodifier` また、Visual Basic が外部ファイルの内部で外部プロシージャを検索する方法を指定します。 `Ansi` および`Unicode`検索するか、検索中にその名前を変更することがなく Visual Basic の直接両方です。 `Auto` Visual Basic ランタイム プラットフォームの基本文字セットを確認し、場合によっては外部プロシージャ名は次のように変更が送信されます。  
  
    -   プラットフォームでは、ANSI、Windows 95、Windows 98 または Windows Millennium Edition などは、名前のまま変更せずに、外部の手順をまず検索します。 失敗した場合は、外部プロシージャ名の末尾に"A"を追加し、再度検索します。  
  
    -   Windows NT、Windows 2000、Windows XP などの Unicode プラットフォームでは、名前のまま変更せずに、外部の手順をまず検索します。 失敗した場合、追加"W"最後に、外部プロシージャの名前を指定し、再度検索します。  
  
-   **メカニズムです。** Visual Basic、.NET Framework を使用して*プラットフォーム呼び出し*(PInvoke) メカニズムを解決し、外部プロシージャにアクセスします。 `Declare`ステートメントおよび<xref:System.Runtime.InteropServices.DllImportAttribute>両方のクラスが自動的に、このメカニズムを使用して、PInvoke を認識する必要はありません。 詳細については、次を参照してください。[チュートリアル: Windows Api の呼び出し](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)です。  
  
> [!IMPORTANT]
>  外部プロシージャは、共通言語ランタイム (CLR) の外部で実行する場合、は*アンマネージ コード*です。 プロシージャを呼び出す場合などは、Win32 API 関数または COM メソッドの場合は、たとえば、セキュリティ リスクに対するアプリケーションを公開する可能性があります。 詳細については、次を参照してください。[安全なコーディングのガイドライン、アンマネージ コード](../../../framework/security/secure-coding-guidelines-for-unmanaged-code.md)です。  
  
## <a name="example"></a>例  
 次の例への外部参照の宣言、`Function`を現在のユーザー名を返すプロシージャです。 外部プロシージャを呼び出して`GetUserNameA`の一部として、`getUser`プロシージャです。  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_1.vb)]  
  
## <a name="example"></a>例  
 <xref:System.Runtime.InteropServices.DllImportAttribute>関数を使用するアンマネージ コードでの代替手段を提供します。 次の例では、インポートされた関数を宣言を使用せず、`Declare`ステートメントです。  
  
 [!code-vb[VbVbalrStatements#16](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_2.vb)]  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_3.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>  
 [Imports ステートメント (.NET 名前空間および型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [AddressOf 演算子](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [Call ステートメント](../../../visual-basic/language-reference/statements/call-statement.md)  
 [チュートリアル : Windows API の呼び出し](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
