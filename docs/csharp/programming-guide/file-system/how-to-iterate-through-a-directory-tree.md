---
title: "方法 : ディレクトリ ツリーを反復処理する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ファイル反復処理 [C#]"
  - "反復処理 (フォルダーの) [C#]"
ms.assetid: c4be4a75-6b1b-46a7-9d38-bab353091ed7
caps.latest.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 10
---
# 方法 : ディレクトリ ツリーを反復処理する (C# プログラミング ガイド)
"ディレクトリ ツリーを反復処理する" とは、指定したルート フォルダー以下の入れ子になっている各サブディレクトリ内の各ファイルにアクセスすることです。  各ファイルを開く必要がない場合もあります。  単に、ファイルまたはサブディレクトリの名前を `string` として取得することもでき、その他の情報を <xref:System.IO.FileInfo?displayProperty=fullName> オブジェクトまたは <xref:System.IO.DirectoryInfo?displayProperty=fullName> オブジェクトの形式で取得することもできます。  
  
> [!NOTE]
>  Windows では、"ディレクトリ" および "フォルダー" という用語は同義です。  多くのドキュメントおよびユーザー インターフェイスのテキストでは、"フォルダー" という用語が使用されていますが、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] クラス ライブラリでは、"ディレクトリ" という用語が使用されています。  
  
 最も容易なケース、つまり、指定したルート以下のすべてのディレクトリのアクセス許可があることが確実にわかっている場合、`System.IO.SearchOption.AllDirectories` フラグを使用できます。  このフラグは、指定したパターンと一致する、すべての入れ子にされたサブディレクトリを返します。  このフラグを使用する方法を次の例に示します。  
  
```c#  
root.GetDirectories("*.*", System.IO.SearchOption.AllDirectories);  
```  
  
 この方法の弱点は、指定したルート以下のサブディレクトリの 1 つが <xref:System.IO.DirectoryNotFoundException> または <xref:System.UnauthorizedAccessException> を発生させた場合、メソッド全体が失敗し、ディレクトリが返されないという点です。  <xref:System.IO.DirectoryInfo.GetFiles%2A> メソッドを使用する場合も同様です。  特定のサブフォルダーに関するこれらの例外を処理する必要がある場合、次の例に示されているように、ディレクトリ ツリーを手動で移動する必要があります。  
  
 ディレクトリ ツリーを手動で移動する場合、最初にサブディレクトリを処理すること \(*先行順走査*\)、または最初にファイルを処理すること \(*後順走査*\) ができます。  先行順走査を実行する場合、現在のフォルダー以下のツリー全体を移動しながら、そのフォルダー自体に直接格納されているファイルを反復処理していきます。  このドキュメント内の後の例では、後順走査を実行していますが、先行順走査を実行するように簡単に変更できます。  
  
 もう 1 つのオプションは、再帰とスタック ベースの走査のうちのどちらを使用するかです。  このドキュメント内の後の例では、両方の方法を示しています。  
  
 ファイルおよびフォルダーに対してさまざまな操作を実行する必要がある場合、単一のデリゲートを使用して呼び出すことができる個別の関数内に操作をリファクタリングすることで、これらの例をモジュール化できます。  
  
> [!NOTE]
>  NTFS ファイル システムには、*接合ポイント*、*シンボリック リンク*、および*ハード リンク*の形式で*リパース ポイント*を含めることができます。  <xref:System.IO.DirectoryInfo.GetFiles%2A>、<xref:System.IO.DirectoryInfo.GetDirectories%2A> などの .NET Framework メソッドは、リパース ポイント以下のサブディレクトリを返しません。  この動作により、リパース ポイントが相互参照している場合に、無限ループに入るのが回避されます。  通常、ファイルを誤って変更または削除しないようにするためにリパース ポイントを処理する場合、十分な注意が必要です。  リパース ポイントを詳細に制御する必要がある場合、プラットフォーム呼び出しまたはネイティブ コードを使用して、適切な Win32 ファイル システム メソッドを直接呼び出します。  
  
## 使用例  
 再帰を使用してディレクトリ ツリーを移動する方法を次の例に示します。  この再帰の方法は洗練されていますが、ディレクトリ ツリーが大規模で入れ子の階層が深い場合、スタック オーバーフロー例外が発生する可能性があります。  
  
 処理される特定の例外、および各ファイルまたは各フォルダーに対して実行される特定の操作は、例としてのみ用意したものです。  特定の要件を満たすには、このコードを修正する必要があります。  詳細については、コード内のコメントを参照してください。  
  
 [!code-cs[csFilesandFolders#1](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-iterate-through-a-directory-tree_1.cs)]  
  
## 使用例  
 再帰を使用せずにディレクトリ ツリー内のファイルおよびフォルダーを反復処理する方法を、次の例に示します。  この方法では、後入れ先出し \(LIFO: Last In First Out\) スタックである <xref:System.Collections.Generic.Stack%601> コレクション型を使用します。  
  
 処理される特定の例外、および各ファイルまたは各フォルダーに対して実行される特定の操作は、例としてのみ用意したものです。  特定の要件を満たすには、このコードを修正する必要があります。  詳細については、コード内のコメントを参照してください。  
  
 [!code-cs[csFilesandFolders#2](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-iterate-through-a-directory-tree_2.cs)]  
  
 アプリケーションにフォルダーを開くアクセス許可があるかどうか確認するためにすべてのフォルダーをテストするのは、通常、たいへん時間がかかります。  そのため、コード例には、`try/catch` ブロック内の操作のその部分のみが含まれています。  `catch` ブロックを修正すると、フォルダーへのアクセスを拒否されたとき、アクセス許可を昇格して再びアクセスを試行できます。  原則として、アプリケーションが不明の状態にならずに処理できる例外のみをキャッチします。  
  
 ディレクトリ ツリーの内容をメモリまたはディスクに保存する必要がある場合、各ファイルの \(`string` 型の\) <xref:System.IO.FileSystemInfo.FullName%2A> プロパティのみ保存するのが最適な選択肢です。  その後、必要に応じて、この文字列を使用して新しい <xref:System.IO.FileInfo> オブジェクトまたは <xref:System.IO.DirectoryInfo> オブジェクトを作成すること、または追加処理が必要なファイルを開くことができます。  
  
## 信頼性の高いプログラミング  
 堅牢性の高いファイル反復処理コードを作成するには、ファイル システムの数多くの複雑な部分を考慮する必要があります。  詳細については、「[NTFS Technical Reference](http://go.microsoft.com/fwlink/?LinkId=79488)」を参照してください。  
  
## 参照  
 <xref:System.IO>   
 [LINQ and File Directories](../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)   
 [ファイル システムとレジストリ](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)