---
title: "PrintDocument コンポーネント (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PrintDocument component [Windows Forms]
- printing [Windows Forms], documents
ms.assetid: 5af6a51d-66f6-43cd-a8cd-d64eb18fe7e7
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f37fdb04d29ae713d0ca851b53fe075c04a8e6bf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="printdocument-component-windows-forms"></a><span data-ttu-id="4ebde-102">PrintDocument コンポーネント (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="4ebde-102">PrintDocument Component (Windows Forms)</span></span>
<span data-ttu-id="4ebde-103">Windows フォーム `PrintDocument` コンポーネントを使用して印刷する対象を記述するプロパティを設定し、Windows ベースのアプリケーション内でドキュメントを印刷します。</span><span class="sxs-lookup"><span data-stu-id="4ebde-103">The Windows Forms `PrintDocument` component is used to set the properties that describe what to print and then to print the document within Windows-based applications.</span></span> <span data-ttu-id="4ebde-104">ドキュメント印刷のあらゆる側面を管理するために、<xref:System.Windows.Forms.PrintDialog> コンポーネントと組み合わせて使用することができます。</span><span class="sxs-lookup"><span data-stu-id="4ebde-104">It can be used in conjunction with the <xref:System.Windows.Forms.PrintDialog> component to be in command of all aspects of document printing.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4ebde-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4ebde-105">In This Section</span></span>  
 [<span data-ttu-id="4ebde-106">PrintDocument コンポーネントの概要</span><span class="sxs-lookup"><span data-stu-id="4ebde-106">PrintDocument Component Overview</span></span>](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md)  
 <span data-ttu-id="4ebde-107">印刷する内容を記述し、Windows ベースのアプリケーションで印刷を起動するプロパティを設定できる `PrintDocument` コンポーネントの一般的な概念を紹介します。</span><span class="sxs-lookup"><span data-stu-id="4ebde-107">Introduces the general concepts of the `PrintDocument` component, which allows you to set properties describing what to print and launches printing in a Windows-based application.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4ebde-108">参照</span><span class="sxs-lookup"><span data-stu-id="4ebde-108">Reference</span></span>  
 <xref:System.Drawing.Printing.PrintDocument>  
 <span data-ttu-id="4ebde-109">クラスとそのメンバーに関するリファレンス情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="4ebde-109">Provides reference information on the class and its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4ebde-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ebde-110">Related Sections</span></span>  
 [<span data-ttu-id="4ebde-111">Windows フォームにおける印刷のサポート</span><span class="sxs-lookup"><span data-stu-id="4ebde-111">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 <span data-ttu-id="4ebde-112">Windows フォームに関連する印刷のトピックの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="4ebde-112">Presents a list of printing topics related to Windows Forms.</span></span>  
  
 [<span data-ttu-id="4ebde-113">PrintDialog コンポーネント</span><span class="sxs-lookup"><span data-stu-id="4ebde-113">PrintDialog Component</span></span>](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 <span data-ttu-id="4ebde-114">ユーザーがプリンターの選択、印刷するページの選択、および印刷関連の設定を決定するために使用できる構成済みのダイアログ ボックスを表示できる、<xref:System.Windows.Forms.PrintDialog> コンポーネントの全般的な概要を紹介します。</span><span class="sxs-lookup"><span data-stu-id="4ebde-114">Introduces the general concepts of the <xref:System.Windows.Forms.PrintDialog> component, which allows you to display a pre-configured dialog box that users can use to select a printer, choose pages to print, and determine print-related settings.</span></span>  
  
 [<span data-ttu-id="4ebde-115">PrintPreviewControl コントロール</span><span class="sxs-lookup"><span data-stu-id="4ebde-115">PrintPreviewControl Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-windows-forms.md)  
 <span data-ttu-id="4ebde-116">独自の印刷プレビュー ダイアログ ボックスまたはコンポーネントの設計に使用できる、<xref:System.Windows.Forms.PrintPreviewControl> の一般的な概念を説明しています。</span><span class="sxs-lookup"><span data-stu-id="4ebde-116">Introduces the general concepts of the <xref:System.Windows.Forms.PrintPreviewControl>, which you can use to design your own print preview dialog box or component.</span></span>  
  
 [<span data-ttu-id="4ebde-117">PrintPreviewDialog コントロール</span><span class="sxs-lookup"><span data-stu-id="4ebde-117">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 <span data-ttu-id="4ebde-118"><xref:System.Windows.Forms.PrintPreviewDialog> コントロールの全般的な概念を説明します。このコントロールにより、ユーザーがドキュメントの印刷イメージを見るために使用する事前構成済みダイアログ ボックスを表示できます。</span><span class="sxs-lookup"><span data-stu-id="4ebde-118">Introduces the general concepts of the <xref:System.Windows.Forms.PrintPreviewDialog> control, which allows you to display a pre-configured dialog box that users can use to see a version of their document as it will look when it prints.</span></span>
