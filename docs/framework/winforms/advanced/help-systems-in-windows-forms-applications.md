---
title: "Windows フォーム アプリケーションのヘルプ システム"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [Windows Forms], adding to Windows applications
- Windows applications [Windows Forms], providing Help systems
- What's This? Help
- Help [Windows Forms], Windows Forms
- HelpProvider component [Windows Forms], providing Help in Windows applications
ms.assetid: 2a96a278-432c-41fc-9e3c-5bfedf5e1267
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 45d3385d008f823050f213252fdc2e1851cf422b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="help-systems-in-windows-forms-applications"></a><span data-ttu-id="ac93a-102">Windows フォーム アプリケーションのヘルプ システム</span><span class="sxs-lookup"><span data-stu-id="ac93a-102">Help Systems in Windows Forms Applications</span></span>
<span data-ttu-id="ac93a-103">1 つの最も重要な配慮をするように、アプリケーションの開発者は、ユーザーを提供できますが立つヘルプ システムです。</span><span class="sxs-lookup"><span data-stu-id="ac93a-103">One of the most important courtesies you, as a developer of applications, can furnish your users with is a competent Help system.</span></span> <span data-ttu-id="ac93a-104">これは、ここでは有効にする混乱または混乱になるときです。</span><span class="sxs-lookup"><span data-stu-id="ac93a-104">This is where they will turn when they become confused or disoriented.</span></span> <span data-ttu-id="ac93a-105">使用して簡単に実行が Windows ベースのアプリケーションにヘルプ システムを提供する、 [HelpProvider コンポーネント](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="ac93a-105">Providing a Help system in a Windows-based application is easily done by using the [HelpProvider Component](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md).</span></span>  
  
## <a name="different-types-of-help"></a><span data-ttu-id="ac93a-106">異なる種類のヘルプ</span><span class="sxs-lookup"><span data-stu-id="ac93a-106">Different Types of Help</span></span>  
 <span data-ttu-id="ac93a-107">Windows フォーム <xref:System.Windows.Forms.HelpProvider> コンポーネントは、Windows ベースのアプリケーションで HTML ヘルプ 1.x のヘルプ ファイル (HTML Help Workshop で生成された .chm ファイル、または .htm ファイル) を関連付けるために使用します。</span><span class="sxs-lookup"><span data-stu-id="ac93a-107">The Windows Forms <xref:System.Windows.Forms.HelpProvider> component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows-based application.</span></span> <span data-ttu-id="ac93a-108"><xref:System.Windows.Forms.HelpProvider>コンポーネントは、特定のコントロールや Windows フォームでコントロールの状況依存のヘルプを提供するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="ac93a-108">The <xref:System.Windows.Forms.HelpProvider> component can be used to provide context-sensitive Help for controls on Windows Forms or specific controls.</span></span> <span data-ttu-id="ac93a-109">さらに、<xref:System.Windows.Forms.HelpProvider>コンポーネントは、内容、インデックス、または検索関数のテーブルのメイン ページなどの特定領域へのヘルプ ファイルを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="ac93a-109">Additionally, the <xref:System.Windows.Forms.HelpProvider> component can open a Help file to specific areas, such as the main page of a table of contents, an index, or a search function.</span></span> <span data-ttu-id="ac93a-110">概要については、<xref:System.Windows.Forms.HelpProvider>コンポーネントを参照してください[HelpProvider コンポーネントの概要](../../../../docs/framework/winforms/controls/helpprovider-component-overview-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="ac93a-110">For general information about the <xref:System.Windows.Forms.HelpProvider> component, see [HelpProvider Component Overview](../../../../docs/framework/winforms/controls/helpprovider-component-overview-windows-forms.md).</span></span> <span data-ttu-id="ac93a-111">使用する方法について、 <xref:System.Windows.Forms.HelpProvider> Windows フォームでポップアップ ヘルプを表示するコンポーネントを参照してください[する方法: ポップアップ ヘルプを表示](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)です。</span><span class="sxs-lookup"><span data-stu-id="ac93a-111">For information on how to use the <xref:System.Windows.Forms.HelpProvider> component to show pop-up Help on Windows Forms, see [How to: Display Pop-up Help](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).</span></span> <span data-ttu-id="ac93a-112">使用方法について、<xref:System.Windows.Forms.ToolTip>コントロールに固有のヘルプを表示するコンポーネントを参照してください[コントロールのヘルプを使用してツールヒント](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)です。</span><span class="sxs-lookup"><span data-stu-id="ac93a-112">For information on using the <xref:System.Windows.Forms.ToolTip> component to show control-specific Help, see [Control Help Using ToolTips](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md).</span></span>  
  
 <span data-ttu-id="ac93a-113">HTML Help Workshop で HTML ヘルプ 1.x のファイルを生成することができます。</span><span class="sxs-lookup"><span data-stu-id="ac93a-113">You can generate HTML Help 1.x files with the HTML Help Workshop.</span></span> <span data-ttu-id="ac93a-114">HTML ヘルプの詳細については、"HTML Help Workshop"または MSDN の他の HTML Help」トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac93a-114">For more information on HTML Help, see the "HTML Help Workshop" or the other "HTML Help" topics in MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac93a-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac93a-115">See Also</span></span>  
 [<span data-ttu-id="ac93a-116">Windows フォームでのヘルプの統合</span><span class="sxs-lookup"><span data-stu-id="ac93a-116">Integrating User Help in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [<span data-ttu-id="ac93a-117">HelpProvider コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ac93a-117">HelpProvider Component</span></span>](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)  
 [<span data-ttu-id="ac93a-118">ToolTip コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ac93a-118">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)  
 [<span data-ttu-id="ac93a-119">Windows フォームの概要</span><span class="sxs-lookup"><span data-stu-id="ac93a-119">Windows Forms Overview</span></span>](../../../../docs/framework/winforms/windows-forms-overview.md)  
 [<span data-ttu-id="ac93a-120">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="ac93a-120">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
