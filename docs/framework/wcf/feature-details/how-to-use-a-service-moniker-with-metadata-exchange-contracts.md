---
title: "方法 : Metadata Exchange コントラクトと共にサービス モニカーを使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ed6ce9b87a5e2d8945a57110c02cce8024439f14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="a85d6-102">方法 : Metadata Exchange コントラクトと共にサービス モニカーを使用する</span><span class="sxs-lookup"><span data-stu-id="a85d6-102">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>
<span data-ttu-id="a85d6-103">新しい [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスをいくつか開発した後に、そのサービスをスクリプトまたは Visual Basic 6.0 アプリケーションから呼び出せるようにする必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a85d6-103">After developing some new [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="a85d6-104">この方法の 1 つに、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント アセンブリを作成し、そのアセンブリを COM を使用して登録して GAC にインストールし、Visual Basic コードで COM 型を参照する方法があります。</span><span class="sxs-lookup"><span data-stu-id="a85d6-104">One method would be to generate a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="a85d6-105">アプリケーションを配布するときに、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント アセンブリも配信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a85d6-105">When you distribute the application, you will have to distribute the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Client assembly as well.</span></span> <span data-ttu-id="a85d6-106">次にユーザーは COM を使用して WCF クライアント アセンブリを登録し、それを GAC に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a85d6-106">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a85d6-107"> COM Interop でも、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント アセンブリに依存しない同じサービス呼び出しを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a85d6-107"> COM Interop also allows you to make the same service calls without relying on a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly.</span></span> <span data-ttu-id="a85d6-108">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] モニカーを使用すれば、サービスに関する型情報を抽出するためにサービス モニカーで使用されるメタデータ交換 (Mex) エンドポイント URI を指定することにより、必要な [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを任意の COM 互換言語 (Visual Basic、VBScript、Visual Basic for Applications (VBA) など) から呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="a85d6-108">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker allows you to call any [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="a85d6-109">ここでは、Mex エンドポイントを指定する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] モニカーを使用して、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の入門サンプルを呼び出す方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a85d6-109">This topic describes how to call the Getting Started [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sample using a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a85d6-110">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアント アセンブリで定義された型は、実際にインスタンス化されることはありません。</span><span class="sxs-lookup"><span data-stu-id="a85d6-110">The types defined by the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly are never actually instantiated.</span></span> <span data-ttu-id="a85d6-111">アセンブリはメタデータにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="a85d6-111">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="a85d6-112">Mex アドレスを使うサービス モニカーの使用</span><span class="sxs-lookup"><span data-stu-id="a85d6-112">Using the service moniker with a Mex address</span></span>  
  
1.  <span data-ttu-id="a85d6-113">入門サンプルを構築し、Internet Explorer を使用してその URL (http://localhost/ServiceModelSamples/Service.svc) を参照し、サービスが動作していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a85d6-113">Build the Getting Started sample and use Internet Explorer to browse to its URL (http://localhost/ServiceModelSamples/Service.svc) to ensure that the service is working.</span></span>  
  
2.  <span data-ttu-id="a85d6-114">Visual Basic スクリプトまたは Visual Basic アプリケーションを作成し、次のコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="a85d6-114">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3.  <span data-ttu-id="a85d6-115">作成した Visual Basic アプリケーションまたはスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="a85d6-115">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a85d6-116">モニカーがサービスのメタデータを読み取るには、呼び出すサービスで、Mex エンドポイントが公開されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a85d6-116">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="a85d6-117">詳細については、次を参照してください。[する方法: 構成ファイルを使用して、サービスのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)です。</span><span class="sxs-lookup"><span data-stu-id="a85d6-117">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a85d6-118">モニカーの形式が正しくないか、`GetObject` を呼び出せない場合は、"構文が無効です" というメッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="a85d6-118">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="a85d6-119">このエラーが発生した場合は、使用しているモニカーが正しく、サービスが使用可能であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a85d6-119">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a85d6-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="a85d6-120">See Also</span></span>  
 [<span data-ttu-id="a85d6-121">方法: 登録しないと Windows Communication Foundation サービス モニカーを使用します。</span><span class="sxs-lookup"><span data-stu-id="a85d6-121">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 [<span data-ttu-id="a85d6-122">方法: WSDL コントラクトと共にサービス モニカーを使用</span><span class="sxs-lookup"><span data-stu-id="a85d6-122">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
