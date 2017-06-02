---
title: "方法 : 印刷ダイアログ ボックスを呼び出す | Microsoft Docs"
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
  - "呼び出し (印刷ダイアログ ボックスを)"
  - "印刷ダイアログ ボックス, 呼び出し"
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : 印刷ダイアログ ボックスを呼び出す
アプリケーションからの印刷機能は、<xref:System.Windows.Controls.PrintDialog> オブジェクトを作成して開くだけで提供できます。  
  
## 使用例  
 <xref:System.Windows.Controls.PrintDialog> コントロールは、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、構成、および [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ジョブ送信のための単一エントリ ポイントを提供します。  このコントロールは使いやすく、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] マークアップまたはコードを使用してインスタンス化できます。  コードでコントロールをインスタンス化して開き、そのコントロールから印刷する方法を次の例に示します。  また、ダイアログ ボックスを使用してユーザーがページの特定範囲を設定できるようにする方法も示します。  このコード例は、C: ドライブのルートに FixedDocumentSequence.xps というファイルがあることを前提としています。  
  
 [!code-csharp[printdialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 ダイアログ ボックスを開くと、ユーザーは各自のコンピューターにインストールされているプリンターの中からプリンターを選択することができます。  また、印刷する代わりに [Microsoft XPS ドキュメント ライター](http://go.microsoft.com/fwlink/?LinkId=147319)を選択して [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] ファイルを作成することもできます。  
  
> [!NOTE]
>  このトピックで説明する [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の <xref:System.Windows.Controls.PrintDialog?displayProperty=fullName> コントロールを [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)]の <xref:System.Windows.Forms.PrintDialog?displayProperty=fullName> コンポーネントと混同しないようにしてください。  
  
 厳密には、ダイアログを開かないで <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> メソッドを使用できます。  この意味で、このコントロールは非表示の印刷コンポーネントとして使用できます。  ただし、パフォーマンス上の理由から、<xref:System.Printing.PrintQueue.AddJob%2A> メソッドまたは <xref:System.Windows.Xps.XpsDocumentWriter> の複数の <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> メソッドおよび <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> メソッドのいずれかを使用することをお勧めします。  この詳細については、「[XPS ファイルをプログラムにより印刷する](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Controls.PrintDialog>   
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)   
 [Microsoft XPS Document Writer \(Microsoft XPS ドキュメント ライター\)](http://go.microsoft.com/fwlink/?LinkId=147319)