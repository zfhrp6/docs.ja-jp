---
title: "アプリケーションの Web サービスへのアクセス (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Web services [Visual Basic], My.WebServices object
- My.WebServices object
- applications [Visual Basic], Web services
ms.assetid: 8ad5405b-e771-42b1-82d3-ce97af2cea9e
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f15c0fd761f08f41abc05f7019ce27bc8cf8dff3
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="accessing-application-web-services-visual-basic"></a><span data-ttu-id="24ee8-102">アプリケーションの Web サービスへのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24ee8-102">Accessing Application Web Services (Visual Basic)</span></span>
<span data-ttu-id="24ee8-103">`My.WebServices` オブジェクトは、現在のプロジェクトにより参照されている各 Web サービスのインスタンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="24ee8-103">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="24ee8-104">各インスタンスは要求に応じてインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="24ee8-104">Each instance is instantiated on demand.</span></span> <span data-ttu-id="24ee8-105">これらの Web サービスには `My.WebServices` オブジェクトのプロパティを介してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="24ee8-105">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="24ee8-106">プロパティの名前は、プロパティがアクセスする Web サービスの名前と同じになります。</span><span class="sxs-lookup"><span data-stu-id="24ee8-106">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="24ee8-107"><xref:System.Web.Services.Protocols.SoapHttpClientProtocol> から継承されたクラスはすべて Web サービスです。</span><span class="sxs-lookup"><span data-stu-id="24ee8-107">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="24ee8-108">タスク</span><span class="sxs-lookup"><span data-stu-id="24ee8-108">Tasks</span></span>  
 <span data-ttu-id="24ee8-109">次の表は、アプリケーションにより参照される Web サービスにアクセスする方法を一覧にしたものです。</span><span class="sxs-lookup"><span data-stu-id="24ee8-109">The following table lists possible ways to access Web services referenced by an application.</span></span>  
  
|<span data-ttu-id="24ee8-110">目的</span><span class="sxs-lookup"><span data-stu-id="24ee8-110">To</span></span>|<span data-ttu-id="24ee8-111">参照トピック</span><span class="sxs-lookup"><span data-stu-id="24ee8-111">See</span></span>|  
|---|---|   
|<span data-ttu-id="24ee8-112">Web サービスを呼び出す</span><span class="sxs-lookup"><span data-stu-id="24ee8-112">Call a Web service</span></span>|[<span data-ttu-id="24ee8-113">My.WebServices オブジェクト</span><span class="sxs-lookup"><span data-stu-id="24ee8-113">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)|  
|<span data-ttu-id="24ee8-114">Web サービスを非同期で呼び出し、完了時にイベントを処理する</span><span class="sxs-lookup"><span data-stu-id="24ee8-114">Call a Web service asynchronously and handle an event when it completes</span></span>|[<span data-ttu-id="24ee8-115">方法 : Web サービスを非同期で呼び出す</span><span class="sxs-lookup"><span data-stu-id="24ee8-115">How to: Call a Web Service Asynchronously</span></span>](../../../visual-basic/developing-apps/programming/how-to-call-a-web-service-asynchronously.md)|  
  
## <a name="see-also"></a><span data-ttu-id="24ee8-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="24ee8-116">See Also</span></span>  
 [<span data-ttu-id="24ee8-117">My.WebServices オブジェクト</span><span class="sxs-lookup"><span data-stu-id="24ee8-117">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
