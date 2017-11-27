---
title: "整数型 (Integer) (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69c7fb6caf5d9a10c7d033d1ba0a05c9230d472c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="integer-data-type-visual-basic"></a>整数データ型 (Visual Basic)
-2,147,483,648 から 2,147,483,647 までの符号付き 32 ビット (4 バイト) の整数を保持します。  
  
## <a name="remarks"></a>コメント
 `Integer` データ型は、32 ビットのプロセッサでパフォーマンスが最大になります。 他の整数型では、メモリとの間の読み込みと格納により長い時間がかかります。  
  
 `Integer` の既定値は 0 です。  

## <a name="literal-assignments"></a>リテラルの割り当て

宣言して初期化することができます、`Integer`変数の 10 進数リテラル、16 進数のリテラルに 8 進数のリテラルを割り当てまたは (Visual Basic 2017 以降)、バイナリ リテラルです。 整数リテラルが `Integer` の範囲外にある場合 (つまり、<xref:System.Int32.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.Int32.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。

次の例では、整数 16,342 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`Integer` 値に割り当てられています。

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> プレフィックスを使用する`&h`または`&H`、16 進数リテラル プレフィックスを表すために`&b`または`&B`バイナリ リテラル、およびプレフィックスを意味する`&o`または`&O`を 8 進数のリテラルを示すためにします。 10 進リテラルには、プレフィックスはありません。

Visual Basic 2017 から始めて、使用することできますもアンダー スコア文字`_`、読みやすさを強化するために、桁区切り記号として次の例として示します。

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

数値リテラルを含めることも、 `I` [文字入力](../../programming-guide\language-features\data-types/type-characters.md)を示すために、`Integer`データ型は、次の例のようにします。

```vb
Dim number = &H035826I
```

## <a name="programming-tips"></a>プログラミングのヒント

-   **相互運用の考慮事項。** オートメーションまたは COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントとやり取りする場合の点に注意`Integer`が他の環境で別のデータ幅 (16 ビット) を持ちます。 そのようなコンポーネントに 16 ビットの引数を渡す場合は、新しい Visual Basic のコードで、整数型 (`Short`) ではなく短整数型 (`Integer`) として宣言します。  
  
-   **拡大します。** `Integer` データ型は、`Long`、`Decimal`、`Single`、または `Double` に拡大変換されます。 これは、`Integer` エラーを発生させることなく、これらの型のいずれかに <xref:System.OverflowException?displayProperty=nameWithType> を変換できることを意味します。  
  
-   **型宣言文字。** あるリテラルにリテラルの型文字 `I` を付けると、そのリテラルは `Integer` に変換されます。 ある識別子に識別子の型文字 `%` を付けると、その識別子は整数型 (`Integer`) に変換されます。  
  
-   **Framework の型。** .NET Framework において対応する型は、<xref:System.Int32?displayProperty=nameWithType> 構造体です。  
  
## <a name="range"></a>範囲

整数型の変数をその型の範囲外の数値に設定しようとすると、エラーが発生します。 小数に設定しようとすると、最も近い整数値に丸められます。 2 つの整数値に等しく近い場合は、最も近い偶数の整数に丸められます。 この処理により、常に中間値を単一方向に丸めるために発生する丸め誤差が最小限に抑えられます。 丸めの例を次のコードに示します。  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a>関連項目

<xref:System.Int32?displayProperty=nameWithType>   
 [データの種類](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Long データ型](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [Short データ型](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
