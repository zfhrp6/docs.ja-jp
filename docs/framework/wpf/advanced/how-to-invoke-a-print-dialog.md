---
title: "方法 : 印刷ダイアログ ボックスを呼び出す"
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
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8831566daca6ca36b40fbaaedbec9ff3ca8aaa99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-invoke-a-print-dialog"></a><span data-ttu-id="0ccca-102">方法 : 印刷ダイアログ ボックスを呼び出す</span><span class="sxs-lookup"><span data-stu-id="0ccca-102">How to: Invoke a Print Dialog</span></span>
<span data-ttu-id="0ccca-103">アプリケーションから印刷する機能を提供するだけで作成して開く、、<xref:System.Windows.Controls.PrintDialog>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="0ccca-103">To provide the ability to print from you application, you can simply create and open a <xref:System.Windows.Controls.PrintDialog> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ccca-104">例</span><span class="sxs-lookup"><span data-stu-id="0ccca-104">Example</span></span>  
 <span data-ttu-id="0ccca-105"><xref:System.Windows.Controls.PrintDialog> コントロールには、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、構成、および [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ジョブの送信用の 1 つのエントリ ポイントが用意されています。</span><span class="sxs-lookup"><span data-stu-id="0ccca-105">The <xref:System.Windows.Controls.PrintDialog> control provides a single entry point for [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], configuration, and [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] job submission.</span></span> <span data-ttu-id="0ccca-106">コントロールが使いやすいを使用して、インスタンス化できます[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]マークアップやコード。</span><span class="sxs-lookup"><span data-stu-id="0ccca-106">The control is easy to use and can be instantiated by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup or code.</span></span> <span data-ttu-id="0ccca-107">次の例では、インスタンスを作成し、コードでコントロールを開く方法とそのプリンターから印刷する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0ccca-107">The following example demonstrates how to instantiate and open the control in code and how to print from it.</span></span> <span data-ttu-id="0ccca-108">ダイアログ ボックスは、ユーザーを特定のページ範囲を設定するオプションを確認する方法も示しています。</span><span class="sxs-lookup"><span data-stu-id="0ccca-108">It also shows how to ensure that the dialog will give the user the option of setting a specific range of pages.</span></span> <span data-ttu-id="0ccca-109">コード例では、FixedDocumentSequence.xps c: ドライブのルート内のファイルがあることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="0ccca-109">The example code assumes that there is a file FixedDocumentSequence.xps in the root of the C: drive.</span></span>  
  
 [!code-csharp[printdialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 <span data-ttu-id="0ccca-110">ダイアログ ボックスが表示されたら、ユーザーは自分のコンピューターにインストールされているプリンターを選択することになります。</span><span class="sxs-lookup"><span data-stu-id="0ccca-110">Once the dialog is open, users will be able to select from the printers installed on their computer.</span></span> <span data-ttu-id="0ccca-111">選択した場合のオプションもありますが、 [Microsoft XPS Document Writer](http://go.microsoft.com/fwlink/?LinkId=147319)を作成する、[!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)]印刷ではなくファイル。</span><span class="sxs-lookup"><span data-stu-id="0ccca-111">They will also have the option of selecting the [Microsoft XPS Document Writer](http://go.microsoft.com/fwlink/?LinkId=147319) to create an [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] file instead of printing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ccca-112"><xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>の制御[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、これは、このトピックの内容について説明する必要がありますと混同しないで、<xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType>コンポーネント[!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="0ccca-112">The <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> control of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], which is discussed in this topic, should not be confused with the <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> component of [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)].</span></span>  
  
 <span data-ttu-id="0ccca-113">厳密には、使用することができます、<xref:System.Windows.Controls.PrintDialog.PrintDocument%2A>ダイアログを開くことがなくメソッドです。</span><span class="sxs-lookup"><span data-stu-id="0ccca-113">Strictly speaking, you can use the <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> method without ever opening the dialog.</span></span> <span data-ttu-id="0ccca-114">その意味では、コンポーネントとして含まれる未知、印刷コントロールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0ccca-114">In that sense, the control can be used as an unseen printing component.</span></span> <span data-ttu-id="0ccca-115">パフォーマンス上の理由から、いずれかを使用する方がよいなりますが、<xref:System.Printing.PrintQueue.AddJob%2A>メソッドまたは多くのいずれかの<xref:System.Windows.Xps.XpsDocumentWriter.Write%2A>と<xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>のメソッド、 <xref:System.Windows.Xps.XpsDocumentWriter>。</span><span class="sxs-lookup"><span data-stu-id="0ccca-115">But for performance reasons, it would be better to use either the <xref:System.Printing.PrintQueue.AddJob%2A> method or one of the many <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> and <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> methods of the <xref:System.Windows.Xps.XpsDocumentWriter>.</span></span> <span data-ttu-id="0ccca-116">詳細については、これは、次を参照してください。 [XPS ファイルをプログラムによって印刷](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md)とします。</span><span class="sxs-lookup"><span data-stu-id="0ccca-116">For more about this, see [Programmatically Print XPS Files](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md) and .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ccca-117">参照</span><span class="sxs-lookup"><span data-stu-id="0ccca-117">See Also</span></span>  
 <xref:System.Windows.Controls.PrintDialog>  
 [<span data-ttu-id="0ccca-118">WPF のドキュメント</span><span class="sxs-lookup"><span data-stu-id="0ccca-118">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="0ccca-119">印刷の概要</span><span class="sxs-lookup"><span data-stu-id="0ccca-119">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [<span data-ttu-id="0ccca-120">Microsoft XPS Document Writer</span><span class="sxs-lookup"><span data-stu-id="0ccca-120">Microsoft XPS Document Writer</span></span>](http://go.microsoft.com/fwlink/?LinkId=147319)
