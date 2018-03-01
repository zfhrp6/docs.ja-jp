---
title: "COR_PRF_MODULE_FLAGS 列挙体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- COR_PRF_MODULE_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MODULE_FLAGS
helpviewer_keywords:
- COR_PRF_MODULE_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 7bc3a938-0df1-4739-9ff1-89cff454b704
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 727816a674d2357c8a9ba1f19679c57669e92f50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corprfmoduleflags-enumeration"></a>COR_PRF_MODULE_FLAGS 列挙体
モジュールのプロパティを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum  
{  
    COR_PRF_MODULE_DISK             = 0x00000001,  
    COR_PRF_MODULE_NGEN             = 0x00000002,  
    COR_PRF_MODULE_DYNAMIC          = 0x00000004,  
    COR_PRF_MODULE_COLLECTIBLE      = 0x00000008,  
    COR_PRF_MODULE_RESOURCE         = 0x00000010,  
    COR_PRF_MODULE_FLAT_LAYOUT      = 0x00000020,  
    COR_PRF_MODULE_WINDOWS_RUNTIME  = 0x00000040  
}   COR_PRF_MODULE_FLAGS;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|COR_PRF_MODULE_DISK|モジュールは、ディスクから読み込まれました。|  
|COR_PRF_MODULE_NGEN|モジュールは、ネイティブ イメージ ジェネレーター (Ngen.exe) によって生成されました。|  
|COR_PRF_MODULE_DYNAMIC|メソッドによって作成されたモジュール、<xref:System.Reflection.Emit?displayProperty=nameWithType>名前空間。|  
|COR_PRF_MODULE_COLLECTIBLE|モジュールの有効期間は、ガベージ コレクターによって管理されます。|  
|COR_PRF_MODULE_RESOURCE|モジュールは、メタデータが含まれていないと、リソースとしてにのみ使用されます。 このビットのマネージ相当するものは、<xref:System.Reflection.Module.IsResource%2A?displayProperty=nameWithType>メソッドです。|  
|COR_PRF_MODULE_FLAT_LAYOUT|メモリ内のモジュールのレイアウトは、割り当てられていないフラットな。 モジュールがこのビット設定場合、ポータブル実行可能 (PE) ファイル ヘッダーから直接情報が相対仮想アドレス (Rva) ヘッダーを解釈する際は注意する必要があるプロファイラーです。|  
|COR_PRF_MODULE_WINDOWS_RUNTIME|このモジュールのアセンブリのメタデータで Windows ランタイム コンテンツ タイプ フラグが設定します。 これは、すべての Windows メタデータ (.winmd) モジュールの場合です。|  
  
## <a name="remarks"></a>コメント  
 プロファイラーに返されるビットは COR_PRF_MODULE_FLAGS から、`pdwModuleFlags`出力のパラメーター、 [icorprofilerinfo 3::getmoduleinfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)メソッドです。 2 つ以上のフラグの組み合わせによっては、可能であればが、すべての組み合わせが可能です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [列挙型のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
