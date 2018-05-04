---
title: '&lt;idn&gt;要素 (Uri 設定)'
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 17f68fbb92797928be911e530232e8638793687f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltidngt-element-uri-settings"></a>&lt;idn&gt;要素 (Uri 設定)
国際化ドメイン名 (IDN) の解析中に適用されます、ドメイン名を指定します。  
  
## <a name="schema-hierarchy"></a>スキーマの階層  
 [\<configuration> 要素](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<Uri > 要素 (Uri 設定)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<idn >](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
## <a name="syntax"></a>構文  
  
```xml  
<idn  
  enabled="All|AllExceptIntranet|None"  
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|`enabled`|ドメイン名では、国際化ドメイン名 (IDN) の解析が適用されている場合、既定値は none を指定します。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[Uri](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|.NET Framework での web アドレスの uniform resource identifier (Uri) を使用して表現の処理方法を指定する設定が含まれています。|  
  
## <a name="remarks"></a>コメント  
 既存の<xref:System.Uri>クラスが .NET Framework 3.5 で拡張されています。 3.0 SP1、および 2.0 SP1 国際リソース識別子 (IRI) および国際化ドメイン名 (IDN) をサポートします。 ユーザーは、IDN を明確にする場合を除きは、現在のユーザーには、.NET Framework 2.0 の動作から変更は表示されませんをサポートします。 これにより、.NET Framework の以前のバージョンとのアプリケーションの互換性を保証します。  
  
 IRI のサポートを有効にするのには、次の 2 つの変更が必要です。  
  
1.  .NET Framework 2.0 ディレクトリ下にある machine.config ファイルに次の行を追加します。  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  国際化ドメイン名 (IDN) の解析中、ドメイン名に適用するかどうかと IRI 解析規則を適用するかどうかを指定します。 これは、machine.config ファイルまたは app.config ファイルで指定できます。  
  
 使用される DNS サーバーによって、IDN 可能な値は次の 3 つです。  
  
-   有効な idn = All  
  
     この値は、Unicode ドメイン名を Punycode 同等の (IDN 名) に変換されます。  
  
-   有効な idn AllExceptIntranet を =  
  
     この値は、すべての Unicode ドメイン名 (IDN 名) と同等の Punycode を使用するローカルのイントラネットではなくに変換されます。 ここでは、ローカルのイントラネット上の国際化名の処理、イントラネットで使用される DNS サーバーは、Unicode 名前解決をサポートする必要があります。  
  
-   有効な idn = なし  
  
     この値は、Unicode のドメイン名を Punycode を使用するには変換されません。 これは、.NET Framework 2.0 の動作と整合する既定値です。  
  
 IDN を有効にすると、ドメイン名に含まれるすべての Unicode のラベルが Punycode のラベルに変換されます。 Punycode 名には ASCII 文字のみが含まれ、常に xn-- プレフィックスで始まります。 この理由は、ほとんどの DNS サーバーは ASCII 文字しかサポートしていないため、インターネットで既存の DNS サーバーをサポートするためです (RFC 3940 を参照)。  
  
### <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例で使用する構成を示しています、 <xref:System.Uri> IRI 解析と IDN 名をサポートするクラス。  
  
### <a name="code"></a>コード  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Configuration.IdnElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
