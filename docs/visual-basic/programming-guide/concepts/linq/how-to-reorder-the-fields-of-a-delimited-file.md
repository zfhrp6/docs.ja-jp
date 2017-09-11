---
title: "方法: 区切り記号入りファイル (LINQ) (Visual Basic) のフィールドの順序を |Microsoft ドキュメント"
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
ms.assetid: c451c7db-663b-4daf-b8ba-a2093095d672
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8540dff06e146a1846063e11e3382e9457f9e412
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-reorder-the-fields-of-a-delimited-file-linq-visual-basic"></a><span data-ttu-id="bd01f-102">方法: 区切り記号入りファイル (LINQ) (Visual Basic) のフィールドの順序を変更</span><span class="sxs-lookup"><span data-stu-id="bd01f-102">How to: Reorder the Fields of a Delimited File (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="bd01f-103">コンマ区切り値 (CSV) ファイルは、スプレッドシートのデータまたはその他の行と列によって表される表形式のデータの格納に使用される多くの場合、テキスト ファイルです。</span><span class="sxs-lookup"><span data-stu-id="bd01f-103">A comma-separated value (CSV) file is a text file that is often used to store spreadsheet data or other tabular data that is represented by rows and columns.</span></span> <span data-ttu-id="bd01f-104">使用して、 <xref:System.String.Split%2A>、フィールドを分割するメソッドはクエリおよび LINQ を使用して CSV ファイルを操作する方が簡単です</xref:System.String.Split%2A>。</span><span class="sxs-lookup"><span data-stu-id="bd01f-104">By using the <xref:System.String.Split%2A> method to separate the fields, it is very easy to query and manipulate CSV files by using LINQ.</span></span> <span data-ttu-id="bd01f-105">実際に、任意の構造化された行のテキスト部分の順序を変更する同じ手法を使用できます。CSV ファイルに制限はありません。</span><span class="sxs-lookup"><span data-stu-id="bd01f-105">In fact, the same technique can be used to reorder the parts of any structured line of text; it is not limited to CSV files.</span></span>  
  
 <span data-ttu-id="bd01f-106">次の例では、3 つの列を表す受講者「姓」という前提としています「姓」と"ID"</span><span class="sxs-lookup"><span data-stu-id="bd01f-106">In the following example, assume that the three columns represent students' "last name," "first name", and "ID."</span></span> <span data-ttu-id="bd01f-107">フィールドは、学生の姓に基づいてアルファベット順になっています。</span><span class="sxs-lookup"><span data-stu-id="bd01f-107">The fields are in alphabetical order based on the students' last names.</span></span> <span data-ttu-id="bd01f-108">クエリでは、ID 列が表示される&1; つは、生徒の名前と姓を結合する&2; 番目の列の後に新しいシーケンスを生成します。</span><span class="sxs-lookup"><span data-stu-id="bd01f-108">The query produces a new sequence in which the ID column appears first, followed by a second column that combines the student's first name and last name.</span></span> <span data-ttu-id="bd01f-109">行の順序は、ID フィールドに基づいて変更されます。</span><span class="sxs-lookup"><span data-stu-id="bd01f-109">The lines are reordered according to the ID field.</span></span> <span data-ttu-id="bd01f-110">結果は、新しいファイルに保存し、元のデータは変更されません。</span><span class="sxs-lookup"><span data-stu-id="bd01f-110">The results are saved into a new file and the original data is not modified.</span></span>  
  
### <a name="to-create-the-data-file"></a><span data-ttu-id="bd01f-111">データ ファイルを作成するには</span><span class="sxs-lookup"><span data-stu-id="bd01f-111">To create the data file</span></span>  
  
1.  <span data-ttu-id="bd01f-112">Spreadsheet1.csv というプレーン テキスト ファイルに次の行をコピーします。</span><span class="sxs-lookup"><span data-stu-id="bd01f-112">Copy the following lines into a plain text file that is named spreadsheet1.csv.</span></span> <span data-ttu-id="bd01f-113">プロジェクト フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="bd01f-113">Save the file in your project folder.</span></span>  
  
    ```  
    Adams,Terry,120  
    Fakhouri,Fadi,116  
    Feng,Hanying,117  
    Garcia,Cesar,114  
    Garcia,Debra,115  
    Garcia,Hugo,118  
    Mortensen,Sven,113  
    O'Donnell,Claire,112  
    Omelchenko,Svetlana,111  
    Tucker,Lance,119  
    Tucker,Michael,122  
    Zabokritski,Eugene,121  
    ```  
  
## <a name="example"></a><span data-ttu-id="bd01f-114">例</span><span class="sxs-lookup"><span data-stu-id="bd01f-114">Example</span></span>  
  
```vb  
Class CSVFiles  
  
    Shared Sub Main()  
  
        ' Create the IEnumerable data source.  
        Dim lines As String() = System.IO.File.ReadAllLines("../../../spreadsheet1.csv")  
  
        ' Execute the query. Put field 2 first, then  
        ' reverse and combine fields 0 and 1 from the old field  
        Dim lineQuery = From line In lines   
                        Let x = line.Split(New Char() {","})   
                        Order By x(2)   
                        Select x(2) & ", " & (x(1) & " " & x(0))  
  
        ' Execute the query and write out the new file. Note that WriteAllLines  
        ' takes a string array, so ToArray is called on the query.  
        System.IO.File.WriteAllLines("../../../spreadsheet2.csv", lineQuery.ToArray())  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Spreadsheet2.csv written to disk. Press any key to exit")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output to spreadsheet2.csv:  
' 111, Svetlana Omelchenko  
' 112, Claire O'Donnell  
' 113, Sven Mortensen  
' 114, Cesar Garcia  
' 115, Debra Garcia  
' 116, Fadi Fakhouri  
' 117, Hanying Feng  
' 118, Hugo Garcia  
' 119, Lance Tucker  
' 120, Terry Adams  
' 121, Eugene Zabokritski  
' 122, Michael Tucker  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bd01f-115">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="bd01f-115">Compiling the Code</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd01f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="bd01f-116">See Also</span></span>  
 <span data-ttu-id="bd01f-117">[LINQ と文字列 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md) </span><span class="sxs-lookup"><span data-stu-id="bd01f-117">[LINQ and Strings (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md) </span></span>  
<span data-ttu-id="bd01f-118"> [LINQ とファイル ディレクトリ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md) </span><span class="sxs-lookup"><span data-stu-id="bd01f-118"> [LINQ and File Directories (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md) </span></span>  
<span data-ttu-id="bd01f-119"> [方法: CSV ファイルから XML を生成する](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd)</span><span class="sxs-lookup"><span data-stu-id="bd01f-119"> [How to: Generate XML from CSV Files](http://msdn.microsoft.com/library/dd7bab8c-96fa-4343-94d0-9739dd6a74fd)</span></span>
