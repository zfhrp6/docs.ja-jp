---
title: "方法 : WCF REST プログラミング モデルを使用して任意のデータを受け入れるサービスを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e566c15a-b600-4e4a-be3a-4af43e767dae
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 方法 : WCF REST プログラミング モデルを使用して任意のデータを受け入れるサービスを作成する
開発者は、データがサービス操作から返される流れを完全に制御する必要が生じることがあります。 たとえば、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ではサポートされない形式のデータを、サービス操作から返す必要がある場合です。 このトピックでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] REST プログラミング モデルを使用して任意のデータを受信するサービスの作成方法について説明します。  
  
### <a name="to-implement-the-service-contract"></a>サービス コントラクトを実装するには  
  
1.  サービス コントラクトを定義します。 任意のデータを受信する操作は、型のパラメーターを持つ必要があります<xref:System.IO.Stream>します。 さらに、このパラメーターは要求の本文に渡される唯一のパラメーターでなければなりません。 この例で説明されている操作では、filename パラメーターも使用できます。 このパラメーターは要求の URL に格納されて渡されます。 指定して、URL 内でパラメーターを渡すことを指定する、 <xref:System.UriTemplate>で、 <xref:System.ServiceModel.Web.WebInvokeAttribute>します。 この場合、このメソッドを呼び出すのに使用する URI は “UploadFile/Some-Filename” で終わります。 URI テンプレートの "{filename}" 部分は、操作に使用する filename パラメーターが操作の呼び出しに使用する URI に格納されて渡されるように指定します。  
  
    ```  
     [ServiceContract]  
    public interface IReceiveData  
    {  
        [WebInvoke(UriTemplate = "UploadFile/{fileName}")]  
        void UploadFile(string fileName, Stream fileContents);  
    }  
    ```  
  
2.  サービス コントラクトを実装します。 コントラクトには、ストリーム内の任意のデータのファイルを受け取る `UploadFile` というメソッドが&1; つだけあります。 操作では、ストリームを読み取り、読み取ったバイト数をカウントしてから、ファイル名と読み取ったバイト数を表示します。  
  
    ```  
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
  
### <a name="to-host-the-service"></a>サービスをホストするには  
  
1.  コンソール アプリケーションを作成し、サービスをホストします。  
  
    ```  
    class Program  
    {  
       static void Main(string[] args)  
       {  
       }  
    }  
  
    ```  
  
2.  変数を作成し、`Main` メソッド内のサービスに使用するベース アドレスを保持します。  
  
    ```  
    string baseAddress = "http://" + Environment.MachineName + ":8000/Service";  
    ```  
  
3.  作成、 <xref:System.ServiceModel.ServiceHost>サービス クラスとベース アドレスを指定するサービスのインスタンス。  
  
    ```  
    ServiceHost host = new ServiceHost(typeof(RawDataService), new Uri(baseAddress));  
    ```  
  
4.  コントラクトを指定するエンドポイントを追加<xref:System.ServiceModel.WebHttpBinding>、および<xref:System.ServiceModel.Description.WebHttpBehavior>します。  
  
    ```  
    host.AddServiceEndpoint(typeof(IReceiveData), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
    ```  
  
5.  サービス ホストを開きます。 サービスは要求を受け取る準備ができました。  
  
    ```  
    host.Open();  
    Console.WriteLine("Host opened");  
    ```  
  
### <a name="to-call-the-service-programmatically"></a>プログラムによってサービスを呼び出すには  
  
1.  作成、 <xref:System.Net.HttpWebRequest>サービスを呼び出すために使用する URI を使用します。 このコードでは、ベース アドレスは `“/UploadFile/Text”` と組み合わされています。 URI の `“UploadFile”` 部分で呼び出す操作を指定します。 URI の `“Test.txt”` 部分で `UploadFile` 操作に渡す filename パラメーターを指定します。 これらの項目の両方にマップ、 <xref:System.UriTemplate>操作コントラクトに適用します。  
  
    ```  
    HttpWebRequest req = (HttpWebRequest)HttpWebRequest.Create(baseAddress + "/UploadFile/Test.txt");  
  
    ```  
  
2.  設定、<xref:System.Net.HttpWebRequest.Method%2A>のプロパティ、 <xref:System.Net.HttpWebRequest>に`POST`と<xref:System.Net.HttpWebRequest.ContentType%2A>プロパティを`“text/plain”`します。 この設定により、サービスはコードがデータを送信し、そのデータがプレーン テキストであることを認識します。  
  
    ```  
    req.Method = "POST";  
    req.ContentType = "text/plain";  
    ```  
  
3.  呼び出す<xref:System.Net.HttpWebRequest.GetRequestStream%2A>要求ストリームを取得するには、送信、要求ストリームにそのデータを書き込みおよびストリームを閉じるにデータを作成します。  
  
    ```  
    Stream reqStream = req.GetRequestStream();  
    byte[] fileToSend = new byte[12345];  
    for (int i = 0; i < fileToSend.Length; i++)  
       {  
           fileToSend[i] = (byte)('a' + (i % 26));  
       }  
    reqStream.Write(fileToSend, 0, fileToSend.Length);  
    reqStream.Close();  
    ```  
  
4.  呼び出して、サービスから応答を取得<xref:System.Net.HttpWebRequest.GetResponse%2A>し、応答データをコンソールに表示します。  
  
    ```  
    HttpWebResponse resp = (HttpWebResponse)req.GetResponse();  
    Console.WriteLine("Client: Receive Response HTTP/{0} {1} {2}", resp.ProtocolVersion, (int)resp.StatusCode, resp.StatusDescription);  
  
    ```  
  
5.  サービス ホストを閉じます。  
  
    ```  
    host.Close();  
    ```  
  
## <a name="example"></a>例  
 この例で使用されているコードの完全な一覧を次に示します。  
  
```  
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
  
<!-- TODO: review snippet reference  [!CODE [Microsoft.Win32.RegistryKey#4](Microsoft.Win32.RegistryKey#4)]  -->  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
-   コードのコンパイル時には、System.ServiceModel.dll と System.ServiceModel.Web.dll を参照します。  
  
## <a name="see-also"></a>関連項目  
 [UriTemplate と UriTemplateTable](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)   
 [WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)   
 [WCF Web HTTP プログラミング モデルの概要](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)