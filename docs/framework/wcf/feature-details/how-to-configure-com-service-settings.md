---
title: "方法 : COM+ サービス設定を構成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM+ [WCF], configuring service settings
ms.assetid: f42a55a8-3af8-4394-9fdd-bf12a93780eb
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fa497567c5cf380d7764499991ad9e7e95a5cbe0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-com-service-settings"></a>方法 : COM+ サービス設定を構成する
COM+ サービス構成ツールを使用してアプリケーション インターフェイスを追加または削除すると、アプリケーション構成ファイル内の Web サービス構成が更新されます。 COM + ホスト モードでは、Application.config ファイルはアプリケーションのルート ディレクトリに配置されます (%PROGRAMFILES%\ComPlus アプリケーション\\%programfiles%\complus は既定値)。 いずれの Web ホスト モードでも、Web.config ファイルは指定した vroot ディレクトリに配置されます。  
  
> [!NOTE]
>  クライアントとサーバー間のメッセージの改ざんを防止するには、メッセージの署名を使用する必要があります。 また、クライアントとサーバー間のメッセージから情報が漏えいするのを防止するには、メッセージまたはトランスポート層の暗号化を使用する必要があります。 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスの場合と同様に、調整機能を使用して同時呼び出し、同時接続、同時インスタンス、同時保留操作の数を制限する必要があります。 これによりリソースの過剰消費を防ぐことができます。 調整の動作は、サービス構成ファイルの設定で指定します。  
  
## <a name="example"></a>例  
 次のインターフェイスを実装するコンポーネントについて考えます。  
  
```  
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 コンポーネントを Web サービスとして公開する場合、クライアントが準拠する必要のある対応の公開サービス コントラクトは次のとおりです。  
  
```  
[ServiceContract(Session = true,  
Namespace = "http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7",  
Name = "IFinances")]  
public interface IFinancesContract : IDisposable  
{  
    [OperationContract]  
    string Debit(string accountNo, double amount);  
    [OperationContract]  
    string Credit(string accountNo, double amount);  
}  
```  
  
> [!NOTE]
>  IID はコントラクトの初期名前空間の一部です。  
  
 このサービスを使用するクライアント アプリケーションはこのコントラクトに準拠し、さらにアプリケーションの構成に指定したバインディングと互換性のあるバインディングを使用する必要があります。  
  
 次のコード例は、既定の構成ファイルの例を示しています。 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web サービスであるため、これは標準サービス モデルの構成スキーマに準拠し、他の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの構成ファイルと同様の方法で編集できます。  
  
 通常、次のような変更を行います。  
  
-   エンドポイント アドレスを既定の ApplicationName/ComponentName/InterfaceName という形式から、より利用しやすい形式に変更する。  
  
-   サービスの名前空間を既定の "http://tempuri.org/InterfaceID" という形式から、より関連性の高い形式に変更する。  
  
-   異なるトランスポート バインディングを使用するようにエンドポイントを変更する。  
  
     COM+ ホスト モードの場合、既定では名前付きパイプ トランスポートが使用されますが、その代わりに TCP などのコンピューターに関係のないトランスポートも使用できます。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <netNamedPipeBinding>  
                <binding name="comNonTransactionalBinding" />  
                <binding name="comTransactionalBinding" transactionFlow="true" />  
            </netNamedPipeBinding>  
        </bindings>  
        <comContracts>  
            <comContract contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"  
                name="IFinances" namespace="http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7"  
                requiresSession="true">  
                <exposedMethods>  
                    <add exposedMethod="Debit" />  
                    <add exposedMethod="Credit" />  
                </exposedMethods>  
            </comContract>  
        </comContracts>  
        <services>  
            <service name="{DCDB24CC-0B19-4534-95CD-FBBFF4D67DD9},{C942B840-AD54-4A44-B5F7-928130980AB9}">  
                <endpoint address="IFinances" binding="netNamedPipeBinding" bindingConfiguration="comNonTransactionalBinding"  
                    contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" />  
                <host>  
                    <baseAddresses>  
                        <add baseAddress="net.pipe://localhost/ServiceModelDocSampleApp/ServiceModelDocSample.esFinance" />  
                    </baseAddresses>  
                </host>  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 [COM + アプリケーションとの統合](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
