---
title: '&lt;tokenReplayCache&gt;'
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 79022319944c4042c6f62a7521784b826b90d4ce
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="lttokenreplaycachegt"></a>&lt;tokenReplayCache&gt;
トークン リプレイ キャッシュ サービスまたはセキュリティ トークン ハンドラー コレクションに登録します。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<キャッシュ >  
\<tokenReplayCache >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|型|派生する型、<xref:System.IdentityModel.Tokens.TokenReplayCache>クラスです。 詳細については、ユーザー設定を指定する方法についての`type`、[カスタム型の参照] を参照してください。
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<キャッシュ >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|サービスまたはセキュリティ トークン ハンドラーのコレクションによって使用されるキャッシュに登録します。|  
  
## <a name="remarks"></a>コメント  
 トークン リプレイ キャッシュを使用して、再生されたトークンを検出できます。 トークン リプレイ検出が有効になって、 [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)もトークンの最大有効期限を指定する要素。  
  
## <a name="example"></a>例  
 次の XML では、再生されたトークンを検出するためのカスタム キャッシュの構成を示します。  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IdentityModel.Tokens.TokenReplayCache>  
 [\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
