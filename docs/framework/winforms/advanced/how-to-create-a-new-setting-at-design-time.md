---
title: "方法 : 設計時に新しい設定を作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e8a05b6f37f7686f18a6200e009aabe7eed5537
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-new-setting-at-design-time"></a><span data-ttu-id="9a75c-102">方法 : 設計時に新しい設定を作成する</span><span class="sxs-lookup"><span data-stu-id="9a75c-102">How To: Create a New Setting at Design Time</span></span>
<span data-ttu-id="9a75c-103">デザイン時に、新しい設定を作成するには、設定デザイナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="9a75c-103">You can create a new setting at design time by using the Settings designer.</span></span> <span data-ttu-id="9a75c-104">設定デザイナーは、グリッド スタイル インターフェイスを使用すると、新しい設定を作成し、それらの設定のプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="9a75c-104">The Settings designer is a grid-style interface that allows you to create new settings and specify properties for those settings.</span></span> <span data-ttu-id="9a75c-105">名前、値、型、および、新しい設定のスコープを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a75c-105">You must specify Name, Value, Type and Scope for your new settings.</span></span> <span data-ttu-id="9a75c-106">設定が作成されるは、コード内でアクセスします。</span><span class="sxs-lookup"><span data-stu-id="9a75c-106">Once a setting is created, it is accessible in code.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-c"></a><span data-ttu-id="9a75c-107">C# でのデザイン時に新しい設定を作成するには</span><span class="sxs-lookup"><span data-stu-id="9a75c-107">To create a new setting at design time in C#</span></span>  
  
1.  <span data-ttu-id="9a75c-108">**ソリューション エクスプ ローラー**、展開、**プロパティ**プロジェクトのノードです。</span><span class="sxs-lookup"><span data-stu-id="9a75c-108">In **Solution Explorer**, expand the **Properties** node of your project.</span></span>  
  
2.  <span data-ttu-id="9a75c-109">新しい設定を追加する .settings ファイルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="9a75c-109">Double-click the .settings file in which you want to add a new setting.</span></span> <span data-ttu-id="9a75c-110">このファイルの既定の名前は、Settings.settings です。</span><span class="sxs-lookup"><span data-stu-id="9a75c-110">The default name for this file is Settings.settings.</span></span>  
  
3.  <span data-ttu-id="9a75c-111">設定デザイナーでは、名前、値、型、およびスコープを設定を設定します。</span><span class="sxs-lookup"><span data-stu-id="9a75c-111">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="9a75c-112">各行は、1 つの設定を表します。</span><span class="sxs-lookup"><span data-stu-id="9a75c-112">Each row represents a single setting.</span></span>  
  
### <a name="to-create-a-new-setting-at-design-time-in-visual-basic"></a><span data-ttu-id="9a75c-113">Visual Basic でのデザイン時に新しい設定を作成するには</span><span class="sxs-lookup"><span data-stu-id="9a75c-113">To create a new setting at design time in Visual Basic</span></span>  
  
1.  <span data-ttu-id="9a75c-114">**ソリューション エクスプ ローラー**をプロジェクト ノードを右クリックして**プロパティ**です。</span><span class="sxs-lookup"><span data-stu-id="9a75c-114">In **Solution Explorer**, right-click your project node and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="9a75c-115">**プロパティ**] ページで、[、**設定**タブです。</span><span class="sxs-lookup"><span data-stu-id="9a75c-115">In the **Properties** page, select the **Settings** tab.</span></span>  
  
3.  <span data-ttu-id="9a75c-116">設定デザイナーでは、名前、値、型、およびスコープを設定を設定します。</span><span class="sxs-lookup"><span data-stu-id="9a75c-116">In the Settings designer, set the Name, Value, Type, and Scope for your setting.</span></span> <span data-ttu-id="9a75c-117">各行は、1 つの設定を表します。</span><span class="sxs-lookup"><span data-stu-id="9a75c-117">Each row represents a single setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a75c-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a75c-118">See Also</span></span>  
 [<span data-ttu-id="9a75c-119">アプリケーション設定とユーザー設定の使用</span><span class="sxs-lookup"><span data-stu-id="9a75c-119">Using Application Settings and User Settings</span></span>](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [<span data-ttu-id="9a75c-120">アプリケーション設定の概要</span><span class="sxs-lookup"><span data-stu-id="9a75c-120">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [<span data-ttu-id="9a75c-121">方法: 設計時に既存の設定の値を変更する</span><span class="sxs-lookup"><span data-stu-id="9a75c-121">How To: Change the Value of an Existing Setting at Design Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-an-existing-setting-at-design-time.md)
