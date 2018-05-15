---
title: WebContentTypeMapper のサンプル
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 89f13599e23f3e60ae4d9bc973debc436f46c147
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="webcontenttypemapper-sample"></a><span data-ttu-id="c6128-102">WebContentTypeMapper のサンプル</span><span class="sxs-lookup"><span data-stu-id="c6128-102">WebContentTypeMapper Sample</span></span>
<span data-ttu-id="c6128-103">このサンプルでは、Windows Communication Foundation (WCF) メッセージの本文の形式に新しいコンテンツの種類をマップする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c6128-103">This sample demonstrates how to map new content types to Windows Communication Foundation (WCF) message body formats.</span></span>  
  
 <span data-ttu-id="c6128-104"><xref:System.ServiceModel.Description.WebHttpEndpoint>要素は、により、JSON、XML、または同じエンドポイントで生のバイナリ メッセージを受信する WCF Web メッセージ エンコーダーをプラグインします。</span><span class="sxs-lookup"><span data-stu-id="c6128-104">The <xref:System.ServiceModel.Description.WebHttpEndpoint> element plugs in the Web message encoder, which allows WCF to receive JSON, XML, or raw binary messages at the same endpoint.</span></span> <span data-ttu-id="c6128-105">このエンコーダは、要求の HTTP コンテンツ タイプを調べて、メッセージ本文の書式を決定します。</span><span class="sxs-lookup"><span data-stu-id="c6128-105">The encoder determines the body format of the message by looking at the HTTP content-type of the request.</span></span> <span data-ttu-id="c6128-106">このサンプルでは、コンテンツ タイプと本文書式との間の割り当てを制御するための <xref:System.ServiceModel.Channels.WebContentTypeMapper> クラスを示します。</span><span class="sxs-lookup"><span data-stu-id="c6128-106">This sample introduces the <xref:System.ServiceModel.Channels.WebContentTypeMapper> class, which allows the user to control the mapping between content type and body format.</span></span>  
  
 <span data-ttu-id="c6128-107">WCF では、コンテンツの種類の既定のマッピングのセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="c6128-107">WCF provides a set of default mappings for content types.</span></span> <span data-ttu-id="c6128-108">たとえば、`application/json` は JSON に割り当てられ、`text/xml` は XML に割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="c6128-108">For example, `application/json` maps to JSON and `text/xml` maps to XML.</span></span> <span data-ttu-id="c6128-109">JSON または XML に割り当てられていないコンテンツ タイプは、生のバイナリ形式に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="c6128-109">Any content type that is not mapped to JSON or XML is mapped to raw binary format.</span></span>  
  
 <span data-ttu-id="c6128-110">場合によっては (プッシュ スタイルの API など)、クライアントによって返されるコンテンツ タイプがサービス開発者によって制御されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="c6128-110">In some scenarios (for example, push-style APIs), the service developer does not control the content type returned by the client.</span></span> <span data-ttu-id="c6128-111">たとえば、クライアントは `text/javascript` としてではなく `application/json` として JSON を返す場合があります。</span><span class="sxs-lookup"><span data-stu-id="c6128-111">For example, clients might return JSON as `text/javascript` instead of `application/json`.</span></span> <span data-ttu-id="c6128-112">この場合、サービス開発者は、特定のコンテンツ タイプを正しく処理できるように、次のサンプル コードに示すような <xref:System.ServiceModel.Channels.WebContentTypeMapper> の派生型を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6128-112">In this case, the service developer must provide a type that derives from <xref:System.ServiceModel.Channels.WebContentTypeMapper> to handle the given content type correctly, as shown in the following sample code.</span></span>  
  
```  
public class JsonContentTypeMapper : WebContentTypeMapper  
{  
    public override WebContentFormat  
               GetMessageFormatForContentType(string contentType)  
    {  
        if (contentType == "text/javascript")  
        {  
            return WebContentFormat.Json;  
        }  
        else  
        {  
            return WebContentFormat.Default;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="c6128-113">この派生型は、<xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> メソッドをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6128-113">The type must override the <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29> method.</span></span> <span data-ttu-id="c6128-114">このメソッドは、`contentType` 引数を評価して、<xref:System.ServiceModel.Channels.WebContentFormat.Json>、<xref:System.ServiceModel.Channels.WebContentFormat.Xml>、<xref:System.ServiceModel.Channels.WebContentFormat.Raw>、または <xref:System.ServiceModel.Channels.WebContentFormat.Default> のいずれかの値を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6128-114">The method must evaluate the `contentType` argument and return one of the following values: <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw>, or <xref:System.ServiceModel.Channels.WebContentFormat.Default>.</span></span> <span data-ttu-id="c6128-115"><xref:System.ServiceModel.Channels.WebContentFormat.Default> の戻り値は、Web メッセージ エンコーダの既定の割り当てによって決まります。</span><span class="sxs-lookup"><span data-stu-id="c6128-115">Returning <xref:System.ServiceModel.Channels.WebContentFormat.Default> defers to the default Web message encoder mappings.</span></span> <span data-ttu-id="c6128-116">前のサンプル コードでは、`text/javascript` コンテンツ タイプが JSON に割り当てられ、その他すべての割り当ては変わりません。</span><span class="sxs-lookup"><span data-stu-id="c6128-116">In the previous sample code, the `text/javascript` content type is mapped to JSON, and all other mappings remain unchanged.</span></span>  
  
 <span data-ttu-id="c6128-117">`JsonContentTypeMapper` クラスを使用するには、Web.config 内で次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="c6128-117">To use the `JsonContentTypeMapper` class, use the following in your Web.config:</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="c6128-118">JsonContentTypeMapper の使用要件を検証するには、Web.config ファイルから contentTypeMapper 属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="c6128-118">To verify the requirement for using the JsonContentTypeMapper, remove the contentTypeMapper attribute from the above configuration file.</span></span> <span data-ttu-id="c6128-119">`text/javascript` を使用して JSON コンテンツを送信しようとすると、クライアント ページの読み込みに失敗します。</span><span class="sxs-lookup"><span data-stu-id="c6128-119">The client page fails to load when attempting to use `text/javascript` to send JSON content.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c6128-120">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="c6128-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c6128-121">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="c6128-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c6128-122">ソリューションをビルドします WebContentTypeMapperSample.sln」の説明に従って[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="c6128-122">Build the solution WebContentTypeMapperSample.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="c6128-123">移動http://localhost/ServiceModelSamples/JCTMClientPage.htm(開かないで JCTMClientPage.htm プロジェクト ディレクトリ内からブラウザーで)。</span><span class="sxs-lookup"><span data-stu-id="c6128-123">Navigate to http://localhost/ServiceModelSamples/JCTMClientPage.htm (do not open JCTMClientPage.htm in the browser from within the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c6128-124">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="c6128-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c6128-125">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c6128-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c6128-126">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="c6128-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c6128-127">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c6128-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
  
## <a name="see-also"></a><span data-ttu-id="c6128-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6128-128">See Also</span></span>
