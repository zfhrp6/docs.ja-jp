---
title: ICorDebugProcess5 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5
helpviewer_keywords:
- ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3aed85e989313e4778e12a6f6bb789ccef49747
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess5-interface"></a>ICorDebugProcess5 インターフェイス
管理対象のオブジェクトのガベージ コレクションに関する情報を提供する、マネージ ヒープに対するアクセスをサポートするために ICorDebugProcess インターフェイスを拡張し、デバッガーかどうかを判断するには、アプリケーションのローカル ネイティブ イメージ キャッシュからイメージを読み込みます。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnableNGENPolicy メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|アプリケーションがマネージ デバッガーで実行中にネイティブ イメージを読み込む方法を決定する値を設定します。|  
|[EnumerateGCReferences メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|プロセスでガベージ コレクトされるすべてのオブジェクトの列挙子を取得します。|  
|[EnumerateHandles メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|プロセスで、オブジェクト ハンドルの列挙子を取得します。|  
|[EnumerateHeap メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|マネージ ヒープのオブジェクトの列挙子を取得します。|  
|[EnumerateHeapRegions メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|マネージ ヒープの領域の列挙子を取得します。|  
|[GetArrayLayout メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|メモリ内には、配列のレイアウトに関する情報を取得します。|  
|[GetGCHeapInformation メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|ポインターを取得、 [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)には、マネージ ヒープでガベージ コレクトされるオブジェクトに関する情報を格納する構造体。|  
|[GetObject メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|マネージ ヒープのオブジェクトへのポインターを取得します。|  
|[GetTypeFields メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|その型の識別子に基づく型のフィールド情報を格納している配列へのポインターを取得します。|  
|[GetTypeForTypeID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|その型の識別子に基づくオブジェクトに関する情報を提供する型オブジェクトを取得します。|  
|[GetTypeID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|指定したアドレスにオブジェクトの型の識別子を取得します。|  
|[GetTypeLayout メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|その型の識別子に基づいて、メモリ内のオブジェクトのレイアウトに関する情報を取得します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスは ICorDebugProcess、ICorDebugProcess2、論理的に拡張し、 [ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)インターフェイスです。  
  
> [!NOTE]
>  このインターフェイスは、別のコンピューターとは別のプロセスでのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
