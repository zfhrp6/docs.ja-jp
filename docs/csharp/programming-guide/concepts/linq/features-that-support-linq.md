---
title: "C# Features That Support LINQ | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "LINQ [C#], features supporting LINQ"
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
caps.latest.revision: 23
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# C# Features That Support LINQ
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

このセクションでは、C\# 3.0 で導入された新しい言語構成要素について説明します。  これらの新機能は [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリでも使用されますが、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] だけでなく、これらの新機能が役立つと思われるあらゆる状況で使用できます。  
  
## クエリ式  
 クエリ式は、SQL や XQuery に似た宣言構文を使用して、IEnumerable コレクションを照会します。  クエリの構文は、コンパイル時に、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] プロバイダーの標準クエリ演算子拡張メソッドの実装に対するメソッド呼び出しに変換されます。  アプリケーションは、`using` ディレクティブを使用して適切な名前空間を指定することで、スコープ内の標準クエリ演算子を制御します。  次のクエリ式では、文字列の配列を受け取り、文字列の最初の文字に基づいて文字列をグループ化し、グループを並べ替えています。  
  
```  
var query = from str in stringArray  
            group str by str[0] into stringGroup  
            orderby stringGroup.Key  
            select stringGroup;  
```  
  
 詳細については、「[LINQ クエリ式](../../../../csharp/programming-guide/linq-query-expressions/index.md)」を参照してください。  
  
## 暗黙的に型指定される変数 \(var\)  
 変数を宣言して初期化するときに変数の型を明示的に指定する代わりに、次に示すように [var](../../../../csharp/language-reference/keywords/var.md) 修飾子を使用すると、型を推論して代入するようにコンパイラに指示できます。  
  
```  
var number = 5;  
var name = "Virginia";  
var query = from str in stringArray  
            where str[0] == 'm'  
            select str;  
```  
  
 `var` として宣言された変数は、明示的に型を指定した変数と同じように厳密に型指定されます。  `var` を使用すると匿名型を作成できますが、それ以外にも、任意のローカル変数に使用できます。  暗黙的な型指定を使用して、配列を宣言することもできます。  
  
 詳細については、「[暗黙的に型指定されるローカル変数](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)」を参照してください。  
  
## オブジェクト初期化子とコレクション初期化子  
 オブジェクト初期化子とコレクション初期化子を使用すると、オブジェクトのコンストラクターを明示的に呼び出さなくても、オブジェクトを初期化できます。  通常、初期化子は、ソース データを新しいデータ型に投影するクエリ式で使用されます。  パブリックな `Name` プロパティおよび `Phone` プロパティを持つ `Customer` という名前のクラスがある場合、オブジェクト初期化子は次のコードのように使用できます。  
  
```  
Customer cust = new Customer { Name = "Mike", Phone = "555-1212" };  
```  
  
 詳細については、「[オブジェクト初期化子とコレクション初期化子](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)」を参照してください。  
  
## 匿名型  
 匿名型はコンパイラによって構築され、型名はコンパイラにしかわかりません。  匿名型を使用すると、個別の名前付き型を定義しなくても、クエリ結果に一時的に含まれるプロパティのセットをグループ化できるので便利です。  次に示すように、匿名型は、new 式およびオブジェクト初期化子を使用して初期化されます。  
  
```  
select new {name = cust.Name, phone = cust.Phone};  
```  
  
 詳細については、「[匿名型](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)」を参照してください。  
  
## 拡張メソッド  
 拡張メソッドは型に関連付けることができる静的メソッドで、その型のインスタンス メソッドと同じように呼び出すことができます。  この機能を使用すると、既存の型を実際に変更しなくても、その型に新しいメソッドを実質的に "追加" できます。  標準クエリ演算子は、<xref:System.Collections.Generic.IEnumerable%601> を実装する任意の型で [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリ機能を実現する拡張メソッドのセットです。  
  
 詳細については、「[拡張メソッド](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)」を参照してください。  
  
## ラムダ式  
 ラムダ式は、\=\> 演算子を使用して関数本体から入力パラメーターを分離するインライン関数であり、コンパイル時にはデリゲートまたは式ツリーに変換されます。  [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] プログラミングでは、標準クエリ演算子に対する直接メソッド呼び出しを行う場合にラムダ式を使用します。  
  
 詳細については、次のトピックを参照してください。  
  
-   [匿名関数](../../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)  
  
-   [ラムダ式](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [式ツリー](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)  
  
## 自動実装プロパティ  
 自動実装プロパティによって、プロパティ宣言が簡略化されます。  次の例のようなプロパティを宣言すると、コンパイラによってプライベートな匿名バッキング フィールドが作成されます。このフィールドには、プロパティの getter および setter を使用する方法でしかアクセスできません。  
  
```  
public string Name {get; set;}  
```  
  
 詳細については、「[自動実装プロパティ](../../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)」を参照してください。  
  
## 参照  
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Visual Basic Features That Support LINQ](../../../../visual-basic/programming-guide/concepts/linq/features-that-support-linq.md)