---
title: "ICorDebugInternalFrame2::IsCloserToLeaf メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame2.IsCloserToLeaf Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame2::IsCloserToLeaf
helpviewer_keywords:
- ICorDebugInternalFrame2::IsCloserToLeaf method [.NET Framework debugging]
- IsCloserToLeaf method [.NET Framework debugging]
ms.assetid: c1d3d1eb-8370-4f25-8297-3bd262b4740a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b6b769c25e0cd706eb57965b73d0fcfdcf9b9ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginternalframe2isclosertoleaf-method"></a>ICorDebugInternalFrame2::IsCloserToLeaf メソッド
チェックするかどうか、`this`内部フレームは、指定した ICorDebugFrame オブジェクトよりも、リーフに近づきます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT IsCloserToLeaf([in] ICorDebugFrame * pFrameToCompare,  
                       [out] BOOL * pIsCloser);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pFrameToCompare`  
 [in]比較するポインター`ICorDebugFrame`オブジェクト。  
  
 `pIsCloser`  
 [out]`true`場合、`this`内部フレームがで指定された枠よりも、リーフに近い`pFrameToCompare`、それ以外の`false`します。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|比較が正常に実行されました。|  
|E_FAIL|比較を実行できませんでした。|  
|E_INVALIDARG|`pFrameToCompare` または `pIsCloser` が null です。|  
  
## <a name="remarks"></a>コメント  
 `IsCloserToLeaf`スタック上の他のフレームを持つ内部フレームをインターリーブのポリシーを実装するために使用します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorDebugInternalFrame2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
