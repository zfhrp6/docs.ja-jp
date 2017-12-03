---
title: "&lt;baseAddressPrefixFilter&gt; の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bd0a0d7fc5a83c78a56df796714e70e2e2a61767
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltbaseaddressprefixfiltergt"></a>&lt;baseAddressPrefixFilter&gt; の &lt;add&gt;
パススルー フィルターを指定する構成要素を表します。パススルー フィルターには、インターネット インフォメーション サービス (IIS) で [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] アプリケーションをホストする場合に適切な IIS バインドを選択する機構が用意されています。  
  
 \<システムです。ServiceModel >  
\<ServiceHostingEnvironment >  
\<baseAddressPrefixFilters >  
\<add>  
  
## <a name="syntax"></a>構文  
  
```xml  
<serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="string"/>  
     </baseAddressPrefixFilters>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|prefix|ベース アドレスの一部の一致に使用される URI。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters >](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|パススルー フィルターを指定する構成要素のコレクション。パススルー フィルターには、IIS で [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] アプリケーションをホストする場合に適切な IIS バインドを選択する機構が用意されています。|  
  
## <a name="remarks"></a>コメント  
 プレフィックス フィルターは、サービスによって使用される URI を、共有ホスティング プロバイダーが指定できるようにする手段を提供します。 これにより、共有ホストは、同じサイト上の同じスキームに対して、別々のベース アドレスを使用して複数のアプリケーションをホストできるようになります。  
  
 IIS Web サイトは、仮想ディレクトリを含む仮想アプリケーションのコンテナーです。 サイト内のアプリケーションに、1 つ以上の IIS バインディングからアクセスできます。 IIS バインディングは、バインディング プロトコルとバインディング情報という 2 つの情報を提供します。 バインディング プロトコル (HTTP など) は通信を行うスキームを定義し、バインディング情報 (IP アドレス、ポート、ホスト ヘッダーなど) にはサイトにアクセスするために使用するデータが含まれます。  
  
 IIS では、サイトごとに複数の IIS バインディングを指定できるので、各スキームに複数のベース アドレスが定義されることがあります。 これに対して、サイトでホストされる [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] サービスでは、スキームごとに 1 つのベース アドレスにしかバインドできません。そこで、プレフィックス フィルター機能を使用すると、ホストされるサービスの必要なベース アドレスを選択できます。 IIS によって指定される受信ベース アドレスは、オプションのプレフィックス リスト フィルターに基づいてフィルター処理されます。  
  
 たとえば、サイトに次のベース アドレスが含まれているとします。  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 次の構成ファイルを使用して、appdomain レベルでプレフィックス フィルターを指定できます。  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="net.tcp://test1.fabrikam.com:8000"/>  
        <add prefix="http://test2.fabrikam.com:9000"/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 この例では、`net.tcp://test1.fabrikam.com:8000` と `http://test2.fabrikam.com:9000` はそれぞれのスキームにおいて、そのまま渡すことができる唯一のベース アドレスです。  
  
 既定では、プレフィックスを指定しない場合、すべてのアドレスが渡されます。 プレフィックスだけを指定すると、そのスキームに一致するベース アドレスを渡すことができます。  
  
> [!NOTE]
>  フィルターでワイルドカードはサポートされません。 また、IIS が提供する baseAddresses には、`baseAddressPrefixFilters` リストに存在しない他のスキームにバインドされたアドレスが指定される場合があります。 これらのアドレスはフィルターで除外されません。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [ホスティング](../../../../../docs/framework/wcf/feature-details/hosting.md)
