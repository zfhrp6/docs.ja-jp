---
title: "ラップされていないメッセージ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
caps.latest.revision: "22"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 99aa1d00c2992842a7019d4f4fc4aa98c25f644a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="unwrapped-messages"></a><span data-ttu-id="6053a-102">ラップされていないメッセージ</span><span class="sxs-lookup"><span data-stu-id="6053a-102">Unwrapped Messages</span></span>
<span data-ttu-id="6053a-103">このサンプルでは、ラップされていないメッセージを示します。</span><span class="sxs-lookup"><span data-stu-id="6053a-103">This sample demonstrates unwrapped messages.</span></span> <span data-ttu-id="6053a-104">既定では、メッセージの本文は、サービス操作に渡されるパラメーターがラップされるように書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="6053a-104">By default, the message body is formatted such that the parameters to a service operation are wrapped.</span></span> <span data-ttu-id="6053a-105">ラップされたモードでの `Add` サービスへの `ICalculator` 要求メッセージのサンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="6053a-105">The following sample shows an `Add` request message to the `ICalculator` service in wrapped mode.</span></span>  
  
```xml  
<s:Envelope   
    xmlns:s=http://www.w3.org/2003/05/soap-envelope  
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        …  
    </s:Header>  
    <s:Body>  
      <Add xmlns="http://Microsoft.ServiceModel.Samples">  
        <n1>100</n1>  
        <n2>15.99</n2>  
      </Add>  
    </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="6053a-106">メッセージ本文の `<Add>` 要素は、`n1` パラメータおよび `n2` パラメータをラップします。</span><span class="sxs-lookup"><span data-stu-id="6053a-106">The `<Add>` element in the message body wraps the `n1` and `n2` parameters.</span></span> <span data-ttu-id="6053a-107">これに対して、ラップされていないモードでの同様のメッセージのサンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="6053a-107">In contrast, the following sample shows the equivalent message in the unwrapped mode.</span></span>  
  
```xml  
<s:Envelope   
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"   
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        ….  
    </s:Header>  
    <s:Body>  
      <n1 xmlns="http://Microsoft.ServiceModel.Samples">100</n1>  
      <n2 xmlns="http://Microsoft.ServiceModel.Samples">15.99</n2>  
    </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
 <span data-ttu-id="6053a-108">ラップされていないメッセージは、格納要素内の `n1` パラメータおよび `n2` パラメータをラップしません。これらのパラメータは、SOAP 本文要素の直接の子になります。</span><span class="sxs-lookup"><span data-stu-id="6053a-108">The unwrapped message does not wrap the `n1` and `n2` parameters in a containing element, they are direct children of the soap body element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6053a-109">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6053a-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="6053a-110">このサンプルでは、ラップされていないメッセージは、サービス操作のパラメータ型に <xref:System.ServiceModel.MessageContractAttribute> を適用して値型を返すことによって作成されます。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6053a-110">In this sample, an unwrapped message is created by applying the <xref:System.ServiceModel.MessageContractAttribute> to the service operation parameter type and return value type as shown in the following sample code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    ResponseMessage Add(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Subtract(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Multiply(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Divide(RequestMessage request);  
}  
  
//setting IsWrapped to false means the n1 and n2  
//members will be direct children of the soap body element  
[MessageContract(IsWrapped = false)]  
public class RequestMessage  
{  
    [MessageBodyMember]  
    private double n1;  
    [MessageBodyMember]  
    private double n2;  
    //…  
}  
  
//setting IsWrapped to false means the result  
//member will be a direct child of the soap body element  
[MessageContract(IsWrapped = false)]  
public class ResponseMessage  
{  
    [MessageBodyMember]  
    private double result;  
    //…  
}  
```  
  
 <span data-ttu-id="6053a-111">送受信されたメッセージを表示できるようにするため、このサンプルではトレースを使用します。</span><span class="sxs-lookup"><span data-stu-id="6053a-111">To allow you to see the messages being sent and received, this sample uses tracing.</span></span> <span data-ttu-id="6053a-112">さらに、<xref:System.ServiceModel.WSHttpBinding> は、記録されるメッセージ数を減らす目的で、セキュリティを無効にして構成されています。</span><span class="sxs-lookup"><span data-stu-id="6053a-112">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, to reduce the number of messages it logs.</span></span>  
  
 <span data-ttu-id="6053a-113">結果のトレース ログ (c:\logs\Message.log) を使用して表示することができます、[サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="6053a-113">The resulting trace log (c:\logs\Message.log) can be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="6053a-114">メッセージの内容を表示するには選択**メッセージ**左と、サービス トレース ビューアー ツールの右側のウィンドウの両方でします。</span><span class="sxs-lookup"><span data-stu-id="6053a-114">To view message contents, select **Messages** in both the left and the right panes of the Service Trace Viewer tool.</span></span> <span data-ttu-id="6053a-115">このサンプルのトレース ログは、C:\LOGS フォルダーに生成されるように構成されています。</span><span class="sxs-lookup"><span data-stu-id="6053a-115">Trace logs in this sample are configured to be generated into the C:\LOGS folder.</span></span> <span data-ttu-id="6053a-116">サンプルの実行前にこのフォルダを作成し、ユーザー Network Service にそのディレクトリへの書き込み権限を与えます。</span><span class="sxs-lookup"><span data-stu-id="6053a-116">Create this folder before running the sample and give the user Network Service write permissions for this directory.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6053a-117">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="6053a-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6053a-118">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="6053a-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="6053a-119">メッセージのログ記録用に C:\LOGS ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="6053a-119">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="6053a-120">ユーザー Network Service にそのディレクトリの書き込み権限を与えます。</span><span class="sxs-lookup"><span data-stu-id="6053a-120">Give the user Network Service write permissions for this directory.</span></span>  
  
3.  <span data-ttu-id="6053a-121">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="6053a-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="6053a-122">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="6053a-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6053a-123">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="6053a-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6053a-124">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="6053a-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6053a-125">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="6053a-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6053a-126">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="6053a-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
  
## <a name="see-also"></a><span data-ttu-id="6053a-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="6053a-127">See Also</span></span>
