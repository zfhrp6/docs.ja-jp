---
title: '&lt;generatePublisherEvidence&gt;要素'
ms.date: 03/30/2017
helpviewer_keywords:
- generatePublisherEvidence element
- <generatePublisherEvidence> element
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f56bbef6ed6decf6be4246f649665db4cf0f766
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746021"
---
# <a name="ltgeneratepublisherevidencegt-element"></a>&lt;generatePublisherEvidence&gt;要素
ランタイムを作成するかどうかを示す<xref:System.Security.Policy.Publisher>コード アクセス セキュリティ (CAS) の証拠。  
  
 \<configuration>  
\<ランタイム >  
\<generatePublisherEvidence >  
  
## <a name="syntax"></a>構文  
  
```xml  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> ランタイムを作成するかどうかを示す<xref:System.Security.Policy.Publisher>証拠。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|作成されません<xref:System.Security.Policy.Publisher>証拠。|  
|`true`|作成<xref:System.Security.Policy.Publisher>証拠。 既定値です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]後で、この要素にはアセンブリの読み込み時間に影響はありません。 詳細についてを参照してください「セキュリティ ポリシーの簡略化」[セキュリティの変更点](../../../../../docs/framework/security/security-changes.md)です。  
  
 共通言語ランタイム (CLR) を作成する読み込み時に、Authenticode 署名を検証しようとしました。 <xref:System.Security.Policy.Publisher> 、アセンブリの証拠。 ただし、既定では、ほとんどのアプリケーションは必要ありません<xref:System.Security.Policy.Publisher>証拠。 標準の CAS ポリシーに頼りません、<xref:System.Security.Policy.PublisherMembershipCondition>です。 アプリケーションがカスタムの CAS ポリシーを使用しているコンピューター上で実行またはの需要を満たすために意図しない限り、発行元の署名の検証に関連付けられている不要なスタートアップ コストを回避する必要があります<xref:System.Security.Permissions.PublisherIdentityPermission>部分的に信頼された環境でします。 (Id アクセス許可の要求は常には、完全に信頼された環境で失敗した)。  
  
> [!NOTE]
>  サービスが使用することをお勧め、`<generatePublisherEvidence>`起動時のパフォーマンスを向上させるために要素。  この要素を使用しても、タイムアウトと、サービスのスタートアップのキャンセルを引き起こす可能性がある遅延を避けるためとことができます。  
  
## <a name="configuration-file"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルでのみ使用できます。  
  
## <a name="example"></a>例  
 次の例を使用する方法を示しています、`<generatePublisherEvidence>`要素をアプリケーションで CA 発行者ポリシーのチェックを無効にします。  
  
```xml  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
