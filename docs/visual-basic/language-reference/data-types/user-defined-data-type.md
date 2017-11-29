---
title: "ユーザー定義型"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- UserDefined
- UDT
- vb.UDT
- User-Defined
- vb.UserDefined
- vb.User-Defined
helpviewer_keywords:
- user-defined data types [Visual Basic], Visual Basic
- user-defined types
- structures [Visual Basic], as user-defined data types
- user-defined types [Visual Basic], Visual Basic
- user-defined types [Visual Basic], structure declaration
- user-defined types [Visual Basic], structures in Visual Basic
- user-defined data types [Visual Basic], structure declaration
- data types [Visual Basic], assigning
- Structure statement [Visual Basic]
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], structures in Visual Basic
- user-defined data types
- types [Visual Basic], user-defined
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e1876d61a2ce89b04c6e5061b868f0be365639f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="user-defined-data-type"></a>ユーザー定義型
定義する形式でデータを保持します。 `Structure`ステートメント形式を定義します。  
  
 以前のバージョンの Visual Basic では、ユーザー定義型 (UDT) をサポートします。 現在のバージョンを展開する UDT、*構造*です。 構造体は、1 つ以上の連結*メンバー*さまざまなデータ型。 Visual Basic は、そのメンバーを個別にもアクセスできますが、1 つの単位として構造体を扱います。  
  
## <a name="remarks"></a>コメント  
 定義して、さまざまなデータ型を 1 つの単位に結合する必要がある場合、またはニーズに対応基本データ型のいずれも、構造体のデータ型を使用します。  
  
 構造体のデータ型の既定値は、各メンバーの既定値の組み合わせで構成されます。  
  
## <a name="declaration-format"></a>宣言の形式  
 構造体の宣言が始まり、 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)で終わると、`End``Structure`ステートメントです。 `Structure`ステートメントは、構造体を定義するデータ型の識別子でもある構造体の名前を提供します。 コードの他の部分では、この識別子を使用して、変数、パラメーター、および関数の戻り値をこの構造体のデータ型の値を宣言します。  
  
 宣言の間、`Structure`と`End``Structure`ステートメントは、構造体のメンバーを定義します。  
  
## <a name="member-access-levels"></a>メンバーのアクセス レベル  
 使用してすべてのメンバーを宣言する必要があります、 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)またはアクセス レベルをなどを指定するステートメント[パブリック](../../../visual-basic/language-reference/modifiers/public.md)、[フレンド](../../../visual-basic/language-reference/modifiers/friend.md)、または[プライベート](../../../visual-basic/language-reference/modifiers/private.md). 使用する場合、`Dim`ステートメントでは、パブリックにアクセス レベルの既定値です。  
  
## <a name="programming-tips"></a>プログラミングのヒント  
  
-   **メモリ使用量。**  他のすべての複合データ型と同様に、構造体の総メモリ使用量を計算する場合、各メンバーのストレージ割り当ての公称サイズを単に合計しただけでは安全ではありません。 さらに、メモリ内に格納される順序が宣言の順序と同じであると仮定するのも安全ではありません。 構造体のストレージ レイアウトを制御する必要がある場合は、<xref:System.Runtime.InteropServices.StructLayoutAttribute> 属性を `Structure` ステートメントに適用します。  
  
-   **相互運用の考慮事項。** .NET Framework 用に作成されていないコンポーネントとやり取りする場合は、たとえばオートメーションまたは COM オブジェクト、他の環境でのユーザー定義の型が Visual Basic と互換性がないことに注意してくださいには、型が構造化します。  
  
-   **拡大します。** どの構造データ型に/からの自動変換はありません。 構造体を使用して、変換演算子を定義することができます、 [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)、するには、各変換演算子を宣言して`Widening`または`Narrowing`です。  
  
-   **型宣言文字。** 構造体のデータ型があるないリテラルの型文字または識別子の型文字です。  
  
-   **Framework の型。** .NET Framework では、対応する型はありません。 すべての構造は、.NET Framework クラスから継承<xref:System.ValueType?displayProperty=nameWithType>に対応する個々 の構造がありませんが、<xref:System.ValueType?displayProperty=nameWithType>です。  
  
## <a name="example"></a>例  
 構造体の宣言の概要を次に示します。  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ValueType>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 [データの種類](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)  
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
