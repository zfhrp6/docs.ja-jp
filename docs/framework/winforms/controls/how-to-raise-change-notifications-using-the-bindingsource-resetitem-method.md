---
title: '方法 : BindingSource ResetItem メソッドを使用して変更通知を発生させる'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- change notifications [Windows Forms], raising
- data binding [Windows Forms], change notifications
- BindingSource component [Windows Forms], raising change notifications with
- data sources [Windows Forms], detecting changes
- change notifications
ms.assetid: ab8b4096-37ff-4e30-aabc-de79a2f2e972
ms.openlocfilehash: 5894e7036126cb5271cea65e6025e9880b0cbe3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-raise-change-notifications-using-the-bindingsource-resetitem-method"></a>方法 : BindingSource ResetItem メソッドを使用して変更通知を発生させる
コントロールのデータ ソースの中には、項目が変更、追加、または削除されても変更通知が発生しないものがあります。 <xref:System.Windows.Forms.BindingSource> コンポーネントを使用すると、そのようなデータ ソースをバインドし、コードから変更通知を発生させることができます。  
  
## <a name="example"></a>例  
 このフォームは、<xref:System.Windows.Forms.BindingSource> コンポーネントを使用してリストを <xref:System.Windows.Forms.DataGridView> コントロールにバインドする方法を示しています。 リストは変更通知を発生しないため、リスト内の項目が変更されると、<xref:System.Windows.Forms.BindingSource> の <xref:System.Windows.Forms.BindingSource.ResetItem%2A> メソッドが呼び出されます。 である必要があります。  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetItem#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Data、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。 この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。  また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [BindingSource コンポーネント](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [方法: Windows フォーム コントロールを型にバインドする](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
