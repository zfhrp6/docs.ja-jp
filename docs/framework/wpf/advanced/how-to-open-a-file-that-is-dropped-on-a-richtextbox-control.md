---
title: "方法: RichTextBox コントロール上にドロップしたファイルを開く"
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
- drag-and-drop [WPF], RichTextBox
- RichTextBox [WPF], drag-and-drop
- drag-and-drop [WPF], open a dropped file
ms.assetid: 6bb8bb54-f576-41db-a9a7-24102ddeb490
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7dfb5f0f442b18159c18a6e5345f6757674fbb90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-a-file-that-is-dropped-on-a-richtextbox-control"></a><span data-ttu-id="e5fc2-102">方法: RichTextBox コントロール上にドロップしたファイルを開く</span><span class="sxs-lookup"><span data-stu-id="e5fc2-102">How to: Open a File That is Dropped on a RichTextBox Control</span></span>
<span data-ttu-id="e5fc2-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]、 <xref:System.Windows.Controls.TextBox>、 <xref:System.Windows.Controls.RichTextBox>、および<xref:System.Windows.Documents.FlowDocument>組み込みのドラッグ アンド ドロップ機能をすべてのコントロールがあります。</span><span class="sxs-lookup"><span data-stu-id="e5fc2-103">In [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], the <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, and <xref:System.Windows.Documents.FlowDocument> controls all have built-in drag-and-drop functionality.</span></span> <span data-ttu-id="e5fc2-104">組み込みの機能は、テキスト内と、コントロール間のドラッグ アンド ドロップできます。</span><span class="sxs-lookup"><span data-stu-id="e5fc2-104">The built-in functionality enables drag-and-drop of text within and between the controls.</span></span> <span data-ttu-id="e5fc2-105">ただし、コントロール上のファイルを削除することにより、ファイルを開く、ことはできません。</span><span class="sxs-lookup"><span data-stu-id="e5fc2-105">However, it does not enable opening a file by dropping the file on the control.</span></span> <span data-ttu-id="e5fc2-106">これらのコントロールは、処理済みとしても、ドラッグ アンド ドロップ イベントをマークします。</span><span class="sxs-lookup"><span data-stu-id="e5fc2-106">These controls also mark the drag-and-drop events as handled.</span></span> <span data-ttu-id="e5fc2-107">その結果、既定では、削除されたファイルを開くための機能を提供する独自のイベント ハンドラーを追加できません。</span><span class="sxs-lookup"><span data-stu-id="e5fc2-107">As a result, by default, you cannot add your own event handlers to provide functionality to open dropped files.</span></span>  
  
 <span data-ttu-id="e5fc2-108">これらのコントロールでドラッグ アンド ドロップのイベントの追加の処理を追加するには、使用、<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>をドラッグ アンド ドロップのイベントのイベント ハンドラーを追加するメソッド。</span><span class="sxs-lookup"><span data-stu-id="e5fc2-108">To add additional handling for drag-and-drop events in these controls, use the <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> method to add your event handlers for the drag-and-drop events.</span></span> <span data-ttu-id="e5fc2-109">設定、`handledEventsToo`パラメーターを`true`に呼び出すイベント ルート上の別の要素によって処理されるように既に指定されているルーティング イベントのハンドラーを指定します。</span><span class="sxs-lookup"><span data-stu-id="e5fc2-109">Set the `handledEventsToo` parameter to `true` to have the specified handler be invoked for a routed event that has already been marked as handled by another element along the event route.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="e5fc2-110">組み込みのドラッグ アンド ドロップ機能を置き換えることができます<xref:System.Windows.Controls.TextBox>、 <xref:System.Windows.Controls.RichTextBox>、および<xref:System.Windows.Documents.FlowDocument>ドラッグ アンド ドロップのイベントのプレビュー バージョンを処理してプレビュー イベントを処理済みとしてマークします。</span><span class="sxs-lookup"><span data-stu-id="e5fc2-110">You can replace the built-in drag-and-drop functionality of <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, and <xref:System.Windows.Documents.FlowDocument> by handling the preview versions of the drag-and-drop events and marking the preview events as handled.</span></span> <span data-ttu-id="e5fc2-111">ただし、この組み込みのドラッグ アンド ドロップ機能を無効になります、お勧めできません。</span><span class="sxs-lookup"><span data-stu-id="e5fc2-111">However, this will disable the built-in drag-and-drop functionality, and is not recommended.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5fc2-112">例</span><span class="sxs-lookup"><span data-stu-id="e5fc2-112">Example</span></span>  
 <span data-ttu-id="e5fc2-113">次の例は、のハンドラーを追加する方法を示します、<xref:System.Windows.DragDrop.DragOver>と<xref:System.Windows.DragDrop.Drop>上のイベント、<xref:System.Windows.Controls.RichTextBox>です。</span><span class="sxs-lookup"><span data-stu-id="e5fc2-113">The following example demonstrates how to add handlers for the <xref:System.Windows.DragDrop.DragOver> and <xref:System.Windows.DragDrop.Drop> events on a <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="e5fc2-114">この例では、<xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>メソッドとセット、`handledEventsToo`パラメーターを`true`いなくても、イベント ハンドラーが呼び出されるように、<xref:System.Windows.Controls.RichTextBox>これらのイベントを処理済みとしてマークします。</span><span class="sxs-lookup"><span data-stu-id="e5fc2-114">This example uses the <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> method and sets the `handledEventsToo` parameter to `true` so that the events handlers will be invoked even though the <xref:System.Windows.Controls.RichTextBox> marks these events as handled.</span></span> <span data-ttu-id="e5fc2-115">イベント ハンドラーでコードがテキスト ファイルの削除を開く機能を追加、<xref:System.Windows.Controls.RichTextBox>です。</span><span class="sxs-lookup"><span data-stu-id="e5fc2-115">The code in the event handlers adds functionality to open a text file that is dropped on the <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 <span data-ttu-id="e5fc2-116">この例をテストする Windows エクスプ ローラーからテキスト ファイルまたはリッチ テキスト形式の (式 RTF) ファイルをドラッグ、<xref:System.Windows.Controls.RichTextBox>です。</span><span class="sxs-lookup"><span data-stu-id="e5fc2-116">To test this example, drag a text file or a rich text format (RTF) file from Windows Explorer to the <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="e5fc2-117">ファイルが開きます、<xref:System.Windows.Controls.RichTextBox>です。</span><span class="sxs-lookup"><span data-stu-id="e5fc2-117">The file will be opened in the <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="e5fc2-118">削除する前に、SHIFT キーを押した場合、ファイル、ファイルは、プレーン テキストとして開きます。</span><span class="sxs-lookup"><span data-stu-id="e5fc2-118">If you press the SHIFT key before the dropping the file, the file will be opened as plain text.</span></span>  
  
 [!code-xaml[DragDropSnippets#RtbXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml#rtbxaml)]  
  
 [!code-csharp[DragDropSnippets#RtbHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/dragdropsnippets/cs/mainwindow.xaml.cs#rtbhandlers)]
 [!code-vb[DragDropSnippets#RtbHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/dragdropsnippets/vb/mainwindow.xaml.vb#rtbhandlers)]
