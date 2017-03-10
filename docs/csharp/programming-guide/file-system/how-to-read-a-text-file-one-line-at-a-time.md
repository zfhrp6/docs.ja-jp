---
title: "方法: テキスト ファイルを一度に 1 行読み込む (Visual C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "読み取り (テキスト ファイルを), 行単位"
  - "ReadLine メソッド [C#]"
  - "テキスト ファイル [C#]"
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
caps.latest.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 11
---
# 方法: テキスト ファイルを一度に 1 行読み込む (Visual C#)
`StreamReader` クラスの `ReadLine` メソッドを使用してテキスト ファイルの内容を一度に 1 行、文字列に読み込む例を次に示します。  各テキスト行は、文字列 `line` に格納され、画面に表示されます。  
  
## 使用例  
  
```  
int counter = 0;  
string line;  
  
// Read the file and display it line by line.  
System.IO.StreamReader file =   
    new System.IO.StreamReader(@"c:\test.txt");  
while((line = file.ReadLine()) != null)  
{  
    System.Console.WriteLine (line);  
    counter++;  
}  
  
file.Close();  
System.Console.WriteLine("There were {0} lines.", counter);  
// Suspend the screen.  
System.Console.ReadLine();  
```  
  
## コードのコンパイル  
 コードをコピーし、コンソール アプリケーションの `Main` メソッドに貼り付けます。  
  
 `"c:\test.txt"` を実際のファイル名に置き換えます。  
  
## 信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   ファイルが存在しない。  
  
## .NET Framework セキュリティ  
 ファイル名からファイルの内容を判断しないでください。  たとえば、`myFile.cs` ファイルが C\# ソース ファイルとは限りません。  
  
## 参照  
 <xref:System.IO?displayProperty=fullName>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ファイル システムとレジストリ](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)