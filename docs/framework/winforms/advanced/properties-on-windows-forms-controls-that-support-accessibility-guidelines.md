---
title: "ユーザ補助ガイドラインをサポートする Windows フォーム コントロールのプロパティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, accessibility properties of controls
- accessibility [Windows Forms], Windows Forms control properties
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 967b4a0e883338c756aceef37d11edecfb978527
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="properties-on-windows-forms-controls-that-support-accessibility-guidelines"></a><span data-ttu-id="77dd3-102">ユーザ補助ガイドラインをサポートする Windows フォーム コントロールのプロパティ</span><span class="sxs-lookup"><span data-stu-id="77dd3-102">Properties on Windows Forms Controls That Support Accessibility Guidelines</span></span>
<span data-ttu-id="77dd3-103">Windows フォームの標準的なツールボックス上のコントロールは、キーボード フォーカスを公開することや、画面要素を公開するなど、ユーザー補助ガイドラインの多くをサポートします。</span><span class="sxs-lookup"><span data-stu-id="77dd3-103">Controls on the standard toolbox for Windows Forms support many of the accessibility guidelines, including exposing the keyboard focus and exposing the screen elements.</span></span>  
  
## <a name="planning-ahead-for-accessibility"></a><span data-ttu-id="77dd3-104">ユーザー補助の事前の計画</span><span class="sxs-lookup"><span data-stu-id="77dd3-104">Planning Ahead for Accessibility</span></span>  
 <span data-ttu-id="77dd3-105">コントロールのプロパティは、次の表に示すように、その他のユーザー補助ガイドラインをサポートするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="77dd3-105">The controls' properties can be used to support other accessibility guidelines as shown in the following table.</span></span> <span data-ttu-id="77dd3-106">さらに、プログラムの機能へのアクセスを提供するのにメニューを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="77dd3-106">Additionally, you should use menus to provide access to program features.</span></span>  
  
|<span data-ttu-id="77dd3-107">コントロールのプロパティ</span><span class="sxs-lookup"><span data-stu-id="77dd3-107">Control Property</span></span>|<span data-ttu-id="77dd3-108">ユーザー補助機能に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="77dd3-108">Considerations for Accessibility</span></span>|  
|----------------------|--------------------------------------|  
|<span data-ttu-id="77dd3-109">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="77dd3-109">AccessibleDescription</span></span>|<span data-ttu-id="77dd3-110">説明については、スクリーン リーダーなどのユーザー補助機能に報告されます。</span><span class="sxs-lookup"><span data-stu-id="77dd3-110">The description is reported to accessibility aids such as screen readers.</span></span> <span data-ttu-id="77dd3-111">ユーザー補助機能は専用のプログラムおよびデバイスで、障碍を持つユーザーがコンピューターをより効果的に使用するよう助けます。</span><span class="sxs-lookup"><span data-stu-id="77dd3-111">Accessibility aids are specialized programs and devices that help people with disabilities use computers more effectively.</span></span>|  
|<span data-ttu-id="77dd3-112">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="77dd3-112">AccessibleName</span></span>|<span data-ttu-id="77dd3-113">ユーザー補助機能に報告される名前です。</span><span class="sxs-lookup"><span data-stu-id="77dd3-113">The name that will be reported to the accessibility aids.</span></span>|  
|<span data-ttu-id="77dd3-114">AccessibleRole</span><span class="sxs-lookup"><span data-stu-id="77dd3-114">AccessibleRole</span></span>|<span data-ttu-id="77dd3-115">ユーザー インターフェイスの要素の使用方法をについて説明します。</span><span class="sxs-lookup"><span data-stu-id="77dd3-115">Describes the use of the element in the user interface.</span></span>|  
|<span data-ttu-id="77dd3-116">TabIndex</span><span class="sxs-lookup"><span data-stu-id="77dd3-116">TabIndex</span></span>|<span data-ttu-id="77dd3-117">フォームで実用的な移動パスを作成します。</span><span class="sxs-lookup"><span data-stu-id="77dd3-117">Creates a sensible navigational path through the form.</span></span> <span data-ttu-id="77dd3-118">など、関連するラベルのタブ オーダーの直前に、テキスト ボックスに、固有のラベルを持たないコントロールの重要です。</span><span class="sxs-lookup"><span data-stu-id="77dd3-118">It is important for controls without intrinsic labels, such as text boxes, to have their associated label immediately precede them in the tab order.</span></span>|  
|<span data-ttu-id="77dd3-119">テキスト</span><span class="sxs-lookup"><span data-stu-id="77dd3-119">Text</span></span>|<span data-ttu-id="77dd3-120">"&"の文字を使用して、アクセス キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="77dd3-120">Use the "&" character to create access keys.</span></span> <span data-ttu-id="77dd3-121">アクセス キーの使用は、機能を文書化されたキーボード アクセスを提供する部分です。</span><span class="sxs-lookup"><span data-stu-id="77dd3-121">Using access keys is part of providing documented keyboard access to features.</span></span>|  
|<span data-ttu-id="77dd3-122">フォント サイズ</span><span class="sxs-lookup"><span data-stu-id="77dd3-122">Font Size</span></span>|<span data-ttu-id="77dd3-123">フォント サイズが調整可能でない場合は、10 ポイント以上に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="77dd3-123">If the font size is not adjustable, then it should be set to 10 points or larger.</span></span> <span data-ttu-id="77dd3-124">フォームのフォント サイズを設定すると、後からフォームに追加されるすべてのコントロールが同じサイズになります。</span><span class="sxs-lookup"><span data-stu-id="77dd3-124">Once the form's font size is set, all the controls added to the form thereafter will have the same size.</span></span>|  
|<span data-ttu-id="77dd3-125">前景色</span><span class="sxs-lookup"><span data-stu-id="77dd3-125">Forecolor</span></span>|<span data-ttu-id="77dd3-126">このプロパティが既定値に設定されている場合、フォームにユーザーのカラー設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="77dd3-126">If this property is set to the default, then the user's color preferences will be used on the form.</span></span>|  
|<span data-ttu-id="77dd3-127">背景色</span><span class="sxs-lookup"><span data-stu-id="77dd3-127">Backcolor</span></span>|<span data-ttu-id="77dd3-128">このプロパティが既定値に設定されている場合、フォームにユーザーのカラー設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="77dd3-128">If this property is set to the default, then the user's color preferences will be used on the form.</span></span>|  
|<span data-ttu-id="77dd3-129">BackgroundImage</span><span class="sxs-lookup"><span data-stu-id="77dd3-129">BackgroundImage</span></span>|<span data-ttu-id="77dd3-130">このプロパティは、テキストを読みやすくする場合は空白のままにします。</span><span class="sxs-lookup"><span data-stu-id="77dd3-130">Leave this property blank to make text more readable.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77dd3-131">参照</span><span class="sxs-lookup"><span data-stu-id="77dd3-131">See Also</span></span>  
 [<span data-ttu-id="77dd3-132">チュートリアル: ユーザー補助対応の Windows ベースのアプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="77dd3-132">Walkthrough: Creating an Accessible Windows-based Application</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-creating-an-accessible-windows-based-application.md)
