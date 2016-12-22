---
title: "方法 : 文字列の内容を変更する (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "文字列 [C#], 変更"
ms.assetid: b6c20bba-ce22-43d7-ad1b-5ce65f714055
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法 : 文字列の内容を変更する (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

文字列は*変更不可*であるため、\(アンセーフ コードを使用しない限り\) 文字列オブジェクトを作成した後、その値は変更できません。  ただし、文字列の値を変更し、その結果を新しい文字列オブジェクトに格納する方法は数多くあります。  <xref:System.String?displayProperty=fullName> クラスには、入力文字列を操作し、新しい文字列オブジェクトを返すメソッドが用意されています。  多くの場合、元の文字列を格納している変数に新しいオブジェクトを代入できます。  <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> クラスには、同じように動作する追加のメソッドが用意されています。  <xref:System.Text.StringBuilder?displayProperty=fullName> クラスには、"埋め込み先" を変更できる文字バッファーが用意されています。バッファーの現在の内容を格納する新しい文字列オブジェクトを作成するには、<xref:System.Text.StringBuilder.ToString%2A?displayProperty=fullName> メソッドを呼び出します。  
  
## 使用例  
 指定した文字列内のサブストリングを置き換える、または削除するさまざまな方法を次の例に示します。  
  
 [!code-cs[csProgGuideStrings#28](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_1.cs)]  
  
## 使用例  
 配列表記を使用して文字列内の個々の文字にアクセスするには、`[]` 演算子をオーバーロードして内部文字バッファーにアクセスする方法を提供する <xref:System.Text.StringBuilder> オブジェクトを使用します。  また、<xref:System.String.ToCharArray%2A> メソッドを使用することで、文字列を文字の配列に変換することもできます。  次の例では、`ToCharArray` を使用して配列を作成しています。  その後、この配列の要素の一部を変更しています。  さらに、入力パラメーターとして文字配列を受け取る文字列コンストラクターを呼び出して、新しい文字列を作成しています。  
  
 [!code-cs[csProgGuideStrings#24](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_2.cs)]  
  
## 使用例  
 次の例は、C スタイルの文字配列と同様の方法でアンセーフ コードを使用して埋め込み文字列を変更する、非常にまれな場合のために用意したものです。  この例では、fixed キーワードを使用して "埋め込まれている" 個々の文字にアクセスする方法を示します。  また、文字列に対しアンセーフ操作を実行すると発生する可能性のある副作用を示します。この副作用の原因は、C\# コンパイラが文字列を内部に格納する \(保持する\) 方法です。  通常、この方法は、特に必要な場合以外は使用しないでください。  
  
 [!code-cs[csProgGuideStrings#29](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-modify-string-contents_3.cs)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [文字列](../../../csharp/programming-guide/strings/index.md)