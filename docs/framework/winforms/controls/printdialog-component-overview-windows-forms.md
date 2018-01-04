---
title: "PrintDialog コンポーネントの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b90d94165de6985b43d47809ae57bfcae204f0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="printdialog-component-overview-windows-forms"></a><span data-ttu-id="389a9-102">PrintDialog コンポーネントの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="389a9-102">PrintDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="389a9-103">Windows フォーム[PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)コンポーネントは、構成済みのダイアログ ボックスのプリンターを選択し、印刷するページの選択、Windows ベースのアプリケーションで他の印刷関連の設定を決定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="389a9-103">The Windows Forms [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) component is a pre-configured dialog box used to select a printer, choose the pages to print, and determine other print-related settings in Windows-based applications.</span></span> <span data-ttu-id="389a9-104">独自のダイアログ ボックスを構成する代わりに、プリンターと印刷関連の設定の選択のための簡単なソリューションとして使用します。</span><span class="sxs-lookup"><span data-stu-id="389a9-104">Use it as a simple solution for printer and print-related settings selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="389a9-105">ユーザーが自分のドキュメントの多くの部分を印刷を有効にすることができます。 すべてを印刷、選択したページ範囲、または選択した印刷します。</span><span class="sxs-lookup"><span data-stu-id="389a9-105">You can enable users to print many parts of their documents: print all, print a selected page range, or print a selection.</span></span> <span data-ttu-id="389a9-106">Windows の標準のダイアログ ボックスを使用して、ユーザーがすぐに慣れる基本的な機能を持つアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="389a9-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="389a9-107"><xref:System.Windows.Forms.PrintDialog>コンポーネントが継承、<xref:System.Windows.Forms.CommonDialog>クラスです。</span><span class="sxs-lookup"><span data-stu-id="389a9-107">The <xref:System.Windows.Forms.PrintDialog> component inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="working-with-the-component"></a><span data-ttu-id="389a9-108">コンポーネントの操作</span><span class="sxs-lookup"><span data-stu-id="389a9-108">Working with the Component</span></span>  
 <span data-ttu-id="389a9-109">使用して、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッドを実行時に、ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="389a9-109">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="389a9-110">このコンポーネントには、単一の印刷ジョブのいずれかに関連するプロパティ (<xref:System.Drawing.Printing.PrintDocument>クラス) または個々 のプリンターの設定 (<xref:System.Drawing.Printing.PrinterSettings>クラス)。</span><span class="sxs-lookup"><span data-stu-id="389a9-110">This component has properties that relate to either a single print job (<xref:System.Drawing.Printing.PrintDocument> class) or the settings of an individual printer (<xref:System.Drawing.Printing.PrinterSettings> class).</span></span> <span data-ttu-id="389a9-111">さらに、これらのいずれかには複数のプリンターで共有することがあります。</span><span class="sxs-lookup"><span data-stu-id="389a9-111">Either of these, in turn, may be shared by multiple printers.</span></span>  
  
 <span data-ttu-id="389a9-112">フォームに追加されたとき、<xref:System.Windows.Forms.PrintDialog>コンポーネントは、Windows フォーム デザイナーの下部にあるトレイに表示されます。</span><span class="sxs-lookup"><span data-stu-id="389a9-112">When it is added to a form, the <xref:System.Windows.Forms.PrintDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="389a9-113">参照</span><span class="sxs-lookup"><span data-stu-id="389a9-113">See Also</span></span>  
 <xref:System.Windows.Forms.PrintDialog>  
 [<span data-ttu-id="389a9-114">PrintDialog コンポーネント</span><span class="sxs-lookup"><span data-stu-id="389a9-114">PrintDialog Component</span></span>](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)
