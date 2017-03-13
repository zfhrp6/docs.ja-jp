---
title: "方法: ファイルまたはフォルダーを作成する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "作成 (ファイルを) [C#]"
  - "作成 (フォルダーを) [C#]"
  - "ファイル [C#]"
  - "フォルダー [C#]"
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# 方法: ファイルまたはフォルダーを作成する (C# プログラミング ガイド)
プログラムによって、コンピューター上でのフォルダーの作成、サブフォルダーの作成、サブフォルダー内でのファイルの作成、およびファイルへのデータの記述を行うことができます。  
  
## 使用例  
 [!code-cs[csFilesandFolders#10](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-create-a-file-or-folder_1.cs)]  
  
 フォルダーが既に存在していた場合、<xref:System.IO.Directory.CreateDirectory%2A> は何も実行せず、例外はスローされません。  ただし <xref:System.IO.File.Create%2A?displayProperty=fullName> は、既存のファイルを新しいファイルに置き換えます。  この例では、既存のファイルの置換を抑制するために、`if`\-`else` ステートメントを使用します。  
  
 この例に次の変更を加えることによって、特定の名前のファイルが既に存在するかどうかに基づいて異なる結果を指定できます。  そのようなファイルが存在しない場合、コードによって作成されます。  このようなファイルがある場合、コードはそのファイルにデータを追加します。  
  
-   ランダムではないファイル名を指定します。  
  
    ```c#  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
  
    ```  
  
-   次のコードで、`if`\-`else` ステートメントを探し、そのステートメントを `using` に置き換えます。  
  
    ```c#  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))   
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
  
    ```  
  
 データがファイルに追加されたことを毎回確認するために、この例を数回実行します。  
  
 試用できるその他の `FileMode` 値については、<xref:System.IO.FileMode> を参照してください。  
  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   フォルダー名が不適切である場合。  たとえば、不正な文字が含まれている場合や、空白だけの場合などがその例です \(<xref:System.ArgumentException> クラス\)。  有効なパス名を作成するには、<xref:System.IO.Path> クラスを使用します。  
  
-   作成するフォルダーの親フォルダーが読み取り専用である場合 \(<xref:System.IO.IOException> クラス\)。  
  
-   フォルダー名が `null` である場合 \(<xref:System.ArgumentNullException> クラス\)。  
  
-   フォルダー名が長すぎる場合 \(<xref:System.IO.PathTooLongException> クラス\)。  
  
-   フォルダー名がコロン \(":"\) だけである場合 \(<xref:System.IO.PathTooLongException> クラス\)。  
  
## .NET Framework セキュリティ  
 部分的に信頼された状況では、<xref:System.Security.SecurityException> クラスのインスタンスがスローされることがあります。  
  
 フォルダーの作成に必要なアクセス許可が与えられていない場合、この例では <xref:System.UnauthorizedAccessException> クラスのインスタンスがスローされます。  
  
## 参照  
 <xref:System.IO?displayProperty=fullName>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ファイル システムとレジストリ](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)