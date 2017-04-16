---
title: "方法 : XPS ファイルをプログラムにより印刷する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "印刷 (XPS ファイルをプログラムで)"
  - "XPS ファイル, 印刷 (プログラムで)"
ms.assetid: 0b1c0a3f-b19e-43d6-bcc9-eb3ec4e555ad
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : XPS ファイルをプログラムにより印刷する
<xref:System.Printing.PrintQueue.AddJob%2A> メソッドの 1 つのオーバーロードを使用すると、<xref:System.Windows.Controls.PrintDialog> や、原則としてはその他の[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] を一切開くことなく、[!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] ファイルを印刷することができます。  
  
 また、<xref:System.Windows.Xps.XpsDocumentWriter> の多くの <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> メソッドや <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> メソッドを使用して、[!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] ファイルを印刷することもできます。  この詳細については、「[Printing an XPS Document](http://msdn.microsoft.com/ja-jp/849555c8-0c4e-48c0-86bc-a5494c69b36c)」を参照してください。  
  
 [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] の印刷は、<xref:System.Windows.Controls.PrintDialog> コントロールの <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> メソッドまたは <xref:System.Windows.Controls.PrintDialog.PrintVisual%2A> メソッドを使用しても実行できます。  「[印刷ダイアログ ボックスを呼び出す](../../../../docs/framework/wpf/advanced/how-to-invoke-a-print-dialog.md)」を参照してください。  
  
## 使用例  
 3 つのパラメーターをとる <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> メソッドを使用する主な手順は次のとおりです。  詳細は、下記の例に示します。  
  
1.  プリンターが XPSDrv プリンターであるかどうかを確認します   \(XPSDrv の詳細については、「[印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)」を参照してください\)。  
  
2.  プリンターが XPSDrv プリンターでない場合は、スレッドのアパートメントをシングル スレッドに設定します。  
  
3.  プリント サーバーと印刷キューのオブジェクトをインスタンス化します。  
  
4.  ジョブ名、印刷するファイル、およびプリンターが XPSDrv プリンターであるかどうかを示す <xref:System.Boolean> フラグを指定して、メソッドを呼び出します。  
  
 ディレクトリ内のすべての [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ファイルをバッチ印刷する方法を次の例に示します。  アプリケーションはユーザーにディレクトリの指定を求めますが、3 つのパラメーターをとる <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> メソッドは[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] を必要としません。  このメソッドは、そのメソッドに渡すことができる [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ファイル名とパスが記述された任意のコード パスで使用できます。  
  
 <xref:System.Printing.PrintQueue.AddJob%2A> の 3 つのパラメーターをとる <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> オーバーロードは、<xref:System.Boolean> パラメーターが `false` の場合 \(XPSDrv 以外のプリンターが使用されている場合\) は必ずシングル スレッドで実行する必要があります。  ただし、[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] の既定のアパートメントの状態は、マルチ スレッドです。  この例では XPSDrv 以外のプリンターを前提にしているため、この既定の状態を逆にする必要があります。  
  
 既定の状態を変更する方法は 2 つあります。  1 つは、単純に <xref:System.STAThreadAttribute> \(つまり "`[System.STAThreadAttribute()]`"\) をアプリケーションの `Main` メソッド \(通常は "`static void Main(string[] args)`"\) のすぐ上に追加する方法です。  ただし、多くのアプリケーションは、`Main` メソッドのアパートメントの状態がマルチ スレッドであることを必要とするため、もう 1 つの方法が用意されています。それは、<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> の呼び出しを、そのアパートメントの状態が <xref:System.Threading.Thread.SetApartmentState%2A> で <xref:System.Threading.ApartmentState> に設定されている個別のスレッドで行う方法です。  次に示す例では、この 2 番目の方法を使用します。  
  
 したがって、この例では、最初に <xref:System.Threading.Thread> オブジェクトをインスタンス化し、そのオブジェクトを **PrintXPS** メソッドに <xref:System.Threading.ThreadStart> パラメーターとして渡します   \(**PrintXPS** メソッドは例の後半で定義されます\)。次に、そのスレッドをシングル スレッド アパートメントに設定します。  それ以降の `Main` メソッドのコードでは、この新しいスレッドを開始します。  
  
 この例の要点は、`static` **BatchXPSPrinter.PrintXPS** メソッド内にあります。  プリント サーバーとキューを作成した後、このメソッドによって、[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ファイルを含むディレクトリの指定を求めるプロンプトが表示されます。  ディレクトリの有無と、そのディレクトリに \*.xps ファイルがあるかどうかを確認した後に、各ファイルが印刷キューに追加されます。  この例では、プリンターが XPSDrv 以外のプリンターであることが前提になっているため、<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> メソッドの最後のパラメーターに `false` を渡しています。  このため、このメソッドはファイル内の [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] マークアップを検証してから、そのマークアップをプリンターのページ記述言語に変換しようとします。  検証に失敗すると、例外がスローされます。  このコード例では、その例外をキャッチし、ユーザーに例外の発生を通知してから、次の [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ファイルの処理に進みます。  
  
 [!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
 [!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]  
  
 XPSDrv プリンターを使用している場合は、最後のパラメーターを `true` に設定できます。  その場合、[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] はプリンターのページ記述言語であるため、メソッドはファイルの検証や別のページ記述言語への変換を行わずにファイルをプリンターに送ります。  アプリケーションが XPSDrv プリンターを使用するかどうかがデザイン時に不明な場合は、<xref:System.Printing.PrintQueue.IsXpsDevice%2A> プロパティを読み込んで、その検出内容に従って分岐するようにアプリケーションを変更できます。  
  
 [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] および [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] のリリースの直後には XPSDrv プリンターの普及率が低いことが想定されるため、場合によっては、XPSDrv プリンターではないプリンターを XPSDrv プリンターに見せかける必要があります。  そのためには、アプリケーションを実行しているコンピューターで、以下のレジストリ キーのファイルの一覧に Pipelineconfig.xml を追加します。  
  
 HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\Print\\Environments\\Windows NT x86\\Drivers\\Version\-3\\*\<PseudoXPSPrinter\>*\\DependentFiles  
  
 *\<PseudoXPSPrinter\>* は任意の印刷キューです。  変更後に、コンピューターを再起動する必要があります。  
  
 このように見せかけることで、例外を発生させることなく、<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> の最後のパラメーターとして `true` を渡すことができますが、*\<PseudoXPSPrinter\>* は実際には XPSDrv プリンターではないため、正しく印刷されません。  
  
 **メモ** 上記の例では、単純化のため、\*.xps 拡張子の有無でファイルが [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] かどうかを確認していますが、  [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ファイルには、この拡張子を付ける必要はありません。  [isXPS.exe \(isXPS 適合性ツール\)](../Topic/isXPS.exe%20\(isXPS%20Conformance%20Tool\).md)は、ファイルが [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] かどうかをテストする 1 つの手段です。  
  
## 参照  
 <xref:System.Printing.PrintQueue>   
 <xref:System.Printing.PrintQueue.AddJob%2A>   
 <xref:System.Threading.ApartmentState>   
 <xref:System.STAThreadAttribute>   
 [XPS \(XPS\)](http://www.microsoft.com/japan/whdc/xps/default.mspx)   
 [Printing an XPS Document](http://msdn.microsoft.com/ja-jp/849555c8-0c4e-48c0-86bc-a5494c69b36c)   
 [Managed and Unmanaged Threading](http://msdn.microsoft.com/ja-jp/db425c20-4b2f-4433-bf96-76071c7881e5)   
 [isXPS.exe \(isXPS 適合性ツール\)](../Topic/isXPS.exe%20\(isXPS%20Conformance%20Tool\).md)   
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)