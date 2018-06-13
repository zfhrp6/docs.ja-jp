---
title: アプリケーションの Web サービスへのアクセス (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Web services [Visual Basic], My.WebServices object
- My.WebServices object
- applications [Visual Basic], Web services
ms.assetid: 8ad5405b-e771-42b1-82d3-ce97af2cea9e
ms.openlocfilehash: b1d5a2166ace2ea16e1764139133457439675876
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583735"
---
# <a name="accessing-application-web-services-visual-basic"></a><span data-ttu-id="f52ac-102">アプリケーションの Web サービスへのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f52ac-102">Accessing Application Web Services (Visual Basic)</span></span>
<span data-ttu-id="f52ac-103">`My.WebServices` オブジェクトは、現在のプロジェクトにより参照されている各 Web サービスのインスタンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="f52ac-103">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="f52ac-104">各インスタンスは要求に応じてインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="f52ac-104">Each instance is instantiated on demand.</span></span> <span data-ttu-id="f52ac-105">これらの Web サービスには `My.WebServices` オブジェクトのプロパティを介してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f52ac-105">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="f52ac-106">プロパティの名前は、プロパティがアクセスする Web サービスの名前と同じになります。</span><span class="sxs-lookup"><span data-stu-id="f52ac-106">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="f52ac-107"><xref:System.Web.Services.Protocols.SoapHttpClientProtocol> から継承されたクラスはすべて Web サービスです。</span><span class="sxs-lookup"><span data-stu-id="f52ac-107">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="f52ac-108">[タスク]</span><span class="sxs-lookup"><span data-stu-id="f52ac-108">Tasks</span></span>  
 <span data-ttu-id="f52ac-109">次の表は、アプリケーションにより参照される Web サービスにアクセスする方法を一覧にしたものです。</span><span class="sxs-lookup"><span data-stu-id="f52ac-109">The following table lists possible ways to access Web services referenced by an application.</span></span>  
  
|<span data-ttu-id="f52ac-110">終了</span><span class="sxs-lookup"><span data-stu-id="f52ac-110">To</span></span>|<span data-ttu-id="f52ac-111">解決方法については、</span><span class="sxs-lookup"><span data-stu-id="f52ac-111">See</span></span>|  
|---|---|   
|<span data-ttu-id="f52ac-112">Web サービスを呼び出す</span><span class="sxs-lookup"><span data-stu-id="f52ac-112">Call a Web service</span></span>|[<span data-ttu-id="f52ac-113">My.WebServices オブジェクト</span><span class="sxs-lookup"><span data-stu-id="f52ac-113">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)|  
|<span data-ttu-id="f52ac-114">Web サービスを非同期で呼び出し、完了時にイベントを処理する</span><span class="sxs-lookup"><span data-stu-id="f52ac-114">Call a Web service asynchronously and handle an event when it completes</span></span>|[<span data-ttu-id="f52ac-115">方法 : Web サービスを非同期で呼び出す</span><span class="sxs-lookup"><span data-stu-id="f52ac-115">How to: Call a Web Service Asynchronously</span></span>](../../../visual-basic/developing-apps/programming/how-to-call-a-web-service-asynchronously.md)|  
  
## <a name="see-also"></a><span data-ttu-id="f52ac-116">参照</span><span class="sxs-lookup"><span data-stu-id="f52ac-116">See Also</span></span>  
 [<span data-ttu-id="f52ac-117">My.WebServices オブジェクト</span><span class="sxs-lookup"><span data-stu-id="f52ac-117">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
