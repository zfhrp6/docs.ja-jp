---
title: "方法: ファイルまたはディレクトリ ツリー (LINQ) (Visual Basic) 内のファイル サイズの大きい照会 |Microsoft ドキュメント"
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
ms.assetid: 8c1c9f0c-95dd-4222-9be2-9ec026a13e81
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
ms.openlocfilehash: 055cbdd5a5903417ab382d390e1215f0319c0b5a
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq-visual-basic"></a>方法: ディレクトリ ツリー内で最もサイズの大きいファイルを照会する (LINQ) (Visual Basic)
この例では、ファイルのサイズ (バイト単位) に関連する&5; つのクエリを示します。  
  
-   最大ファイルのバイト単位のサイズを取得する方法。  
  
-   最も小さいファイルのバイト単位のサイズを取得する方法。  
  
-   取得する方法、 <xref:System.IO.FileInfo>、指定したルート フォルダーの下の&1; つまたは複数のフォルダーから、オブジェクトの最大値または最小ファイル</xref:System.IO.FileInfo>。  
  
-   10 個のファイルなどのシーケンスを取得する方法。  
  
-   指定したサイズよりも小さいファイルを無視して、ファイル サイズ (バイト単位) に基づくグループにファイルを注文する方法。  
  
## <a name="example"></a>例  
 次の例には、クエリを実行する方法と、ファイル サイズ (バイト単位) に応じて、グループのファイルを表示する&5; つの独立したクエリが含まれています。 これらの例をいくつかの他のプロパティの基にクエリを簡単に変更することができます、<xref:System.IO.FileInfo>オブジェクト</xref:System.IO.FileInfo>。  
  
```vb  
Module QueryBySize  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Return the size of the largest file  
        Dim maxSize = Aggregate aFile In fileList Into Max(GetFileLength(aFile))  
  
        'Dim maxSize = fileLengths.Max  
        Console.WriteLine("The length of the largest file under {0} is {1}", _  
                          root, maxSize)  
  
        ' Return the FileInfo object of the largest file  
        ' by sorting and selecting from the beginning of the list  
        Dim filesByLengDesc = From file In fileList _  
                              Let filelength = GetFileLength(file) _  
                              Where filelength > 0 _  
                              Order By filelength Descending _  
                              Select file  
  
        Dim longestFile = filesByLengDesc.First  
  
        Console.WriteLine("The largest file under {0} is {1} with a length of {2} bytes", _  
                          root, longestFile.FullName, longestFile.Length)  
  
        Dim smallestFile = filesByLengDesc.Last  
  
        Console.WriteLine("The smallest file under {0} is {1} with a length of {2} bytes", _  
                                root, smallestFile.FullName, smallestFile.Length)  
  
        ' Return the FileInfos for the 10 largest files  
        ' Based on a previous query, but nothing is executed  
        ' until the For Each statement below.  
        Dim tenLargest = From file In filesByLengDesc Take 10  
  
        Console.WriteLine("The 10 largest files under {0} are:", root)  
  
        For Each fi As System.IO.FileInfo In tenLargest  
            Console.WriteLine("{0}: {1} bytes", fi.FullName, fi.Length)  
        Next  
  
        ' Group files according to their size,  
        ' leaving out the ones under 200K  
        Dim sizeGroups = From file As System.IO.FileInfo In fileList _  
                         Where file.Length > 0 _  
                         Let groupLength = file.Length / 100000 _  
                         Group file By groupLength Into fileGroup = Group _  
                         Where groupLength >= 2 _  
                         Order By groupLength Descending  
  
        For Each group In sizeGroups  
            Console.WriteLine(group.groupLength + "00000")  
  
            For Each item As System.IO.FileInfo In group.fileGroup  
                Console.WriteLine("   {0}: {1}", item.Name, item.Length)  
            Next  
        Next  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    ' In this particular case, it is safe to ignore the exception.  
    Function GetFileLength(ByVal fi As System.IO.FileInfo) As Long  
        Dim retval As Long  
        Try  
            retval = fi.Length  
        Catch ex As FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 1 つまたは複数の完了を返す<xref:System.IO.FileInfo>オブジェクトの場合、クエリは最初に&1; つずつでデータを調べる必要がありますソースで実行され、Length プロパティの値で並べ替えます</xref:System.IO.FileInfo>。 1 つまたはシーケンスの最大の長さを返すことできます。 使用<xref:System.Linq.Enumerable.First%2A>をリスト内の最初の要素を返します</xref:System.Linq.Enumerable.First%2A>。 使用する<xref:System.Linq.Enumerable.Take%2A>要素の最初の n の数を返します</xref:System.Linq.Enumerable.Take%2A>。 リストの先頭にある最も小さい要素を配置する降順の並べ替え順序を指定します。  
  
 クエリの場合は、ファイルが以降の時間内に別のスレッドで削除された場所に表示されるだけは例外を使用するために、ファイル サイズ (バイト単位) を取得する個別のメソッドを呼び出す、<xref:System.IO.FileInfo>への呼び出しでオブジェクトが作成された`GetFiles`</xref:System.IO.FileInfo>。 <xref:System.IO.FileInfo>オブジェクトが既に作成されて、例外が発生する可能性があるため、<xref:System.IO.FileInfo>オブジェクトは、更新しようとしますその<xref:System.IO.FileInfo.Length%2A>初めてプロパティにアクセス (バイト単位) の最新のサイズを使用してプロパティ。</xref:System.IO.FileInfo.Length%2A> </xref:System.IO.FileInfo> </xref:System.IO.FileInfo> 。 クエリの外部の try-catch ブロックでこの操作を配置することで、副作用を引き起こす可能性のあるクエリでの操作を防ぐための規則に従っています。 一般に、十分な注意する必要があります、例外を使用するときにために実行するアプリケーションが不明な状態で残っていないことを確認します。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 .NET Framework version 3.5 またはそれ以上、System.Core.dll への参照を対象とするプロジェクトを作成し、 `Imports` System.Linq 名前空間のステートメントです。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)   
 [LINQ とファイル ディレクトリ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
