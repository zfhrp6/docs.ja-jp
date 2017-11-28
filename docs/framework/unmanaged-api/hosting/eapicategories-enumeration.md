---
title: "EApiCategories 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EApiCategories
api_location: mscoree.dll
api_type: COM
f1_keywords: EApiCategories
helpviewer_keywords: EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: eaff0133020fe84e58f8a130bffc8ddc2a55a19d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="eapicategories-enumeration"></a>EApiCategories 列挙型
部分的に信頼されたコードでの実行をブロックするホスト機能のカテゴリについて説明します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
    eNoCategory               = 0,  
    eSynchronization          = 0x1,  
    eSharedState              = 0x2,  
    eExternalProcessMgmt      = 0x4,  
    eSelfAffectingProcessMgmt = 0x8,  
    eExternalThreading        = 0x10,  
    eSelfAffectingThreading   = 0x20,  
    eSecurityInfrastructure   = 0x40,  
    eUI                       = 0x80,  
    eMayLeakOnAbort           = 0x100,  
    eAll                      = 0x1ff  
} EHostProtectionCategories;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`eAll`|指定するすべてのマネージ クラスとその他の対象となるメンバー`EApiCategories`フィールドは、部分的に信頼されたコードでの実行をブロックします。|  
|`eExternalProcessMgmt`|マネージ クラスとメンバーを作成、操作、および外部プロセスの破棄を部分的に信頼されるコードで実行をブロックすることを指定します。|  
|`eExternalThreading`|マネージ クラスとメンバーを作成、操作、および外部スレッドの破棄を部分的に信頼されるコードで実行をブロックすることを指定します。|  
|`eMayLeakOnAbort`|部分的に信頼されたコードでの実行中止にメモリをリーク可能性がある可能性があるマネージ型とメンバーがブロックされることを指定します。|  
|`eNoCategory`|部分信頼コードでの実行をブロックするマネージ コードのカテゴリがないを指定します。|  
|`eSecurityInfrastructure`|共通言語ランタイム (CLR) のセキュリティ インフラストラクチャが部分的に信頼されたコードによって使用されるからブロックされることを指定します。|  
|`eSelfAffectingProcessMgmt`|部分的に信頼されたコードでの実行、マネージ クラスとメンバーが影響を与える機能ホストされたプロセスがブロックされることを指定します。|  
|`eSelfAffectingThreading`|部分的に信頼されたコードでの実行、マネージ クラスとメンバーが影響を与える機能ホスト プロセス内のスレッドがブロックされることを指定します。|  
|`eSharedState`|部分的に信頼されたコードでの実行、マネージ クラスと共有の状態を公開するメンバーがブロックされることを指定します。|  
|`eSynchronization`|共通言語ランタイム クラスとロックを保持するためにユーザー コードを許可するメンバーを部分的に信頼されるコードで実行をブロックすることを指定します。|  
|`eUI`|部分的に信頼されたコードでの実行、マネージ クラスとを許可または対話操作を必要とするメンバーがブロックされることを指定します。|  
  
## <a name="remarks"></a>コメント  
 [Iclrhostprotectionmanager::setprotectedcategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)メソッドが型のパラメーターを受け取る`EApiCategories`です。  
  
 `EApiCategories`列挙と`SetProtectedCategories`メソッドは直接関連するマネージ<xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType>クラスです。 マネージ クラスが使用されて、<xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType>列挙型、値が対応に直接、`EApiCategories`によって記述されたカテゴリに対応する機能を公開するマネージ型とメンバーをマークする、値`EApiCategories`です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRHostProtectionManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [ホスティングの列挙体](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
