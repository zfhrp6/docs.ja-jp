---
title: '方法 : Metadata Exchange コントラクトと共にサービス モニカーを使用する'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: 6265860c2e1efb2f74a0243157a223a33889629a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="18e16-102">方法 : Metadata Exchange コントラクトと共にサービス モニカーを使用する</span><span class="sxs-lookup"><span data-stu-id="18e16-102">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>
<span data-ttu-id="18e16-103">新しい WCF サービスを開発した後にスクリプトまたは Visual Basic 6.0 アプリケーションからこれらのサービスを呼び出せるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="18e16-103">After developing some new WCF services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="18e16-104">1 つのメソッドは、WCF クライアント アセンブリを生成、COM にアセンブリを登録、アセンブリを GAC にインストール、および Visual Basic コードから COM の型を参照することです。</span><span class="sxs-lookup"><span data-stu-id="18e16-104">One method would be to generate a WCF client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="18e16-105">アプリケーションを配布するときに、WCF クライアント アセンブリもを配布する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18e16-105">When you distribute the application, you will have to distribute the WCF Client assembly as well.</span></span> <span data-ttu-id="18e16-106">次にユーザーは COM を使用して WCF クライアント アセンブリを登録し、それを GAC に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18e16-106">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> <span data-ttu-id="18e16-107">WCF の COM 相互運用機能を使用すると、WCF クライアント アセンブリに依存せず、同じサービス呼び出しを行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="18e16-107">WCF COM Interop also allows you to make the same service calls without relying on a WCF client assembly.</span></span> <span data-ttu-id="18e16-108">WCF モニカーでは、metadata exchange (Mex) エンドポイント サービス モニカーを使用して型を抽出する URI を指定することで任意の COM 互換言語 (Visual Basic、VBScript、Visual Basic for Applications (VBA) やなど) からすべての WCF サービスを呼び出すことができます。サービスに関する情報。</span><span class="sxs-lookup"><span data-stu-id="18e16-108">The WCF moniker allows you to call any WCF service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="18e16-109">このトピックでは、Mex エンドポイントを指定する WCF モニカーを使用して WCF の入門サンプルを呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="18e16-109">This topic describes how to call the Getting Started WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18e16-110">WCF クライアント アセンブリで定義された型が実際にはインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="18e16-110">The types defined by the WCF client assembly are never actually instantiated.</span></span> <span data-ttu-id="18e16-111">アセンブリはメタデータにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="18e16-111">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="18e16-112">Mex アドレスを使うサービス モニカーの使用</span><span class="sxs-lookup"><span data-stu-id="18e16-112">Using the service moniker with a Mex address</span></span>  
  
1.  <span data-ttu-id="18e16-113">この入門サンプルをビルドし、Internet Explorer を使用して、その URL を参照 (http://localhost/ServiceModelSamples/Service.svc)サービスが動作していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="18e16-113">Build the Getting Started sample and use Internet Explorer to browse to its URL (http://localhost/ServiceModelSamples/Service.svc) to ensure that the service is working.</span></span>  
  
2.  <span data-ttu-id="18e16-114">Visual Basic スクリプトまたは Visual Basic アプリケーションを作成し、次のコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="18e16-114">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3.  <span data-ttu-id="18e16-115">作成した Visual Basic アプリケーションまたはスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="18e16-115">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="18e16-116">モニカーがサービスのメタデータを読み取るには、呼び出すサービスで、Mex エンドポイントが公開されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="18e16-116">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="18e16-117">詳細については、次を参照してください。[する方法: 構成ファイルを使用して、サービスのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)です。</span><span class="sxs-lookup"><span data-stu-id="18e16-117">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="18e16-118">モニカーの形式が正しくないか、`GetObject` を呼び出せない場合は、"構文が無効です" というメッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="18e16-118">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="18e16-119">このエラーが発生した場合は、使用しているモニカーが正しく、サービスが使用可能であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="18e16-119">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18e16-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="18e16-120">See Also</span></span>  
 [<span data-ttu-id="18e16-121">方法 : 未登録で Windows Communication Foundation のサービス モニカーを使用する</span><span class="sxs-lookup"><span data-stu-id="18e16-121">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 [<span data-ttu-id="18e16-122">方法 : WSDL コントラクトと共にサービス モニカーを使用する</span><span class="sxs-lookup"><span data-stu-id="18e16-122">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
