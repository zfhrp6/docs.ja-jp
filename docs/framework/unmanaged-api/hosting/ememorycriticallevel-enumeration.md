---
title: EMemoryCriticalLevel 列挙型
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acf4f3f582e417c5e7b814622986427f996796ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432529"
---
# <a name="ememorycriticallevel-enumeration"></a>EMemoryCriticalLevel 列挙型
特定のメモリ割り当てが要求されましたが満足することはできません、エラーの影響を示す値が含まれています。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`eAppDomainCritical`|割り当てが、割り当てが要求したドメイン内のマネージ コードを実行するために重要なことを示します。 メモリを割り当てることができない場合、CLR はドメインが引き続き使用できることを保証できません。 ホストは、満たすことができない、割り当て時に実行するアクションを決定します。 中止する CLR に指示することができますが、`AppDomain`自動的に、メソッドを呼び出すことによっても引き続き実行することを許可または[ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)です。|  
|`eProcessCritical`|割り当てが、プロセスのマネージ コードの実行に不可欠であることを示します。 この値は使用の起動中に、ファイナライザーを実行するときにします。 メモリを割り当てることができない場合、CLR は、プロセスで動作できません。 割り当てに失敗した場合、CLR は無効になります。 CLR のすべての後続の呼び出しは、HOST_E_CLRNOTAVAILABLE で失敗します。|  
|`eTaskCritical`|割り当てが、割り当てが要求したタスクの実行に不可欠であることを示します。 メモリを割り当てることができない場合、CLR がタスクを実行できることを保証することはできません。 CLR を発生させる障害が発生した場合、<xref:System.Threading.ThreadAbortException>物理的な運用システムのスレッドでします。|  
  
## <a name="remarks"></a>コメント  
 定義されているメモリの割り当て方法、 [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)と[IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)インターフェイスは、この型のパラメーターを受け取ります。 エラーの重大度に応じて、ホスト決定できますは割り当て要求はすぐに失敗するか、満たすことができるまで待機するか。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICLRMemoryNotificationCallback インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 [ホスティングの列挙型](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
