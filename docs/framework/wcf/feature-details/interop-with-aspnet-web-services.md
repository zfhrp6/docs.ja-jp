---
title: "ASP.NET Web サービスとの相互運用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# ASP.NET Web サービスとの相互運用
[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web サービスと [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web サービスの相互運用性は、この 2 つのテクノロジを使用して実装されたサービスを確実に WS\-I Basic Profile 1.1 仕様に準拠させることによって実現されます。WS\-I Basic Profile 1.1 準拠の [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web サービスは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] システムによって提供されるバインディングである <xref:System.ServiceModel.BasicHttpBinding> を使用することで [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントと相互運用できます。  
  
 次のサンプル コードに示すように、<xref:System.Web.Services.WebService> 属性と <xref:System.Web.Services.WebMethodAttribute> 属性をインターフェイス \(クラスではありません\) に追加し、そのインターフェイスを実装するクラスを作成するという、[!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)] のオプションを使用します。  
  
```  
[WebService]  
public interface IEcho  
{  
    [WebMethod]  
    string Echo(string input);  
}  
  
public class Service : IEcho  
{  
  
   public string Echo(string input)  
   {  
        return input;  
    }  
}  
```  
  
 <xref:System.Web.Services.WebService> 属性を持つインターフェイスは、同じコントラクトを異なる方法で実装する可能性のあるさまざまなクラスで再利用可能なサービスによって実行される操作のコントラクトを構成するため、このオプションを使用することをお勧めします。  
  
 <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> 属性を使用する場合、`SOAPAction` HTTP ヘッダーではなく、SOAP メッセージの本文要素の完全修飾名に基づいてメッセージをメソッドへルーティングすることは避けます。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、`SOAPAction` HTTP ヘッダーを使用してメッセージをルーティングします。  
  
 <xref:System.Xml.Serialization.XmlSerializer> によって既定で型のシリアル化が行われる XML は、XML の名前空間が明示的に定義されている場合、<xref:System.Runtime.Serialization.DataContractSerializer> によって型のシリアル化が行われる XML と意味的に同一です。将来 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を採用する予定がある場合、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web サービスで使用するデータ型を定義するには、次の操作を実行します。  
  
-   XML スキーマではなく、.NET Framework クラスを使用して型を定義します。  
  
-   <xref:System.SerializableAttribute> と <xref:System.Xml.Serialization.XmlRootAttribute> だけをそのクラスに追加します。後者を使用して型の名前空間を明示的に定義してください。.NET Framework クラスを XML に変換する方法を制御する目的で、<xref:System.Xml.Serialization> 名前空間の属性を追加しないでください。  
  
-   この手法を採用すると、後から <xref:System.Runtime.Serialization.DataContractAttribute> および <xref:System.Runtime.Serialization.DataMemberAttribute> を追加することで、転送のためにクラスをシリアル化する XML に大きな変更を加えることなく .NET クラスをデータ コントラクトにすることができます。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションは、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web サービスがメッセージ内で使用する型をデータ コントラクトとして処理できます。これは、特に [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションのパフォーマンスを向上できるという利点があります。  
  
 インターネット インフォメーション サービス \(IIS\) に用意されている認証オプションは使用しないでください。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントではこれらの認証オプションはサポートされません。サービスをセキュリティで保護する必要がある場合は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で提供されるオプションを使用します。これらのオプションの方が信頼性が高く、標準プロトコルに基づいているためです。  
  
## ServiceModel HttpModule の読み込みがパフォーマンスに及ぼす影響  
 .NET Framework Version 3.0 では、WCF `HttpModule` が、すべての ASP.NET アプリケーションが WCF 対応になるように、ルートの Web.config ファイルにインストールされます。これによりパフォーマンスに影響が出る場合があるため、次の例に示すように、Web.config ファイルの `ServiceModel` を削除することもできます。  
  
```  
<httpModules>  
    <remove name=”ServiceModel” />  
<httpModules/>  
  
```  
  
## 参照  
 [方法 : WCF サービスおよび ASP.NET Web サービス クライアントを相互運用するために構成する](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)