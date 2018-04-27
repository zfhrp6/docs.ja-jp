---
title: トランスポート セキュリティ付き BasicBinding
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f49b1de6-0254-4362-8ef2-fccd8ff9688b
caps.latest.revision: 26
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 4d06f7652f7366fc795cd157398bbb15ed78828c
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="basicbinding-with-transport-security"></a><span data-ttu-id="b9afe-102">トランスポート セキュリティ付き BasicBinding</span><span class="sxs-lookup"><span data-stu-id="b9afe-102">BasicBinding with Transport Security</span></span>
<span data-ttu-id="b9afe-103">このサンプルでは、基本的なバインディングを使用した SSL トランスポート セキュリティを示します。</span><span class="sxs-lookup"><span data-stu-id="b9afe-103">This sample demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="b9afe-104">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)電卓サービスを実装します。</span><span class="sxs-lookup"><span data-stu-id="b9afe-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b9afe-105">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="b9afe-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b9afe-106">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b9afe-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b9afe-107">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="b9afe-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b9afe-108">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="b9afe-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\TransportSecurity`  
  
## <a name="sample-details"></a><span data-ttu-id="b9afe-109">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="b9afe-109">Sample Details</span></span>  
 <span data-ttu-id="b9afe-110">既定で、基本的なバインディングは HTTP 通信をサポートします。</span><span class="sxs-lookup"><span data-stu-id="b9afe-110">By default, the basic binding supports HTTP communication.</span></span> <span data-ttu-id="b9afe-111">このサンプルでは、基本的なバインディングのトランスポート セキュリティを有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b9afe-111">The sample shows how to enable transport security for the basic binding.</span></span> <span data-ttu-id="b9afe-112">このサンプルを実行する前に、証明書を作成し、Web サーバー証明書ウィザードを使用してあらかじめ割り当てておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9afe-112">Before you run the sample, you must create a certificate and assign it by using the Web Server Certificate Wizard.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9afe-113">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9afe-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b9afe-114">プログラム コード サンプルでは、ものと同じ、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)サービス。</span><span class="sxs-lookup"><span data-stu-id="b9afe-114">The program code in the sample is identical to that of the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) service.</span></span> <span data-ttu-id="b9afe-115">次に示すサンプル構成のように、構成ファイル設定でエンドポイントとバインディングを定義すると、通信のセキュリティ保護が有効になるように変更されます。</span><span class="sxs-lookup"><span data-stu-id="b9afe-115">The endpoint definition and binding definition in the configuration file settings are modified to enable secure communication, as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <endpoint address=""  
                binding="basicHttpBinding"  
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
   </services>  
  <bindings>  
    <basicHttpBinding>  
      <!-- Configure basicHttpBinding with Transport security -- >  
      <!-- mode and clientCredentialType set to None.-->  
      <binding name="Binding1">  
        <security mode="Transport">  
          <transport clientCredentialType="None"/>  
        </security>  
      </binding>  
    </basicHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="b9afe-116">HTTPS にアクセスしようとしたときにこのサンプルで使用する証明書は Makecert.exe で作成されたテスト証明書であるため、セキュリティ警告が表示されます。 など、ブラウザーでアドレスhttps://localhost/servicemodelsamples/service.svcです。</span><span class="sxs-lookup"><span data-stu-id="b9afe-116">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert appears when you try to access an HTTPS: address in your browser, such as https://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="b9afe-117">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クライアントがテスト証明書に対して動作するようにするには、クライアントにコードを追加して、セキュリティ警告を非表示にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9afe-117">To allow the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client to work with a test certificate, some additional code is added to the client to suppress the security alert.</span></span> <span data-ttu-id="b9afe-118">そのためのコードとそれに必要なクラスは、実際の証明書を使用するときには不要です。</span><span class="sxs-lookup"><span data-stu-id="b9afe-118">This code, and the accompanying class, is not necessary when using real certificates.</span></span>  

```csharp
// This code is required only for test certificates such as those   
// created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 <span data-ttu-id="b9afe-119">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9afe-119">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b9afe-120">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="b9afe-120">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b9afe-121">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="b9afe-121">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b9afe-122">次のコマンドを使用して、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="b9afe-122">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command:</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="b9afe-123">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="b9afe-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="b9afe-124">実行したことを確認してください、[インターネット インフォメーション サービス (IIS) サーバー証明書のインストール手順](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)です。</span><span class="sxs-lookup"><span data-stu-id="b9afe-124">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4.  <span data-ttu-id="b9afe-125">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="b9afe-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="b9afe-126">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="b9afe-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9afe-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9afe-127">See Also</span></span>
