---
title: "WCF サービスからの REST スタイル サービスの呼び出し | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 77df81d8-7f53-4daf-8d2d-bf7996e94d5a
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# WCF サービスからの REST スタイル サービスの呼び出し
標準の \(SOAP ベース\) WCF サービスから REST スタイルのサービスを呼び出すとき、受信要求に関する情報を含んでいるサービス メソッドの操作コンテキストは、送信要求が使用するコンテキストをオーバーライドします。  これにより、HTTP GET 要求は HTTP POST 要求に変更されます。  WCF サービスが正しいコンテキストを使用して REST スタイルのサービスを呼び出すには、新しい <xref:System.ServiceModel.OperationContextScope> を作成し、操作コンテキスト スコープ内から REST スタイルのサービスを呼び出します。  このトピックでは、この手法を説明する簡単なサンプルを作成する方法について説明します。  
  
## REST スタイルのサービス コントラクトを定義する  
 簡単な REST スタイルのサービス コントラクトを定義する:  
  
```  
[ServiceContract]  
        public interface IRestInterface  
        {  
            [OperationContract, WebGet]  
            int Add(int x, int y);  
            [OperationContract, WebGet]  
            string Echo(string input);  
        }  
```  
  
## REST スタイルのサービス コントラクトを実装する  
 REST スタイルのサービス コントラクトを実装する:  
  
```  
public class RestService : IRestInterface  
        {  
            public int Add(int x, int y)  
            {  
                return x + y;  
            }  
  
            public string Echo(string input)  
            {  
                return input;  
            }  
        }  
  
```  
  
## WCF サービス コントラクトを定義する  
 REST スタイルのサービスの呼び出しに使用する WCF サービス コントラクトを定義する:  
  
```  
[ServiceContract]  
 public interface INormalInterface  
 {  
     [OperationContract]  
     int CallAdd(int x, int y);  
     [OperationContract]  
     string CallEcho(string input);  
 }  
```  
  
## WCF サービス コントラクトを実装する  
 WCF サービス コントラクトを実装する:  
  
```  
public class NormalService : INormalInterface  
        {  
            static MyRestClient client = new MyRestClient(RestServiceBaseAddress);  
            public int CallAdd(int x, int y)  
            {  
                return client.Add(x, y);  
            }  
  
            public string CallEcho(string input)  
            {  
                return client.Echo(input);  
            }  
        }  
```  
  
## REST スタイルのサービスのクライアント プロキシを作成する  
 <xref:System.ServiceModel.ClientBase%60> を使用してクライアント プロキシを実装します。  呼び出される各メソッドで、新しい <xref:System.ServiceModel.OperationContextScope> が作成され、操作の呼び出しに使用されます。  
  
```  
public class MyRestClient : ClientBase<IRestInterface>, IRestInterface  
        {  
            public MyRestClient(string address)  
                : base(new WebHttpBinding(), new EndpointAddress(address))  
            {  
                this.Endpoint.Behaviors.Add(new WebHttpBehavior());  
            }  
  
            public int Add(int x, int y)  
            {  
                using (new OperationContextScope(this.InnerChannel))  
                {  
                    return base.Channel.Add(x, y);  
                }  
            }  
  
            public string Echo(string input)  
            {  
                using (new OperationContextScope(this.InnerChannel))  
                {  
                    return base.Channel.Echo(input);  
                }  
            }  
        }  
```  
  
## サービスをホストし、呼び出す  
 コンソール アプリケーションの両方のサービスをホストし、必要なエンドポイントと動作を追加します。  次に、通常の WCF サービスを呼び出します。  
  
```  
public static void Main()  
        {  
            ServiceHost restHost = new ServiceHost(typeof(RestService), new Uri(RestServiceBaseAddress));  
            restHost.AddServiceEndpoint(typeof(IRestInterface), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
            restHost.Open();  
  
            ServiceHost normalHost = new ServiceHost(typeof(NormalService), new Uri(NormalServiceBaseAddress));  
            normalHost.AddServiceEndpoint(typeof(INormalInterface), new BasicHttpBinding(), "");  
            normalHost.Open();  
  
            Console.WriteLine("Hosts opened");  
  
            ChannelFactory<INormalInterface> factory = new ChannelFactory<INormalInterface>(new BasicHttpBinding(), new EndpointAddress(NormalServiceBaseAddress));  
            INormalInterface proxy = factory.CreateChannel();  
  
            Console.WriteLine(proxy.CallAdd(123, 456));  
            Console.WriteLine(proxy.CallEcho("Hello world"));  
        }  
```  
  
## 完全なコード リスト  
 このトピックで実装されるサンプルの完全なコード リストを次に示します。  
  
```  
public class CallingRESTSample  
    {  
        static readonly string RestServiceBaseAddress = "http://" + Environment.MachineName + ":8008/Service";  
        static readonly string NormalServiceBaseAddress = "http://" + Environment.MachineName + ":8000/Service";  
  
        [ServiceContract]  
        public interface IRestInterface  
        {  
            [OperationContract, WebGet]  
            int Add(int x, int y);  
            [OperationContract, WebGet]  
            string Echo(string input);  
        }  
  
        [ServiceContract]  
        public interface INormalInterface  
        {  
            [OperationContract]  
            int CallAdd(int x, int y);  
            [OperationContract]  
            string CallEcho(string input);  
        }  
  
        public class RestService : IRestInterface  
        {  
            public int Add(int x, int y)  
            {  
                return x + y;  
            }  
  
            public string Echo(string input)  
            {  
                return input;  
            }  
        }  
  
        public class MyRestClient : ClientBase<IRestInterface>, IRestInterface  
        {  
            public MyRestClient(string address)  
                : base(new WebHttpBinding(), new EndpointAddress(address))  
            {  
                this.Endpoint.Behaviors.Add(new WebHttpBehavior());  
            }  
  
            public int Add(int x, int y)  
            {  
                using (new OperationContextScope(this.InnerChannel))  
                {  
                    return base.Channel.Add(x, y);  
                }  
            }  
  
            public string Echo(string input)  
            {  
                using (new OperationContextScope(this.InnerChannel))  
                {  
                    return base.Channel.Echo(input);  
                }  
            }  
        }  
  
        public class NormalService : INormalInterface  
        {  
            static MyRestClient client = new MyRestClient(RestServiceBaseAddress);  
            public int CallAdd(int x, int y)  
            {  
                return client.Add(x, y);  
            }  
  
            public string CallEcho(string input)  
            {  
                return client.Echo(input);  
            }  
        }  
        public static void Main()  
        {  
            ServiceHost restHost = new ServiceHost(typeof(RestService), new Uri(RestServiceBaseAddress));  
            restHost.AddServiceEndpoint(typeof(IRestInterface), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());  
            restHost.Open();  
  
            ServiceHost normalHost = new ServiceHost(typeof(NormalService), new Uri(NormalServiceBaseAddress));  
            normalHost.AddServiceEndpoint(typeof(INormalInterface), new BasicHttpBinding(), "");  
            normalHost.Open();  
  
            Console.WriteLine("Hosts opened");  
  
            ChannelFactory<INormalInterface> factory = new ChannelFactory<INormalInterface>(new BasicHttpBinding(), new EndpointAddress(NormalServiceBaseAddress));  
            INormalInterface proxy = factory.CreateChannel();  
  
            Console.WriteLine(proxy.CallAdd(123, 456));  
            Console.WriteLine(proxy.CallEcho("Hello world"));  
        }  
    }  
```  
  
## 参照  
 [方法 : 基本的な WCF Web HTTP サービスを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)   
 [WCF Web HTTP プログラミング オブジェクト モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)