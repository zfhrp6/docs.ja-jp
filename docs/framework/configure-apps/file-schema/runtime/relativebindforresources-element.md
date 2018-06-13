---
title: '&lt;relativeBindForResources&gt;要素'
ms.date: 03/30/2017
helpviewer_keywords:
- RelativeBindForResources element
- <relativeBindForResources> element
ms.assetid: 846ffa47-7257-4ce3-8cac-7ff627e0e34f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ae5d1ca6403d84c9828dcf9550e9fbf40b28e1b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752300"
---
# <a name="ltrelativebindforresourcesgt-element"></a>&lt;relativeBindForResources&gt;要素
サテライト アセンブリのプローブを最適化します。  
  
 \<configuration > 要素  
\<ランタイム > 要素  
\<relativeBindForResources > 要素  
  
## <a name="syntax"></a>構文  
  
```xml
<relativeBindForResources    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> 共通言語ランタイムが、サテライト アセンブリのプローブを最適化するかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|ランタイムでは、サテライト アセンブリのプローブは最適化されません。 これが既定値です。|  
|`true`|ランタイムは、サテライト アセンブリのプローブを最適化します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## <a name="remarks"></a>コメント  
 一般に、リソース マネージャー プローブのリソースについては、『 の説明に従って、[パッケージと展開のリソース](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)トピックです。 つまり、リソース マネージャーは、特定のローカライズされたバージョンのリソースにプローブ、ときにその可能性があります、グローバル アセンブリ キャッシュ ファイルの場所、サテライト アセンブリのファイルの場所はアプリケーションのコード ベース、クエリ Windows インストーラーにカルチャ固有のフォルダーおよびを発生させる、<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>イベント。 `<relativeBindForResources>`要素は、リソース マネージャーがサテライト アセンブリをプローブする方法を最適化します。 これにより、次の条件下でリソースの調査時にパフォーマンスが向上することができます。  
  
-   サテライト アセンブリを展開する際、コードのアセンブリと同じ場所にします。 つまり、コードのアセンブリがグローバル アセンブリ キャッシュにインストールされている場合、サテライト アセンブリもインストールする必要があります。 コードのアセンブリがアプリケーションのコード ベースでインストールされている場合、サテライト アセンブリは、コード ベースのカルチャに固有のフォルダーにもインストールする必要があります。  
  
-   Windows インストーラーが実行されていないまたはほとんど使用されないがサテライト アセンブリのオンデマンドでインストールします。  
  
-   アプリケーション コードが処理しない場合、<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>イベント。  
  
 設定、`enabled`の属性、`<relativeBindForResources>`要素を`true`サテライト アセンブリのリソース マネージャーのプローブを次のように最適化されます。  
  
-   サテライト アセンブリを探すために、コードの親アセンブリの場所を使用します。  
  
-   サテライト アセンブリの Windows インストーラーをクエリにはできません。  
  
-   発生しない、<xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>イベント。  
  
## <a name="see-also"></a>関連項目  
 [リソースのパッケージ化と配置](../../../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
