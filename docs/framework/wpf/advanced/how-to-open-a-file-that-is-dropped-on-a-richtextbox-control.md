---
title: '方法: RichTextBox コントロール上にドロップしたファイルを開く'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], RichTextBox
- RichTextBox [WPF], drag-and-drop
- drag-and-drop [WPF], open a dropped file
ms.assetid: 6bb8bb54-f576-41db-a9a7-24102ddeb490
ms.openlocfilehash: f3c10ae76a9afcc04578c590cc57cd43c3ab7a1e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547763"
---
# <a name="how-to-open-a-file-that-is-dropped-on-a-richtextbox-control"></a>方法: RichTextBox コントロール上にドロップしたファイルを開く
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]、 <xref:System.Windows.Controls.TextBox>、 <xref:System.Windows.Controls.RichTextBox>、および<xref:System.Windows.Documents.FlowDocument>組み込みのドラッグ アンド ドロップ機能をすべてのコントロールがあります。 組み込みの機能は、テキスト内と、コントロール間のドラッグ アンド ドロップできます。 ただし、コントロール上のファイルを削除することにより、ファイルを開く、ことはできません。 これらのコントロールは、処理済みとしても、ドラッグ アンド ドロップ イベントをマークします。 その結果、既定では、削除されたファイルを開くための機能を提供する独自のイベント ハンドラーを追加できません。  
  
 これらのコントロールでドラッグ アンド ドロップのイベントの追加の処理を追加するには、使用、<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>をドラッグ アンド ドロップのイベントのイベント ハンドラーを追加するメソッド。 設定、`handledEventsToo`パラメーターを`true`に呼び出すイベント ルート上の別の要素によって処理されるように既に指定されているルーティング イベントのハンドラーを指定します。  
  
> [!TIP]
>  組み込みのドラッグ アンド ドロップ機能を置き換えることができます<xref:System.Windows.Controls.TextBox>、 <xref:System.Windows.Controls.RichTextBox>、および<xref:System.Windows.Documents.FlowDocument>ドラッグ アンド ドロップのイベントのプレビュー バージョンを処理してプレビュー イベントを処理済みとしてマークします。 ただし、この組み込みのドラッグ アンド ドロップ機能を無効になります、お勧めできません。  
  
## <a name="example"></a>例  
 次の例は、のハンドラーを追加する方法を示します、<xref:System.Windows.DragDrop.DragOver>と<xref:System.Windows.DragDrop.Drop>上のイベント、<xref:System.Windows.Controls.RichTextBox>です。 この例では、<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>メソッドとセット、`handledEventsToo`パラメーターを`true`いなくても、イベント ハンドラーが呼び出されるように、<xref:System.Windows.Controls.RichTextBox>これらのイベントを処理済みとしてマークします。 イベント ハンドラーでコードがテキスト ファイルの削除を開く機能を追加、<xref:System.Windows.Controls.RichTextBox>です。  
  
 この例をテストする Windows エクスプ ローラーからテキスト ファイルまたはリッチ テキスト形式の (式 RTF) ファイルをドラッグ、<xref:System.Windows.Controls.RichTextBox>です。 ファイルが開きます、<xref:System.Windows.Controls.RichTextBox>です。 削除する前に、SHIFT キーを押した場合、ファイル、ファイルは、プレーン テキストとして開きます。  
  
 [!code-xaml[DragDropSnippets#RtbXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]  
  
 [!code-csharp[DragDropSnippets#RtbHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
 [!code-vb[DragDropSnippets#RtbHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]
