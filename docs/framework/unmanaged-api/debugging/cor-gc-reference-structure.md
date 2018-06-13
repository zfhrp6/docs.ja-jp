---
title: COR_GC_REFERENCE 構造体
ms.date: 03/30/2017
api_name:
- COR_GC_REFERENCE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_GC_REFERENCE
helpviewer_keywords:
- COR_GC_REFERENCE structure [.NET Framework debugging]
ms.assetid: 162e8179-0cd4-4110-8f06-5f387698bd62
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 732bc9d38ca0d6c2dc3f30603a722b7370034b80
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408191"
---
# <a name="corgcreference-structure"></a>COR_GC_REFERENCE 構造体
ガベージ コレクトされるオブジェクトに関する情報が含まれます。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct _COR_GC_REFERENCE {  
    ICorDebugAppDomain *domain;   
    ICorDebugValue *location;  
    CorGCReferenceType type;  
    UINT64 extraData;  
} COR_GC_REFERENCE;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`domain`|ハンドルまたはオブジェクトが所属するアプリケーション ドメインへのポインター。 その値があります`null`です。|  
|`location`|ICorDebugValue またはガベージ コレクトされるオブジェクトに対応する ICorDebugReferenceValue インターフェイスのいずれか。|  
|`type`|A [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)でルートの出所を示す列挙値。 詳細については、「解説」を参照してください。|  
|`extraData`|ガベージ コレクトされるオブジェクトに関する追加データ。 この情報は、によって示される、オブジェクトのソースとは異なります。、`type`フィールドです。 詳細については、「解説」を参照してください。|  
  
## <a name="remarks"></a>コメント  
 `type`フィールドは、 [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)参照元の場所を示す列挙値。 特定の`COR_GC_REFERENCE`値は、管理対象オブジェクトの次の種類のいずれかを反映できます。  
  
-   すべてのマネージ スタックからオブジェクト (`CorGCReferenceType.CorReferenceStack`)。 これには、共通言語ランタイムによって作成されたオブジェクトと同様に、マネージ コードでのライブ参照が含まれます。  
  
-   オブジェクト ハンドル テーブルから (`CorGCReferenceType.CorHandle*`)。 これには、強い参照が含まれます (`HNDTYPE_STRONG`と`HNDTYPE_REFCOUNT`) とモジュールの静的変数。  
  
-   ファイナライザー キューからのオブジェクト (`CorGCReferenceType.CorReferenceFinalizer`)。 ファイナライザー キューは、ファイナライザーが実行されるまで、オブジェクトをルートします。  
  
 `extraData`フィールドには参照のソース (または型) によって余分なデータが含まれています。 指定できる値は次のとおりです。  
  
-   `DependentSource`。 場合、`type`は`CorGCREferenceType.CorHandleStrongDependent`、このフィールドはオブジェクトでガベージ コレクトされるオブジェクトの場合は、ルートを`COR_GC_REFERENCE.Location`です。  
  
-   `RefCount`。 場合、`type`は`CorGCREferenceType.CorHandleStrongRefCount`、このフィールドは、ハンドルの参照カウントします。  
  
-   `Size`。 場合、`type`は`CorGCREferenceType.CorHandleStrongSizedByref`、このフィールドは、ガベージ コレクターがオブジェクトのルートを計算する、オブジェクト ツリーの最後のサイズ。 この計算は最新の状態とは限りませんではないことに注意してください。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
