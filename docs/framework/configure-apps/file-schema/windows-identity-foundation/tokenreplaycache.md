---
title: '&lt;tokenReplayCache&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: e43e79416ddb8862cbc6e52d9d449a02b123af83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="lttokenreplaycachegt"></a>&lt;tokenReplayCache&gt;
トークン リプレイ キャッシュ サービスまたはセキュリティ トークン ハンドラー コレクションに登録します。  
  
 \<system.identityModel >  
\<identityConfiguration >  
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
