---
title: ICorDebugILFrame::GetArgument メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetArgument
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetArgument
helpviewer_keywords:
- GetArgument method [.NET Framework debugging]
- ICorDebugILFrame::GetArgument method [.NET Framework debugging]
ms.assetid: 4e2fd423-f643-4c27-ba5f-41b5ebc3b416
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1653913ca7410728f0f90a546f613a9d8b88be7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414054"
---
# <a name="icordebugilframegetargument-method"></a>ICorDebugILFrame::GetArgument メソッド
この Microsoft intermediate language (MSIL) のスタック フレーム内には、指定された引数の値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwIndex`  
 [in]MSIL のこのスタック フレーム内の引数のインデックス。  
  
 `ppValue`  
 [out]取得した値を表す ICorDebugValue オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>コメント  
 `GetArgument` ・ イン タイム (JIT) コンパイル フレームまたは MSIL スタック フレームで、メソッドを使用できます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
