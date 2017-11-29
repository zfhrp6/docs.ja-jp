---
title: "ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 84b58e3a016431eba10710ea384338cb388404ff
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs メソッド
キャッシュされた列挙子を取得[!INCLUDE[wrt](../../../../includes/wrt-md.md)]アプリケーション ドメイン内の型、インターフェイスの id に基づいています。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cReqTypes`  
 [in]必要な種類の数。  
  
 `iidsToResolve`  
 [in]管理対象の形式に対応するインターフェイスの id を格納している配列へのポインター、[!INCLUDE[wrt](../../../../includes/wrt-md.md)]を取得する型。  
  
 `ppTypesEnum`  
 [out]マネージの表現をキャッシュの列挙体をできるようにする"ICorDebugTypeEnum"インターフェイス オブジェクトのアドレスへのポインター、[!INCLUDE[wrt](../../../../includes/wrt-md.md)]にインターフェイス識別子に基づいて、型が取得`iidsToResolve`です。  
  
## <a name="remarks"></a>コメント  
 "ICorDebugTypeEnum"コレクション内の対応するエントリがの型を持つメソッドは、特定のインターフェイスの識別子の情報を取得できなかった場合、`ELEMENT_TYPE_END`データ取得に関する問題によるエラーのまたは`ELEMENT_TYPE_VOID`の不明なインターフェイス識別子。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugAppDomain3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
