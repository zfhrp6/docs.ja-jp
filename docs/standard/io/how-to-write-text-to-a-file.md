---
title: "方法 : ファイルにテキストを書き込む | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "書き込み (テキストをファイルに)"
  - "I/O [.NET Framework]、書き込み (テキストをファイルに)"
  - "ストリーム、書き込み (テキストをファイルに)"
  - "データ ストリーム、書き込み (テキストをファイルに)"
ms.assetid: 060cbe06-2adf-4337-9e7b-961a5c840208
caps.latest.revision: 29
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 29
---
# 方法 : ファイルにテキストを書き込む
このトピックでは、.NET Framework アプリケーションまたは [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリのファイルにテキストを書き込むためのさまざまな方法について説明します。 テキストをファイルに書き込むには、一般に次のクラスおよびメソッドを使用します。  
  
-   <xref:System.IO.StreamWriter> \- 同期的にファイルに書き込むメソッド \(<xref:System.IO.StreamWriter.Write%2A> または <xref:System.IO.TextWriter.WriteLine%2A>\) あるいは非同期的に書き込むメソッド \(<xref:System.IO.StreamWriter.WriteAsync%2A> と <xref:System.IO.StreamWriter.WriteLineAsync%2A>\) が含まれています。  
  
-   <xref:System.IO.File> – .NET Framework アプリケーションで使用します。 ファイルにテキストを書き込む静的メソッド \(<xref:System.IO.File.WriteAllLines%2A> と <xref:System.IO.File.WriteAllText%2A>\)、あるいはファイルにテキストを追加する静的メソッド \(<xref:System.IO.File.AppendAllLines%2A>、<xref:System.IO.File.AppendAllText%2A>、または <xref:System.IO.File.AppendText%2A>\) があります。  
  
-   [FileIO](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.aspx) \- [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリで使用します。 ファイルにテキストを書き込む非同期メソッド \([WriteLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writelinesasync.aspx) または [WriteTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writetextasync.aspx)\)、あるいはファイルにテキストを追加する非同期メソッド \([AppendLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendlinesasync.aspx) または [AppendTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendtextasync.aspx)\) が含まれています。  
  
 実行するタスクに焦点を合わせるために、サンプルは単純化されています。 このため、サンプルでは最小限のエラー チェックと、\(例外が存在する場合は\) 最小限の例外処理だけを行います。 通常、実際のアプリケーションではこれよりも信頼性の高いエラー チェックと例外処理を行います。  
  
## 使用例  
 次の例に、<xref:System.IO.StreamWriter> クラスを使用して、新しいファイルにテキストを一度に 1 行ずつ同期的に書き込む方法を示します。 新しいテキスト ファイルは、ユーザーの \[マイ ドキュメント\] フォルダーに保存されます。`using` ステートメントで <xref:System.IO.StreamWriter> オブジェクトが宣言され、インスタンス化されるため、<xref:System.IO.StreamWriter.Dispose%2A> メソッドが呼び出され、それによってストリームが自動的にフラッシュされて閉じられます。  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeline)]
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeline)]  
  
## 使用例  
 次の例に、<xref:System.IO.StreamWriter> クラスを使用して、既存のファイルにテキストを追加する方法を示します。 この例では、前の例と同じテキスト ファイルを使用しています。  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#appendtext)]
 [!code-vb[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#appendtext)]  
  
## 使用例  
 次の例に、<xref:System.IO.StreamWriter> クラスを使用して、新しいファイルにテキストを非同期的に書き込む方法を示します。<xref:System.IO.StreamWriter.WriteAsync%2A> メソッドを呼び出すには、このメソッドの呼び出しを `async` メソッドに含める必要があります。 新しいテキスト ファイルは、ユーザーの \[マイ ドキュメント\] フォルダーに保存されます。  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeasync)]
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeasync)]  
  
## 使用例  
 次の例に、<xref:System.IO.File> クラスを使用して、新しいファイルにテキストを書き込み、この同じファイルに新しいテキスト行を追加する方法を示します。<xref:System.IO.File.WriteAllText%2A> および <xref:System.IO.File.AppendAllLines%2A> メソッドは、ファイルを自動的に開き、閉じます。<xref:System.IO.File.WriteAllText%2A> メソッドに指定したパスが既に存在する場合、ファイルは上書きされます。  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writefile)]
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writefile)]  
  
## 使用例  
 次の例では、ユーザーの入力を [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリでテキスト ファイルに非同期的に書き込む方法を示します。 セキュリティの考慮事項により、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリからファイルを開くには、一般に [FileOpenPicker](http://msdn.microsoft.com/library/windows/apps/windows.storage.pickers.fileopenpicker.aspx) コントロールを使用する必要があります。 この例では、テキスト ファイルを表示するため `FileOpenPicker` がフィルター処理されます。  
  
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
  
## 参照  
 <xref:System.IO.StreamWriter>   
 <xref:System.IO.File.CreateText%2A?displayProperty=fullName>   
 [方法: ディレクトリとファイルを列挙する](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)   
 [方法 : 新しく作成されたデータ ファイルに対して読み書きする](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)   
 [方法 : ログ ファイルを開いて情報を追加する](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)   
 [方法 : ファイルからテキストを読み取る](../../../docs/standard/io/how-to-read-text-from-a-file.md)   
 [ファイルおよびストリーム入出力](../../../docs/standard/io/index.md)