---
title: "My の参照 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My feature
- My reference
ms.assetid: 6f803bd7-21ff-4569-b1fe-b00a6678b1e3
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9cf23a3cc435f3ddea778b368716a35dde90656c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="my-reference-visual-basic"></a><span data-ttu-id="9a2e1-102">My の参照 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a2e1-102">My Reference (Visual Basic)</span></span>
<span data-ttu-id="9a2e1-103">`My`機能により、プログラミング迅速かつ容易に一般的に使用されるメソッド、プロパティ、およびイベントへの直感的なアクセスを付与します。</span><span class="sxs-lookup"><span data-stu-id="9a2e1-103">The `My` feature makes programming faster and easier by giving you intuitive access to commonly used methods, properties, and events.</span></span> <span data-ttu-id="9a2e1-104">次の表に含まれるオブジェクト`My`、および各に実行できるアクション。</span><span class="sxs-lookup"><span data-stu-id="9a2e1-104">This table lists the objects contained in `My`, and the actions that can be performed with each.</span></span>  
  
|<span data-ttu-id="9a2e1-105">**動作**</span><span class="sxs-lookup"><span data-stu-id="9a2e1-105">**Action**</span></span>|<span data-ttu-id="9a2e1-106">**オブジェクト**</span><span class="sxs-lookup"><span data-stu-id="9a2e1-106">**Object**</span></span>|  
|----------------|----------------|  
|<span data-ttu-id="9a2e1-107">アプリケーションの情報およびサービスにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="9a2e1-107">Accessing application information and services.</span></span>|<span data-ttu-id="9a2e1-108">`My.Application` オブジェクトは、次のクラスで構成されています。</span><span class="sxs-lookup"><span data-stu-id="9a2e1-108">The `My.Application` object consists of the following classes:</span></span><br /><br /> <span data-ttu-id="9a2e1-109"><xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> は、すべてのプロジェクトで使用可能なメンバーを提供します。</span><span class="sxs-lookup"><span data-stu-id="9a2e1-109"><xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase> provides members that are available in all projects.</span></span><br /><br /> <span data-ttu-id="9a2e1-110"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> は、Windows フォーム アプリケーションで使用可能なメンバーを提供します。</span><span class="sxs-lookup"><span data-stu-id="9a2e1-110"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> provides members available in Windows Forms applications.</span></span><br /><br /> <span data-ttu-id="9a2e1-111"><xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> は、コンソール アプリケーションで使用可能なメンバーを提供します。</span><span class="sxs-lookup"><span data-stu-id="9a2e1-111"><xref:Microsoft.VisualBasic.ApplicationServices.ConsoleApplicationBase> provides members available in console applications.</span></span>|  
|<span data-ttu-id="9a2e1-112">ホスト コンピューターとそのリソース、サービス、およびデータにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="9a2e1-112">Accessing the host computer and its resources, services, and data.</span></span>|<span data-ttu-id="9a2e1-113">`My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>)</span><span class="sxs-lookup"><span data-stu-id="9a2e1-113">`My.Computer` (<xref:Microsoft.VisualBasic.Devices.Computer>)</span></span>|  
|<span data-ttu-id="9a2e1-114">現在のプロジェクトのフォームにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="9a2e1-114">Accessing the forms in the current project.</span></span>|[<span data-ttu-id="9a2e1-115">My.Forms オブジェクト</span><span class="sxs-lookup"><span data-stu-id="9a2e1-115">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)|  
|<span data-ttu-id="9a2e1-116">アプリケーション ログにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="9a2e1-116">Accessing the application log.</span></span>|<span data-ttu-id="9a2e1-117">`My.Application.Log` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log%2A>)</span><span class="sxs-lookup"><span data-stu-id="9a2e1-117">`My.Application.Log` (<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log%2A>)</span></span>|  
|<span data-ttu-id="9a2e1-118">現在の web 要求へのアクセス。</span><span class="sxs-lookup"><span data-stu-id="9a2e1-118">Accessing the current web request.</span></span>|[<span data-ttu-id="9a2e1-119">My.Request オブジェクト</span><span class="sxs-lookup"><span data-stu-id="9a2e1-119">My.Request Object</span></span>](../../../visual-basic/language-reference/objects/my-request-object.md)|  
|<span data-ttu-id="9a2e1-120">リソース要素にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="9a2e1-120">Accessing resource elements.</span></span>|[<span data-ttu-id="9a2e1-121">My.Resources オブジェクト</span><span class="sxs-lookup"><span data-stu-id="9a2e1-121">My.Resources Object</span></span>](../../../visual-basic/language-reference/objects/my-resources-object.md)|  
|<span data-ttu-id="9a2e1-122">現在の web 応答にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="9a2e1-122">Accessing the current web response.</span></span>|[<span data-ttu-id="9a2e1-123">My.Response オブジェクト</span><span class="sxs-lookup"><span data-stu-id="9a2e1-123">My.Response Object</span></span>](../../../visual-basic/language-reference/objects/my-response-object.md)|  
|<span data-ttu-id="9a2e1-124">ユーザーとアプリケーション レベルの設定にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="9a2e1-124">Accessing user and application level settings.</span></span>|[<span data-ttu-id="9a2e1-125">My.Settings オブジェクト</span><span class="sxs-lookup"><span data-stu-id="9a2e1-125">My.Settings Object</span></span>](../../../visual-basic/language-reference/objects/my-settings-object.md)|  
|<span data-ttu-id="9a2e1-126">現在のユーザーのセキュリティ コンテキストにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="9a2e1-126">Accessing the current user's security context.</span></span>|<span data-ttu-id="9a2e1-127">`My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>)</span><span class="sxs-lookup"><span data-stu-id="9a2e1-127">`My.User` (<xref:Microsoft.VisualBasic.ApplicationServices.User>)</span></span>|  
|<span data-ttu-id="9a2e1-128">現在のプロジェクトによって参照される XML Web サービスへのアクセス。</span><span class="sxs-lookup"><span data-stu-id="9a2e1-128">Accessing XML Web services referenced by the current project.</span></span>|[<span data-ttu-id="9a2e1-129">My.WebServices オブジェクト</span><span class="sxs-lookup"><span data-stu-id="9a2e1-129">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)|  
  
## <a name="see-also"></a><span data-ttu-id="9a2e1-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a2e1-130">See Also</span></span>  
 [<span data-ttu-id="9a2e1-131">Visual Basic アプリケーション モデルの概要</span><span class="sxs-lookup"><span data-stu-id="9a2e1-131">Overview of the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)  
 [<span data-ttu-id="9a2e1-132">My による開発</span><span class="sxs-lookup"><span data-stu-id="9a2e1-132">Development with My</span></span>](../../../visual-basic/developing-apps/development-with-my/index.md)
