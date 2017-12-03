---
title: "&lt;protocolMapping&gt; の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 255cd8518bd9c6c6c199c75aa32ca086c801d23f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltprotocolmappinggt"></a>&lt;protocolMapping&gt; の &lt;add&gt;
トランスポート プロトコル スキーム (など、http、net.tcp、net.pipe など) の間の既定のプロトコル マッピングを表す、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]バインドします。 実行時に既定のエンドポイントを作成するときに、[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] は構成されたマッピングを確認し、特定のベース アドレスに使用するバインディングを決定します。  
  
 \<system.serviceModel >  
\<protocolMapping >  
\<add>  
  
## <a name="syntax"></a>構文  
  
```xml
   <protocolMapping>    <add binding="String"         bindingConfiguration="String"         scheme="http/net.msmq/net.pipe/net.tcp"/></protocolMapping>
```

## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|要素|説明|  
|-------------|-----------------|  
|バインド|既定のエンドポイントを作成するときにエンドポイントに使用されるバインディングの種類を指定する文字列。|  
|bindingConfiguration|参照されるバインディング構成セクションの名前を指定する文字列。|  
|scheme|既定のエンドポイントに使用されるトランスポート プロトコル スキーム。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<protocolMapping >](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|トランスポート プロトコル スキーム (など、http、net.tcp、net.pipe など) の間で既定のプロトコル マッピングを定義する構成セクションを表しますと[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]バインドします。|  
  
## <a name="example"></a>例  
 次の構成例は、machine.config ファイル内の既定のプロトコル マッピングを示しています。 machine.config ファイルを変更することで、既定のマッピングをコンピューター レベルでオーバーライドできます。 または、アプリケーションのスコープ内だけでオーバーライドする場合は、アプリケーション構成ファイルのこのセクションをオーバーライドし、各プロトコル スキームのマッピングを変更できます。  
  
```xml  
<protocolMapping>  
        <add scheme="http" binding="basicHttpBinding"/>  
        <add scheme="net.tcp" binding="netTcpBinding"/>  
        <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
        <add scheme="net.msmq" binding="netMsmqBinding"/>  
</protocolMapping>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
