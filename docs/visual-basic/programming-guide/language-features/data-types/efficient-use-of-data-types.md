---
title: "Efficient Use of Data Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "performance, data type efficiency"
  - "data types [Visual Basic], weak typing"
  - "AscW function, preferred to Asc"
  - "data types [Visual Basic], using efficiently"
  - "optimization, data types"
  - "data types [Visual Basic], strong typing"
  - "strong typing"
  - "typing, strong"
  - "data types [Visual Basic], optimizing"
  - "ChrW function, preferred to Chr"
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Efficient Use of Data Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

宣言されていない変数、およびデータ型を指定しないで宣言された変数には、`Object` データ型が割り当てられます。  したがって、プログラムの記述が簡単になりますが、実行速度は遅くなることがあります。  
  
## 厳密な型指定  
 すべての変数についてデータ型を指定することは、*厳密な型指定*と呼ばれます。  厳密な型指定を使用する利点は次のとおりです。  
  
-   これは、変数のIntellisenseのサポートを有効にします。  これにより、コードの入力時に、プロパティや他のメンバーを表示できます。  
  
-   コンパイラの型チェック機能を利用できます。  これにより、実行時にオーバーフローなどのエラーで失敗するステートメントが検出されます。  また、オブジェクトでサポートされていないメソッドの呼び出しも検出されます。  
  
-   コードの実行速度が速くなります。  
  
## 最も効率的なデータ型  
 小数を含まない変数では、整数型が非整数型よりも有効です。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、`Integer` および `UInteger` が最も効率的な数値型です。  
  
 小数値の場合、現在のプラットフォームのプロセッサでは浮動小数点演算が倍精度で実行されるため、`Double` が最も効率的なデータ型です。  しかし、`Double` を使用した演算は、`Integer` などの整数型を使用した演算ほどは速くありません。  
  
## データ型の指定  
 特定の型の変数を宣言するには、[Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) を使用します。  次の例のように、[Public](../../../../visual-basic/language-reference/modifiers/public.md) キーワード、[Protected](../../../../visual-basic/language-reference/modifiers/protected.md) キーワード、[Friend](../../../../visual-basic/language-reference/modifiers/friend.md) キーワード、または [Private](../../../../visual-basic/language-reference/modifiers/private.md) キーワードを使用して同時にアクセス レベルも指定できます。  
  
```  
Private x As Double  
Protected s As String  
```  
  
## 文字の変換  
 `AscW` 関数と `ChrW` 関数は Unicode で動作します。  Unicode との変換が必要な `Asc` や `Chr` よりも、これらを優先的に使用することをお勧めします。  
  
## 参照  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>   
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>   
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Numeric Data Types](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)   
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [IntelliSense の使用方法](/visual-studio/ide/using-intellisense)