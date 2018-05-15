---
title: PageSetupDialog コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: 4e7b4548f5a178ed7b819dbc2edc37bb95e3e0f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a><span data-ttu-id="80f45-102">PageSetupDialog コンポーネントの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="80f45-102">PageSetupDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="80f45-103">Windows フォーム<xref:System.Windows.Forms.PageSetupDialog>コンポーネントは、構成済みのダイアログ ボックスが Windows ベースのアプリケーションで印刷ページの詳細を設定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="80f45-103">The Windows Forms <xref:System.Windows.Forms.PageSetupDialog> component is a pre-configured dialog box used to set page details for printing in Windows-based applications.</span></span> <span data-ttu-id="80f45-104">独自のダイアログ ボックスを構成する代わりに、ページの基本設定を設定するのにユーザーの簡単な解決策として、Windows ベース アプリケーションの中で使用します。</span><span class="sxs-lookup"><span data-stu-id="80f45-104">Use it within your Windows-based application as a simple solution for users to set page preferences in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="80f45-105">ユーザーに境界線と余白の調整、ヘッダーとフッター、および縦または横方向の設定を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="80f45-105">You can enable users to set border and margin adjustments, headers and footers, and portrait or landscape orientation.</span></span> <span data-ttu-id="80f45-106">Windows の標準のダイアログ ボックスを使用して、ユーザーがすぐに慣れる基本的な機能を持つアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="80f45-106">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span>  
  
## <a name="key-properties-and-methods"></a><span data-ttu-id="80f45-107">キー プロパティとメソッド</span><span class="sxs-lookup"><span data-stu-id="80f45-107">Key Properties and Methods</span></span>  
 <span data-ttu-id="80f45-108">使用して、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッドを実行時に、ダイアログ ボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="80f45-108">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="80f45-109">このコンポーネントには 1 つのページのいずれかに関連するプロパティを設定できます (<xref:System.Drawing.Printing.PrintDocument>クラス)、または任意の文書 (<xref:System.Drawing.Printing.PageSettings>クラス)。</span><span class="sxs-lookup"><span data-stu-id="80f45-109">This component has properties you can set that relate to either a single page (<xref:System.Drawing.Printing.PrintDocument> class) or any document (<xref:System.Drawing.Printing.PageSettings> class).</span></span> <span data-ttu-id="80f45-110">さらに、<xref:System.Windows.Forms.PageSetupDialog>に格納されている特定のプリンター設定を確認するコンポーネントを使用することができます、<xref:System.Drawing.Printing.PrinterSettings>クラスです。</span><span class="sxs-lookup"><span data-stu-id="80f45-110">Additionally, the <xref:System.Windows.Forms.PageSetupDialog> component can be used to determine specific printer settings, which are stored in the <xref:System.Drawing.Printing.PrinterSettings> class.</span></span>  
  
 <span data-ttu-id="80f45-111">フォームに追加されたとき、<xref:System.Windows.Forms.PageSetupDialog>コンポーネントは、Windows フォーム デザイナーの下部にあるトレイに表示されます。</span><span class="sxs-lookup"><span data-stu-id="80f45-111">When it is added to a form, the <xref:System.Windows.Forms.PageSetupDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80f45-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="80f45-112">See Also</span></span>  
 <xref:System.Windows.Forms.PageSetupDialog>  
 [<span data-ttu-id="80f45-113">PageSetupDialog コンポーネント</span><span class="sxs-lookup"><span data-stu-id="80f45-113">PageSetupDialog Component</span></span>](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)
