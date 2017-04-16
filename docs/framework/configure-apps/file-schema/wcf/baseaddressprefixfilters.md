---
title: "&lt;baseAddressPrefixFilters&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# &lt;baseAddressPrefixFilters&gt;
パス スルー フィルターを指定する構成要素のコレクションを表します。パス スルー フィルターには、インターネット インフォメーション サービス \(IIS\) で [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] アプリケーションをホストする場合に適切な IIS バインドを選択する機構が用意されています。  
  
> [!WARNING]
>  \<baseAddressPrefixFilters\> は localhost を認識しません。代わりに、コンピューターの完全修飾名を使用します。  
  
## 構文  
  
```  
  
<serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="string"/>  
     </baseAddressPrefixFilters>  
</serviceHostingEnvironment>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 なし。  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddressprefixfilter.md)|サービス ホストによって使用されるベース アドレスのプレフィックス フィルターを指定する構成要素を追加します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<serviceHostingEnvironment\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|環境をホストするサービスがインスタンス化する特定のトランスポートの型を定義します。|  
  
## 解説  
 プレフィックス フィルターは、サービスによって使用される URI を、共有ホスティング プロバイダーが指定できるようにする手段を提供します。  これにより、共有ホストは、同じサイト上の同じスキームに対して、別々のベース アドレスを使用して複数のアプリケーションをホストできるようになります。  
  
 IIS Web サイトは、仮想ディレクトリを含む仮想アプリケーションのコンテナーです。  サイト内のアプリケーションには、1 つ以上の IIS バインディングからアクセスできます。  IIS バインディングは、バインディング プロトコルとバインディング情報という 2 つの情報を提供します。  バインディング プロトコル \(HTTP など\) は通信を行うスキームを定義し、バインディング情報 \(IP アドレス、ポート、ホスト ヘッダーなど\) にはサイトにアクセスするために使用するデータが含まれます。  
  
 IIS では、サイトごとに複数の IIS バインディングを指定できるので、各スキームに複数のベース アドレスが定義されることがあります。  これに対して、サイトでホストされる [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスでは、スキームごとに 1 つのベース アドレスにしかバインドできません。そこで、プレフィックス フィルター機能を使用すると、ホストされるサービスの必要なベース アドレスを選択できます。  IIS によって指定される受信ベース アドレスは、オプションのプレフィックス リスト フィルターに基づいてフィルター処理されます。  
  
 たとえば、サイトに次のベース アドレスが含まれているとします。  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 次の構成ファイルを使用して、appdomain レベルでプレフィックス フィルターを指定できます。  
  
```  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix=”net.tcp://test1.fabrikam.com:8000”/>  
        <add prefix=”http://test2.fabrikam.com:9000”/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 この例では、`net.tcp://test1.fabrikam.com:8000` と `http://test2.fabrikam.com:9000` が、対応するスキームに渡される唯一のベース アドレスです。  
  
 既定では、プレフィックスを指定しない場合、すべてのアドレスが渡されます。  プレフィックスだけを指定すると、そのスキームに一致するベース アドレスを渡すことができます。  
  
> [!NOTE]
>  フィルターでワイルドカードはサポートされません。  また、IIS が提供する baseAddresses には、`baseAddressPrefixFilters` リストに存在しない他のスキームにバインドされたアドレスが指定される場合があります。  これらのアドレスはフィルターで除外されません。  
  
## 参照  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>   
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>   
 <xref:System.ServiceModel.ServiceHostingEnvironment>   
 [ホスト](../../../../../docs/framework/wcf/feature-details/hosting.md)