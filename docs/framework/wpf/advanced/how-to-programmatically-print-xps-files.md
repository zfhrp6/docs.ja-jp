---
title: "方法 : XPS ファイルをプログラムにより印刷する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing XPS files programmatically [WPF]
- XPS files [WPF], printing programmatically
ms.assetid: 0b1c0a3f-b19e-43d6-bcc9-eb3ec4e555ad
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 949d92e8599ee083593cbd7f970a9b37d31970ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-programmatically-print-xps-files"></a>方法 : XPS ファイルをプログラムにより印刷する
1 つのオーバー ロードを使用することができます、<xref:System.Printing.PrintQueue.AddJob%2A>を印刷するメソッド[!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)]ファイルを開かず、<xref:System.Windows.Controls.PrintDialog>または原則として、任意[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]まったくです。  
  
 印刷することも[!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)]多くを使用してファイル<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>と<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>のメソッド、<xref:System.Windows.Xps.XpsDocumentWriter>です。 この詳細については、「[XPS ドキュメントの印刷](http://msdn.microsoft.com/en-us/849555c8-0c4e-48c0-86bc-a5494c69b36c)」を参照してください。  
  
 別の印刷方法[!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)]を使用して、<xref:System.Windows.Controls.PrintDialog.PrintDocument%2A>または<xref:System.Windows.Controls.PrintDialog.PrintVisual%2A>のメソッド、<xref:System.Windows.Controls.PrintDialog>コントロール。 [印刷ダイアログ ボックスの呼び出し](../../../../docs/framework/wpf/advanced/how-to-invoke-a-print-dialog.md)に関するページをご覧ください。  
  
## <a name="example"></a>例  
 3 つのパラメーターを使用する主要な手順<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>メソッドは、次のとおりです。 詳細は、下記の例に示します。  
  
1.  プリンターが XPSDrv プリンターかどうかを確認します  (XPSDrv の詳細については、「[印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)」を参照してください)。  
  
2.  プリンターが XPSDrv プリンターでない場合は、スレッドのアパートメントをシングル スレッドに設定します。  
  
3.  プリント サーバーと印刷キューのオブジェクトをインスタンス化します。  
  
4.  ジョブ名、印刷するファイルを指定して、メソッドを呼び出すと、<xref:System.Boolean>プリンターが XPSDrv プリンターかどうかどうかを示すフラグします。  
  
 ディレクトリ内のすべての [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ファイルをバッチ印刷する方法を次の例に示します。 アプリケーションには、ディレクトリ、3 つのパラメーターを指定するように求めるが<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>メソッドは必要ありません、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]です。 このメソッドは、そのメソッドに渡すことができる [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ファイル名とパスが記述された任意のコード パスで使用できます。  
  
 3 パラメーター<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>のオーバー ロード<xref:System.Printing.PrintQueue.AddJob%2A>シングル スレッド アパートメントで実行する必要があるたびに、<xref:System.Boolean>パラメーターは`false`、XPSDrv 以外のプリンターを使用する場合があります。 ただし、[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] の既定のアパートメントの状態は、マルチ スレッドです。 この例では XPSDrv 以外のプリンターを前提にしているため、この既定の状態を逆にする必要があります。  
  
 既定の状態を変更する方法は 2 つあります。 1 つの方法は、単に追加する、 <xref:System.STAThreadAttribute> (つまり、"`[System.STAThreadAttribute()]`") のアプリケーションの最初の行のすぐ上`Main`メソッド (通常"`static void Main(string[] args)`") です。 ただし、多くのアプリケーションが必要です、`Main`メソッドには、マルチ スレッド アパートメント状態があるため、2 番目のメソッドがあります: を呼び出して<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>アパートメント状態が に設定されている別のスレッドで<xref:System.Threading.ApartmentState.STA>で<xref:System.Threading.Thread.SetApartmentState%2A>です。 次の例では、この 2 番目の方法を使用します。  
  
 同様に、した後、インスタンス化する、<xref:System.Threading.Thread>オブジェクトを渡すこと、 **PrintXPS**メソッドとして、<xref:System.Threading.ThreadStart>パラメーター。 (**PrintXPS** メソッドは、例の後半で定義されます)。次に、そのスレッドをシングル スレッド アパートメントに設定します。 それ以降の `Main` メソッドのコードは、この新しいスレッドを開始します。  
  
 この例の要点は、`static`**staticBatchXPSPrinter.PrintXPS** メソッド内にあります。 プリント サーバーとキューを作成すると、[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ファイルを含むディレクトリを指定するように求められます。 ディレクトリの有無と、そのディレクトリに *.xps ファイルがあるかどうかを確認した後、各ファイルが印刷キューに追加されます。 この例では、プリンターがで渡しているように XPSDrv 以外の場合、ある`false`の最後のパラメーターを<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>メソッドです。 このため、このメソッドはファイル内の [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] マークアップを検証してから、そのマークアップをプリンターのページ記述言語に変換しようとします。 検証に失敗すると、例外がスローされます。 このコード例では、その例外をキャッチし、ユーザーに例外の発生を通知してから、次の [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ファイルの処理に進みます。  
  
 [!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
 [!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]  
  
 XPSDrv プリンターを使用している場合は、最後のパラメーターを `true` に設定できます。 その場合、[!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] はプリンターのページ記述言語であるため、メソッドはファイルの検証や別のページ記述言語への変換を行わずにファイルをプリンターに送ります。 不明なデザイン時にするかどうか、アプリケーションで使用される XPSDrv プリンター場合、は、アプリケーションの読み取りを変更することができます、<xref:System.Printing.PrintQueue.IsXpsDevice%2A>プロパティと検出した内容に従って分岐します。  
  
 [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] および [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] のリリースの直後には XPSDrv プリンターの普及率が低いことが想定されるため、場合によっては、XPSDrv プリンターではないプリンターを XPSDrv プリンターに見せかける必要があります。 そのためには、アプリケーションを実行しているコンピューターで、以下のレジストリ キーのファイルの一覧に Pipelineconfig.xml を追加します。  
  
 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\\*\<PseudoXPSPrinter>*\DependentFiles  
  
 ここで、*\<PseudoXPSPrinter* は任意の印刷キューです。 その後、コンピューターを再起動する必要があります。  
  
 この使用してを使用すると、渡す`true`の最後のパラメーターとして<xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>させずに、例外が *\<PseudoXPSPrinter >* XPSDrv プリンターではありませんガベージのみが印刷されます。  
  
 **メモ** 上記の例では、説明を簡単にするために、*.xps 拡張子の有無でファイルが [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] かどうかを確認していますが、 [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] ファイルには、この拡張子を付ける必要はありません。 [isXPS.exe (isXPS 適合性ツール)](http://msdn.microsoft.com/library/bfbb433f-7ab6-417a-90f0-71443d76bcb3) は、ファイルが [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] かどうかをテストする 1 つの手段です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.AddJob%2A>  
 <xref:System.Threading.ApartmentState>  
 <xref:System.STAThreadAttribute>  
 [XPS](http://www.microsoft.com/xps)  
 [XPS ドキュメントの印刷](http://msdn.microsoft.com/en-us/849555c8-0c4e-48c0-86bc-a5494c69b36c)  
 [マネージ コードとアンマネージ スレッド処理](http://msdn.microsoft.com/en-us/db425c20-4b2f-4433-bf96-76071c7881e5)  
 [isXPS.exe (isXPS 適合性ツール)](http://msdn.microsoft.com/library/bfbb433f-7ab6-417a-90f0-71443d76bcb3)  
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)
