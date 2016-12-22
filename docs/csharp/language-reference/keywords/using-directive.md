---
title: "using ディレクティブ (C# リファレンス) | Microsoft Docs"
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
  - "using ディレクティブ [C#]"
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
caps.latest.revision: 31
caps.handback.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# using ディレクティブ (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`using` ディレクティブは、次の 3 つの用途で使用します。  
  
-   名前空間で型の使用を許可する場合。これにより、その名前空間内では型を修飾せずに使用できます。  
  
    ```c#  
    using System.Text;  
    ```  
  
-   アクセスを型名で修飾する必要なしに型の静的メンバーへのアクセスを許可する場合。  
  
    ```c#  
    using static System.Math;  
    ```  
  
-   名前空間または型のエイリアスを作成する場合。  これを *using エイリアス ディレクティブ*と呼びます。  
  
    ```c#  
    using Project = PC.MyCompany.Project;  
    ```  
  
 `using` キーワードは、*using ステートメント*の作成にも使用します。ファイルやフォントなどの <xref:System.IDisposable> オブジェクトを正しく処理できるようになります。  詳細については、「[using ステートメント](../../../visual-basic/language-reference/statements/using-statement.md)」を参照してください。  
  
## using static 型  
 アクセスを型名で修飾することなく型の静的メンバーにアクセスできます。  
  
```c#  
using static System.Console;   
using static System.Math;  
class Program   
{   
    static void Main()   
    {   
        WriteLine(Sqrt(3*3 + 4*4));   
    }   
}  
  
```  
  
 `Using static` は、指定した型で宣言されているアクセス可能な静的メンバーおよび入れ子になった型のみをインポートします。  継承されたメンバーはインポートされません。  using static ディレクティブを使用して、Visual Basic モジュールを含む、名前付きの型からインポートすることができます。  F\# の最上位の関数が、有効な C\# 識別子を名前に持つ名前付きの型の静的メンバーとしてメタデータに存在する場合は、その F\# 関数をインポートできます。  
  
 `Using static` を使用すると、指定した型で宣言された拡張メソッドを拡張メソッドの参照で使用できるようになります。  ただし、コード内で修飾なしで参照している場合は、拡張メソッドの名前はスコープにインポートされません。  
  
 同じコンパイル単位または名前空間の多様な using static ディレクティブによってさまざまな型からインポートされた同じ名前を持つメソッドが、メソッド グループを形成します。  これらのメソッド グループ内のオーバーロードの解決方法は、C\# の通常の規則に従います。  
  
## 解説  
 `using` ディレクティブのスコープは、このディレクティブが存在するファイルに限定されます。  
  
 `using` エイリアスを作成すると、名前空間または型への識別子を修飾しやすくなります。  using エイリアス ディレクティブの右側は、その前にある using ディレクティブに関係なく、必ず完全修飾型である必要があります。  
  
 `using` ディレクティブを作成すると、名前空間内の型を、名前空間を指定することなく使用できます。  `using` ディレクティブでは、指定した名前空間に入れ子になった別の名前空間へのアクセスは許可されません。  
  
 名前空間は、ユーザー定義とシステム定義の 2 つのカテゴリに分類されます。  ユーザー定義の名前空間は、コードで定義された名前空間です。  システム定義の名前空間の一覧については、「[.NET Framework クラス ライブラリ](http://go.microsoft.com/fwlink/?LinkID=227195)」を参照してください。  
  
 他のアセンブリのメソッドを参照する方法の例については、「[C\# DLL の作成と使用](../Topic/How%20to:%20Create%20and%20Use%20Assemblies%20Using%20the%20Command%20Line%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
## 例 1  
  
### 説明  
 次の例は、名前空間の `using` エイリアスを定義して使用する方法を示しています。  
  
### コード  
 [!code-cs[csrefKeywordsNamespace#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_1.cs)]  
  
### コメント  
 using エイリアス ディレクティブの右側には、オープン ジェネリック型を配置できません。  たとえば、List\<T\> の using エイリアスを作成することはできませんが、List\<int\> の using エイリアスは作成できます。  
  
## 例 2  
  
### 説明  
 次の例は、クラスの `using` ディレクティブと `using` エイリアスを定義する方法を示しています。  
  
### コード  
 [!code-cs[csrefKeywordsNamespace#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-directive_2.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [名前空間の使用](../../../csharp/programming-guide/namespaces/using-namespaces.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [名前空間キーワード](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [名前空間](../../../csharp/programming-guide/namespaces/index.md)   
 [using ステートメント](../../../visual-basic/language-reference/statements/using-statement.md)