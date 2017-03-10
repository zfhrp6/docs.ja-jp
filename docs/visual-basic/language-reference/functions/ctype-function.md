---
title: "CType 関数 (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.CType"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "式の変換結果"
  - "明示的なデータ型の変換"
  - "CType 関数"
  - "変換、式"
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# CType 関数 (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

任意の式を、指定されたデータ型、オブジェクト、構造体、クラス、またはインターフェイスに明示的に変換し、その結果を返します。  
  
## 構文  
  
```  
CType(expression, typename)  
```  
  
## 指定項目  
 `expression`  
 任意の有効な式。  `expression` の値が `typename` で許可されている範囲内でない場合、Visual Basic が例外をスローします。  
  
 `typename`  
 `Dim` ステートメントの `As` 句で有効な任意の式。つまり、任意のデータ型、オブジェクト、構造体、クラス、またはインターフェイスの名前を指定します。  
  
## 解説  
  
> [!TIP]
>  次の関数を使用して型変換を実行することもできます。  
>   
>  -   特定のデータ型への変換を実行する、`CByte`、`CDbl`、`CInt` などの型変換関数。  詳細については、「[Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)」を参照してください。  
> -   [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) または [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md)。  これらの演算子では、一方の型が他方の型を継承または実装している必要があります。  これらの場合は、`Object` データ型との間で変換を行うときに、`CType` よりもいくらかパフォーマンスが向上します。  
  
 `CType` は、インラインでコンパイルされます。つまり、変換コードは、式を評価するコードに含まれます。  場合によっては、変換を実行するプロシージャが呼び出されないため、コードの実行速度が速くなります。  
  
 `Integer` から `Date` など、`expression` から `typename` への変換が定義されていない場合、Visual Basic はコンパイル時のエラー メッセージを表示します。  
  
 実行時に変換が失敗すると、適切な例外がスローされます。  縮小変換が失敗した場合、最もよくスローされるのは <xref:System.OverflowException> です。  変換が定義されていない場合、<xref:System.InvalidCastException> がスローされます。  たとえば、これは、`expression` が `Object` 型で、実行時の型が `typename` への変換を持たない場合に起こります。  
  
 `expression` または `typename` のデータ型が、定義したクラスまたは構造体の場合、そのクラスまたは構造体に `CType` を変換演算子として定義できます。  これにより、`CType` は*オーバーロードされた演算子*として機能します。  この方法を利用する場合、定義したクラスまたは構造体からの変換、またはこのクラスまたは構造体への変換の動作 \(スローする例外など\) を制御できます。  
  
## オーバーロード  
 `CType` 演算子も、コードの外部で定義されたクラスまたは構造体でオーバーロードできます。  このようなクラスまたは構造体からの変換、またはこのクラスまたは構造体への変換を行う場合は、その `CType` 演算子の動作を確認してください。  詳細については、「[Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## 動的オブジェクトの変換  
 動的オブジェクトの型変換は、<xref:System.Dynamic.DynamicObject.TryConvert%2A> メソッドまたは <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> メソッドを使用するユーザー定義の動的変換によって実行されます。  動的オブジェクトを使用する場合は、<xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> メソッドを使用して動的オブジェクトを変換します。  
  
## 使用例  
 `CType` 関数を使用して任意の式を `Single` データ型に変換する例を次に示します。  
  
 [!code-vb[VbVbalrFunctions#24](../../../visual-basic/language-reference/functions/codesnippet/visualbasic/ctype-function_1.vb)]  
  
 その他の例については、「[Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)」を参照してください。  
  
## 参照  
 <xref:System.OverflowException>   
 <xref:System.InvalidCastException>   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Conversion Functions](../../../visual-basic/language-reference/functions/conversion-functions.md)   
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [.NET Framework における型変換](../Topic/Type%20Conversion%20in%20the%20.NET%20Framework.md)