---
title: ICorDebugAppDomain::EnumerateBreakpoints メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateBreakpoints
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints method [.NET Framework debugging]
- EnumerateBreakpoints method [.NET Framework debugging]
ms.assetid: 206069c5-25cb-4794-9d69-67c5aa7ed0af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cfd7ee890a7f2c3ea8cd3de9fbe830575c0ca10c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402775"
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a>ICorDebugAppDomain::EnumerateBreakpoints メソッド
アプリケーション ドメインですべてのアクティブなブレークポイントの列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppBreakpoints`  
 [out]アプリケーション ドメイン内のすべてのアクティブなブレークポイントの列挙子である ICorDebugBreakpointEnum オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>コメント  
 列挙子には、すべての種類関数のブレークポイントとデータ ブレークポイントを含む、ブレークポイントにはが含まれています。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
