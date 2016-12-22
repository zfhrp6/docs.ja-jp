---
title: "#line (C# リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "#line"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#line ディレクティブ [C#]"
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# #line (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`#line` を使用すると、エラーや警告で出力するコンパイラの行番号とファイル名 \(省略可能\) を変更できます。  この例は、2 つの警告の行番号がどのように報告されるかを示しています。  `#line 200` ディレクティブによって行番号が強制的に 200 となり \(既定値は \#7\)、次の \#line ディレクティブまではファイル名が "Special" と報告されます。  \#line default ディレクティブによって行番号が既定値に戻り、前のディレクティブで番号が変更された行がカウントされます。  
  
```  
class MainClass  
{  
    static void Main()  
    {  
#line 200 "Special"  
        int i;    // CS0168 on line 200  
        int j;    // CS0168 on line 201  
#line default  
        char c;   // CS0168 on line 9  
        float f;  // CS0168 on line 10  
#line hidden // numbering not affected  
        string s;   
        double d; // CS0168 on line 13  
    }  
}  
```  
  
## 解説  
 `#line` ディレクティブは、ビルド プロセスの、自動化された中間ステップで使われる場合があります。  たとえば、元のソース コード ファイルから行を削除した場合でも、コンパイラがファイル内での削除前の行番号のままで出力を生成できるように、行を削除してから `#line` を指定して、削除前の行番号指定をシミュレートします。  
  
 `#line hidden` ディレクティブは、後続の行をデバッガーから隠します。これで、開発者がコードをステップ実行するときに、`#line hidden` から次の `#line` ディレクティブ \(もう 1 つの `#line hidden` ディレクティブでないことが前提\) までのすべての行がステップ オーバーされます。  このオプションを ASP.NET で使用すると、ユーザー定義のコードとコンピューターが生成したコードを区別できます。  この機能は主に ASP.NET で使用されますが、より多くのソース ジェネレーターで利用される可能性があります。  
  
 `#line hidden` ディレクティブは、エラー報告のファイル名や行番号には影響しません。  このため、隠ぺいされたブロック内でエラーが検出された場合、コンパイラは現在のファイル名とエラーの行番号を報告します。  
  
 `#line filename` ディレクティブにより、コンパイラ出力に表示するファイル名が指定されます。  既定では、ソース コード ファイルの実際の名前が使われます。  ファイル名は二重引用符 \(""\) で囲み、前に行番号を指定する必要があります。  
  
 ソース コード ファイルには、任意の数の `#line` ディレクティブを指定できます。  
  
## 例 1  
 次の例は、デバッガーがどのようにコード内の隠ぺいされた行を無視するかを示しています。  この例を実行すると、3 行のテキストが表示されます。  ただし、この例で示すようにブレークポイントを設定し、**F10** キーを押してコードをステップ実行すると、デバッガーは隠ぺいされた行を無視します。  また、隠ぺいされた行にブレークポイントを設定しても、デバッガーはその行を無視します。  
  
```  
// preprocessor_linehidden.cs  
using System;  
class MainClass   
{  
    static void Main()   
    {  
        Console.WriteLine("Normal line #1."); // Set break point here.  
#line hidden  
        Console.WriteLine("Hidden line.");  
#line default  
        Console.WriteLine("Normal line #2.");  
    }  
}  
```  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# プリプロセッサ ディレクティブ](../../../visual-basic/reference/command-line-compiler/index.md)