---
title: "How to: Copy a Directory to Another Directory in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "I/O [Visual Basic], copying directories"
  - "I/O [Visual Basic], copying folders"
  - "folders [Visual Basic], copying"
  - "directories [Visual Basic], copying"
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Copy a Directory to Another Directory in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> メソッドを使用すると、ディレクトリを別のディレクトリにコピーできます。  このメソッドでは、ディレクトリ自体とその内容がコピーされます。  コピー先のディレクトリが存在しない場合は作成されます。  コピー先の場所に同じ名前のディレクトリが存在し、`overwrite` が `False` に設定されている場合は、2 つのディレクトリの内容がマージされます。  操作の中で、ディレクトリの新しい名前を指定できます。  
  
 ディレクトリ内のファイルをコピーするときに、特定のファイルが原因で例外がスローされることがあります。たとえば、`overwrite` が `False` に設定されていて、マージを実行しているときに、既に存在するファイルなどが原因です。  こうしてスローされた例外は、単一の例外に統合され、その `Data` プロパティにエントリが保持されています。それらのエントリでは、ファイルまたはディレクトリ パスがキーとなっており、それに対応する値には、該当する例外メッセージが格納されています。  
  
### ディレクトリを別のディレクトリにコピーするには  
  
-   `CopyDirectory` メソッドを使用し、コピー元とコピー先のディレクトリ名を指定します。  次の例では、`TestDirectory1` という名前のディレクトリを `TestDirectory2` にコピーします。その際、既存のファイルは上書きします。  
  
     [!code-vb[VbVbcnMyFileSystem#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-a-directory-to-another-directory_1.vb)]  
  
     このコードの例は、IntelliSense コード スニペットとしても利用できます。  コード スニペット ピッカーでは、コード例は **\[ファイル システム \- ドライブ、フォルダー、およびファイルの処理\]** にあります。  詳細については、「[コード スニペット](/visual-studio/ide/code-snippets)」を参照してください。  
  
## 信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   ディレクトリに指定された新しい名前にコロン \(:\) またはスラッシュ \(\\ または \/\) が含まれている \(<xref:System.ArgumentException>\)。  
  
-   パスが無効な場合。次のいずれかの理由が考えられる。1\) 長さが 0 の文字列である、2\) 空白だけが含まれている、3\) 無効な文字が含まれている、4\) デバイス パスである \(先頭が \\\\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   パスが `Nothing` であるため、有効でない \(<xref:System.ArgumentNullException>\)。  
  
-   `destinationDirectoryName` が `Nothing` または空の文字列である \(<xref:System.ArgumentNullException>\)。  
  
-   コピー元のディレクトリが存在しない \(<xref:System.IO.DirectoryNotFoundException>\)。  
  
-   コピー元のディレクトリがルート ディレクトリである \(<xref:System.IO.IOException>\)。  
  
-   パスを組み合わせると既存のファイルと同じになる \(<xref:System.IO.IOException>\)。  
  
-   コピー元とコピー先のパスが同じである \(<xref:System.IO.IOException>\)。  
  
-   `ShowUI` が `UIOption.AllDialogs` に設定されており、ユーザーが操作をキャンセルしたか、またはディレクトリ内のいくつかのファイルをコピーできなかった \(<xref:System.OperationCanceledException>\)。  
  
-   操作が巡回している \(<xref:System.InvalidOperationException>\)。  
  
-   パスにコロン \(:\) が含まれている \(<xref:System.NotSupportedException>\)。  
  
-   パスがシステムで定義されている最大長を超えている \(<xref:System.IO.PathTooLongException>\)。  
  
-   パス内のファイル名またはフォルダー名にコロン \(:\) が含まれているか、または形式が無効である \(<xref:System.NotSupportedException>\)  
  
-   ユーザーがパスを参照するのに必要なアクセス許可がない \(<xref:System.Security.SecurityException>\)  
  
-   コピー先のファイルが存在するが、アクセスできない \(<xref:System.UnauthorizedAccessException>\)。  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>   
 [How to: Find Subdirectories with a Specific Pattern](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)   
 [How to: Get the Collection of Files in a Directory](../Topic/How%20to:%20Get%20the%20Collection%20of%20Files%20in%20a%20Directory%20in%20Visual%20Basic.md)