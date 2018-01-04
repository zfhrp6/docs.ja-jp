---
title: "TableLayoutPanel コントロールの推奨される手順"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- layout [Windows Forms]
- TableLayoutPanel control [Windows Forms], best practices
- forms [Windows Forms], best practices
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- layout [Windows Forms], AutoSize
- layout [Windows Forms], best practices
- best practices [Windows Forms], tableLayoutPanel control
- sizing [Windows Forms], automatic
- automatic sizing
ms.assetid: b6706efb-d7a4-45ec-8cf4-08fa993e3afb
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f2c5a16ea1f07f7688c9df14bdb6b29350f3acf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a><span data-ttu-id="644cd-102">TableLayoutPanel コントロールの推奨される手順</span><span class="sxs-lookup"><span data-stu-id="644cd-102">Best Practices for the TableLayoutPanel Control</span></span>
<span data-ttu-id="644cd-103"><xref:System.Windows.Forms.TableLayoutPanel>コントロールは、Windows フォームで使用する前に慎重に考慮すべき強力なレイアウト機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="644cd-103">The <xref:System.Windows.Forms.TableLayoutPanel> control provides powerful layout features that you should consider carefully before using on your Windows Forms.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="644cd-104">推奨事項</span><span class="sxs-lookup"><span data-stu-id="644cd-104">Recommendations</span></span>  
 <span data-ttu-id="644cd-105">次の推奨事項は、使用するのに役立つ、<xref:System.Windows.Forms.TableLayoutPanel>最大限に活用するコントロール。</span><span class="sxs-lookup"><span data-stu-id="644cd-105">The following recommendations will help you use the <xref:System.Windows.Forms.TableLayoutPanel> control to its best advantage.</span></span>  
  
### <a name="targeted-use"></a><span data-ttu-id="644cd-106">対象の使用</span><span class="sxs-lookup"><span data-stu-id="644cd-106">Targeted Use</span></span>  
 <span data-ttu-id="644cd-107">使用して、<xref:System.Windows.Forms.TableLayoutPanel>慎重を制御します。</span><span class="sxs-lookup"><span data-stu-id="644cd-107">Use the <xref:System.Windows.Forms.TableLayoutPanel> control sparingly.</span></span> <span data-ttu-id="644cd-108">サイズ変更可能なレイアウトを必要とするすべての状況で使用する必要がありますされません。</span><span class="sxs-lookup"><span data-stu-id="644cd-108">You should not use it in all situations that require a resizable layout.</span></span> <span data-ttu-id="644cd-109">次のリストの使用を最大限に活用するレイアウトの説明、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="644cd-109">The following list describes layouts that benefit most from the use of the <xref:System.Windows.Forms.TableLayoutPanel> control:</span></span>  
  
-   <span data-ttu-id="644cd-110">保存されているフォームの相互に比例してサイズが変更される複数の部分のレイアウトです。</span><span class="sxs-lookup"><span data-stu-id="644cd-110">Layouts in which there are multiple parts of the form that resize proportionally to each other.</span></span>  
  
-   <span data-ttu-id="644cd-111">変更または追加、または削除、ユーザーがカスタマイズできるフィールドを持つデータ エントリ フォームなどの実行時に動的に生成されるレイアウトは、基本設定に基づいています。</span><span class="sxs-lookup"><span data-stu-id="644cd-111">Layouts that will be modified or generated dynamically at run time, such as data entry forms that have user-customizable fields added or subtracted based on preferences.</span></span>  
  
-   <span data-ttu-id="644cd-112">レイアウトを全体の固定サイズのままにします。</span><span class="sxs-lookup"><span data-stu-id="644cd-112">Layouts that should remain at an overall fixed size.</span></span> <span data-ttu-id="644cd-113">たとえば、800 x 600 よりも小さい必要のあるダイアログ ボックスがありますが、ローカライズされた文字列をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="644cd-113">For example, you may have a dialog box that should remain smaller than 800 x 600, but you need to support localized strings.</span></span>  
  
 <span data-ttu-id="644cd-114">次のように、有効ではありませんが大幅に使用するレイアウト、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="644cd-114">The following list describes layouts that do not benefit greatly from using the <xref:System.Windows.Forms.TableLayoutPanel> control:</span></span>  
  
-   <span data-ttu-id="644cd-115">単純なデータ エントリ フォームを 1 つの列のラベルとテキスト入力領域の 1 つの列です。</span><span class="sxs-lookup"><span data-stu-id="644cd-115">Simple data entry forms with a single column of labels and a single column of text-entry areas.</span></span>  
  
-   <span data-ttu-id="644cd-116">1 つの大きなフォームは、サイズ変更が発生したときに使用可能なすべての領域の塗りつぶし領域を表示します。</span><span class="sxs-lookup"><span data-stu-id="644cd-116">Forms with a single large display area that should fill all the available space when a resize occurs.</span></span> <span data-ttu-id="644cd-117">この例は、1 つを表示するフォーム<xref:System.Windows.Forms.PropertyGrid>コントロール。</span><span class="sxs-lookup"><span data-stu-id="644cd-117">An example of this is a form that displays a single <xref:System.Windows.Forms.PropertyGrid> control.</span></span> <span data-ttu-id="644cd-118">この例を使用して固定、フォームのサイズが変更されるときにそれ以外のものを展開するためです。</span><span class="sxs-lookup"><span data-stu-id="644cd-118">In this case, use anchoring, because nothing else should expand when the form is resized.</span></span>  
  
 <span data-ttu-id="644cd-119">内にある必要があるコントロールを慎重に選択して、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="644cd-119">Choose carefully which controls need to be in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="644cd-120">アンカーを使用して、30% ずつ増加して、文字列を使っている場合は、使用を検討して、<xref:System.Windows.Forms.Control.Anchor%2A>プロパティのみです。</span><span class="sxs-lookup"><span data-stu-id="644cd-120">If you have room for your text to grow by 30% using anchoring, consider using the <xref:System.Windows.Forms.Control.Anchor%2A> property only.</span></span> <span data-ttu-id="644cd-121">場合は、レイアウトに必要な領域を見積もるを使用して<xref:System.Windows.Forms.Control.Dock%2A>と<xref:System.Windows.Forms.Control.Anchor%2A>残りの領域の詳細の見積もりよりも簡単です、<xref:System.Windows.Forms.Control.AutoSize%2A>動作します。</span><span class="sxs-lookup"><span data-stu-id="644cd-121">If you can estimate the space required by your layout, use of <xref:System.Windows.Forms.Control.Dock%2A> and <xref:System.Windows.Forms.Control.Anchor%2A> is easier than estimating the details of remaining space and <xref:System.Windows.Forms.Control.AutoSize%2A> behavior.</span></span>  
  
 <span data-ttu-id="644cd-122">一般を使用してレイアウトを設計するとき、<xref:System.Windows.Forms.TableLayoutPanel>制御、できるだけ単純な設計を保持します。</span><span class="sxs-lookup"><span data-stu-id="644cd-122">In general, when designing your layout with the <xref:System.Windows.Forms.TableLayoutPanel> control, keep the design as simple as possible.</span></span>  
  
### <a name="use-the-document-outline-window"></a><span data-ttu-id="644cd-123">ドキュメント アウトライン ウィンドウを使用します。</span><span class="sxs-lookup"><span data-stu-id="644cd-123">Use the Document Outline Window</span></span>  
 <span data-ttu-id="644cd-124">ドキュメント アウトライン ウィンドウでは、コントロールの z オーダーと、親子のリレーションシップを操作に使用できるのレイアウトのツリー ビューを示します。</span><span class="sxs-lookup"><span data-stu-id="644cd-124">The Document Outline window gives you a tree view of your layout, which you can use to manipulate the z-order and parent-child relationships of your controls.</span></span> <span data-ttu-id="644cd-125">**表示 メニュー****その他のウィンドウ**選択してから、 **ドキュメント アウトライン**です。</span><span class="sxs-lookup"><span data-stu-id="644cd-125">From the **View menu**, select **Other Windows**, then select **Document Outline**.</span></span>  
  
### <a name="avoid-nesting"></a><span data-ttu-id="644cd-126">入れ子を回避します。</span><span class="sxs-lookup"><span data-stu-id="644cd-126">Avoid Nesting</span></span>  
 <span data-ttu-id="644cd-127">その他の入れ子を避ける<xref:System.Windows.Forms.TableLayoutPanel>内で制御、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。</span><span class="sxs-lookup"><span data-stu-id="644cd-127">Avoid nesting other <xref:System.Windows.Forms.TableLayoutPanel> controls within a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="644cd-128">入れ子になったレイアウトのデバッグは難しくなります。</span><span class="sxs-lookup"><span data-stu-id="644cd-128">Debugging nested layouts can be difficult.</span></span>  
  
### <a name="avoid-visual-inheritance"></a><span data-ttu-id="644cd-129">ビジュアル継承を避ける</span><span class="sxs-lookup"><span data-stu-id="644cd-129">Avoid Visual Inheritance</span></span>  
 <span data-ttu-id="644cd-130"><xref:System.Windows.Forms.TableLayoutPanel>コントロールは、Windows フォーム デザイナーでのビジュアル継承をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="644cd-130">The <xref:System.Windows.Forms.TableLayoutPanel> control does not support visual inheritance in the Windows Forms Designer.</span></span> <span data-ttu-id="644cd-131">A <xref:System.Windows.Forms.TableLayoutPanel> 「ロックされている」デザイン時に、派生クラスでのコントロールが表示されます。</span><span class="sxs-lookup"><span data-stu-id="644cd-131">A <xref:System.Windows.Forms.TableLayoutPanel> control in a derived class appears as "locked" at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="644cd-132">参照</span><span class="sxs-lookup"><span data-stu-id="644cd-132">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>
