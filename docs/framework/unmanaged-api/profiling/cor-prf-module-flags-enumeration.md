---
title: COR_PRF_MODULE_FLAGS 列挙体
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 48617022940d889abedb9a9d25f04782371c4a5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451946"
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
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [列挙型のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
