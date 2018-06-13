---
title: ICorDebugMDA::GetDescription メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetDescription
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetDescription
helpviewer_keywords:
- GetDescription method [.NET Framework debugging]
- ICorDebugMDA::GetDescription method [.NET Framework debugging]
ms.assetid: 01d1b481-ca67-4712-8744-d342ec0df639
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fdace527194228dd6004a991950a80d23275650
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413297"
---
# <a name="icordebugmdagetdescription-method"></a>ICorDebugMDA::GetDescription メソッド
によって表されるマネージ デバッグ アシスタント (MDA) の説明を含む文字列を取得[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cchName`  
 [in]説明を格納する文字列バッファーのサイズ。  
  
 `pcchName`  
 [out]文字列バッファーに返されるバイト数へのポインター。  
  
 `szName`  
 [out]MDA の説明を含む文字列バッファー。  
  
## <a name="remarks"></a>コメント  
 文字列は長さ 0 を指定できます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorDebugMDA インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [マネージ デバッグ アシスタントによるエラーの診断](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
