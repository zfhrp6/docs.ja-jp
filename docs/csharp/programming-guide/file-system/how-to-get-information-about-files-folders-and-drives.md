---
title: "方法 : ファイル、フォルダー、およびドライブに関する情報を取得する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ファイル [C#], 取得 (情報を)"
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
caps.latest.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 30
---
# 方法 : ファイル、フォルダー、およびドライブに関する情報を取得する (C# プログラミング ガイド)
.NET Framework では、次のクラスを使用してファイル システム情報にアクセスできます。  
  
-   <xref:System.IO.FileInfo?displayProperty=fullName>  
  
-   <xref:System.IO.DirectoryInfo?displayProperty=fullName>  
  
-   <xref:System.IO.DriveInfo?displayProperty=fullName>  
  
-   <xref:System.IO.Directory?displayProperty=fullName>  
  
-   <xref:System.IO.File?displayProperty=fullName>  
  
 <xref:System.IO.FileInfo> クラスおよび <xref:System.IO.DirectoryInfo> クラスはファイルまたはディレクトリを表し、NTFS ファイル システムでサポートされる多数のファイル属性を公開するプロパティを含みます。  ファイルやフォルダーを作成、クローズ、移動、および削除するためのメソッドも含まれます。  ファイル、フォルダー、またはドライブの名前を表す文字列をコンストラクターに渡すことで、これらのクラスのインスタンスを作成できます。  
  
```c#  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=fullName>、<xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=fullName>、および <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=fullName> への呼び出しを使用することで、ファイル、フォルダー、またはドライブの名前を取得することもできます。  
  
 <xref:System.IO.Directory?displayProperty=fullName> クラスと <xref:System.IO.File?displayProperty=fullName> クラスは、ディレクトリおよびファイルに関する情報を取得するための静的メソッドを提供します。  
  
## 使用例  
 ファイルおよびフォルダーに関する情報へのさまざまなアクセス方法を次の例に示します。  
  
 [!code-cs[csFilesandFolders#6](../../../csharp/programming-guide/file-system/codesnippet/csharp/csFilesFolders/FileIteration.cs#6)]  
  
## 信頼性の高いプログラミング  
 ユーザー指定のパス文字列を処理する場合、次の条件の例外も処理する必要があります。  
  
-   ファイル名が不適切である場合。  たとえば、無効な文字が含まれている場合や、空白のみの場合。  
  
-   ファイル名が null である場合。  
  
-   ファイル名の長さが、システム定義の最大長を超えている場合  
  
-   ファイル名にコロン \(:\) が含まれる場合  
  
 指定したファイルの読み取りに必要なアクセス許可がアプリケーションに与えられていない場合、`Exists` メソッドは目的のパスが存在するかどうかに関係なく `false` を返します。ただし、例外はスローされません。  
  
## 参照  
 <xref:System.IO?displayProperty=fullName>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ファイル システムとレジストリ](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)