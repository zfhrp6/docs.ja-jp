---
title: "方法 : クライアントのメッセージを検査または変更する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 方法 : クライアントのメッセージを検査または変更する
<xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=fullName> を実装し、それをクライアントのランタイムに追加することで、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントの送受信メッセージを検査または変更できます。  詳細については、「[クライアントの拡張](../../../../docs/framework/wcf/extending/extending-clients.md)」を参照してください。  サービスの同等の機能は、<xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=fullName> です。  コード例全体については、「[メッセージ インスペクター](../../../../docs/framework/wcf/samples/message-inspectors.md)」のサンプルを参照してください。  
  
### メッセージを検査または変更するには  
  
1.  <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=fullName> インターフェイスを実装します。  
  
2.  クライアント メッセージ インスペクターを挿入するスコープに応じて、<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=fullName> または <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=fullName> を実装します。  <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=fullName> を使用すると、エンドポイント レベルで動作を変更できます。  <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=fullName> を使用すると、コントラクト レベルで動作を変更できます。  
  
3.  <xref:System.ServiceModel.ChannelFactory%601?displayProperty=fullName> で <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=fullName> メソッドまたは <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=fullName> メソッドを呼び出す前に、動作を追加します。  詳細については、「[動作を使用したランタイムの構成と拡張](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)」を参照してください。  
  
## 使用例  
 下のコード例では、次の項目を順番に示しています。  
  
-   クライアント インスペクター実装  
  
-   インスペクターを挿入するエンドポイント動作  
  
-   構成ファイルで動作を追加できるようにする <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> 派生クラス。  
  
-   クライアント メッセージ インスペクターをクライアント ランタイムに挿入するエンドポイント動作を追加する構成ファイル。  
  
```csharp  
// Client message inspector  
public class SimpleMessageInspector : IClientMessageInspector  
{  
    public void AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
    {  
        // Implement this method to inspect/modify messages after a message  
        // is received but prior to passing it back to the client   
        Console.WriteLine("AfterReceiveReply called");  
    }  
  
    public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, IClientChannel channel)  
    {  
        // Implement this method to inspect/modify messages before they   
        // are sent to the service  
        Console.WriteLine("BeforeSendRequest called");  
        return null;  
    }  
}  
  
```  
  
```csharp  
// Endpoint behavior  
public class SimpleEndpointBehavior : IEndpointBehavior  
{  
    public void AddBindingParameters(ServiceEndpoint endpoint, System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
    {  
         // No implementation necessary  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint, ClientRuntime clientRuntime)  
    {  
        clientRuntime.MessageInspectors.Add(new SimpleMessageInspector());  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint, EndpointDispatcher endpointDispatcher)  
    {  
         // No implementation necessary  
    }  
  
    public void Validate(ServiceEndpoint endpoint)  
    {  
         // No implementation necessary  
    }  
}  
```  
  
```csharp  
// Configuration element   
public class SimpleBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public override Type BehaviorType  
    {  
        get { return typeof(SimpleEndpointBehavior); }  
    }  
  
    protected override object CreateBehavior()  
    {  
         // Create the  endpoint behavior that will insert the message  
         // inspector into the client runtime  
        return new SimpleEndpointBehavior();  
    }  
}  
  
```  
  
```vb  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <system.serviceModel>  
        <client>  
            <endpoint address="http://localhost:8080/SimpleService/"   
                      binding="wsHttpBinding"  
                      contract="ServiceReference1.IService1"  
                      name="WSHttpBinding_IService1"/>  
        </client>  
  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="clientInspectorsAdded">  
            <simpleBehaviorExtension />  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <extensions>  
        <behaviorExtensions>  
          <add  
            name="simpleBehaviorExtension"  
            type="SimpleServiceLib.SimpleBehaviorExtensionElement, Host, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
        </behaviorExtensions>  
      </extensions>  
    </system.serviceModel>  
</configuration>  
  
```  
  
## 参照  
 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=fullName>   
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=fullName>   
 [動作を使用したランタイムの構成と拡張](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)