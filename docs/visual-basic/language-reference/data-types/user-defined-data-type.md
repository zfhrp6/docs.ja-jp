---
title: "User-Defined Data Type | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "UserDefined"
  - "UDT"
  - "vb.UDT"
  - "User-Defined"
  - "vb.UserDefined"
  - "vb.User-Defined"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "user-defined data types, Visual Basic"
  - "user-defined types"
  - "structures, as user-defined data types"
  - "user-defined types, Visual Basic"
  - "user-defined types, structure declaration"
  - "user-defined types, structures in Visual Basic"
  - "user-defined data types, structure declaration"
  - "data types [Visual Basic], assigning"
  - "Structure statement"
  - "data types [Visual Basic], user-defined"
  - "user-defined data types, structures in Visual Basic"
  - "user-defined data types"
  - "types [Visual Basic], user-defined"
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# User-Defined Data Type
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

定義した形式でデータを保持します。  `Structure` ステートメントは形式を定義します。  
  
 Visual Basic の以前のバージョンでは、ユーザー定義型 \(UDT\) がサポートされていました。  現在のバージョンでは、UDT を*構造体*に拡張したものが使用されています。  構造体は、さまざまなデータ型の 1 つ以上の*メンバー*を連結したものです。  Visual Basic では、構造体は単独のユニットとして扱われますが、そのメンバーに個別にアクセスすることもできます。  
  
## 解説  
 複数のデータ型を結合して単一のユニットにする場合、または、どの基本データ型も要件を満たしていない場合に、構造体データ型を定義および使用します。  
  
 構造体データ型の既定値は、各メンバーの既定値を組み合わせたものです。  
  
## 宣言の形式  
 構造体宣言は、[Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) ステートメントと `End` `Structure` ステートメントの間に記述します。  `Structure` ステートメントで構造体の名前を指定します。この名前は、構造体によって定義されるデータ型の識別子にもなります。  コードの他の部分では、この識別子を使用して、この構造体のデータ型で変数、パラメーター、関数の戻り値を宣言できます。  
  
 `Structure` ステートメントと `End` `Structure` ステートメントの間の宣言によって、構造体のメンバーが定義されます。  
  
## メンバーのアクセス レベル  
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) または、[Public](../../../visual-basic/language-reference/modifiers/public.md)、[Friend](../../../visual-basic/language-reference/modifiers/friend.md)、[Private](../../../visual-basic/language-reference/modifiers/private.md) などのアクセス レベルを指定するステートメントを使用して、すべてのメンバーを宣言する必要があります。  `Dim` ステートメントを使用すると、アクセス レベルは既定の public になります。  
  
## プログラミングのヒント  
  
-   **メモリの使用量。** 他のすべての複合データ型と同様に、構造体の総メモリ使用量を計算する場合、各メンバーのストレージ割り当ての公称サイズを単に合計しただけでは安全ではありません。  さらに、メモリ内に格納される順序が宣言の順序と同じであると仮定するのも安全ではありません。  構造体のストレージ レイアウトを制御する必要がある場合は、<xref:System.Runtime.InteropServices.StructLayoutAttribute> 属性を `Structure` ステートメントに適用します。  
  
-   **相互運用の考慮事項。**オートメーションまたは COM オブジェクトのように、.NET Framework 向けに作成されていないコンポーネントとやり取りする場合、他の環境のユーザー定義型は Visual Basic の構造体型と互換性がないことに注意してください。  
  
-   **拡大変換。**構造体データ型から、または構造体データ型に自動変換することはできません。  [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md) を使用して構造体に変換演算子を定義し、各変換演算子を `Widening` または `Narrowing` として定義します。  
  
-   **型宣言文字。**構造体データ型には、リテラルの型文字も識別子の型文字もありません。  
  
-   **Framework のデータ型。**.NET Framework にはこれに対応するデータ型はありません。  すべての構造体は .NET Framework のクラス <xref:System.ValueType?displayProperty=fullName> から継承されていますが、<xref:System.ValueType?displayProperty=fullName> に対応する個別の構造体はありません。  
  
## 使用例  
 構造体の宣言の概要を次に示します。  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## 参照  
 <xref:System.ValueType>   
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)   
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Efficient Use of Data Types](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)