---
title: WS トランスポート セキュリティ
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33a20358-5e1b-458a-a6a9-15753bc7b99b
caps.latest.revision: 22
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 4a332394877e33f6ab97b4be77da6c3267d85401
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="ws-transport-security"></a><span data-ttu-id="95def-102">WS トランスポート セキュリティ</span><span class="sxs-lookup"><span data-stu-id="95def-102">WS Transport Security</span></span>
<span data-ttu-id="95def-103">このサンプルでは、<xref:System.ServiceModel.WSHttpBinding> バインディングを使用した SSL トランスポート セキュリティを示します。</span><span class="sxs-lookup"><span data-stu-id="95def-103">This sample demonstrates the use of SSL transport security with the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span> <span data-ttu-id="95def-104">既定で、`wsHttpBinding` バインディングは HTTP 通信を実現します。</span><span class="sxs-lookup"><span data-stu-id="95def-104">By default, the `wsHttpBinding` binding provides HTTP communication.</span></span> <span data-ttu-id="95def-105">トランスポート セキュリティ用に構成すると、バインディングは HTTPS 通信をサポートします。</span><span class="sxs-lookup"><span data-stu-id="95def-105">When configured for transport security, the binding supports HTTPS communication.</span></span> <span data-ttu-id="95def-106">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)電卓サービスを実装します。</span><span class="sxs-lookup"><span data-stu-id="95def-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="95def-107">`wsHttpBinding` は、クライアントとサービスのアプリケーション構成ファイルに指定され、構成されます。</span><span class="sxs-lookup"><span data-stu-id="95def-107">The `wsHttpBinding` is specified and configured in the application configuration files for the client and service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95def-108">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95def-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="95def-109">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="95def-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="95def-110">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="95def-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="95def-111">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="95def-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="95def-112">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="95def-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsTransportSecurity`  
  
 <span data-ttu-id="95def-113">プログラム コード サンプルでは、ものと同じ、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)サービス。</span><span class="sxs-lookup"><span data-stu-id="95def-113">The program code in the sample is identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="95def-114">このサンプルをビルドして実行する前に、証明書を作成し、Web サーバー証明書ウィザードを使用してあらかじめ割り当てておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="95def-114">You must create a certificate and assign it by using the Web Server Certificate Wizard before building and running the sample.</span></span> <span data-ttu-id="95def-115">次に示すクライアント用構成の例のように、構成ファイル設定でエンドポイントとバインディングを定義すると、`Transport` セキュリティ モードが有効になります。</span><span class="sxs-lookup"><span data-stu-id="95def-115">The endpoint definition and binding definition in the configuration file settings enable `Transport` security mode, as shown in the following sample configuration for the client.</span></span>  
  
```xml  
<system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address="https://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as None -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="95def-116">アドレス指定では https:// スキームを使用しています。</span><span class="sxs-lookup"><span data-stu-id="95def-116">The address specified uses the https:// scheme.</span></span> <span data-ttu-id="95def-117">このバインディング構成により、セキュリティ モードが `Transport` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="95def-117">The binding configuration sets the security mode to `Transport`.</span></span> <span data-ttu-id="95def-118">同じセキュリティ モードが、サービスの Web.config ファイルで指定される必要があります。</span><span class="sxs-lookup"><span data-stu-id="95def-118">The same security mode must be specified in the service's Web.config file.</span></span>  
  
 <span data-ttu-id="95def-119">Https にアクセスしようとしたときにこのサンプルで使用する証明書は Makecert.exe で作成されたテスト証明書であるため、セキュリティ警告が表示されます: で対応するhttps://localhost/servicemodelsamples/service.svc、お使いのブラウザーからです。</span><span class="sxs-lookup"><span data-stu-id="95def-119">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an https: address, such as https://localhost/servicemodelsamples/service.svc, from your browser.</span></span> <span data-ttu-id="95def-120">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クライアントがテスト証明書に対して問題なく動作するようにするには、クライアントにコードを追加して、セキュリティ警告を非表示にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="95def-120">To allow the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="95def-121">そのためのコードとそれに必要なクラスは、本運用の証明書を使用するときには不要です。</span><span class="sxs-lookup"><span data-stu-id="95def-121">This code, and the accompanying class, is not required when using production certificates.</span></span>  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="95def-122">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="95def-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="95def-123">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="95def-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="95def-124">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="95def-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="95def-125">次のコマンドを使用して、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="95def-125">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="95def-126">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="95def-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="95def-127">実行したことを確認してください、[インターネット インフォメーション サービス (IIS) サーバー証明書のインストール手順](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)です。</span><span class="sxs-lookup"><span data-stu-id="95def-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4.  <span data-ttu-id="95def-128">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="95def-128">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="95def-129">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="95def-129">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95def-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="95def-130">See Also</span></span>
