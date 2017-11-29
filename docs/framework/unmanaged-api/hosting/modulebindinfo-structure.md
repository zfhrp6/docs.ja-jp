---
title: "ModuleBindInfo 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ModuleBindInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: ModuleBindInfo
helpviewer_keywords: ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6488503e0300530b22c0c6f904e11db7f5d5b41c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="modulebindinfo-structure"></a>ModuleBindInfo 構造体
参照されるモジュールとそれを含むアセンブリに関する詳細情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`dwAppDomainId`|一意の識別子、`IStream`への呼び出しによって返される、 [ihostassemblystore::providemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)元となる参照されるモジュールが読み込まれるメソッド。|  
|`lpAssemblyIdentity`|参照されるモジュールを含むアセンブリの一意の識別子。|  
|`lpModuleName`|参照されるモジュールの名前。|  
  
## <a name="remarks"></a>コメント  
 `ModuleBindInfo`パラメーターとして渡される`IHostAssemblyStore::ProvideModule`です。 ホスト提供の一意識別子`dwAppDomainId`共通言語ランタイム (CLR) にします。 呼び出した後、 [ihostassemblystore::provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)ランタイム識別子を使用して決定メソッドが返されるかどうかの内容、`IStream`マップされています。 場合は、ランタイムは、ストリームを再割り当てするのではなく、既存のコピーを読み込みます。 ランタイムへの呼び出しから返されるストリームのルックアップ キーとしてこの識別子を使用するも、`IHostAssemblyStore::ProvideAssembly`メソッドです。 したがって、識別子は、アセンブリの要求だけモジュール同様の要求の一意である必要があります。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.idl  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ホスト構造体](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [AssemblyBindInfo 構造体](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)  
 [ICLRAssemblyIdentityManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [ICLRAssemblyReferenceList インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
