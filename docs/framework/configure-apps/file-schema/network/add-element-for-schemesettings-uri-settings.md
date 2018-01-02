---
title: "&lt;追加&gt;schemeSettings (Uri 設定) の要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 2d617e78231bd0b9f4e332c4b7fbe58b78598868
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-schemesettings-uri-settings"></a>&lt;追加&gt;schemeSettings (Uri 設定) の要素
スキーム名にスキームの設定を追加します。  
  
 \<configuration>  
\<uri >  
\<schemeSettings >  
\<add>  
  
## <a name="syntax"></a>構文  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|name|スキーム名は、この設定が適用されます。 だけでサポートされる値は名前 ="http"、name ="https"。|  
  
## <a name="attribute-name-attribute"></a>{属性名}属性  
  
|値|説明|  
|-----------|-----------------|  
|genericUriParserOptions|このスキーム パーサー オプション。 のみサポートされている値が genericUriParserOptions ="DontUnescapePathDotsAndSlashes"です。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<schemeSettings> 要素 (Uri 設定)](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<xref:System.Uri> が特定のスキームに解析される方法を指定します。|  
  
## <a name="remarks"></a>コメント  
 既定では、<xref:System.Uri?displayProperty=nameWithType>クラス エスケープを解除 % は、パスの圧縮を実行する前にパスの区切り記号をエンコードします。 これは、次のような攻撃に対するセキュリティ機構として実装されていました。  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 この URI が渡される場合は、モジュール % は処理されません。 エンコードした文字を正しく、サーバーにより実行されている次のコマンドを可能性があります。  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 このため、<xref:System.Uri?displayProperty=nameWithType>クラスの最初のエスケープを解除パス区切り記号とパスの圧縮を適用します。 上への悪意のある URL を渡した結果<xref:System.Uri?displayProperty=nameWithType>クラスのコンス トラクターの結果で、次の URI:  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 いないエスケープ解除パーセント エンコードされたパスの区切り記号 schemeSettings 構成オプションを使用して、特定のスキームには、この既定の動作を変更できます。  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
 次の例で使用する構成を示しています、 <xref:System.Uri> http スキームのパーセントでエンコードされたパスの区切り記号をエスケープしないをサポートするクラス。  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
