---
title: "&lt;Uri&gt;要素 (Uri 設定)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 735a6596b22e6d6fdcff776dd79224230db5b7b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="lturigt-element-uri-settings"></a>&lt;Uri&gt;要素 (Uri 設定)
.NET Framework での web アドレスの uniform resource identifier (Uri) を使用して表現の処理方法を指定する設定が含まれています。  
  
## <a name="schema-hierarchy"></a>スキーマの階層  
 [\<configuration> 要素](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<uri >](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
## <a name="syntax"></a>構文  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[idn](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|国際化ドメイン名 (IDN) の解析がドメイン名に適用されるかどうかを指定します。|  
|[iriParsing](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|International Resource Identifier (IRI) 解析に適用されますを指定します<xref:System.Uri>IRI 解析規則を適用するかどうかとします。|  
|[schemeSettings](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<xref:System.Uri> が特定のスキームに解析される方法を指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[構成](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|すべての名前空間の設定が含まれています。|  
  
## <a name="remarks"></a>コメント  
 `uri`要素にはメンバーの設定が含まれています、<xref:System.Uri>内のクラスによって使用されるクラス、<xref:System.Net>名前空間。 設定は、IRI と IDN のサポートを構成します。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例で使用する構成を示しています、 <xref:System.Uri> IRI 解析と IDN 名をサポートするクラス。 この例もすべての設定の設定をクリアし、http スキームのパーセントでエンコードされたパスの区切り記号をエスケープしないサポートが追加されます。  
  
### <a name="code"></a>コード  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>参照  
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
