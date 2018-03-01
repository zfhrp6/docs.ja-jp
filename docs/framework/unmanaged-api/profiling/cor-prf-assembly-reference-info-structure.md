---
title: "COR_PRF_ASSEMBLY_REFERENCE_INFO 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4b5889f8e0b0dc8faab76f637e2fcf03853709bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corprfassemblyreferenceinfo-structure"></a>COR_PRF_ASSEMBLY_REFERENCE_INFO 構造体
[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
 アセンブリ参照クロージャのウォークを実行するときに考慮する必要があるアセンブリ参照の情報を、共通言語ランタイムに提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _COR_PRF_ASSEMBLY_REFERENCE_INFO {  
    void* pbPublicKeyOrToken;  
    ULONG cbPublicKeyOrToken;  
    LPCWSTR szName;  
    ASSEMBLYMETADATA* pMetaData;  
    void* pbHashValue;  
    ULONG cbHashValue;  
    DWORD dwAssemblyRefFlags;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|公開キー、またはアセンブリのトークンへのポインター。|  
|`cbPublicKeyOrToken`|公開キーまたはトークンのバイト数。|  
|`szName`|参照されるアセンブリの名前。|  
|`pMetaData`|アセンブリのメタデータへのポインター。|  
|`pbHashValue`|ハッシュ バイナリ ラージ オブジェクト (BLOB) へのポインター。|  
|`cbHashValue`|ハッシュ BLOB のバイト数。|  
|`dwAssemblyRefFlags`|アセンブリのフラグ。|  
  
## <a name="remarks"></a>コメント  
 `COR_PRF_EX_CLAUSE_INFO` 構造は、追加のアセンブリ参照を宣言するときに、プロファイラーによって値が設定されます。ここでの追加のアセンブリ参照は、アセンブリ参照クロージャのウォークを実行するときに共通言語ランタイムが考慮するものです。  
  
 プロファイラーの登録の場合、 [icorprofilercallback 6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)コールバック メソッド、ランタイムへのポインターと共に、読み込まれるアセンブリの名前とパスを渡す、 [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)インターフェイス オブジェクトをメソッドにします。 プロファイラーを呼び出すことができますし、 [icorprofilerassemblyreferenceprovider::addassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)メソッドを`COR_PRF_ASSEMBLY_REFERENCE_INFO`オブジェクトで指定されたアセンブリから参照される対象アセンブリごとに、 [Icorprofilercallback 6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)コールバック。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [構造体のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)  
 [GetAssemblyReferences メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)  
 [AddAssemblyReference メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
