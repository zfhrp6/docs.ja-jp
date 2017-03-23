---
title: "方法: 一連のフォルダー (LINQ) (Visual Basic) のバイト数の合計数を問い合わせる |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 668a8a4d89f7b81c3aef9b4e1a46ad749c4a8341
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a>方法: 一連のフォルダー (LINQ) (Visual Basic) のバイト数の合計数を問い合わせる
この例では、指定したフォルダー内のすべてのファイルとそのすべてのサブフォルダーで使用されるバイトの総数を取得する方法を示します。  
  
## <a name="example"></a>例  
 <xref:System.Linq.Enumerable.Sum%2A>メソッドを追加で選択されているすべてのアイテムの値、`select`句</xref:System.Linq.Enumerable.Sum%2A>。 <xref:System.Linq.Enumerable.Min%2A>または<xref:System.Linq.Enumerable.Max%2A><xref:System.Linq.Enumerable.Sum%2A>。</xref:System.Linq.Enumerable.Sum%2A>の代わりにメソッド</xref:System.Linq.Enumerable.Max%2A></xref:System.Linq.Enumerable.Min%2A>を呼び出すことによって指定されたディレクトリ ツリー内の最大または最小のファイルを取得するには、このクエリを簡単に変更することができます。  
  
```vb  
Module QueryTotalBytes  
    Sub Main()  
  
        ' Change the drive\path if necessary.  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0\VB"  
  
        'Take a snapshot of the folder contents.  
        ' This method assumes that the application has discovery permissions  
        ' for all folders under the specified path.  
        Dim fileList = My.Computer.FileSystem.GetFiles _  
                  (root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")  
  
        Dim fileQuery = From file In fileList _  
                        Select GetFileLength(file)  
  
        ' Force execution and cache the results to avoid multiple trips to the file system.  
        Dim fileLengths = fileQuery.ToArray()  
  
        ' Find the largest file  
        Dim maxSize = Aggregate aFile In fileLengths Into Max()  
  
        ' Find the total number of bytes  
        Dim totalBytes = Aggregate aFile In fileLengths Into Sum()  
  
        Console.WriteLine("The largest file is " & maxSize & " bytes")  
        Console.WriteLine("There are " & totalBytes & " total bytes in " & _  
                          fileList.Count & " files under " & root)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    Function GetFileLength(ByVal filename As String) As Long  
        Dim retval As Long  
        Try  
            Dim fi As New System.IO.FileInfo(filename)  
            retval = fi.Length  
        Catch ex As System.IO.FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 指定したディレクトリ ツリー内のバイト数をカウントするした場合これより効率的にデータ ソースとしてリスト コレクションを作成するオーバーヘッドが発生し、LINQ クエリを作成しなくても実行できます。 LINQ アプローチの有用性は、クエリがより複雑なまたは同じデータ ソースに対して複数のクエリを実行するときに増加します。  
  
 クエリは、ファイル長を取得する別のメソッドを呼び出します。 これは、ファイルが別のスレッドの後で削除された場合に発生する例外を使用するために、<xref:System.IO.FileInfo>への呼び出しでオブジェクトが作成された`GetFiles`</xref:System.IO.FileInfo>。 にもかかわらず、<xref:System.IO.FileInfo>オブジェクトが既に作成されて、例外が発生する可能性があるため、<xref:System.IO.FileInfo>オブジェクトは、更新しようとしますその<xref:System.IO.FileInfo.Length%2A>プロパティへのアクセスは、最初に、最新の長さを持つプロパティです。</xref:System.IO.FileInfo.Length%2A> </xref:System.IO.FileInfo> </xref:System.IO.FileInfo> 。 クエリの外部の try-catch ブロックでこの操作を配置することでコードは、副作用を引き起こす可能性のあるクエリでの操作を防ぐためのルールに従います。 一般に、アプリケーションが不明な状態で残っていないことを確認する例外を処理する時は、十分な注意を考慮しなければなりません。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 .NET Framework version 3.5 またはそれ以上、System.Core.dll への参照を対象とするプロジェクトを作成し、 `Imports` System.Linq 名前空間のステートメントです。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)   
 [LINQ とファイル ディレクトリ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
