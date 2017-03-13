---
title: "Declare Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Declare"
  - "vb.Lib"
  - "vb.Any"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Lib keyword"
  - "declaring procedures, Declare statement"
  - "functions [Visual Basic], function procedures"
  - "declarations, procedures"
  - "procedures, declaration"
  - "procedures, external"
  - "Alias keyword"
  - "external references, Visual Basic"
  - "DLLs, declaring procedures"
  - "Declare statement"
  - "declarations, external"
  - "Visual Basic code, Function procedures"
  - "As keyword, in Declare statement"
  - "resources [Visual Basic], declaring"
  - "Public keyword, Declare statement"
  - "platform invoke, Visual Basic external references"
  - "Sub procedures, declarations"
  - "APIs, declaring API functions"
  - "Visual Basic code, Sub procedures"
  - "Function procedures, declaring"
ms.assetid: d3f21fb0-b804-4c99-97ed-583b23894cf1
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 30
---
# Declare Statement
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

外部ファイル内で実装されているプロシージャへの参照を宣言します。  
  
## 構文  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _  
Declare [ charsetmodifier ] [ Sub ] name Lib "libname" _  
[ Alias "aliasname" ] [ ([ parameterlist ]) ]  
' -or-  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _  
Declare [ charsetmodifier ] [ Function ] name Lib "libname" _  
[ Alias "aliasname" ] [ ([ parameterlist ]) ] [ As returntype ]  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`attributelist`|省略可能です。  「[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)」を参照してください。|  
|`accessmodifier`|省略可能です。  次のいずれかになります。<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> 「[Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。|  
|`Shadows`|省略可能です。  「[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)」を参照してください。|  
|`charsetmodifier`|省略可能です。  文字セットとファイル検索情報を指定します。  次のいずれかになります。<br /><br /> -   [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md) \(既定値\)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [Auto](../../../visual-basic/language-reference/modifiers/auto.md)|  
|`Sub`|省略できます。ただし、`Sub` か `Function` のどちらかを指定する必要があります。  外部プロシージャが戻り値を返さないことを表します。|  
|`Function`|省略できます。ただし、`Sub` か `Function` のどちらかを指定する必要があります。  外部プロシージャが戻り値を返すことを表します。|  
|`name`|必ず指定します。  この外部参照の名前です。  詳細については、「[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。|  
|`Lib`|必ず指定します。  `Lib` 句は、外部プロシージャを含む外部ファイル \(DLL またはコード リソース\) であることを示します。|  
|`libname`|必ず指定します。  宣言するプロシージャが含まれているファイルの名前を指定します。|  
|`Alias`|省略可能です。  `name` で指定した名前では、宣言するプロシージャをそのファイル内で特定できないことを表します。  識別子は `aliasname` で指定します。|  
|`aliasname`|`Alias` キーワードを使用する場合は必ず指定します。  プロシージャを識別する文字列を、次のどちらかの方法で指定します。<br /><br /> ファイル内でのプロシージャのエントリ ポイント名を引用符 \(`""`\) で囲んで指定します。<br /><br /> または<br /><br /> シャープ記号 \(`#`\) の後ろに、ファイル内でのプロシージャのエントリ ポイントの序数を表す整数を指定します。|  
|`parameterlist`|プロシージャがパラメーターを受け取る場合は、必ず指定します。  「[Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md)」を参照してください。|  
|`returntype`|`Function` が指定されていて、`Option Strict` が `On` の場合は、必ず指定します。  プロシージャによって返される値のデータ型を指定します。|  
  
## 解説  
 場合によっては、プロジェクト外部のファイル \(DLL やコード リソースなど\) 内で定義されたプロシージャを呼び出すことがあります。  このとき、Visual Basic コンパイラは、目的のプロシージャを正しく呼び出すために必要な情報 \(プロシージャの定義場所、識別方法、呼び出しシーケンスや戻り値の型、使用される文字セットなど\) を知りません。  `Declare` ステートメントは、外部プロシージャへの参照を作成し、この必須情報を提供します。  
  
 `Declare` は、モジュール レベルでのみ使用できます。  つまり、外部参照の*宣言コンテキスト*は、クラス、構造体、またはモジュールであることが必要で、ソース ファイル、名前空間、インターフェイス、プロシージャ、ブロックでは宣言できません。  詳細については、「[Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 外部参照は、既定で [Public](../../../visual-basic/language-reference/modifiers/public.md) アクセスになります。  アクセス修飾子を使用してこれらのアクセス レベルを調整できます。  
  
## 規則  
  
-   **属性。**外部参照には属性を適用できます。  適用した属性はプロジェクト内でのみ有効であり、外部ファイル内では無効です。  
  
-   **修飾子。**外部プロシージャは暗黙的に [Shared](../../../visual-basic/language-reference/modifiers/shared.md) になります。  外部参照を宣言するときに `Shared` キーワードを使用することはできません。また、この共有ステータスは変更できません。  
  
     外部プロシージャは、オーバーライドに参加したり、インターフェイス メンバーを実装したり、イベントを処理したりすることはできません。  そのため、`Declare` ステートメント内では `Overrides`、`Overridable`、`NotOverridable`、`MustOverride`、`Implements`、または `Handles` キーワードを使用できません。  
  
-   **外部プロシージャ名。**この外部参照の名前 \(`name`\) を、外部ファイル内でのプロシージャのエントリ ポイント名 \(`aliasname`\) と同じにする必要はありません。  エントリ ポイント名を指定するには `Alias` 句を使用します。  この方法は、目的の外部プロシージャが Visual Basic の予約済みの修飾子や同じスコープ内の変数、プロシージャ、その他のプログラミング要素と同じ名前を持っている場合に役立ちます。  
  
    > [!NOTE]
    >  ほとんどの DLL 内のエントリ ポイント名は、大文字と小文字を区別します。  
  
-   **外部プロシージャ番号。**別の方法として、`Alias` 句を使用して、外部ファイルのエクスポート テーブル内でのエントリ ポイントの序数を指定することもできます。  この方法を使用する場合は、`aliasname` の先頭をシャープ記号 \(`#`\) にします。  この方法は、外部プロシージャ名のいずれかの文字が Visual Basic 内で許可されていない場合や、外部ファイルがプロシージャを名前なしでエクスポートする場合に役立ちます。  
  
## データ型のルール  
  
-   **パラメーターのデータ型。** `Option Strict` が `On` の場合は、`parameterlist` 内の各パラメーターのデータ型を指定する必要があります。  任意のデータ型、または列挙体、構造体、クラス、インターフェイスの名前を指定できます。  各パラメーターに渡される引数のデータ型を指定するには、`parameterlist` 内で `As` 句を使用します。  
  
    > [!NOTE]
    >  外部プロシージャが .NET Framework 用に記述されていない場合は、データ型の対応に注意する必要があります。  たとえば、`Integer` 型 \(Visual Basic 6.0 では 16 ビット\) のパラメーターを持つ Visual Basic 6.0 プロシージャへの外部参照を宣言する場合は、その `Declare` ステートメント内で、対応する引数を `Short` 型として指定する必要があります \(これが Visual Basic の 16 ビットの整数型に相当します\)。  同様に、`Long` は Visual Basic 6.0 では異なるデータ幅を持ち、`Date` は実装方法が異なります。  
  
-   **戻り値の型。**外部プロシージャが `Function` で、`Option Strict` が `On` の場合は、呼び出し元コードに返される値のデータ型を指定する必要があります。  任意のデータ型、または列挙体、構造体、クラス、インターフェイスの名前を指定できます。  
  
    > [!NOTE]
    >  Visual Basic コンパイラは、指定したデータ型が外部プロシージャのものと互換性を持つかどうかを検証しません。  一致しない場合は、実行時に共通言語ランタイムが <xref:System.Runtime.InteropServices.MarshalDirectiveException> 例外を生成します。  
  
-   **既定のデータ型。** `Option Strict` が `Off` で、`parameterlist` 内でパラメーターのデータ型を指定していない場合は、Visual Basic コンパイラは対応する引数を [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md)に変換します。  同様に、`returntype` を指定していない場合は、コンパイラは戻り値のデータ型を `Object` にします。  
  
    > [!NOTE]
    >  使用しようとする外部プロシージャが別のプラットフォーム上で記述されている可能性もあるので、データ型を憶測で扱ったり、データ型を既定のままにしたりするのは危険です。  すべてのパラメーターと戻り値 \(ある場合\) に対してデータ型を指定した方が安全です。  こうすると、コードも読みやすくなります。  
  
## \[動作\]  
  
-   **スコープ。**外部参照のスコープは、そのクラス、構造体、またはモジュール全体になります。  
  
-   **有効期間。**外部参照の有効期間は、それが宣言されているクラス、構造体、またはモジュールと同じになります。  
  
-   **外部プロシージャの呼び出し。**外部プロシージャの呼び出し方は、`Function` または `Sub` プロシージャを呼び出すときと同じです。つまり、そのプロシージャが値を返す場合は式の中で使用し、値を返さない場合は [Call Statement](../../../visual-basic/language-reference/statements/call-statement.md) で指定します。  
  
     外部プロシージャに引数を渡すときは、`Declare` ステートメントの `parameterlist` で指定したとおりに指定します。  外部ファイルの中でパラメーターがどのように宣言されているかを気にする必要はありません。  同様に、戻り値がある場合は、`Declare` ステートメントの `returntype` で指定したとおりの方法で使用します。  
  
-   **文字セット。** `charsetmodifier` では、外部プロシージャを呼び出すときに Visual Basic が文字列をどのようにマーシャリングするかを指定できます。  `Ansi` 修飾子は、すべての文字列を ANSI 値にマーシャリングすることを表します。`Unicode` 修飾子は、すべての文字列を Unicode 値にマーシャリングすることを表します。  `Auto` 修飾子は、文字列を外部参照の `name` または `aliasname` \(指定した場合\) に基づく .NET Framework の規則に従ってマーシャリングすることを表します。  既定値 `Ansi` です。  
  
     さらに、`charsetmodifier` は、Visual Basic が外部ファイル内で外部プロシージャを検索する方法も指定します。  `Ansi` および `Unicode` を指定した場合、Visual Basic は検索中に名前を修飾しません。  `Auto` を指定した場合、Visual Basic は実行時プラットフォームの基本文字セットを調べて、外部プロシージャの名前を次のように修飾します。  
  
    -   Windows 95、Windows 98、Windows Millennium Edition などの ANSI プラットフォームでは、まず名前修飾なしで外部プロシージャを検索します。  見つからなかった場合は、外部プロシージャ名の末尾に "A" を付けて再度検索します。  
  
    -   Windows NT、Windows 2000、Windows XP などの Unicode プラットフォームでは、まず名前修飾なしで外部プロシージャを検索します。  見つからなかった場合は、外部プロシージャ名の末尾に "W" を付けて再度検索します。  
  
-   **しくみ。**Visual Basic は、.NET Framework の*プラットフォーム呼び出し* \(PInvoke\) 機構を使用して外部プロシージャの解決とアクセスを行います。  `Declare` ステートメントと <xref:System.Runtime.InteropServices.DllImportAttribute> クラスは両方ともこの機構を自動的に使用するので、PInvoke についての知識は必要ありません。  詳細については、「[Walkthrough: Calling Windows APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)」を参照してください。  
  
> [!IMPORTANT]
>  共通言語ランタイム \(CLR\) の外部で実行される外部プロシージャは*アンマネージ コード*と呼ばれます。  たとえば Win32 API 関数や COM メソッドなどが該当しますが、このようなプロシージャを呼び出すとセキュリティ上のリスクが考えられます。  詳細については、「[アンマネージ コードの安全なコーディングのガイドライン](../Topic/Secure%20Coding%20Guidelines%20for%20Unmanaged%20Code.md)」を参照してください。  
  
## 使用例  
 次の例では、現在のユーザーの名前を返す `Function` プロシージャへの外部参照を宣言します。  その後、外部プロシージャ `GetUserNameA` を `getUser` プロシージャの一部として呼び出します。  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_1.vb)]  
  
## 使用例  
 <xref:System.Runtime.InteropServices.DllImportAttribute> を使うと、アンマネージ コード内の関数を別の方法で使うことができます。  インポートした関数を `Declare` ステートメントを使わずに宣言する例を次に示します。  
  
 [!code-vb[VbVbalrStatements#16](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_2.vb)]  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_3.vb)]  
  
## 参照  
 <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>   
 [Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md)   
 [Call Statement](../../../visual-basic/language-reference/statements/call-statement.md)   
 [Walkthrough: Calling Windows APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)