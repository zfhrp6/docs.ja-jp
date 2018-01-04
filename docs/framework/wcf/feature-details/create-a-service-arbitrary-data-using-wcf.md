---
title: "方法 : WCF REST プログラミング モデルを使用して任意のデータを受け入れるサービスを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e566c15a-b600-4e4a-be3a-4af43e767dae
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 170149f5a6c495b3f22b9fd30f79ecdda87789b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-service-that-accepts-arbitrary-data-using-the-wcf-rest-programming-model"></a><span data-ttu-id="e6aef-102">方法 : WCF REST プログラミング モデルを使用して任意のデータを受け入れるサービスを作成する</span><span class="sxs-lookup"><span data-stu-id="e6aef-102">How to: Create a Service That Accepts Arbitrary Data using the WCF REST Programming Model</span></span>
<span data-ttu-id="e6aef-103">開発者は、データがサービス操作から返される流れを完全に制御する必要が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="e6aef-103">Sometimes developers must have full control of how data is returned from a service operation.</span></span> <span data-ttu-id="e6aef-104">たとえば、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ではサポートされない形式のデータを、サービス操作から返す必要がある場合です。</span><span class="sxs-lookup"><span data-stu-id="e6aef-104">This is the case when a service operation must return data in a format not supported by[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="e6aef-105">このトピックでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] REST プログラミング モデルを使用して任意のデータを受信するサービスの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e6aef-105">This topic discusses using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] REST Programming Model to create a service that receives arbitrary data.</span></span>  
  
### <a name="to-implement-the-service-contract"></a><span data-ttu-id="e6aef-106">サービス コントラクトを実装するには</span><span class="sxs-lookup"><span data-stu-id="e6aef-106">To implement the service contract</span></span>  
  
1.  <span data-ttu-id="e6aef-107">サービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="e6aef-107">Define the service contract.</span></span> <span data-ttu-id="e6aef-108">任意のデータを受信する操作には、<xref:System.IO.Stream> 型のパラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="e6aef-108">The operation that receives the arbitrary data must have a parameter of type <xref:System.IO.Stream>.</span></span> <span data-ttu-id="e6aef-109">さらに、このパラメーターは要求の本文に渡される唯一のパラメーターでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="e6aef-109">In addition, this parameter must be the only parameter passed in the body of the request.</span></span> <span data-ttu-id="e6aef-110">この例で説明されている操作では、filename パラメーターも使用できます。</span><span class="sxs-lookup"><span data-stu-id="e6aef-110">The operation described in this example also takes a filename parameter.</span></span> <span data-ttu-id="e6aef-111">このパラメーターは要求の URL に格納されて渡されます。</span><span class="sxs-lookup"><span data-stu-id="e6aef-111">This parameter is passed within the URL of the request.</span></span> <span data-ttu-id="e6aef-112"><xref:System.UriTemplate> で <xref:System.ServiceModel.Web.WebInvokeAttribute> を指定すると、パラメーターが URL に格納されて渡されるように指定できます。</span><span class="sxs-lookup"><span data-stu-id="e6aef-112">You can specify that a parameter is passed within the URL by specifying a <xref:System.UriTemplate> in the <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="e6aef-113">この場合は、URI は、呼び出しに使用では、このメソッドは、「UploadFile/一部のファイル名」で終了します。</span><span class="sxs-lookup"><span data-stu-id="e6aef-113">In this case the URI used to call this method ends in "UploadFile/Some-Filename".</span></span> <span data-ttu-id="e6aef-114">URI テンプレートの"{filename}"部分では、操作を呼び出すために使用する URI 内で操作の filename パラメーターが渡されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="e6aef-114">The "{filename}" portion of the URI template specifies that the filename parameter for the operation is passed within the URI used to call the operation.</span></span>  
  
    ```csharp  
     [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    ```  
  
2.  <span data-ttu-id="e6aef-115">サービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="e6aef-115">Implement the service contract.</span></span> <span data-ttu-id="e6aef-116">コントラクトには、ストリーム内の任意のデータのファイルを受け取る `UploadFile` というメソッドが 1 つだけあります。</span><span class="sxs-lookup"><span data-stu-id="e6aef-116">The contract has only one method, `UploadFile` that receives a file of arbitrary data in a stream.</span></span> <span data-ttu-id="e6aef-117">操作では、ストリームを読み取り、読み取ったバイト数をカウントしてから、ファイル名と読み取ったバイト数を表示します。</span><span class="sxs-lookup"><span data-stu-id="e6aef-117">The operation reads the stream counting the number of bytes read and then displays the filename and the number of bytes read.</span></span>  
  
    ```csharp  
    public class RawDataService : IReceiveData  
    {  
        public void UploadFile(string fileName, Stream fileContents)  
        {  
            byte[] buffer = new byte[10000];  
            int bytesRead, totalBytesRead = 0;  
            do  
            {  
                bytesRead = fileContents.Read(buffer, 0, buffer.Length);  
                totalBytesRead += bytesRead;  
            } while (bytesRead > 0);  
            Console.WriteLine("Service: Received file {0} with {1} bytes", fileName, totalBytesRead);  
        }  
    }  
    ```  
  
### <a name="to-host-the-service"></a><span data-ttu-id="e6aef-118">サービスをホストするには</span><span class="sxs-lookup"><span data-stu-id="e6aef-118">To host the service</span></span>  
  
1.  <span data-ttu-id="e6aef-119">コンソール アプリケーションを作成し、サービスをホストします。</span><span class="sxs-lookup"><span data-stu-id="e6aef-119">Create a console application to host the service.</span></span>  
  
    ```csharp  
    class Program  
    {  
       static void Main(string[] args)  
       {  
       }  
    }  
    ```  
  
2.  <span data-ttu-id="e6aef-120">変数を作成し、`Main` メソッド内のサービスに使用するベース アドレスを保持します。</span><span class="sxs-lookup"><span data-stu-id="e6aef-120">Create a variable to hold the base address for the service within the `Main` method.</span></span>  
  
    ```csharp  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3.  <span data-ttu-id="e6aef-121">サービスの <xref:System.ServiceModel.ServiceHost> インスタンスを作成して、サービス クラスとベース アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="e6aef-121">Create a <xref:System.ServiceModel.ServiceHost> instance for the service that specifies the service class and the base address.</span></span>  
  
    ```csharp  
    ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
    ```  
  
4.  <span data-ttu-id="e6aef-122">コントラクト、<xref:System.ServiceModel.WebHttpBinding>、および <xref:System.ServiceModel.Description.WebHttpBehavior> を指定するエンドポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="e6aef-122">Add an endpoint that specifies the contract, <xref:System.ServiceModel.WebHttpBinding>, and <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
    ```csharp  
    host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5.  <span data-ttu-id="e6aef-123">サービス ホストを開きます。</span><span class="sxs-lookup"><span data-stu-id="e6aef-123">Open the service host.</span></span> <span data-ttu-id="e6aef-124">サービスは要求を受け取る準備ができました。</span><span class="sxs-lookup"><span data-stu-id="e6aef-124">The service is now ready to receive requests.</span></span>  
  
    ```csharp  
    host.Open();  
    Console.WriteLine("Host opened");  
    ```  
  
### <a name="to-call-the-service-programmatically"></a><span data-ttu-id="e6aef-125">プログラムによってサービスを呼び出すには</span><span class="sxs-lookup"><span data-stu-id="e6aef-125">To call the service programmatically</span></span>  
  
1.  <span data-ttu-id="e6aef-126">サービスの呼び出しに使用する URI で <xref:System.Net.HttpWebRequest> を作成します。</span><span class="sxs-lookup"><span data-stu-id="e6aef-126">Create a <xref:System.Net.HttpWebRequest> with the URI used to call the service.</span></span> <span data-ttu-id="e6aef-127">このコードでは、ベース アドレスは `"/UploadFile/Text"` と組み合わされています。</span><span class="sxs-lookup"><span data-stu-id="e6aef-127">In this code, the base address is combined with `"/UploadFile/Text"`.</span></span> <span data-ttu-id="e6aef-128">URI の `"UploadFile"` 部分で呼び出す操作を指定します。</span><span class="sxs-lookup"><span data-stu-id="e6aef-128">The `"UploadFile"` portion of the URI specifies the operation to call.</span></span> <span data-ttu-id="e6aef-129">URI の `"Test.txt"` 部分で `UploadFile` 操作に渡す filename パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="e6aef-129">The `"Test.txt"` portion of the URI specifies the filename parameter to pass to the `UploadFile` operation.</span></span> <span data-ttu-id="e6aef-130">これらの項目はいずれも操作コントラクトに適用された <xref:System.UriTemplate> にマップされます。</span><span class="sxs-lookup"><span data-stu-id="e6aef-130">Both of these items map to the <xref:System.UriTemplate> applied to the operation contract.</span></span>  
  
    ```csharp  
    HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
    ```  
  
2.  <span data-ttu-id="e6aef-131"><xref:System.Net.HttpWebRequest.Method%2A> の <xref:System.Net.HttpWebRequest> プロパティを `POST`、<xref:System.Net.HttpWebRequest.ContentType%2A> プロパティを `"text/plain"` にそれぞれ設定します。</span><span class="sxs-lookup"><span data-stu-id="e6aef-131">Set the <xref:System.Net.HttpWebRequest.Method%2A> property of the <xref:System.Net.HttpWebRequest> to `POST` and the <xref:System.Net.HttpWebRequest.ContentType%2A> property to `"text/plain"`.</span></span> <span data-ttu-id="e6aef-132">この設定により、サービスはコードがデータを送信し、そのデータがプレーン テキストであることを認識します。</span><span class="sxs-lookup"><span data-stu-id="e6aef-132">This tells the service that the code is sending data and that data is in plain text.</span></span>  
  
    ```csharp  
    req.Method = "POST";  
    req.ContentType = "text/plain";  
    ```  
  
3.  <span data-ttu-id="e6aef-133"><xref:System.Net.HttpWebRequest.GetRequestStream%2A> を呼び出すと、要求ストリームの取得や送信するデータの作成ができます。また、そのデータの要求ストリームに書き込んだり、ストリームを閉じることもできます。</span><span class="sxs-lookup"><span data-stu-id="e6aef-133">Call <xref:System.Net.HttpWebRequest.GetRequestStream%2A> to get the request stream, create the data to send, write that data to the request stream, and close the stream.</span></span>  
  
    ```csharp  
    Stream reqStream = req.GetRequestStream();  
    byte[] fileToSend = new byte[12345];  
    for (int i = 0; i < fileToSend.Length; i++)  
       {  
           fileToSend[i] = (byte)('a' + (i % 26));  
       }  
    reqStream.Write(fileToSend, 0, fileToSend.Length);  
    reqStream.Close();  
    ```  
  
4.  <span data-ttu-id="e6aef-134"><xref:System.Net.HttpWebRequest.GetResponse%2A> を呼び出してサービスから応答を取得すると、応答データをコンソールに表示できます。</span><span class="sxs-lookup"><span data-stu-id="e6aef-134">Get the response from the service by calling <xref:System.Net.HttpWebRequest.GetResponse%2A> and display the response data to the console.</span></span>  
  
    ```csharp  
    HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
    Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
    ```  
  
5.  <span data-ttu-id="e6aef-135">サービス ホストを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e6aef-135">Close the service host.</span></span>  
  
    ```csharp  
    host.Close();  
    ```  
  
## <a name="example"></a><span data-ttu-id="e6aef-136">例</span><span class="sxs-lookup"><span data-stu-id="e6aef-136">Example</span></span>  
 <span data-ttu-id="e6aef-137">この例で使用されているコードの完全な一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e6aef-137">The following is a complete listing of the code for this example.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.ServiceModel;  
using System.ServiceModel.Web;  
using System.ServiceModel.Description;  
using System.IO;  
using System.Net;  
  
namespace ReceiveRawData  
{  
    [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    public class RawDataService : IReceiveData  
    {  
        public void UploadFile(string fileName, Stream fileContents)  
        {  
            byte[] buffer = new byte[10000];  
            int bytesRead, totalBytesRead = 0;  
            do  
            {  
                bytesRead = fileContents.Read(buffer, 0, buffer.Length);  
                totalBytesRead += bytesRead;  
            } while (bytesRead > 0);  
            Console.WriteLine("Service: Received file {0} with {1} bytes", fileName, totalBytesRead);  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
            ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
            host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
            host.Open();  
            Console.WriteLine("Host opened");  
  
            HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
            req.Method = "POST";  
            req.ContentType = "text/plain";  
            Stream reqStream = req.GetRequestStream();  
            byte[] fileToSend = new byte[12345];  
            for (int i = 0; i < fileToSend.Length; i++)  
            {  
                fileToSend[i] = (byte)('a' + (i % 26));  
            }  
            reqStream.Write(fileToSend, 0, fileToSend.Length);  
            reqStream.Close();  
            HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
            Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
            host.Close();  
  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e6aef-138">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="e6aef-138">Compiling the Code</span></span>  
  
-   <span data-ttu-id="e6aef-139">コードのコンパイル時には、System.ServiceModel.dll と System.ServiceModel.Web.dll を参照します。</span><span class="sxs-lookup"><span data-stu-id="e6aef-139">When compiling the code reference System.ServiceModel.dll and System.ServiceModel.Web.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6aef-140">参照</span><span class="sxs-lookup"><span data-stu-id="e6aef-140">See Also</span></span>  
 [<span data-ttu-id="e6aef-141">UriTemplate と UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="e6aef-141">UriTemplate and UriTemplateTable</span></span>](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
 [<span data-ttu-id="e6aef-142">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="e6aef-142">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="e6aef-143">WCF Web HTTP プログラミング モデルの概要</span><span class="sxs-lookup"><span data-stu-id="e6aef-143">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
