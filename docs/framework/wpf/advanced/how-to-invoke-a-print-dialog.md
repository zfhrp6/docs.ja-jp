---
title: '方法 : 印刷ダイアログ ボックスを呼び出す'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
ms.openlocfilehash: f94a965f724e85fb63ed9c98ebddba40938eb9b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-invoke-a-print-dialog"></a>方法 : 印刷ダイアログ ボックスを呼び出す
アプリケーションから印刷する機能を提供するだけで作成して開く、、<xref:System.Windows.Controls.PrintDialog>オブジェクト。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Controls.PrintDialog> コントロールには、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、構成、および [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ジョブの送信用の 1 つのエントリ ポイントが用意されています。 コントロールが使いやすいを使用して、インスタンス化できます[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]マークアップやコード。 次の例では、インスタンスを作成し、コードでコントロールを開く方法とそのプリンターから印刷する方法を示します。 ダイアログ ボックスは、ユーザーを特定のページ範囲を設定するオプションを確認する方法も示しています。 コード例では、FixedDocumentSequence.xps c: ドライブのルート内のファイルがあることを前提としています。  
  
 [!code-csharp[printdialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 ダイアログ ボックスが表示されたら、ユーザーは自分のコンピューターにインストールされているプリンターを選択することになります。 選択した場合のオプションもありますが、 [Microsoft XPS Document Writer](http://go.microsoft.com/fwlink/?LinkId=147319)を作成する、[!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)]印刷ではなくファイル。  
  
> [!NOTE]
>  <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>の制御[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、これは、このトピックの内容について説明する必要がありますと混同しないで、 <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> Windows フォームのコンポーネントです。  
  
 厳密には、使用することができます、<xref:System.Windows.Controls.PrintDialog.PrintDocument%2A>ダイアログを開くことがなくメソッドです。 その意味では、コンポーネントとして含まれる未知、印刷コントロールを使用できます。 パフォーマンス上の理由から、いずれかを使用する方がよいなりますが、<xref:System.Printing.PrintQueue.AddJob%2A>メソッドまたは多くのいずれかの<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>と<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>のメソッド、 <xref:System.Windows.Xps.XpsDocumentWriter>。 詳細については、これは、次を参照してください。 [XPS ファイルをプログラムによって印刷](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md)とします。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.PrintDialog>  
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Microsoft XPS Document Writer](http://go.microsoft.com/fwlink/?LinkId=147319)
