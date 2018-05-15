---
title: '方法 : ファイルにテキストを書き込む'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- writing text to files
- I/O [.NET Framework], writing text to files
- streams, writing text to files
- data streams, writing text to files
ms.assetid: 060cbe06-2adf-4337-9e7b-961a5c840208
caps.latest.revision: 29
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 926dfe1ea254fdb6460c835f58721f54609ddc90
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="8ca7b-102">方法 : ファイルにテキストを書き込む</span><span class="sxs-lookup"><span data-stu-id="8ca7b-102">How to: Write Text to a File</span></span>
<span data-ttu-id="8ca7b-103">このトピックでは、.NET Framework アプリケーションまたは [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリのファイルにテキストを書き込むためのさまざまな方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-103">This topic shows different ways you can write text to a file for .NET Framework applications or [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="8ca7b-104">テキストをファイルに書き込むには、一般に次のクラスおよびメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
-   <span data-ttu-id="8ca7b-105"><xref:System.IO.StreamWriter> - 同期的にファイルに書き込むメソッド (<xref:System.IO.StreamWriter.Write%2A> または <xref:System.IO.TextWriter.WriteLine%2A>) あるいは非同期的に書き込むメソッド (<xref:System.IO.StreamWriter.WriteAsync%2A> と <xref:System.IO.StreamWriter.WriteLineAsync%2A>) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-105"><xref:System.IO.StreamWriter> - it contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> or <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
-   <span data-ttu-id="8ca7b-106"><xref:System.IO.File> – .NET Framework アプリケーションで使用します。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-106"><xref:System.IO.File> – to be used with .NET Framework applications.</span></span> <span data-ttu-id="8ca7b-107">ファイルにテキストを書き込む静的メソッド ( <xref:System.IO.File.WriteAllLines%2A> と <xref:System.IO.File.WriteAllText%2A>)、あるいはファイルにテキストを追加する静的メソッド (<xref:System.IO.File.AppendAllLines%2A>、 <xref:System.IO.File.AppendAllText%2A> 、または <xref:System.IO.File.AppendText%2A>) があります。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-107">It provides static methods to write text to a file such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file (<xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> or <xref:System.IO.File.AppendText%2A>).</span></span>  
  
-   <span data-ttu-id="8ca7b-108">[FileIO](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.aspx) - [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリで使用します。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-108">[FileIO](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.aspx) - to be used with [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="8ca7b-109">ファイルにテキストを書き込む非同期メソッド ([WriteLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writelinesasync.aspx) または [WriteTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writetextasync.aspx))、あるいはファイルにテキストを追加する非同期メソッド ([AppendLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendlinesasync.aspx) または [AppendTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendtextasync.aspx)) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-109">It contains asynchronous methods to write text to a file ([WriteLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writelinesasync.aspx) or [WriteTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writetextasync.aspx)) or to append text to a file ([AppendLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendlinesasync.aspx) or [AppendTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendtextasync.aspx)).</span></span>  

- <span data-ttu-id="8ca7b-110"><xref:System.IO.Path> - ファイルまたはディレクトリのパス情報を格納する文字列で使用されます。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-110"><xref:System.IO.Path> - to be used on strings that contain file or directory path information.</span></span> <span data-ttu-id="8ca7b-111">これには、ファイルまたはディレクトリのパスを構築するための文字列の連結を許可する <xref:System.IO.Path.Combine%2A> メソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-111">It contains the <xref:System.IO.Path.Combine%2A> method, which allows concatenation of strings to build a file or directory path.</span></span>


 <span data-ttu-id="8ca7b-112">実行するタスクに焦点を合わせるために、サンプルは単純化されています。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-112">The samples have been kept simple in order to focus on the task being performed.</span></span> <span data-ttu-id="8ca7b-113">このため、サンプルでは最小限のエラー チェックと、(例外が存在する場合は) 最小限の例外処理だけを行います。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-113">For this reason, the samples perform minimal error checking and exception handling, if any.</span></span> <span data-ttu-id="8ca7b-114">通常、実際のアプリケーションではこれよりも信頼性の高いエラー チェックと例外処理を行います。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-114">A real-world application generally provides more robust error checking and exception handling.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ca7b-115">例</span><span class="sxs-lookup"><span data-stu-id="8ca7b-115">Example</span></span>  
 <span data-ttu-id="8ca7b-116">次の例に、 <xref:System.IO.StreamWriter> クラスを使用して、新しいファイルにテキストを一度に 1 行ずつ同期的に書き込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-116">The following example shows how to synchronously write text to a new file using the <xref:System.IO.StreamWriter> class, one line at a time.</span></span> <span data-ttu-id="8ca7b-117">新しいテキスト ファイルは、ユーザーの [マイ ドキュメント] フォルダーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-117">The new text file is saved to the user's My Documents folder.</span></span> <span data-ttu-id="8ca7b-118"><xref:System.IO.StreamWriter> ステートメントで `using` オブジェクトが宣言され、インスタンス化されるため、 <xref:System.IO.StreamWriter.Dispose%2A> メソッドが呼び出され、それによってストリームが自動的にフラッシュされて閉じられます。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-118">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked which automatically flushes and closes the stream.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeline)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeline)]  
  
## <a name="example"></a><span data-ttu-id="8ca7b-119">例</span><span class="sxs-lookup"><span data-stu-id="8ca7b-119">Example</span></span>  
 <span data-ttu-id="8ca7b-120">次の例に、 <xref:System.IO.StreamWriter> クラスを使用して、既存のファイルにテキストを追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-120">The following example shows how to append text to an existing file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="8ca7b-121">この例では、前の例と同じテキスト ファイルを使用しています。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-121">It uses the same text file from the previous example.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#appendtext)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#appendtext)]     
  
## <a name="example"></a><span data-ttu-id="8ca7b-122">例</span><span class="sxs-lookup"><span data-stu-id="8ca7b-122">Example</span></span>  
 <span data-ttu-id="8ca7b-123">次の例に、 <xref:System.IO.StreamWriter> クラスを使用して、新しいファイルにテキストを非同期的に書き込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-123">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="8ca7b-124"><xref:System.IO.StreamWriter.WriteAsync%2A> メソッドを呼び出すには、このメソッドの呼び出しを `async` メソッドに含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-124">In order to invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call needs to be within an `async` method.</span></span> <span data-ttu-id="8ca7b-125">新しいテキスト ファイルは、ユーザーの [マイ ドキュメント] フォルダーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-125">The new text file is saved to the user's My Documents folder.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeasync)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeasync)]  
  
## <a name="example"></a><span data-ttu-id="8ca7b-126">例</span><span class="sxs-lookup"><span data-stu-id="8ca7b-126">Example</span></span>  
 <span data-ttu-id="8ca7b-127">次の例に、 <xref:System.IO.File> クラスを使用して、新しいファイルにテキストを書き込み、この同じファイルに新しいテキスト行を追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-127">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="8ca7b-128"><xref:System.IO.File.WriteAllText%2A> および <xref:System.IO.File.AppendAllLines%2A> メソッドは、ファイルを自動的に開き、閉じます。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-128">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="8ca7b-129"><xref:System.IO.File.WriteAllText%2A> メソッドに指定したパスが既に存在する場合、ファイルは上書きされます。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-129">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file will be overwritten.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writefile)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writefile)]  
  
## <a name="example"></a><span data-ttu-id="8ca7b-130">例</span><span class="sxs-lookup"><span data-stu-id="8ca7b-130">Example</span></span>  
 <span data-ttu-id="8ca7b-131">次の例では、ユーザーの入力を [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリでテキスト ファイルに非同期的に書き込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-131">The following example shows how to asynchronously write user input to a text file in a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app.</span></span> <span data-ttu-id="8ca7b-132">セキュリティの考慮事項により、 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリからファイルを開くには、一般に [FileOpenPicker](http://msdn.microsoft.com/library/windows/apps/windows.storage.pickers.fileopenpicker.aspx) コントロールを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-132">Because of security considerations, opening a file from a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app typically requires the use of a [FileOpenPicker](http://msdn.microsoft.com/library/windows/apps/windows.storage.pickers.fileopenpicker.aspx) control.</span></span> <span data-ttu-id="8ca7b-133">この例では、テキスト ファイルを表示するため `FileOpenPicker` がフィルター処理されます。</span><span class="sxs-lookup"><span data-stu-id="8ca7b-133">In this example, the `FileOpenPicker` is filtered to show text files.</span></span>  
  
```xaml  
<Page  
    x:Class="OpenFileWindowsStore.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:OpenFileWindowsStore"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d">  
  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
        <Button Content="save text to a file" HorizontalAlignment="Left" Margin="103,417,0,0" VerticalAlignment="Top"   
                Width="329" Height="86" FontSize="35" Click="Button_Click"/>  
        <TextBox Name="UserInputTextBox"  FontSize="18" HorizontalAlignment="Left" Margin="106,146,0,0"   
                 TextWrapping="Wrap" Text="Write some text here, and select a file to write it to." VerticalAlignment="Top"   
                 Height="201" Width="558" AcceptsReturn="True"/>  
        <TextBlock Name="StatusTextBox" HorizontalAlignment="Left" Margin="106,570,0,147" TextWrapping="Wrap" Text="Status:"   
                   VerticalAlignment="Center" Height="51" Width="1074" FontSize="18" />  
    </Grid>  
</Page>  
```  
  
 [!code-csharp[OpenFileWindowsStore#Code](../../../samples/snippets/csharp/VS_Snippets_CLR/openfilewindowsstore/cs/mainpage.xaml.cs#code)]
 [!code-vb[OpenFileWindowsStore#Code](../../../samples/snippets/visualbasic/VS_Snippets_CLR/openfilewindowsstore/vb/mainpage.xaml.vb#code)]  
  
## <a name="see-also"></a><span data-ttu-id="8ca7b-134">参照</span><span class="sxs-lookup"><span data-stu-id="8ca7b-134">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.Path>  
 <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="8ca7b-135">方法: ディレクトリとファイルを列挙する</span><span class="sxs-lookup"><span data-stu-id="8ca7b-135">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="8ca7b-136">方法: 新しく作成されたデータ ファイルに対して読み書きする</span><span class="sxs-lookup"><span data-stu-id="8ca7b-136">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="8ca7b-137">方法: ログ ファイルを開いて情報を追加する</span><span class="sxs-lookup"><span data-stu-id="8ca7b-137">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="8ca7b-138">方法: ファイルからテキストを読み取る</span><span class="sxs-lookup"><span data-stu-id="8ca7b-138">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="8ca7b-139">ファイルおよびストリーム入出力</span><span class="sxs-lookup"><span data-stu-id="8ca7b-139">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
