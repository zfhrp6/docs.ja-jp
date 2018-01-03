---
title: "ICorDebugGCReferenceEnum インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGCReferenceEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGCReferenceEnum
helpviewer_keywords: ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1afe52c3df8f61b234b3c68ee819ba8389593c82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuggcreferenceenum-interface"></a>ICorDebugGCReferenceEnum インターフェイス
ガベージ コレクトされるオブジェクトの列挙子を提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Next メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|指定した数を取得[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)ガベージ コレクトされるオブジェクトに関する情報が含まれているインスタンス。|  
  
## <a name="remarks"></a>コメント  
 `ICorDebugGCReferenceEnum`インターフェイスは、"ICorDebugEnum"インターフェイスを実装します。  
  
 `ICorDebugGCReferenceEnum`インスタンスが格納されます[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)を呼び出してインスタンス、 [icordebugprocess 5::enumerategcreferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)メソッドです。 [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)を呼び出してオブジェクトを列挙することができます、 [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)メソッドです。  
  
 [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)このメソッドによって設定されます。 コレクション内のオブジェクトは、3 種類のオブジェクトを表します。  
  
-   すべてのマネージ スタックからオブジェクト。 これには、マネージ コードだけでなく、共通言語ランタイムによって作成されたオブジェクトのライブ参照が含まれます。  
  
-   オブジェクト ハンドル テーブルをします。 これには、強い参照が含まれます (`HNDTYPE_STRONG`と`HNDTYPE_REFCOUNT`) とモジュールの静的変数。  
  
-   ファイナライザー キューからのオブジェクト。 ファイナライザー キューは、ファイナライザーが実行されるまで、オブジェクトをルートします。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
