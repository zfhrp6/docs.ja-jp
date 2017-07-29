---
title: "方法: テキスト ファイルを一度に 1 行読み込む (Visual C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e9327181d82a97559c7be99bb76a2a93118d796b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-read-a-text-file-one-line-at-a-time-visual-c"></a>方法: テキスト ファイルを一度に 1 行読み込む (Visual C#)
次の例では、`StreamReader` クラスの `ReadLine` メソッドを使用して、テキスト ファイルの内容を一度に 1 行ずつ文字列に読み込みます。 各テキスト行は文字列 `line` に格納され、画面に表示されます。  
  
## <a name="example"></a>例  
  
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
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 コードをコピーし、コンソール アプリケーションの `Main` メソッドに貼り付けます。  
  
 `"c:\test.txt"` を実際のファイル名に置き換えます。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   ファイルが存在しない。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 ファイル名からファイルの内容を判断しないでください。 たとえば、`myFile.cs` ファイルが C# ソース ファイルとは限りません。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IO?displayProperty=fullName>   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ファイル システムとレジストリ (C# プログラミング ガイド)](../../../csharp/programming-guide/file-system/index.md)

