---
title: "方法: 拡張機能 (LINQ) (Visual Basic) でファイルをグループ化 |Microsoft ドキュメント"
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
ms.assetid: 904dc6d7-7162-4655-a7f4-5785d669bc5a
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f78785b4da3ae3b362603eea34d81207ed48a657
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-group-files-by-extension-linq-visual-basic"></a>方法: 拡張機能 (LINQ) (Visual Basic) でファイルをグループ化
この例では、LINQ を使用して、高度なグループ化と並べ替えファイルまたはフォルダーのリストに対する操作を実行する方法を示します。 使用して、コンソール ウィンドウに出力をページングする方法についても示しています、<xref:System.Linq.Enumerable.Skip%2A>と<xref:System.Linq.Enumerable.Take%2A>メソッド</xref:System.Linq.Enumerable.Take%2A></xref:System.Linq.Enumerable.Skip%2A>。  
  
## <a name="example"></a>例  
 次のクエリでは、指定したディレクトリ ツリーの内容をファイル名拡張子別にグループ化する方法を示します。  
  
```vb  
Module GroupByExtension  
    Public Sub Main()  
  
        ' Root folder to query, along with all subfolders.  
        Dim startFolder As String = "C:\program files\Microsoft Visual Studio 9.0\VB\"  
  
        ' Used in WriteLine() to skip over startfolder in output lines.  
        Dim rootLength As Integer = startFolder.Length  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(startFolder)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Create the query.  
        Dim queryGroupByExt = From file In fileList _  
                          Group By file.Extension.ToLower() Into fileGroup = Group _  
                          Order By ToLower _  
                          Select fileGroup  
  
        ' Execute the query. By storing the result we can  
        ' page the display with good performance.  
        Dim groupByExtList = queryGroupByExt.ToList()  
  
        ' Display one group at a time. If the number of   
        ' entries is greater than the number of lines  
        ' in the console window, then page the output.  
        Dim trimLength = startFolder.Length  
        PageOutput(groupByExtList, trimLength)  
  
    End Sub  
  
    ' Pages console diplay for large query results. No more than one group per page.  
    ' This sub specifically works with group queries of FileInfo objects  
    ' but can be modified for any type.  
    Sub PageOutput(ByVal groupQuery, ByVal charsToSkip)  
  
        ' "3" = 1 line for extension key + 1 for "Press any key" + 1 for input cursor.  
        Dim numLines As Integer = Console.WindowHeight - 3  
        ' Flag to indicate whether there are more results to diplay  
        Dim goAgain As Boolean = True  
  
        For Each fg As IEnumerable(Of System.IO.FileInfo) In groupQuery  
            ' Start a new extension at the top of a page.  
            Dim currentLine As Integer = 0  
  
            Do While (currentLine < fg.Count())  
                Console.Clear()  
                Console.WriteLine(fg(0).Extension)  
  
                ' Get the next page of results  
                ' No more than one filename per page  
                Dim resultPage = From file In fg _  
                                Skip currentLine Take numLines  
  
                ' Execute the query. Trim the display output.  
                For Each line In resultPage  
                    Console.WriteLine(vbTab & line.FullName.Substring(charsToSkip))  
                Next  
  
                ' Advance the current position  
                currentLine = numLines + currentLine  
  
                ' Give the user a chance to break out of the loop  
                Console.WriteLine("Press any key for next page or the 'End' key to exit.")  
                Dim key As ConsoleKey = Console.ReadKey().Key  
                If key = ConsoleKey.End Then  
                    goAgain = False  
                    Exit For  
                End If  
            Loop  
        Next  
    End Sub  
End Module  
```  
  
 このプログラムの出力がローカル ファイル システムの詳細によって時間がかかることができますあります、`startFolder`に設定されています。 すべての結果の表示を有効にするのには、この例は、結果をページに移動する方法を示します。 Windows および Web アプリケーションには、同じ手法を適用できます。 コードは、入れ子になったグループ内の項目をページため`For Each`ループが必要です。 一覧で、現在の位置を計算し、ユーザーはページングを停止し、プログラムを終了できるようにするロジックも追加もできます。 この場合、ページング クエリが、元のクエリからキャッシュされた結果に対して実行します。 LINQ to SQL など、他のコンテキストでこのようなキャッシュする必要はありません。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 .NET Framework version 3.5 またはそれ以上、System.Core.dll への参照を対象とするプロジェクトを作成し、 `Imports` System.Linq 名前空間のステートメントです。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)   
 [LINQ とファイル ディレクトリ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
