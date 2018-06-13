---
title: ICorDebugNativeFrame2::IsMatchingParentFrame メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2.IsMatchingParentFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2::IsMatchingParentFrame
helpviewer_keywords:
- IsMatchingParentFrame method [.NET Framework debugging]
- ICorDebugNativeFrame2::IsMatchingParentFrame method [.NET Framework debugging]
ms.assetid: d2ca20db-df22-4528-a0dd-a09ea62c8998
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 39c0ea69a0922f5e0d25c98c21ec17a872b2f421
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418871"
---
# <a name="icordebugnativeframe2ismatchingparentframe-method"></a>ICorDebugNativeFrame2::IsMatchingParentFrame メソッド
指定したフレームが現在のフレームの親であるかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT IsMatchingParentFrame([in] ICorDebugNativeFrame2  
                                      *pPotentialParentFrame,  
                              [out] BOOL *pIsParent);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pPotentialParentFrame`  
 [in]親のステータスを評価するフレーム オブジェクトへのポインター。  
  
 `pIsParent`  
 [out]`true`場合`pPotentialParentFrame`が現在のフレームの親である、それ以外の`false`します。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|親の状態が正常に返されます。|  
|E_FAIL|親のステータスは返されませんでした。|  
|E_INVALIDARG|`pPotentialParentFrame` または `pIsParent` が null です。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>コメント  
 `IsMatchingParentFrame` 返します`true`フレーム オブジェクトのメソッドに渡すメソッドが呼び出されたフレーム オブジェクトの親であるかどうか。 指定したフレームの子ではないフレーム上のメソッドを呼び出す場合は、エラーを返します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugNativeFrame2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
