---
title: '&lt;bypassTrustedAppStrongNames&gt;要素'
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6988be28e3129748ee7f7996a66c728ccde3c70b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745384"
---
# <a name="ltbypasstrustedappstrongnamesgt-element"></a>&lt;bypassTrustedAppStrongNames&gt;要素
完全信頼に読み込まれる完全に信頼されたアセンブリに厳密な名前の検証をバイパスするかどうかを示す<xref:System.AppDomain>です。  
  
 \<configuration>  
\<ランタイム >  
\<bypassTrustedAppStrongNames >  
  
## <a name="syntax"></a>構文  
  
```xml  
<bypassTrustedAppStrongNames    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> 完全信頼アセンブリの厳密名の検証を回避するバイパス機能が有効になっているかどうかを指定します。 この機能を有効にすると、アセンブリが読み込まれるときに正しいかどうかの厳密な名前は検証されません。 既定値は、`true` です。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`true`|アセンブリは完全信頼に読み込まれるときに、完全信頼アセンブリの厳密な名前の署名が検証されません<xref:System.AppDomain>です。 既定値です。|  
|`false`|アセンブリは完全信頼に読み込まれるときに完全信頼アセンブリの厳密な名前の署名は検証<xref:System.AppDomain>です。 厳密な名前の署名がチェックのみ署名の正確性です。一致するものを別の厳密な名前には比較されません。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>コメント  
 厳密な名前のバイパス機能は、完全に信頼されたアセンブリの厳密名署名検証のオーバーヘッドを回避できます。  
  
 バイ パス機能は、厳密な名前で署名されていて、次の特性を持つアセンブリに適用されます。  
  
-   なく完全に信頼された、<xref:System.Security.Policy.StrongName>証拠 (たとえば、`MyComputer`ゾーン証拠)。  
  
-   完全に信頼された <xref:System.AppDomain> に読み込まれる。  
  
-   その <xref:System.AppDomain> の <xref:System.AppDomainSetup.ApplicationBase%2A> プロパティに基づいた場所から読み込まれる。  
  
-   遅延署名されていない。  
  
> [!NOTE]
>  場合のバイパス機能がオフになっているコンピューター上のすべてのアプリケーションのレジストリ キーを使用してこの構成ファイルの設定は無効です。 詳細については、次を参照してください。[する方法: 厳密な名前のバイパス機能を無効にする](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)です。  
  
## <a name="example"></a>例  
 次の例では、完全信頼アセンブリの厳密な名前の署名を検証する動作を指定する方法を示します。  
  
```xml  
<configuration>  
   <runtime>  
      <bypassTrustedAppStrongNames enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [方法: 厳密な名前のバイパス機能を無効にする](../../../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)
