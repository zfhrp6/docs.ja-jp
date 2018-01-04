---
title: "Windows フォームでのヘルプの統合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [Windows Forms], Windows Forms (using designer)
- Windows Forms, Help (using designer)
- HTML Help [Windows Forms], Windows Forms (using designer)
- Help [Windows Forms], Windows applications (using designer)
- forms. Help (using designer)
- Windows applications [Windows Forms], Help (using designer)
ms.assetid: a8563d25-8a75-4bc7-a024-f1870591b50f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9563ce0ca95a728cc1a9aaa219fbc9fea2cd7153
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="integrating-user-help-in-windows-forms"></a><span data-ttu-id="6f0e6-102">Windows フォームでのヘルプの統合</span><span class="sxs-lookup"><span data-stu-id="6f0e6-102">Integrating User Help in Windows Forms</span></span>
<span data-ttu-id="6f0e6-103">これは、ユーザーが混乱したときにアシスタンスを有効に、よく見過ごされますに関して重要 Windows ベースのアプリケーションの構築のヘルプ システムです。</span><span class="sxs-lookup"><span data-stu-id="6f0e6-103">An essential, but often overlooked, aspect of building Windows-based applications is the Help system, as this is where users turn for assistance in times of confusion.</span></span> <span data-ttu-id="6f0e6-104">Windows フォームでは、次の 2 つの異なる種類のヘルプをサポート、それぞれによって提供される、 [HelpProvider コンポーネント](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="6f0e6-104">Windows Forms support two different types of Help, each provided by the [HelpProvider Component](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md).</span></span> <span data-ttu-id="6f0e6-105">1 つ目は、HTML または HTML ヘルプ 1 のいずれかのヘルプ ファイルをユーザーを指す必要があります。*x*または大きい値の形式です。</span><span class="sxs-lookup"><span data-stu-id="6f0e6-105">The first involves pointing the user to a Help file of either HTML or HTML Help 1.*x* or greater format.</span></span> <span data-ttu-id="6f0e6-106">2 番目できますを表示する簡単な"新機能"-個別のコントロールのヘルプを入力これは、ダイアログ ボックスで特に便利です。</span><span class="sxs-lookup"><span data-stu-id="6f0e6-106">The second can display brief "What's This"-type Help on individual controls; this is especially useful on dialog boxes.</span></span> <span data-ttu-id="6f0e6-107">ヘルプの両方の種類は、同じフォームで使用できます。</span><span class="sxs-lookup"><span data-stu-id="6f0e6-107">Both types of Help can be used on the same form.</span></span>  
  
 <span data-ttu-id="6f0e6-108">さらに、 [ToolTip コンポーネント](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)Windows フォームでコントロールの個々 のヘルプを提供するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="6f0e6-108">Additionally, the [ToolTip Component](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md) can be used to provide individual Help for controls on Windows Forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6f0e6-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="6f0e6-109">In This Section</span></span>  
 [<span data-ttu-id="6f0e6-110">方法: Windows アプリケーションにヘルプを提供する</span><span class="sxs-lookup"><span data-stu-id="6f0e6-110">How to: Provide Help in a Windows Application</span></span>](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md)  
 <span data-ttu-id="6f0e6-111">使用する方法について説明します、`HelpProvider`ヘルプ システムのファイルへのコントロールをリンクするコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="6f0e6-111">Explains how to use the `HelpProvider` component to link controls to files in a Help system.</span></span>  
  
 [<span data-ttu-id="6f0e6-112">方法: ポップアップ ヘルプを表示する</span><span class="sxs-lookup"><span data-stu-id="6f0e6-112">How to: Display Pop-up Help</span></span>](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)  
 <span data-ttu-id="6f0e6-113">使用する方法について説明します、`HelpProvider`コンポーネントを Windows フォームでポップアップ ヘルプを表示します。</span><span class="sxs-lookup"><span data-stu-id="6f0e6-113">Explains how to use the `HelpProvider` component to show pop-up Help on Windows Forms.</span></span>  
  
 [<span data-ttu-id="6f0e6-114">ツールヒントを使用したコントロールのヘルプ</span><span class="sxs-lookup"><span data-stu-id="6f0e6-114">Control Help Using ToolTips</span></span>](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 <span data-ttu-id="6f0e6-115">使用方法について説明、`ToolTip`コントロールに固有のヘルプを表示するコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="6f0e6-115">Describes using the `ToolTip` component to show control-specific Help.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6f0e6-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f0e6-116">Related Sections</span></span>  
 [<span data-ttu-id="6f0e6-117">HelpProvider コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6f0e6-117">HelpProvider Component</span></span>](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)  
 <span data-ttu-id="6f0e6-118">基本について説明します、`HelpProvider`コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="6f0e6-118">Explains the basics of the `HelpProvider` component.</span></span>  
  
 [<span data-ttu-id="6f0e6-119">ToolTip コンポーネント</span><span class="sxs-lookup"><span data-stu-id="6f0e6-119">ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)  
 <span data-ttu-id="6f0e6-120">基本について説明します、`ToolTip`コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="6f0e6-120">Explains the basics of the `ToolTip` component.</span></span>  
  
 [<span data-ttu-id="6f0e6-121">Windows フォームの概要</span><span class="sxs-lookup"><span data-stu-id="6f0e6-121">Windows Forms Overview</span></span>](../../../../docs/framework/winforms/windows-forms-overview.md)  
 <span data-ttu-id="6f0e6-122">Windows フォームの基本について説明します。</span><span class="sxs-lookup"><span data-stu-id="6f0e6-122">Explains the basics of Windows Forms.</span></span>  
  
 [<span data-ttu-id="6f0e6-123">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="6f0e6-123">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)  
 <span data-ttu-id="6f0e6-124">Windows フォームの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="6f0e6-124">Provides an overview of Windows Forms.</span></span>
