---
title: "WCF Web HTTP エラー処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 156960a6594f5475e339b36e5dabf46f26d13d62
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-web-http-error-handling"></a><span data-ttu-id="50dca-102">WCF Web HTTP エラー処理</span><span class="sxs-lookup"><span data-stu-id="50dca-102">WCF Web HTTP Error Handling</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="50dca-103"> Web HTTP エラー処理では、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web HTTP サービスからエラーを返すことができます。このサービスは、HTTP 状態コードを指定し、操作と同じ形式 (XML、JSON など) を使用してエラーの詳細を返します。</span><span class="sxs-lookup"><span data-stu-id="50dca-103"> Web HTTP error handling enables you to return errors from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web HTTP services that specify an HTTP status code and return error details using the same format as the operation (for example, XML or JSON).</span></span>  
  
## <a name="wcf-web-http-error-handling"></a><span data-ttu-id="50dca-104">WCF Web HTTP エラー処理</span><span class="sxs-lookup"><span data-stu-id="50dca-104">WCF Web HTTP Error Handling</span></span>  
 <span data-ttu-id="50dca-105"><xref:System.ServiceModel.Web.WebFaultException> クラスは、HTTP 状態コードを指定できるようにするコンストラクターを定義します。</span><span class="sxs-lookup"><span data-stu-id="50dca-105">The <xref:System.ServiceModel.Web.WebFaultException> class defines a constructor that allows you to specify an HTTP status code.</span></span> <span data-ttu-id="50dca-106">この状態コードは、クライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="50dca-106">This status code is then returned to the client.</span></span> <span data-ttu-id="50dca-107"><xref:System.ServiceModel.Web.WebFaultException> クラスのジェネリック バージョンである <xref:System.ServiceModel.Web.WebFaultException%601> を使用すると、発生したエラーに関する情報を格納しているユーザー定義型を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="50dca-107">A generic version of the <xref:System.ServiceModel.Web.WebFaultException> class, <xref:System.ServiceModel.Web.WebFaultException%601> enables you to return a user-defined type that contains information about the error that occurred.</span></span> <span data-ttu-id="50dca-108">このカスタム オブジェクトは、操作で定義された形式を使用してシリアル化され、クライアントに返されます。</span><span class="sxs-lookup"><span data-stu-id="50dca-108">This custom object is serialized using the format specified by the operation and returned to the client.</span></span> <span data-ttu-id="50dca-109">次の例は、HTTP 状態コードを返す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="50dca-109">The following example shows how to return an HTTP status code.</span></span>  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 <span data-ttu-id="50dca-110">次の例は、HTTP 状態コードおよび追加情報をユーザー定義型で返す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="50dca-110">The following example shows how to return an HTTP status code and extra information in a user-defined type.</span></span> <span data-ttu-id="50dca-111">`MyErrorDetail` は、発生したエラーに関する追加情報を格納しているユーザー定義型です。</span><span class="sxs-lookup"><span data-stu-id="50dca-111">`MyErrorDetail` is a user-defined type that contains extra information about the error that occurred.</span></span>  
  
```  
Public string Operation2()  
   // Operation logic  
   // ...   MyErrorDetail detail = new MyErrorDetail  
   {  
      Message = "Error Message",  
      ErrorCode = 123,  
   }  
   throw new WebFaultException<MyErrorDetail>(detail, HttpStatusCode.Forbidden);  
}  
```  
  
 <span data-ttu-id="50dca-112">このコードは、禁止されている状態コード、および `MyErrorDetails` オブジェクトのインスタンスを格納している本文と共に、HTTP 応答を返します。</span><span class="sxs-lookup"><span data-stu-id="50dca-112">The preceding code returns an HTTP response with the forbidden status code and a body that contains an instance of the `MyErrorDetails` object.</span></span> <span data-ttu-id="50dca-113">`MyErrorDetails` オブジェクトの形式は、次の値によって決まります。</span><span class="sxs-lookup"><span data-stu-id="50dca-113">The format of the `MyErrorDetails` object is determined by:</span></span>  
  
-   <span data-ttu-id="50dca-114">サービス操作で指定された `ResponseFormat` 属性または <xref:System.ServiceModel.Web.WebGetAttribute> 属性の <xref:System.ServiceModel.Web.WebInvokeAttribute> パラメーターの値。</span><span class="sxs-lookup"><span data-stu-id="50dca-114">The value of the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute specified on the service operation.</span></span>  
  
-   <span data-ttu-id="50dca-115"><xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> の値。</span><span class="sxs-lookup"><span data-stu-id="50dca-115">The value of <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.</span></span>  
  
-   <span data-ttu-id="50dca-116"><xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> プロパティの値 (<xref:System.ServiceModel.Web.OutgoingWebResponseContext> にアクセスして取得)。</span><span class="sxs-lookup"><span data-stu-id="50dca-116">The value of the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property by accessing the <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="50dca-117">これらの値は、操作の書式設定に及ぼす影響を参照してください。 [WCF Web HTTP 書式](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)です。</span><span class="sxs-lookup"><span data-stu-id="50dca-117"> how these values affect the formatting of the operation, see [WCF Web HTTP Formatting](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>  
  
 <span data-ttu-id="50dca-118"><xref:System.ServiceModel.Web.WebFaultException> は <xref:System.ServiceModel.FaultException> であるため、SOAP エンドポイントと Web HTTP エンドポイントを公開するサービスのエラー例外プログラミング モデルとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="50dca-118"><xref:System.ServiceModel.Web.WebFaultException> is a <xref:System.ServiceModel.FaultException> and therefore can be used as the fault exception programming model for services that expose SOAP endpoints as well as web HTTP endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50dca-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="50dca-119">See Also</span></span>  
 [<span data-ttu-id="50dca-120">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="50dca-120">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="50dca-121">WCF Web HTTP 形式</span><span class="sxs-lookup"><span data-stu-id="50dca-121">WCF Web HTTP Formatting</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)  
 [<span data-ttu-id="50dca-122">エラーの定義と指定</span><span class="sxs-lookup"><span data-stu-id="50dca-122">Defining and Specifying Faults</span></span>](../../../../docs/framework/wcf/defining-and-specifying-faults.md)  
 [<span data-ttu-id="50dca-123">例外とエラーの処理</span><span class="sxs-lookup"><span data-stu-id="50dca-123">Handling Exceptions and Faults</span></span>](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)  
 [<span data-ttu-id="50dca-124">エラーの送受信</span><span class="sxs-lookup"><span data-stu-id="50dca-124">Sending and Receiving Faults</span></span>](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
