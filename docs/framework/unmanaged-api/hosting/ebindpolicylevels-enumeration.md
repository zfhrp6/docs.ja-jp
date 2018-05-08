---
title: EBindPolicyLevels 列挙型
ms.date: 03/30/2017
api_name:
- EBindPolicyLevels
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EBindPolicyLevels
helpviewer_keywords:
- EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1da1d368725ab0a2334080c1caa7d4e25f5f3bab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ebindpolicylevels-enumeration"></a>EBindPolicyLevels 列挙型
適用またはアセンブリのポリシーを変更するレベルを指定するフラグを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
    ePolicyLevelNone         = 0x0,  
    ePolicyLevelRetargetable = 0x1,  
    ePolicyUnifiedToCLR      = 0x2,  
    ePolicyLevelApp          = 0x4,  
    ePolicyLevelPublisher    = 0x8,  
    ePolicyLevelHost         = 0x10,  
    ePolicyLevelAdmin        = 0x20  
    ePolicyPortability       = 0x40  
} EBindPolicyLevels;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|ポリシーが、管理者レベルで適用することを指定します。|  
|`ePolicyLevelApp`|ポリシーが、アプリケーション レベルで適用することを指定します。|  
|`ePolicyLevelHost`|ポリシーが、ホスト レベルで適用することを指定します。|  
|`ePolicyLevelNone`|ポリシー レベルのフラグを指定しません。|  
|`ePolicyLevelPublisher`|パブリッシャー レベルでポリシーを適用する必要がありますを指定します。|  
|`ePolicyLevelRetargetable`|ポリシーをさまざまなレベルで適用できる必要がありますを指定します。|  
|`ePolicyPortability`|ポリシーが、.NET Framework アセンブリの実装間で移植性をサポートするように指定します。 参照してください、 [ \<supportPortability >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)構成ファイルの要素。|  
|`ePolicyUnifiedToCLR`|共通言語ランタイム (CLR) のポリシーを統合する必要がありますを指定します。|  
  
## <a name="remarks"></a>コメント  
 この列挙体は、のメソッドに渡される、 [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)アプリケーション ポリシーの変更を指定するインターフェイスです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRAssemblyIdentityManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [ホスティングの列挙型](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
